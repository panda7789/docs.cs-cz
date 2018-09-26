---
title: Přehled architektury metadat
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], overview
ms.assetid: 1d37645e-086d-4d68-a358-f3c5b6e8205e
ms.openlocfilehash: d0fc45b5ccabedb127061090eed1f6b63fd7acba
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47108373"
---
# <a name="metadata-architecture-overview"></a>Přehled architektury metadat
Windows Communication Foundation (WCF) poskytuje bohaté infrastrukturu pro export, publikování, načítání a import metadat služby. Služby WCF pomocí metadata popisují, jak pracovat s koncovými body služby tak, aby nástroje, jako je například Svcutil.exe, můžete automaticky vygenerovat kód klienta pro přístupu ke službě.  
  
 Většina typů, které tvoří infrastruktura WCF metadat jsou umístěny v <xref:System.ServiceModel.Description> oboru názvů.  
  
 Používá WCF <xref:System.ServiceModel.Description.ServiceEndpoint> tříd k popisu koncových bodů služby. Generovat metadata pro koncové body služby nebo importovat metadata služby pro generování můžou využít WCF <xref:System.ServiceModel.Description.ServiceEndpoint> instancí.  
  
 WCF představuje metadata pro služby jako instance <xref:System.ServiceModel.Description.MetadataSet> typ struktura, z nichž se silnou vazbu na formát serializace metadata definované v WS-MetadataExchange. <xref:System.ServiceModel.Description.MetadataSet> Typ obsahuje metadata aktuální služby, jako jsou dokumenty služby popis jazyka WSDL (Web), dokumentů schématu XML nebo výrazy WS-Policy ureitou jako kolekci <xref:System.ServiceModel.Description.MetadataSection> instancí. Každý <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> instance obsahuje metadata specifická dialekt a identifikátor. A <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> může obsahovat následující položky v jeho <xref:System.ServiceModel.Description.MetadataSection.Metadata%2A?displayProperty=nameWithType> vlastnost:  
  
- Nezpracovaná metadata.  
  
- A <xref:System.ServiceModel.Description.MetadataReference> instance.  
  
