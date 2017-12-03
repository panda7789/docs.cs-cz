---
title: "Přehled architektury metadat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: metadata [WCF], overview
ms.assetid: 1d37645e-086d-4d68-a358-f3c5b6e8205e
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cc42aa130ce5da05739af43d287441d1644d55c3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="metadata-architecture-overview"></a>Přehled architektury metadat
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]poskytuje bohaté infrastrukturu pro export, publikování, načítání a Import metadata služby. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]služby používají metadata k popisují, jak pracovat s koncovými body služby tak, aby nástroje, jako je například Svcutil.exe, může automaticky generovat kód klienta pro přístup k službě.  
  
 Většina typů, které tvoří [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury metadata jsou umístěny ve <xref:System.ServiceModel.Description> oboru názvů.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]používá <xref:System.ServiceModel.Description.ServiceEndpoint> třída k popisu koncových bodů ve službě. Můžete použít [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ke generování metadat pro koncové body služby nebo importovat metadata služby ke generování <xref:System.ServiceModel.Description.ServiceEndpoint> instance.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]představuje metadata pro služby jako instanci <xref:System.ServiceModel.Description.MetadataSet> typu, jejichž struktura je důrazně vázaný na formát serializace metadata definované v WS-MetadataExchange. <xref:System.ServiceModel.Description.MetadataSet> Typ obsahuje metadata skutečné služby, jako jsou webové služby popis Language (WSDL) dokumenty, dokumentech schémat XML nebo výrazy WS-Policy, ureitou jako kolekce <xref:System.ServiceModel.Description.MetadataSection> instance. Každý <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> instance obsahuje dialekt konkrétních metadat a identifikátor. A <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> může obsahovat následující položky v jeho <xref:System.ServiceModel.Description.MetadataSection.Metadata%2A?displayProperty=nameWithType> vlastnost:  
  
-   Nezpracovaná metadata.  
  
-   A <xref:System.ServiceModel.Description.MetadataReference> instance.  
  
-   A <xref:System.ServiceModel.Description.MetadataLocation> instance.  
  
 A <xref:System.ServiceModel.Description.MetadataReference?displayProperty=nameWithType> instance, přejděte na jiný koncový bod metadat exchange (MEX) a <xref:System.ServiceModel.Description.MetadataLocation?displayProperty=nameWithType> instancí bodu k dokumentu metadat pomocí adresy URL protokolu HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]podporuje použití dokumentů WSDL k popisu koncové body služby, kontraktů služby, vazby, zprávu výměna vzory, zpráv a chybové zprávy, které jsou implementované služby. Datové typy, které používá služba jsou popsané v dokumentech WSDL pomocí schématu XML. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Import a Export schémat](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md). Můžete použít [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pro export a import rozšíření schématu WSDL pro chování služby, smlouvy chování a prvky vazeb, které rozšiřují funkce služby. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Export vlastních metadat pro rozšíření WCF](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="exporting-service-metadata"></a>Export metadat služby  
 V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], *export metadat* je proces popisující koncové body služby a projekce je do znázornění paralelní, standardizované, který můžou klienti používat pochopit, jak používat službu. Pro export metadat z <xref:System.ServiceModel.Description.ServiceEndpoint> instance slouží provádění <xref:System.ServiceModel.Description.MetadataExporter> abstraktní třídy. A <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> implementace generuje metadata, která je zapouzdřené v <xref:System.ServiceModel.Description.MetadataSet> instance.  
  
 <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> Třída poskytuje rozhraní pro generování výrazy zásad, které popisují možnosti a požadavky vazbu koncového bodu a jeho přidružené operace, zpráv a chyb. Tyto výrazy zásad zachyceny v <xref:System.ServiceModel.Description.PolicyConversionContext> instance. A <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> implementace můžete tyto výrazy zásad pak připojit k metadatům vygeneruje.  
  
 <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> Volání do každé <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> , která implementuje <xref:System.ServiceModel.Description.IPolicyExportExtension> rozhraní v vazba <xref:System.ServiceModel.Description.ServiceEndpoint> při generování <xref:System.ServiceModel.Description.PolicyConversionContext> objekt pro <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> implementace používat. Nové výrazy zásad můžete exportovat implementací <xref:System.ServiceModel.Description.IPolicyExportExtension> rozhraní na vaše vlastní implementace <xref:System.ServiceModel.Channels.BindingElement> typu.  
  
 <xref:System.ServiceModel.Description.WsdlExporter> Typ je implementace <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> abstraktní třídy součástí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. <xref:System.ServiceModel.Description.WsdlExporter> Typ generuje WSDL metadat pomocí výrazů zásad připojené.  
  
 Export vlastních metadat WSDL nebo rozšíření WSDL pro koncový bod chování, kontrakt chování nebo prvky vazeb v koncového bodu služby, můžete implementovat <xref:System.ServiceModel.Description.IWsdlExportExtension> rozhraní. <xref:System.ServiceModel.Description.WsdlExporter> Zjistí <xref:System.ServiceModel.Description.ServiceEndpoint> instance pro vazby prvky, operace chování, kontrakt chování a koncový bod chování, které implementují <xref:System.ServiceModel.Description.IWsdlExportExtension> rozhraní při generování souboru WSDL.  
  
