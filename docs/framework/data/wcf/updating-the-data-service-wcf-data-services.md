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
ms.openlocfilehash: 5cf7a6e563069e35a4ac0fe729a616dc1c56bdb5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779740"
---
# <a name="updating-the-data-service-wcf-data-services"></a>Aktualizace datové služby (WCF Data Services)
Použijete [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] -li knihovnu klienta ke [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] využívání informačního kanálu, knihovna přeloží položky v informačním kanálu do instancí tříd služby data Client. Tyto třídy datové služby jsou sledovány pomocí služby <xref:System.Data.Services.Client.DataServiceContext> , ke <xref:System.Data.Services.Client.DataServiceQuery%601> které patří. Klient sleduje změny entit, které hlásíte pomocí metod v <xref:System.Data.Services.Client.DataServiceContext>. Tyto metody umožňují klientovi sledovat přidané a odstraněné entity a také změny, které provedete v hodnotách vlastností nebo vztahy mezi instancemi entit. Tyto sledované změny jsou odesílány zpět do datové služby jako operace založené na REST při volání <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metody.  
  
> [!NOTE]
> Použijete-li instanci <xref:System.Data.Services.Client.DataServiceCollection%601> pro svázání dat s ovládacími prvky, změny provedené v datech v rámci vázaného ovládacího prvku jsou automaticky hlášeny <xref:System.Data.Services.Client.DataServiceContext>do. Další informace najdete v tématu [vázání dat na ovládací prvky](binding-data-to-controls-wcf-data-services.md).  
  
