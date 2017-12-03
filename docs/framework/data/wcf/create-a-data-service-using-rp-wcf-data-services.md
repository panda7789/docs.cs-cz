---
title: "Postupy: vytvoření služby Data pomocí poskytovatele reflexe (služby WCF Data Services)"
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
helpviewer_keywords: WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 11f01a88e1d276321384f00f3e103322ccaef339
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a>Postupy: vytvoření služby Data pomocí poskytovatele reflexe (služby WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Umožňuje definovat datového modelu, který je založen na libovolný třídách tak dlouho, dokud tyto třídy jsou zveřejněné jako objekty, které implementují <xref:System.Linq.IQueryable%601> rozhraní. Další informace najdete v tématu [zprostředkovatelé dat služby](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu definuje datového modelu, který zahrnuje `Orders` a `Items`. Kontejner – třída entity `OrderItemData` má dvě veřejné metody, které vracejí <xref:System.Linq.IQueryable%601> rozhraní. Tato rozhraní jsou sady entit `Orders` a `Items` typy entit. `Order` Může obsahovat více `Items`, proto `Orders` typ entity má `Items` navigační vlastnost, která vrátí kolekci `Items` objekty. `OrderItemData` Třídy kontejneru entita je obecný typ <xref:System.Data.Services.DataService%601> třídu, ze které `OrderItems` služba dat je odvozený.  
  
> [!NOTE]
>  Protože tento příklad ukazuje poskytovatele dat v paměti a změny nejsou trvalé mimo aktuální instance objektů, nepřináší žádný užitek odvozené z implementace <xref:System.Data.Services.IUpdatable> rozhraní. Pro příklad, který implementuje <xref:System.Data.Services.IUpdatable> rozhraní najdete v tématu [postupy: vytvoření službu dat pomocí LINQ to SQL zdroj dat](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria reflection provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria reflection provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy: vytvoření služby dat pomocí LINQ ke zdroji dat SQL](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)  
 [Zprostředkovatelé dat služby](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [Postupy: vytvoření služby Data pomocí zdroje dat ADO.NET Entity Framework](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
