# these-doctorat-TOTI-Anicet
# Scoring de crédit explicable pour l'inclusion financière

**Modélisation du risque de crédit pour l'amélioration de l'inclusion financière dans une banque commerciale en contexte africain post-crise**
*Approche fondée sur le scoring comportemental, l'intelligence artificielle explicable et l'intégration de données externes (sectorielles et télécoms)*

Thèse de doctorat (Executive Doctorate of Engineering) – ISAE ISM Paris – soutenue le 10 octobre 2026
Auteur : **Dr Tchétché Anicet TOTI**

---

## 🎯 La question

> Comment modéliser le risque de crédit dans une banque commerciale post-crise pour, à la fois, assurer un scoring **justifiable** et **recalibrable**, et améliorer **durablement** l'inclusion financière des populations non ou mal bancarisées ?

Les modèles importés des marchés matures, fondés sur des historiques longs et des revenus documentés, déclarent « non scorable » une grande partie de la population africaine. **Hypothèse de travail :** sécurité et inclusion ne s'opposent pas. Leur opposition vient d'un manque d'information sur l'emprunteur.

## 🧩 L'approche

Quatre couches de données, combinées progressivement dans **six configurations (M1 à M6)** pour isoler l'apport de chaque source :

| Couche | Source | Exemples de variables |
|---|---|---|
| 1. Financière | Banque commerciale (zone CEMAC) | Montant, durée, taux, secteur, retard moyen de paiement |
| 2. Comportementale (CRM) | Banque commerciale | Score CRM à 8 dimensions : usage numérique, engagement, ancienneté, fidélité… |
| 3. Sectorielle | BEAC | Croissance, confiance, indicateur de crise |
| 4. Télécoms | Opérateur mobile | Usage du mobile money, régularité et montant des recharges, ancienneté de ligne |

- **Modèle :** Random Forest (paramètres identiques de M1 à M6), comparé à Gradient Boosting, régression logistique (WoE) et arbre unique
- **Explicabilité :** SHAP global et local, restitué à 3 niveaux (technique, analyste, client)
- **Protocole :** 5 928 dossiers de crédit, 2 229 clients, période 2017–2025 ; test stratifié de 30 % ; validation hors période ; appariement pseudonymisé (SHA-256)

## 📊 Résultats clés

| Configuration | AUC |
|---|---|
| Données financières seules | 0,592 |
| Financier + comportemental (modèle interne) | 0,660 |
| + données sectorielles (BEAC) | 0,709 |
| **+ données télécoms (modèle complet)** | **0,768** (IC 95 % : 0,737–0,799) |

- **+10,8 points d'AUC** par rapport au modèle interne (p < 0,001)
- **62 % des clients refusés** par le modèle interne requalifiés, avec un taux de défaut comparable (16,0 % contre 14,9 %)
- **+29 % de dossiers acceptés** au total
- Les **données télécoms** pèsent le plus : 41,4 % de l'importance des 15 premières variables
- Performance du même ordre que les solutions africaines publiées (0,70–0,75)
- **Hypothèses :** 5 soutenues sur 7, 2 partiellement (dont une alerte d'équité pour les travailleurs informels)

> *« L'exclusion du crédit est d'abord une conséquence de l'invisibilité statistique, et non de l'insolvabilité. »*

## 📁 Contenu du dépôt

```
├── these/            # Document de thèse et présentation de soutenance (PDF)
├── data/             # Données SYNTHÉTIQUES (même structure que les données réelles)
├── notebooks/        # Exploration, modélisation M1–M6, analyses SHAP
├── src/              # Préparation des données, entraînement, évaluation
├── figures/          # Courbes ROC, importance des variables, exemples SHAP
└── requirements.txt
```

### ⚠️ Données

Les données réelles (bancaires et télécoms) sont **confidentielles** et ne sont pas publiées. Le dossier `data/` contient un **jeu de données synthétique** qui reproduit leur structure, pour que le code puisse être exécuté. Les résultats obtenus sur ces données fictives ne reproduisent pas ceux de la thèse.

## 🚀 Lancer le projet

```bash
git clone https://github.com/TOTI-Anicet/credit-scoring-ia-explicable.git
cd credit-scoring-ia-explicable
pip install -r requirements.txt
jupyter notebook notebooks/
```

## 🔭 Limites et perspectives

- Un seul établissement, un seul pays et un seul opérateur télécoms : la généralisation à la zone CEMAC reste à tester
- Une baisse de performance hors période (0,724) justifie le recalibrage trimestriel prévu
- Pistes : extension multi-opérateurs, réplication multi-pays, évaluation de l'impact social

## 📬 Contact

**Dr Tchétché Anicet TOTI** · [LinkedIn](https://www.linkedin.com/in/dr-anicet-toti-pmp) · totianicet7@gmail.com
