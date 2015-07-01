# Note #

Free is a French FAI providing SIP / VoIP account linked to the internet subscription. This guide should be useless for most people not living in France. That's why this in untranslated.

# Introduction #

Free est un FAI français qui fourni à ses abonnés un compte SIP lié à leur compte de téléphonie fixe.

Il leur est donc possible d'utiliser leur compte SIP pour effectuer des appels aux même tarifs que ceux de leur téléphone lié à leur Freebox (à savoir gratuit vers les fixes et vers les destinations fixes de certains pays).

Mais pas seulement, il est également possible de reçevoir les appels de sa ligne fixe sur son compte SIP.

CSipSimple étant un logiciel supportant le protocole SIP, vous pouvez utiliser votre compte SIP sur votre mobile android.


# Préparation de votre compte Free #

Il vous faut tout d'abord activer le SIP pour votre compte freephonie.

  * Connectez vous sur votre interface Free et allez dans l'interface liée à la Téléphonie :
![http://csipsimple.googlecode.com/svn/graphics/Freephonie_1.png](http://csipsimple.googlecode.com/svn/graphics/Freephonie_1.png)
  * Dans la **Gestion de mon compte SIP** entrez un mot de passe et cochez Service activée
![http://csipsimple.googlecode.com/svn/graphics/Freephonie_2.png](http://csipsimple.googlecode.com/svn/graphics/Freephonie_2.png)

Vous noterez ici qu'il y a deux façon de reçevoir les appels. Vous pouvez choisir de les reçevoir sur votre téléphone fixe connecté à votre freebox ou sur le téléphone SIP.

Vous pourrez dans tous les cas utiliser votre compte SIP pour les appels sortant.

Sauvegardez.

# Installation de CSipSimple #
Vous pouvez installer CSipSimple depuis l'android Market, l'AppsLib ou depuis ce site web.

Une fois l'application installée lancez là.

Il faut avoir une connection data (wifi ou 3G) activée lors du premier lancement.

L'application va télécharger la version de la librairie SIP optimale pour votre téléphone patientez pendant cette étape - vous pouvez lire le texte de bienvenue au dessus : ça aide toujours de lire ce que les concepteurs du logiciel veulent que vous lisiez.

Une fois que l'installation de la librairie est effectuée, vous pouvez cliquer sur le bouton "Suivant" qui apparait en bas.

# Configuration de base #

  * Vous arrivez sur une interface de configuration rapide de l'application. Vous pourrez y choisir :
    * Si vous voulez que l'application s'intègre intelligement dans Android (lorsque vous utiliserez le numéroteur Android, il vous sera proposé d'utiliser un compte SIP ou un compte GSM).
    * Votre politique d'activation de CSipSimple :
      * Toujours disponible : vous voulez que CSipSimple soit disponible au maximum possible pour recevoir vos appels entrant. Ca consomme plus de batterie mais ça essaie autant que faire ce peux que vous receviez vos appels.
      * Disponible sur Wifi : vous serez disponible lorsque le wifi sera activé sur le téléphone (en fait quand on est pas autorisé à utiliser le SIP en 3G, ce qui est le cas en France), ça correspond à la même chose que précedemment sauf que CSipSimple ne verouille pas le Wifi, donc si votre politique de veille wifi est de s'éteindre lorsque l'écran s'éteind, CSipSimple risque de ne pas reçevoir les appels lorsque l'écran est éteint.
      * Uniquement pour les appels sortant : Impact quasi nul sur la batterie, puisque l'application n'esserai pas de rester active toute seule. Elle ne se lance en **tache de fond** (attention tache de fond = service qui tourne c'est different d'être listé dans les task manager, qu'il ne faut pas croire !!!!! ) uniquement que lorsque vous initiez un appel. Si vous avez choisi dans votre interface Freephonie de ne pas rediriger les appels entrant vers le SIP, c'est la bonne option !
    * Une coche qui vous permet de dire que vous être autorisé à utiliser la 3G pour passer des appels VoIP. Pour info pour les français : SFR et Bouygues interdisent dans leur contrat cette utilisation et bloquent le traffic SIP... donc n'y comptez pas... Faites une pétition auprès des opérateurs, mais l'application n'y peux absolument rien. Chez Orange il existe une option (assez cher) qui permet cette utilisation de façon légale.

Une fois que vous avez selectionné les options qui correspondent à ce que vous voulez, vous pouvez cliquer sur Enregistrer.

Vous devez alors atterir sur la page de création d'un compte.

  * Cliquez sur **"Ajouter un compte"**
  * Une liste d'assistant disponible apparait; choisissez "Freephonie"
![http://csipsimple.googlecode.com/svn/graphics/Freephonie_3.png](http://csipsimple.googlecode.com/svn/graphics/Freephonie_3.png)![http://csipsimple.googlecode.com/svn/graphics/Freephonie_4.png](http://csipsimple.googlecode.com/svn/graphics/Freephonie_4.png)

  * Remplissez alors votre numéro de téléphone => Attention il s'agit de votre numéro de téléphone Freephonie (il peut être différent de votre numéro de téléphone fixe)
  * Remplissez votre mot de passe **SIP** => Il s'agit ici du mot de passe que vous aurez rentré dans le chapitre précédent (et **NON** du mot de passe de votre compte free)
  * Cliquez sur enregistrer...
  * Ca devrait s'enregistrer auprès de Freephonie cliquez sur le bouton retour pour revenir sur l'écran de numérotation.

Voilà vous pouvez désormais passer des appels. Par exemple testez la boite vocale (`**`1)...


# Vous en voulez plus? #
CSipSimple est livrée avec un outil puissant de filtrage/réécriture de numéro de téléphone.
Dans le cas de freephonie ça peut être un outil très interessant à utiliser.

Vous aurez noter que pour l'instant si vous utiliser la numérotation depuis une fiche contact ou l'application native android, CSipSimple va vous proposer un popup pour choisir quel compte utiliser pour passer cet appel....

Ca serait bien de pouvoir par exemple utiliser Freephonie dès que le numéro commence par 04 par exemple, d'ignorer le choix Freephonie (et passer directement par le GSM) si ça commence par 06 et de demander pour les autres numéros....

Et bien... CSipSimple permet de faire ça !

Comment :
  * Ouvrez CSipSimple
  * Appuyez sur le bouton menu de votre téléphone puis choisissez Comptes
  * Cliquez sur la ligne correspondant à Freephonie
  * Vous être maintenant dans l'édition du compte ... Cliquez sur "Menu" et choisissez **"Filtres"**
  * Vous arrivez dans l'interface de gestion des filtres pour ce compte.
  * Cliquez sur **Ajouter une règle**
  * Là on va choisir "Ne pas appeler" et en dessous "Commence avec" et encore en dessous 06. Enregistrer
Ca y est => Dès que vous effecturez un appel depuis les applications native android, ce compte sera ignoré des proposition qui vous seront faites.
  * Vous pouvez ajouter une autre règle !
  * "Appeler automatiquement" "Commence avec" 04 => Dès que vous effecturez un appel vers un numéro en 04 **et que votre connection data le permettra** On utilisera automatiquement le SIP !!
