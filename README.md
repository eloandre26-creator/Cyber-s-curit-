# PHIS GUARD — Détecteur Pédagogique de Signaux de Phishing

**PHIS GUARD** est une application web académique et pédagogique d'initiation à la cybersécurité défensive et à la détection d'attaques par ingénierie sociale (hameçonnage / phishing).

---

## 🎯 Objectifs du Projet

Phis Guard permet à tout utilisateur d'analyser le contenu textuel d'un e-mail, d'un SMS, d'une adresse URL suspecte ou d'un mélange texte/URL afin d'identifier des motifs trompeurs récurrents.

L'application calcule :
- **Un score de risque de 0 à 100** calculé de façon transparente selon une grille heuristique pondérée.
- **Un niveau de risque qualifié** :
  - `0 à 29` : **RISQUE FAIBLE**
  - `30 à 59` : **RISQUE MODÉRÉ**
  - `60 à 100` : **RISQUE ÉLEVÉ**
- **Un rapport explicatif détaillé** listant chaque signal repéré, son explication pédagogique et ses points associés.
- **Des recommandations défensives ciblées** adaptées aux signaux observés.

---

## 🔍 Signaux Analysés & Grille de Pondération

| Famille de signal | Points | Exemples de déclencheurs |
| :--- | :---: | :--- |
| **A. Urgence et pression** | `+22` | *urgent, urgence, immédiatement, dernier avertissement, action requise, votre compte sera suspendu, bloqué dans 24h, maintenant* |
| **B. Informations sensibles / accès** | `+25` | *mot de passe, identifiant, code OTP, code de sécurité, connexion, login, confirmation de compte* |
| **C1. Présence d'un lien web** | `+10` | Présence d'une URL HTTP / HTTPS ou nom de domaine |
| **C2. Liens suspects ou trompeurs** | `+15` | Protocole HTTP non sécurisé, adresse IP brute (`192.168.x.x`), sous-domaines multiples, extensions inhabituelles (`.xyz`, `.top`, `.tk`), mots-clés (`login`, `secure`, `verify`, `account`, `support`, `confirm`, `update`) |
| **D. Promesses attractives / gains** | `+12` | *cadeau, gain, récompense, loterie, prix exceptionnel, offre limitée, félicitations* |
| **E. Services financiers & marques** | `+8` | *banque, paiement, PayPal, Visa, Mastercard, Orange Money, MTN Mobile Money, etc.* |
| **F. Appel direct à l'action (CTA)** | `+8` | *cliquez, cliquez ici, connectez-vous, vérifiez, confirmez, ouvrez le lien* |

> **Plafond strict :** Le score total est plafonné à 100.
> **Avertissement méthodologique :** Le score est une estimation heuristique. Ne jamais affirmer qu'un lien ou message est définitivement frauduleux (ou sûr) uniquement à partir de ce score.

---

## 🛡️ Confidentialité & Sécurité (Privacy-First)

- **Traitement 100% Côté Client (Browser-Only)** : Aucune donnée textuelle, aucune URL et aucun mot-clé saisi n'est transmis sur internet ou enregistré sur un serveur.
- **Sécurité contre les injections (XSS)** : Aucun contenu utilisateur n'est interprété via `innerHTML` ou `eval()`. L'affichage passe strictement par `textContent` et des méthodes sécurisées du DOM.
- **Aucune dépendance externe opaque** : Fonctionne sans framework lourd, sans API externe, sans clé d'API et sans base de données.

---

## 🚀 Déploiement sur Vercel

Le projet a été conçu pour un déploiement direct et sans accroc sur **Vercel** :

1. Importez le dépôt GitHub sur [Vercel](https://vercel.com).
2. Vercel détecte automatiquement la configuration dans `vercel.json` et exécute la commande de build statique.
3. L'application est immédiatement disponible en ligne en HTTPS avec des en-têtes de sécurité renforcés.

### Utilisation Locale
Il suffit d'ouvrir directement le fichier `index.html` dans n'importe quel navigateur moderne (Chrome, Firefox, Safari, Edge) par un simple double-clic, ou via un serveur local :
```bash
npx serve .
# ou
npm run dev
```

---

## 📁 Structure du Projet

```
├── /index.html       # Application complète autonome (HTML5, CSS3, JavaScript vanilla)
├── /vercel.json      # Configuration optimisée de déploiement Vercel
├── /README.md        # Documentation académique et guide d'utilisation
├── /package.json     # Scripts Vite & vérifications TypeScript
└── /metadata.json    # Métadonnées de l'application
```
