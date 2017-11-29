---
title: "konce přidružení sady"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 20810eddda98403d244f6104807504489dde71cc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="association-set-end"></a>konce přidružení sady
*Nastavená přidružení end* identifikuje [typ entity](../../../../docs/framework/data/adonet/entity-type.md) a [sady entit](../../../../docs/framework/data/adonet/entity-set.md) na konci [sadu přidružení](../../../../docs/framework/data/adonet/association-set.md). Přidružení sady končí jsou definované jako součást sady přidružení; sadu přidružení musí mít přesně dva sadu zakončení.  
  
 Definici sady end přidružení obsahuje následující informace:  
  
-   Jeden z typů entity účastní přidružení nastavit. (Povinné)  
  
-   Sada entit pro typ entity účastní sadu přidružení. (Povinné)  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje Koncepční model se dvě přidružení: `WrittenBy` a `PublishedBy`.  
  
 ![Ukázkový Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 Následující diagram znázorňuje sadu přidružení (`PublishedBy`) a dvě sady entit (`Books` a `Publishers`) na základě konceptuálního modelu uvedené výše. Elementy end přidružení sady jsou `Books` a `Publishers` sady entit. BI v `Books` sady entit představuje instanci `Book` typ entity v době běhu. Podobně, představuje Pj `Publisher` instance v `Publishers` sady entit. BiPj představuje instanci `PublishedBy` přidružení v `PublishedBy` sadu přidružení.  
  
 ![Nastaví příklad](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá DSL, kterému se říká jazyk definice konceptuálního schématu ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech. Následující CSDL definuje jednu sadu pro každé přidružení v diagramu výše přidružení kontejner entity. Všimněte si, že zakončení sady jsou definovány v rámci každé definici sady přidružení.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>Viz také  
 [Entity Data Model klíčové koncepty](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Datového modelu entity](../../../../docs/framework/data/adonet/entity-data-model.md)
