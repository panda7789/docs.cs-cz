---
title: Možnosti zpracování XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 33ced8ee-1745-4e71-8dee-ebe70ec067c7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3fc7def48bff71935fce7c6ed914ad20c66e5182
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425169"
---
# <a name="xml-processing-options"></a>Možnosti zpracování XML
V následujících tabulkách najdete seznam technologií Microsoftu, které můžete použít ke zpracování dat XML.  
  
## <a name="net-framework-options"></a>Možnosti .NET Framework  
  
|**Nastavení**|**Typ zpracování**|**Popis**|  
|----------------|-------------------------|---------------------|  
|[LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) <br/> [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) <br />(<xref:System.Xml.Linq> obor názvů)|V paměti|– Založený na technologii LINQ (.NET Framework Language-Integrated Query).<br />– Poskytuje možnosti dotazů, které jsou podobné SQL pro objekty, relační data a data XML.<br />– Poskytuje intuitivní možnosti vytváření a transformace dokumentů.<br />– Tuto možnost použijte, pokud píšete nový kód.|  
|<xref:System.Xml.XmlReader?displayProperty=nameWithType>|Založené na streamu|– Poskytuje rychlý a neuložený soubor, který je pouze pro přístup k datům XML.<br />– Objekty lze vytvořit pomocí metody <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType> a zadat sadu funkcí, které mají být povoleny u objektu pomocí <xref:System.Xml.XmlReaderSettings> třídy.|  
|<xref:System.Xml.XmlWriter?displayProperty=nameWithType>|Založené na streamu|– Poskytuje rychlý, neuložený obsah do mezipaměti, jenom pro generování dat XML.<br />– Objekty lze vytvořit pomocí metody <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> a zadat sadu funkcí, které mají být povoleny u objektu pomocí <xref:System.Xml.XmlWriterSettings> třídy.|  
|<xref:System.Xml.XmlDocument?displayProperty=nameWithType>|V paměti|– Implementuje základní doporučení na [úrovni W3C model DOM (Document Object Model) (DOM) 1 Core](https://www.w3.org/TR/REC-DOM-Level-1/level-one-core.html) a [DOM úrovně 2](https://www.w3.org/TR/DOM-Level-2-Core/) .<br />– Můžete vytvářet, vkládat, odebírat a upravovat uzly pomocí metod a vlastností založených na známém modelu DOM.<br />– Tuto možnost použijte, pokud upravujete existující kód, který využívá W3C DOM.|  
|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|V paměti|– Nabízí několik možností úprav a možností navigace pomocí modelu kurzoru.<br />– Dokumenty XML mohou být obsaženy v objektu <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument>.<br />– Poskytuje vynikající výkon pro zpracování XML jen pro čtení.<br />– Tuto možnost použijte, pokud upravujete existující kód pomocí dotazů XPath nebo transformací XSLT.|  
|<xref:System.Xml.Xsl.XslCompiledTransform>|V paměti|– Poskytuje možnosti pro transformaci dat XML pomocí transformací XSL.<br />– [Kompilátor XSLT (xsltc. exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md) umožňuje odkazovat předem zkompilované transformace ve vaší aplikaci.|  
  
## <a name="win32-and-com-based-options"></a>Možnosti založené na Win32 a COM  
  
|**Nastavení**|**Popis**|  
|----------------|---------------------|  
|[Analyzátor](https://docs.microsoft.com/previous-versions/windows/desktop/ms752872(v=vs.85))|– Rychlý, zabezpečený, neukládání do mezipaměti, jenom dopředný analyzátor XML, který vám pomůže vytvářet vysoce výkonné aplikace XML.<br />– Funguje s jakýmkoli jazykem, který může používat knihovny DLL (Dynamic Link Library); Doporučujeme použít C++.|  
|[SLUŽBU](https://docs.microsoft.com/previous-versions/windows/desktop/ms763742(v=vs.85))|– Technologie založená na modelu COM pro zpracování kódu XML, který je součástí operačního systému Windows.<br />-Poskytuje nativní implementaci modelu DOM s podporou XPath a XSLT.<br />-Obsahuje analyzátor založený na událostech SAX2.|  
  
## <a name="see-also"></a>Viz také:

- [Zpracování dat XML pomocí modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Kompilátor XSLT (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)
