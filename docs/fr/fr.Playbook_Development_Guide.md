# Guide de développement de Playbook
Ce document est fourni à titre informatif uniquement. Il représente les offres de produits et les pratiques actuelles d'Amazon Web Services (AWS) à la date d'émission de ce document, qui peuvent être modifiées sans préavis. Les clients sont responsables de faire leur propre évaluation indépendante des informations contenues dans ce document et de toute utilisation des produits ou services AWS, chacun étant fourni « en l'état » sans garantie d'aucune sorte, expresse ou implicite. Ce document ne crée aucune garantie, représentation, engagement contractuel, condition ou assurance de la part d'AWS, de ses sociétés affiliées, de ses fournisseurs ou de ses concédants de licence. Les responsabilités et responsabilités d'AWS envers ses clients sont contrôlées par des accords AWS, et ce document ne fait pas partie ni ne modifie un accord entre AWS et ses clients.

© 2021 Amazon Web Services, Inc. ou ses sociétés affiliées. Tous droits réservés. Cette œuvre est sous licence Creative Commons Attribution 4.0 International License.

Ce contenu AWS est fourni sous réserve des termes de l'accord client AWS disponible à l'adresse http://aws.amazon.com/agreement ou d'un autre accord écrit entre le client et Amazon Web Services, Inc. ou Amazon Web Services EMEA SARL ou les deux.

## Playbook comme code :

* Les playbooks doivent être stockés au format markdown dans un référentiel git.
* Créez une version autonome imprimable de chaque playbook à partager avec ceux qui n'ont pas accès au référentiel git.
* Il est recommandé que les membres de l'équipe de réponse aux incidents soient autorisés à brancher le projet git et à cloner vers leur environnement local, tel que PC, VDI ou ordinateur portable.
* Lorsque des améliorations sont apportées à la branche, soumettez-les à l'examen, à l'approbation et à la fusion dans le master.
* Le projet git hébergera la documentation et le code.
* Envisagez d'utiliser le pipeline CD/CI pour faciliter la gouvernance et le déploiement du playbook.

## Structure du Playbook :

