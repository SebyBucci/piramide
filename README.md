# piramide

Consegna:
Quando si avvia un progetto come la costruzione di una piramide, è meglio pensarci due volte.

Il tuo compito oggi è scrivere un programma che calcoli l'altezza massima di una piramide (in piani) dato un certo numero di cubi di pietra.

Ipotizzando che:

- i piani della piramide siano quadrati
- la piramide da costruire sia compatta, cioè non ci siano cavità al suo interno. 
- ogni piano è quadrato, con una lunghezza laterale inferiore di due rispetto a quella sottostante.
- il primo piano è sempre di un mattone

Sviluppare:
- il metodo int Piani( int mattoni ) che torna il numero di piani
- il metodo int Rimanenti( int mattoni ) che torna il numero di mattoni rimasti dopo la costruzione


 Codice intero:
  ```C#
  
  using System;
namespace Piramide{
public class Piramide{
    public static int Piani(int mattoni) {
        int piani = 0;
        while (mattoni >= (2 * piani + 1) * (2 * piani + 1)) {
        piani++;
         mattoni -= (2 * piani - 1) * (2 * piani - 1);
        }
        return piani;
    }
    public static int Rimanenti(int mattoni) {
        int piani = Piani(mattoni);
        int mattoniutilizzati = 0;
        for (int i = 1; i <= piani; i++) {
            mattoniutilizzati += (2 * i - 1) * (2 * i - 1);
        }
        return mattoni - mattoniutilizzati;
        }
    }
}
   ```

 Ho utilizzato un ciclo while per incrementare il numero di piani finché ci sono abbastanza mattoni per costruirli.
 La formula utilizzata per calcolare il numero di mattoni necessari per un certo numero di piani è (2 * piani - 1) * (2 * piani - 1):
 ```C#
         while (mattoni >= (2 * piani + 1) * (2 * piani + 1)) {
        piani++;
         mattoni -= (2 * piani - 1) * (2 * piani - 1);
 ```
 
Poi ho calcolato il numero di mattoni utilizzati per costruire la piramide e poi sottrae questo numero dalla quantità totale di mattoni per ottenere il numero di mattoni rimanenti dopo la costruzione.

```C#
    public static int Rimanenti(int mattoni) {
        int piani = Piani(mattoni);
        int mattoniutilizzati = 0;
        for (int i = 1; i <= piani; i++) {
            mattoniutilizzati += (2 * i - 1) * (2 * i - 1);
        }
        return mattoni - mattoniutilizzati;
        }
 ```