## <a name="publishing-service-metadata"></a>Publikování metadat služby  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]služby publikování metadat díky zpřístupnění jeden nebo více koncových bodů metadat. Publikování metadat služby zpřístupní metadata služby pomocí standardizovaných protokolů, jako jsou žádosti o MEX a HTTP/GET. Koncové body metadat jsou podobná další koncové body služby v tom, že mají adresy, vazby a kontraktu. Koncové body metadat můžete přidat na hostitele služby v konfiguraci nebo v kódu.  
  
 Publikování kocových bodů metadat pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, je nejprve nutno přidat instanci <xref:System.ServiceModel.Description.ServiceMetadataBehavior> služby chování ke službě. Přidání <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> instance služby rozšiřuje služby umožňuje publikování metadat díky zpřístupnění jeden nebo více koncových bodů metadat. Jakmile přidáte <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> chování služby můžete pak vystavit koncové body metadat, které podporují MEX protokolu nebo metadat koncových bodů, které reagují na požadavky HTTP/GET.  
  
 Přidat koncové body metadat, které používají protokol MEX, přidejte do vaší hostitele služby využívající kontrakt služby s názvem IMetadataExchange koncové body služby.[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] definuje <xref:System.ServiceModel.Description.IMetadataExchange> rozhraní, které má tento název kontraktu služby. Koncové body služby WS-MetadataExchange, nebo MEX koncových bodů, můžete použít jednu z vazby čtyři výchozí vystavené factory statické metody na <xref:System.ServiceModel.Description.MetadataExchangeBindings> třídy tak, aby odpovídala výchozí vazby používané [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nástroje, jako je například Svcutil.exe. Můžete také nakonfigurovat koncové body metadat MEX použití vlastní vazby.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Používá <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> pro export metadat pro všechny koncové body služby ve službě. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Export metadat ze služby, najdete v části [export a import metadat](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Rozšiřuje vaše hostitele služby přidáním <xref:System.ServiceModel.Description.ServiceMetadataExtension> instance jako rozšíření na hostiteli služby. <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> Poskytuje implementaci pro publikování protokoly metadat. Můžete také použít <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> se získat metadata služby za běhu přímým přístupem <xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A> vlastnost.  
  
> [!CAUTION]
>  Pokud přidáte koncový bod MEX v konfiguračním souboru aplikace a pak se pokusíte přidat <xref:System.ServiceModel.Description.ServiceMetadataBehavior> k hostiteli služby v kódu můžete získat následující výjimky:  
>   
>  System.InvalidOperationException: Název kontraktu 'IMetadataExchange' nebyl nalezen v seznamu smluv, které implementují službu Service1. Přidáte vlastnosti ServiceMetadataBehavior do konfiguračního souboru nebo ServiceHost přímo k povolení podpory pro tento kontrakt.  
>   
>  Tento problém můžete vyřešit přidáním buď <xref:System.ServiceModel.Description.ServiceMetadataBehavior> v konfiguračním souboru nebo přidání obou koncový bod a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> v kódu.  
>   
>  Příklad přidání <xref:System.ServiceModel.Description.ServiceMetadataBehavior> v konfiguračním souboru aplikace naleznete v části [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). Příklad přidání <xref:System.ServiceModel.Description.ServiceMetadataBehavior> v kódu, najdete v článku [hostování na vlastním](../../../../docs/framework/wcf/samples/self-host.md) ukázka.  
  
> [!CAUTION]
>  Při publikování metadat služby, který zveřejňuje dva různé služby měnící každá obsahovat operace se stejným názvem výjimku je vyvolána. Například pokud máte služby, která zveřejňuje kontrakt služby s názvem ICarService, který má operace získání (Car c) a stejnou službu zpřístupní kontrakt služby s názvem IBookService, který má operace Get (kniha b), je vyvolána výjimka, nebo je chybová zpráva Zobrazí, když generování metadat služby. Chcete-li vyřešit tomuto problému, proveďte jednu z následujících:  
>   
>  -   Přejmenujte jeden z činnosti.  
> -   Nastavte <xref:System.ServiceModel.OperationContractAttribute.Name%2A> na jiný název.  
> -   Jeden z oborů názvů na operace nastavenou na jiný obor názvů pomocí <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> vlastnost.  
  
## <a name="retrieving-service-metadata"></a>Načítání metadat služby  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]můžete načíst metadata služby pomocí standardizovaných protokolů, jako je WS-MetadataExchange a HTTP. Obě tyto protokoly jsou podporovány <xref:System.ServiceModel.Description.MetadataExchangeClient> typu. Načtení služby metadat pomocí <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> typ poskytnutím adresy a volitelné vazby. Vazby používané <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> instance může být jedna z vazeb výchozí z <xref:System.ServiceModel.Description.MetadataExchangeBindings> statická třída, vazbu uživatelem zadané nebo vazbu načtené ze konfigurace koncového bodu pro `IMetadataExchange` kontrakt. <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> Můžete také vyřešit odkazy na základní adresy URL metadat pomocí <xref:System.Net.HttpWebRequest> typu.  
  
 Ve výchozím nastavení <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> instance je vázaný na jednu <xref:System.ServiceModel.Channels.ChannelFactoryBase> instance. Můžete změnit nebo nahradit <xref:System.ServiceModel.Channels.ChannelFactoryBase> instanci použitou <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> přepsáním <xref:System.ServiceModel.Description.MetadataExchangeClient.GetChannelFactory%2A> virtuální metoda. Podobně můžete změnit nebo nahradit <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> instanci použitou <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> provádět požadavky HTTP/GET přepsáním <xref:System.ServiceModel.Description.MetadataExchangeClient.GetWebRequest%2A?displayProperty=nameWithType> virtuální metoda.  
  
 Můžete načíst metadata služby pomocí protokolu WS-MetadataExchange nebo protokolu HTTP nebo získat požadavků pomocí nástroje Svcutil.exe a předávání **/target:metadata** přepínač a adresu. Svcutil.exe metadata na zadané adrese stáhne a uloží soubory na disk. Používá svcutil.exe <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> instance interně a načítání MEX koncový bod konfigurace aplikace (z konfiguračního souboru aplikace) jejíž název odpovídá schéma adresy předaný Svcutil.exe, pokud existuje. V opačném Svcutil.exe ve výchozím nastavení používá jedna z vazeb definovaných prostředím <xref:System.ServiceModel.Description.MetadataExchangeBindings> typ objektu pro vytváření statické.  
  
## <a name="importing-service-metadata"></a>Import metadat služby  
 V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], import metadat je proces generování abstraktní reprezentace služby nebo jeho součásti z jeho metadata. Například [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] můžete importovat <xref:System.ServiceModel.Description.ServiceEndpoint> instancí <xref:System.ServiceModel.Channels.Binding> instance nebo <xref:System.ServiceModel.Description.ContractDescription> instancí z WSDL dokumentů pro službu. Chcete-li importovat metadata služby v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], použít implementaci <xref:System.ServiceModel.Description.MetadataImporter> abstraktní třídy. Typy, které jsou odvozeny od <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> třída implementovat podporu pro import formáty metadat, které využít WS-Policy importovat logiku [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 A <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> implementace shromažďuje výrazy zásad, které jsou připojené k metadata služby v <xref:System.ServiceModel.Description.PolicyConversionContext> objektu. <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> Pak zpracovává zásady v rámci importu metadata voláním implementace <xref:System.ServiceModel.Description.IPolicyImportExtension> rozhraní v <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> vlastnost.  
  
 Můžete přidat podporu pro nové výrazy zásad pro import <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> přidáním vlastní implementaci <xref:System.ServiceModel.Description.IPolicyImportExtension> rozhraní k <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> kolekce na <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> instance. Alternativně můžete zaregistrovat import rozšíření zásad v konfiguračním souboru aplikace klienta.  
  
 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Typ je implementace <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> abstraktní třídy součástí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Typ naimportuje metadata WSDL s připojené zásady, které jsou seskupeny v <xref:System.ServiceModel.Description.MetadataSet> objektu.  
  
 Můžete přidat podporu pro import rozšíření schématu WSDL implementací <xref:System.ServiceModel.Description.IWsdlImportExtension> rozhraní a následným přidáním do vaší implementace <xref:System.ServiceModel.Description.WsdlImporter.WsdlImportExtensions%2A> vlastnost na vaše <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> instance. <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Můžete také načíst implementace <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> rozhraní registrovaný v konfiguračním souboru aplikace klienta.  
  
## <a name="dynamic-bindings"></a>Dynamické vazby  
 Vazba, která můžete použít k vytvoření kanálu pro koncový bod služby v případě, že změní vazby pro koncový bod můžete aktualizovat dynamicky nebo chcete vytvořit kanál pro koncový bod, který používá stejné smlouvy, ale má jinou vazbou. Můžete použít <xref:System.ServiceModel.Description.MetadataResolver> statická třída pro načtení a import metadat při běhu pro koncové body služby, které implementují konkrétní smlouvě. Pak můžete použít importovaných <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> objekty pro vytváření klienta nebo kanál pro požadovaný koncový bod.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description>  
 [Formáty metadat](../../../../docs/framework/wcf/feature-details/metadata-formats.md)  
 [Export a import metadat](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)  
 [Publikování metadat](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)  
 [Načítání metadat](../../../../docs/framework/wcf/feature-details/retrieving-metadata.md)  
 [Pomocí metadat](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [Aspekty zabezpečení s metadaty](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)  
 [Rozšíření systému metadat](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)
