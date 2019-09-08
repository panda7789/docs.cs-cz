---
title: 'Postupy: Přidání, úprava a odstranění entit (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: a00f8933-b232-4445-95ba-adc634f055d8
ms.openlocfilehash: 13c59bee9fc58dbe8c5b8c768fe9ff8b31d72e76
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780255"
---
# <a name="how-to-add-modify-and-delete-entities-wcf-data-services"></a>Postupy: Přidání, úprava a odstranění entit (WCF Data Services)
Pomocí klientských knihoven můžete vytvářet, aktualizovat a odstraňovat entity data v datové službě tím, že provádíte ekvivalentní akce s objekty <xref:System.Data.Services.Client.DataServiceContext>v. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Další informace najdete v tématu [aktualizace datové služby](updating-the-data-service-wcf-data-services.md).  
  
 V příkladu v tomto tématu se používá ukázková datová služba Northwind a automaticky vygenerované třídy klientské datové služby. Tato služba a klientské datové třídy se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří novou instanci objektu a poté zavolá <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> pro vytvoření položky v kontextu. Zpráva HTTP Post se pošle službě Data Service při <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> volání metody.  
  
 [!code-csharp[Astoria Northwind Client#AddProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addproduct)]
 [!code-vb[Astoria Northwind Client#AddProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addproduct)]  
  
## <a name="example"></a>Příklad  
 Následující příklad načte a upraví existující objekt a potom zavolá <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> na k označení položky v kontextu jako aktualizované. Zpráva sloučení http se pošle službě Data Service při <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> volání metody.  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#modifycustomer)]
 [!code-vb[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#modifycustomer)]  
  
## <a name="example"></a>Příklad  
 Následující příklad volá <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> na k označení položky v kontextu jako odstraněné. Po zavolání <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metody se do datové služby pošle zpráva HTTP DELETE.  
  
 [!code-csharp[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#deleteproduct)]
 [!code-vb[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#deleteproduct)]  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří novou instanci objektu a poté zavolá <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> pro vytvoření položky v kontextu spolu s odkazem na související pořadí. Zpráva HTTP Post se pošle službě Data Service při <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> volání metody.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
- [Postupy: Připojit existující entitu k DataServiceContext](attach-an-existing-entity-to-dc-wcf-data.md)
- [Postupy: Definování vztahů mezi entitami](how-to-define-entity-relationships-wcf-data-services.md)
- [Operace dávkování](batching-operations-wcf-data-services.md)
