---
title: Import vlastních metadat pro rozšíření WCF
ms.date: 03/30/2017
ms.assetid: 78beb28f-408a-4c75-9c3c-caefe9595b1a
ms.openlocfilehash: f6f858cbe86bd2965decf42be5daa7b3f7d3c8c2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796926"
---
# <a name="importing-custom-metadata-for-a-wcf-extension"></a>Import vlastních metadat pro rozšíření WCF
V Windows Communication Foundation (WCF) import metadat je proces generování abstraktní reprezentace služby nebo jejích částí z metadat. Služba WCF může například importovat <xref:System.ServiceModel.Description.ServiceEndpoint> instance, <xref:System.ServiceModel.Channels.Binding> instance nebo <xref:System.ServiceModel.Description.ContractDescription> instance z dokumentu WSDL pro službu. Chcete-li importovat metadata služby ve službě WCF, použijte implementaci <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> abstraktní třídy. Typy, které jsou odvozeny z <xref:System.ServiceModel.Description.MetadataImporter> třídy, implementují podporu pro Import formátů metadat, které využívají logiku importu WS-Policy ve službě WCF.  
  
 Vlastní metadata se skládají z elementů XML, které nemohou importovat dovozci metadat do systému. Obvykle to zahrnuje vlastní rozšíření WSDL a kontrolní výrazy vlastních zásad.  
  
 Tato část popisuje, jak importovat vlastní rozšíření WSDL a kontrolní výrazy zásad. Nezaměřuje se na samotný proces importu. Další informace o tom, jak používat typy, které exportují a importují metadata bez ohledu na to, jestli jsou metadata vlastní nebo podporuje systém, najdete v tématu [Export a import metadat](../feature-details/exporting-and-importing-metadata.md).  
  
## <a name="overview"></a>Přehled  
 Typ je implementace <xref:System.ServiceModel.Description.MetadataImporter> abstraktní třídy, která je součástí WCF. <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Typ Importuje metadata WSDL s připojenými zásadami, které jsou <xref:System.ServiceModel.Description.MetadataSet?displayProperty=nameWithType> v objektu seskupeny. <xref:System.ServiceModel.Description.WsdlImporter> Kontrolní výrazy zásad a rozšíření WSDL, které výchozí nástroje pro import nerozpoznají, jsou předávány všem registrovaným vlastním zásadám a dovozcům WSDL pro import. K podpoře uživatelsky definovaných prvků vazby nebo k úpravám importované smlouvy jsou obvykle implementovány nástroje pro import.  
  
 Tato část popisuje:  
  
1. Jak implementovat a používat <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> rozhraní, které zpřístupňuje data WSDL vlastním dovozcům před generováním popisů a generování kódu. Toto rozhraní můžete použít k prohlédnutí nebo úpravě typů popisu a kompilaci kódu prováděného pomocí dané sady metadat.  
  
