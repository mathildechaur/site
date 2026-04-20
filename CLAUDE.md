## Project Configuration

- **Language**: TypeScript
- **Package Manager**: pnpm
- **Add-ons**: tailwindcss

---

# Projet Site — Instructions

## Stack technique

- **Framework** : SvelteKit
- **CSS** : Tailwind CSS
- **Package manager** : pnpm
- **Langage** : TypeScript

## Règles de développement

### Structure
- Respecter la structure de dossiers SvelteKit : `src/routes/`, `src/lib/`, `src/components/`
- Les composants réutilisables vont dans `src/lib/components/`
- Les utilitaires et helpers vont dans `src/lib/utils/`

### Style
- Utiliser exclusivement Tailwind CSS pour le style — pas de CSS custom sauf cas exceptionnel
- Pas de fichiers `.css` séparés (sauf `app.css` pour les directives Tailwind)
- Privilégier les classes utilitaires Tailwind directement dans les templates

### SvelteKit
- Utiliser les `load` functions pour le fetch de données (pas de fetch dans `onMount`)
- Préférer le rendu serveur (SSR) par défaut
- Nommer les fichiers de routes selon la convention SvelteKit : `+page.svelte`, `+layout.svelte`, `+page.server.ts`, etc.

### TypeScript
- Typer toutes les fonctions et variables explicitement
- Pas de `any` — utiliser des types précis ou `unknown` si nécessaire
- Définir les types/interfaces dans `src/lib/types.ts`

### Commandes
```bash
pnpm dev        # démarrer le serveur de dev
pnpm build      # build de production
pnpm preview    # prévisualiser le build
pnpm check      # vérifier les types TypeScript
```
