## Questions et Réponses

1. **Décrivez les changements observés dans les valeurs des registres `msp`, `lr` et `ipsr` après l'exécution de l'instruction `svc`. Expliquez la signification de ces changements dans le contexte des appels système.**

   Réponse :                                                  
   
   Avant l'exécution de l'instruction `svc`, les valeurs par défaut des registres étaient :
   
   - **ipsr** : `no fault`:mode utilisateur
     - **Signification** : Cela indique qu'il n'y a pas d'exceptions en cours.
   - **msp** : `0x2003ffd0`
     - **Signification** : Cela pointe vers le sommet de la pile principale, où les données de la fonction en cours sont stockées.
   - **lr** : `0x2eb <main+14>`
     - **Signification** : Ce registre contient l'adresse de retour après l'exécution de `main`, indiquant où le programme doit reprendre après un appel de fonction.
   
   
   
   ![image-20241103183138220](/home/mohamed/.config/Typora/typora-user-images/image-20241103183138220.png)
   
   
   
   
   
   Après l'exécution de l'instruction `svc`, les valeurs par défaut des registres sont devenues :
   
   - **ipsr** : `faults 0x11` : mode systeme
     - **Signification** : La valeur `0x11` indique qu'une exception a été déclenchée, signalant le passage en mode d'exécution des appels système.
   - **msp** : `0x2003ffb0`
     - **Signification** : La modification de cette valeur indique que la pile a été ajustée pour gérer des données liées à l'appel système.
   - **lr** : `0xfffffff9`
     - **Signification** : Cette valeur indique que le programme doit revenir à une adresse spécifique après l'exécution de l'appel système, signalant une transition dans le mode d'exécution.
   
   ​																																						
   
   ​											![image-20241103182559563](/home/mohamed/.config/Typora/typora-user-images/image-20241103182559563.png) 
   
   

---

2. **Que révèle la transition vers `sys_add` sur le mécanisme de passage de paramètres entre `test_add` et `sys_add` ? Vérifiez que les paramètres correspondent et expliquez pourquoi cela est important pour la fonctionnalité des appels système.**

   Réponse :  
   <espace pour réponse>

---

3. **Après avoir complété l'exécution de `sys_add`, observez le retour du programme à la fonction `test_add`. Le programme est-il revenu à son mode initial ? Expliquez comment cela est réalisé et pourquoi c'est crucial pour le bon fonctionnement des appels système.**

   Réponse :  
   <espace pour réponse>

---

4. **Vérifiez que le résultat de l'addition effectuée dans `sys_add` est correctement retourné à `test_add`. Pourquoi la récupération précise du résultat est-elle essentielle dans le contexte des appels système ?**

   Réponse :  
   <espace pour réponse>