---
title: end přidružení
ms.date: 03/30/2017
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
ms.openlocfilehash: 8c156ca1c05e22e540578adfb2be06cf477b29e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744944"
---
# <a name="association-end"></a>end přidružení
*End přidružení* identifikuje [typ entity](../../../../docs/framework/data/adonet/entity-type.md) na jednom konci [přidružení](../../../../docs/framework/data/adonet/association-type.md) a počet entit zadejte instancí, které mohou existovat, které končí přidružení. Zakončení jsou definované jako součást přidružení; přidružení musí mít přesně dva elementy přidružení. [Vlastnosti navigace](../../../../docs/framework/data/adonet/navigation-property.md) umožňují navigace z end přidružení jednoho na druhý.  
  
 Definici end přidružení obsahuje následující informace:  
  
-   Jeden z typů entit, která je součástí přidružení. (Povinné)  
  
    > [!NOTE]
    >  Pro daný přidružení pro každý konec asociace zadán typ entity může být stejné. Tím se vytvoří vlastní přidružení.  
  
-   [Násobnost end přidružení](../../../../docs/framework/data/adonet/association-end-multiplicity.md) , která určuje počet instancí typu entity, které mohou být na jednom konci přidružení. Násobnost end přidružení může mít hodnotě jedna (1), žádný nebo jeden (0..1), nebo mnoho (*).  
  
-   Název přidružení. (Volitelné)  
  
-   Informace o operacích, které se provádí na konci přidružení, jako je například kaskádové odstranění. (Volitelné)  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje Koncepční model se dvěma přidružení: `PublishedBy` a `WrittenBy`. Konec asociace `PublishedBy` přidružení se `Book` a `Publisher` typy entit. Násobnost `Publisher` end je jedna (1) a násobnost `Book` end je mnoho (*), označující, že vydavatel publikuje mnoho knih a knihy se publikuje vydavatele.  
  
 ![Ukázkový Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 ADO.NET Entity Framework používá jazyka specifického pro doménu (DSL) volá Konceptuální schéma definici jazyka ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelů. Definuje CSDL níže `PublishedBy` přidružení, které jsou zobrazeny ve výše uvedeném diagramu. Všimněte si, že typ, název a násobnost každý konec asociace jsou určena pomocí atributů XML ( `Type`, `Role`, a `Multiplicity` atributů). Volitelné informace o operace provedené na skončí je zadaný v elementu XML ( `OnDelete` element). V tomto případě pokud vydavatele se odstraní, proto jsou všechny přidružené knihy.  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## <a name="see-also"></a>Viz také:
- [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)
