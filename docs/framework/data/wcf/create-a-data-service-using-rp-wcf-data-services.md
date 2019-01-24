---
title: 'Postupy: Vytvoření datové služby pomocí zprostředkovatel reflexe (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: 723f4759f8f3f0152e08b46163545b833727d2d8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691739"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a>Postupy: Vytvoření datové služby pomocí zprostředkovatel reflexe (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Umožňuje definovat datový model, který je založen na libovolné třídy tak dlouho, dokud tyto třídy jsou vystaveny jako objekty, které implementují <xref:System.Linq.IQueryable%601> rozhraní. Další informace najdete v tématu [zprostředkovatelé dat služby](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje datový model, který zahrnuje `Orders` a `Items`. Třída kontejneru entity `OrderItemData` má dvě veřejné metody, které vracejí <xref:System.Linq.IQueryable%601> rozhraní. Tato rozhraní jsou sady entit `Orders` a `Items` typy entit. `Order` Může obsahovat více `Items`, takže `Orders` má typ entity `Items` vlastnost navigace, která vrátí kolekci `Items` objekty. `OrderItemData` Třída kontejneru entity je obecný typ <xref:System.Data.Services.DataService%601> třídu, ze které `OrderItems` datové služby je odvozený.  
  
> [!NOTE]
>  Protože tento příklad ukazuje poskytovatele dat v paměti a nejsou trvalé změny mimo aktuální instance objektů, neexistuje žádný přínos odvozen od implementace <xref:System.Data.Services.IUpdatable> rozhraní. Příklad, který implementuje <xref:System.Data.Services.IUpdatable> rozhraní najdete v tématu [jak: Vytvoření datové služby pomocí LINQ ke zdroji dat SQL](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria reflection provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria reflection provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Vytvoření datové služby pomocí LINQ ke zdroji dat SQL](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)
- [Zprostředkovatelé datových služeb](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [Postupy: Vytvoření datové služby pomocí zdroje dat rozhraní ADO.NET Entity Framework](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
