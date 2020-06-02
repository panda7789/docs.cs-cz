---
title: Dokumenty a data XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: e695047f-3c0f-4045-8708-5baea91cc380
ms.openlocfilehash: a752d634141a56df1caa61eb5d375dd2a402832f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287685"
---
# <a name="xml-documents-and-data"></a>Dokumenty a data XML

.NET Framework poskytuje komplexní a integrovanou sadu tříd, které vám umožní snadno vytvářet aplikace podporující XML. Třídy v následujících oborech názvů podporují analýzu a zápis XML, úpravu dat XML v paměti, ověřování dat a transformaci XSLT.

- <xref:System.Xml>

- <xref:System.Xml.XPath>

- <xref:System.Xml.Xsl>

- <xref:System.Xml.Schema>

- <xref:System.Xml.Linq>

Úplný seznam najdete v tématu "System. XML" v [prohlížeči rozhraní .NET API](https://docs.microsoft.com/dotnet/api/?term=system.xml).

Třídy v těchto oborech názvů podporují doporučení konsorcium World Wide Web (W3C). Například:

- <xref:System.Xml.XmlDocument?displayProperty=nameWithType>Třída implementuje základní doporučení na úrovni [W3C model DOM (Document Object Model) (DOM) 1 Core](https://www.w3.org/TR/REC-DOM-Level-1/) a [DOM úrovně 2](https://www.w3.org/TR/DOM-Level-2-Core/) .

- <xref:System.Xml.XmlReader?displayProperty=nameWithType>Třídy a <xref:System.Xml.XmlWriter?displayProperty=nameWithType> podporují [W3C XML 1,0](https://www.w3.org/TR/2006/REC-xml-20060816/) a [obory názvů v](https://www.w3.org/TR/REC-xml-names/) doporučeních XML.

- Schémata ve <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> třídě podporují [součást 1 W3C XML schématu: struktury](https://www.w3.org/TR/xmlschema-1/) a [schéma XML – část 2: doporučení k datatypeům](https://www.w3.org/TR/xmlschema-2/) .

- Třídy v <xref:System.Xml.Xsl?displayProperty=nameWithType> oboru názvů podporují transformace XSLT, které odpovídají doporučením [W3C XSLT 1,0](https://www.w3.org/TR/xslt) .

Třídy XML v .NET Framework poskytují tyto výhody:

- **Produktivitu.** [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) a [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) usnadňují program s XML a poskytuje podobné prostředí jako SQL.

- **Možností.** Třídy XML v .NET Framework jsou rozšiřitelné prostřednictvím použití abstraktních základních tříd a virtuálních metod. Můžete například vytvořit odvozenou třídu <xref:System.Xml.XmlUrlResolver> třídy, která ukládá datový proud mezipaměti na místní disk.

- **Připojitelné architektury.** .NET Framework poskytuje architekturu, ve které komponenty mohou být vzájemně využívány, a data lze streamovat mezi komponentami. Například úložiště dat, jako je <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> objekt nebo, lze transformovat s <xref:System.Xml.Xsl.XslCompiledTransform> třídou a výstup může být následně streamování do jiného úložiště nebo vráceno jako datový proud z webové služby.

- **Předepsané.** Pro lepší výkon aplikace některé třídy XML v .NET Framework podporují model založený na streamování s následujícími charakteristikami:

  - Minimální ukládání do mezipaměti pro analýzu, která je jen pro čtení ( <xref:System.Xml.XmlReader> ).

  - Ověřování jen pro čtení ( <xref:System.Xml.XmlReader> ).

  - Navigace ve stylu kurzoru, která minimalizuje vytváření uzlů na jeden virtuální uzel při poskytování náhodného přístupu k dokumentu ( <xref:System.Xml.XPath.XPathNavigator> ).

  Pro lepší výkon vždy, když je vyžadováno zpracování XSLT, můžete použít <xref:System.Xml.XPath.XPathDocument> třídu, což je optimalizované úložiště jen pro čtení pro dotazy XPath navržené pro efektivní práci s <xref:System.Xml.Xsl.XslCompiledTransform> třídou.

- **Integrace s ADO.NET.** Třídy XML a [ADO.NET](../../../framework/data/adonet/index.md) jsou pevně integrované pro spojování relačních dat a XML. <xref:System.Data.DataSet>Třída je mezipaměť dat načtená z databáze z paměti. <xref:System.Data.DataSet>Třída má možnost číst a zapisovat XML pomocí <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> tříd a, aby bylo možné zachovat vnitřní relační strukturu schématu jako schéma XML (XSD) a jak odvodit strukturu schématu dokumentu XML.

## <a name="in-this-section"></a>V tomto oddílu

[Možnosti zpracování XML](xml-processing-options.md) Popisuje možnosti zpracování dat XML.

[Zpracování dat XML v paměti](processing-xml-data-in-memory.md) Popisuje tři modely pro zpracování dat XML v paměti: [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) a [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md), <xref:System.Xml.XmlDocument> třídy (založené na model DOM (Document Object Model) konsorcia W3C) a <xref:System.Xml.XPath.XPathDocument> třídě (na základě datového modelu XPath).

[Transformace XSLT](xslt-transformations.md)\
Popisuje, jak používat procesor XSLT.

[Model objektu XML schématu (SOM)](xml-schema-object-model-som.md)\
Popisuje třídy používané pro sestavování a manipulaci se schématy XML (XSD) poskytnutím <xref:System.Xml.Schema.XmlSchema> třídy pro načtení a úpravu schématu.

[Integrace XML s relačními daty a ADO.NET](xml-integration-with-relational-data-and-adonet.md)\
Popisuje, jak .NET Framework umožňuje synchronní přístup v reálném čase do relačních i hierarchických reprezentace dat prostřednictvím <xref:System.Data.DataSet> objektu a <xref:System.Xml.XmlDataDocument> objektu.

[Správa oborů názvů v dokumentu XML](managing-namespaces-in-an-xml-document.md)\
Popisuje, jak <xref:System.Xml.XmlNamespaceManager> se třída používá k ukládání a údržbě informací o oboru názvů.

[Podpora typů v třídách System. XML](type-support-in-the-system-xml-classes.md)\
Popisuje, jak jsou datové typy XML mapovány na typy CLR, jak převést datové typy XML a další funkce podpory typu ve <xref:System.Xml> třídách.

## <a name="related-sections"></a>Související oddíly

[ADO.NET](../../../framework/data/adonet/index.md)\
Poskytuje informace o tom, jak přistupovat k datům pomocí ADO.NET.

[Bezpečnost](../../security/index.md)\
V této části najdete přehled systému .NET Framework Security.
