---
title: 'Postupy: provádění dotazů v dávce (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, batch requests
ms.assetid: 3b4db7df-bd33-43a1-8ea4-63a18e131f97
ms.openlocfilehash: 0ddf5b4f68ca08fca0c55cfcdfcd5431bcec6de2
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569056"
---
# <a name="how-to-execute-queries-in-a-batch-wcf-data-services"></a>Postupy: provádění dotazů v dávce (WCF Data Services)
Pomocí klientské knihovny WCF Data Services můžete v jedné dávce spustit více než jeden dotaz na datovou službu. Další informace najdete v tématu [dávkové operace](batching-operations-wcf-data-services.md).  
  
 V příkladu v tomto tématu se používá ukázková datová služba Northwind a automaticky vygenerované třídy klientské datové služby. Tato služba a klientské datové třídy se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zavolat metodu <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> pro spuštění pole <xref:System.Data.Services.Client.DataServiceRequest%601> objektů, které obsahují dotazy, které vracejí `Customers` a `Products` objektů z datové služby Northwind. Kolekce objektů <xref:System.Data.Services.Client.QueryOperationResponse%601> v vrácených <xref:System.Data.Services.Client.DataServiceResponse> je tvořena výčtem a kolekce objektů obsažených v každém <xref:System.Data.Services.Client.QueryOperationResponse%601> je také vytvořena ve výčtu.  
  
 [!code-csharp[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#batchquery)]
 [!code-vb[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#batchquery)]  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
