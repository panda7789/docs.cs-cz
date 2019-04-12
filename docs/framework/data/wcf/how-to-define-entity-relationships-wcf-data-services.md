---
title: 'Postupy: Definování vztahů mezi entitami (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: cc255524-1534-4fae-b83c-250933d5a72b
ms.openlocfilehash: 3bd2293f02e77ab2db5c3ba245596021e08b04c8
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/12/2019
ms.locfileid: "59517818"
---
# <a name="how-to-define-entity-relationships-wcf-data-services"></a>Postupy: Definování vztahů mezi entitami (WCF Data Services)
Když přidáte novou entitu v [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], případné relace mezi nové entity a související entity nejsou definovány automaticky. Můžete vytvořit a změnit vztahy mezi instancí entit a mít klientská knihovna odrážet provedené změny ve službě data. Další informace najdete v tématu [aktualizace datové služby](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
 V příkladu v tomto tématu se používá Northwind ukázková data service a automaticky vygenerovaných tříd klientské datové služby. Tuto službu a třídy dat klientů jsou vytvořeny po dokončení [rychlý start služeb WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří novou instanci objektu a pak zavolá <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> vytvoření položky v rámci spolu se odkaz na související objednávky. Zpráva HTTP POST posílá data provozu, jestliže <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda je volána.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> metoda pro přidání `Order_Details` objektu se souvisejícím `Orders` objektu s odkazem na konkrétní `Products` objektu. <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> a <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> metod definuje vztahy. V tomto příkladu, navigačních vlastností na `Order_Details` objektu jsou také explicitně nastavit.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorder)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorder)]  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Postupy: Přidání, úpravy a odstranění entit](../../../../docs/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services.md)
