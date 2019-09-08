---
title: 'Postupy: Definovat operaci služby (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
ms.openlocfilehash: 3154fadeda400440f68a184b430b7ff15a02203d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780086"
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a>Postupy: Definovat operaci služby (WCF Data Services)

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Vystavte metody, které jsou definovány na serveru jako operace služby. Operace služby umožňují datové službě poskytovat přístup prostřednictvím identifikátoru URI metodě, která je definována na serveru. Chcete-li definovat operaci služby, použijte atribut`WebGet]` [ `[WebInvoke]` nebo pro metodu. Aby bylo možné podporovat operátory dotazů, musí operace služby vracet <xref:System.Linq.IQueryable%601> instanci. Operace služby mohou přistupovat k základnímu zdroji dat prostřednictvím <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> vlastnosti <xref:System.Data.Services.DataService%601>v. Další informace najdete v tématu [provozní operace](service-operations-wcf-data-services.md).

Příklad v tomto tématu definuje operaci služby s `GetOrdersByCity` názvem, která vrací filtrovanou <xref:System.Linq.IQueryable%601> instanci `Orders` a související `Order_Details` objekty. V příkladu se přistupuje k <xref:System.Data.Objects.ObjectContext> instanci, která je zdrojem dat pro ukázkovou datovou službu Northwind. Tato služba se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).

### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a>Definování operace služby v datové službě Northwind

1. V projektu datové služby Northwind otevřete soubor Northwind. svc.

2. Ve třídě Definujte metodu operace služby s názvem `GetOrdersByCity` následujícím způsobem: `Northwind`

     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]

3. `InitializeService` V metodě `Northwind` třídy přidejte následující kód pro povolení přístupu k operaci služby:

     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]

### <a name="to-query-the-getordersbycity-service-operation"></a>Dotazování na operaci služby GetOrdersByCity

- Ve webovém prohlížeči zadejte jeden z následujících identifikátorů URI pro vyvolání operace služby, která je definována v následujícím příkladu:

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`

## <a name="example"></a>Příklad

Následující příklad implementuje operaci služby s názvem `GetOrderByCity` ve službě Northwind data Service. Tato operace používá Entity Framework ADO.NET k vrácení sady `Orders` a souvisejících `Order_Details` objektů jako <xref:System.Linq.IQueryable%601> instance na základě zadaného názvu města.

> [!NOTE]
> Operátory dotazů jsou podporovány u tohoto koncového bodu operace služby, protože metoda <xref:System.Linq.IQueryable%601> vrací instanci.

[!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperation)]
[!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperation)]

## <a name="see-also"></a>Viz také:

- [Definování datových služeb WCF Data Services](defining-wcf-data-services.md)
