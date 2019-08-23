---
title: 'Postupy: Vytvoření datové služby pomocí zprostředkovatele reflexe (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: fb40a60850739147b2bf0f15a3babfe1d0dfa486
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965797"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a>Postupy: Vytvoření datové služby pomocí zprostředkovatele reflexe (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]umožňuje definovat datový model, který je založen na libovolných třídách, pokud jsou tyto třídy vystaveny jako objekty, které implementují <xref:System.Linq.IQueryable%601> rozhraní. Další informace najdete v tématu [poskytovatelé Data Services](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje datový model, který obsahuje `Orders` a. `Items` Třída `OrderItemData` kontejneru entity má dvě veřejné metody, které vracejí <xref:System.Linq.IQueryable%601> rozhraní. Tato rozhraní jsou sady `Orders` entit typů entit a. `Items` `Items` `Orders` `Items` Může obsahovat více, takže typ entity má vlastnost navigace, která vrací kolekci `Items` objektů. `Order` Třída kontejneru <xref:System.Data.Services.DataService%601> entityje`OrderItems` obecný typ třídy, ze které je datová služba odvozena. `OrderItemData`  
  
> [!NOTE]
> Vzhledem k tomu, že tento příklad ukazuje poskytovatele dat v paměti a změny nejsou zachovány mimo aktuální instance objektů, není implementováno žádné výhody odvozené od implementace <xref:System.Data.Services.IUpdatable> rozhraní. Příklad, který implementuje <xref:System.Data.Services.IUpdatable> rozhraní, naleznete v tématu [How to: Vytvořte datovou službu pomocí LINQ to SQL zdroje](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)dat.  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření datové služby pomocí LINQ to SQL zdroje dat](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)
- [Zprostředkovatelé datových služeb](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [Postupy: Vytvoření datové služby pomocí zdroje dat Entity Framework ADO.NET](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
