---
title: Import vlastních metadat pro rozšíření WCF
ms.date: 03/30/2017
ms.assetid: 78beb28f-408a-4c75-9c3c-caefe9595b1a
ms.openlocfilehash: b99d7fbab08c5edabe3a08baf89dd267c3f9fa25
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562099"
---
# <a name="importing-custom-metadata-for-a-wcf-extension"></a>Import vlastních metadat pro rozšíření WCF
Ve Windows Communication Foundation (WCF), import metadat je proces generování abstraktní reprezentace služby nebo jeho součásti z jeho metadata. Například můžete importovat WCF <xref:System.ServiceModel.Description.ServiceEndpoint> instancí, <xref:System.ServiceModel.Channels.Binding> instance nebo <xref:System.ServiceModel.Description.ContractDescription> instancí ze souboru WSDL dokumentů pro službu. Při importu metadat služby ve službě WCF použijte implementace <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> abstraktní třídy. Typy, které jsou odvozeny z <xref:System.ServiceModel.Description.MetadataImporter> třída implementovat podporu pro import formáty metadat, které budou využívat WS-Policy importovat logiky ve službě WCF.  
  
 Vlastní metadata se skládá z elementů XML, které importers poskytované systémem metadata se nedá importovat. Obvykle obsahuje vlastní rozšíření WSDL a kontrolních výrazů vlastních zásad.  
  
 Tato část popisuje, jak importovat vlastní rozšíření WSDL a kontrolní výrazy zásad. Nezaměřuje se na samotný proces importu. Další informace o tom, jak používat typy, které export a import metadat bez ohledu na to, jestli jsou metadata vlastní nebo systém nepodporuje najdete v tématu [pro export a import metadat](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
## <a name="overview"></a>Přehled  
 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Typ je provádění <xref:System.ServiceModel.Description.MetadataImporter> abstraktní třída součástí WCF. <xref:System.ServiceModel.Description.WsdlImporter> Typ Importuje metadata WSDL s připojenými zásady, které jsou spojeny v <xref:System.ServiceModel.Description.MetadataSet?displayProperty=nameWithType> objektu. Kontrolní výrazy zásad a rozšíření WSDL, která nebyla rozpoznána importers výchozí jsou předány žádné registrované vlastních zásad a WSDL importers pro import. Obvykle importers jsou implementovány pro podporu elementů uživatelem definované vazby nebo pro úpravu importované kontraktu.  
  
 Tato část popisuje:  
  
1.  Jak implementovat a používat <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> rozhraní, které zveřejňuje data WSDL na vlastní importers před generováním popisy a generování kódu. Toto rozhraní můžete prozkoumat nebo upravit popis typů a kompilace kódu provádí pomocí dané sadě metadat.  
  
2.  Jak implementovat a používat <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> rozhraní, které zveřejňuje kontrolní výrazy zásad na importers před generování popis objekty. Toto rozhraní můžete zkontrolovat nebo změnit vazby nebo smlouvy, na základě zásad stažené.  
  
 Další informace o export vlastního WSDL a kontrolní výrazy zásad najdete v tématu [export vlastních metadat pro rozšíření WCF](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="importing-custom-wsdl-extensions"></a>Import vlastního WSDL rozšíření  
 Chcete-li přidat podporu pro import WSDL rozšíření, implementovat <xref:System.ServiceModel.Description.IWsdlImportExtension> rozhraní a pak přidejte implementace <xref:System.ServiceModel.Description.WsdlImporter.WsdlImportExtensions%2A> vlastnost. <xref:System.ServiceModel.Description.WsdlImporter> Můžete také načíst implementace <xref:System.ServiceModel.Description.IWsdlImportExtension> rozhraní registrovaný v konfiguračním souboru aplikace. Všimněte si, že ve výchozím nastavení jsou registrované číslo WSDL importers a je důležité pořadí registrované importers WSDL.  
  
 Když je import vlastního WSDL načíst a použít <xref:System.ServiceModel.Description.WsdlImporter>nejdřív <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%2A> metoda je volána umožňující změnu metadat před proces importu. V dalším kroku smlouvách importují po jejímž uplynutí <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%2A> metoda je volána k povolení úprav kontrakty naimportované z metadat. Nakonec <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%2A> metoda je volána umožňující změnu importované koncových bodů.  
  
 Další informace najdete v tématu [jak: Import vlastního WSDL](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md).  
  
### <a name="importing-custom-policy-assertions"></a>Import kontrolních výrazů vlastních zásad  
 <xref:System.ServiceModel.Description.WsdlImporter> Typ a [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) automaticky zpracovává zpracování různých typů kontrolní výraz zásad v výrazy zásad, které jsou připojené k dokumenty WSDL. Tyto nástroje shromažďovat normalizovat a sloučit výrazy zásad, které jsou připojené ke vazby WSDL a porty WSDL.  
  
 Chcete-li přidat podporu pro import kontrolních výrazů vlastních zásad, implementovat <xref:System.ServiceModel.Description.IPolicyImportExtension> rozhraní a pak přidejte implementace <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> vlastnost. <xref:System.ServiceModel.Description.MetadataImporter> Můžete také načíst implementace <xref:System.ServiceModel.Description.IPolicyImportExtension> rozhraní registrovaný v konfiguračním souboru aplikace. Všimněte si, že ve výchozím nastavení jsou registrované číslo pro import a je důležité pořadí registrovaný pro import.  
  
 Metadata systém opakovaně volá <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> metodu na všech registrovaných zásad import rozšíření pro každou kombinaci alternativy zásad, které jsou připojené k zásad témata zpráv, operace a koncového bodu. Při importu WSDL port, zásady připojené k portu a odpovídající vazby WSDL jsou sloučeny před voláním do rozšíření importu zásady. Alternativy zásad jsou k dispozici prostřednictvím <xref:System.ServiceModel.Description.PolicyConversionContext> jako <xref:System.ServiceModel.Description.PolicyAssertionCollection> objekty. Každý <xref:System.ServiceModel.Description.PolicyAssertionCollection> je kolekce kontrolní výrazy zásad reprezentována <xref:System.Xml.XmlElement> objekty.  
  
 <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A> a <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A> vlastnosti <xref:System.ServiceModel.Description.PolicyConversionContext> objektu vystavení <xref:System.ServiceModel.Description.ContractDescription> a <xref:System.ServiceModel.Channels.BindingElement> objekty, jež byla importována ze schématu WSDL. Rozšíření importu zásady zpracování kontrolních výrazů zásad hledáním instancí typu kontrolní výraz konkrétní zásady, provádět odpovídající změny do <xref:System.ServiceModel.Description.ContractDescription> nebo <xref:System.ServiceModel.Channels.BindingElement> objekty a poté odstraněním z odpovídající kontrolnívýrazyzásad<xref:System.ServiceModel.Description.PolicyAssertionCollection> instance.  
  
 `wsp:Optional` Atribut a výrazy vnořené zásad nejsou normalized, tak rozšíření importu zásady musí zpracovat tyto zásady konstrukce. Také rozšíření importu zásad může být volána více než jednou se stejným <xref:System.ServiceModel.Description.ContractDescription> a <xref:System.ServiceModel.Channels.BindingElement> objekty, rozšíření importu zásady by tak měly být robustní na toto chování.  
  
> [!IMPORTANT]
>  Neplatná nebo nesprávná data může být předán tabulkách. Zajistěte, aby byly vlastní importers robustní pro všechny formy XML.  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Import vlastního WSDL](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
- [Postupy: Import kontrolních výrazů vlastních zásad](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)
- [Postupy: Vytvoření rozšíření pro třídu ServiceContractGenerator](../../../../docs/framework/wcf/extending/how-to-write-an-extension-for-the-servicecontractgenerator.md)
