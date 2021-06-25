
# 2) Descreva o funcionamento de uma árvore binária, também compare o desempenho de uma árvore binária balanceada e outra não balanceada, relacionando as principais diferenças entre as duas e seus possíveis impactos em execução. Também adicione um exemplo prático de cada uma delas.
# R:  
#### Uma árvore é uma estrutura de dados composta por elementos interligados. Cada elemento contém dados que descrevem alguma coisa de interesse e geralmente são chamados de nós. Dois nós são conectados por meio de ligações chamadas ramos. Como toda árvore é um tipo de grafo, um nó corresponde a um vértice do grafo e um ramo corresponde a uma aresta.

#### Árvores são estruturas hierárquicas, pois há um único caminho de interligações que leva até um nó específico (árvores são grafos sem ciclos). Um nó pode levar diretamente a uma certa quantidade de nós, o que determina o grau desse nó. Se um nó permite chegar a dois outros nós diretamente, ele tem grau dois. Árvores binárias são aquelas em que cada nó leva a, no máximo, dois outros nós diretamente, como mostrada a seguir.

#### Se a árvore binária possui todos os seus nós com o máximo de descendentes, exceto na última camada, onde todos os nós possuem grau zero, são chamadas de árvores binárias completas, como a mostrada na próxima figura.

#### Caso nessa árvore completa do exemplo não tivesse os nós com os valores 19 e 25, ela ainda seria considerada completa, pois em geral se tolera que o último nível esteja incompleto, desde que seus nós estejam alocados na esquerda desse nível. Repare então que a árvore da primeira figura não é completa, por esse critério.

#### Árvore Balanceada são as árvores que minimizam o número de comparações efetuadas no pior caso para uma busca com chaves de probabilidades de ocorrências idênticas. Contudo, para garantir essa propriedade em aplicações dinâmicas, é preciso reconstruir a árvore para seu estado ideal a cada operação sobre seus nós (inclusão ou exclusão), para ser alcançado um custo de algoritmo com o tempo de pesquisa tendendo a {\displaystyle O(\log n)}{\displaystyle O(\log n)}.

As operações de busca, inserção e remoção de elementos possuem complexidade {\displaystyle O(\log n)}{\displaystyle O(\log n)}(no qual {\displaystyle n}n é o número de elementos da árvore), que são aplicados a árvore de busca binária.
#### Árvore Binária exemplo prático:
public class Arvbin<T extends Comparable<T>>
{
    private T val;   /* Valor armazenado na raiz. */

    /* Referências para sub-árvores. */
    private Arvbin<T> esq, dir;

    /* Construtor de árvore sem sub-ávores (dir = esq = null). É fornecido apenas o valor da raiz. */
    public Arvbin(T valor)
    {
        val = valor;
        esq = null;
        dir = null;
    }

    /* Construtor de árvore com sub-ávores. São fornecidos
    o valor da raiz e as sub-árvores, que devem ter sido 
    construídas previamente.*/
    public Arvbin(T valor, Arvbin<T> arvEsq, Arvbin<T> arvDir)
    {
        val = valor;
        esq = arvEsq;
        dir = arvDir;
    }

    /* Retorna o valor armazenado na raiz. */
    public T retornaVal()
    {
        return val;
    }

    /* Retorna a sub-árvore esquerda 
       (ou null se não houver). */
    public Arvbin<T> retornaEsq()
    {
        return esq;
    }

    /* Retorna a sub-árvore direita 
    (ou null se não houver). */
    public Arvbin<T> retornaDir()
    {
        return dir;
    }

    /* Modifica o valor armazenado na raiz. */
    public void defineVal(T valor)
    {
        val = valor;
    }

    /* Redefine a sub-árvore esquerda, apagando a antiga se houver. */
    public void defineEsq(Arvbin<T> filho)
    {
        esq = filho;
    } 

    /* Redefine a sub-árvore direita, apagando a antiga se houver. */
    public void defineDir(Arvbin<T> filho)
    {
        dir = filho;
    }

    /* Imprime o conteúdo da árvore em pré-ordem */
    public void mostra()
    {
        System.out.print("(" + val);
        if (esq != null)
            esq.mostra();
        if (dir != null)
            dir.mostra();
        System.out.print(")");
    }

    /* Calcula e retorna a altura da árvore. */
    public int calculaAltura()
    {
        if((esq == null) && (dir == null))
            return 0;

        int altEsq = 0, altDir = 0;

        if(esq != null)
            altEsq = esq.calculaAltura();

        if(dir != null)
            altDir = dir.calculaAltura();

        return 1 + Math.max(altEsq, altDir);
    }

