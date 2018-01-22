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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 37c6b04fbea69f62aaf7bc148ee04ace5a5a349c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
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
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech. V CSDL, je jednou z implementací funkce modelu deklarované [import funkce](http://msdn.microsoft.com/library/125704ae-56c7-4233-80b7-389a10f3a65d). Následující CSDL definuje kontejner entity s definicí importu funkce. Všimněte si, že návratový typ pro funkci je neplatné, protože není zadán žádný návratový typ.  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a>Viz také  
 [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)