2. Jak implementovat a používat <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> rozhraní, které zveřejňuje kontrolní výrazy zásad pro dovozce před generováním objektů popisu. Toto rozhraní můžete použít k prohlédnutí nebo úpravě vazby nebo kontraktu na základě stažených zásad.  
  
 Další informace o exportu vlastních kontrolních výrazů WSDL a zásad najdete v tématu [Export vlastních metadat pro rozšíření WCF](exporting-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="importing-custom-wsdl-extensions"></a>Import vlastních rozšíření WSDL  
 Chcete-li přidat podporu pro import rozšíření WSDL, <xref:System.ServiceModel.Description.IWsdlImportExtension> implementujte rozhraní a pak přidejte vaši implementaci <xref:System.ServiceModel.Description.WsdlImporter.WsdlImportExtensions%2A> do vlastnosti. Může také načítat implementace <xref:System.ServiceModel.Description.IWsdlImportExtension> rozhraní registrovaného v konfiguračním souboru aplikace. <xref:System.ServiceModel.Description.WsdlImporter> Počítejte s tím, že ve výchozím nastavení jsou registrovány počty dovozců WSDL a pořadí registrovaných dovozců WSDL je významné.  
  
 Když je vlastní Import WSDL načten a používán nástrojem <xref:System.ServiceModel.Description.WsdlImporter>, <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%2A> nejprve je volána metoda, aby bylo možné upravit metadata před procesem importu. Dál se naimportují smlouvy, po kterých <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%2A> se zavolá metoda, která umožní změnu kontraktů importovaných z metadat. Nakonec je volána metoda, která povoluje úpravu importovaných koncových bodů. <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%2A>  
  
 Další informace najdete v tématu [jak: Importujte vlastní WSDL](how-to-import-custom-wsdl.md).  
  
### <a name="importing-custom-policy-assertions"></a>Import kontrolních výrazů vlastních zásad  
 Typ a nástroj pro dokládání [metadat (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) automaticky zpracovávají zpracování nejrůznějších typů kontrolního výrazu ve výrazech zásad připojených k dokumentům WSDL. <xref:System.ServiceModel.Description.WsdlImporter> Tyto nástroje shromažďují, normalizují a sloučí výrazy zásad připojené k vazbám WSDL a portům WSDL.  
  
 Chcete-li přidat podporu pro import kontrolních výrazů vlastních zásad, <xref:System.ServiceModel.Description.IPolicyImportExtension> implementujte rozhraní a pak přidejte vaši implementaci <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> do vlastnosti. Může také načítat implementace <xref:System.ServiceModel.Description.IPolicyImportExtension> rozhraní registrovaného v konfiguračním souboru aplikace. <xref:System.ServiceModel.Description.MetadataImporter> Všimněte si, že ve výchozím nastavení jsou zaregistrované některé dovozců zásad a pořadí registrovaných dovozců zásad je důležité.  
  
 Systém metadat opakovaně volá <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> metodu pro všechna zaregistrovaná rozšíření importu zásad pro každou kombinaci alternativ zásad připojená k předmětům zprávy, operace a zásad koncového bodu. Při importu portu WSDL jsou před voláním do rozšíření pro import zásad sloučeny zásady připojené k portu a odpovídající vazbě WSDL. Alternativy zásad jsou zpřístupněny prostřednictvím <xref:System.ServiceModel.Description.PolicyConversionContext> objektů as. <xref:System.ServiceModel.Description.PolicyAssertionCollection> Každé <xref:System.ServiceModel.Description.PolicyAssertionCollection> je kolekce kontrolních výrazů, které <xref:System.Xml.XmlElement> představují objekty.  
  
 <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A> Vlastnosti a <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A> na<xref:System.ServiceModel.Description.PolicyConversionContext> objektu zpřístupňují objekty a<xref:System.ServiceModel.Channels.BindingElement>, které byly naimportovány z WSDL. <xref:System.ServiceModel.Description.ContractDescription> Naimportují kontrolní výrazy zásad procesu – vyhledají instance konkrétního typu kontrolního výrazu zásad, které provádějí odpovídající <xref:System.ServiceModel.Description.ContractDescription> změny <xref:System.ServiceModel.Channels.BindingElement> objektů nebo a pak odeberou kontrolní výrazy zásad z odpovídajících <xref:System.ServiceModel.Description.PolicyAssertionCollection> instance.  
  
 Výrazy `wsp:Optional` atributů a vnořené zásady nejsou normalizovány, takže rozšíření pro import zásad musí tyto konstrukce zásad zpracovat. Kromě toho můžou být rozšíření pro import zásad volána víckrát se stejnými <xref:System.ServiceModel.Description.ContractDescription> objekty <xref:System.ServiceModel.Channels.BindingElement> a, takže rozšíření pro import zásad by měla být pro toto chování robustní.  
  
> [!IMPORTANT]
> Import může předat neplatná nebo nesprávná metadata. Ujistěte se, že vlastní dovozci jsou robustní pro všechny formy XML.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Importovat vlastní WSDL](how-to-import-custom-wsdl.md)
- [Postupy: Import kontrolních výrazů vlastních zásad](how-to-import-custom-policy-assertions.md)
- [Postupy: Zapsat rozšíření pro ServiceContractGenerator](how-to-write-an-extension-for-the-servicecontractgenerator.md)
