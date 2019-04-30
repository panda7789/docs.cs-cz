---
title: Zpracování dat XML v paměti
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f1a4587838180896b52bb79d447ed7ede3e22d1a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770419"
---
# <a name="processing-xml-data-in-memory"></a>Zpracování dat XML v paměti
Rozhraní Microsoft .NET Framework zahrnuje tři modely pro zpracování dat XML: <xref:System.Xml.XmlDocument> třídy, <xref:System.Xml.XPath.XPathDocument> třídy, a [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) a [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).  
  
 <xref:System.Xml.XmlDocument> Třída implementuje úroveň 1 jádro W3C dokumentu objektu model (DOM) a modelu DOM základní úrovně 2 doporučení. (Mezipaměť) v paměti je v modelu DOM stromu reprezentace dokumentu XML. S <xref:System.Xml.XmlDocument> a jeho souvisejících tříd, můžete vytvořit dokumentů XML, načtení a přístup k datům a upravovat data, a uložit změny.  
  
 <xref:System.Xml.XPath.XPathDocument> Třída je úložiště dat jen pro čtení, v paměti, která je založena na modelu dat XPath. <xref:System.Xml.XPath.XPathNavigator> Třídy nabízí několik možností úprav a možností navigace pomocí modelu kurzoru nad dokumenty XML obsažených v jen pro čtení <xref:System.Xml.XPath.XPathDocument> třídy i na <xref:System.Xml.XmlDocument> třídy.  
  
 [Technologie LINQ to XML](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) je model zavedena v rozhraní .NET Framework verze 3.5 pro zpracování dat XML. Je modelu v paměti, který využívá [Language-Integrated Query (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md). Rozšiřuje syntaxi jazyka LINQ C# a Visual Basic a poskytují nové možnosti dotazu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Zpracování dat XML pomocí modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 Popisuje použití <xref:System.Xml.XmlDocument>a její související třídy pro zpracování dat XML.  
  
 [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 Popisuje použití <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument>, a <xref:System.Xml.XPath.XPathNavigator> třídy pro zpracování dat XML.  
  
 [Zpracování dat XML pomocí LINQ to XML](../../../../docs/standard/data/xml/process-xml-data-using-linq-to-xml.md)  
 Poskytuje stručný přehled technologie LINQ to XML a poskytuje odkazy na LINQ to XML dokumentace.  
  
## <a name="related-sections"></a>Související oddíly  
 [Dokumenty a data XML](../../../../docs/standard/data/xml/index.md)
