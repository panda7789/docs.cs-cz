---
title: 'Postupy: definování relací mezi Entity (služby WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: cc255524-1534-4fae-b83c-250933d5a72b
ms.openlocfilehash: 5658f83eb352327b63bc89db48afcf0f8aae3774
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33363989"
---
# <a name="how-to-define-entity-relationships-wcf-data-services"></a>Postupy: definování relací mezi Entity (služby WCF Data Services)
Když přidáte novou entitu v [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], nejsou automaticky definovány žádné vztahy mezi nové entity a související entity. Můžete vytvořit a změnit vztahy mezi instancí entit a mají klientské knihovny ve službě data tyto změny projevily. Další informace najdete v tématu [aktualizaci dat služby](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
 V příkladu v tomto tématu používá Northwind ukázková data služby a automaticky generovaný klienta dat služby třídy. Tato služba a datové třídy klienta se vytvoří při dokončení [rychlého startu služby WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří novou instanci objektu a potom zavolá <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> vytvořit položky v kontextu společně s odkaz na související pořadí. Zprávu HTTP POST posílá data služby, kdy <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda je volána.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> metoda pro přidání `Order_Details` objekt se souvisejícím `Orders` objekt s odkazem na konkrétní `Products` objektu. <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> a <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> metody definovat vztahy. V tomto příkladu navigační vlastnosti na `Order_Details` objekt jsou rovněž explicitně nastaven.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addorderdetailtoorder)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addorderdetailtoorder)]  
  
## <a name="see-also"></a>Viz také  
 [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [Postupy: Přidání, úpravy a odstranění entit](../../../../docs/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services.md)
