---
title: Export a import metadat
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], exporting and importing
ms.assetid: 614a75bb-e0b0-4c95-b6d8-02cb5e5ddb38
ms.openlocfilehash: f07a1a10529aa1615bb00a0f3faeca9cb249aa64
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595528"
---
# <a name="exporting-and-importing-metadata"></a>Export a import metadat
V Windows Communication Foundation (WCF) je export metadat proces popsání koncových bodů služby a jejich zabalení do paralelní, standardizované reprezentace, kterou klienti můžou použít k pochopení toho, jak službu používat. Import metadat služby je proces generování <xref:System.ServiceModel.Description.ServiceEndpoint> instancí nebo částí z metadat služby.  
  
## <a name="exporting-metadata"></a>Exportují se metadata  
 Chcete-li exportovat metadata z <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> instancí, použijte implementaci <xref:System.ServiceModel.Description.MetadataExporter> abstraktní třídy. <xref:System.ServiceModel.Description.WsdlExporter>Typ je implementace <xref:System.ServiceModel.Description.MetadataExporter> abstraktní třídy, která je součástí WCF.  
  
 <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType>Typ vygeneruje metadata jazyka WSDL (Web Services Description Language) s připojenými výrazy zásad, které jsou zapouzdřeny v <xref:System.ServiceModel.Description.MetadataSet> instanci. Můžete použít <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> instanci k opakovanému exportu metadat pro <xref:System.ServiceModel.Description.ContractDescription> objekty a <xref:System.ServiceModel.Description.ServiceEndpoint> objekty. Můžete také exportovat kolekci <xref:System.ServiceModel.Description.ServiceEndpoint> objektů a přidružit je k určitému názvu služby.  
  
> [!NOTE]
> Můžete použít pouze `WsdlExporter` k exportu metadat z `ContractDescription` instancí, které obsahují informace o typu modulu CLR (Common Language Runtime), jako je například `ContractDescription` instance vytvořená pomocí `ContractDescription.GetContract` metody nebo vytvořená jako součást `ServiceDescription` `ServiceHost` instance. Pomocí nástroje nelze `WsdlExporter` exportovat metadata z `ContractDescription` instancí importovaných z metadat služby nebo vytvořená bez informací o typu.  
  
## <a name="importing-metadata"></a>Import metadat  
  
### <a name="importing-wsdl-documents"></a>Import dokumentů WSDL  
 Chcete-li importovat metadata služby ve službě WCF, použijte implementaci <xref:System.ServiceModel.Description.MetadataImporter> abstraktní třídy. <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>Typ je implementace <xref:System.ServiceModel.Description.MetadataImporter> abstraktní třídy, která je součástí WCF. <xref:System.ServiceModel.Description.WsdlImporter>Typ Importuje metadata WSDL s připojenými zásadami, které jsou v <xref:System.ServiceModel.Description.MetadataSet> objektu seskupené.  
  
 <xref:System.ServiceModel.Description.WsdlImporter>Typ poskytuje kontrolu nad importem metadat. Můžete importovat všechny koncové body, všechny vazby nebo všechny kontrakty. Můžete importovat všechny koncové body přidružené ke konkrétní službě WSDL, vazbě nebo typu portu. Koncový bod můžete také naimportovat pro určitý port WSDL, vazbu pro konkrétní vazbu WSDL nebo kontrakt pro určitý typ portu WSDL.  
  
 <xref:System.ServiceModel.Description.WsdlImporter>Také zpřístupňuje <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> vlastnost, která umožňuje zadat sadu kontraktů, které není nutné naimportovat. <xref:System.ServiceModel.Description.WsdlImporter>Místo toho používá kontrakty ve <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> vlastnosti namísto importu kontraktu se stejným kvalifikovaným názvem z metadat.  
  
