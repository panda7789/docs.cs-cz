---
title: Dokumenty a data XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: e695047f-3c0f-4045-8708-5baea91cc380
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d9cc44b8a5d43a3fe0414ddeeb51f37e239480b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647902"
---
# <a name="xml-documents-and-data"></a>Dokumenty a data XML
Rozhraní .NET Framework poskytuje komplexního a integrovaného sadu tříd, které vám umožní snadno vytvářet aplikace pracující s XML. Třídy v následující obory názvů podporují analýzu a zápis dat XML v paměti, ověřování dat a transformace XSLT pro úpravy XML.  
  
- <xref:System.Xml>  
  
- <xref:System.Xml.XPath>  
  
- <xref:System.Xml.Xsl>  
  
- <xref:System.Xml.Schema>  
  
- <xref:System.Xml.Linq>  
  
 Úplný seznam, vyhledejte "System.Xml" na [.NET API browseru](https://docs.microsoft.com/dotnet/api/?term=system.xml).  
  
 Třídy v tyto obory názvů podporují World Wide Web Consortium (W3C) doporučení. Příklad:  
  
- <xref:System.Xml.XmlDocument?displayProperty=nameWithType> Implementuje třída [W3C Document Object Model (DOM) úrovně 1 jádro](https://www.w3.org/TR/REC-DOM-Level-1/) a [modelu DOM úroveň 2 jádra](https://www.w3.org/TR/DOM-Level-2-Core/) doporučení.  
  
- <xref:System.Xml.XmlReader?displayProperty=nameWithType> a <xref:System.Xml.XmlWriter?displayProperty=nameWithType> třídy podporu [W3C XML 1.0](https://www.w3.org/TR/2006/REC-xml-20060816/) a [obory názvů v XML](https://www.w3.org/TR/REC-xml-names/) doporučení.  
  
- Schémata <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> třídy podporu [části 1 W3C XML schématu: Struktury](https://www.w3.org/TR/xmlschema-1/) a [XML schématu část 2: Datové typy](https://www.w3.org/TR/xmlschema-2/) doporučení.  
  
- Třídy v <xref:System.Xml.Xsl?displayProperty=nameWithType> transformace XSLT podpora oboru názvů, které odpovídají [W3C XSLT 1.0](https://www.w3.org/TR/xslt) doporučení.  
  
 XML tříd v rozhraní .NET Framework poskytuje tyto výhody:  
  
- **Zvýšení produktivity.** [Technologie LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) a [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) usnadňuje programu pomocí XML a poskytuje možnosti dotazu, který je podobný SQL.  
  
- **Rozšiřitelnost.** XML tříd v rozhraní .NET Framework je rozšiřitelný prostřednictvím použití základních tříd abstraktu a virtuální metody. Můžete například vytvořit odvozenou třídu <xref:System.Xml.XmlUrlResolver> třída, která obsahuje datový proud mezipaměti na místní disk.  
  
- **Připojitelná architektura.** Rozhraní .NET Framework poskytuje architekturu, ve kterém komponenty se mezi sebou můžou využívat a Streamovat data mezi komponentami. Například úložiště dat, například <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu, lze je transformovat pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy a výstup je pak možné Streamovat buď do jiného úložiště nebo vrácena jako datový proud z webové služby.  
  
- **Výkon.** Pro lepší výkon aplikace a některé třídy XML v rozhraní .NET Framework podporují jako model založený na datových proudů s následujícími charakteristikami:  
  
    - Minimální ukládání do mezipaměti pro dopředné, pull model analýzu (<xref:System.Xml.XmlReader>).  
  
    - Dopředné ověření (<xref:System.Xml.XmlReader>).  
  
    - Kurzor styl navigace, která minimalizuje vytvoření uzlu na jeden virtuální uzel poskytuje náhodný přístup k tomuto dokumentu (<xref:System.Xml.XPath.XPathNavigator>).  
  
     Pro zajištění lepšího výkonu při každém zpracování XSLT je nutné použít, můžete použít <xref:System.Xml.XPath.XPathDocument> třídu, která je optimalizovaná, jen pro čtení obchod pro dotazy XPath, které jsou navržené tak, aby efektivně pracovat <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
- **Integrace s ADO.NET.** XML tříd a [ADO.NET](../../../../docs/framework/data/adonet/index.md) jsou pevně integrovány spojit relační data a XML. <xref:System.Data.DataSet> Třída je mezipaměti z dat načtených z databáze. <xref:System.Data.DataSet> Má možnost číst a zapisovat XML pomocí třídy <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter> třídy, a zachová své interní schéma relační struktury jako schématu XML (XSD) a k odvození schématu strukturu dokumentu XML.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Možnosti zpracování XML](../../../../docs/standard/data/xml/xml-processing-options.md)  
 Tento článek popisuje možnosti pro zpracování dat XML.  
  
 [Zpracování dat XML v paměti](../../../../docs/standard/data/xml/processing-xml-data-in-memory.md)  
 Tento článek popisuje tři modely pro zpracování XML dat v paměti: [Technologie LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) a [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md), <xref:System.Xml.XmlDocument> třídy (založené na modelu objektu dokumentu W3C) a <xref:System.Xml.XPath.XPathDocument> třídy (založené na modelu dat XPath).  
  
 [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)  
 Popisuje způsob použití procesoru XSLT.  
  
 [Model objektu schématu (SOM) XML](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 Popisuje třídy používané pro vytváření a manipulaci s schémat XML (XSD) tím, že poskytuje <xref:System.Xml.Schema.XmlSchema> třídy pro načtení a upravit schéma.  
  
 [Integrace XML s relačními daty a ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md)  
 Popisuje, jak rozhraní .NET Framework umožňuje v reálném čase, která je synchronní přístup k relačních a hierarchických reprezentace dat prostřednictvím <xref:System.Data.DataSet> objektu a <xref:System.Xml.XmlDataDocument> objektu.  
  
 [Správa oborů názvů v dokumentu XML](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)  
 Popisuje, jak <xref:System.Xml.XmlNamespaceManager> třída se používá k ukládání a správě informace oboru názvů.  
  
 [Podpora typu v třídách System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)  
 Popisuje, jak mapa typy dat XML do CLR typy, jak převést datové typy XML a další funkce podpory typu <xref:System.Xml> třídy.  
  
## <a name="related-sections"></a>Související oddíly  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)  
 Poskytuje informace o tom, jak získat přístup k datům pomocí technologie ADO.NET.  
  
 [Zabezpečení](../../../../docs/standard/security/index.md)  
 Poskytuje přehled o systém zabezpečení rozhraní .NET Framework.  
