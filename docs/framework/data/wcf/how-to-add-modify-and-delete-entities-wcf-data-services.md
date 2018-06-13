---
title: 'Postupy: přidat, upravit a odstranit entity (služby WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: a00f8933-b232-4445-95ba-adc634f055d8
ms.openlocfilehash: 4475d8767226a810c7b6f7d8949e9cbe2d846cca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356508"
---
# <a name="how-to-add-modify-and-delete-entities-wcf-data-services"></a>Postupy: přidat, upravit a odstranit entity (služby WCF Data Services)
Pomocí [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientské knihovny, můžete vytvořit, aktualizovat a odstranit data entity v datové služby provedením ekvivalentní akce u objektů v <xref:System.Data.Services.Client.DataServiceContext>. Další informace najdete v tématu [aktualizaci dat služby](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
 V příkladu v tomto tématu používá Northwind ukázková data služby a automaticky generovaný klienta dat služby třídy. Tato služba a datové třídy klienta se vytvoří při dokončení [rychlého startu služby WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří novou instanci objektu a potom zavolá <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> vytvořit položky v kontextu. Zprávu HTTP POST posílá data služby, kdy <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda je volána.  
  
 [!code-csharp[Astoria Northwind Client#AddProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addproduct)]
 [!code-vb[Astoria Northwind Client#AddProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addproduct)]  
  
## <a name="example"></a>Příklad  
 Následující příklad načte a upraví stávající objekt a potom zavolá <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> označit položku v kontextu jako aktualizovat. Zprávu HTTP SLOUČENÍ posílá data služby, kdy <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda je volána.  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#modifycustomer)]
 [!code-vb[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#modifycustomer)]  
  
## <a name="example"></a>Příklad  
 Následující příklad volání <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> označit položku v kontextu, jako je odstranit. Zprávu HTTP DELETE posílá data služby, kdy <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda je volána.  
  
 [!code-csharp[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#deleteproduct)]
 [!code-vb[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#deleteproduct)]  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří novou instanci objektu a potom zavolá <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> vytvořit položky v kontextu společně s odkaz na související pořadí. Zprávu HTTP POST posílá data služby, kdy <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda je volána.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="see-also"></a>Viz také  
 [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [Postupy: Přiřazení existující entity k prvku DataServiceContext](../../../../docs/framework/data/wcf/attach-an-existing-entity-to-dc-wcf-data.md)  
 [Postupy: Definování relací mezi entitami](../../../../docs/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services.md)  
 [Operace dávkování](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)
