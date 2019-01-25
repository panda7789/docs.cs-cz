---
title: Nastavit konec asociace
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: 9a71fd434bea87a75e259a3d5caa902fbecf8a57
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701635"
---
# <a name="association-set-end"></a>Nastavit konec asociace
*Přidružení nastavit konec* identifikuje [typ entity](../../../../docs/framework/data/adonet/entity-type.md) a [sadu entit](../../../../docs/framework/data/adonet/entity-set.md) na konci [sada přidružení](../../../../docs/framework/data/adonet/association-set.md). Zakončení sady jsou definované jako součást sady přidružení; skupinu přidružení musí mít přesně dva zakončení sady.  
  
 Definici sady end přidružení obsahuje následující informace:  
  
-   Jeden z typů entity účastnící se přidružení nastavení. (Povinné)  
  
-   Sada entit pro typ entity účastnící se sada přidružení. (Povinné)  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje Koncepční model se dvěma přidružení: `WrittenBy` a `PublishedBy`.  
  
 ![Ukázkový Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 Následující diagram znázorňuje skupinu přidružení (`PublishedBy`) a dvě sady entit (`Books` a `Publishers`) založené na konceptuální model, uvedené výše. Jsou sady zakončení `Books` a `Publishers` sady entit. BI v `Books` sadu entit představuje instanci `Book` typ entity v době běhu. Obdobně Pj představuje `Publisher` instance v `Publishers` sady entit. BiPj představuje instanci `PublishedBy` přidružení v `PublishedBy` sada přidružení.  
  
 ![Nastaví příklad](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá DSL volá Konceptuální schéma definici jazyka ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelů. Následující CSDL definuje kontejneru entity s jeden přidružení nastavení pro každé přidružení ve výše uvedeném diagramu. Všimněte si, že Sada zakončení jsou definované jako součást každé definice sady přidružení.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>Viz také:
- [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)
