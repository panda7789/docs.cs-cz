---
title: Zprostředkovatel streamování (WCF Data Services)
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
ms.openlocfilehash: 543d095c88670024a53fad7c865883ecaab1c6e0
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45527574"
---
# <a name="streaming-provider-wcf-data-services"></a>Zprostředkovatel streamování (WCF Data Services)
Datové služby může vystavit data binárního rozsáhlého objektu. Tento binární data mohou představovat video a audiostreamů, obrázky, soubory dokumentů nebo jiných typů médií binární. Pokud entita v datovém modelu obsahuje jeden nebo více binárních vlastností, datové služby vrátí tato binární data kódováním base-64 uvnitř položky v odpovědi informačního kanálu. Protože načítání a serializaci velkému objemu binárních dat tímto způsobem může ovlivnit výkon, [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] definuje mechanismus pro načítání binárních dat, které jsou nezávislé na entitu, do které patří. Toho dosahuje oddělením binární data z entity do jednoho nebo více datových proudů.  
  
-   Mediální zdroj - binární data, která patří do entity, jako jsou videa, zvuk, image nebo jiný typ média datový proud prostředků.  
  
-   Odkaz na médium položky - entita, která obsahuje odkaz na datový proud prostředků souvisejících média.  
  
 S [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], definovat datový proud binárních prostředků díky implementaci zprostředkovatele streamovaná data. Streamování implementace poskytovatele poskytuje datové služby s datový proud prostředků média přidružený k konkrétní entity jako <xref:System.IO.Stream> objektu. Tato implementace umožňuje datové službě dovoluje přijímají a vrací zdroje médií prostřednictvím protokolu HTTP jako binární datové proudy zadaného typu MIME.  
  
 Konfigurace datové služby podporovat datový proud binárních dat vyžaduje následující kroky:  
  
1.  Atribut jeden nebo více entit v datovém modelu, jak položkou odkazu na média. Tyto entity by neměl obsahovat binární data, která mají Streamovat. Žádné binární vlastnosti entity jsou vždy vrátí v položce jako kódování base-64 binární.  
  
2.  Implementujte rozhraní T:System.Data.Services.Providers.IDataServiceStreamProvider.  
  
3.  Definování datové služby, který implementuje <xref:System.IServiceProvider> rozhraní. Služba používá data <xref:System.IServiceProvider.GetService%2A> implementace pro přístup k streamování implementace poskytovatele dat. Tato metoda vrátí odpovídající streamování implementace poskytovatele.  
  
4.  Povolte datové proudy velké zprávy v konfiguraci webové aplikace.  
  
