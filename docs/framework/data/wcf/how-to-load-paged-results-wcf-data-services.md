---
title: "Postupy: načtení stránkovaného výsledky (služby WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: bb786ea4-f3ef-4ad3-9a41-3a0b7feb6a1f
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 405bea18b03ba695dcb952d10a193decc124841d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-load-paged-results-wcf-data-services"></a>Postupy: načtení stránkovaného výsledky (služby WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]povoluje službu data omezit počet entit, které se vrátí odpověď o jedné informačního kanálu. V takovém případě poslední položku v informačním kanálu obsahuje odkaz na další stránku data. Identifikátor URI na další stránku dat se získá voláním <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> metodu <xref:System.Data.Services.Client.QueryOperationResponse%601>, která je vrácena, pokud <xref:System.Data.Services.Client.DataServiceQuery%601> se spustí. Identifikátor URI představuje tento objekt se pak použije k načtení další stránky výsledků. Další informace najdete v tématu [načítání odložení obsahu](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
 V příkladu v tomto tématu používá Northwind ukázková data služby a automaticky generovaný klienta dat služby třídy. Tato služba a datové třídy klienta se vytvoří při dokončení [rychlého startu služby WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `do…while` smyčky načíst `Customers` entity z stránkových výsledků z službu data.  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getcustomerspaged)]
 [!code-vb[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getcustomerspaged)]  
  
## <a name="example"></a>Příklad  
 Tento příklad vrátí související `Orders` entity s každou `Customers` entity a použije `do…while` smyčky načíst `Customers` entity stránky a vnořený `while` opakování ve smyčce bude načtení stránek ze souvisejících `Orders` entity ze služby data .  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getcustomerspagednested)]
 [!code-vb[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getcustomerspagednested)]  
  
## <a name="see-also"></a>Viz také  
 [Načtení odloženého obsahu](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 [Postupy: Načtení souvisejících entit](../../../../docs/framework/data/wcf/how-to-load-related-entities-wcf-data-services.md)
