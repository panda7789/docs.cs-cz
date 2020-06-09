---
title: Přehled architektury metadat
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], overview
ms.assetid: 1d37645e-086d-4d68-a358-f3c5b6e8205e
ms.openlocfilehash: a6bd41fa5aed4c2a22ee7c72087e2da0d7e4ea17
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598850"
---
# <a name="metadata-architecture-overview"></a>Přehled architektury metadat
Windows Communication Foundation (WCF) poskytuje bohatou infrastrukturu pro export, publikování, načítání a import metadat služby. Služby WCF používají metadata k popisu způsobu interakce s koncovými body služby, aby nástroje, jako je Svcutil. exe, mohly automaticky generovat kód klienta pro přístup ke službě.  
  
 Většina typů, které tvoří infrastrukturu metadat WCF, se nachází v <xref:System.ServiceModel.Description> oboru názvů.  
  
 WCF používá <xref:System.ServiceModel.Description.ServiceEndpoint> třídu k popisu koncových bodů ve službě. Pomocí WCF můžete generovat metadata pro koncové body služby nebo importovat metadata služby pro generování <xref:System.ServiceModel.Description.ServiceEndpoint> instancí.  
  
 WCF představuje metadata pro službu jako instanci <xref:System.ServiceModel.Description.MetadataSet> typu. struktura, která je silně svázána s formátem serializace metadat definovaným v WS-MetadataExchange. <xref:System.ServiceModel.Description.MetadataSet>Typ naváže skutečná metadata služby, jako jsou dokumenty jazyka WSDL (Web Services Description Language), dokumenty schématu XML nebo výrazy WS-Policy jako kolekce <xref:System.ServiceModel.Description.MetadataSection> instancí. Každá <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> instance obsahuje konkrétní dialekt metadat a identifikátor. <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType>Může obsahovat následující položky ve své <xref:System.ServiceModel.Description.MetadataSection.Metadata%2A?displayProperty=nameWithType> vlastnosti:  
  
- Nezpracovaná metadata  
  
- <xref:System.ServiceModel.Description.MetadataReference>Instance.  
  