### <a name="importing-policies"></a>Importování zásad  
 <xref:System.ServiceModel.Description.WsdlImporter>Typ shromažďuje výrazy zásad připojené k předmětům zprávy, operace a zásad koncového bodu a pak používá <xref:System.ServiceModel.Description.IPolicyImportExtension> implementace v <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> kolekci k importu výrazů zásad.  
  
 Logika importu zásad automaticky zpracovává odkazy zásad na výrazy zásad ve stejném dokumentu WSDL a jsou identifikovány `wsu:Id` `xml:id` atributem nebo. Logika importu zásad chrání aplikace proti cyklickým odkazům na zásady tím, že omezuje velikost výrazu zásady na 4096 uzlů, kde uzel je jedním z následujících prvků: `wsp:Policy` , `wsp:All` , `wsp:ExactlyOne` , `wsp:policyReference` .  
  
 Logika importu zásad také automaticky normalizuje výrazy zásad. Vnořené výrazy zásad a `wsp:Optional` atribut nejsou normalizovány. Množství provedení normalizace je omezeno na 4096 kroků, kde každý krok vychází z kontrolního výrazu zásady nebo podřízeného prvku `wsp:ExactlyOne` elementu.  
  
 <xref:System.ServiceModel.Description.WsdlImporter>Typ se pokusí o až 32 kombinace alternativ zásad připojených k různým předmětům zásad WSDL. Pokud nejsou žádné kombinace importovány čistě, je první kombinace použita k vytvoření částečné vlastní vazby.  
  
## <a name="error-handling"></a>Zpracování chyb  
 Oba <xref:System.ServiceModel.Description.MetadataExporter> <xref:System.ServiceModel.Description.MetadataImporter> typy a zpřístupňují `Errors` vlastnost, která může obsahovat kolekci chybových a varovných zpráv, které byly zjištěny během procesu exportu a importu, které lze použít při implementaci nástrojů.  
  
 <xref:System.ServiceModel.Description.WsdlImporter>Typ obecně vyvolá výjimku pro výjimku zachycenou během procesu importu a ke své vlastnosti přidá odpovídající chybu `Errors` . <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>Metody, <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A> , <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> a <xref:System.ServiceModel.Description.WsdlImporter.ImportEndpoints%2A> , ale tyto výjimky nevyvolávají, takže musíte ověřit vlastnost, `Errors` abyste zjistili, jestli při volání těchto metod došlo k nějakým potížím.  
  
 <xref:System.ServiceModel.Description.WsdlExporter>Typ znovu vyvolá všechny výjimky zachycené během procesu exportu. Tyto výjimky nejsou zachyceny jako chyby ve `Errors` Vlastnosti. Jakmile <xref:System.ServiceModel.Description.WsdlExporter> vyvolá výjimku, je v chybovém stavu a nelze ji znovu použít. <xref:System.ServiceModel.Description.WsdlExporter>Přidá upozornění na `Errors` vlastnost, pokud operaci nelze exportovat, protože používá zástupné akce a při zjištění duplicitních názvů vazeb.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Import metadat do koncových bodů služby](how-to-import-metadata-into-service-endpoints.md)  
 Popisuje, jak importovat stažená metadata do objektů Description.  
  
 [Postupy: Export metadat z koncových bodů služby](how-to-export-metadata-from-service-endpoints.md)  
 Popisuje, jak exportovat objekty popisu do metadat.  
  
 [ServiceDescription a referenční informace pro WSDL](servicedescription-and-wsdl-reference.md)  
 Popisuje mapování mezi objekty Description a WSDL.  
  
 [Postupy: Použití nástroje Svcutil.exe pro export metadat z kompilovaného kódu služby](how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)  
 Popisuje použití nástroje Svcutil. exe pro export metadat pro služby, kontrakty a datové typy v kompilovaných sestaveních.  
  
 [Schéma kontraktů dat – referenční informace](data-contract-schema-reference.md)  
 Popisuje podmnožinu schématu XML (XSD) používaného <xref:System.Runtime.Serialization.DataContractSerializer> pro popis typů modulu CLR (Common Language run-time) pro serializaci XML.  
  
## <a name="reference"></a>Referenční informace  
 <xref:System.ServiceModel.Description.WsdlExporter>  
  
 <xref:System.ServiceModel.Description.WsdlImporter>  
  
## <a name="see-also"></a>Viz také

- [Export vlastních metadat pro rozšíření WCF](../extending/exporting-custom-metadata-for-a-wcf-extension.md)
- [Import vlastních metadat pro rozšíření WCF](../extending/importing-custom-metadata-for-a-wcf-extension.md)
