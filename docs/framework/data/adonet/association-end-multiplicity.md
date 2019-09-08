---
title: association end multiplicity
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: cdcf69e7118620b2f8febd02d7695d429bf8cc2c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786941"
---
# <a name="association-end-multiplicity"></a>association end multiplicity
*Násobnost zakončení přidružení* definuje počet instancí [typu entity](entity-type.md) , které mohou být na jednom konci [přidružení](association-type.md).  
  
 Násobnost zakončení přidružení může mít jednu z následujících hodnot:  
  
- jedna (1): Označuje, že na konci přidružení existuje přesně jedna instance typu entity.  
  
- nula nebo jedna (0.. 1): Označuje, že na konci přidružení existují žádné nebo jedna instance typu entity.  
  
- mnoho (\*): Označuje, že na konci přidružení existují žádné instance typu entity nula, jedna nebo více.  
  
 Přidružení je často charakteristické násobnostmi koncovosti přidružení. Například pokud končí přidružení násobnosti jedna (1) a many (\*), přidružení se nazývá přidružení 1:1. V následujícím `PublishedBy` příkladu je přidružení přidružení typu 1: n (vydavatel zveřejňuje mnoho knih a kniha je publikována jedním vydavatelem). `WrittenBy` Přidružení je asociace typu m:n (kniha může mít více autorů a autor může zapisovat několik knih).  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje koncepční model se dvěma přidruženími: `PublishedBy` a. `WrittenBy` Přidružení `PublishedBy` jsouzakončenápro`Publisher` přidružení jsou typy entit a.`Book` Násobnost elementu `Publisher` end je jedna (1) a násobnost elementu `Book` end je mnoho (\*).  
  
 ![Vzorový model se třemi typy entit](./media/association-end-multiplicity/example-model-three-entity-types.gif)  
  
 ADO.NET Entity Framework používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](./ef/language-reference/csdl-specification.md)(konceptuální schéma Definition Language). Následující CSDL definuje `PublishedBy` přidružení zobrazené v diagramu výše:  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](entity-data-model.md)