## <a name="adding-modifying-and-changing-entities"></a>Přidání, úprava a změna entit  
 Při použití dialogového okna **Přidat odkaz na službu** v aplikaci Visual Studio k přidání odkazu na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informační kanál mají výsledné třídy klientské datové služby všechny statické metody *Create* , které pro každou vlastnost entity bez hodnoty null přebírají jeden parametr. . Tuto metodu lze použít k vytvoření instancí tříd typu entity, jako v následujícím příkladu:  
  
 [!code-csharp[Astoria Northwind Client#CreateNewProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#createnewproduct)]
 [!code-vb[Astoria Northwind Client#CreateNewProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#createnewproduct)]  
  
 Chcete-li přidat instanci entity, zavolejte příslušnou metodu *AddTo* pro <xref:System.Data.Services.Client.DataServiceContext> třídu vygenerovanou dialogem **Přidat odkaz na službu** , jak je uvedeno v následujícím příkladu:  
  
 [!code-csharp[Astoria Northwind Client#AddProductSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addproductspecific)]
 [!code-vb[Astoria Northwind Client#AddProductSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addproductspecific)]  
  
 Tím se objekt přidá do kontextu a do správné sady entit. Můžete také volat <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A>, ale místo toho je nutné zadat název sady entit. Pokud má přidaná entita jednu nebo více relací k jiným entitám, můžete buď použít <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> metodu, nebo použít jednu z předchozích metod a také tyto odkazy explicitně definovat. Tyto operace jsou popsány dále v tomto tématu.  
  
 Chcete-li upravit existující instanci entity, nejprve dotaz pro tuto entitu, proveďte požadované změny vlastností a poté zavolejte <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> na, aby označovala klientskou knihovnu, kterou potřebuje k odeslání aktualizace pro daný objekt, jak je znázorněno v Následující příklad:  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomerSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#modifycustomerspecific)]
 [!code-vb[Astoria Northwind Client#ModifyCustomerSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#modifycustomerspecific)]  
  
 Chcete-li odstranit instanci entity, zavolejte <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> metodu <xref:System.Data.Services.Client.DataServiceContext>na, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[Astoria Northwind Client#DeleteProductSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#deleteproductspecific)]
 [!code-vb[Astoria Northwind Client#DeleteProductSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#deleteproductspecific)]  
  
 Další informace najdete v tématu [jak: Přidávání, upravování a odstraňování entit](how-to-add-modify-and-delete-entities-wcf-data-services.md).  
  
## <a name="attaching-entities"></a>Připojování entit  
 Klientská knihovna umožňuje uložit aktualizace, které jste provedli v entitě, aniž byste nejprve vyprováděli dotaz pro načtení <xref:System.Data.Services.Client.DataServiceContext>entity do. Použijte metodu pro připojení existujícího objektu ke konkrétní sadě entit <xref:System.Data.Services.Client.DataServiceContext>v. <xref:System.Data.Services.Client.DataServiceContext.AttachTo%2A> Pak můžete objekt upravit a uložit změny do datové služby. V následujícím příkladu je objekt zákazníka, který byl změněn, připojen k kontextu a poté <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> je volána k označení připojeného objektu jako <xref:System.Data.Services.Client.EntityStates.Modified> před <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> voláním metody:  
  
 [!code-csharp[Astoria Northwind Client#AttachObjectSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#attachobjectspecific)]
 [!code-vb[Astoria Northwind Client#AttachObjectSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#attachobjectspecific)]  
  
 Při připojování objektů platí následující požadavky:  
  
- Objekt je připojen ve <xref:System.Data.Services.Client.EntityStates.Unchanged> stavu.  
  
- Když je objekt připojen, objekty, které se vztahují k připojenému objektu, nejsou také připojeny.  
  
- Objekt nelze připojit, pokud je entita již sledována kontextem.  
  
- Přetížení metody, které přijímá parametr, se používá při připojení objektu entity, který byl přijat společně s hodnotou eTag. `etag` <xref:System.Data.Services.Client.DataServiceContext.AttachTo%28System.String%2CSystem.Object%2CSystem.String%29> Tato hodnota eTag se pak používá ke kontrole souběžnosti při uložení změn připojeného objektu.  
  
 Další informace najdete v tématu [jak: Připojte existující entitu k DataServiceContext](attach-an-existing-entity-to-dc-wcf-data.md).  
  
## <a name="creating-and-modifying-relationship-links"></a>Vytváření a úpravy propojení vztahů  
 Když přidáte novou entitu pomocí <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> metody nebo příslušné metody <xref:System.Data.Services.Client.DataServiceContext> AddTo třídy, kterou vygeneruje dialogové okno **Přidat odkaz na službu** , všechny relace mezi novou entitou a související entitou jsou není definováno automaticky.  
  
 Můžete vytvořit a změnit vztahy mezi instancemi entit a klientské knihovny tyto změny odrážejí v datové službě. Vztahy mezi entitami jsou definovány jako asociace v modelu a <xref:System.Data.Services.Client.DataServiceContext> sledují každý vztah jako objekt propojení v kontextu. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]poskytuje následující metody <xref:System.Data.Services.Client.DataServiceContext> pro třídu pro vytvoření, úpravu a odstranění těchto odkazů:  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A>|Vytvoří nové propojení mezi dvěma souvisejícími objekty entity. Volání této metody je ekvivalentní volání <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> a <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> vytvoření nového objektu a definování vztahu k existujícímu objektu.|  
|<xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>|Vytvoří nové propojení mezi dvěma souvisejícími objekty entity.|  
|<xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>|Aktualizuje existující propojení mezi dvěma souvisejícími objekty entit. <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>slouží také k odstranění propojení se mohutnou nulou (`0..1:1`) a 1:1 () a jedním z nich (`1:1`). To lze provést nastavením souvisejícího objektu na `null`.|  
|<xref:System.Data.Services.Client.DataServiceContext.DeleteLink%2A>|Označí odkaz, který kontext sleduje pro odstranění při <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> volání metody. Tuto metodu použijte, když odstraníte související objekt nebo změníte relaci, a to tak, že nejprve odstraníte odkaz na existující objekt a pak přidáte odkaz na nový související objekt.|  
|<xref:System.Data.Services.Client.DataServiceContext.AttachLink%2A>|Upozorní kontext existujícího propojení mezi dvěma objekty entity. Kontext předpokládá, že tato relace již v datové službě existuje a nepokusí se vytvořit odkaz při volání <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metody. Tuto metodu použijte, pokud připojíte objekty ke kontextu a potřebujete také propojení mezi nimi. Pokud definujete novou relaci, měli byste místo toho použít <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>.|  
|<xref:System.Data.Services.Client.DataServiceContext.DetachLink%2A>|Zastaví sledování zadaného odkazu v kontextu. Tato metoda slouží k odstranění vztahů 1: n`*:*`. Pro propojení vztahů se mohutnou jednou je třeba použít <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>.|  
  
 Následující příklad ukazuje, jak použít <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> metodu pro přidání nového `Order_Detail` , který souvisí s existující `Orders` entitou. Vzhledem k tomu `Order_Details` <xref:System.Data.Services.Client.DataServiceContext>, že nový objekt je nyní sledován pomocí, je relace přidaného `Order_Details` objektu existující `Products` entitě definována voláním <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> metody:  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderspecific)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderspecific)]  
  
 I když <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> Metoda definuje propojení, která musí být vytvořena v datové službě, aby se tyto odkazy projevily v objektech, které jsou v kontextu, je nutné také nastavit navigační vlastnosti u samotných objektů. V předchozím příkladu byste měli nastavit navigační vlastnosti následujícím způsobem:  
  
 [!code-csharp[Astoria Northwind Client#SetNavProps](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#setnavprops)]
 [!code-vb[Astoria Northwind Client#SetNavProps](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#setnavprops)]  
  
 Další informace najdete v tématu [jak: Definujte vztahy mezi](how-to-define-entity-relationships-wcf-data-services.md)entitami.  
  
## <a name="saving-changes"></a>Uložení změn  
 Změny jsou sledovány v <xref:System.Data.Services.Client.DataServiceContext> instanci, ale nejsou odesílány přímo na server. Po dokončení požadovaných změn u zadané aktivity zavolejte <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> na Odeslat všechny změny do datové služby. Další informace najdete v tématu [Správa kontextu datové služby](managing-the-data-service-context-wcf-data-services.md). Změny lze také asynchronně ukládat pomocí <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A> metod a. <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A> Další informace najdete v tématu [asynchronní operace](asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
- [Dotazování v datové službě](querying-the-data-service-wcf-data-services.md)
- [Asynchronní operace](asynchronous-operations-wcf-data-services.md)
- [Operace dávkování](batching-operations-wcf-data-services.md)
- [Materializace objektů](object-materialization-wcf-data-services.md)
- [Správa kontextu datové služby](managing-the-data-service-context-wcf-data-services.md)
