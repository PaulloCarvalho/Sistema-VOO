import java.time.LocalDate;
import java.time.LocalTime;
import java.util.Scanner;

public class Voo {

    private String companhia;
    private String origem;
    private String destino;
    private boolean[] ocupacao;
    private static int numeroDoVoo;
    private LocalTime horaVoo;
    private LocalDate dataVoo;

    public Voo(String companhia, String origem, String destino, int numeroDoVoo, LocalTime horaVoo, LocalDate dataVoo) {
        this.companhia = companhia;
        this.origem = origem;
        this.destino = destino;
        this.ocupacao = new boolean[100];
        this.numeroDoVoo = numeroDoVoo;
        this.dataVoo = dataVoo;
        this.horaVoo = horaVoo;
    }

    public int proximoLivre() {
        for (int i = 0; i < ocupacao.length; i++) {
            if (!ocupacao[i]) {
                return i + 1;
            }
        }
        return -1;
    }

    public boolean verifica(int numeroCadeira) {
        if (numeroCadeira > 0 && numeroCadeira <= 100) {
            return ocupacao[numeroCadeira - 1];
        }
        return false;
    }

    public boolean ocupa(int numeroCadeira) {
        if (numeroCadeira > 0 && numeroCadeira <= 100 && !ocupacao[numeroCadeira - 1]) {
            ocupacao[numeroCadeira - 1] = true;
            return true;
        }
        return false;
    }

    public int vagas() {
        int vagas = 0;
        for (boolean ocupada : ocupacao) {
            if (!ocupada) {
                vagas++;
            }
        }
        return vagas;
    }

    public int getVoo() {
        return numeroDoVoo;
    }

    public LocalDate getData() {
        return dataVoo;
    }

    public static void main(String[] args) {
      Voo easy = new Voo("Azul", "Aracaju-SE", "Destino", 654321, 
      LocalTime.of(10, 13), LocalDate.of(2023, 4, 20));
      


Scanner sc = new Scanner(System.in);
int escolha;


do{

System.out.println();
System.out.println("Opções da Companhia Aeria");
System.out.println("1 - Próxima cadeira livre");
System.out.println("2 - Verificar se está ocupada ");
System.out.println("3 - Sentar na cadeira");
System.out.println("4 - Opções");
System.out.println("5 - Número do voo");
System.out.println("6 - Data de partida ");
System.out.println("0 - Saida  ");
System.out.println(); 
System.out.print("faça sua logistica: ");
System.out.println();

escolha = sc.nextInt();


switch (escolha) {

case 1:
int CadeiraLivre = easy.proximoLivre();
  if (CadeiraLivre != -1) {
System.out.println("Próxima cadeira livre: " + CadeiraLivre);
} else  {
System.out.println("Não há cadeiras livres.");
}  break;


case 2:

System.out.print("Digite o número da cadeira: ");
int numeroCadeira = sc.nextInt();

boolean ocupada = easy.verifica(numeroCadeira);
if (ocupada) {
 System.out.println("Cadeira ocupada.");
 } 
  else {
System.out.println("Cadeira livre.");
}  break;


case 3:
System.out.print("Digite o número da cadeira: ");
int cadeira = sc.nextInt();

boolean Ocupada = easy.ocupa(cadeira);

   if (Ocupada) {
System.out.println("Cadeira: "+ cadeira +" cadeira escolhida.");
 } else {
System.out.println("Cadeira: " + cadeira+ " já está ocupada.");
} break;


case 4:

int vagas = easy.vagas();
System.out.println("Opções disponíveis: " +vagas);

  break;


case 5:
int numeroVoo = easy.getVoo();

System.out.println("Número do voo: " + numeroVoo);
break;

case 6:
LocalDate dataVoo = easy.getData();
System.out.println("Data de Partida: " + dataVoo);

System.out.println("Data de Partida: " + dataVoo);


break;


case 0:

System.out.println("Escolha errada");
break;



default:
System.out.println("Essa escolha não da, tente outra .");
break;
 }


    } while (escolha != 0);

}
}
