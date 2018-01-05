---
title: "Postupy: Definování operace služby (služby WCF Data Services)"
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
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 03dc0b774fe6c3e077fa539fc14c7df4a1fb448d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a>Postupy: Definování operace služby (služby WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]vystavení metody, které jsou definovány na serveru jako operací služby. Operace služby povolit datové služby poskytovat přístup pomocí identifikátoru URI na metodu, která je definován na serveru. Chcete-li definovat operace služby, použít [`WebGet]` nebo `[WebInvoke]` atribut do metody. Pro podporu operátory dotazu, musí vracet operace služby <xref:System.Linq.IQueryable%601> instance. Operace služby může přístup ke zdroji dat základní prostřednictvím <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> vlastnost <xref:System.Data.Services.DataService%601>. Další informace najdete v tématu [operací služby](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).  
  
 V příkladu v tomto tématu definuje operace služby s názvem `GetOrdersByCity` , který vrací vyfiltrované <xref:System.Linq.IQueryable%601> instanci `Orders` a související `Order_Details` objekty. V příkladu přistupuje <xref:System.Data.Objects.ObjectContext> instance, který je zdrojem dat pro službu Northwind ukázková data. Tato služba se vytvoří při dokončení [rychlého startu služby WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a>Chcete-li definovat operace služby ve službě data Northwind  
  
1.  V projektu služby Northwind data otevřete soubor Northwind.svc.  
  
2.  V `Northwind` třídy, definování metody operace služby s názvem `GetOrdersByCity` následujícím způsobem:  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationdef)]  
  
3.  V `InitializeService` metodu `Northwind` třídy, přidejte následující kód k povolení přístupu k operaci služby:  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationconfig)]  
  
### <a name="to-query-the-getordersbycity-service-operation"></a>K dotazování GetOrdersByCity operaci služby  
  
-   Ve webovém prohlížeči zadejte jeden z následujících identifikátorů URI k vyvolání operace služby, která je definována v následujícím příkladu:  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`  
  
## <a name="example"></a>Příklad  
 Následující příklad implementuje operace služby s názvem `GetOrderByCity` na službu Northwind data. Tato operace používá k vrácení sadu ADO.NET Entity Framework `Orders` a související `Order_Details` objekty jako <xref:System.Linq.IQueryable%601> instance na základě zadané města názvu.  
  
> [!NOTE]
>  Operátory dotazu jsou podporována pro tento koncový bod služby operaci, protože metoda vrátí <xref:System.Linq.IQueryable%601> instance.  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperation)]
 [!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperation)]  
  
## <a name="see-also"></a>Viz také  
 [Definování datových služeb WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