- <xref:System.ServiceModel.Description.MetadataLocation>Instance.  
  
 <xref:System.ServiceModel.Description.MetadataReference?displayProperty=nameWithType>Instance ukazují na koncový bod a instance jiného serveru metadat (MEX) <xref:System.ServiceModel.Description.MetadataLocation?displayProperty=nameWithType> odkazují na dokument metadat pomocí adresy URL protokolu HTTP. Služba WCF podporuje použití dokumentů WSDL k popisu koncových bodů služby, kontraktů služeb, vazeb, vzorců výměny zpráv, zpráv a zpráv o chybách implementovaných službou. Datové typy používané službou jsou popsány v dokumentu WSDL pomocí schématu XML. Další informace najdete v tématu [Import a Export schématu](schema-import-and-export.md). Pomocí služby WCF můžete exportovat a importovat rozšíření WSDL pro chování služby, chování kontraktu a prvky vazby, které zvyšují funkčnost služby. Další informace najdete v tématu [Export vlastních metadat pro rozšíření WCF](../extending/exporting-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="exporting-service-metadata"></a>Exportují se metadata služby.  
 V rámci WCF je *Export metadat* proces popsání koncových bodů služby a jejich prochází paralelně standardizovaným znázorněním, které mohou klienti použít k pochopení toho, jak službu používat. Chcete-li exportovat metadata z <xref:System.ServiceModel.Description.ServiceEndpoint> instancí, použijte implementaci <xref:System.ServiceModel.Description.MetadataExporter> abstraktní třídy. <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType>Implementace generuje metadata, která jsou zapouzdřena v <xref:System.ServiceModel.Description.MetadataSet> instanci.  
  
 <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType>Třída poskytuje rozhraní pro generování výrazů zásad, které popisují schopnosti a požadavky vazby koncového bodu a jeho přidružené operace, zprávy a chyby. Tyto výrazy zásad jsou zachyceny v <xref:System.ServiceModel.Description.PolicyConversionContext> instanci. <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType>Implementace pak může připojit tyto výrazy zásad k metadatům, které generuje.  
  
 <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType>Volání do každého <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> , který implementuje <xref:System.ServiceModel.Description.IPolicyExportExtension> rozhraní ve vazbě <xref:System.ServiceModel.Description.ServiceEndpoint> při generování <xref:System.ServiceModel.Description.PolicyConversionContext> objektu pro <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> použití implementace. Můžete exportovat nové kontrolní výrazy zásad implementací <xref:System.ServiceModel.Description.IPolicyExportExtension> rozhraní pro vlastní implementace <xref:System.ServiceModel.Channels.BindingElement> typu.  
  
 <xref:System.ServiceModel.Description.WsdlExporter>Typ je implementace <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> abstraktní třídy, která je součástí WCF. <xref:System.ServiceModel.Description.WsdlExporter>Typ generuje metadata WSDL s připojenými výrazy zásad.  
  
 Chcete-li exportovat vlastní metadata WSDL nebo rozšíření WSDL pro chování koncových bodů, chování kontraktu nebo prvky vazby v koncovém bodu služby, můžete implementovat <xref:System.ServiceModel.Description.IWsdlExportExtension> rozhraní. Podívá se <xref:System.ServiceModel.Description.WsdlExporter> na <xref:System.ServiceModel.Description.ServiceEndpoint> instanci pro prvky vazby, chování operace, chování kontraktu a chování koncového bodu, které implementuje <xref:System.ServiceModel.Description.IWsdlExportExtension> rozhraní při generování dokumentu WSDL.  
  
## <a name="publishing-service-metadata"></a>Publikování metadat služby  
 Služby WCF publikují metadata vyvoláním jednoho nebo více koncových bodů metadat. Publikování metadat služby zpřístupňuje metadata služby pomocí standardizovaných protokolů, jako jsou požadavky MEX a HTTP/GET. Koncové body metadat jsou podobné jiným koncovým bodům služby v tom, že mají adresu, vazbu a kontrakt. Můžete přidat koncové body metadat do hostitele služby v konfiguraci nebo v kódu.  
  
 Chcete-li publikovat koncové body metadat pro službu WCF, musíte nejprve do služby přidat instanci <xref:System.ServiceModel.Description.ServiceMetadataBehavior> chování služby. Přidání <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> instance do služby rozšiřuje vaši službu o možnost publikovat metadata vyplněním jednoho nebo více koncových bodů metadat. Jakmile přidáte <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> chování služby, můžete vystavit koncové body metadat podporující protokol MEX nebo koncové body metadat, které reagují na požadavky HTTP/GET.  
  
 Chcete-li přidat koncové body metadat používající protokol MEX, přidejte koncové body služby pro hostitele služby, které používají kontrakt služby s názvem IMetadataExchange. WCF definuje <xref:System.ServiceModel.Description.IMetadataExchange> rozhraní, které má tento název kontraktu služby. Koncové body WS-MetadataExchange nebo MEX můžou použít jednu ze čtyř výchozích vazeb vystavených statickými výrobními metodami <xref:System.ServiceModel.Description.MetadataExchangeBindings> třídy, aby odpovídaly výchozím vazbám používaným v nástrojích WCF, jako je Svcutil. exe. Můžete také nakonfigurovat koncové body metadat MEX pomocí vlastní vazby.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>Používá <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> k exportu metadat pro všechny koncové body služby ve vaší službě. Další informace o exportu metadat ze služby najdete v tématu [Export a import metadat](exporting-and-importing-metadata.md).  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>Rozšiřuje hostitele služby přidáním <xref:System.ServiceModel.Description.ServiceMetadataExtension> instance jako rozšíření pro hostitele služby. <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType>Poskytuje implementaci pro protokoly publikování metadat. K <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> získání metadat služby za běhu můžete použít také přístup k <xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A> Vlastnosti.  
  
> [!CAUTION]
> Pokud přidáte koncový bod MEX do konfiguračního souboru aplikace a potom se pokusíte přidat <xref:System.ServiceModel.Description.ServiceMetadataBehavior> do hostitele služby v kódu, získáte následující výjimku:  
>
> System. InvalidOperationException: název kontraktu ' IMetadataExchange ' nebyl nalezen v seznamu kontraktů implementovaných službou Service Service1. Přidejte ServiceMetadataBehavior do konfiguračního souboru nebo do hostitele ServiceHost přímo pro povolení podpory této smlouvy.  
>
> Tento problém můžete obejít tak, že přidáte <xref:System.ServiceModel.Description.ServiceMetadataBehavior> konfigurační soubor do konfiguračního souboru nebo přidáte jak koncový bod, tak i <xref:System.ServiceModel.Description.ServiceMetadataBehavior> v kódu.  
>
> Příklad přidání <xref:System.ServiceModel.Description.ServiceMetadataBehavior> do konfiguračního souboru aplikace naleznete v [Začínáme](../samples/getting-started-sample.md). Příklad přidání <xref:System.ServiceModel.Description.ServiceMetadataBehavior> v kódu naleznete v části ukázka pro [sebe v samostatném hostiteli](../samples/self-host.md) .  

> [!CAUTION]
> Při publikování metadat pro službu, která zveřejňuje dvě různé kontrakty služby, ve kterých každá obsahuje operaci se stejným názvem, je vyvolána výjimka. Například pokud máte službu, která zveřejňuje kontrakt služby s názvem ICarService, který obsahuje operaci get (auto c), a stejná služba zveřejňuje kontrakt služby s názvem IBookService, který má operaci get (Book b), je vyvolána výjimka nebo při generování metadat služby se zobrazí chybová zpráva. Pokud chcete tento problém obejít, proveďte jednu z následujících akcí:  
>
> - Přejmenujte jednu z operací.
> - Nastavte na <xref:System.ServiceModel.OperationContractAttribute.Name%2A> jiný název.  
> - Nastavte jeden z oborů názvů operací na jiný obor názvů pomocí <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> Vlastnosti.  
  
## <a name="retrieving-service-metadata"></a>Načítají se metadata služby.  
 WCF může načítat metadata služby pomocí standardizovaných protokolů, jako jsou WS-MetadataExchange a HTTP. Oba tyto protokoly jsou podporovány <xref:System.ServiceModel.Description.MetadataExchangeClient> typem. Metadata služby můžete načíst pomocí typu zadáním <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> adresy a volitelné vazby. Vazba, kterou používá <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> instance, může být jedna z výchozích vazeb ze <xref:System.ServiceModel.Description.MetadataExchangeBindings> statické třídy, uživatelsky zadané vazby nebo vazby načtené z konfigurace koncového bodu pro `IMetadataExchange` kontrakt. <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType>Může také vyřešit odkazy adresy URL http na metadata pomocí <xref:System.Net.HttpWebRequest> typu.  
  
 Ve výchozím nastavení <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> je instance svázána s jednou <xref:System.ServiceModel.Channels.ChannelFactoryBase> instancí. Můžete změnit nebo nahradit instanci, kterou <xref:System.ServiceModel.Channels.ChannelFactoryBase> používá, <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> přepsáním <xref:System.ServiceModel.Description.MetadataExchangeClient.GetChannelFactory%2A> virtuální metody. Podobně můžete změnit nebo nahradit instanci, kterou <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> používá, <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> k provádění požadavků HTTP/GET přepsáním <xref:System.ServiceModel.Description.MetadataExchangeClient.GetWebRequest%2A?displayProperty=nameWithType> virtuální metody.  
  
 Metadata služby můžete načíst pomocí požadavků WS-MetadataExchange nebo HTTP/GET pomocí nástroje Svcutil. exe a předáním přepínače **/target: metadata** a adresy. Svcutil. exe stáhne metadata na zadané adrese a uloží soubory na disk. Svcutil. exe používá <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> instanci interně a načítá konfiguraci koncového bodu MEX (z konfiguračního souboru aplikace), jejíž název odpovídá schématu adresy předané na Svcutil. exe, pokud existuje. V opačném případě Svcutil. exe ve výchozím nastavení používá jednu z vazeb definovaných <xref:System.ServiceModel.Description.MetadataExchangeBindings> typem statického objektu pro vytváření.  
  
## <a name="importing-service-metadata"></a>Importují se metadata služby.  
 V rámci WCF je import metadat proces generování abstraktní reprezentace služby nebo jejích součástí z metadat. Služba WCF může například importovat <xref:System.ServiceModel.Description.ServiceEndpoint> instance, <xref:System.ServiceModel.Channels.Binding> instance nebo <xref:System.ServiceModel.Description.ContractDescription> instance z dokumentu WSDL pro službu. Chcete-li importovat metadata služby ve službě WCF, použijte implementaci <xref:System.ServiceModel.Description.MetadataImporter> abstraktní třídy. Typy, které jsou odvozeny z <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> třídy, implementují podporu pro Import formátů metadat, které využívají logiku importu WS-Policy ve službě WCF.  
  
 <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType>Implementace shromažďuje výrazy zásad připojené k metadatům služby v <xref:System.ServiceModel.Description.PolicyConversionContext> objektu. <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType>Pak zpracuje zásady v rámci importu metadat voláním implementací <xref:System.ServiceModel.Description.IPolicyImportExtension> rozhraní ve <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> Vlastnosti.  
  
 Můžete přidat podporu pro import nových kontrolních výrazů zásad do a <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> přidáním vlastní implementace <xref:System.ServiceModel.Description.IPolicyImportExtension> rozhraní do <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> kolekce v <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> instanci. Případně můžete zaregistrovat rozšíření pro import zásad do konfiguračního souboru klientské aplikace.  
  
 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>Typ je implementace <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> abstraktní třídy, která je součástí WCF. <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>Typ Importuje metadata WSDL s připojenými zásadami, které jsou v objektu seskupeny <xref:System.ServiceModel.Description.MetadataSet> .  
  
 Můžete přidat podporu pro import rozšíření WSDL implementací <xref:System.ServiceModel.Description.IWsdlImportExtension> rozhraní a následnou přidáním vaší implementace do <xref:System.ServiceModel.Description.WsdlImporter.WsdlImportExtensions%2A> vlastnosti v <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> instanci. <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>Může také načítat implementace <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> rozhraní registrovaného v konfiguračním souboru klientské aplikace.  
  
## <a name="dynamic-bindings"></a>Dynamické vazby  
 Vazbu, kterou použijete k vytvoření kanálu pro koncový bod služby, můžete dynamicky aktualizovat v případě, že se vazba pro koncový bod změní nebo chcete vytvořit kanál ke koncovému bodu, který používá stejný kontrakt, ale má jinou vazbu. Statickou třídu můžete použít <xref:System.ServiceModel.Description.MetadataResolver> k načtení a importu metadat za běhu pro koncové body služby, které implementují konkrétní kontrakt. Pomocí importovaných objektů pak můžete vytvořit objekt pro vytváření <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> klienta nebo kanálu do požadovaného koncového bodu.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Description>
- [Formáty metadat](metadata-formats.md)
- [Export a import metadat](exporting-and-importing-metadata.md)
- [Publikování metadat](publishing-metadata.md)
- [Načítání metadat](retrieving-metadata.md)
- [Používání metadat](using-metadata.md)
- [Informace o zabezpečení metadat](security-considerations-with-metadata.md)
- [Rozšíření systému metadat](../extending/extending-the-metadata-system.md)
