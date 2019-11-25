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
ms.openlocfilehash: 02bcb8f12cd7f230d60c3b3c58174a54405ff955
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975113"
---
# <a name="updating-the-data-service-wcf-data-services"></a>Aktualizace datové služby (WCF Data Services)
Když použijete klientskou knihovnu [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ke zpracování informačního kanálu OData (Open Data Protocol), knihovna přeloží položky v informačním kanálu do instancí klientských datových služeb. Tyto třídy datové služby jsou sledovány pomocí <xref:System.Data.Services.Client.DataServiceContext>, ke kterému patří <xref:System.Data.Services.Client.DataServiceQuery%601>. Klient sleduje změny entit, které vytváříte pomocí metod v <xref:System.Data.Services.Client.DataServiceContext>. Tyto metody umožňují klientovi sledovat přidané a odstraněné entity a také změny, které provedete v hodnotách vlastností nebo vztahy mezi instancemi entit. Tyto sledované změny jsou odesílány zpět do datové služby jako operace založené na REST při volání metody <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>.  
  
> [!NOTE]
> Použijete-li instanci <xref:System.Data.Services.Client.DataServiceCollection%601> pro svázání dat s ovládacími prvky, změny provedené v datech v rámci vázaného ovládacího prvku jsou automaticky hlášeny do <xref:System.Data.Services.Client.DataServiceContext>. Další informace najdete v tématu [vázání dat na ovládací prvky](binding-data-to-controls-wcf-data-services.md).  
  
## <a name="adding-modifying-and-changing-entities"></a>Přidání, úprava a změna entit  
 Při použití dialogového okna **Přidat odkaz na službu** v aplikaci Visual Studio k přidání odkazu na datový kanál OData mají výsledné třídy služby data klienta všechny statické metody *Create* , které pro každou vlastnost entity bez hodnoty null přebírají jeden parametr. Tuto metodu lze použít k vytvoření instancí tříd typu entity, jako v následujícím příkladu:  
  
 [!code-csharp[Astoria Northwind Client#CreateNewProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#createnewproduct)]
 [!code-vb[Astoria Northwind Client#CreateNewProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#createnewproduct)]  
  
 Chcete-li přidat instanci entity, zavolejte příslušnou metodu *AddTo* pro třídu <xref:System.Data.Services.Client.DataServiceContext> generovanou dialogem **Přidat odkaz na službu** , jak je uvedeno v následujícím příkladu:  
  
 [!code-csharp[Astoria Northwind Client#AddProductSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addproductspecific)]
 [!code-vb[Astoria Northwind Client#AddProductSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addproductspecific)]  
  
 Tím se objekt přidá do kontextu a do správné sady entit. Můžete také volat <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A>, ale místo toho je nutné zadat název sady entit. Pokud má přidaná entita jednu nebo více relací k jiným entitám, můžete použít metodu <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> nebo použít jednu z předchozích metod a také tyto odkazy explicitně definovat. Tyto operace jsou popsány dále v tomto tématu.  
  
 Chcete-li upravit existující instanci entity, nejprve dotaz pro tuto entitu, proveďte požadované změny vlastností a poté zavolejte metodu <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> v <xref:System.Data.Services.Client.DataServiceContext> k označení klientské knihovně, kterou potřebuje k odeslání aktualizace pro daný objekt, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomerSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#modifycustomerspecific)]
 [!code-vb[Astoria Northwind Client#ModifyCustomerSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#modifycustomerspecific)]  
  
 Chcete-li odstranit instanci entity, zavolejte metodu <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> v <xref:System.Data.Services.Client.DataServiceContext>, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[Astoria Northwind Client#DeleteProductSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#deleteproductspecific)]
 [!code-vb[Astoria Northwind Client#DeleteProductSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#deleteproductspecific)]  
  
 Další informace najdete v tématu [Postup: Přidání, úprava a odstranění entit](how-to-add-modify-and-delete-entities-wcf-data-services.md).  
  
## <a name="attaching-entities"></a>Připojování entit  
 Klientská knihovna umožňuje uložit aktualizace, které jste provedli v entitě, aniž byste nejdřív vyprováděli dotaz pro načtení entity do <xref:System.Data.Services.Client.DataServiceContext>. Pomocí metody <xref:System.Data.Services.Client.DataServiceContext.AttachTo%2A> připojte existující objekt ke konkrétní sadě entit v <xref:System.Data.Services.Client.DataServiceContext>. Pak můžete objekt upravit a uložit změny do datové služby. V následujícím příkladu je objekt zákazníka, který byl změněn, připojen k kontextu a poté <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> volána k označení připojeného objektu jako <xref:System.Data.Services.Client.EntityStates.Modified> před voláním <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>.  
  
 [!code-csharp[Astoria Northwind Client#AttachObjectSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#attachobjectspecific)]
 [!code-vb[Astoria Northwind Client#AttachObjectSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#attachobjectspecific)]  
  
 Při připojování objektů platí následující požadavky:  
  
- Objekt je připojen ve stavu <xref:System.Data.Services.Client.EntityStates.Unchanged>.  
  
- Když je objekt připojen, objekty, které se vztahují k připojenému objektu, nejsou také připojeny.  
  
- Objekt nelze připojit, pokud je entita již sledována kontextem.  
  
- Přetížení metody <xref:System.Data.Services.Client.DataServiceContext.AttachTo%28System.String%2CSystem.Object%2CSystem.String%29>, které přijímá parametr `etag`, se používá při připojení objektu entity, který byl přijat společně s hodnotou eTag. Tato hodnota eTag se pak používá ke kontrole souběžnosti při uložení změn připojeného objektu.  
  
 Další informace najdete v tématu [Postup: připojení existující entity k DataServiceContext](attach-an-existing-entity-to-dc-wcf-data.md).  
  
## <a name="creating-and-modifying-relationship-links"></a>Vytváření a úpravy propojení vztahů  
 Když přidáte novou entitu pomocí metody <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> nebo příslušné metody *AddTo* třídy <xref:System.Data.Services.Client.DataServiceContext>, kterou dialogové okno **Přidat odkaz na službu** vygeneruje, všechny relace mezi novou entitou a související entitou nejsou automaticky definované.  
  
 Můžete vytvořit a změnit vztahy mezi instancemi entit a klientské knihovny tyto změny odrážejí v datové službě. Vztahy mezi entitami jsou definovány jako asociace v modelu a <xref:System.Data.Services.Client.DataServiceContext> v kontextu sleduje každou relaci jako objekt propojení. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] poskytuje následující metody třídy <xref:System.Data.Services.Client.DataServiceContext> k vytvoření, úpravě a odstranění těchto odkazů:  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A>|Vytvoří nové propojení mezi dvěma souvisejícími objekty entity. Volání této metody je ekvivalentní volání <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> a <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> k vytvoření nového objektu a definování vztahu k existujícímu objektu.|  
|<xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>|Vytvoří nové propojení mezi dvěma souvisejícími objekty entity.|  
|<xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>|Aktualizuje existující propojení mezi dvěma souvisejícími objekty entit. <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> se také používá k odstranění propojení se mohutnou nulou nebo 1:1 (`0..1:1`) a 1:1 (`1:1`). To můžete provést nastavením souvisejícího objektu na `null`.|  
|<xref:System.Data.Services.Client.DataServiceContext.DeleteLink%2A>|Označí odkaz, který kontext sleduje pro odstranění při volání metody <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>. Tuto metodu použijte, když odstraníte související objekt nebo změníte relaci, a to tak, že nejprve odstraníte odkaz na existující objekt a pak přidáte odkaz na nový související objekt.|  
|<xref:System.Data.Services.Client.DataServiceContext.AttachLink%2A>|Upozorní kontext existujícího propojení mezi dvěma objekty entity. Kontext předpokládá, že tato relace již v datové službě existuje a nepokusí se vytvořit odkaz při volání metody <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>. Tuto metodu použijte, pokud připojíte objekty ke kontextu a potřebujete také propojení mezi nimi. Pokud definujete novou relaci, měli byste místo toho použít <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>.|  
|<xref:System.Data.Services.Client.DataServiceContext.DetachLink%2A>|Zastaví sledování zadaného odkazu v kontextu. Tato metoda slouží k odstranění vztahů 1: n (`*:*`). Pro propojení vztahů se mohutnou jednou je místo toho nutné použít <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>.|  
  
 Následující příklad ukazuje, jak použít metodu <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> k přidání nového `Order_Detail`, který souvisí s existující entitou `Orders`. Vzhledem k tomu, že nový objekt `Order_Details` je nyní sledován <xref:System.Data.Services.Client.DataServiceContext>, je vztah objektu přidané `Order_Details` k existující entitě `Products` definován voláním metody <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>:  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderspecific)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderspecific)]  
  
 I když metoda <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> definuje odkazy, které musí být vytvořeny v datové službě, aby se tyto odkazy projevily v objektech, které jsou v kontextu, je nutné také nastavit navigační vlastnosti u samotných objektů. V předchozím příkladu byste měli nastavit navigační vlastnosti následujícím způsobem:  
  
 [!code-csharp[Astoria Northwind Client#SetNavProps](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#setnavprops)]
 [!code-vb[Astoria Northwind Client#SetNavProps](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#setnavprops)]  
  
 Další informace najdete v tématu [Postupy: definování vztahů mezi entitami](how-to-define-entity-relationships-wcf-data-services.md).  
  
## <a name="saving-changes"></a>Uložení změn  
 Změny jsou sledovány v instanci <xref:System.Data.Services.Client.DataServiceContext>, ale nejsou odesílány přímo na server. Po dokončení požadovaných změn u zadané aktivity zavolejte <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> pro odeslání všech změn do datové služby. Další informace najdete v tématu [Správa kontextu datové služby](managing-the-data-service-context-wcf-data-services.md). Změny můžete také asynchronně ukládat pomocí <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A> a <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A>ch metod. Další informace najdete v tématu [asynchronní operace](asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
- [Dotazování v datové službě](querying-the-data-service-wcf-data-services.md)
- [Asynchronní operace](asynchronous-operations-wcf-data-services.md)
- [Operace dávkování](batching-operations-wcf-data-services.md)
- [Materializace objektů](object-materialization-wcf-data-services.md)
- [Správa kontextu datové služby](managing-the-data-service-context-wcf-data-services.md)
