---
title: Serializace XML a SOAP
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
ms.openlocfilehash: ca3b31c1d60770a6b9db5e92275d9840036ee0b0
ms.sourcegitcommit: bd4fa78f5a46133efdead1bc692a9aa2811d7868
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2018
ms.locfileid: "42753905"
---
# <a name="xml-and-soap-serialization"></a>Serializace XML a SOAP

Převede serializace XML (serializuje) veřejné polí a vlastností objektu, nebo parametry a návratovými hodnotami metod do datový proud XML, který odpovídá určitého dokumentu definition language (XSD) schématu XML. Serializace XML výsledkem silného typu třídy s veřejné vlastnosti a pole, které jsou převedeny na sériového formátu (v tomto případě XML) pro uložení nebo přenos.

Protože kód XML je otevřený standard, může být zpracována datový proud XML ve všech aplikacích, podle potřeby, bez ohledu na platformu. Můžete například webové služby XML vytvořené pomocí technologie ASP.NET použití <xref:System.Xml.Serialization.XmlSerializer> třídy za účelem vytvoření datové proudy XML, který vkládá data mezi aplikací webové služby XML v rámci Internetu nebo v těchto sítích. Deserializace naopak přebírá takové datový proud XML a rekonstruuje objektu.

Serializace XML lze také použít k serializaci objektů do datových proudů XML, které odpovídají specifikaci protokolu SOAP. Protokol SOAP je protokol založený na formát XML, který je určen speciálně k přenosu volání procedur pomocí jazyka XML.

K serializaci nebo deserializaci objektů, použijte <xref:System.Xml.Serialization.XmlSerializer> třídy. Chcete-li vytvořit třídy k serializaci, použijte nástroj definici schématu XML.

## <a name="in-this-section"></a>V tomto oddílu

[Představení serializace XML](introducing-xml-serialization.md)  
Poskytuje obecné definici serializaci, zejména serializace XML.

[Postupy: Serializace objektu](how-to-serialize-an-object.md)  
Obsahuje podrobné pokyny pro serializaci objektu.

[Postupy: Deserializace objektu](how-to-deserialize-an-object.md)  
Obsahuje podrobné pokyny pro deserializaci objektu.

[Příklady serializace XML](examples-of-xml-serialization.md)  
Poskytuje příklady, které ukazují základní informace o serializaci kódu XML.

[Nástroj pro definici schématu XML a serializace XML](the-xml-schema-definition-tool-and-xml-serialization.md)  
Popisuje, jak používat nástroj definici schématu XML k vytvoření třídy, které splňovat konkrétní jazyk (XSD) schématu definice schématu XML nebo ke generování schématu XML z soubor DLL.

[Řízení serializace XML pomocí atributů](controlling-xml-serialization-using-attributes.md)  
Popisuje, jak řídit serializace pomocí atributů.

[Seznam atributů řídících serializaci XML](attributes-that-control-xml-serialization.md)  
Seznam atributů, které se používají k řízení serializace XML.

[Postupy: Zadání alternativního názvu elementu pro XML stream](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
Uvede případě rozšířeného scénáře ukázkami, jak ke generování více datové proudy XML přepsáním serializace.

[Postupy: Řízení serializace odvozených tříd](how-to-control-serialization-of-derived-classes.md)  
Obsahuje příklad toho, jak řídit serializace odvozené třídy.

[Postupy: Kvalifikace názvů elementů a atributů XML](how-to-qualify-xml-element-and-xml-attribute-names.md)  
Popisuje, jak lze definovat a určit tak, jak v XML, které se používají obory názvů v datovém proudu XML.

[Serializace XML pomocí webových služeb XML](xml-serialization-with-xml-web-services.md)  
Vysvětluje, jak serializace XML se používá v webové služby XML.

[Postupy: Serializace objektu jako XML streamu zakódovaného v protokolu SOAP](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
Popisuje způsob použití <xref:System.Xml.Serialization.XmlSerializer> třídy za účelem vytvoření kódovaného datové proudy SOAP XML, které odpovídají část 5 World Wide Web Consortium (W3C) dokumentu s názvem [jednoduchý objekt přístup protokolu (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/).

[Postupy: Přepsání serializace XML zakódované v protokolu SOAP](how-to-override-encoded-soap-xml-serialization.md)  
Popisuje proces pro přepsání XML serializaci objektů jako zprávy protokolu SOAP.

[Seznam atributů řídících serializaci zakódovanou v protokolu SOAP](attributes-that-control-encoded-soap-serialization.md)  
Seznam atributů, které se používají k řízení kódováním SOAP serializace.

[\<system.xml.serialization> Element](system-xml-serialization-element.md)  
Element konfigurace nejvyšší úrovně pro řízení serializace XML.

[\<dateTimeSerialization > – Element](datetimeserialization-element.md)  
Určuje režim serializace <xref:System.DateTime> objekty.

[\<schemaImporterExtensions > – Element](schemaimporterextensions-element.md)  
Obsahuje typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> třídy.

[\<Přidat > – Element pro \<schemaImporterExtensions >](add-element-for-schemaimporterextensions.md)  
Přidá typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> třídy.

## <a name="related-sections"></a>Související oddíly

[Pokročilé vývojovým technologiím](https://msdn.microsoft.com/library/c4a7e341-f0c6-4df4-a74f-223387ac6e4e)  
Obsahuje odkazy na další informace o sofistikované vývojářské úlohy a techniky v rozhraní .NET Framework.

[Webové služby XML vytvořené pomocí ASP.NET a klienty webové služby XML](https://msdn.microsoft.com/library/1e64af78-d705-4384-b08d-591a45f4379c)  
Obsahuje témata, které popisují a vysvětluje, jak program webové služby XML pomocí technologie ASP.NET.

## <a name="see-also"></a>Viz také

[Binární serializace](binary-serialization.md)  