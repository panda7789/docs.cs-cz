---
title: 'Postupy: Definování vztahů mezi entitami (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: cc255524-1534-4fae-b83c-250933d5a72b
ms.openlocfilehash: 63714f97e691b2ba0177a36a599b62ca7681dcf6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790645"
---
# <a name="how-to-define-entity-relationships-wcf-data-services"></a>Postupy: Definování vztahů mezi entitami (WCF Data Services)
Když přidáte novou entitu v [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], nebudou se automaticky definovat žádné relace mezi novou entitou a souvisejícími entitami. Můžete vytvořit a změnit vztahy mezi instancemi entit a klientské knihovny tyto změny odrážejí v datové službě. Další informace najdete v tématu [aktualizace datové služby](updating-the-data-service-wcf-data-services.md).  
  
 V příkladu v tomto tématu se používá ukázková datová služba Northwind a automaticky vygenerované třídy klientské datové služby. Tato služba a klientské datové třídy se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří novou instanci objektu a poté zavolá <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> pro vytvoření položky v kontextu spolu s odkazem na související pořadí. Zpráva HTTP Post se pošle službě Data Service při <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> volání metody.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> , jak použít metodu pro `Order_Details` přidání objektu do souvisejícího `Orders` objektu s odkazem na konkrétní `Products` objekt. Metody <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> a<xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> definují relace. V tomto příkladu jsou také explicitně nastaveny navigační vlastnosti `Order_Details` objektu.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorder)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorder)]  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
- [Postupy: Přidání, úprava a odstranění entit](how-to-add-modify-and-delete-entities-wcf-data-services.md)
