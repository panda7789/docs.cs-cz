---
title: 'Postupy: Spustit dotazy na asynchronní datové služby (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
ms.assetid: 902a2dc1-d0e9-4b00-90a8-becc4cb1f6a7
ms.openlocfilehash: 14bfc138c5ece45184fb939f19aaf3d7e73e7294
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790567"
---
# <a name="how-to-execute-asynchronous-data-service-queries-wcf-data-services"></a>Postupy: Spustit dotazy na asynchronní datové služby (WCF Data Services)
Pomocí [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientské knihovny můžete asynchronně provádět operace mezi klientem a serverem, jako je spouštění dotazů a ukládání změn. Další informace najdete v tématu [asynchronní operace](asynchronous-operations-wcf-data-services.md).  
  
> [!NOTE]
> V aplikaci, kde musí být zpětné volání vyvoláno v konkrétním vlákně, je nutné explicitně zařadit provedení <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> metody. Další informace najdete v tématu [asynchronní operace](asynchronous-operations-wcf-data-services.md).  
  
 V příkladu v tomto tématu se používá ukázková datová služba Northwind a automaticky vygenerované třídy klientské datové služby. Tato služba a klientské datové třídy se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak spustit asynchronní dotaz voláním <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> metody pro spuštění dotazu. Vložený delegát volá <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> metodu pro zobrazení výsledků dotazu.  
  
 [!code-csharp[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#executequeryasync)]
 [!code-vb[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#executequeryasync)]  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
