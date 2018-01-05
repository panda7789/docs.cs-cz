---
title: "deklarovaný modelu – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2f5c7828dc1ea79a548b35109b428da05c2b4560
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="model-declared-function"></a>deklarovaný modelu – funkce
A *modelu deklarované funkce* je funkce, která je deklarován v konceptuálním modelu, ale není definován v tomto konceptuálním modelu. Funkce mohou být definovány v prostředí hostování nebo úložiště. Například může funkce modelu deklarované mapovat na funkci, která je definována v databázi, proto vystavení funkce na straně serveru v konceptuálním modelu.  
  
 Deklarace funkce deklarovaný model obsahuje následující informace:  
  
-   Název funkce. (Povinné)  
  
-   Typ vrácené hodnoty. (Volitelné)  
  
    > [!NOTE]
    >  Pokud je zadán žádnou návratovou hodnotu, je návratový typ void.  
  
-   Informace o parametrech, včetně parametr názvu a typu. (Volitelné)  
  
## <a name="example"></a>Příklad  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech. V CSDL, je jednou z implementací funkce modelu deklarované [import funkce](http://msdn.microsoft.com/en-us/125704ae-56c7-4233-80b7-389a10f3a65d). Následující CSDL definuje kontejner entity s definicí importu funkce. Všimněte si, že návratový typ pro funkci je neplatné, protože není zadán žádný návratový typ.  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a>Viz také  
 [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)