5.  Povolení přístupu k binární prostředky na serveru nebo ve zdroji dat.  
  
 Příklady v tomto tématu jsou založené na vzorku služba pro streamování fotek, která je podrobně popsané v příspěvku [datové služby streamování poskytovatele řady: implementace poskytovatele datových proudů (část 1)](https://go.microsoft.com/fwlink/?LinkID=198989). Zdrojový kód pro tuto službu ukázka je k dispozici na [streamování fotek ukázková Data pro službu stránky](https://go.microsoft.com/fwlink/?LinkID=198988) Galerie kódu MSDN.  
  
## <a name="defining-a-media-link-entry-in-the-data-model"></a>Definování položku Media Link Entry v datovém modelu  
 Zprostředkovatel zdroje dat určuje způsob, jakým, že entita je definován jako položku media link entry v datovém modelu.  
  
 **Zprostředkovatel Entity Framework**  
 Označuje, že entita položkou odkazu na média, přidejte `HasStream` atributu na definici typu entity v konceptuálním modelu, jako v následujícím příkladu:  
  
 [!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria photo streaming service/xml/photodata.edmx#hasstream)]  
  
 Musíte taky přidat obor názvů `xmlns:m=http://schemas.microsoft.com/ado/2007/08/dataservices/metadata` k entitě nebo do kořenového adresáře souboru .edmx nebo .csdl, který definuje datový model.  
  
 Příklad z datové služby, který používá [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] zprostředkovatele a zveřejňuje mediální zdroj, najdete v příspěvku [datové služby streamování poskytovatele řady: implementace poskytovatele datových proudů (část 1)](https://go.microsoft.com/fwlink/?LinkID=198989).  
  
 **Zprostředkovatel reflexe**  
 Označuje, že entita položkou odkazu na média, přidejte <xref:System.Data.Services.Common.HasStreamAttribute> do třídy, která definuje typ entity v zprostředkovatel reflexe.  
  
 **Poskytovatel služeb vlastních dat**  
 Při použití vlastních zprostředkovatelů, můžete implementovat <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> rozhraní definují metadata pro datové služby. Další informace najdete v tématu [Vlastní zprostředkovatelé datových služeb](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md). Označuje, že datový proud binární prostředek patří do <xref:System.Data.Services.Providers.ResourceType> nastavením <xref:System.Data.Services.Providers.ResourceType.IsMediaLinkEntry%2A> vlastnost `true` na <xref:System.Data.Services.Providers.ResourceType> , který představuje typ entity, která je položka media link entry.  
  
## <a name="implementing-the-idataservicestreamprovider-interface"></a>Implementace rozhraní IDataServiceStreamProvider  
 K vytvoření datové služby, který podporuje binární datové proudy, je nutné implementovat <xref:System.Data.Services.Providers.IDataServiceStreamProvider> rozhraní. Tato implementace umožňuje službě data a vrátit binární data jako datový proud do klienta a zpracování binárních dat jako datový proud odeslaných z klienta. Datové služby vytvoří instanci tohoto rozhraní pokaždé, když jej potřebuje přístup k binárních dat jako datový proud. <xref:System.Data.Services.Providers.IDataServiceStreamProvider> Rozhraní určuje následující členy:  
  
|Název členu|Popis|  
|-----------------|-----------------|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.DeleteStream%2A>|Tato metoda vyvolá datové službě dovoluje při odstranění jeho položka media link entry odstranění odpovídající mediální zdroj. Při implementaci <xref:System.Data.Services.Providers.IDataServiceStreamProvider>, tato metoda obsahuje kód, který odstraní přidružené položka zadaná media link entry mediální zdroj.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStream%2A>|Tato metoda vyvolá datové služby se vraťte mediální zdroj jako datový proud. Při implementaci <xref:System.Data.Services.Providers.IDataServiceStreamProvider>, tato metoda obsahuje kód, který poskytuje datový proud, který je používán službou data do prostředku vrátit média, který je spojen s položka zadaná media link entry.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStreamUri%2A>|Tato metoda vyvolána datová služba vrátit identifikátor URI, který slouží k vyžádání mediální zdroj pro položka media link entry. Tato hodnota se používá k vytvoření `src` atribut v obsahu elementu položka media link entry a, který slouží k vyžádání datového proudu. Při návratu tato metoda `null`, datové služby automaticky určuje identifikátor URI. Tuto metodu použijte, pokud je potřeba zadat klientů s přímým přístupem k binárních dat bez použití zprostředkovatele datový proud.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetStreamContentType%2A>|Tato metoda vyvolá datové službě dovoluje návratová hodnota Content-Type mediální zdroj, který je přidružen položka zadaná media link entry.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetStreamETag%2A>|Datová služba k vrácení eTag datový proud, který je spojen s zadaná entita byla tato metoda vyvolána. Tato metoda se používá při správě souběžnosti pro binární data. Když tato metoda vrátí hodnotu null, nesleduje datové služby souběžnosti.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A>|Datová služba k získání datového proudu, který se používá při přijímání datový proud odeslaných z klienta byla tato metoda vyvolána. Při implementaci <xref:System.Data.Services.Providers.IDataServiceStreamProvider>, musí vracet zapisovatelný datový proud, do které datové služby zápisy přijatá data datového proudu.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.ResolveType%2A>|Vrátí název typu kvalifikovaného oboru názvů, který představuje typ, který modul runtime služby data musíte vytvořit pro položka media link entry, který je spojen s datovým proudem pro mediální zdroj, který bude vložen.|  
  
## <a name="creating-the-streaming-data-service"></a>Vytvoření datových proudů datové služby  
 K poskytování [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] modulu runtime s přístupem k <xref:System.Data.Services.Providers.IDataServiceStreamProvider> implementace, datové služby, kterou vytvoříte musí implementovat taky <xref:System.IServiceProvider> rozhraní. Následující příklad ukazuje, jak implementovat <xref:System.IServiceProvider.GetService%2A> metoda vrátí instanci `PhotoServiceStreamProvider` třídu, která implementuje <xref:System.Data.Services.Providers.IDataServiceStreamProvider>.  
  
 [!code-csharp[Astoria Photo Streaming Service#PhotoServiceStreamingProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria photo streaming service/cs/photodata.svc.cs#photoservicestreamingprovider)]
 [!code-vb[Astoria Photo Streaming Service#PhotoServiceStreamingProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria photo streaming service/vb/photodata.svc.vb#photoservicestreamingprovider)]  
  
 Obecné informace o tom, jak vytvořit datovou službu, naleznete v tématu [konfigurace datové služby](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
## <a name="enabling-large-binary-streams-in-the-hosting-environment"></a>Povolení velké binární datové proudy v hostitelském prostředí  
 Při vytváření datové služby v [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webové aplikace, Windows Communication Foundation (WCF) slouží k poskytování implementace protokolu HTTP. Ve výchozím nastavení WCF omezení velikosti zpráv HTTP na pouze 65 kB. Aby bylo možné do datového proudu velkému objemu binárních dat do a z datové služby, musíte také nakonfigurovat webovou aplikaci povolit velkých binárních souborů a použití datových proudů pro přenos. Chcete-li to provést, přidejte následující kód do `<configuration />` prvek souboru Web.config aplikace:  
  
  
  
> [!NOTE]
>  Je nutné použít <xref:System.ServiceModel.TransferMode.Streamed?displayProperty=nameWithType> přenosový režim na binární data ve zprávách žádost a odpověď streamování a nejsou ukládány do vyrovnávací paměti ve WCF.  
  
 Další informace najdete v tématu [streamování přenosu zpráv](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md) a [přenosové kvóty](../../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
 Ve výchozím nastavení Internetové informační služby (IIS) také omezuje množství požadavků na 4MB. Pokud chcete povolit datové služby přijímat datové proudy, které jsou větší než 4MB, když ve službě IIS, musíte taky nastavit `maxRequestLength` atribut [httpRuntime – Element (schéma nastavení technologie ASP.NET)](https://msdn.microsoft.com/library/e9b81350-8aaf-47cc-9843-5f7d0c59f369) v `<system.web />` konfiguračního oddílu jako můžete vidět v následujícím příkladu:  
  
  
  
## <a name="using-data-streams-in-a-client-application"></a>Použití datových proudů v klientské aplikaci  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klientská knihovna umožňuje načíst i aktualizovat tyto materiály vystavené jako binární datové proudy na straně klienta. Další informace najdete v tématu [práce s binárními daty](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md).  
  
## <a name="considerations-for-working-with-a-streaming-provider"></a>Důležité informace týkající se práce se zprostředkovateli datových proudů  
 Níže jsou věci k uvážení při implementaci zprostředkovatele datových proudů a když je přístup k prostředkům média z datové služby.  
  
-   Požadavky na SLOUČENÍ nejsou podporovány pro prostředky médií. Chcete-li změnit mediální zdroj existující entity použijte požadavek PUT.  
  
-   Požadavek POST nelze použít k vytvoření nového média odkazů. Místo toho musíte vydat požadavek POST vytvořit nový prostředek služby media a datové služby vytvoří nové médium odkazů s výchozími hodnotami. Tato nová entita je možné aktualizovat podle další požadavek SLOUČENÍ nebo PUT. Zvažte možnost ukládání do mezipaměti entity, kde můžete provést aktualizace v zneškodňovatel, jako je například nastavení hodnoty vlastnosti na hodnotu záhlaví zkráceného názvu stránky v požadavku POST.  
  
-   Při přijetí požadavku POST data servisní volání <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> a vytvoří prostředek služby media dříve, než se zavolá <xref:System.Data.Services.IUpdatable.SaveChanges%2A> k vytvoření médií záznamu odkazu.  
  
-   Implementace <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> by neměly vracet <xref:System.IO.MemoryStream> objektu. Pokud použijete tento druh datového proudu, dojde k potížím prostředků paměti když služba přijímá velmi velkých datových proudů.  
  
-   Tady jsou věci k uvážení při ukládání zdroje médií v databázi:  
  
    -   Binární vlastnost, která je příslušný mediální zdroj by neměl být zařazen datového modelu. Všechny vlastnosti, které jsou zveřejněné v datovém modelu se vrátí v položce v odpovědi informačního kanálu.  
  
    -   Zlepšení výkonu pomocí velké binární datový proud, doporučujeme vám, že vytvoříte vlastní datový proud třídu pro ukládání binárních dat v databázi. Tato třída je vrácený vaše <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> provádění a odešle binární data do databáze v blocích. Pro databázi serveru SQL Server doporučujeme použít FILESTREAM pro streamování dat do databáze, pokud binárních dat je větší než 1MB.  
  
    -   Ujistěte se, že vaše databáze je navržená k ukládání binární velké datové proudy, které se mají přijímat datové služby.  
  
    -   Když klient odešle požadavek POST vložit položku media link entry s prostředkem média v rámci jednoho požadavku <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> je volána k získání datového proudu před datové služby vloží nové entity do databáze. Streamování implementaci zprostředkovatele musí být schopna zpracovávat toto chování služby data. Zvažte použití samostatná data pro tabulku pro ukládání binárních dat nebo úložiště na datový proud v souboru až po entity byla vložena do databáze.  
  
-   Při implementaci <xref:System.Data.Services.Providers.IDataServiceStreamProvider.DeleteStream%2A>, <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStream%2A>, nebo <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> metody, musíte použít značku eTag a Content-Type hodnoty, které jsou dodávány jako parametry metody. Nenastavujte eTag nebo záhlaví Content-Type v vaše <xref:System.Data.Services.Providers.IDataServiceStreamProvider> používaná implementace poskytovatele.  
  
-   Ve výchozím nastavení klient odešle velké binární datové proudy s použitím bloku HTTP Transfer-Encoding. Vzhledem k tomu, [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] vývojový Server nepodporuje tento typ kódování, nelze použít tento webový server k hostování datových proudů datových služeb, musíte přijmout velké binární datové proudy. Další informace o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] vývojový Server, naleznete v tématu [webové servery v sadě Visual Studio pro webové projekty ASP.NET](https://msdn.microsoft.com/library/31d4f588-df59-4b7e-b9ea-e1f2dd204328).  
  
<a name="versioning"></a>   
## <a name="versioning-requirements"></a>Požadavky na správu verzí  
 Zprostředkovatel streamování má následující [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokol požadavků na správu verzí:  
  
-   Zprostředkovatel streamování vyžaduje, aby podporoval službu dat verzi 2.0 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokol a novějších verzích.  
  
 Další informace najdete v tématu [Správa verzí datové služby](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také  
 [Zprostředkovatelé datových služeb](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [Vlastní zprostředkovatelé datových služeb](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)  
 [Práce s binárními daty](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md)
