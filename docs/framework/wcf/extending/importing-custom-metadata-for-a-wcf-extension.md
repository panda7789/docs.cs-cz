---
title: Import vlastních metadat pro rozšíření WCF
ms.date: 03/30/2017
ms.assetid: 78beb28f-408a-4c75-9c3c-caefe9595b1a
ms.openlocfilehash: bb7124cbce3fa38d00446b6568c85fc3136ee180
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="importing-custom-metadata-for-a-wcf-extension"></a>Import vlastních metadat pro rozšíření WCF
Ve Windows Communication Foundation (WCF), import metadat je proces generování abstraktní reprezentace služby nebo jeho součásti z jeho metadata. Například [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] můžete importovat <xref:System.ServiceModel.Description.ServiceEndpoint> instancí <xref:System.ServiceModel.Channels.Binding> instance nebo <xref:System.ServiceModel.Description.ContractDescription> instancí z WSDL dokumentů pro službu. Chcete-li importovat metadata služby v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], použít implementaci <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> abstraktní třídy. Typy, které jsou odvozeny od <xref:System.ServiceModel.Description.MetadataImporter> třída implementovat podporu pro import formáty metadat, které využít WS-Policy importovat logiku [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Vlastní metadata se skládá z elementů XML, které společnost importers poskytované systémem metadata nelze importovat. Obvykle obsahuje vlastní rozšíření WSDL a kontrolních výrazů vlastních zásad.  
  
 Tato část popisuje, jak importovat vlastní rozšíření WSDL a výrazy zásad. Nejsou zaměřeny na samotný proces import. Další informace o tom, jak používat typy, které exportovat a importovat metadata bez ohledu na to, zda se jedná o vlastní nebo systém nepodporuje metadata najdete v tématu [export a import metadat](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
## <a name="overview"></a>Přehled  
 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Typ je implementace <xref:System.ServiceModel.Description.MetadataImporter> abstraktní třídy součástí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. <xref:System.ServiceModel.Description.WsdlImporter> Typ naimportuje metadata WSDL s připojené zásady, které jsou seskupeny v <xref:System.ServiceModel.Description.MetadataSet?displayProperty=nameWithType> objektu. Výrazy zásad a WSDL rozšíření, které nelze rozpoznat společnosti importers výchozí jsou předány všechny registrované vlastní zásady a Importers k účetnictví WSDL pro import. Obvykle se Importers k účetnictví implementují podporovat prvky uživatelem definované vazby nebo upravit importované kontrakt.  
  
 Tato část popisuje:  
  
1.  Tom, jak implementovat a použít <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> rozhraní, která zpřístupňuje WSDL data, která mají vlastní Importers k účetnictví před generování popisy a generování kódu. Toto rozhraní můžete zkontrolovat nebo upravit popis typy a provádí pomocí danou sadu metadata kompilace kódu.  
  
2.  Tom, jak implementovat a použít <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> rozhraní, která zpřístupňuje výrazy zásad na Importers k účetnictví před generování objektů popis. Toto rozhraní můžete použít k prozkoumání nebo změně vazby nebo kontrakt na základě stažené zásad.  
  
 Další informace o export vlastního WSDL a kontrolních výrazů zásad najdete v tématu [export vlastních metadat pro rozšíření WCF](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="importing-custom-wsdl-extensions"></a>Import rozšíření vlastního WSDL  
 Chcete-li přidat podporu pro import rozšíření schématu WSDL, implementujte <xref:System.ServiceModel.Description.IWsdlImportExtension> rozhraní a pak přidejte do vaší implementace <xref:System.ServiceModel.Description.WsdlImporter.WsdlImportExtensions%2A> vlastnost. <xref:System.ServiceModel.Description.WsdlImporter> Můžete také načíst implementace <xref:System.ServiceModel.Description.IWsdlImportExtension> rozhraní registrovaný v konfiguračním souboru aplikace. Upozorňujeme, že ve výchozím nastavení jsou registrované číslo Importers k účetnictví WSDL a je důležité pořadí registrované společnosti importers WSDL.  
  
 Když je vlastní – Importér WSDL načíst a použít <xref:System.ServiceModel.Description.WsdlImporter>, první <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%2A> metoda je volána umožňující změnu metadat před procesu importu. V dalším kroku smluv importují po jejímž uplynutí <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%2A> metoda je volána umožňující změnu smluv importovat z metadat. Nakonec <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%2A> metoda je volána umožňující změnu importované koncových bodů.  
  
 Další informace najdete v tématu [postupy: Import vlastní WSDL](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md).  
  
### <a name="importing-custom-policy-assertions"></a>Import kontrolních výrazů vlastních zásad  
 <xref:System.ServiceModel.Description.WsdlImporter> Typu a [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) zpracují automaticky zpracování celou řadu typů zásad assertion ve výrazech zásad, které jsou připojené k dokumentům WSDL. Tyto nástroje shromažďování, normalizaci a sloučení výrazy zásad, které jsou připojené k WSDL vazby a porty WSDL.  
  
 Chcete-li přidat podporu pro import kontrolních výrazů vlastních zásad, implementujte <xref:System.ServiceModel.Description.IPolicyImportExtension> rozhraní a pak přidejte do vaší implementace <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> vlastnost. <xref:System.ServiceModel.Description.MetadataImporter> Můžete také načíst implementace <xref:System.ServiceModel.Description.IPolicyImportExtension> rozhraní registrovaný v konfiguračním souboru aplikace. Upozorňujeme, že počet zásad Importers k účetnictví je registrován ve výchozím nastavení a je důležité pořadí společnosti importers registrované zásad.  
  
 Systém metadat opakovaně volá <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> metoda na všech registrovaných zásady importu rozšíření pro každou kombinaci alternativy zásady připojené k zásad témata zprávu, operace a koncový bod. Při importu WSDL port, zásady, které jsou připojené k portu a odpovídající vazby WSDL sloučení před voláním do rozšíření importu zásad. Alternativy zásad jsou dostupné prostřednictvím <xref:System.ServiceModel.Description.PolicyConversionContext> jako <xref:System.ServiceModel.Description.PolicyAssertionCollection> objekty. Každý <xref:System.ServiceModel.Description.PolicyAssertionCollection> je kolekce výrazy zásad reprezentována <xref:System.Xml.XmlElement> objekty.  
  
 <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A> a <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A> vlastnosti <xref:System.ServiceModel.Description.PolicyConversionContext> objektu zveřejněte <xref:System.ServiceModel.Description.ContractDescription> a <xref:System.ServiceModel.Channels.BindingElement> objekty, které byly naimportovány z schématu WSDL. Import rozšíření zásad zpracování kontrolních výrazů zásad hledání instance typu assertion konkrétní zásady, provedení odpovídající změny <xref:System.ServiceModel.Description.ContractDescription> nebo <xref:System.ServiceModel.Channels.BindingElement> objekty a výrazy zásad odebráním odpovídající <xref:System.ServiceModel.Description.PolicyAssertionCollection> instance.  
  
 `wsp:Optional` Atribut a vnořené zásad výrazy nejsou normalized, tak import rozšíření zásad musí zpracovávat tyto konstruktory zásad. Navíc import rozšíření zásad může volat vícekrát, se stejným <xref:System.ServiceModel.Description.ContractDescription> a <xref:System.ServiceModel.Channels.BindingElement> objekty, takže import rozšíření zásad by mělo být robustní toto chování.  
  
> [!IMPORTANT]
>  Neplatný nebo nesprávný metadata můžete předat program pro import. Zajistěte, aby vlastní Importers k účetnictví robustní všem formulářům XML.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Import vlastního WSDL](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)  
 [Postupy: Import kontrolních výrazů vlastních zásad](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)  
 [Postupy: Vytvoření rozšíření pro ServiceContractGenerator](../../../../docs/framework/wcf/extending/how-to-write-an-extension-for-the-servicecontractgenerator.md)
