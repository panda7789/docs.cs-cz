---
title: 'Postupy: spouštění dotazů na asynchronní datové služby (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
ms.assetid: 902a2dc1-d0e9-4b00-90a8-becc4cb1f6a7
ms.openlocfilehash: 68e2035315780b7c6dd60e93ae6eb10d252aabb3
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569069"
---
# <a name="how-to-execute-asynchronous-data-service-queries-wcf-data-services"></a>Postupy: spouštění dotazů na asynchronní datové služby (WCF Data Services)
Pomocí klientské knihovny WCF Data Services můžete asynchronně provádět operace mezi klientem a serverem, jako je spouštění dotazů a ukládání změn. Další informace najdete v tématu [asynchronní operace](asynchronous-operations-wcf-data-services.md).  
  
> [!NOTE]
> V aplikaci, kde musí být zpětné volání vyvoláno v konkrétním vlákně, je nutné explicitně zařadit spuštění metody <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>. Další informace najdete v tématu [asynchronní operace](asynchronous-operations-wcf-data-services.md).  
  
 V příkladu v tomto tématu se používá ukázková datová služba Northwind a automaticky vygenerované třídy klientské datové služby. Tato služba a klientské datové třídy se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak spustit asynchronní dotaz voláním metody <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> pro spuštění dotazu. Vložený delegát volá metodu <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> pro zobrazení výsledků dotazu.  
  
 [!code-csharp[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#executequeryasync)]
 [!code-vb[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#executequeryasync)]  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
