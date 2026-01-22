# **Démarrage avec Antigravity Awesome Skills**

**Nouveau ici ? Ce guide vous aidera à comprendre et utiliser ce dépôt en 5 minutes \!**

---

## **🤔 Qu'est-ce qu'une "Skill" ?**

Pensez aux skills comme des **manuels d'instructions spécialisés** pour les assistants de codage IA.

**Analogie simple :** Tout comme vous pourriez embaucher différents experts (un designer, un expert en sécurité, un marketeur), ces skills permettent à votre assistant IA de devenir un expert dans des domaines spécifiques quand vous en avez besoin.

---

## **📦 Que contient ce dépôt ?**

Ce dépôt contient **233 skills prêtes à l'emploi** organisées dans le dossier `skills/`. Chaque skill est un dossier contenant au moins un fichier : `SKILL.md`

skills/  
├── brainstorming/  
│   └── SKILL.md          ← La définition de la skill  
├── stripe-integration/  
│   └── SKILL.md  
├── react-best-practices/  
│   └── SKILL.md  
└── ... (176 skills supplémentaires)

---

## **Comment fonctionnent les Skills ?**

### **Étape 1 : Installer les Skills**

Copiez les skills dans le répertoire de votre outil IA :

\# Pour la plupart des outils IA (Claude Code, Gemini CLI, etc.)  
git clone https://github.com/sickn33/antigravity-awesome-skills.git .agent/skills

### **Étape 2 : Utiliser une Skill**

Dans votre chat IA, mentionnez la skill :

@brainstorming aide-moi à concevoir une application todo

ou

/stripe-integration ajoute un traitement des paiements à mon application

### **Étape 3 : L'IA devient un Expert**

L'IA charge les connaissances de cette skill et vous aide avec une expertise spécialisée \!

---

## **Quels outils IA fonctionnent avec ceci ?**

| Outil | Compatible ? | Chemin d'installation |
| ----- | ----- | ----- |
| **Claude Code** | ✅ Oui | `.claude/skills/` ou `.agent/skills/` |
| **Gemini CLI** | ✅ Oui | `.gemini/skills/` ou `.agent/skills/` |
| **Cursor** | ✅ Oui | `.cursor/skills/` |
| **GitHub Copilot** | ⚠️ Partiel | Copier dans `.github/copilot/` |
| **Antigravity IDE** | ✅ Oui | `.agent/skills/` |

---

## **Catégories de Skills (Simplifiées)**

### **Créatif & Design (10 skills)**

Créez de belles choses : design UI, art, thèmes, composants web

* Essayez : `@frontend-design`, `@canvas-design`, `@ui-ux-pro-max`

### **Développement (25 skills)**

Écrivez un meilleur code : tests, débogage, patterns React, architecture

* Essayez : `@test-driven-development`, `@systematic-debugging`, `@react-best-practices`

### **Sécurité (50 skills)**

Outils de hacking éthique et tests de pénétration

* Essayez : `@ethical-hacking-methodology`, `@burp-suite-testing`

### **IA & Agents (30 skills)**

Construisez des applications IA : RAG, LangGraph, prompt engineering, agents vocaux

* Essayez : `@rag-engineer`, `@prompt-engineering`, `@langgraph`

### **Documents (4 skills)**

Travaillez avec des fichiers Word, Excel, PowerPoint, PDF

* Essayez : `@docx-official`, `@xlsx-official`, `@pdf-official`

### **Marketing (23 skills)**

Développez votre produit : SEO, rédaction, publicités, campagnes email

* Essayez : `@copywriting`, `@seo-audit`, `@page-cro`

### **Intégrations (25 skills)**

Connectez-vous aux services : Stripe, Firebase, Twilio, Discord, Slack

* Essayez : `@stripe-integration`, `@firebase`, `@clerk-auth`

---

## **Votre première Skill : Un exemple rapide**

Essayons la skill **brainstorming** :

1. **Ouvrez votre assistant IA** (Claude Code, Cursor, etc.)

**Tapez ceci :**

 @brainstorming Je veux créer une simple application météo

2.   
3. **Ce qui se passe :**

   * L'IA charge la skill brainstorming  
   * Elle vous pose des questions une par une  
   * Elle vous aide à concevoir l'application avant de coder  
   * Elle crée un document de conception pour vous  
4. **Résultat :** Vous obtenez un plan bien pensé au lieu de vous lancer directement dans le code \!

---

## **Comment trouver la bonne Skill**

### **Méthode 1 : Parcourir par catégorie**

Consultez le [Registre complet des Skills](https://claude.ai/chat/README.md#full-skill-registry-233233) dans le README principal

### **Méthode 2 : Rechercher par mot-clé**

Utilisez votre explorateur de fichiers ou terminal :

\# Trouver des skills liées aux "tests"  
ls skills/ | grep test

\# Trouver des skills liées à "auth"  
ls skills/ | grep auth

### **Méthode 3 : Consulter l'index**

Consultez `skills_index.json` pour une liste lisible par machine

---

## **🤝 Vous voulez contribuer ?**

Génial \! Voici comment :

### **Option 1 : Améliorer la documentation**

* Rendre les README plus clairs  
* Ajouter plus d'exemples  
* Corriger les fautes ou les parties confuses

### **Option 2 : Créer une nouvelle Skill**

Consultez notre [CONTRIBUTING.md](https://claude.ai/chat/CONTRIBUTING.md) pour des instructions étape par étape

### **Option 3 : Signaler des problèmes**

Vous avez trouvé quelque chose de confus ? [Ouvrez un ticket](https://github.com/sickn33/antigravity-awesome-skills/issues)

---

## **❓ Questions fréquentes**

### **Q : Dois-je installer les 233 skills ?**

**R :** Non \! Clonez l'ensemble du dépôt, et votre IA ne chargera les skills que lorsque vous les utiliserez.

### **Q : Puis-je créer mes propres skills ?**

**R :** Oui \! Consultez la skill `@skill-creator` ou lisez [CONTRIBUTING.md](https://claude.ai/chat/CONTRIBUTING.md)

### **Q : Que faire si mon outil IA n'est pas listé ?**

**R :** S'il prend en charge le format `SKILL.md`, essayez `.agent/skills/` \- c'est le chemin universel.

### **Q : Ces skills sont-elles gratuites ?**

**R :** Oui \! Licence MIT. Utilisez-les comme vous le souhaitez.

### **Q : Les skills fonctionnent-elles hors ligne ?**

**R :** Les fichiers de skills sont locaux, mais votre assistant IA a besoin d'internet pour fonctionner.

---

## **Prochaines étapes**

1. ✅ Installez les skills dans votre outil IA  
2. ✅ Essayez 2-3 skills de différentes catégories  
3. ✅ Lisez [CONTRIBUTING.md](https://claude.ai/chat/CONTRIBUTING.md) si vous voulez aider  
4. ✅ Mettez une étoile au dépôt si vous le trouvez utile \! ⭐

---

## **💡 Astuces Pro**

* **Commencez avec `@brainstorming`** avant de construire quoi que ce soit de nouveau  
* **Utilisez `@systematic-debugging`** quand vous êtes bloqué sur un bug  
* **Essayez `@test-driven-development`** pour écrire un meilleur code  
* **Explorez `@skill-creator`** pour créer vos propres skills

---

**Toujours confus ?** Ouvrez un ticket et nous vous aiderons \! 🙌

**Prêt à aller plus loin ?** Consultez le [README.md](https://claude.ai/chat/README.md) principal pour la liste complète des skills.

