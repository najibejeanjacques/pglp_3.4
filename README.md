# pglp_3.4

1) Les problèmes qui peuvent se poser sur cette solution sont:
Dans cette situation nous constatons que SimplePrinter implements Printer mais ne fait qu'imprimé des documents c'est a dire implmenete uniquement la méthode print() mais pas les autres methodes. Le problème qui peux se poser a ce niveau est SimplePrinter depend de quelques choses qu'elle n'utilise pas.

2) L'impact que cela aura sur SimpePrinter est que:
Si on change l'interface de la méthode fax() en 
      
            void fax(List <Document> l);
      
cela aura pour impact, une reconstruction de la methode SimplePrinter afin de prendre en compte la nouvelle méthode fax implementée qu'elle n'utilisera pas, du coups elle dépend toujours de quelque chose qu'elle n'utilise pas, et une modification de n'importe qu'elles méthode qu'elle n'utilse pas entrainera une recompilation de l'application SimplePrinter.

3) Proposons une solution qui respect ISP:
-Créons les interfaces afin de respecter le principe ISP:
    
            interface Printer
            {
                  void print();  
            }
      
            interface Scanner
            {
                  void scan();
            }
      
            interface Copieur
            {
                  void copy();
            }
      
            interface Fax
            {
                  void fax();
            }
      
 Après cela si une application est de type bien défini, il suffit d'implement avec l'interface bien définie qui fera le travail sans dépendre d'autres choses qu'elle n'utilise pas. Pour prendre en compte la nouvelle demande nous aurons alors
 
      public class SimpleFax implements Fax,Printer
      {
            @Override
            public print()
            {
                //Traitement pour l'impression
            }
            
            @Override
            public fax()
            {
                //Traitement pour l'utilisation du fax
            }
      }
      
      
      
      
      
      
