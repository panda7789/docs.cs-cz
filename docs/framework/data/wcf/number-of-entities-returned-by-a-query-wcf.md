---
title: 'Postupy: určení počtu entit vrácených dotazem (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, row count
ms.assetid: 03d41a82-df95-40ac-8439-a6c327d37ba8
ms.openlocfilehash: 43833566d59b15ef382872b0c40f452192b59bac
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568917"
---
# <a name="how-to-determine-the-number-of-entities-returned-by-a-query-wcf-data-services"></a>Postupy: určení počtu entit vrácených dotazem (WCF Data Services)
Pomocí WCF Data Services můžete určit počet entit, které jsou v sadě entit určené identifikátorem URI dotazu. Tento počet lze zahrnout buď spolu s výsledkem dotazu, nebo jako celočíselnou hodnotu. Další informace najdete v tématu [dotazování datové služby](querying-the-data-service-wcf-data-services.md).  
  
 V příkladu v tomto tématu se používá ukázková datová služba Northwind a automaticky vygenerované třídy klientské datové služby. Tato služba a klientské datové třídy se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Tento příklad spustí dotaz po volání metody <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A>. Vlastnost <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> vrací počet entit v sadě entit `Customers`.  
  
 [!code-csharp[Astoria Northwind Client#CountAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#countallcustomers)]
 [!code-vb[Astoria Northwind Client#CountAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#countallcustomers)]  
  
## <a name="example"></a>Příklad  
 Tento příklad volá metodu <xref:System.Linq.Enumerable.Count%2A>, aby vrátila pouze celočíselnou hodnotu, která je počtem entit v sadě entit `Customers`.  
  
 [!code-csharp[Astoria Northwind Client#CountAllCustomersValueOnly](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#countallcustomersvalueonly)]
 [!code-vb[Astoria Northwind Client#CountAllCustomersValueOnly](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#countallcustomersvalueonly)]  
  
## <a name="see-also"></a>Viz také:

- [Dotazování v datové službě](querying-the-data-service-wcf-data-services.md)
