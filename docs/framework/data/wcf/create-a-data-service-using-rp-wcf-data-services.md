---
title: 'Postupy: Vytvoření datové služby pomocí zprostředkovatele reflexe (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: feee679c37cd3dafb80021752ee25444c54f0809
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791007"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a>Postupy: Vytvoření datové služby pomocí zprostředkovatele reflexe (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]umožňuje definovat datový model, který je založen na libovolných třídách, pokud jsou tyto třídy vystaveny jako objekty, které implementují <xref:System.Linq.IQueryable%601> rozhraní. Další informace najdete v tématu [poskytovatelé Data Services](data-services-providers-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje datový model, který obsahuje `Orders` a. `Items` Třída `OrderItemData` kontejneru entity má dvě veřejné metody, které vracejí <xref:System.Linq.IQueryable%601> rozhraní. Tato rozhraní jsou sady `Orders` entit typů entit a. `Items` `Items` `Orders` `Items` Může obsahovat více, takže typ entity má vlastnost navigace, která vrací kolekci `Items` objektů. `Order` Třída kontejneru <xref:System.Data.Services.DataService%601> entityje`OrderItems` obecný typ třídy, ze které je datová služba odvozena. `OrderItemData`  
  
> [!NOTE]
> Vzhledem k tomu, že tento příklad ukazuje poskytovatele dat v paměti a změny nejsou zachovány mimo aktuální instance objektů, není implementováno žádné výhody odvozené od implementace <xref:System.Data.Services.IUpdatable> rozhraní. Příklad, který implementuje <xref:System.Data.Services.IUpdatable> rozhraní, naleznete v tématu [How to: Vytvořte datovou službu pomocí LINQ to SQL zdroje](create-a-data-service-using-linq-to-sql-wcf.md)dat.  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření datové služby pomocí LINQ to SQL zdroje dat](create-a-data-service-using-linq-to-sql-wcf.md)
- [Zprostředkovatelé datových služeb](data-services-providers-wcf-data-services.md)
- [Postupy: Vytvoření datové služby pomocí zdroje dat Entity Framework ADO.NET](create-a-data-service-using-an-adonet-ef-data-wcf.md)
