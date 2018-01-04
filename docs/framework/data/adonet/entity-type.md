---
title: Typ entity
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: dd1a669b81b9dbbb54b83d13dbb7c0ba7ce3f5cd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="entity-type"></a>Typ entity
*Typ entity* je základní stavební blok pro popisující strukturu dat s Entity Data Model (EDM). Typ entity v konceptuálním modelu představuje strukturu nejvyšší úrovně koncepty, jako jsou zákazníci nebo objednávky. Typ entity je šablona pro instance typu entity. Každá šablona obsahuje následující informace:  
  
-   Jedinečný název. (Povinné).  
  
-   [Klíč entity](../../../../docs/framework/data/adonet/entity-key.md) definované jednu nebo více vlastností. (Povinné).  
  
-   Data ve formě [vlastnosti](../../../../docs/framework/data/adonet/property.md). (Volitelné).  
  
-   [Navigační vlastnosti](../../../../docs/framework/data/adonet/navigation-property.md) které umožňují pro navigaci z jednoho [end](../../../../docs/framework/data/adonet/association-end.md) z [přidružení](../../../../docs/framework/data/adonet/association-type.md) na druhém konci. (Volitelné)  
  
 V aplikaci představuje instanci typu entity na konkrétní objekt (například konkrétního zákazníka nebo pořadí). Každá instance typu entity, musí mít jedinečnou [klíč entity](../../../../docs/framework/data/adonet/entity-key.md) v rámci [sady entit](../../../../docs/framework/data/adonet/entity-set.md).  
  
 Dvě instance typu entity jsou považovány za shodné, pouze v případě, že jsou stejného typu a hodnoty jejich klíče entity jsou stejné.  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje Koncepční model se tři typy entit: `Book`, `Publisher`, a `Author`:  
  
 ![Ukázkový Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 Všimněte si, že vlastnosti každého typu entity, které tvoří svůj klíč entity, jsou označeny "(klíč)".  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech. Definuje následující CSDL `Book` typ entity, které jsou uvedené v diagramu výše:  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a>Viz také  
 [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [facet](../../../../docs/framework/data/adonet/facet.md)
