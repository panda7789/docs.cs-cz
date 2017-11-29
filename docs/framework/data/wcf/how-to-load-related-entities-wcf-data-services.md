---
title: "Postupy: načtení entit v relaci (služby WCF Data Services)"
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
ms.assetid: 6f143d30-d997-4e6b-bcf0-d5c394ecb108
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 67f18d8dd9f25a5eb99f522ddd7942ff27dda497
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-load-related-entities-wcf-data-services"></a>Postupy: načtení entit v relaci (služby WCF Data Services)
Když potřebujete k načtení přidružených entit v [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], můžete použít <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> třídy. Můžete také <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> metodu <xref:System.Data.Services.Client.DataServiceQuery%601> vyžadovat, aby entit v relaci například načíst v odpovědi na stejný dotaz.  
  
 V příkladu v tomto tématu používá Northwind ukázková data služby a automaticky generovaný klienta dat služby třídy. Tato služba a datové třídy klienta se vytvoří při dokončení [rychlého startu služby WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak explicitně načíst `Customer` který souvisí s každou vrátil `Orders` instance.  
  
 [!code-csharp[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#loadrelatedordercustomer)]
 [!code-vb[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#loadrelatedordercustomer)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> metoda vrátí `Order Details` který patří do `Orders` vrácených dotazem.  
  
 [!code-csharp[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#expandorderdetails)]
 [!code-vb[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#expandorderdetails)]  
  
## <a name="see-also"></a>Viz také  
 [Dotaz na službu Data](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
