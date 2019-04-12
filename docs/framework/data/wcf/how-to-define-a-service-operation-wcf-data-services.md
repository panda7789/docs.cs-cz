---
title: 'Postupy: Definování operace služby (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
ms.openlocfilehash: fc738f7e81c02e44075ce5ed151ed42452650c94
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/12/2019
ms.locfileid: "59518120"
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a>Postupy: Definování operace služby (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Zveřejněte metody, které jsou definovány na serveru jako servisní operace. Operace služby umožňují datové služby a zajistit tak přístup prostřednictvím identifikátoru URI metodě, která je definována na serveru. K definování operace služby, použít [`WebGet]` nebo `[WebInvoke]` atribut do metody. Pro podporu operátorů dotazu, musí vrátit operace služby <xref:System.Linq.IQueryable%601> instance. Operace služby může přístup k podkladovému zdroji dat prostřednictvím <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> vlastnost <xref:System.Data.Services.DataService%601>. Další informace najdete v tématu [operací služby](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).  
  
 V příkladu v tomto tématu je definována operace služby s názvem `GetOrdersByCity` , která vrací vyfiltrované <xref:System.Linq.IQueryable%601> instanci `Orders` a související `Order_Details` objekty. V příkladu přistupuje <xref:System.Data.Objects.ObjectContext> instanci, která je zdrojem dat pro datová služba Northwind vzorku. Tato služba se vytvoří při dokončení [rychlý start služeb WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a>K definování operace služby v datová služba Northwind  
  
1. V projektu služby Northwind data otevřete soubor Northwind.svc.  
  
2. V `Northwind` tříd, definice služby operace metodu s názvem `GetOrdersByCity` následujícím způsobem:  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]  
  
3. V `InitializeService` metodu `Northwind` třídy, přidejte následující kód k umožnění přístupu k operace služby:  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]  
  
### <a name="to-query-the-getordersbycity-service-operation"></a>K dotazování GetOrdersByCity operace služby  
  
-   Ve webovém prohlížeči zadejte jeden z následujících identifikátorů URI k vyvolání operace služby, který je definován v následujícím příkladu:  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`  
  
## <a name="example"></a>Příklad  
 Následující příklad implementuje operace služby s názvem `GetOrderByCity` na datová služba Northwind. Tato operace používá rozhraní ADO.NET Entity Framework vrátit sadu `Orders` a související `Order_Details` objektů jako <xref:System.Linq.IQueryable%601> instance podle zadané město.  
  
> [!NOTE]
>  Operátory dotazu jsou podporované na tomto koncovém bodu služby operaci, protože metoda vrátí <xref:System.Linq.IQueryable%601> instance.  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperation)]
 [!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperation)]  
  
## <a name="see-also"></a>Viz také:

- [Definování datových služeb WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
