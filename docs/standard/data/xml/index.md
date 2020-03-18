---
title: Dokumenty a data XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: e695047f-3c0f-4045-8708-5baea91cc380
ms.openlocfilehash: e0c3f3e99b06b65caf79d87a7831369f6fb33b08
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75710788"
---
# <a name="xml-documents-and-data"></a>Dokumenty a data XML

Rozhraní .NET Framework poskytuje komplexní a integrovanou sadu tříd, které umožňují snadné vytváření aplikací podporujících jazyk XML. Třídy v následujících oborech názvů podporují analýzu a zápis XML, úpravy dat XML v paměti, ověření dat a transformaci XSLT.

- <xref:System.Xml>

- <xref:System.Xml.XPath>

- <xref:System.Xml.Xsl>

- <xref:System.Xml.Schema>

- <xref:System.Xml.Linq>

Úplný seznam vyhledejte v [prohlížeči rozhraní .NET API](https://docs.microsoft.com/dotnet/api/?term=system.xml)v režimu "System.Xml" .

Třídy v těchto oborech názvů podporují doporučení konsorcia W3C (World Wide Web Consortium). Například:

- Třída <xref:System.Xml.XmlDocument?displayProperty=nameWithType> implementuje [W3C Document Object Model (DOM) Úroveň 1 Core](https://www.w3.org/TR/REC-DOM-Level-1/) a [DOM Úroveň 2 Core](https://www.w3.org/TR/DOM-Level-2-Core/) doporučení.

- <xref:System.Xml.XmlReader?displayProperty=nameWithType> Třídy <xref:System.Xml.XmlWriter?displayProperty=nameWithType> a podporují [W3C XML 1.0](https://www.w3.org/TR/2006/REC-xml-20060816/) a [Namespaces v doporučeních XML.](https://www.w3.org/TR/REC-xml-names/)

- Schémata ve <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> třídě podporují [W3C XML schéma část 1: Struktury](https://www.w3.org/TR/xmlschema-1/) a schéma XML Část [2: Datatypes](https://www.w3.org/TR/xmlschema-2/) doporučení.

- Třídy <xref:System.Xml.Xsl?displayProperty=nameWithType> v oboru názvů podporují transformace XSLT, které odpovídají doporučení [W3C XSLT 1.0.](https://www.w3.org/TR/xslt)

Třídy XML v rozhraní .NET Framework poskytují tyto výhody:

- **Produktivity.** [LINQ na XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) a [LINQ do XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) usnadňuje programování pomocí jazyka XML a poskytuje prostředí dotazu, které je podobné SQL.

- **Rozšiřitelnost.** Třídy XML v rozhraní .NET Framework jsou rozšiřitelné pomocí abstraktních základních tříd a virtuálních metod. Můžete například vytvořit odvozenou třídu <xref:System.Xml.XmlUrlResolver> třídy, která ukládá datový proud mezipaměti na místní disk.

- **Připojitelná architektura.** Rozhraní .NET Framework poskytuje architekturu, ve které součásti mohou využívat navzájem a data mohou být datového proudu mezi součástmi. Například úložiště dat, jako <xref:System.Xml.XPath.XPathDocument> je <xref:System.Xml.XmlDocument> například nebo objekt, <xref:System.Xml.Xsl.XslCompiledTransform> lze transformovat s třídou a výstup pak může být datový proud buď do jiného úložiště nebo vráceny jako datový proud z webové služby.

- **Výkon.** Pro lepší výkon aplikace podporují některé třídy XML v rozhraní .NET Framework model založený na streamování s následujícími charakteristikami:

  - Minimální ukládání do mezipaměti pro analýzu modelu<xref:System.Xml.XmlReader>tahu pouze dopředu ( ).

  - Ověření pouze dopředu<xref:System.Xml.XmlReader>( ).

  - Navigace ve stylu kurzoru, která minimalizuje vytváření uzlů do jednoho<xref:System.Xml.XPath.XPathNavigator>virtuálního uzlu a zároveň poskytuje náhodný přístup k dokumentu ( ).

  Pro lepší výkon vždy, když je vyžadováno <xref:System.Xml.XPath.XPathDocument> zpracování XSLT, můžete použít třídu, která je optimalizované úložiště <xref:System.Xml.Xsl.XslCompiledTransform> jen pro čtení pro dotazy XPath určené pro efektivní práci s třídou.

- **Integrace s ADO.NET.** Třídy XML a [ADO.NET](../../../../docs/framework/data/adonet/index.md) jsou úzce integrovány tak, aby spojily relační data a XML. Třída <xref:System.Data.DataSet> je mezipaměť dat načtených z databáze v paměti. Třída <xref:System.Data.DataSet> má schopnost číst a zapisovat XML pomocí tříd <xref:System.Xml.XmlReader> y a, <xref:System.Xml.XmlWriter> zachovat vnitřní strukturu relačního schématu jako schémata XML (XSD) a odvodit strukturu schématu dokumentu XML.

## <a name="in-this-section"></a>V tomto oddílu

[Možnosti zpracování XML](../../../../docs/standard/data/xml/xml-processing-options.md) Popisuje možnosti pro zpracování dat XML.

[Zpracování dat XML v paměti](../../../../docs/standard/data/xml/processing-xml-data-in-memory.md) Popisuje tři modely pro zpracování dat XML v paměti: [LINQ na XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) a <xref:System.Xml.XmlDocument> [LINQ na XML (Visual Basic),](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) <xref:System.Xml.XPath.XPathDocument> třída (na základě w3c document object model) a třída (na základě datového modelu XPath).

[Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)\
Popisuje způsob použití procesoru XSLT.

[Objektový model schématu XML (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)\
Popisuje třídy používané pro vytváření a manipulaci se schématy XML <xref:System.Xml.Schema.XmlSchema> (XSD) tím, že poskytuje třídu pro načtení a úpravu schématu.

[Integrace XML s relačními daty a ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md)\
Popisuje, jak rozhraní .NET Framework umožňuje synchronní přístup k relačním i hierarchickým reprezentacím dat prostřednictvím objektu <xref:System.Data.DataSet> a objektu v <xref:System.Xml.XmlDataDocument> reálném čase.

[Správa oborů názvů v dokumentu XML](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)\
Popisuje, jak <xref:System.Xml.XmlNamespaceManager> se třída používá k ukládání a údržbě informací o oboru názvů.

[Podpora typů ve třídách System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)\
Popisuje, jak se datové typy XML mapují na typy CLR, jak <xref:System.Xml> převést datové typy XML a další funkce podpory typů ve třídách.

## <a name="related-sections"></a>Související oddíly

[ADO.NET](../../../../docs/framework/data/adonet/index.md)\
Obsahuje informace o tom, jak získat přístup k datům pomocí ADO.NET.

[Zabezpečení](../../../../docs/standard/security/index.md)\
Obsahuje přehled systému zabezpečení rozhraní .NET Framework.
