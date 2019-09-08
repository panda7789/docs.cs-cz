---
title: association type
ms.date: 03/30/2017
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
ms.openlocfilehash: e75037223b235cf09df0bca85c6a4feb0b340174
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786890"
---
# <a name="association-type"></a>association type
*Typ přidružení* (označovaný také jako asociace) je základní stavební blok pro popis vztahů v model EDM (Entity Data Model) (EDM). V koncepčním modelu představuje přidružení vztah mezi dvěma [typy entit](entity-type.md) (například `Customer` a `Order`). V aplikaci instance přidružení představuje konkrétní přidružení (například přidružení mezi instancí `Customer` a `Order`instancí). Instance přidružení jsou logicky seskupeny v [sadě přidružení](association-set.md).  
  
 Definice přidružení obsahuje následující informace:  
  
- Jedinečný název. Požadovanou  
  
- Dvě [zakončení přidružení](association-end.md), jedna pro každý typ entity v relaci. Požadovanou  
  
    > [!NOTE]
    > Přidružení nemůže představovat relaci mezi více než dvěma typy entit. Přidružení může nicméně definovat vlastní relaci zadáním stejného typu entity pro každé z jeho zakončení přidružení.  
  
- [Omezení referenční integrity](referential-integrity-constraint.md). Volitelné  
  
 Každé zakončení přidružení musí určovat [násobnost zakončení přidružení](association-end-multiplicity.md) , která označuje počet instancí typu entity, které mohou být na jednom konci přidružení. Násobnost zakončení přidružení může mít hodnotu jedna (1), 0 nebo 1 (0.. 1) nebo mnoho (\*). Instance typu entity na jednom konci přidružení lze zpřístupnit prostřednictvím [vlastností navigace](navigation-property.md) nebo cizích klíčů, pokud jsou vystaveny na typu entity. Další informace najdete v tématu [model EDM (Entity Data Model): Cizí klíče](foreign-key-property.md).  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje koncepční model se dvěma přidruženími: `PublishedBy` a. `WrittenBy` Přidružení `PublishedBy` jsouzakončenápro`Publisher` přidružení jsou typy entit a.`Book` Násobnost elementu `Publisher` end je jedna (1) a násobnost elementu `Book` end je mnoho (\*), což znamená, že vydavatel zveřejňuje mnoho knih a kniha je publikována jedním vydavatelem.  
  
 ![Vzorový model se třemi typy entit](./media/association-type/example-model-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](./ef/language-reference/csdl-specification.md)(konceptuální schéma Definition Language). Následující CSDL definuje `PublishedBy` přidružení zobrazené v diagramu výše:  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](entity-data-model.md)
