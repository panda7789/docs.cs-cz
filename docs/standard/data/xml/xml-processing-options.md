---
title: Možnosti zpracování XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 33ced8ee-1745-4e71-8dee-ebe70ec067c7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 585a6e568bde6e6eca15477eaa10b5c91c91c5a4
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835548"
---
# <a name="xml-processing-options"></a>Možnosti zpracování XML
Najdete v následujících tabulkách seznam technologie Microsoftu, které lze použít ke zpracování dat XML.  
  
## <a name="net-framework-options"></a>Možnosti rozhraní .NET framework  
  
|**Možnost**|**Typ zpracování**|**Popis**|  
|----------------|-------------------------|---------------------|  
|[Technologie LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) <br/> [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) <br />(<xref:System.Xml.Linq> oboru názvů)|V paměti|-Založené na technologii .NET Framework Language-Integrated Query (LINQ).<br />-Poskytuje práce s dotazy, který je podobný SQL pro objekty, relačních dat a XML data.<br />-Poskytuje funkce pro vytváření a transformace intuitivní dokumentu.<br />– Tuto možnost použijte, pokud píšete nový kód.|  
|<xref:System.Xml.XmlReader?displayProperty=nameWithType>|Na základě Stream|-Zajišťuje rychlá, bez mezipaměti, dopředné přístup k datům XML.<br />– Můžete vytvořit objekty pomocí <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType> metoda a určit sadu funkcí pro povolení objektu pomocí <xref:System.Xml.XmlReaderSettings> třídy.|  
|<xref:System.Xml.XmlWriter?displayProperty=nameWithType>|Na základě Stream|-Poskytuje rychlá, bez mezipaměti, dopředné způsob, jak vygenerovat XML data.<br />– Můžete vytvořit objekty pomocí <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> metoda a určit sadu funkcí pro povolení objektu pomocí <xref:System.Xml.XmlWriterSettings> třídy.|  
|<xref:System.Xml.XmlDocument?displayProperty=nameWithType>|V paměti|-Implementuje [W3C Document Object Model (DOM) úrovně 1 jádro](https://www.w3.org/TR/REC-DOM-Level-1/level-one-core.html) a [modelu DOM úroveň 2 jádra](https://www.w3.org/TR/DOM-Level-2-Core/) doporučení.<br />– Můžete vytvořit, vložit, odstranit a upravit uzly pomocí metod a vlastností na základě známých modelu DOM.<br />– Tuto možnost použijte, pokud upravujete stávající kód, který využívá W3C modelu DOM.|  
|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|V paměti|-Nabízí několik možností úprav a možností navigace pomocí modelu kurzoru.<br />– XML dokumenty mohou být obsaženy v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu.<br />-Poskytuje vynikající výkon pro zpracování XML jen pro čtení.<br />– Tuto možnost použijte, pokud upravujete stávající kód s dotazy XPath nebo transformace XSLT.|  
|<xref:System.Xml.Xsl.XslCompiledTransform>|V paměti|-Poskytuje možnosti pro transformaci dat XML pomocí transformace XSL.<br />– [Kompilátor XSLT (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md) umožňuje odkazujete předem zkompilovat transformace ve vaší aplikaci.|  
  
## <a name="win32-and-com-based-options"></a>Win32 a možnosti založené na modelu COM  
  
|**Možnost**|**Popis**|  
|----------------|---------------------|  
|[XmlLite](https://docs.microsoft.com/previous-versions/windows/desktop/ms752872(v=vs.85))|-Rychlé a zabezpečené, bez ukládání do mezipaměti, dopředné analyzátoru XML, který vám pomůže vytvářet výkonné při XML aplikace.<br />– Funguje v libovolném jazyce, který můžete použít dynamické knihovny (DLL); Doporučujeme, abyste pomocí jazyka C++.|  
|[MSXML](https://docs.microsoft.com/previous-versions/windows/desktop/ms763742(v=vs.85))|-Založené na modelu COM. technologii ke zpracování jazyka XML, který je součástí operačního systému Windows.<br />-Poskytuje nativní implementaci modelu DOM s podporou jazyka XPath a XSLT.<br />-Obsahuje SAX2 Analyzátor založený na událostech.|  
  
## <a name="see-also"></a>Viz také:

- [Zpracování dat XML pomocí modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Kompilátor XSLT (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)
