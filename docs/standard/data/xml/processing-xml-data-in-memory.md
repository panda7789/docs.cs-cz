---
title: Zpracování dat XML v paměti
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
ms.openlocfilehash: 038bcfcb9d40ee6087efa3487b6f27f252393f2c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710424"
---
# <a name="processing-xml-data-in-memory"></a>Zpracování dat XML v paměti
Microsoft .NET Framework obsahuje tři modely pro zpracování dat XML: <xref:System.Xml.XmlDocument> třídy, třídy <xref:System.Xml.XPath.XPathDocument> a [LINQ to XMLC#()](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) a [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).  
  
 Třída <xref:System.Xml.XmlDocument> implementuje doporučení modelu DOM (Document Object Model) W3C úrovně 1 Core a Core DOM na úrovni 2. DOM je reprezentace stromu dokumentu XML v paměti (cache). S <xref:System.Xml.XmlDocument> a souvisejícími třídami můžete vytvářet dokumenty XML, načítat a přistupovat k datům, upravovat data a ukládat změny.  
  
 Třída <xref:System.Xml.XPath.XPathDocument> je úložiště dat v paměti jen pro čtení, které je založené na datovém modelu XPath. Třída <xref:System.Xml.XPath.XPathNavigator> nabízí několik možností úprav a možností navigace pomocí modelu kurzoru nad dokumenty XML obsaženými ve třídě <xref:System.Xml.XPath.XPathDocument> jen pro čtení a také v třídě <xref:System.Xml.XmlDocument>.  
  
 [LINQ to XML](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) je model představený v .NET Framework verze 3,5 pro zpracování dat XML. Jedná se o model v paměti, který využívá [LINQ (Language-Integrated Query)](../../../csharp/programming-guide/concepts/linq/index.md). LINQ rozšiřuje jazykovou syntaxi C# a Visual Basic, aby poskytovala nové možnosti dotazování.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Zpracování dat XML pomocí modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 Popisuje použití <xref:System.Xml.XmlDocument>a jeho souvisejících tříd pro zpracování dat XML.  
  
 [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 Popisuje použití tříd <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument>a <xref:System.Xml.XPath.XPathNavigator> pro zpracování dat XML.  
  
 [Zpracování dat XML pomocí LINQ to XML](../../../../docs/standard/data/xml/process-xml-data-using-linq-to-xml.md)  
 Poskytuje stručný přehled LINQ to XML a obsahuje odkazy na dokumentaci k LINQ to XML.  
  
## <a name="related-sections"></a>Související oddíly  
 [Dokumenty a data XML](../../../../docs/standard/data/xml/index.md)
