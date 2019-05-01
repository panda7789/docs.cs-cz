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
ms.openlocfilehash: d9dc68d8e7eced031af404aaec20784573c9930a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62028236"
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

[Postupy: Určení alternativního názvu elementu pro Stream XML](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
Uvede případě rozšířeného scénáře ukázkami, jak ke generování více datové proudy XML přepsáním serializace.

[Postupy: Řízení serializace odvozených tříd](how-to-control-serialization-of-derived-classes.md)  
Obsahuje příklad toho, jak řídit serializace odvozené třídy.

[Postupy: Kvalifikovat názvy atributů XML a elementu XML](how-to-qualify-xml-element-and-xml-attribute-names.md)  
Popisuje, jak lze definovat a určit tak, jak v XML, které se používají obory názvů v datovém proudu XML.

[Serializace XML pomocí webových služeb XML](xml-serialization-with-xml-web-services.md)  
Vysvětluje, jak serializace XML se používá v webové služby XML.

[Postupy: Serializace objektu jako XML kódováním protokolu SOAP Stream](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
Popisuje způsob použití <xref:System.Xml.Serialization.XmlSerializer> třídy za účelem vytvoření kódovaného datové proudy SOAP XML, které odpovídají část 5 World Wide Web Consortium (W3C) dokumentu s názvem [jednoduchý objekt přístup protokolu (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/).

[Postupy: Přepsat kódovaný protokol SOAP serializace XML](how-to-override-encoded-soap-xml-serialization.md)  
Popisuje proces pro přepsání XML serializaci objektů jako zprávy protokolu SOAP.

[Seznam atributů řídících serializaci zakódovanou v protokolu SOAP](attributes-that-control-encoded-soap-serialization.md)  
Seznam atributů, které se používají k řízení kódováním SOAP serializace.

[\<system.xml.serialization> Element](system-xml-serialization-element.md)  
Element konfigurace nejvyšší úrovně pro řízení serializace XML.

[\<dateTimeSerialization > – Element](datetimeserialization-element.md)  
Určuje režim serializace <xref:System.DateTime> objekty.

[\<schemaImporterExtensions> Element](schemaimporterextensions-element.md)  
Obsahuje typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> třídy.

[\<Přidat > – Element pro \<schemaImporterExtensions >](add-element-for-schemaimporterextensions.md)  
Přidá typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> třídy.

## <a name="related-sections"></a>Související oddíly

[Webové služby XML vytvořené pomocí ASP.NET a klienty webové služby XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))  
Obsahuje témata, které popisují a vysvětluje, jak program webové služby XML pomocí technologie ASP.NET.

## <a name="see-also"></a>Viz také:

- [Binární serializace](binary-serialization.md)
