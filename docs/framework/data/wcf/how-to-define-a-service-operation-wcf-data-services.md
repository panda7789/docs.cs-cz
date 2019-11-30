---
title: 'Postupy: definování operace služby (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
ms.openlocfilehash: e9d15698c1e020f5b4179efb3e8492f3754ff02f
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569132"
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a>Postupy: definování operace služby (WCF Data Services)

WCF Data Services vystavovat metody, které jsou definovány na serveru jako operace služby. Operace služby umožňují datové službě poskytovat přístup prostřednictvím identifikátoru URI metodě, která je definována na serveru. Chcete-li definovat operaci služby, použijte pro metodu atribut [`WebGet]` nebo `[WebInvoke]`. Aby bylo možné podporovat operátory dotazů, musí operace služby vracet instanci <xref:System.Linq.IQueryable%601>. Operace služby mohou přistupovat k základnímu zdroji dat prostřednictvím vlastnosti <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> v <xref:System.Data.Services.DataService%601>. Další informace najdete v tématu [provozní operace](service-operations-wcf-data-services.md).

Příklad v tomto tématu definuje operaci služby s názvem `GetOrdersByCity`, která vrací filtrovanou <xref:System.Linq.IQueryable%601> instanci `Orders` a související objekty `Order_Details`. Tento příklad přistupuje k instanci <xref:System.Data.Objects.ObjectContext>, která je zdrojem dat pro ukázkovou datovou službu Northwind. Tato služba se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).

### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a>Definování operace služby v datové službě Northwind

1. V projektu datové služby Northwind otevřete soubor Northwind. svc.

2. Ve třídě `Northwind` Definujte metodu operace služby s názvem `GetOrdersByCity` následujícím způsobem:

     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]

3. V metodě `InitializeService` `Northwind` třídy přidejte následující kód pro povolení přístupu k operaci služby:

     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]

### <a name="to-query-the-getordersbycity-service-operation"></a>Dotazování na operaci služby GetOrdersByCity

- Ve webovém prohlížeči zadejte jeden z následujících identifikátorů URI pro vyvolání operace služby, která je definována v následujícím příkladu:

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`

## <a name="example"></a>Příklad

Následující příklad implementuje operaci služby s názvem `GetOrderByCity` ve službě Northwind data Service. Tato operace používá Entity Framework ADO.NET k vrácení sady `Orders` a souvisejících `Order_Details` objektů jako instance <xref:System.Linq.IQueryable%601> na základě zadaného názvu města.

> [!NOTE]
> Operátory dotazů jsou podporovány u tohoto koncového bodu operace služby, protože metoda vrací instanci <xref:System.Linq.IQueryable%601>.

[!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperation)]
[!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperation)]

## <a name="see-also"></a>Viz také:

- [Definování datových služeb WCF Data Services](defining-wcf-data-services.md)
