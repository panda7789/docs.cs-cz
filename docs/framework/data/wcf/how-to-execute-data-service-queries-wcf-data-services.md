---
title: 'Postupy: Spustit dotazy datové služby (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- querying the data service [WCF Data Services]
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: 62997821-e0c6-4c4d-9fb7-1273fb5e5d18
ms.openlocfilehash: 984bba9f31ddaee68c6997ba6da09a511e42b4ce
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780074"
---
# <a name="how-to-execute-data-service-queries-wcf-data-services"></a>Postupy: Spustit dotazy datové služby (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]umožňuje zadávat dotazy na datovou službu z .NET Framework klientské aplikace založené na vygenerovaných třídách klientské datové služby. Dotazy můžete spouštět pomocí jedné z těchto metod:  
  
- Provádění dotazu LINQ proti pojmenovanému <xref:System.Data.Services.Client.DataServiceQuery%601> , které získáte <xref:System.Data.Services.Client.DataServiceContext> z `Add Data Service Reference` nástroje, který vygeneruje nástroj.  
  
- Implicitně pomocí výčtu nad názvem <xref:System.Data.Services.Client.DataServiceQuery%601> , který jste získali <xref:System.Data.Services.Client.DataServiceContext> z `Add Data Service Reference` nástroje, který vygeneruje nástroj.  
  
- Explicitně, voláním <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> metody <xref:System.Data.Services.Client.DataServiceQuery%601>na, nebo <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> metodou pro asynchronní provádění.  
  
 Další informace najdete v tématu [dotazování datové služby](querying-the-data-service-wcf-data-services.md).  
  
 V příkladu v tomto tématu se používá ukázková datová služba Northwind a automaticky vygenerované třídy klientské datové služby. Tato služba a klientské datové třídy se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak definovat a spustit dotaz LINQ, který vrátí vše `Customers` proti datové službě Northwind.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomerslinq)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomerslinq)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít kontext, který `Add Data Service Reference` Nástroj generuje pro implicitní provedení dotazu, který vrátí vše `Customers` proti datové službě Northwind. Identifikátor URI požadované `Customers` sady entit je automaticky určen kontextem. Dotaz se spustí implicitně, když dojde ke výčtu.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomers)]
 [!code-vb[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomers)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít <xref:System.Data.Services.Client.DataServiceContext> k explicitnímu provedení dotazu, který vrátí vše `Customers` proti datové službě Northwind.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomersexplicit)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomersexplicit)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Přidání možností dotazu do dotazu datové služby](how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)
