---
title: "Transformace XSLT přes různé úložiště"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 369850e9-004a-45d2-b5c3-5060d9135adb
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b909b754c1d0d3007e06cd04376413d02cbc2f76
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="xslt-transformations-over-different-stores"></a>Transformace XSLT přes různé úložiště
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Můžete provést jazyk XSL pro transformace transformace XSLT () pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy. V tématu [pomocí třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.  
  
 Technologie ADO.NET a soubor XML třídy v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] poskytnout jednotný programovací model pro přístup k datům. Tato data je reprezentován jako data XML, který je text oddělený podle značky, a relační data, která je tabulky, který se skládá z řádků a sloupců. Kód XML v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] čte XML data z jakékoli datový proud do stromy uzlu XML modelu DOM (Document Object), kde je přístupný prostřednictvím kódu programu, zatímco ADO.NET poskytuje způsob, jak přistupovat a manipulovat s relačních dat v rámci <xref:System.Data.DataSet> objektu.  
  
 XML DOM poskytuje přístup k datům v XML – dokumenty a další třídy pro čtení, zápisu a přejděte do dokumentů XML. Tyto třídy jsou podporovány v <xref:System.Xml> názvů, který také kombinuje XML DOM s služby přístup dat poskytované ADO.NET. <xref:System.Xml.XmlDataDocument> Poskytuje relační přístup k datům. <xref:System.Xml.XmlDataDocument> Mapuje XML na relační data v technologie ADO.NET <xref:System.Data.DataSet>. Všechny [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]– na základě aplikace můžete použít třídy v <xref:System.Xml> obor názvů pro přístup a zpracování dokumentů XML a relační data v <xref:System.Xml.XmlDataDocument>. Tato implementace podporuje n vrstvé architektury pro shromažďování a distribuci dat. Další informace najdete v tématu [XML integrace s relačních dat a ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md).  
  
## <a name="see-also"></a>Viz také  
 [Třída XslTransform implementuje procesoru XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
