---
title: Zpracování dat XML v paměti
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
caps.latest.revision: 2
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1c451e4015e37c118f475ec1e7c099566e28767f
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="processing-xml-data-in-memory"></a>Zpracování dat XML v paměti
Rozhraní Microsoft .NET Framework zahrnuje tři modely pro zpracování dat XML: <xref:System.Xml.XmlDocument> třídy, <xref:System.Xml.XPath.XPathDocument> třída, a [technologie LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).  
  
 <xref:System.Xml.XmlDocument> Třída implementuje základní úroveň 1 W3C dokumentu objektu modelu (DOM) a modelu DOM základní úroveň 2 doporučení. Je modelu DOM v paměti (mezipaměť) stromu reprezentace dokumentu XML. Pomocí <xref:System.Xml.XmlDocument> a související třídy, můžete vytvořit dokumentů XML, spouštění a přístup k datům, upravovat data a uložit změny.  
  
 <xref:System.Xml.XPath.XPathDocument> Třída je jen pro čtení, v paměti datové úložiště, které je založená na datovém modelu XPath. <xref:System.Xml.XPath.XPathNavigator> Třída nabízí několik možností úprav a navigační možnosti použití modelu kurzoru nad dokumentů XML obsažených v jen pro čtení <xref:System.Xml.XPath.XPathDocument> třídy a taky <xref:System.Xml.XmlDocument> třídy.  
  
 [Technologie LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) je nový model v rozhraní .NET Framework verze 3.5 pro zpracování dat XML. Je model v paměti, která využívá [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d). LINQ rozšiřuje na syntaxi jazyka C# a Visual Basic zajistit nové možnosti dotazu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Zpracování dat XML pomocí modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 Popisuje použití <xref:System.Xml.XmlDocument>a jeho souvisejících tříd zpracovat XML data.  
  
 [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 Popisuje použití <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument>, a <xref:System.Xml.XPath.XPathNavigator> třídy zpracovat XML data.  
  
 [Zpracování dat XML pomocí LINQ to XML](../../../../docs/standard/data/xml/process-xml-data-using-linq-to-xml.md)  
 Poskytuje stručný přehled technologie LINQ to XML a poskytuje odkazy na LINQ to XML dokumentace.  
  
## <a name="related-sections"></a>Související oddíly  
 [Dokumenty a data XML](../../../../docs/standard/data/xml/index.md)
