---
title: 'Postupy: spouštění dotazů datové služby (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- querying the data service [WCF Data Services]
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: 62997821-e0c6-4c4d-9fb7-1273fb5e5d18
ms.openlocfilehash: b06a21a45dcf6e67c41287c4cd59cdda4aa7b447
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569085"
---
# <a name="how-to-execute-data-service-queries-wcf-data-services"></a>Postupy: spouštění dotazů datové služby (WCF Data Services)
WCF Data Services umožňuje dotazovat se na datovou službu z klientské aplikace založené na .NET Framework pomocí vygenerovaných tříd klientské datové služby. Dotazy můžete spouštět pomocí jedné z těchto metod:  
  
- Spouští se dotaz LINQ proti pojmenovanému <xref:System.Data.Services.Client.DataServiceQuery%601>, který získáte z <xref:System.Data.Services.Client.DataServiceContext>, který vygeneruje nástroj pro `Add Data Service Reference`.  
  
- Implicitně na základě výčtu pojmenovaných <xref:System.Data.Services.Client.DataServiceQuery%601>, které získáte z <xref:System.Data.Services.Client.DataServiceContext>, který vygeneruje nástroj pro `Add Data Service Reference`.  
  
- Explicitně, voláním metody <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> v <xref:System.Data.Services.Client.DataServiceQuery%601>nebo metody <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> pro asynchronní spuštění.  
  
 Další informace najdete v tématu [dotazování datové služby](querying-the-data-service-wcf-data-services.md).  
  
 V příkladu v tomto tématu se používá ukázková datová služba Northwind a automaticky vygenerované třídy klientské datové služby. Tato služba a klientské datové třídy se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak definovat a spustit dotaz LINQ, který vrátí všechny `Customers`y proti datové službě Northwind.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomerslinq)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomerslinq)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít kontext, který nástroj `Add Data Service Reference` generuje pro implicitní provedení dotazu, který vrátí všechny `Customers`y proti datové službě Northwind. Identifikátor URI požadované sady entit `Customers` je automaticky určen kontextem. Dotaz se spustí implicitně, když dojde ke výčtu.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomers)]
 [!code-vb[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomers)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít <xref:System.Data.Services.Client.DataServiceContext> k explicitnímu provedení dotazu, který vrátí všechny `Customers`y proti datové službě Northwind.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomersexplicit)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomersexplicit)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Přidání možností do dotazu v datové službě](how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)
