---
title: Streamování zprostředkovatele (služby WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, binary data
- streaming data provider [WCF Data Services]
- WCF Data Services, streams
ms.assetid: f0978fe4-5f9f-42aa-a5c2-df395d7c9495
ms.openlocfilehash: d65ea58bc2e98ab2607ce105b496ac0a870362b0
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805470"
---
# <a name="streaming-provider-wcf-data-services"></a>Streamování zprostředkovatele (služby WCF Data Services)
Datové služby můžou zpřístupnit binární data rozsáhlého objektu. Tato binární data může představovat datové proudy videa a audia, bitové kopie, soubory dokumentů nebo jiných typů médií binární. Pokud entitu v datovém modelu obsahuje jeden nebo více binárních vlastností, vrátí službu data tato binární data kódovaná jako kódování base-64 uvnitř položky v odpovědi informačního kanálu. Protože načítání a serializaci velké binární data tímto způsobem může ovlivnit výkon, [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] definuje mechanismus pro načtení binární data nezávisle na entity, do které patří. Toho dosahuje tím, že oddělíte binární data z entity do jednoho nebo více datových proudů.  
  
-   Mediální zdroj - binární data, která patří do entity, jako je například video, zvuk, image nebo jiný typ média datový proud prostředku.  
  
-   Odkaz na médium položka - entita, která obsahuje odkaz na datový proud prostředku související média.  
  
 S [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], definujte datový proud binárního prostředku implementací streamování zprostředkovatele dat. Streamování implementace zprostředkovatele poskytuje službu data s datový proud prostředku média přidružené k určité entitě jako <xref:System.IO.Stream> objektu. Tato implementace umožňuje službu data přijmout a vrátit zdrojů médií prostřednictvím protokolu HTTP jako binární datové proudy zadaného typu MIME.  
  
 Konfigurace datové služby pro podporu streamování binárních dat vyžaduje následující kroky:  
  
1.  Jedna nebo více entit v datovém modelu atribut jako záznamu odkazu na média. Binární data odesílání nesmí obsahovat tyto entity. Všechny binární vlastnosti entity jsou vždy vrátí v položce jako kódování base-64 binární.  
  
2.  Implementujte rozhraní T:System.Data.Services.Providers.IDataServiceStreamProvider.  
  
3.  Definovat službu data, která implementuje <xref:System.IServiceProvider> rozhraní. Data služby používá <xref:System.IServiceProvider.GetService%2A> implementace pro přístup k streamování implementace dat zprostředkovatele. Tato metoda vrátí odpovídající streamování implementace zprostředkovatele.  
  
4.  Povolte datové proudy velké zprávy v konfiguraci webové aplikace.  
  
5.  Povolení přístupu k binární prostředkům na serveru nebo v datovém zdroji.  
  
 V příkladech v tomto tématu jsou na základě vzorku, vysílání datového proudu fotografií služby, která je podrobně popsané v příspěvku [datové služby streamování zprostředkovatele řady: implementace poskytovatele streamování (část 1)](http://go.microsoft.com/fwlink/?LinkID=198989). Zdrojový kód pro tuto službu ukázka je dostupná na [vysílání datového proudu fotografií služby vzorek dat stránky](http://go.microsoft.com/fwlink/?LinkID=198988) na galerie kódů MSDN.  
  
## <a name="defining-a-media-link-entry-in-the-data-model"></a>Definování Media Link Entry v datovém modelu  
 Zprostředkovatel zdroje dat určuje způsob, že entita je definován jako položku média odkaz v datovém modelu.  
  
 **Zprostředkovatel Entity Framework**  
 Chcete-li znamenat, že entita záznamu odkazu na média, přidejte `HasStream` atribut definici entity typu v konceptuálním modelu, jako v následujícím příkladu:  
  
 [!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria photo streaming service/xml/photodata.edmx#hasstream)]  
  
 Musíte taky přidat obor názvů `xmlns:m=http://schemas.microsoft.com/ado/2007/08/dataservices/metadata` v entitě nebo do kořenového adresáře souboru EDMX nebo .csdl, který definuje datový model.  
  
 Příklad dat službu, která používá [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] zprostředkovatele a zveřejňuje prostředku média, najdete v příspěvku [datové služby streamování zprostředkovatele řady: implementace poskytovatele streamování (část 1)](http://go.microsoft.com/fwlink/?LinkID=198989).  
  
 **Zprostředkovatel reflexe**  
 Chcete-li znamenat, že entita záznamu odkazu na média, přidejte <xref:System.Data.Services.Common.HasStreamAttribute> na třídu, která definuje typ entity ve zprostředkovateli reflexe.  
  
 **Poskytovatel služeb vlastních dat**  
 Pokud používáte vlastní poskytovatelé, implementovat <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> rozhraní k definování metadata pro vaši službu data. Další informace najdete v tématu [vlastní Data poskytovatelé](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md). Označuje, že datový proud binárního prostředku patří do <xref:System.Data.Services.Providers.ResourceType> nastavením <xref:System.Data.Services.Providers.ResourceType.IsMediaLinkEntry%2A> vlastnost, která má `true` na <xref:System.Data.Services.Providers.ResourceType> , která představuje typ entity, které je položka odkaz média.  
  
## <a name="implementing-the-idataservicestreamprovider-interface"></a>Implementace rozhraní IDataServiceStreamProvider  
 Pokud chcete vytvořit službu data, která podporuje binární datové proudy, je nutné implementovat <xref:System.Data.Services.Providers.IDataServiceStreamProvider> rozhraní. Tato implementace umožňuje službu data vrátit binární data jako datový proud do klienta a využívat binární data jako datový proud odeslaných z klienta. Služba data vytvoří instanci tohoto rozhraní vždy, když jej potřebuje přístup k binární data jako datový proud. <xref:System.Data.Services.Providers.IDataServiceStreamProvider> Rozhraní určuje následující členy:  
  
|Název členu|Popis|  
|-----------------|-----------------|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.DeleteStream%2A>|Tato metoda je volána službou data můžete odstranit odpovídající prostředek médium, když jeho záznam média odkaz se odstraní. Při implementaci <xref:System.Data.Services.Providers.IDataServiceStreamProvider>, tato metoda obsahuje kód, který odstraní mediální prostředek přidružený záznam odkaz zadaný média.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStream%2A>|Tato metoda je volána službou data vrátit k mediálnímu zdroji jako datový proud. Při implementaci <xref:System.Data.Services.Providers.IDataServiceStreamProvider>, tato metoda obsahuje kód, který poskytuje datový proud, který je používán službou data vrátit média prostředek, který je přidružený záznam odkaz zadaný média.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStreamUri%2A>|Tato metoda je volána službou data vrátit identifikátor URI, který slouží k vyžádání média prostředku pro položku odkaz média. Tato hodnota se používá k vytvoření `src` atribut v obsahu elementu odkaz položka médií a který slouží k vyžádání datového proudu. Když tato metoda vrátí hodnotu `null`, službu data automaticky určuje identifikátor URI. Tuto metodu použijte, když potřebujete poskytovat klientům přímý přístup k binárních dat bez použití zprostředkovatele datový proud.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetStreamContentType%2A>|Tato metoda je volána službou data pro návratová hodnota Content-Type média prostředku, který je přidružený záznam odkaz zadaný média.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetStreamETag%2A>|Tato metoda je volána službou data vrátit značku eTag datový proud, který je přidružen zadanou entitu. Tato metoda se používá při správě souběžnosti pro binární data. Když tato metoda vrátí hodnotu null, službu data nesleduje souběžnosti.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A>|Tato metoda je volána službou data získat datový proud, který se používá při přijímání datového proudu odeslaných z klienta. Při implementaci <xref:System.Data.Services.Providers.IDataServiceStreamProvider>, musí vracet zapisovatelné datový proud, do které data služby zápisy přijal data datového proudu.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.ResolveType%2A>|Vrátí název oboru názvů kvalifikovaný typ, který představuje typ, který běh služby dat musíte vytvořit položku odkaz média, který je přidružen datový proud pro mediální zdroj, který bude vložen.|  
  
## <a name="creating-the-streaming-data-service"></a>Vytváření datových proudů dat služby  
 K poskytování [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] runtime s přístupem k <xref:System.Data.Services.Providers.IDataServiceStreamProvider> implementace, služba dat, která vytvoříte musí také implementovat <xref:System.IServiceProvider> rozhraní. Následující příklad ukazuje, jak implementovat <xref:System.IServiceProvider.GetService%2A> metoda vrátí instanci `PhotoServiceStreamProvider` třídu, která implementuje <xref:System.Data.Services.Providers.IDataServiceStreamProvider>.  
  
 [!code-csharp[Astoria Photo Streaming Service#PhotoServiceStreamingProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria photo streaming service/cs/photodata.svc.cs#photoservicestreamingprovider)]
 [!code-vb[Astoria Photo Streaming Service#PhotoServiceStreamingProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria photo streaming service/vb/photodata.svc.vb#photoservicestreamingprovider)]  
  
 Obecné informace o tom, jak vytvořit datové služby najdete v tématu [konfigurace službu Data](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
## <a name="enabling-large-binary-streams-in-the-hosting-environment"></a>Povolení velké binární proudy v hostitelském prostředí  
 Při vytváření datové služby v [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webové aplikace služby Windows Communication Foundation (WCF) slouží k poskytování implementace protokolu HTTP. Ve výchozím nastavení omezuje WCF velikost zpráv protokolu HTTP na pouze 65 kB. Abyste mohli do datového proudu velké binární data do a z službu data, musíte také nakonfigurovat webovou aplikaci povolit velké binární soubory a používat pro přenos datových proudů. Chcete-li to provést, přidejte následující v `<configuration />` element souboru Web.config aplikace:  
  
  
  
> [!NOTE]
>  Je nutné použít <xref:System.ServiceModel.TransferMode.Streamed?displayProperty=nameWithType> režim přenosu k zajistěte, aby byly binární data ve zprávách požadavků a odpovědí prostřednictvím datového proudu a není ve WCF do vyrovnávací paměti.  
  
 Další informace najdete v tématu [streamování přenosu zpráv](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md) a [přenosové kvóty](../../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
 Ve výchozím nastavení Internetové informační služby (IIS) také omezuje velikost žádostí o 4 MB volného místa. Pro povolení služby data získat větší než 4 MB volného místa pro datové proudy při spuštění ve službě IIS, je třeba také nastavit `maxRequestLength` atribut [httpRuntime Element (schéma nastavení ASP.NET)](http://msdn.microsoft.com/library/e9b81350-8aaf-47cc-9843-5f7d0c59f369) v `<system.web />` konfigurační oddíl jako vidět v následujícím příkladu:  
  
  
  
## <a name="using-data-streams-in-a-client-application"></a>Pomocí datových proudů v aplikaci klienta  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klientské knihovny umožňuje jak načíst a aktualizovat tyto prostředky zveřejněné jako binární proudy na straně klienta. Další informace najdete v tématu [práce s binární Data](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md).  
  
## <a name="considerations-for-working-with-a-streaming-provider"></a>Důležité informace týkající se práce s streamování zprostředkovatele  
 Níže jsou co je třeba zvážit při implementaci zprostředkovatele streamování a když je přístup k prostředkům média z datové služby.  
  
-   SLOUČENÍ požadavky nejsou podporovány pro zdrojů médií. Požadavek PUT použijte ke změně mediální zdroj existující entity.  
  
-   Požadavek POST nelze použít k vytvoření nového média odkazů. Místo toho musíte vydat požadavek POST k vytvoření nového prostředku média a službu data vytvoří nové médium záznam odkaz s výchozími hodnotami. Tuto novou entitu lze aktualizovat pomocí následující požadavek SLOUČENÍ nebo PUT. Vezměte v úvahu ukládání do mezipaměti entity, kde můžete provádět aktualizace v zneškodňovatel, například nastavení hodnoty vlastnosti na hodnotu záhlaví zkráceného názvu stránky v požadavku POST.  
  
-   Po přijetí požadavek POST data služby volání <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> vytvoření prostředku média dříve, než se volání <xref:System.Data.Services.IUpdatable.SaveChanges%2A> k vytvoření média odkazů.  
  
-   Implementace <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> by neměla vrátit <xref:System.IO.MemoryStream> objektu. Pokud použijete tento typ datového proudu, dojde k potížím prostředků paměti velké datové proudy přijetí služby.  
  
-   Tady jsou co je třeba zvážit při ukládání zdrojů médií v databázi:  
  
    -   Binární vlastnosti, která je k mediálnímu zdroji by neměly být obsažené v datovém modelu. Všechny vlastnosti v modelu dat jsou vráceny v položce v odpovědi informačního kanálu.  
  
    -   Zlepšení výkonu pomocí velké binárního datového proudu, doporučujeme vytvořit třídu vlastního datového proudu k uložení binární data v databázi. Tato třída je vrácen rutinou vaší <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> implementaci a odešle binární data do databáze v datové dávky. Pro databázi systému SQL Server doporučujeme použít FILESTREAM datový proud dat do databáze, když binární data jsou větší než 1MB.  
  
    -   Ujistěte se, že vaše databáze je určen k ukládání binární velké datové proudy, které mají být přijatých služby data.  
  
    -   Když klient odešle požadavek POST vložit položku média odkaz s mediálního zdroje v jedné žádosti, <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> je volat za účelem získání datového proudu, než služba data vloží novou entitu do databáze. Streamování implementace zprostředkovatele musí být schopna zpracovávat toto chování služby data. Zvažte použití samostatných data tabulky pro uložení binární data nebo úložiště datový proud v souboru až po entita byla vložena do databáze.  
  
-   Při implementaci <xref:System.Data.Services.Providers.IDataServiceStreamProvider.DeleteStream%2A>, <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStream%2A>, nebo <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> metody, musíte použít eTag a Content-Type hodnoty, které jsou zadané jako parametry metody. Nenastavujte značka eTag nebo hlavičky Content-Type v vaší <xref:System.Data.Services.Providers.IDataServiceStreamProvider> implementace zprostředkovatele.  
  
-   Ve výchozím nastavení klient odešle velké binární proudy pomocí bloku HTTP Transfer-Encoding. Protože [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] vývojový Server nepodporuje tento typ kódování, tohoto webového serveru nelze použít k hostování streamování služba dat, která musí přijmout velký binární datové proudy. Další informace o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] vývojový Server, najdete v části [webové servery v sadě Visual Studio pro webové projekty ASP.NET](http://msdn.microsoft.com/library/31d4f588-df59-4b7e-b9ea-e1f2dd204328).  
  
<a name="versioning"></a>   
## <a name="versioning-requirements"></a>Požadavky na Správa verzí  
 Poskytovatel nástroje streamování má následující [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokolu požadavků na správu verzí:  
  
-   Streamování zprostředkovatele vyžaduje, aby podporoval službu data verzi 2.0 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokol a novější verze.  
  
 Další informace najdete v tématu [verze datové služby](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také  
 [Zprostředkovatelé datových služeb](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [Vlastní zprostředkovatelé datových služeb](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)  
 [Práce s binárními daty](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md)