1. **Menace** : décrit la menace traitée par le playbook
2. **Endgame** : décrit les résultats souhaités pour le playbook en fonction de la perspective de sécurité du _ [*AWS Cloud Adoption Framework (CAF) *] (https://d0.awsstatic.com/whitepapers/AWS_CAF_Security_Perspective.pdf)_) et des modèles de sécurité acceptés par l'industrie, tels que l'évaluation de la vulnérabilité et l'analyse d'impact.
3. **Étapes de réponse** : fournit une procédure étape par étape dans l'ordre chronologique pour répondre à l'événement basé sur * [_NIST 800-61r2 - Computer Security Incident Response Guide_] (https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf) *. Reportez-vous à la figure A.
4. **Simulation** [**CODE**] : fournit une procédure étape par étape pour générer les indicateurs nécessaires au déclenchement de l'alerte déclenchant la réponse.
5. **Classification, gestion et détection** : catégorise le livre de lecture selon [*_MITRE ATT&CK_* tactiques d'entreprise] (https://attack.mitre.org/tactics/enterprise/), énumère les outils nécessaires à l'exécution du playbook, énumère les indicateurs (c.-à-d. résultats) utilisés pour la détection, générant l'alerte, journal les sources nécessaires pour générer des indicateurs et faciliter l'analyse, ainsi que les équipes concernées.
6. **Processus de gestion des incidents** : conseils prescriptifs à suivre pour chaque discipline de la réponse. Ils ne sont pas dans l'ordre chronologique d'exécution, ils sont à titre de référence lors du passage à **3. Étapes de réponse**. Tout au long du processus de réponse, il est important de documenter toutes les actions effectuées et de centraliser toutes les preuves collectées dans un référentiel connu avec des droits appropriés basés sur l'équipe de réponse aux incidents RACI. Il est également essentiel de disposer de canaux de communication appropriés pendant la réponse avec des capacités d'orchestration centralisées, qui permettront aux membres de l'équipe de réponse aux incidents de se concentrer sur leurs tâches au sein de leurs spécialités. La fonction d'orchestration centralisée maintiendra les communications adéquates et veillera à ce que toutes les activités requises soient exécutées avec une connaissance et une approbation commerciales.
1. **Analyse - validation d'alerte** : Le contenu de la notification de l'alerte doit être vérifié directement par rapport aux indicateurs générateurs de source (c.-à-d. « vérité au sol »). Cela est nécessaire pour au moins deux raisons. Premièrement, en général, les indicateurs originaux sont transformés au fur et à mesure qu'ils circulent dans différents systèmes jusqu'à ce qu'ils atteignent l'équipe d'intervention en cas d'incident, ce qui pourrait entraîner une modification involontaire des données sur les incidents critiques. Deuxièmement, la notification aurait pu être générée en raison d'une erreur de configuration machine ou humaine.
2. **Analyse - Triage des alertes** : Sur la base des indicateurs présentés par l'alerte, recherchez les journaux utilisés pour générer un contexte de construction afin de faciliter l'analyse.
3. **Analyse - étendue** : Recherchez des preuves dans les sources de journaux disponibles et associées aux alertes pour déterminer l'activité que l'acteur a exécutée tout au long du cycle de vie de l'événement.
4. **Analyse - Impact** : Déterminez les charges de travail et les composants qui ont été affectés par l'activité de l'acteur et son étendue. Formulez une hypothèse pour discuter avec la grande équipe d'intervention en cas d'incident afin de déterminer l'impact sur l'entreprise et de prioriser les prochaines étapes.
5. **Confinement :** Déterminez la stratégie de confinement de l'incident pendant la progression ou la fin de la phase d'analyse. La stratégie appropriée dépend de la portée et de l'impact, et elle est approuvée par les propriétaires de charges de travail. Les activités de confinement doivent être alignées sur la modélisation des menaces de la charge de travail affectée et le contexte réel pendant la réponse à l'incident. Quelques options de confinement différentes ou complémentaires devraient être disponibles pour minimiser les effets collatéraux possibles, tels que les temps d'arrêt, la destruction des données, à la suite d'actions de confinement. Au cours de cette phase, les précautions nécessaires lors de la collecte des preuves doivent être suivies. Bien que l'agrégation de données médico-légale ait commencé pendant l'analyse, par exemple les journaux CloudTrail, les journaux de flux VPC et les journaux GuardDuty, c'est le moment le plus approprié pour les instantanés et les sauvegardes, car les services sont reconfigurés pour empêcher toute autre activité, par exemple les instantanés d'instance EC2, les sauvegardes de bases de données RDS et le déclencheur Lambda enlèvement.
6. **Eradication & Recovery** : Les ressources provisionnées par l'adversaire sont désactivées ou complètement supprimées, et les vulnérabilités et les problèmes de configuration de toutes les ressources affectées sont identifiés. Après l'approbation du propriétaire de la charge de travail, toutes les ressources sont correctement reconfigurées et des mises à jour de sécurité sont appliquées pour réduire la probabilité de succès résultant d'exploits identiques ou similaires. La réévaluation de la posture de sécurité de la charge de travail est terminée. Une fois les modifications de configuration et les mises à jour de sécurité appliquées, si la posture de sécurité de la charge de travail présente toujours un niveau de risque inacceptable pour l'entreprise, les recommandations relatives aux modifications architecturales à moyen et long terme doivent être rédigées et soumises pour évaluation par les équipes responsables et responsables.
7. **Activité post-incidence** : Une fois toutes les phases précédentes terminées, une analyse approfondie de l'incident est effectuée sous la forme de sessions « leçons apprises ». Le calendrier de réponse aux incidents est publié et discuté en se concentrant sur les changements qui doivent être apportés pour améliorer la préparation au prochain incident de sécurité. Au cours de cette phase, l'équipe de réponse aux incidents se concentre sur l'amélioration des contrôles de directive, de prévention, de détection et de réponse (voir figure B) non seulement pour la charge de travail affectée, mais pour toutes les charges de travail détenues par l'entreprise.

! [Image] (/images/nist_life_cycle.png)

**Figure A - Cycle de vie de la réponse aux incidents


! [Image] (/images/image-caf-sec.png)

**Figure B - Perspective de sécurité de l'infrastructure AWS Cloud Adoption Framework**

## Processus de développement :

1. Sélectionnez la menace que le playbook va traiter et décrivez-la dans le `````1. Section Menace ```. Fournissez autant de références que nécessaire pour aider le lecteur de livres de lecture à le comprendre.
2. Consultez la section du modèle de livre de lecture ```2. Section``` de fin du jeu et apportez des modifications ou conservez tel quel. Ceux-ci sont basés sur des modèles de sécurité et d'industrie AWS tels que [Perspective de sécurité de la CAF] (https://d0.awsstatic.com/whitepapers/AWS_CAF_Security_Perspective.pdf), [pilier de sécurité d'AWS Well-Architected Framework] (https://d1.awsstatic.com/whitepapers/architecture/AWS-Security-Pillar.pdf), [Amazon Services Web : présentation des processus de sécurité] (https://d0.awsstatic.com/whitepapers/aws-security-whitepaper.pdf), [Guide de réponse aux incidents de sécurité AWS] (https://d1.awsstatic.com/whitepapers/aws_security_incident_response.pdf) et [NIST Special Publication 800-61r2 Computer Security Incident Handling Guide] ( https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf).
3. Remplissez la section ```5. Classification, gestion et détection des incidents avec les informations appropriées. Vous pouvez revenir à cette section plus tard, si, au cours de la création d'autres sections du playbook, vous découvrirez de nouveaux indicateurs, d'autres outils que vous voudrez peut-être utiliser, etc.
4. Définissez les étapes pour déclencher les indicateurs de la menace. Documentez le processus, les ressources AWS, le principal IAM, les politiques et le code requis, tels que les commandes AWS CLI, le code basé sur AWS SDK, de préférence encapsulé dans un script shell ou un programme de code de langue pris en charge. Ajoutez des captures d'écran illustrant les différents journaux générés par l'activité de simulation à l'aide d'un outil analytique tel que CloudWatch Insights ou Athena.
5. Élaborez les étapes de réponse sous la section ```3. Section des étapes de réponse``` mettant en évidence la phase du cycle de vie NIST IR à laquelle chaque étape appartient. Les étapes doivent être énumérées dans l'ordre chronologique aligné sur le modèle de menace de la charge de travail affectée. Indiquez clairement dans le playbook que l'ordre chronologique n'est pas immuable et peut être modifié en fonction du contexte de l'événement. Il est recommandé que tout écart par rapport à l'ordre d'exécution établi soit soumis à un processus de vérification préalablement approuvé, afin de minimiser le risque d'actions susceptibles d'endommager davantage la charge de travail affectée.
6. Créez des commandes AWS CLI et des requêtes Athena qui prennent en charge chaque phase du cycle de vie NIST IR dans la section ````6. Processus de gestion des incidents ```. La série de requêtes et de commandes doit répondre aux exigences de chaque phase d'un point de vue général et sa sortie doit être documentée sous forme de captures d'écran. Les commandes sont exécutées sur le compte affecté à l'aide d'un rôle similaire ou égal aux droits du répondeur d'incident. Les requêtes sont exécutées sur les référentiels de journaux associés avec Athena, au minimum, les journaux CloudTrail et VPC Flow. Si les journaux à analyser ne sont pas disponibles via Athena, utilisez l'outil analytique disponible, tel qu'une solution SIEM ou Big Data.