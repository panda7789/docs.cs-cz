---
title: "Postupy: provádění dotazů služby dat (služby WCF Data Services)"
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
- querying the data service [WCF Data Services]
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: 62997821-e0c6-4c4d-9fb7-1273fb5e5d18
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 333c11150994ccdbe3dd6e8fd7349610d924806d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-execute-data-service-queries-wcf-data-services"></a>Postupy: provádění dotazů služby dat (služby WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Umožňuje dotazovat datové služby z klienta na základě rozhraní .NET Framework aplikace pomocí generovaného klienta datových služba tříd. Dotazy můžete spustit pomocí jedné z těchto metod:  
  
-   Provádění dotazů LINQ proti pojmenované <xref:System.Data.Services.Client.DataServiceQuery%601> které jste získali od <xref:System.Data.Services.Client.DataServiceContext> , `Add Data Service Reference` nástroj, který generuje.  
  
-   Implicitně vytyčením přes pojmenované <xref:System.Data.Services.Client.DataServiceQuery%601> které jste získali od <xref:System.Data.Services.Client.DataServiceContext> , `Add Data Service Reference` nástroj, který generuje.  
  
-   Explicitně, voláním <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> metodu <xref:System.Data.Services.Client.DataServiceQuery%601>, nebo <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> metody pro asynchronní zpracování.  
  
 Další informace najdete v tématu [dotaz na službu Data](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 V příkladu v tomto tématu používá Northwind ukázková data služby a automaticky generovaný klienta dat služby třídy. Tato služba a datové třídy klienta se vytvoří při dokončení [rychlého startu služby WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak definovat a provedení dotazu LINQ, která vrátí všechny `Customers` proti službu Northwind data.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomerslinq)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomerslinq)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít kontext, `Add Data Service Reference` nástroj, který generuje implicitně provést dotaz, který vrátí všechny `Customers` proti službu Northwind data. Identifikátor URI požadované `Customers` sady entit je určen automaticky podle kontextu. Dotaz je implicitně provést, když dojde k výčtu.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomers)]
 [!code-vb[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomers)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat <xref:System.Data.Services.Client.DataServiceContext> explicitně provést dotaz, který vrátí všechny `Customers` proti službu Northwind data.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomersexplicit)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomersexplicit)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Přidání možnosti dotazu k dotazu služby dat](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)
