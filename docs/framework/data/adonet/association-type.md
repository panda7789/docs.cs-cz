---
title: Typ přidružení
ms.date: 03/30/2017
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
ms.openlocfilehash: 7a16b4447c9ba35f1a81a8ff837abd984985b097
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="association-type"></a>Typ přidružení
*Typ přidružení* (také nazývané přidružení) je základní stavební blok pro popisující vztahy v Entity Data Model (EDM). V konceptuálním modelu přidružení představuje vztah mezi dvěma [typy entit](../../../../docs/framework/data/adonet/entity-type.md) (například `Customer` a `Order`). V aplikaci, představuje instanci přidružení konkrétní přidružení (jako je například přidružení mezi instanci `Customer` a instance `Order`). Přidružení instance jsou logicky seskupeny do [sadu přidružení](../../../../docs/framework/data/adonet/association-set.md).  
  
 Přidružení definice obsahuje následující informace:  
  
-   Jedinečný název. (Povinné)  
  
-   Dva [zakončení přidružení](../../../../docs/framework/data/adonet/association-end.md), jednu pro každý typ entity v relaci. (Povinné)  
  
    > [!NOTE]
    >  Přidružení nemůže představují vztah mezi více než dva typy entit. Přidružení můžete, ale taky definovat vztah samoobslužné tak, že zadáte stejný typ entity pro každou z konců přidružení.  
  
-   A [omezení referenční integrity](../../../../docs/framework/data/adonet/referential-integrity-constraint.md). (Volitelné)  
  
 Musíte zadat každou end přidružení [násobnost end přidružení](../../../../docs/framework/data/adonet/association-end-multiplicity.md) určující počet instancí typ entity, které mohou být na jednom konci přidružení. Násobnost end přidružení může mít hodnotu jedna (1), žádnou nebo jednu (0..1), nebo mnoho (*). Instance typu entity na jednom konci přidružení je možné přistupovat prostřednictvím [navigační vlastnosti](../../../../docs/framework/data/adonet/navigation-property.md) nebo cizího klíče, pokud jsou zveřejněné na typ entity. Další informace najdete v tématu [datového modelu Entity: cizí klíče](../../../../docs/framework/data/adonet/foreign-key-property.md).  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje Koncepční model se dvě přidružení: `PublishedBy` a `WrittenBy`. Přidružení končí pro `PublishedBy` jsou přidružení `Book` a `Publisher` typy entit. Násobnost `Publisher` koncový je jedna (1) a násobnosti atributu `Book` koncový je mnoho (*), označující, že vydavatel publikuje mnoho knihy a publikování knihy se jeden vydavatelem.  
  
 ![Ukázkový Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech. Definuje následující CSDL `PublishedBy` přidružení vidět v diagramu výše:  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>Viz také  
 [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)
