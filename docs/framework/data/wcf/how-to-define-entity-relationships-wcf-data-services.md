---
title: 'Postupy: definování vztahů mezi entitami (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: cc255524-1534-4fae-b83c-250933d5a72b
ms.openlocfilehash: f693579883ae03a6c8df3e9a9f4941e1f9940a4c
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569124"
---
# <a name="how-to-define-entity-relationships-wcf-data-services"></a>Postupy: definování vztahů mezi entitami (WCF Data Services)
Když přidáte novou entitu v WCF Data Services, nebudou se automaticky definovat žádné relace mezi novou entitou a souvisejícími entitami. Můžete vytvořit a změnit vztahy mezi instancemi entit a klientské knihovny tyto změny odrážejí v datové službě. Další informace najdete v tématu [aktualizace datové služby](updating-the-data-service-wcf-data-services.md).  
  
 V příkladu v tomto tématu se používá ukázková datová služba Northwind a automaticky vygenerované třídy klientské datové služby. Tato služba a klientské datové třídy se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří novou instanci objektu a poté zavolá metodu <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> v <xref:System.Data.Services.Client.DataServiceContext>, aby vytvořila položku v kontextu spolu s odkazem na související pořadí. Do datové služby se pošle zpráva HTTP POST při volání metody <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít metodu <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> pro přidání objektu `Order_Details` do souvisejícího objektu `Orders` s odkazem na konkrétní objekt `Products`. Tyto relace definují metody <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> a <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>. V tomto příkladu jsou také explicitně nastaveny navigační vlastnosti objektu `Order_Details`.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorder)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorder)]  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
- [Postupy: Přidání, úpravy a odstranění entit](how-to-add-modify-and-delete-entities-wcf-data-services.md)