    /* Calcula e retorna o maior valor contido na árvore. */
    public T calculaMaximo()
    {
        if((esq == null) && (dir == null))
            return val;

        T maiorGeral, maiorEsq, maiorDir; 

        if((esq != null) && (dir == null))
        {
            maiorGeral = esq.calculaMaximo();
        }
        else if((esq == null) && (dir != null))
        {
            maiorGeral = dir.calculaMaximo();
        }
        else
        {
            maiorEsq = esq.calculaMaximo();
            maiorDir = dir.calculaMaximo();

            if(maiorEsq.compareTo(maiorDir) > 0)
                maiorGeral = maiorEsq;
            else
                maiorGeral = maiorDir;
        }

        if(maiorGeral.compareTo(val) > 0)
            return maiorGeral;

        return val;
    }

    /* Verifica se um valor está na árvore. Se estiver, retorna um ponteiro para o
       o nó que tem esse valor. Caso contrário, retorna null. */
    public Arvbin<T> busca(T valor)
    {

        Arvbin<T> ret;

        /* Se é igual ao valor armazenado, não precisa procurar mais. O nó é a raiz. */
        if (valor.compareTo(val) == 0)
        {
            return this;
        }

        /* Senão, começa procurando na sub-árvore esquerda. */
        if (esq != null){
            ret = esq.busca(valor);
            if (ret != null)
                return ret;
        }

        /* Se chega a esse ponto, estará na árvore se, e somente se, 
         estiver na sub-árvore direita */
        if (dir != null) 
            return dir.busca(valor);
        return null;
    }
}
Main
public class Main
{
    public static void main(String[] args)
    {
        Arvbin<Integer> a1 = new Arvbin<Integer>(1),
                a2 = new Arvbin<Integer>(2),
                a3 = new Arvbin<Integer>(3,a1,a2),
                a4 = new Arvbin<Integer>(4),
                a5 = new Arvbin<Integer>(5),
                a6 = new Arvbin<Integer>(6),
                a7 = new Arvbin<Integer>(7,a5,a6),
                a8 = new Arvbin<Integer>(8),
                a9 = new Arvbin<Integer>(9),
                a10 = new Arvbin<Integer>(10,a8,a9);

                a4.defineEsq(a3);
                a4.defineDir(a7);
                a4.mostra();
                System.out.println();

                Arvbin<Integer> a11 = a4.busca(3);
                if (a11 != null)
                {
                    a11.defineVal(11);
                    a11.defineEsq(a10);
                }
                a4.mostra();
                System.out.println();
    }
}


#### Árvore Balanceada exemplo prático:
ArvoreAvl.java
import java.util.ArrayList;

public class ArvoreAvl {

  protected No raiz;

	public void inserir(int k) {
		No n = new No(k);
		inserirAVL(this.raiz, n);
	}

	public void inserirAVL(No aComparar, No aInserir) {

		if (aComparar == null) {
			this.raiz = aInserir;

		} else {

			if (aInserir.getChave() < aComparar.getChave()) {

				if (aComparar.getEsquerda() == null) {
					aComparar.setEsquerda(aInserir);
					aInserir.setPai(aComparar);
					verificarBalanceamento(aComparar);

				} else {
					inserirAVL(aComparar.getEsquerda(), aInserir);
				}

			} else if (aInserir.getChave() > aComparar.getChave()) {

				if (aComparar.getDireita() == null) {
					aComparar.setDireita(aInserir);
					aInserir.setPai(aComparar);
					verificarBalanceamento(aComparar);

				} else {
					inserirAVL(aComparar.getDireita(), aInserir);
				}

			} else {
				// O nó já existe
			}
		}
	}

	public void verificarBalanceamento(No atual) {
		setBalanceamento(atual);
		int balanceamento = atual.getBalanceamento();

		if (balanceamento == -2) {

			if (altura(atual.getEsquerda().getEsquerda()) >= altura(atual.getEsquerda().getDireita())) {
				atual = rotacaoDireita(atual);

			} else {
				atual = duplaRotacaoEsquerdaDireita(atual);
			}

		} else if (balanceamento == 2) {

			if (altura(atual.getDireita().getDireita()) >= altura(atual.getDireita().getEsquerda())) {
				atual = rotacaoEsquerda(atual);

			} else {
				atual = duplaRotacaoDireitaEsquerda(atual);
			}
		}

		if (atual.getPai() != null) {
			verificarBalanceamento(atual.getPai());
		} else {
			this.raiz = atual;
		}
	}

	public void remover(int k) {
		removerAVL(this.raiz, k);
	}

	public void removerAVL(No atual, int k) {
		if (atual == null) {
			return;

		} else {

			if (atual.getChave() > k) {
				removerAVL(atual.getEsquerda(), k);

			} else if (atual.getChave() < k) {
				removerAVL(atual.getDireita(), k);

			} else if (atual.getChave() == k) {
				removerNoEncontrado(atual);
			}
		}
	}

