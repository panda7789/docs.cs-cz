---
title: 'Postupy: Přidání, úpravy a odstranění entit (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: a00f8933-b232-4445-95ba-adc634f055d8
ms.openlocfilehash: 501bec59a61b51ec4bece4b0ce2f941189b35ed0
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569202"
---
# <a name="how-to-add-modify-and-delete-entities-wcf-data-services"></a>Postupy: Přidání, úpravy a odstranění entit (WCF Data Services)
Pomocí klientských knihoven WCF Data Services můžete data entit vytvářet, aktualizovat a odstraňovat v datové službě tím, že provádíte ekvivalentní akce s objekty v <xref:System.Data.Services.Client.DataServiceContext>. Další informace najdete v tématu [aktualizace datové služby](updating-the-data-service-wcf-data-services.md).  
  
 V příkladu v tomto tématu se používá ukázková datová služba Northwind a automaticky vygenerované třídy klientské datové služby. Tato služba a klientské datové třídy se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří novou instanci objektu a poté zavolá metodu <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> v <xref:System.Data.Services.Client.DataServiceContext> k vytvoření položky v kontextu. Do datové služby se pošle zpráva HTTP POST při volání metody <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>.  
  
 [!code-csharp[Astoria Northwind Client#AddProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addproduct)]
 [!code-vb[Astoria Northwind Client#AddProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addproduct)]  
  
## <a name="example"></a>Příklad  
 Následující příklad načte a upraví existující objekt a potom zavolá metodu <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> v <xref:System.Data.Services.Client.DataServiceContext> k označení položky v kontextu jako aktualizovaného. Do datové služby se pošle zpráva o sloučení HTTP při volání metody <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>.  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#modifycustomer)]
 [!code-vb[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#modifycustomer)]  
  
## <a name="example"></a>Příklad  
 Následující příklad volá metodu <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> v <xref:System.Data.Services.Client.DataServiceContext> k označení položky v kontextu jako odstraněné. Při volání metody <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> se do datové služby pošle zpráva o odstranění protokolu HTTP.  
  
 [!code-csharp[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#deleteproduct)]
 [!code-vb[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#deleteproduct)]  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří novou instanci objektu a poté zavolá metodu <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> v <xref:System.Data.Services.Client.DataServiceContext>, aby vytvořila položku v kontextu spolu s odkazem na související pořadí. Do datové služby se pošle zpráva HTTP POST při volání metody <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
- [Postupy: Přiřazení existující entity k prvku DataServiceContext](attach-an-existing-entity-to-dc-wcf-data.md)
- [Postupy: Definování relací mezi entitami](how-to-define-entity-relationships-wcf-data-services.md)
- [Operace dávkování](batching-operations-wcf-data-services.md)
