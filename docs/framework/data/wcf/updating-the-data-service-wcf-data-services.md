---
title: Aktualizace datové služby (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
- WCF Data Services, client library
ms.assetid: 00d993be-ffed-4dea-baf7-6eea982cdb54
ms.openlocfilehash: 5b8fa13bf5db7f3c3df97febe4bb6f9ee4c184a4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231289"
---
# <a name="updating-the-data-service-wcf-data-services"></a>Aktualizace datové služby (WCF Data Services)
Při použití [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientskou knihovnu pro využívání [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] informačního kanálu, knihovně přeloží položek v informačním kanálu do instancí tříd klientské datové služby. Tyto datové služby třídy jsou sledovány pomocí <xref:System.Data.Services.Client.DataServiceContext> ke kterému <xref:System.Data.Services.Client.DataServiceQuery%601> patří. Klient sleduje změny entity, které sestavy pomocí metod na <xref:System.Data.Services.Client.DataServiceContext>. Tyto metody umožnění spolupráce klienta služby pro sledování přidané a odstraněné entit a také změny, které provedete na hodnoty vlastnosti nebo vztahy mezi instancí entit. Tyto sledované změny odesílají zpět do datové služby jako operace založené na protokolu REST při volání <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metody.  
  
> [!NOTE]
>  Při použití instance <xref:System.Data.Services.Client.DataServiceCollection%601> vazba dat k ovládacím prvkům, změny dat v ovládacím prvku vazby automaticky hlášení do <xref:System.Data.Services.Client.DataServiceContext>. Další informace najdete v tématu [vazba dat k ovládacím prvkům](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).  
  
## <a name="adding-modifying-and-changing-entities"></a>Přidáním, úpravou a změnou entity  
 Při použití **přidat odkaz na službu** dialogového okna v sadě Visual Studio se přidat odkaz na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informační kanál, výsledný tříd klientské datové služby každý mají statickou *vytvořit* metodu, která má jednu parametr pro každou vlastnost neumožňující entity. Tuto metodu můžete použít k vytvoření instance entity typu třídy, jako v následujícím příkladu:  
  
 [!code-csharp[Astoria Northwind Client#CreateNewProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#createnewproduct)]
 [!code-vb[Astoria Northwind Client#CreateNewProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#createnewproduct)]  
  
 Chcete-li přidat instanci entity, zavolejte odpovídající *AddTo* metodu na <xref:System.Data.Services.Client.DataServiceContext> třídy generované **přidat odkaz na službu** dialogové okno, jako v následujícím příkladu:  
  
 [!code-csharp[Astoria Northwind Client#AddProductSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addproductspecific)]
 [!code-vb[Astoria Northwind Client#AddProductSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addproductspecific)]  
  
 Tento postup přidá objekt do kontextu a do sady entit správné. Můžete také volat <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A>, ale místo toho je nutné zadat název sady entit. Pokud Přidání entity obsahuje jeden nebo více relace s jinými entitami, můžete použít <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> metoda nebo použijte jednu z výše uvedených metod a také explicitně definovat tyto odkazy. Tyto operace jsou popsány dále v tomto tématu.  
  
 Pokud chcete upravit existující instanci entity, první dotaz pro danou entitu, proveďte požadované změny do jeho vlastnosti a poté zavolejte <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> metodu na <xref:System.Data.Services.Client.DataServiceContext> a informuje klientské knihovny potřebné k odeslání aktualizace pro tento objekt, jak je znázorněno v v následujícím příkladu:  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomerSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#modifycustomerspecific)]
 [!code-vb[Astoria Northwind Client#ModifyCustomerSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#modifycustomerspecific)]  
  
 Chcete-li odstranit instanci entity, zavolejte <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> metodu <xref:System.Data.Services.Client.DataServiceContext>, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[Astoria Northwind Client#DeleteProductSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#deleteproductspecific)]
 [!code-vb[Astoria Northwind Client#DeleteProductSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#deleteproductspecific)]  
  
 Další informace najdete v tématu [jak: Přidání, úpravy a odstranění entit](../../../../docs/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services.md).  
  
## <a name="attaching-entities"></a>Připojení entit  
 Klientská knihovna umožňuje ukládat aktualizace, které jste provedli s entitou bez první spuštění dotazu načtěte entitu do <xref:System.Data.Services.Client.DataServiceContext>. Použití <xref:System.Data.Services.Client.DataServiceContext.AttachTo%2A> metoda připojit existující objekt na konkrétní entitu, nastavte <xref:System.Data.Services.Client.DataServiceContext>. Můžete upravit objekt a uložte změny do datové služby. V následujícím příkladu je připojen objekt zákazníka, který byl změněn na kontext a poté <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> je volána k označení připojeného objektu jako <xref:System.Data.Services.Client.EntityStates.Modified> před <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> se volá:  
  
 [!code-csharp[Astoria Northwind Client#AttachObjectSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#attachobjectspecific)]
 [!code-vb[Astoria Northwind Client#AttachObjectSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#attachobjectspecific)]  
  
 Při připojování objekty, platí následující aspekty:  
  
-   Objekt je připojena v <xref:System.Data.Services.Client.EntityStates.Unchanged> stavu.  
  
-   Když je připojen objektu, není připojen také objekty, které se vztahují k připojeného objektu.  
  
-   Objekt nelze připojit, pokud entita již sledován správou kontextu.  
  
-   <xref:System.Data.Services.Client.DataServiceContext.AttachTo%28System.String%2CSystem.Object%2CSystem.String%29> Přetížení metody, která přebírá `etag` parametr se používá při připojení, který uživateli přišel spolu s hodnotou eTag objektu entity. Tato hodnota eTag, pak se k Kontrola souběžnosti při uložení změn do připojeného objektu.  
  
 Další informace najdete v tématu [jak: Přiřazení existující Entity k prvku DataServiceContext](../../../../docs/framework/data/wcf/attach-an-existing-entity-to-dc-wcf-data.md).  
  
## <a name="creating-and-modifying-relationship-links"></a>Vytvoření a úprava vztahů propojení  
 Po přidání nové entity pomocí <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> metody nebo odpovídající *AddTo* metodu <xref:System.Data.Services.Client.DataServiceContext> třídy, která **přidat odkaz na službu** generuje dialogového okna, případné relace mezi nové entity a související entity nejsou definovány automaticky.  
  
 Můžete vytvořit a změnit vztahy mezi instancí entit a mít klientská knihovna odrážet provedené změny ve službě data. Vztahy mezi entitami, které jsou definovány jako přidružení v modelu a <xref:System.Data.Services.Client.DataServiceContext> sleduje každý vztah jako odkaz objektu v kontextu. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] poskytuje následující metody na <xref:System.Data.Services.Client.DataServiceContext> třídy vytvářet, upravovat a odstraňovat tyto odkazy:  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A>|Vytvoří nové propojení mezi dvěma objekty související entity. Voláním této metody je ekvivalentní volání <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> a <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> jak vytvořit nový objekt a definovat vztah na existující objekt.|  
|<xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>|Vytvoří nové propojení mezi dvěma objekty související entity.|  
|<xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>|Aktualizuje existující propojení mezi dvěma objekty související entity. <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> slouží také k odstranění odkazů s kardinalitou nula nebo 1--: 1 (`0..1:1`) a 1: 1 (`1:1`). Můžete to provést nastavením související objekt na `null`.|  
|<xref:System.Data.Services.Client.DataServiceContext.DeleteLink%2A>|Označí odkaz, který sleduje kontext k odstranění při <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda je volána. Tuto metodu použijte, pokud objekt v relaci odstraníte nebo změníte relace nejprve odstranit odkaz na existující objekt a následným přidáním odkazu na nový související objekt.|  
|<xref:System.Data.Services.Client.DataServiceContext.AttachLink%2A>|Upozorní kontextu stávajícího propojení mezi dva objekty entity. Kontext předpokládá, že tato relace již existuje ve službě data a nepokusí se vytvářet propojení při volání <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metody. Tuto metodu použijte, pokud připojení objektů do kontextu a muset připojit také propojení mezi nimi. Pokud definujete novou relaci, měli byste místo toho použít <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>.|  
|<xref:System.Data.Services.Client.DataServiceContext.DetachLink%2A>|Zastaví sledování zadaný odkaz v kontextu. Tato metoda se používá k odstranění jednoho k několika (`*:*`) vztahy. Pro relace propojení s kardinalitou jednoho, je nutné místo toho použít <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>.|  
  
 Následující příklad ukazuje způsob použití <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> způsob, jak přidat nové `Order_Detail` , která má vztah k existujícímu `Orders` entity. Protože nová `Order_Details` objekt je nyní sledován pomocí funkce <xref:System.Data.Services.Client.DataServiceContext>, vztah tvoření přidaného `Order_Details` objekt ke stávající `Products` voláním je definován entity <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> – metoda:  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addorderdetailtoorderspecific)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addorderdetailtoorderspecific)]  
  
 Zatímco <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> metoda definuje odkazů, které musí vytvořit ve službě data, aby tyto odkazy se projeví v objektech, které jsou v kontextu, musíte taky nastavit vlastnosti navigace na samotných objektech. V předchozím příkladu měli byste nastavit navigační vlastnosti následujícím způsobem:  
  
 [!code-csharp[Astoria Northwind Client#SetNavProps](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#setnavprops)]
 [!code-vb[Astoria Northwind Client#SetNavProps](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#setnavprops)]  
  
 Další informace najdete v tématu [jak: Definování vztahů mezi entitami](../../../../docs/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services.md).  
  
## <a name="saving-changes"></a>Ukládají se změny  
 Změny jsou sledovány v <xref:System.Data.Services.Client.DataServiceContext> instance však nebyla odeslána na server okamžitě. Po dokončení se požadované změny pro zadané aktivita volat <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> odeslat všechny provedené změny do datové služby. Další informace najdete v tématu [Správa kontextu datové služby](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md). Můžete také uložit změny asynchronně pomocí <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A> a <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A> metody. Další informace najdete v tématu [asynchronních operací](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Dotazování v datové službě](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
- [Asynchronní operace](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)
- [Operace dávkování](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)
- [Materializace objektů](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)
- [Správa kontextu datové služby](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)
