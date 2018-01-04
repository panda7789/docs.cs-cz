---
title: "násobnost end přidružení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0d66c141b83402b011fdebbb04c0b2a9adc5ec29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="association-end-multiplicity"></a>násobnost end přidružení
*Násobnost end přidružení* definuje počet [typ entity](../../../../docs/framework/data/adonet/entity-type.md) instancí, které můžou být v jednom konci [přidružení](../../../../docs/framework/data/adonet/association-type.md).  
  
 Násobnost end přidružení může mít jednu z následujících hodnot:  
  
-   jedna (1): Určuje tuto instanci typu přesně jedna entita existuje na konci přidružení.  
  
-   nula nebo jeden (0..1): udává, že existuje žádnou nebo jednu instance typu entity na konci přidružení.  
  
-   Mnoho (*): udává, že existuje nula, jednu nebo více instancí typu entity na konci přidružení.  
  
 Přidružení je často charakterizovaná jeho Násobnosti zakončení přidružení. Například pokud konce přidružení mnohočetnostmi jedna (1) a mnoho (*), se nazývá přidružení na více přidružení. V následujícím příkladu `PublishedBy` přidružení je to přidružení k více (vydavatel publikuje mnoho knihy a publikování knihy se jeden vydavatelem). `WrittenBy` Association je m: n přidružení (knihy, může mít několik autoři a Autor může zapisovat více knih).  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje Koncepční model se dvě přidružení: `PublishedBy` a `WrittenBy`. Přidružení končí pro `PublishedBy` jsou přidružení `Book` a `Publisher` typy entit. Násobnost `Publisher` koncový je jedna (1) a násobnost `Book` koncový je mnoho (*).  
  
 ![Ukázkový Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 ADO.NET Entity Framework používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech. Definuje následující CSDL `PublishedBy` přidružení vidět v diagramu výše:  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>Viz také  
 [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)