- A <xref:System.ServiceModel.Description.MetadataLocation> instance.  
  
 A <xref:System.ServiceModel.Description.MetadataReference?displayProperty=nameWithType> instance odkazovat na jiný koncový bod metadat exchange (MEX) a <xref:System.ServiceModel.Description.MetadataLocation?displayProperty=nameWithType> instance přejděte k dokumentu metadat pomocí adresy URL protokolu HTTP. Podporuje WCF popsat koncové body služby, kontrakty služeb, vazby, zpráv exchange vzory, zprávy a chybové zprávy, které implementují službu pomocí dokumenty WSDL. Služba používá datové typy jsou popsány v dokumenty WSDL pomocí schématu XML. Další informace najdete v tématu [Import a Export schémat](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md). K exportu a importu WSDL rozšíření pro chování služby, kontrakt chování a prvky vazeb, které rozšiřují funkce služby můžou využít WCF. Další informace najdete v tématu [export vlastních metadat pro rozšíření WCF](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="exporting-service-metadata"></a>Export metadat služby  
 Ve službě WCF *export metadat* je proces popisující koncové body služby a projekci na paralelní standardizované reprezentaci, který můžou klienti použít k vysvětlení použití služby. Pro export metadat z <xref:System.ServiceModel.Description.ServiceEndpoint> instance slouží provádění <xref:System.ServiceModel.Description.MetadataExporter> abstraktní třídy. A <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> generuje metadata, která jsou zapouzdřena v implementaci <xref:System.ServiceModel.Description.MetadataSet> instance.  
  
 <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> Třída poskytuje architekturu pro generování výrazy zásad, které popisují funkce a požadavky na vazbu koncového bodu a jeho přidružené operace, zprávy a chyby. Tyto výrazy zásad jsou zaznamenány <xref:System.ServiceModel.Description.PolicyConversionContext> instance. A <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> implementace může pak připojte tyto výrazy zásad v metadatech generuje.  
  
 <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> Volání do každé <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> , který implementuje <xref:System.ServiceModel.Description.IPolicyExportExtension> rozhraní v vazba <xref:System.ServiceModel.Description.ServiceEndpoint> při generování <xref:System.ServiceModel.Description.PolicyConversionContext> objekt pro <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> implementace. Nový kontrolní výrazy zásad můžete exportovat na základě implementace <xref:System.ServiceModel.Description.IPolicyExportExtension> na vaše vlastní implementace rozhraní <xref:System.ServiceModel.Channels.BindingElement> typu.  
  
 <xref:System.ServiceModel.Description.WsdlExporter> Typ je provádění <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> abstraktní třída součástí WCF. <xref:System.ServiceModel.Description.WsdlExporter> Typ generuje metadata WSDL s výrazy připojené zásad.  
  
 Export vlastních metadat WSDL nebo rozšíření WSDL pro chování koncového bodu, kontrakt chování nebo elementy vazby v koncového bodu služby, můžete implementovat <xref:System.ServiceModel.Description.IWsdlExportExtension> rozhraní. <xref:System.ServiceModel.Description.WsdlExporter> Zkoumá <xref:System.ServiceModel.Description.ServiceEndpoint> instance pro vazby prvky, chování operace, kontrakt chování a chování koncového bodu, které implementují <xref:System.ServiceModel.Description.IWsdlExportExtension> rozhraní při generování dokumentu WSDL.  
  
## <a name="publishing-service-metadata"></a>Publikování metadat služby  
 Služby WCF měla být zveřejněna metadata zveřejněním na jeden nebo více koncových bodů metadat. Publikování metadat služby zpřístupňuje metadata služby pomocí standardizovaných protokolů, jako jsou žádosti o MEX a HTTP/GET. Koncové body metadat se podobně jako ostatní koncové body služby, že mají adresy, vazby a kontrakt. Můžete přidat koncové body metadat k hostiteli služby v konfiguraci nebo v kódu.  
  
 Publikování koncových bodů metadat pro služby WCF, musíte nejprve přidat instanci <xref:System.ServiceModel.Description.ServiceMetadataBehavior> služeb chování ve službě. Přidání <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> instance vaší služby argumentech služby umožňuje publikování metadat zveřejněním na jeden nebo více koncových bodů metadat. Jakmile přidáte <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> chování služby je pak zveřejnit koncové body metadat, které podporují MEX protokol nebo metadata koncových bodů, které reagují na požadavky HTTP/GET.  
  
 Chcete-li přidat koncové body metadat, které používají protokol MEX, přidat koncové body služby na hostitele služby, použít kontrakt služby s názvem IMetadataExchange.WCF definuje <xref:System.ServiceModel.Description.IMetadataExchange> rozhraní, které má tento název kontraktu služby. Koncové body WS-MetadataExchange, nebo na koncové body MEX, můžete použít jednu z vystavené statických metod pro vytváření na čtyři výchozí vazby <xref:System.ServiceModel.Description.MetadataExchangeBindings> třídy tak, aby odpovídaly výchozím vazbám používat nástroje, WCF, jako je například Svcutil.exe. Můžete také nakonfigurovat koncové body metadat MEX použití vlastní vazby.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Používá <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> pro export metadat pro všechny koncové body služby ve své službě. Další informace o exportu metadat ze služby najdete v tématu [pro export a import metadat](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Argumentech hostitel vaší služby tak, že přidáte <xref:System.ServiceModel.Description.ServiceMetadataExtension> instance jako rozšíření hostitele služby. <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> Poskytuje implementaci pro publikování protokoly metadat. Můžete také použít <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> se získat metadata služby za běhu díky přístupu do <xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A> vlastnost.  
  
> [!CAUTION]
> Je-li přidat koncový bod MEX v konfiguračním souboru aplikace a pak se pokusíte přidat <xref:System.ServiceModel.Description.ServiceMetadataBehavior> na hostitele služby v kódu můžete získat následující výjimku:  
>
> System.InvalidOperationException: Název kontraktu: IMetadataExchange' nebyl nalezen v seznamu kontraktů implementovaných službou Service1. Přidejte třídu ServiceMetadataBehavior do konfiguračního souboru nebo třídy ServiceHost přímo k povolení podpory pro tento kontrakt.  
>
> Tento problém můžete obejít tak, že buď přidáte <xref:System.ServiceModel.Description.ServiceMetadataBehavior> v konfiguračním souboru nebo přidání na koncový bod a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> v kódu.  
>
> Příklad přidání <xref:System.ServiceModel.Description.ServiceMetadataBehavior> v konfiguračním souboru aplikace, najdete v článku [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). Příklad přidání <xref:System.ServiceModel.Description.ServiceMetadataBehavior> v kódu, najdete v článku [hostování na vlastním serveru](../../../../docs/framework/wcf/samples/self-host.md) vzorku.  

> [!CAUTION]
> Při publikování metadat služby, který poskytuje dvě různé služby smluv každá obsahovat operace se stejným názvem výjimka je vyvolána. Například pokud máte službu, která zveřejňuje kontrakt služby s názvem ICarService, který má operace získání (Auto c) a ve stejné službě zpřístupňuje kontrakt služby s názvem IBookService, který má operace Get (kniha b), je vyvolána výjimka nebo chybová zpráva Zobrazí se při generování metadat služby. Chcete-li tomuto problému, proveďte jednu z následujících akcí:  
>
> - Po přejmenování jedné z operací.
> - Nastavte <xref:System.ServiceModel.OperationContractAttribute.Name%2A> na jiný název.  
> - Jeden z oborů názvů operace nastavenou na jiný obor názvů pomocí <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> vlastnost.  
  
## <a name="retrieving-service-metadata"></a>Načítání metadat služby  
 WCF můžete načíst metadata služby pomocí standardizovaných protokolů, jako je WS-MetadataExchange a HTTP. Obě tyto protokoly jsou podporovány <xref:System.ServiceModel.Description.MetadataExchangeClient> typu. Načtení služby metadata pomocí <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> typu poskytnutím adresy a volitelné vazby. Vazba používá <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> instance může být jedna z výchozích vazeb z <xref:System.ServiceModel.Description.MetadataExchangeBindings> statické třídy, vazbu uživatelem zadané nebo vazbu načíst z konfigurace koncového bodu pro `IMetadataExchange` kontraktu. <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> Můžete také vyřešit odkazy URL protokolu HTTP pomocí metadat <xref:System.Net.HttpWebRequest> typu.  
  
 Ve výchozím nastavení <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> instance je vázán na jediné <xref:System.ServiceModel.Channels.ChannelFactoryBase> instance. Můžete změnit nebo nahradit <xref:System.ServiceModel.Channels.ChannelFactoryBase> instanci použitou <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> tak, že přepíšete <xref:System.ServiceModel.Description.MetadataExchangeClient.GetChannelFactory%2A> virtuální metody. Podobně můžete změnit nebo nahradit <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> instanci použitou <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> provádět požadavky HTTP/GET tak, že přepíšete <xref:System.ServiceModel.Description.MetadataExchangeClient.GetWebRequest%2A?displayProperty=nameWithType> virtuální metody.  
  
 Můžete načíst metadata služby pomocí nástroje Svcutil.exe a předávání pomocí WS-MetadataExchange nebo HTTP/GET požadavků **/target:metadata** přepínače a adresu. Svcutil.exe metadat na zadané adrese stáhne a uloží soubory na disk. Pomocí svcutil.exe <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> instance interně a načtení MEX konfigurace koncového bodu (z konfiguračního souboru aplikace) jejíž název odpovídá schématu adresy předán Svcutil.exe, pokud existuje. V opačném případě Svcutil.exe ve výchozím nastavení používá jedna z vazeb definovaných prostředím <xref:System.ServiceModel.Description.MetadataExchangeBindings> typ objektu pro vytváření statické.  
  
## <a name="importing-service-metadata"></a>Import metadat služby  
 Import metadat ve službě WCF, je proces generování abstraktní reprezentace služby nebo jeho součásti z jeho metadata. Například můžete importovat WCF <xref:System.ServiceModel.Description.ServiceEndpoint> instancí, <xref:System.ServiceModel.Channels.Binding> instance nebo <xref:System.ServiceModel.Description.ContractDescription> instancí ze souboru WSDL dokumentů pro službu. Při importu metadat služby ve službě WCF použijte implementace <xref:System.ServiceModel.Description.MetadataImporter> abstraktní třídy. Typy, které jsou odvozeny z <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> třída implementovat podporu pro import formáty metadat, které budou využívat WS-Policy importovat logiky ve službě WCF.  
  
 A <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> shromažďuje výrazy zásad, které jsou připojené k metadatům služby v implementaci <xref:System.ServiceModel.Description.PolicyConversionContext> objektu. <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> Zpracuje zásady během importu metadat zavoláním implementace <xref:System.ServiceModel.Description.IPolicyImportExtension> rozhraní v <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> vlastnost.  
  
 Můžete přidat podporu pro import do nové kontrolní výrazy zásad <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> tak, že přidáte vlastní implementaci <xref:System.ServiceModel.Description.IPolicyImportExtension> rozhraní při <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> kolekce na <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> instance. Alternativně můžete zaregistrovat vaše rozšíření importu zásady v konfiguračním souboru aplikace klienta.  
  
 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Typ je provádění <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> abstraktní třída součástí WCF. <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Typ Importuje metadata WSDL s připojenými zásady, které jsou spojeny v <xref:System.ServiceModel.Description.MetadataSet> objektu.  
  
 Můžete přidat podporu pro import WSDL rozšíření implementací <xref:System.ServiceModel.Description.IWsdlImportExtension> rozhraní a následným přidáním implementace <xref:System.ServiceModel.Description.WsdlImporter.WsdlImportExtensions%2A> vlastnost na vaše <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> instance. <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Můžete také načíst implementace <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> rozhraní registrovaný v konfiguračním souboru aplikace klienta.  
  
## <a name="dynamic-bindings"></a>Dynamické vazby  
 Můžete dynamicky aktualizovat vazby, který použijete k vytvoření kanálu pro koncový bod služby v případě, že vazba koncového bodu změní nebo chcete vytvořit kanál pro koncový bod, který používá stejný kontrakt ale má jinou vazbou. Můžete použít <xref:System.ServiceModel.Description.MetadataResolver> statická třída pro načtení a import metadat v době běhu pro koncové body služby, které implementují konkrétní kontraktu. Pak můžete použít importovaná <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> objekty pro vytváření klienta nebo kanálu pro požadovaný koncový bod.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description>  
 [Formáty metadat](../../../../docs/framework/wcf/feature-details/metadata-formats.md)  
 [Export a import metadat](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)  
 [Publikování metadat](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)  
 [Načítání metadat](../../../../docs/framework/wcf/feature-details/retrieving-metadata.md)  
 [Používání metadat](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [Informace o zabezpečení metadat](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)  
 [Rozšíření systému metadat](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)
