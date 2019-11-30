---
title: 'Postupy: vytvoření datové služby pomocí zprostředkovatele reflexe (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: cf20c1d27f22c0248217541763eaa617ed9493db
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569281"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a>Postupy: vytvoření datové služby pomocí zprostředkovatele reflexe (WCF Data Services)
WCF Data Services umožňuje definovat datový model, který je založen na libovolných třídách, pokud jsou tyto třídy vystaveny jako objekty, které implementují rozhraní <xref:System.Linq.IQueryable%601>. Další informace najdete v tématu [poskytovatelé Data Services](data-services-providers-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje datový model, který obsahuje `Orders` a `Items`. Třída kontejneru entity `OrderItemData` má dvě veřejné metody, které vracejí <xref:System.Linq.IQueryable%601> rozhraní. Tato rozhraní jsou sady entit `Orders` a `Items` typy entit. `Order` může zahrnovat více `Items`, takže typ entity `Orders` má vlastnost navigace `Items`, která vrací kolekci `Items` objektů. Třída kontejneru `OrderItemData` entit je obecný typ <xref:System.Data.Services.DataService%601> třídy, ze které je odvozena `OrderItems` datová služba.  
  
> [!NOTE]
> Vzhledem k tomu, že tento příklad ukazuje poskytovatele dat v paměti a změny nejsou zachovány mimo aktuální instance objektů, není implementováno žádné výhody odvozené od implementace rozhraní <xref:System.Data.Services.IUpdatable>. Příklad, který implementuje rozhraní <xref:System.Data.Services.IUpdatable>, naleznete v tématu [How to: Create a data Service using a LINQ to SQL source data](create-a-data-service-using-linq-to-sql-wcf.md).  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření datové služby pomocí zdroje dat LINQ to SQL](create-a-data-service-using-linq-to-sql-wcf.md)
- [Zprostředkovatelé datových služeb](data-services-providers-wcf-data-services.md)
- [Postupy: Vytvoření datové služby pomocí zdroje dat ADO.NET Entity Framework](create-a-data-service-using-an-adonet-ef-data-wcf.md)
