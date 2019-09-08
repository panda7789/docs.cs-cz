---
title: 'Postupy: Spouštění dotazů v dávce (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, batch requests
ms.assetid: 3b4db7df-bd33-43a1-8ea4-63a18e131f97
ms.openlocfilehash: a825fe83ff62d935740fb69871ba2d1e2120e9ec
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790489"
---
# <a name="how-to-execute-queries-in-a-batch-wcf-data-services"></a>Postupy: Spouštění dotazů v dávce (WCF Data Services)
Pomocí [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientské knihovny můžete v jedné dávce spustit více než jeden dotaz na datovou službu. Další informace najdete v tématu [dávkové operace](batching-operations-wcf-data-services.md).  
  
 V příkladu v tomto tématu se používá ukázková datová služba Northwind a automaticky vygenerované třídy klientské datové služby. Tato služba a klientské datové třídy se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> ukazuje, jak zavolat metodu pro spuštění <xref:System.Data.Services.Client.DataServiceRequest%601> pole objektů, které obsahují `Products` dotazy, které vracejí oba `Customers` objekty z datové služby Northwind. Kolekce <xref:System.Data.Services.Client.QueryOperationResponse%601> objektů v vrácených <xref:System.Data.Services.Client.DataServiceResponse> je tvořena výčtem a kolekce objektů, které jsou obsaženy v každé <xref:System.Data.Services.Client.QueryOperationResponse%601> z nich, jsou také vyčísleny.  
  
 [!code-csharp[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#batchquery)]
 [!code-vb[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#batchquery)]  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
