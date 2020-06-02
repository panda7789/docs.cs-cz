---
title: Zpracování dat XML v paměti
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
ms.openlocfilehash: 06863d162a9f9fbf67f41cb12ea4fbb1935b424d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291276"
---
# <a name="processing-xml-data-in-memory"></a>Zpracování dat XML v paměti
Microsoft .NET Framework obsahuje tři modely pro zpracování dat XML: <xref:System.Xml.XmlDocument> třída, <xref:System.Xml.XPath.XPathDocument> třída a [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) a [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).  
  
 Tato <xref:System.Xml.XmlDocument> Třída implementuje doporučení modelu DOM (Document Object Model) W3C úrovně 1 Core a Core DOM na úrovni 2. DOM je reprezentace stromu dokumentu XML v paměti (cache). S <xref:System.Xml.XmlDocument> a souvisejícími třídami můžete vytvářet dokumenty XML, načítat a přistupovat k datům, upravovat data a ukládat změny.  
  
 <xref:System.Xml.XPath.XPathDocument>Třída je úložiště dat v paměti jen pro čtení, které je založené na datovém modelu XPath. <xref:System.Xml.XPath.XPathNavigator>Třída nabízí několik možností úprav a možností navigace pomocí modelu kurzoru nad dokumenty XML obsaženými ve třídě jen pro čtení <xref:System.Xml.XPath.XPathDocument> a také v <xref:System.Xml.XmlDocument> třídě.  
  
 [LINQ to XML](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) je model představený v .NET Framework verze 3,5 pro zpracování dat XML. Jedná se o model v paměti, který využívá [LINQ (Language-Integrated Query)](../../../csharp/programming-guide/concepts/linq/index.md). LINQ rozšiřuje jazykovou syntaxi C# a Visual Basic, aby poskytovala nové možnosti dotazování.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Zpracování dat XML pomocí modelu DOM](process-xml-data-using-the-dom-model.md)  
 Popisuje použití <xref:System.Xml.XmlDocument> a související třídy pro zpracování dat XML.  
  
 [Zpracování dat XML pomocí modelu dat XPath](process-xml-data-using-the-xpath-data-model.md)  
 Popisuje použití <xref:System.Xml.XPath.XPathDocument> tříd, <xref:System.Xml.XmlDocument> a <xref:System.Xml.XPath.XPathNavigator> ke zpracování dat XML.  
  
 [Zpracování dat XML pomocí LINQ to XML](process-xml-data-using-linq-to-xml.md)  
 Poskytuje stručný přehled LINQ to XML a obsahuje odkazy na dokumentaci k LINQ to XML.  
  
## <a name="related-sections"></a>Související oddíly  
 [Dokumenty a data XML](index.md)
