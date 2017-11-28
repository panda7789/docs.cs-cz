---
title: Export a import metadat
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: metadata [WCF], exporting and importing
ms.assetid: 614a75bb-e0b0-4c95-b6d8-02cb5e5ddb38
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6231d6e4b6562aafbb5b6bd88b65b66f44469023
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="exporting-and-importing-metadata"></a>Export a import metadat
V [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], Export metadat je proces popisující koncové body služby a projekce je do znázornění paralelní, standardizované, který můžou klienti používat pochopit, jak používat službu. Import metadat služby je proces generování <xref:System.ServiceModel.Description.ServiceEndpoint> instance nebo části z metadat služby.  
  
## <a name="exporting-metadata"></a>Export metadat  
 Pro export metadat z <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> instance slouží provádění <xref:System.ServiceModel.Description.MetadataExporter> abstraktní třídy. <xref:System.ServiceModel.Description.WsdlExporter> Typ je implementace <xref:System.ServiceModel.Description.MetadataExporter> abstraktní třídy součástí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> Typ generuje metadata webové služby popis Language (WSDL) s výrazy připojené zásad zapouzdřené v <xref:System.ServiceModel.Description.MetadataSet> instance. Můžete použít <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> instance interaktivně vyexportujte metadata pro <xref:System.ServiceModel.Description.ContractDescription> objekty a <xref:System.ServiceModel.Description.ServiceEndpoint> objekty. Můžete také exportovat kolekce <xref:System.ServiceModel.Description.ServiceEndpoint> objekty a jejich přidružení s názvem konkrétní služby.  
  
> [!NOTE]
>  Lze použít pouze `WsdlExporter` pro export metadat z `ContractDescription` instancí, které obsahují modul common language runtime (CLR) zadejte informace, například `ContractDescription` instance vytvořené pomocí `ContractDescription.GetContract` metoda nebo vytvořené jako součást `ServiceDescription` pro `ServiceHost` instance. Nelze použít `WsdlExporter` pro export metadat z `ContractDescription` instance importovat z metadat služby nebo sestavený bez informací o typu.  
  
## <a name="importing-metadata"></a>Import metadat  
  
### <a name="importing-wsdl-documents"></a>Import dokumentů WSDL  
 Chcete-li importovat metadata služby v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], použít implementaci <xref:System.ServiceModel.Description.MetadataImporter> abstraktní třídy. <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Typ je implementace <xref:System.ServiceModel.Description.MetadataImporter> abstraktní třídy součástí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. <xref:System.ServiceModel.Description.WsdlImporter> Zadejte importy WSDL metadata připojené zásadám dodávat v <xref:System.ServiceModel.Description.MetadataSet> objektu.  
  
 <xref:System.ServiceModel.Description.WsdlImporter> Typ umožňuje určit, jak importovat metadata. Můžete importovat všechny koncové body, všechny vazby, nebo všechny smluv. Můžete importovat všechny koncové body přidružené k specifické WSDL služby, vazba nebo typ portu. Můžete také importovat koncový bod pro specifického portu WSDL, vazby pro konkrétní vazbu WSDL nebo kontrakt pro konkrétní typ portu WSDL.  
  
 <xref:System.ServiceModel.Description.WsdlImporter> Taky zpřístupňuje <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> vlastnost, která vám umožní určit sadu smlouvy, které není potřeba importovat. <xref:System.ServiceModel.Description.WsdlImporter> Používá kontrakty v <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> vlastnost místo import kontraktu se stejným názvem kvalifikovaný z metadat.  
  
