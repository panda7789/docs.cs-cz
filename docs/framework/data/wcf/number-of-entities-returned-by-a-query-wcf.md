---
title: "Postupy: určení počtu entity vrácené dotazem (služby WCF Data Services)"
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
helpviewer_keywords: WCF Data Services, row count
ms.assetid: 03d41a82-df95-40ac-8439-a6c327d37ba8
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4d8378cbf6f874e777ce03255962ea4c873449d7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-determine-the-number-of-entities-returned-by-a-query-wcf-data-services"></a>Postupy: určení počtu entity vrácené dotazem (služby WCF Data Services)
S [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], můžete určit počet entit, které jsou v zadaný identifikátor URI dotazu na sadu entit. Tento počet může být zahrnuta, společně s výsledek dotazu nebo jako celočíselnou hodnotu. Další informace najdete v tématu [dotaz na službu Data](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 V příkladu v tomto tématu používá Northwind ukázková data služby a automaticky generovaný klienta dat služby třídy. Tato služba a datové třídy klienta se vytvoří při dokončení [rychlého startu služby WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se provede dotaz po volání <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> metoda. <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> Vlastnost vrací počet entit v `Customers` sady entit.  
  
 [!code-csharp[Astoria Northwind Client#CountAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#countallcustomers)]
 [!code-vb[Astoria Northwind Client#CountAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#countallcustomers)]  
  
## <a name="example"></a>Příklad  
 Tento příklad volá <xref:System.Linq.Enumerable.Count%2A> metoda vrátí pouze celočíselnou hodnotu to znamená počet entit v `Customers` sady entit.  
  
 [!code-csharp[Astoria Northwind Client#CountAllCustomersValueOnly](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#countallcustomersvalueonly)]
 [!code-vb[Astoria Northwind Client#CountAllCustomersValueOnly](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#countallcustomersvalueonly)]  
  
## <a name="see-also"></a>Viz také  
 [Dotaz na službu Data](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
