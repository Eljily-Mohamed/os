Le code de l'utilisateur est déjà implémenté dans main.c, nous allons seulement compléter les appels système.

    Dans oslib, l'appel système test_add effectuera une addition ; main_test contient plusieurs appels système.

    svc contient un gestionnaire pour la gestion des interruptions.

    Dans kernel, nous allons implémenter la création des tâches et des sémaphores. Le code dans kernel s'exécute en mode System Handler.

    Le code dans device s'exécute en mode utilisateur.

    test_add effectue un appel système avec les paramètres (value1, value2).

    Pour ipsr :
        Pas de faute : mode utilisateur.
        Mode handler sans faute : mode utilisateur.
        Faute (0x11) : mode système.