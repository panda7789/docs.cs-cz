---
title: Export a import metadat
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], exporting and importing
ms.assetid: 614a75bb-e0b0-4c95-b6d8-02cb5e5ddb38
ms.openlocfilehash: 39b964584cde42e6569da35f8653042f6d7432cb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61856463"
---
# <a name="exporting-and-importing-metadata"></a>Export a import metadat
Ve Windows Communication Foundation (WCF), Export metadat je proces popisující koncové body služby a projekci na paralelní standardizované reprezentaci, který můžou klienti použít k vysvětlení použití služby. Import metadat služby je procesem generování <xref:System.ServiceModel.Description.ServiceEndpoint> instance nebo části z metadat služby.  
  
## <a name="exporting-metadata"></a>Export metadat  
 Pro export metadat z <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> instance slouží provádění <xref:System.ServiceModel.Description.MetadataExporter> abstraktní třídy. <xref:System.ServiceModel.Description.WsdlExporter> Typ je provádění <xref:System.ServiceModel.Description.MetadataExporter> abstraktní třída součástí WCF.  
  
 <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> Typ generuje metadata služby popis jazyka WSDL (Web) pomocí výrazů zásad připojené zapouzdřené v <xref:System.ServiceModel.Description.MetadataSet> instance. Můžete použít <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> instance pro iterativní export metadat pro <xref:System.ServiceModel.Description.ContractDescription> objekty a <xref:System.ServiceModel.Description.ServiceEndpoint> objekty. Můžete také exportovat kolekci <xref:System.ServiceModel.Description.ServiceEndpoint> objektů a přidružit je k název konkrétní služby.  
  
> [!NOTE]
>  Lze použít pouze `WsdlExporter` pro export metadat z `ContractDescription` instancí, které obsahují common language runtime (CLR) zadejte informace, například `ContractDescription` instance vytvořené pomocí `ContractDescription.GetContract` metoda nebo vytvořen jako součást `ServiceDescription` pro `ServiceHost` instance. Nelze použít `WsdlExporter` pro export metadat z `ContractDescription` instance naimportované z metadat služby nebo vytvořen bez informací o typu.  
  
## <a name="importing-metadata"></a>Import metadat  
  
### <a name="importing-wsdl-documents"></a>Import dokumenty WSDL  
 Při importu metadat služby ve službě WCF použijte implementace <xref:System.ServiceModel.Description.MetadataImporter> abstraktní třídy. <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Typ je provádění <xref:System.ServiceModel.Description.MetadataImporter> abstraktní třída součástí WCF. <xref:System.ServiceModel.Description.WsdlImporter> Typu WSDL metadat připojené zásadami spojeny v příkazu imports <xref:System.ServiceModel.Description.MetadataSet> objektu.  
  
 <xref:System.ServiceModel.Description.WsdlImporter> Typ umožňuje určit, jak importovat metadata. Můžete importovat všechny koncové body, všechny vazby, nebo všechny kontrakty. Můžete importovat všechny koncové body přidružené k určité službě WSDL, vazby nebo typ portu. Můžete také importovat koncový bod pro konkrétní port WSDL, vazby pro konkrétní Vazba WSDL nebo smlouvy pro konkrétní typ portu WSDL.  
  
 <xref:System.ServiceModel.Description.WsdlImporter> Taky zpřístupňuje <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> vlastnost, která vám umožní určit sadu smluv, které nemusí být importován. <xref:System.ServiceModel.Description.WsdlImporter> Používá smlouvy v <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> vlastnost neimportujete kontrakt se stejným názvem kvalifikovaný z metadat.  
  
