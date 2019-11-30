---
title: 'Postupy: načtení stránkovaných výsledků (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: bb786ea4-f3ef-4ad3-9a41-3a0b7feb6a1f
ms.openlocfilehash: d651a66ac619e46d3ec6b46b194436f51300ff25
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569028"
---
# <a name="how-to-load-paged-results-wcf-data-services"></a>Postupy: načtení stránkovaných výsledků (WCF Data Services)
WCF Data Services umožňuje datové službě omezit počet entit, které jsou vráceny v jednom kanálu odpovědí. Pokud k tomu dojde, poslední položka v informačním kanálu obsahuje odkaz na další stránku dat. Identifikátor URI pro další stránku dat se získá voláním metody <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> <xref:System.Data.Services.Client.QueryOperationResponse%601>, která se vrátí při spuštění <xref:System.Data.Services.Client.DataServiceQuery%601>. Identifikátor URI reprezentovaný tímto objektem se pak použije k načtení další stránky výsledků. Další informace najdete v tématu [načítání odloženého obsahu](loading-deferred-content-wcf-data-services.md).  
  
 V příkladu v tomto tématu se používá ukázková datová služba Northwind a automaticky vygenerované třídy klientské datové služby. Tato služba a klientské datové třídy se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá smyčka `do…while` pro načtení `Customers` entit ze stránkovaných výsledků z datové služby.  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getcustomerspaged)]
 [!code-vb[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getcustomerspaged)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu vrátí související entity `Orders` s každou entitou `Customers` a pomocí `do…while` smyčky načte stránky `Customers` entit a vnořený `while` cyklus, aby se načetly stránky souvisejících `Orders` entit z datové služby.  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getcustomerspagednested)]
 [!code-vb[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getcustomerspagednested)]  
  
## <a name="see-also"></a>Viz také:

- [Načtení odloženého obsahu](loading-deferred-content-wcf-data-services.md)
- [Postupy: Načtení souvisejících entit](how-to-load-related-entities-wcf-data-services.md)
