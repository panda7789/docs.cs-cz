---
title: 'Postupy: Přidání, úpravy a odstranění entit (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: a00f8933-b232-4445-95ba-adc634f055d8
ms.openlocfilehash: 66f115bf3bf51b4b5612240c4e34eaf9e08bec0d
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/12/2019
ms.locfileid: "59518081"
---
# <a name="how-to-add-modify-and-delete-entities-wcf-data-services"></a>Postupy: Přidání, úpravy a odstranění entit (WCF Data Services)
S [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientské knihovny, můžete vytvořit, aktualizovat a odstranit dat entity v datové služby pomocí odpovídající akce u objektů v <xref:System.Data.Services.Client.DataServiceContext>. Další informace najdete v tématu [aktualizace datové služby](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
 V příkladu v tomto tématu se používá Northwind ukázková data service a automaticky vygenerovaných tříd klientské datové služby. Tuto službu a třídy dat klientů jsou vytvořeny po dokončení [rychlý start služeb WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří novou instanci objektu a pak zavolá <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> vytvoření položky v kontextu. Zpráva HTTP POST posílá data provozu, jestliže <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda je volána.  
  
 [!code-csharp[Astoria Northwind Client#AddProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addproduct)]
 [!code-vb[Astoria Northwind Client#AddProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addproduct)]  
  
## <a name="example"></a>Příklad  
 Následující příklad načte a upraví existující objekt a poté zavolá <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> a označovat položky v rámci jako aktualizovat. Zpráva HTTP sloučit posílá data provozu, jestliže <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda je volána.  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#modifycustomer)]
 [!code-vb[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#modifycustomer)]  
  
## <a name="example"></a>Příklad  
 Následující příklad volá <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> k označení položek v rámci jako odstraněný. Zpráva požadavku HTTP DELETE posílá data provozu, jestliže <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda je volána.  
  
 [!code-csharp[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#deleteproduct)]
 [!code-vb[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#deleteproduct)]  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří novou instanci objektu a pak zavolá <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> vytvoření položky v rámci spolu se odkaz na související objednávky. Zpráva HTTP POST posílá data provozu, jestliže <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda je volána.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Postupy: Přiřazení existující Entity k prvku DataServiceContext](../../../../docs/framework/data/wcf/attach-an-existing-entity-to-dc-wcf-data.md)
- [Postupy: Definování vztahů mezi entitami](../../../../docs/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services.md)
- [Operace dávkování](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)
