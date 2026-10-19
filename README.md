# A.X.I.S – RedFlame Protection (projet intégré)

Application Qt/C++ unique regroupant les 4 modules :
Employés (+ connexion et congés), Interventions, **Véhicules**, Matériels.

## Compilation
- Qt 5.15+ ou Qt 6 (Widgets, Sql, Network – driver QSQLITE inclus avec Qt), compilateur C++17.
- **Qt Creator** : ouvrir `AXIS.pro` (qmake), puis Compiler / Exécuter.
- Après avoir ajouté ces fichiers : *Build > Nettoyer tout*, puis *Exécuter qmake*, puis *Reconstruire*.

## Droits d'accès (menu principal)
| Module        | Rôles autorisés                      |
|---------------|--------------------------------------|
| Employés      | Administrateur, Chef de caserne      |
| Interventions | Opérateur de dispatch, Chef de caserne |
| Véhicules     | Chef de caserne, Administrateur      |
| Matériels     | Magasinier, Chef de caserne          |

## Module Véhicules (intégré)
- Fichiers : `vehiclespage.*`, `vehicledonutwidget.*`, `vehicletheme.h`.
- Page branchée dans `axis.cpp` (page `PVehicule` du `SWAxis`), avec la barre latérale commune
  (`sidebar.*`) : boutons « Menu principal » / « Déconnexion » + utilisateur connecté.
- Données : `vehicules.json` dans le dossier AppData de l'application (comme avant, pas de base SQL).
  Au premier lancement, les véhicules saisis dans l'ancienne version autonome (dossier `AXIS`) sont repris.
- Le widget en anneau a été renommé `VehicleDonutWidget` : `DonutWidget` existait déjà dans `charts.h`
  (module Matériels) et provoquait un conflit à l'édition de liens.

## Données
Base SQLite `axis.db` créée au premier lancement dans AppData (organisation « RedFlame », application « Caserne »).
