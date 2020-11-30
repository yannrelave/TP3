# TP liste d'utilisateurs

## Analyse de code

Analysez le [code situé du projet](https://codesandbox.io/s/tp-props-q0wln?file=/src/App.js) puis répondez aux questions.


**1. Quelle ligne charge le fichier JSON dans le code ?**

Le fichier JSON est chargé par la ligne `import users from "./Users.json";`

**2. Quelle est la structure de données du fichier JSON ?**

Les fichiers JSON ont une structure clé => valeur. Les valeurs sont identifiées par une clé.

**3. Justifiez le `User.propTypes`. Donnez des exemples de données qui ne sont pas prises en compte.**

`User.propTypes` permet de vérifier la validitée des types des données récupérées et envoyées pour l'affichage.  
Des données non prises en compte : `login`, `phone` et `cell`.

**4. Quelles données sont obligatoires pour construire le composant `User` ?**

L'objet `name` comporte un `.required`, il est donc obligatoire. Et rends également les attributs qu'il contient obligatoires : `title`, `first`, `last`.

**5. A quoi correspond `PropTypes.shape` ?**

`PropTypes.shape` correspond à une méthode permettant de mettre en forme un objet. Grace à celle-ci, il est possible d'ajouter plusieurs champs à un objet.

**6. Pourquoi l'attribut `style` contient deux accolades ?**

La première accolade sert à indiquer que l'on passe du HTML au JavaScript, et la deuxième pour la prise en compte du tableau associatif.

**7. Quel est le nom de l'opérateur qui transmet les données du composant `App` vers le composant `User`? Pourquoi est-ce dangereux d'abuser de cet opérateur ?**

L'opérateur qui transmet les données du composant `App` vers le composant `User` est `export default`.  
Il est dangereux d'abuser de cet opérateur 

**8. Ajoutez un paragraphe `p` au composant `User` pour afficher la date de naissance sous la forme "Né le 27/02/1942" pour un homme ou "Née le 27/02/1942" pour une femme en utilisant une condition ternaire. Copiez le code ajouté dans ce document en guise de réponse.**

`<p> 
          {props.gender === "male" ? "Né le 27/02/1942" : "Née le 27/02/1942"}
     </p>`

(Pensez à mettre votre code dans des balises Markdown  !!)

## Rédaction de tests
**9. Lisez [les recettes de tests](https://fr.reactjs.org/docs/testing-recipes.html#gatsby-focus-wrapper). Rédigez un test pour vérifier que le composant `User` contient une image.**

**10. Rédigez un autre test dans lequel vous créez le composant `User` avec le `name` de votre choix dans le `props` et vérifiez que le composant affiche bien le `name`.**

``js
import React from "react";
import { render, unmountComponentAtNode } from "react-dom";
import { act } from "react-dom/test-utils";
import App from "./App";

let container = null;
beforeEach(() => {
  // met en place un élément DOM comme cible de rendu
  container = document.createElement("div");
  document.body.appendChild(container);
});

afterEach(() => {
  // nettoie en sortie de test
  unmountComponentAtNode(container);
  container.remove();
  container = null;
});

it("Vérifie nom", () => {
  const name = "Terry"
  act(() => {
    render(<App name = {name}/>, container);
  });
  const nom = container.textContent;
  console.log(nom);
  expect(nom).toMatch(name);
});``

**11. Faites un test de "capture d'instantanés" en suivant les indications de la documentation**

**12. Proposez 3 autres tests**


## Mini-projet 

[Téléchargez une liste de films sous le format d'un fichier JSON](https://imdb-api.com/). Cela vous demandera de créer un compte.

**13. Créez un nouveau projet et affichez les films sous la forme de cartes. Vous devrez soigner le design de la page, sans copiant le code de la liste d'utilisateurs**