### <a name="importing-policies"></a>Import zásady  
 <xref:System.ServiceModel.Description.WsdlImporter> Typ shromažďuje výrazy zásad připojeného ke zprávě, operace, a koncového bodu předměty a použije je <xref:System.ServiceModel.Description.IPolicyImportExtension> implementace v <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> kolekce k importu výrazy zásad.  
  
 Logika zásad import automaticky zpracovává zásady odkazy na výrazy zásad do jednoho dokumentu WSDL a je označena `wsu:Id` nebo `xml:id` atribut. Logika zásad import chrání aplikace pro zásady cyklické odkazy omezením velikosti výraz zásad do 4096 uzlů, které je jeden z následujících prvků uzel: `wsp:Policy`, `wsp:All`, `wsp:ExactlyOne`, `wsp:policyReference`.  
  
 Logika zásad import také automaticky normalizuje výrazy zásad. Vnořené výrazy zásad a `wsp:Optional` nejsou normalized atribut. Objem zpracování normalizaci se provádí je omezený na 4096 kroky, kde každý krok vypočítá výraz zásad nebo podřízený prvek `wsp:ExactlyOne` elementu.  
  
 <xref:System.ServiceModel.Description.WsdlImporter> Typ pokusí až 32 kombinace alternativy zásady připojené k jiné zásady témata WSDL. Pokud žádné kombinace importuje řádně, první kombinace slouží k vytvoření částečné vlastní vazby.  
  
## <a name="error-handling"></a>Zpracování chyb  
 Jak <xref:System.ServiceModel.Description.MetadataExporter> a <xref:System.ServiceModel.Description.MetadataImporter> typy vystavit `Errors` vlastnost obsahující kolekci chybové zprávy a upozornění došlo během procesů exportu a importu v uvedeném pořadí, které lze použít při implementaci nástroje.  
  
 <xref:System.ServiceModel.Description.WsdlImporter> Typ obecně vyvolá výjimku, výjimka zachycena během procesu importu a přidá odpovídající chyba k jeho `Errors` vlastnost. <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>, <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A>, A <xref:System.ServiceModel.Description.WsdlImporter.ImportEndpoints%2A> metody, ale nevyvolá výjimku tyto výjimky, takže je nutné zkontrolovat, `Errors` vlastnosti k určení, pokud všechny problémy došlo k chybě při volání těchto metod.  
  
 <xref:System.ServiceModel.Description.WsdlExporter> Typ znovu vyvolá všechny výjimky zachycené během procesu exportu. Tyto výjimky nejsou zaznamená jako chyby v `Errors` vlastnost. Jednou <xref:System.ServiceModel.Description.WsdlExporter> vyvolá výjimku, je v chybovém stavu a nelze znovu použít. <xref:System.ServiceModel.Description.WsdlExporter> Přidání upozornění k jeho `Errors` při operaci nelze exportovat, protože používá zástupný znak akcí a když se vyskytují duplicitní vazbu názvy.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Import metadat do koncových bodů služby](../../../../docs/framework/wcf/feature-details/how-to-import-metadata-into-service-endpoints.md)  
 Popisuje, jak naimportujte stažené metadata do popis objektů.  
  
 [Postupy: Export metadat z koncových bodů služby](../../../../docs/framework/wcf/feature-details/how-to-export-metadata-from-service-endpoints.md)  
 Popisuje, jak exportovat objekty popis do metadat.  
  
 [Referenční dokumentace schématu WSDL a ServiceDescription](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md)  
 Popisuje mapování mezi objekty popis a WSDL.  
  
 [Postupy: použití Svcutil.exe pro Export metadat z kompilovaného kódu služby](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)  
 Popisuje použití nástroje Svcutil.exe pro export metadat pro služby, smlouvy a datových typů v sestaveních kompilované.  
  
 [Přehled schématu kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)  
 Popisuje některé z schéma XML (XSD) používané <xref:System.Runtime.Serialization.DataContractSerializer> k popisu common language runtime (CLR) typy pro serializaci XML.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ServiceModel.Description.WsdlExporter>  
  
 <xref:System.ServiceModel.Description.WsdlImporter>  
  
## <a name="see-also"></a>Viz také  
 [Export vlastních metadat pro rozšíření WCF](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)  
 [Import vlastních metadat pro rozšíření WCF](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)
