---
title: association type
ms.date: 03/30/2017
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
ms.openlocfilehash: e1430e6255dce2bae6d82411db5d2a9f11f46e1a
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738550"
---
# <a name="association-type"></a>association type
*Typ přidružení* (označovaný také jako asociace) je základní stavební blok pro popis vztahů v model EDM (Entity Data Model) (EDM). V koncepčním modelu představuje přidružení vztah mezi dvěma [typy entit](entity-type.md) (například `Customer` a `Order`). V aplikaci instance přidružení představuje konkrétní přidružení (například přidružení mezi instancí `Customer` a instancí `Order`). Instance přidružení jsou logicky seskupeny v [sadě přidružení](association-set.md).  
  
 Definice přidružení obsahuje následující informace:  
  
- Jedinečný název. Požadovanou  
  
- Dvě [zakončení přidružení](association-end.md), jedna pro každý typ entity v relaci. Požadovanou  
  
    > [!NOTE]
    > Přidružení nemůže představovat relaci mezi více než dvěma typy entit. Přidružení může nicméně definovat vlastní relaci zadáním stejného typu entity pro každé z jeho zakončení přidružení.  
  
- [Omezení referenční integrity](referential-integrity-constraint.md). Volitelné  
  
 Každé zakončení přidružení musí určovat [násobnost zakončení přidružení](association-end-multiplicity.md) , která označuje počet instancí typu entity, které mohou být na jednom konci přidružení. Násobnost zakončení přidružení může mít hodnotu jedna (1), 0 nebo 1 (0.. 1) nebo mnoho (\*). Instance typu entity na jednom konci přidružení lze zpřístupnit prostřednictvím [vlastností navigace](navigation-property.md) nebo cizích klíčů, pokud jsou vystaveny na typu entity. Další informace najdete v tématu [model EDM (Entity Data Model): cizí klíče](foreign-key-property.md).  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje koncepční model se dvěma přidruženími: `PublishedBy` a `WrittenBy`. Zakončení přidružení pro `PublishedBy` přidružení jsou typy entit `Book` a `Publisher`. Násobnost `Publisher` end je jedna (1) a násobnost `Book` end je mnoho (\*), což znamená, že vydavatel zveřejňuje mnoho knih a kniha je publikována jedním vydavatelem.  
  
 ![Vzorový model se třemi typy entit](./media/association-type/example-model-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(konceptuální schéma Definition Language). Následující CSDL definuje přidružení `PublishedBy` zobrazené v diagramu výše:  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](entity-data-model.md)
