---
title: Možnosti zpracování XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 33ced8ee-1745-4e71-8dee-ebe70ec067c7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9c316ec79b519e1580f1d5dc7e122d770fb5b82e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583155"
---
# <a name="xml-processing-options"></a>Možnosti zpracování XML
Najdete v následujících tabulkách seznam technologie Microsoftu, které lze použít ke zpracování dat XML.  
  
## <a name="net-framework-options"></a>Možnosti rozhraní .NET framework  
  
|**Možnost**|**Typ zpracování**|**Popis**|  
|----------------|-------------------------|---------------------|  
|[LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) <br />(<xref:System.Xml.Linq> oboru názvů)|V paměti|-Založené na technologii .NET Framework Language-Integrated Query (LINQ).<br />-Poskytuje práce s dotazy, který je podobný SQL pro objekty, relačních dat a XML data.<br />-Poskytuje funkce pro vytváření a transformace intuitivní dokumentu.<br />– Tuto možnost použijte, pokud píšete nový kód.|  
|<xref:System.Xml.XmlReader?displayProperty=nameWithType>|Na základě Stream|-Zajišťuje rychlá, bez mezipaměti, dopředné přístup k datům XML.<br />– Můžete vytvořit objekty pomocí <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType> metoda a určit sadu funkcí pro povolení objektu pomocí <xref:System.Xml.XmlReaderSettings> třídy.|  
|<xref:System.Xml.XmlWriter?displayProperty=nameWithType>|Na základě Stream|-Poskytuje rychlá, bez mezipaměti, dopředné způsob, jak vygenerovat XML data.<br />– Můžete vytvořit objekty pomocí <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> metoda a určit sadu funkcí pro povolení objektu pomocí <xref:System.Xml.XmlWriterSettings> třídy.|  
|<xref:System.Xml.XmlDocument?displayProperty=nameWithType>|V paměti|-Implementuje [W3C Document Object Model (DOM) úrovně 1 jádro](https://www.w3.org/TR/REC-DOM-Level-1/level-one-core.html) a [modelu DOM úroveň 2 jádra](https://www.w3.org/TR/DOM-Level-2-Core/) doporučení.<br />– Můžete vytvořit, vložit, odstranit a upravit uzly pomocí metod a vlastností na základě známých modelu DOM.<br />– Tuto možnost použijte, pokud upravujete stávající kód, který využívá W3C modelu DOM.|  
|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|V paměti|-Nabízí několik možností úprav a možností navigace pomocí modelu kurzoru.<br />– XML dokumenty mohou být obsaženy v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu.<br />-Poskytuje vynikající výkon pro zpracování XML jen pro čtení.<br />– Tuto možnost použijte, pokud upravujete stávající kód s dotazy XPath nebo transformace XSLT.|  
|<xref:System.Xml.Xsl.XslCompiledTransform>|V paměti|-Poskytuje možnosti pro transformaci dat XML pomocí transformace XSL.<br />– [Kompilátor XSLT (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md) umožňuje odkazujete předem zkompilovat transformace ve vaší aplikaci.|  
  
## <a name="win32-and-com-based-options"></a>Win32 a možnosti založené na modelu COM  
  
|**Možnost**|**Popis**|  
|----------------|---------------------|  
|[XmlLite](https://msdn.microsoft.com/library/ms752872.aspx)|-Rychlé a zabezpečené, bez ukládání do mezipaměti, dopředné analyzátoru XML, který vám pomůže vytvářet výkonné při XML aplikace.<br />– Funguje v libovolném jazyce, který můžete použít dynamické knihovny (DLL); Doporučujeme, abyste pomocí jazyka C++.|  
|[MSXML](https://msdn.microsoft.com/library/ms763742.aspx)|-Založené na modelu COM. technologii ke zpracování jazyka XML, který je součástí operačního systému Windows.<br />-Poskytuje nativní implementaci modelu DOM s podporou jazyka XPath a XSLT.<br />-Obsahuje SAX2 Analyzátor založený na událostech.|  
  
## <a name="see-also"></a>Viz také:

- [Zpracování dat XML pomocí modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Kompilátor XSLT (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)
