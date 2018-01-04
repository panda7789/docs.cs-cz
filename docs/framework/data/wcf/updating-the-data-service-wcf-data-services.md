---
title: "Aktualizaci dat služby (služby WCF Data Services)"
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
helpviewer_keywords:
- WCF Data Services, changing data
- WCF Data Services, client library
ms.assetid: 00d993be-ffed-4dea-baf7-6eea982cdb54
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bc8041dee12c8300e18e6321c717cbd80b93d650
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="updating-the-data-service-wcf-data-services"></a>Aktualizaci dat služby (služby WCF Data Services)
Při použití [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientské knihovny využívat [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] kanálu, knihovny překládá položek v informačním kanálu do instance třídy služeb dat klienta. Tyto datové služby třídy jsou sledovány pomocí <xref:System.Data.Services.Client.DataServiceContext> ke kterému <xref:System.Data.Services.Client.DataServiceQuery%601> patří. Klient sleduje změny entit, které ohlásíte pomocí metody na <xref:System.Data.Services.Client.DataServiceContext>. Tyto metody povolit klientovi sledovat entity added a odstranila a taky změny, které provedete na hodnoty vlastnosti nebo vztahy mezi instancí entit. Tyto sledované změny jsou odesílány zpět ke službě data jako založené na REST operace při volání <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda.  
  
> [!NOTE]
>  Při použití instance <xref:System.Data.Services.Client.DataServiceCollection%601> k vytvoření vazby dat s ovládacími prvky, jsou změny dat v ovládacím prvku vázané automaticky oznamovány <xref:System.Data.Services.Client.DataServiceContext>. Další informace najdete v tématu [vazby dat k ovládacím prvkům](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).  
  
## <a name="adding-modifying-and-changing-entities"></a>Přidání, úpravy a změna entit  
 Při použití **přidat odkaz na službu** dialogové okno v sadě Visual Studio se přidat odkaz na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu, mají výsledné klienta dat služby třídy každou statickou *vytvořit* metody, která přijímá jeden parametr pro každou vlastnost neumožňující hodnotu Null entity. Tato metoda slouží k vytvoření instance entity typu třídy, jako v následujícím příkladu:  
  
 [!code-csharp[Astoria Northwind Client#CreateNewProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#createnewproduct)]
 [!code-vb[Astoria Northwind Client#CreateNewProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#createnewproduct)]  
  
 Chcete-li přidat instanci entity, volejte odpovídající *AddTo* metodu <xref:System.Data.Services.Client.DataServiceContext> generované třídy **přidat odkaz na službu** dialogové okno, jako v následujícím příkladu:  
  
 [!code-csharp[Astoria Northwind Client#AddProductSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addproductspecific)]
 [!code-vb[Astoria Northwind Client#AddProductSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addproductspecific)]  
  
 Tento postup přidá objekt do kontextu a do sady entit správné. Můžete také volat <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A>, ale místo toho je nutné zadat název sady entit. Pokud přidané entita má jeden nebo více vztahů s dalšími subjekty, můžete použít <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> metoda nebo použijte jednu z výše uvedených metod a také explicitně definujte tyto odkazy. Tyto operace jsou popsány dále v tomto tématu.  
  
 Pokud chcete upravit existující instanci entity, první dotaz pro tuto entitu, proveďte požadované změny na její vlastnosti a pak zavolají <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> a informuje klientské knihovny, která je nutné odeslat aktualizaci pro tento objekt, jak je znázorněno v v následujícím příkladu:  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomerSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#modifycustomerspecific)]
 [!code-vb[Astoria Northwind Client#ModifyCustomerSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#modifycustomerspecific)]  
  
 Chcete-li odstranit instanci entity, zavolejte <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> metodu <xref:System.Data.Services.Client.DataServiceContext>, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[Astoria Northwind Client#DeleteProductSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#deleteproductspecific)]
 [!code-vb[Astoria Northwind Client#DeleteProductSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#deleteproductspecific)]  
  
 Další informace najdete v tématu [postupy: přidat, upravit a odstranit entity](../../../../docs/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services.md).  
  
## <a name="attaching-entities"></a>Připojení entit  
 Klientská knihovna umožňuje uložit aktualizace, které jste provedli na entitu bez první provádění dotazu se načíst entity do <xref:System.Data.Services.Client.DataServiceContext>. Použití <xref:System.Data.Services.Client.DataServiceContext.AttachTo%2A> metoda k konkrétní sadu entit v připojit existující objekt <xref:System.Data.Services.Client.DataServiceContext>. Potom můžete upravit objekt a uložit změny do službu data. V následujícím příkladu je připojen objekt zákazníka, který byl změněn do kontextu a potom <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> nazývá označit objekt připojené jako <xref:System.Data.Services.Client.EntityStates.Modified> před <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> se označuje jako:  
  
 [!code-csharp[Astoria Northwind Client#AttachObjectSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#attachobjectspecific)]
 [!code-vb[Astoria Northwind Client#AttachObjectSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#attachobjectspecific)]  
  
 Při připojení objekty, platí následující aspekty:  
  
-   Objekt je připojena v <xref:System.Data.Services.Client.EntityStates.Unchanged> stavu.  
  
-   Pokud je objekt připojen, nejsou připojeny také objekty, které se vztahují k objektu připojené.  
  
-   Objekt nelze připojit, pokud entita je již sledován podle kontextu.  
  
-   <xref:System.Data.Services.Client.DataServiceContext.AttachTo%28System.String%2CSystem.Object%2CSystem.String%29> Přetížení metody, která přebírá `etag` parametr je použit pro připojení objektu entity, který jste získali spolu s hodnotou značka eTag. Tato hodnota značky eTag se pak používá zkontrolujte souběžnosti po uložení změn do připojené objektu.  
  
 Další informace najdete v tématu [postup: přiřadit stávající entitu DataServiceContext](../../../../docs/framework/data/wcf/attach-an-existing-entity-to-dc-wcf-data.md).  
  
## <a name="creating-and-modifying-relationship-links"></a>Vytvoření a úprava vztah odkazy  
 Když přidáte novou entitu pomocí <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> metoda nebo odpovídající *AddTo* metodu <xref:System.Data.Services.Client.DataServiceContext> třídy, která **přidat odkaz na službu** generuje dialogové okno, všechny vztahy, mezi nové entity a související entity nejsou definovány automaticky.  
  
 Můžete vytvořit a změnit vztahy mezi instancí entit a mají klientské knihovny ve službě data tyto změny projevily. Relace mezi entitami, které jsou definovány jako přidružení v modelu a <xref:System.Data.Services.Client.DataServiceContext> sleduje každý vztah jako odkaz objektu v kontextu. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]poskytuje následující metody na <xref:System.Data.Services.Client.DataServiceContext> třída vytvářet, upravovat a odstraňovat tyto odkazy:  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A>|Vytvoří nové propojení mezi dvěma objekty související entity. Voláním této metody je ekvivalentní volání <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> a <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> vytvořte nový objekt i definovat relaci s existujícím objektem.|  
|<xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>|Vytvoří nové propojení mezi dvěma objekty související entity.|  
|<xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>|Aktualizuje existující propojení mezi dvěma objekty související entity. <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>také se používá k odstranění odkazy s mohutnost nula nebo---1 (`0..1:1`) a 1: 1 (`1:1`). To provedete nastavením na objekt v relaci na `null`.|  
|<xref:System.Data.Services.Client.DataServiceContext.DeleteLink%2A>|Označí odkaz, který je sledování kontext k odstranění při <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda je volána. Tuto metodu použijte, když související objekt odstranit nebo změnit vztahu nejprve odstranit odkaz na existující objekt a potom přidání odkazu na nové související objekt.|  
|<xref:System.Data.Services.Client.DataServiceContext.AttachLink%2A>|Upozorní kontextu existující propojení mezi dvěma objekty entity. Kontext předpokládá, že tento vztah již existuje ve službě data a nebude pokoušet vytvořit odkaz při volání <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda. Tuto metodu použijte, když objekty přiřadit kontextu a muset také připojit propojení mezi dva. Pokud definujete nový vztah, měli byste místo toho použít <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>.|  
|<xref:System.Data.Services.Client.DataServiceContext.DetachLink%2A>|Zastaví sledování stanovený odkaz v kontextu. Tato metoda se používá k odstranění jeden mnoho (`*:*`) relace. Pro relaci odkazy mohutností jednoho, je nutné místo toho použít <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>.|  
  
 Následující příklad ukazuje, jak používat <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> metoda pro přidání nové `Order_Detail` který souvisí s existující `Orders` entity. Protože nové `Order_Details` objektu je nyní sledovanými <xref:System.Data.Services.Client.DataServiceContext>, relace přidaném `Order_Details` objekt, který má existující `Products` entita je definována volání <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> metoda:  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addorderdetailtoorderspecific)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addorderdetailtoorderspecific)]  
  
 Když <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> metoda definuje odkazy, které musí být vytvořeny ve službě data do mají tyto odkazy promítnuta objekty, které jsou v kontextu, musíte taky nastavit navigační vlastnosti na samotných objektech. V předchozím příkladu měli byste nastavit navigační vlastnosti následujícím způsobem:  
  
 [!code-csharp[Astoria Northwind Client#SetNavProps](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#setnavprops)]
 [!code-vb[Astoria Northwind Client#SetNavProps](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#setnavprops)]  
  
 Další informace najdete v tématu [postupy: definování entitami](../../../../docs/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services.md).  
  
## <a name="saving-changes"></a>Ukládají se změny  
 Změny jsou sledovány v <xref:System.Data.Services.Client.DataServiceContext> instance však nebyla odeslána na server okamžitě. Po skončení požadované změny pro zadanou aktivitu, volat <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> odeslat všechny změny ve službě data. Další informace najdete v tématu [Správa služby kontextu dat](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md). Můžete také uložit změny asynchronně pomocí <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A> a <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A> metody. Další informace najdete v tématu [asynchronních operací](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také  
 [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [Dotazování v datové službě](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 [Asynchronní operace](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)  
 [Operace dávkování](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)  
 [Materializace objektů](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)  
 [Správa kontextu datové služby](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)
