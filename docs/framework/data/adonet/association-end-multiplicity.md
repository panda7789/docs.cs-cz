---
title: association end multiplicity
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: 3f3d8ba9f7e68065024dd3efb599b847496740cd
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738565"
---
# <a name="association-end-multiplicity"></a>association end multiplicity
*Násobnost zakončení přidružení* definuje počet instancí [typu entity](entity-type.md) , které mohou být na jednom konci [přidružení](association-type.md).  
  
 Násobnost zakončení přidružení může mít jednu z následujících hodnot:  
  
- jedna (1): označuje, že na konci přidružení existuje přesně jedna instance typu entity.  
  
- nula nebo jedna (0.. 1): označuje, že na konci přidružení existují žádné nebo jedna instance typu entity.  
  
- mnoho (\*): udává, že na konci přidružení existují žádné instance typu entity nula, jedna nebo více.  
  
 Přidružení je často charakteristické násobnostmi koncovosti přidružení. Například pokud má element end přidružení násobnosti 1 a mnoho (\*), přidružení se nazývá přidružení 1:1. V následujícím příkladu je přidružení `PublishedBy` přidružení typu 1: n (vydavatel zveřejňuje mnoho knih a kniha je publikována jedním vydavatelem). Přidružení `WrittenBy` je přidružení typu m:n (kniha může mít více autorů a autor může zapisovat několik knih).  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje koncepční model se dvěma přidruženími: `PublishedBy` a `WrittenBy`. Zakončení přidružení pro `PublishedBy` přidružení jsou typy entit `Book` a `Publisher`. Násobnost `Publisher` end je jedna (1) a násobnost `Book` end má mnoho (\*).  
  
 ![Vzorový model se třemi typy entit](./media/association-end-multiplicity/example-model-three-entity-types.gif)  
  
 ADO.NET Entity Framework používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(konceptuální schéma Definition Language). Následující CSDL definuje přidružení `PublishedBy` zobrazené v diagramu výše:  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](entity-data-model.md)
