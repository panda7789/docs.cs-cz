---
title: "Postupy: provádění dotazů v dávce (služby WCF Data Services)"
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
helpviewer_keywords: WCF Data Services, batch requests
ms.assetid: 3b4db7df-bd33-43a1-8ea4-63a18e131f97
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 01dfb1ac10bdc54f682df4b8af66ba4fd507b705
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-execute-queries-in-a-batch-wcf-data-services"></a>Postupy: provádění dotazů v dávce (služby WCF Data Services)
Pomocí [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientské knihovny, můžete spustit více než jeden dotaz službu data v jedné dávce. Další informace najdete v tématu [dávkování operací](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md).  
  
 V příkladu v tomto tématu používá Northwind ukázková data služby a automaticky generovaný klienta dat služby třídy. Tato služba a datové třídy klienta se vytvoří při dokončení [rychlého startu služby WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob volání <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> metodu provést. pole <xref:System.Data.Services.Client.DataServiceRequest%601> objekty, které obsahuje dotazy, které vracejí obě `Customers` a `Products` objekty ze služby Northwind data. Kolekce <xref:System.Data.Services.Client.QueryOperationResponse%601> objekty ve vráceném <xref:System.Data.Services.Client.DataServiceResponse> je výčet a kolekce objektů v každém <xref:System.Data.Services.Client.QueryOperationResponse%601> je taky vytvořit její výčet.  
  
 [!code-csharp[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#batchquery)]
 [!code-vb[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#batchquery)]  
  
## <a name="see-also"></a>Viz také  
 [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