### <a name="importing-policies"></a>Import zásady  
 <xref:System.ServiceModel.Description.WsdlImporter> Typ shromažďuje výrazy zásad, který je připojen ke zprávě, operace, a zásady koncového bodu Predmety a použije je <xref:System.ServiceModel.Description.IPolicyImportExtension> implementace v <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> kolekce pro import výrazy zásad.  
  
 Logika importu zásad automaticky zpracovává zásady odkazy na výrazy zásad ve stejném dokumentu WSDL a přiřazen `wsu:Id` nebo `xml:id` atribut. Logika zásad import chrání aplikace proti zásad cyklické odkazy omezením velikosti výraz zásad do 4096 uzlů, kde uzel je jedním z následujících elementů: `wsp:Policy`, `wsp:All`, `wsp:ExactlyOne`, `wsp:policyReference`.  
  
 Logika zásad import také automaticky normalizuje výrazy zásad. Vnořené výrazy zásad a `wsp:Optional` atribut není normalizovaná. Velikost normalizace zpracování dokončení je omezená na 4096 kroků, kdy každý krok provede kontrolní výraz zásad, nebo podřízený prvek `wsp:ExactlyOne` elementu.  
  
 <xref:System.ServiceModel.Description.WsdlImporter> Typ pokusí až 32 kombinací alternativy zásad, které jsou připojené k jiné zásady předměty WSDL. Pokud žádná kombinace importuje čistě, první kombinace slouží k vytvoření částečné vlastní vazby.  
  
## <a name="error-handling"></a>Zpracování chyb  
 Jak <xref:System.ServiceModel.Description.MetadataExporter> a <xref:System.ServiceModel.Description.MetadataImporter> vystavit typy `Errors` vlastnosti, které obsahují kolekci chybové zprávy a upozornění došlo k během procesu exportu a importu v uvedeném pořadí, který může být použit při implementaci nástrojů.  
  
 <xref:System.ServiceModel.Description.WsdlImporter> Typ obvykle vyvolá výjimku, výjimka zachycena během procesu importu a přidá odpovídající chybu k jeho `Errors` vlastnost. <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>, <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A>, A <xref:System.ServiceModel.Description.WsdlImporter.ImportEndpoints%2A> metody, ale nevyvolají výjimku těchto výjimek, musíte zkontrolovat, `Errors` a určí, pokud došlo k nějaké problémy při volání těchto metod.  
  
 <xref:System.ServiceModel.Description.WsdlExporter> Typ znovu vyvolá všechny výjimky zachycené během procesu exportu. Tyto výjimky nejsou zaznamenat jako chyby v `Errors` vlastnost. Jakmile <xref:System.ServiceModel.Description.WsdlExporter> vyvolá výjimku, je v chybovém stavu a nejde použít znovu. <xref:System.ServiceModel.Description.WsdlExporter> Přidá upozornění na jeho `Errors` při operaci nejde exportovat, protože používá akce zástupný znak a když se vyskytují duplicitní vazbu názvy.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Import metadat do koncových bodů služby](../../../../docs/framework/wcf/feature-details/how-to-import-metadata-into-service-endpoints.md)  
 Popisuje, jak importovat metadata stažený do popisu objektů.  
  
 [Postupy: Export metadat z koncových bodů služby](../../../../docs/framework/wcf/feature-details/how-to-export-metadata-from-service-endpoints.md)  
 Popisuje, jak exportovat objekty popis do metadat.  
  
 [ServiceDescription a referenční informace pro WSDL](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md)  
 Popisuje mapování mezi objekty, popis a WSDL.  
  
 [Postupy: Použití Svcutil.exe pro Export metadat z kompilovaného kódu služby](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)  
 Popisuje použití nástroje Svcutil.exe pro export metadat pro služby, kontrakty a datové typy v kompilovaných sestavení.  
  
 [Schéma kontraktů dat – referenční informace](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)  
 Popisuje podmnožinu z schématu XML (XSD) používá <xref:System.Runtime.Serialization.DataContractSerializer> k popisu common language runtime (CLR) typy pro serializaci kódu XML.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ServiceModel.Description.WsdlExporter>  
  
 <xref:System.ServiceModel.Description.WsdlImporter>  
  
## <a name="see-also"></a>Viz také:

- [Export vlastních metadat pro rozšíření WCF](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)
- [Import vlastních metadat pro rozšíření WCF](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)
