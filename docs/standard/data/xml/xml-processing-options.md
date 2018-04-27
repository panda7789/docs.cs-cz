---
title: Možnosti pro zpracování XML
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33ced8ee-1745-4e71-8dee-ebe70ec067c7
caps.latest.revision: 5
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cabe640aa555400228acb572315a43b6ca9265bb
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="xml-processing-options"></a>Možnosti pro zpracování XML
Projděte si následující tabulky seznam technologiích společnosti Microsoft, které můžete použít pro proces XML data.  
  
## <a name="net-framework-options"></a>Možnosti rozhraní .NET framework  
  
|**Možnost**|**Zpracování typu**|**Popis**|  
|----------------|-------------------------|---------------------|  
|[LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) <br />(<xref:System.Xml.Linq> oboru názvů)|V paměti|-Založené na technologii .NET Framework Language-Integrated dotazu (LINQ).<br />-Poskytuje podobné jazyka SQL pro objekty, relační data a XML data možnosti dotazu.<br />-Poskytuje inituive možnosti vytváření a transformace dokumentů.<br />– Tuto možnost použijte, pokud píšete nový kód.|  
|<xref:System.Xml.XmlReader?displayProperty=nameWithType>|Na základě datového proudu|-Umožňuje rychlé, bez mezipaměti, dopředné pro přístup k datům XML.<br />– Můžete vytvořit objekty pomocí <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType> metoda a zadejte sadu funkcí pro povolení objektu pomocí <xref:System.Xml.XmlReaderSettings> – třída.|  
|<xref:System.Xml.XmlWriter?displayProperty=nameWithType>|Na základě datového proudu|-Umožňuje rychlé, bez mezipaměti, dopředné pro generování dat XML.<br />– Můžete vytvořit objekty pomocí <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> metoda a zadejte sadu funkcí pro povolení objektu pomocí <xref:System.Xml.XmlWriterSettings> – třída.|  
|<xref:System.Xml.XmlDocument?displayProperty=nameWithType>|V paměti|-Implementuje [základní úroveň 1 W3C Model Document Object (DOM)](https://www.w3.org/TR/REC-DOM-Level-1/level-one-core.html) a [DOM úroveň 2 jádra](https://www.w3.org/TR/DOM-Level-2-Core/) doporučení.<br />-Můžete vytvořit, vložení, odebrání a změna uzly pomocí metody a vlastnosti, na základě známých modelu DOM.<br />– Tuto možnost použijte, pokud upravujete stávající kód, který využívá W3C modelu DOM.|  
|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|V paměti|-Nabízí několik možností úprav a navigační možnosti použití modelu kurzoru.<br />-Dokumenty XML může obsahovat <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu.<br />-Poskytuje vynikající výkon pro zpracování XML jen pro čtení.<br />– Tuto možnost použijte, pokud upravujete stávající kód dotazů XPath nebo transformací XSLT.|  
|<xref:System.Xml.Xsl.XslCompiledTransform>|V paměti|-Poskytuje možnosti pro transformaci dat XML pomocí XSL transformace.<br />-Na [kompilátoru XSLT (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md) umožňuje odkazujete předem zkompilovat transformace ve vaší aplikaci.|  
  
## <a name="win32-and-com-based-options"></a>Win32 a možnosti založené na modelu COM  
  
|**Možnost**|**Popis**|  
|----------------|---------------------|  
|[Analyzátor XmlLite](https://msdn.microsoft.com/library/ms752872.aspx)|-A rychlé, zabezpečení, bez ukládání do mezipaměti, dopředné analyzátor XML, který vám pomůže vytvořit výkonné při XML aplikace.<br />-Funguje s jakýkoli jazyk, který můžete použít dynamické knihovny (DLL); Doporučujeme používat C++.|  
|[MSXML](https://msdn.microsoft.com/library/ms763742.aspx)|-Založená na modelu COM technologie pro zpracování XML, který je součástí operačního systému Windows.<br />-Poskytuje nativní implementaci modelu DOM s podporou jazyka XPath a XSLT.<br />-Obsahuje SAX2 Analyzátor založený na událostech.|  
  
## <a name="see-also"></a>Viz také  
 [Zpracování dat XML pomocí modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Kompilátor XSLT (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)
