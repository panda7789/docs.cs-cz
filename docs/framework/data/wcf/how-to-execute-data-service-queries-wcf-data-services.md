---
title: 'Postupy: Provádění dotazů v datové služby (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- querying the data service [WCF Data Services]
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: 62997821-e0c6-4c4d-9fb7-1273fb5e5d18
ms.openlocfilehash: 47943392ec6628b6d5a67ac333dd6793f35857b8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645675"
---
# <a name="how-to-execute-data-service-queries-wcf-data-services"></a>Postupy: Provádění dotazů v datové služby (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] umožňuje dotazování dat služby z klienta na základě rozhraní .NET Framework aplikace s použitím tříd generované klientské datové služby. Provádění dotazů pomocí jedné z těchto metod:  
  
- Provádění dotazu LINQ na pojmenované <xref:System.Data.Services.Client.DataServiceQuery%601> , kterou získáte <xref:System.Data.Services.Client.DataServiceContext> , který `Add Data Service Reference` Nástroj generuje.  
  
- Implicitně vytyčením přes pojmenované <xref:System.Data.Services.Client.DataServiceQuery%601> , kterou získáte <xref:System.Data.Services.Client.DataServiceContext> , který `Add Data Service Reference` Nástroj generuje.  
  
- Explicitním voláním <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> metodu <xref:System.Data.Services.Client.DataServiceQuery%601>, nebo <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> metody pro asynchronní zpracování.  
  
 Další informace najdete v tématu [dotazování v datové službě](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 V příkladu v tomto tématu se používá Northwind ukázková data service a automaticky vygenerovaných tříd klientské datové služby. Tuto službu a třídy dat klientů jsou vytvořeny po dokončení [rychlý start služeb WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak definovat a spusťte dotaz LINQ, který vrátí všechny `Customers` proti datová služba Northwind.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomerslinq)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomerslinq)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít kontext, který `Add Data Service Reference` Nástroj generuje implicitně spustit dotaz, který vrátí všechny `Customers` proti datová služba Northwind. Identifikátor URI požadované `Customers` sady entit je automaticky určeno kontextu. Dotaz provádí implicitně, když dojde k výčtu.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomers)]
 [!code-vb[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomers)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití <xref:System.Data.Services.Client.DataServiceContext> explicitně spustit dotaz, který vrátí všechny `Customers` proti datová služba Northwind.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomersexplicit)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomersexplicit)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Přidání možností do dotazu v datové službě](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)
