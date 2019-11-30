---
title: 'Postupy: načtení souvisejících entit (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 6f143d30-d997-4e6b-bcf0-d5c394ecb108
ms.openlocfilehash: 84c2448f317e813a95688feaaac1c97436de1b16
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569019"
---
# <a name="how-to-load-related-entities-wcf-data-services"></a>Postupy: načtení souvisejících entit (WCF Data Services)
Pokud potřebujete načíst přidružené entity v WCF Data Services, můžete použít metodu <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> třídy <xref:System.Data.Services.Client.DataServiceContext>. Metodu <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> v <xref:System.Data.Services.Client.DataServiceQuery%601> můžete použít také k vyžadování toho, aby se související entity eagerly zavedly do stejné odpovědi na dotaz.  
  
 V příkladu v tomto tématu se používá ukázková datová služba Northwind a automaticky vygenerované třídy klientské datové služby. Tato služba a klientské datové třídy se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak explicitně načíst `Customer`, která souvisí s každou vrácenou `Orders` instanci.  
  
 [!code-csharp[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadrelatedordercustomer)]
 [!code-vb[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadrelatedordercustomer)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít metodu <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> pro vrácení `Order Details`, které patří do `Orders` vrácených dotazem.  
  
 [!code-csharp[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#expandorderdetails)]
 [!code-vb[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#expandorderdetails)]  
  
## <a name="see-also"></a>Viz také:

- [Dotazování v datové službě](querying-the-data-service-wcf-data-services.md)
