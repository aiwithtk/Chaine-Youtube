# Guide Pratique : Créer un Site E-commerce avec Stitch

## Projet : LuxeMode - Boutique de Mode en Ligne

Création complète d'un site e-commerce React pour une boutique de vêtements haut de gamme, de l'idée à la démo vidéo.

---

## Table des Matières

1. [Workflow Complet E-commerce](#workflow-complet-e-commerce)
2. [Étape 1 : enhance-prompt - Définir le Concept](#étape-1--enhance-prompt---définir-le-concept)
3. [Étape 2 : stitch-loop - Générer Toutes les Pages](#étape-2--stitch-loop---générer-toutes-les-pages)
4. [Étape 3 : react-components - Convertir en React](#étape-3--react-components---convertir-en-react)
5. [Étape 4 : shadcn-ui - Enrichir les Composants](#étape-4--shadcn-ui---enrichir-les-composants)
6. [Étape 5 : design-md - Documenter le Design](#étape-5--design-md---documenter-le-design)
7. [Étape 6 : remotion - Vidéo Démo E-commerce](#étape-6--remotion---vidéo-démo-e-commerce)
8. [Résultat Final](#résultat-final)
9. [Commandes Complètes](#commandes-complètes)
10. [Optimisations E-commerce](#optimisations-e-commerce)

---

## Workflow Complet E-commerce

Ce guide présente un workflow en 6 étapes pour créer un site e-commerce complet avec les outils Stitch.

### Étapes du Workflow

1. Idée E-commerce initiale
2. **enhance-prompt** : Affiner et détailler le concept
3. **stitch-loop** : Générer toutes les pages automatiquement
4. **react-components** : Convertir en application React
5. **shadcn-ui** : Enrichir les composants UI
6. **design-md** : Documenter le système de design
7. **remotion** : Créer la vidéo de démonstration
8. Site E-commerce complet et fonctionnel

---

## Étape 1 : enhance-prompt - Définir le Concept

### Prompt Initial

```
Je veux créer un site e-commerce pour vendre des vêtements de luxe
```

### Commande

```bash
@enhance-prompt Je veux créer un site e-commerce pour vendre des vêtements de luxe
```

### Prompt Optimisé Généré

Le skill `enhance-prompt` transforme votre idée vague en un prompt détaillé incluant :

**Design System**
- Style : Luxueux, minimaliste, épuré avec beaucoup d'espace blanc
- Palette : Noir (#000000), Blanc cassé (#FAFAFA), Or (#D4AF37), Gris clair (#E5E5E5)
- Typographie : Playfair Display (titres), Inter (corps)
- Arrondis : Minimaux (4px)
- Espacement : Système basé sur 16px

**Pages Requises**
1. Homepage (Hero, Nouveautés, Collections, Newsletter, Footer)
2. Catalogue/Shop (Filtres, Grille produits, Tri, Pagination)
3. Page Produit (Galerie, Sélecteurs, Avis, Produits similaires)
4. Panier (Liste produits, Résumé commande, Codes promo)
5. Checkout (3 étapes : Livraison, Mode de livraison, Paiement)
6. Compte Client (Dashboard, Commandes, Wishlist, Paramètres)

**Composants UI Spécifiques**
- ProductCard avec badges, wishlist, quick view
- Filtres avec accordéons et range slider
- MiniCart dropdown
- Animations d'ajout au panier

**Interactions Clés**
- Ajout au panier avec animation
- Wishlist toggle
- Zoom image produit
- Filtres temps réel
- Toast notifications

---

## Étape 2 : stitch-loop - Générer Toutes les Pages

### Commande

```bash
@stitch-loop Crée toutes les pages de LuxeMode avec le design premium défini
```

### Structure Générée

```
luxemode-stitch/
├── screens/
│   ├── 01-homepage.html
│   ├── 02-catalog.html
│   ├── 03-product-detail.html
│   ├── 04-cart.html
│   ├── 05-checkout-step1.html
│   ├── 05-checkout-step2.html
│   ├── 05-checkout-step3.html
│   └── 06-account.html
├── screenshots/
│   ├── homepage.png
│   ├── catalog.png
│   ├── product-detail.png
│   ├── cart.png
│   ├── checkout.png
│   └── account.png
└── project-info.json
```

---

## Étape 3 : react-components - Convertir en React

### Commande

```bash
@react-components Convertis toutes les pages LuxeMode en application React e-commerce complète avec routing et state management
```

### Architecture React Générée

```
luxemode-app/
├── src/
│   ├── components/
│   │   ├── layout/
│   │   │   ├── Header.tsx
│   │   │   ├── Footer.tsx
│   │   │   ├── Navigation.tsx
│   │   │   └── MobileMenu.tsx
│   │   ├── product/
│   │   │   ├── ProductCard.tsx
│   │   │   ├── ProductGrid.tsx
│   │   │   ├── ProductGallery.tsx
│   │   │   ├── ProductInfo.tsx
│   │   │   ├── SizeSelector.tsx
│   │   │   ├── ColorSelector.tsx
│   │   │   └── QuantitySelector.tsx
│   │   ├── cart/
│   │   │   ├── CartItem.tsx
│   │   │   ├── CartSummary.tsx
│   │   │   ├── MiniCart.tsx
│   │   │   └── PromoCode.tsx
│   │   ├── checkout/
│   │   │   ├── CheckoutProgress.tsx
│   │   │   ├── ShippingForm.tsx
│   │   │   ├── ShippingOptions.tsx
│   │   │   ├── PaymentForm.tsx
│   │   │   └── OrderSummary.tsx
│   │   ├── filters/
│   │   │   ├── FilterSidebar.tsx
│   │   │   ├── PriceRange.tsx
│   │   │   ├── CategoryFilter.tsx
│   │   │   └── ColorFilter.tsx
│   │   └── ui/
│   │       ├── Button.tsx
│   │       ├── Badge.tsx
│   │       ├── Input.tsx
│   │       ├── Select.tsx
│   │       ├── Toast.tsx
│   │       └── Modal.tsx
│   ├── hooks/
│   │   ├── useCart.ts
│   │   ├── useWishlist.ts
│   │   ├── useFilters.ts
│   │   ├── useProducts.ts
│   │   └── useCheckout.ts
│   ├── context/
│   │   ├── CartContext.tsx
│   │   ├── WishlistContext.tsx
│   │   └── AuthContext.tsx
│   ├── data/
│   │   ├── products.ts
│   │   ├── categories.ts
│   │   └── mockData.ts
│   ├── pages/
│   │   ├── HomePage.tsx
│   │   ├── CatalogPage.tsx
│   │   ├── ProductPage.tsx
│   │   ├── CartPage.tsx
│   │   ├── CheckoutPage.tsx
│   │   └── AccountPage.tsx
│   ├── utils/
│   │   ├── formatPrice.ts
│   │   ├── calculateTotal.ts
│   │   └── validation.ts
│   └── App.tsx
├── tailwind.config.js
└── package.json
```

### Exemple : ProductCard Component

```tsx
interface ProductCardProps {
  readonly id: string;
  readonly name: string;
  readonly price: number;
  readonly image: string;
  readonly isNew?: boolean;
  readonly discount?: number;
  readonly colors: string[];
}

export function ProductCard({ 
  id, name, price, image, isNew, discount, colors 
}: Readonly<ProductCardProps>) {
  const { addToWishlist, isInWishlist } = useWishlist();
  const [isHovered, setIsHovered] = useState(false);

  return (
    <div 
      className="group relative"
      onMouseEnter={() => setIsHovered(true)}
      onMouseLeave={() => setIsHovered(false)}
    >
      {/* Image */}
      <div className="relative aspect-[3/4] overflow-hidden bg-gray-100">
        <img 
          src={image} 
          alt={name}
          className="h-full w-full object-cover transition-transform duration-300 group-hover:scale-105"
        />
        
        {/* Badges */}
        {isNew && (
          <Badge className="absolute top-4 left-4 bg-black text-white">
            Nouveau
          </Badge>
        )}
        {discount && (
          <Badge className="absolute top-4 right-4 bg-gold text-black">
            -{discount}%
          </Badge>
        )}

        {/* Wishlist */}
        <button
          onClick={() => addToWishlist(id)}
          className="absolute top-4 right-4 p-2 bg-white rounded-full opacity-0 group-hover:opacity-100 transition-opacity"
        >
          <Heart className={isInWishlist(id) ? 'fill-red-500' : ''} />
        </button>

        {/* Quick View */}
        {isHovered && (
          <button className="absolute bottom-4 left-1/2 -translate-x-1/2 bg-gold text-black px-6 py-2 rounded">
            Aperçu rapide
          </button>
        )}
      </div>

      {/* Info */}
      <div className="mt-4">
        <h3 className="font-playfair text-lg">{name}</h3>
        <div className="flex items-center gap-2 mt-2">
          {discount ? (
            <>
              <span className="text-gray-400 line-through">{price}€</span>
              <span className="text-gold font-semibold">
                {price * (1 - discount / 100)}€
              </span>
            </>
          ) : (
            <span className="font-semibold">{price}€</span>
          )}
        </div>
        
        {/* Colors */}
        <div className="flex gap-2 mt-2">
          {colors.map(color => (
            <div 
              key={color}
              className="w-4 h-4 rounded-full border border-gray-300"
              style={{ backgroundColor: color }}
            />
          ))}
        </div>
      </div>
    </div>
  );
}
```

### Exemple : useCart Hook

```typescript
interface CartItem {
  id: string;
  name: string;
  price: number;
  image: string;
  size: string;
  color: string;
  quantity: number;
}

export function useCart() {
  const [items, setItems] = useState<CartItem[]>([]);

  const addToCart = (product: Product, size: string, color: string) => {
    const existingItem = items.find(
      item => item.id === product.id && item.size === size && item.color === color
    );

    if (existingItem) {
      updateQuantity(existingItem.id, existingItem.quantity + 1);
    } else {
      setItems([...items, { 
        ...product, 
        size, 
        color, 
        quantity: 1 
      }]);
    }

    toast.success('Produit ajouté au panier');
  };

  const removeFromCart = (id: string) => {
    setItems(items.filter(item => item.id !== id));
  };

  const updateQuantity = (id: string, quantity: number) => {
    setItems(items.map(item => 
      item.id === id ? { ...item, quantity } : item
    ));
  };

  const subtotal = items.reduce((sum, item) => sum + item.price * item.quantity, 0);
  const shipping = subtotal > 100 ? 0 : 9.90;
  const total = subtotal + shipping;

  return {
    items,
    addToCart,
    removeFromCart,
    updateQuantity,
    subtotal,
    shipping,
    total,
    itemCount: items.length
  };
}
```

---

## Étape 4 : shadcn-ui - Enrichir les Composants

### Commande

```bash
@shadcn-ui Intègre les composants shadcn/ui pour améliorer l'UX de LuxeMode : Dialog pour quick view, Select pour filtres, Toast pour notifications, Form pour checkout
```

### Installation

```bash
npx shadcn@latest add dialog select toast form input button card
```

### Exemple : Quick View Modal

```tsx
import { Dialog, DialogContent, DialogTrigger } from '@/components/ui/dialog';

export function ProductQuickView({ product }: { product: Product }) {
  return (
    <Dialog>
      <DialogTrigger asChild>
        <Button variant="outline">Aperçu rapide</Button>
      </DialogTrigger>
      <DialogContent className="max-w-4xl">
        <div className="grid grid-cols-2 gap-8">
          <img src={product.image} alt={product.name} />
          <div>
            <h2 className="font-playfair text-3xl">{product.name}</h2>
            <p className="text-2xl text-gold mt-4">{product.price}€</p>
            <SizeSelector sizes={product.sizes} />
            <ColorSelector colors={product.colors} />
            <Button className="w-full mt-6 bg-gold">
              Ajouter au panier
            </Button>
          </div>
        </div>
      </DialogContent>
    </Dialog>
  );
}
```

---

## Étape 5 : design-md - Documenter le Design

### Commande

```bash
@design-md Génère la documentation design system complète de LuxeMode
```

### Contenu du DESIGN.md

Le fichier généré contient :

**Palette Premium**
- Noir Profond (#000000) - Sophistication, navigation, texte
- Blanc Cassé (#FAFAFA) - Fond principal, cartes produits
- Or (#D4AF37) - CTA, accents premium, prix promo
- Gris Clair (#E5E5E5) - Bordures, séparateurs

**Typographie Luxe**
- Playfair Display (serif) pour les titres
- Inter (sans-serif) pour le corps de texte
- Échelle typographique définie (H1: 72px, H2: 48px, etc.)

**Composants E-commerce**
- Product Card (dimensions, hover states, transitions)
- Add to Cart Button (couleurs, padding, animations)
- Mini Cart Dropdown (dimensions, shadow, border-radius)

**Espacement**
- Système basé sur 16px
- Grille responsive

**Animations**
- Transitions (150ms, 300ms, 500ms)
- Hover effects
- Loading states

---

## Étape 6 : remotion - Vidéo Démo E-commerce

### Commande

```bash
@remotion Crée une vidéo de 45 secondes présentant LuxeMode : homepage, navigation catalogue, page produit avec ajout panier, checkout
```

### Timeline Vidéo (45 secondes)

| Temps | Contenu |
|-------|---------|
| 0:00 - 0:03 | Logo LuxeMode avec animation élégante |
| 0:03 - 0:10 | Homepage : Hero + scroll vers produits |
| 0:10 - 0:20 | Catalogue : Filtres + grille produits |
| 0:20 - 0:32 | Produit : Galerie + sélection taille/couleur + ajout panier |
| 0:32 - 0:42 | Checkout : 3 étapes avec progression |
| 0:42 - 0:45 | CTA "Découvrez LuxeMode" + URL |

### Génération de la Vidéo

```bash
# Preview en temps réel
npm run dev

# Rendu final
npm run build
npx remotion render Video LuxeModeDemo luxemode-demo.mp4
```

---

## Résultat Final

### Livrables Complets

```
luxemode-complete/
├── stitch-designs/          # 8 pages HTML/CSS
├── luxemode-app/            # Application React complète
│   ├── 30+ composants
│   ├── 6 pages
│   ├── Context API (Cart, Wishlist, Auth)
│   └── shadcn/ui intégré
├── DESIGN.md                # Design system documenté
└── luxemode-demo.mp4        # Vidéo 45s
```

### Fonctionnalités Implémentées

- Navigation complète avec recherche
- Catalogue avec filtres temps réel
- Pages produits avec galerie et sélecteurs
- Panier avec calcul automatique
- Checkout en 3 étapes
- Wishlist fonctionnelle
- Responsive mobile/tablet/desktop
- Animations et transitions fluides
- Toast notifications
- Quick view modal

---

## Commandes Complètes

Voici toutes les commandes à exécuter dans l'ordre :

### Étape 1
```bash
@enhance-prompt Site e-commerce vêtements luxe avec homepage, catalogue, produit, panier, checkout, compte
```

### Étape 2
```bash
@stitch-loop Génère toutes les pages LuxeMode avec design premium noir/or
```

### Étape 3
```bash
@react-components Convertis en React avec routing, cart context, et composants modulaires
```

### Étape 4
```bash
@shadcn-ui Ajoute Dialog, Select, Toast, Form pour UX premium
```

### Étape 5
```bash
@design-md Documente le design system LuxeMode
```

### Étape 6
```bash
@remotion Vidéo 45s : homepage → catalogue → produit → checkout
```

---

## Optimisations E-commerce

### Performance

- **Image optimization** : Utiliser next/image et sharp
- **Lazy loading** : react-lazy-load-image-component
- **Code splitting** : React.lazy et Suspense
- **Caching** : Service workers pour assets statiques

### SEO

- Metadata dynamique pour chaque produit
- Structured data (JSON-LD) pour les produits
- Sitemap XML généré automatiquement
- URLs optimisées et descriptives

### Analytics

- Tracking des ajouts au panier
- Suivi du funnel de conversion
- Analyse des abandons de panier
- Heatmaps et session recordings

---

## Auteur

**Thierno Koyagbali**

- YouTube : [Thierno Koyagbali](https://www.youtube.com/@thiernokoyagbali)
- LinkedIn : [Thierno Koyagbali](https://www.linkedin.com/in/thierno-koyagbali/)

---

## Licence

MIT

---

Guide créé pour le workflow Stitch - 2026
