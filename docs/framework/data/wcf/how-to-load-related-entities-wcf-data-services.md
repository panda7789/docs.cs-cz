---
title: 'Postupy: Načíst související entity (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 6f143d30-d997-4e6b-bcf0-d5c394ecb108
ms.openlocfilehash: 14b0ba988c96c270610208a4f944083bb333eac5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780024"
---
# <a name="how-to-load-related-entities-wcf-data-services"></a>Postupy: Načíst související entity (WCF Data Services)
Pokud potřebujete načíst přidružené entity v [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]nástroji, můžete <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> použít metodu <xref:System.Data.Services.Client.DataServiceContext> třídy. Můžete také použít <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> metodu <xref:System.Data.Services.Client.DataServiceQuery%601> na, která vyžaduje, aby se související entity eagerly načetly ve stejné odpovědi na dotaz.  
  
 V příkladu v tomto tématu se používá ukázková datová služba Northwind a automaticky vygenerované třídy klientské datové služby. Tato služba a klientské datové třídy se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak explicitně načíst `Customer` , který souvisí s každou vrácenou `Orders` instancí.  
  
 [!code-csharp[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadrelatedordercustomer)]
 [!code-vb[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadrelatedordercustomer)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> metodu k vrácení `Order Details` , která patří do `Orders` vráceného dotazem.  
  
 [!code-csharp[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#expandorderdetails)]
 [!code-vb[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#expandorderdetails)]  
  
## <a name="see-also"></a>Viz také:

- [Dotazování v datové službě](querying-the-data-service-wcf-data-services.md)
