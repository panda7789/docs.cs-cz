---
title: XML a serializace protokolu SOAP
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
ms.openlocfilehash: 4ca812c03949cb6a2cb903ae041e54311e9486bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591515"
---
# <a name="xml-and-soap-serialization"></a>XML a serializace protokolu SOAP
Převede serializace XML (serializuje) veřejné polí a vlastností objektu, nebo parametry a návratovými hodnotami metod do datový proud XML, který odpovídá určitého dokumentu definition language (XSD) schématu XML. Serializace XML výsledkem silného typu třídy s veřejné vlastnosti a pole, které jsou převedeny na sériového formátu (v tomto případě XML) pro uložení nebo přenos.  
  
 Protože kód XML je otevřený standard, může být zpracována datový proud XML ve všech aplikacích, podle potřeby, bez ohledu na platformu. Můžete například webové služby XML vytvořené pomocí technologie ASP.NET použití <xref:System.Xml.Serialization.XmlSerializer> třídy za účelem vytvoření datové proudy XML, který vkládá data mezi aplikací webové služby XML v rámci Internetu nebo v těchto sítích. Deserializace naopak přebírá takové datový proud XML a rekonstruuje objektu.  
  
 Serializace XML lze také použít k serializaci objektů do datových proudů XML, které odpovídají specifikaci protokolu SOAP. Protokol SOAP je protokol založený na formát XML, který je určen speciálně k přenosu volání procedur pomocí jazyka XML.  
  
 K serializaci nebo deserializaci objektů, použijte <xref:System.Xml.Serialization.XmlSerializer> třídy. Chcete-li vytvořit třídy k serializaci, použijte nástroj definici schématu XML.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Představení serializace XML](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 Poskytuje obecné definici serializaci, zejména serializace XML.  
  
 [Postupy: Serializace objektu](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 Obsahuje podrobné pokyny pro serializaci objektu.  
  
 [Postupy: Deserializace objektu](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 Obsahuje podrobné pokyny pro deserializaci objektu.  
  
 [Příklady serializace XML](../../../docs/standard/serialization/examples-of-xml-serialization.md)  
 Obsahuje příklady, které ukazují základy serializace XML.  
  
 [Nástroj pro definici schématu XML a serializace XML](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)  
 Popisuje, jak používat nástroj definici schématu XML k vytvoření třídy, které splňovat konkrétní jazyk (XSD) schématu definice schématu XML nebo ke generování schématu XML z soubor DLL.  
  
 [Řízení serializace XML pomocí atributů](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 Popisuje, jak řídit serializace pomocí atributů.  
  
 [Seznam atributů řídících serializaci XML](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md)  
 Seznam atributů, které se používají k řízení serializace XML.  
  
 [Postupy: Zadání alternativního názvu elementu pro XML stream](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
 Uvede případě rozšířeného scénáře ukázkami, jak ke generování více datové proudy XML přepsáním serializace.  
  
 [Postupy: Řízení serializace odvozených tříd](../../../docs/standard/serialization/how-to-control-serialization-of-derived-classes.md)  
 Obsahuje příklad toho, jak řídit serializace odvozené třídy.  
  
 [Postupy: Kvalifikace názvů elementů a atributů XML](../../../docs/standard/serialization/how-to-qualify-xml-element-and-xml-attribute-names.md)  
 Popisuje, jak lze definovat a určit tak, jak v XML, které se používají obory názvů v datovém proudu XML.  
  
 [Serializace XML pomocí webových služeb XML](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)  
 Vysvětluje, jak serializace XML se používá v webové služby XML.  
  
 [Postupy: Serializace objektu jako XML streamu zakódovaného v protokolu SOAP](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
 Popisuje, jak lze použít <xref:System.Xml.Serialization.XmlSerializer> třídy za účelem vytvoření kódovaného datové proudy SOAP XML, které odpovídají část 5 W3c (www.w3.org) dokumentu s názvem "Simple Object Access Protocol (SOAP) 1.1."  
  
 [Postupy: Přepsání serializace XML zakódované v protokolu SOAP](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)  
 Popisuje proces pro přepsání XML serializaci objektů jako zprávy protokolu SOAP.  
  
 [Seznam atributů řídících serializaci zakódovanou v protokolu SOAP](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
 Seznam atributů, které se používají k řízení kódováním SOAP serializace.  
  
 [\<system.xml.serialization> Element](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 Element konfigurace nejvyšší úrovně pro řízení serializace XML.  
  
 [\<dateTimeSerialization > elementu](../../../docs/standard/serialization/datetimeserialization-element.md)  
 Určuje režim serializace <xref:System.DateTime> objekty.  
  
 [\<schemaImporterExtensions > elementu](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 Obsahuje typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> třídy.  
  
 [\<Přidat > elementu pro \<xmlSchemaImporterExtensions >](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 Přidá typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> třídy.  
  
## <a name="related-sections"></a>Související oddíly  
 [Vývoj pro pokročilé technologie](https://msdn.microsoft.com/library/c4a7e341-f0c6-4df4-a74f-223387ac6e4e)  
 Obsahuje odkazy na další informace o sofistikované vývojářské úlohy a techniky v rozhraní .NET Framework.  
  
 [Webové služby XML vytvořený pomocí technologie ASP.NET a klienty webové služby XML](https://msdn.microsoft.com/library/1e64af78-d705-4384-b08d-591a45f4379c)  
 Obsahuje témata, která popisují a popisují, jak program webové služby XML pomocí technologie ASP.NET.  
  
## <a name="see-also"></a>Viz také  
 [Binární serializace](../../../docs/standard/serialization/binary-serialization.md)