	public void removerNoEncontrado(No aRemover) {
		No r;

		if (aRemover.getEsquerda() == null || aRemover.getDireita() == null) {

			if (aRemover.getPai() == null) {
				this.raiz = null;
				aRemover = null;
				return;
			}
			r = aRemover;

		} else {
			r = sucessor(aRemover);
			aRemover.setChave(r.getChave());
		}

		No p;
		if (r.getEsquerda() != null) {
			p = r.getEsquerda();
		} else {
			p = r.getDireita();
		}

		if (p != null) {
			p.setPai(r.getPai());
		}

		if (r.getPai() == null) {
			this.raiz = p;
		} else {
			if (r == r.getPai().getEsquerda()) {
				r.getPai().setEsquerda(p);
			} else {
				r.getPai().setDireita(p);
			}
			verificarBalanceamento(r.getPai());
		}
		r = null;
	}

	public No rotacaoEsquerda(No inicial) {

		No direita = inicial.getDireita();
		direita.setPai(inicial.getPai());

		inicial.setDireita(direita.getEsquerda());

		if (inicial.getDireita() != null) {
			inicial.getDireita().setPai(inicial);
		}

		direita.setEsquerda(inicial);
		inicial.setPai(direita);

		if (direita.getPai() != null) {

			if (direita.getPai().getDireita() == inicial) {
				direita.getPai().setDireita(direita);
			
			} else if (direita.getPai().getEsquerda() == inicial) {
				direita.getPai().setEsquerda(direita);
			}
		}

		setBalanceamento(inicial);
		setBalanceamento(direita);

		return direita;
	}

	public No rotacaoDireita(No inicial) {

		No esquerda = inicial.getEsquerda();
		esquerda.setPai(inicial.getPai());

		inicial.setEsquerda(esquerda.getDireita());

		if (inicial.getEsquerda() != null) {
			inicial.getEsquerda().setPai(inicial);
		}

		esquerda.setDireita(inicial);
		inicial.setPai(esquerda);

		if (esquerda.getPai() != null) {

			if (esquerda.getPai().getDireita() == inicial) {
				esquerda.getPai().setDireita(esquerda);
			
			} else if (esquerda.getPai().getEsquerda() == inicial) {
				esquerda.getPai().setEsquerda(esquerda);
			}
		}

		setBalanceamento(inicial);
		setBalanceamento(esquerda);

		return esquerda;
	}

	public No duplaRotacaoEsquerdaDireita(No inicial) {
		inicial.setEsquerda(rotacaoEsquerda(inicial.getEsquerda()));
		return rotacaoDireita(inicial);
	}

	public No duplaRotacaoDireitaEsquerda(No inicial) {
		inicial.setDireita(rotacaoDireita(inicial.getDireita()));
		return rotacaoEsquerda(inicial);
	}

	public No sucessor(No q) {
		if (q.getDireita() != null) {
			No r = q.getDireita();
			while (r.getEsquerda() != null) {
				r = r.getEsquerda();
			}
			return r;
		} else {
			No p = q.getPai();
			while (p != null && q == p.getDireita()) {
				q = p;
				p = q.getPai();
			}
			return p;
		}
	}

	private int altura(No atual) {
		if (atual == null) {
			return -1;
		}

		if (atual.getEsquerda() == null && atual.getDireita() == null) {
			return 0;
		
		} else if (atual.getEsquerda() == null) {
			return 1 + altura(atual.getDireita());
		
		} else if (atual.getDireita() == null) {
			return 1 + altura(atual.getEsquerda());
		
		} else {
			return 1 + Math.max(altura(atual.getEsquerda()), altura(atual.getDireita()));
		}
	}

	private void setBalanceamento(No no) {
		no.setBalanceamento(altura(no.getDireita()) - altura(no.getEsquerda()));
	}

	final protected ArrayList<No> inorder() {
		ArrayList<No> ret = new ArrayList<No>();
		inorder(raiz, ret);
		return ret;
	}

	final protected void inorder(No no, ArrayList<No> lista) {
		if (no == null) {
			return;
		}
		inorder(no.getEsquerda(), lista);
		lista.add(no);
		inorder(no.getDireita(), lista);
	}
}
No.java

public class No {
  
	private No esquerda;
	private No direita;
	private No pai;
	private int chave;
	private int balanceamento;

	public No(int k) {
		setEsquerda(setDireita(setPai(null)));
		setBalanceamento(0);
		setChave(k);
	}

	public String toString() {
		return Integer.toString(getChave());
	}

	public int getChave() {
		return chave;
	}

	public void setChave(int chave) {
		this.chave = chave;
	}

	public int getBalanceamento() {
		return balanceamento;
	}

	public void setBalanceamento(int balanceamento) {
		this.balanceamento = balanceamento;
	}

	public No getPai() {
		return pai;
	}

	public No setPai(No pai) {
		this.pai = pai;
		return pai;
	}

	public No getDireita() {
		return direita;
	}

	public No setDireita(No direita) {
		this.direita = direita;
		return direita;
	}

	public No getEsquerda() {
		return esquerda;
	}

	public void setEsquerda(No esquerda) {
		this.esquerda = esquerda;
	}
}