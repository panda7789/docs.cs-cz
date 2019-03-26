---
title: Typ přidružení
ms.date: 03/30/2017
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
ms.openlocfilehash: 895d7fdc464741723322717c3ace027dc49eed9c
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411444"
---
# <a name="association-type"></a>Typ přidružení
*Typ přidružení* (také nazývané přidružení) je základním stavebním blokem popisující relace v modelu Entity Data Model (EDM). V konceptuálním modelu, přidružení představuje vztah mezi dvěma [typy entit](../../../../docs/framework/data/adonet/entity-type.md) (například `Customer` a `Order`). V aplikaci, která představuje instance přidružení konkrétní přidružení (jako je například přidružení mezi instance `Customer` a instance `Order`). Přidružení instance jsou logicky seskupeny do [sada přidružení](../../../../docs/framework/data/adonet/association-set.md).  
  
 Definici přidružení obsahuje následující informace:  
  
-   Jedinečný název. (Povinné)  
  
-   Dvě [zakončení](../../../../docs/framework/data/adonet/association-end.md), jeden pro každý typ entity v relaci. (Povinné)  
  
    > [!NOTE]
    >  Přidružení nemůže představovat vztah mezi více než dva typy entit. Přidružení však můžete definovat vlastní relaci tak, že zadáte stejný typ entity pro každý z jeho zakončení.  
  
-   A [omezení referenční integrity](../../../../docs/framework/data/adonet/referential-integrity-constraint.md). (Volitelné)  
  
 Každý konec asociace musíte zadat [násobnost end přidružení](../../../../docs/framework/data/adonet/association-end-multiplicity.md) , která určuje počet instancí typu entity, které mohou být na jednom konci přidružení. Násobnost end přidružení může mít hodnotu jedna (1), žádný nebo jeden (0..1) nebo mnoho (\*). Instance typu entity na jednom konci asociace je přístupná prostřednictvím [navigační vlastnosti](../../../../docs/framework/data/adonet/navigation-property.md) nebo cizí klíče, pokud jsou zveřejněné na typ entity. Další informace najdete v tématu [modelu Entity Data Model: Cizí klíče](../../../../docs/framework/data/adonet/foreign-key-property.md).  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje Koncepční model se dvěma přidružení: `PublishedBy` a `WrittenBy`. Konec asociace `PublishedBy` přidružení se `Book` a `Publisher` typy entit. Násobnost `Publisher` end je jedna (1) a násobnost `Book` end je mnoho (\*), označující, že vydavatel publikuje mnoho knih a knihy se publikuje vydavatele.  
  
 ![Příklad modelu s tři typy entit](./media/association-type/example-model-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá jazyka specifického pro doménu (DSL) volá Konceptuální schéma definici jazyka ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelů. Definuje následující CSDL `PublishedBy` přidružení, které jsou zobrazeny ve výše uvedeném diagramu:  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)
