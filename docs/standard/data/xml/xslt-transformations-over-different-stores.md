---
title: Transformace XSLT v různých úložištích
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 369850e9-004a-45d2-b5c3-5060d9135adb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0b5ff264f9a781c95ccf9bdbabf4b29806016362
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43890838"
---
# <a name="xslt-transformations-over-different-stores"></a>Transformace XSLT v různých úložištích
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Můžete provádět rozšiřitelný jazyk šablony stylů transformace XSLT () transformaci pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy. Zobrazit [používání třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.  
  
 ADO.NET a XML tříd v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] poskytují jednotný programovací model pro přístup k datům. Tato data je vyjádřena jako data XML, což je text oddělený podle klíčových slov, a relační data, která je tabulkách sestávajících z řádků a sloupců. Kód XML v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] přečte XML data z jakékoli datový proud do uzel stromů XML Document Object Model (DOM), kde data je možné programově přistupovat, zatímco ADO.NET poskytuje způsob, jak přistupovat k a manipulaci s relačními daty v rámci <xref:System.Data.DataSet> objektu.  
  
 Modelu DOM jazyka XML poskytuje přístup k datům v dokumentech XML a další třídy pro čtení, zápisu a přejděte v dokumentech XML. Tyto třídy jsou podporovány v <xref:System.Xml> obor názvů, který také sjednocuje modelu DOM jazyka XML pomocí poskytnutých ADO.NET data access services. <xref:System.Xml.XmlDataDocument> Poskytuje relační přístup k datům. <xref:System.Xml.XmlDataDocument> XML se mapuje na relačními daty v technologie ADO.NET <xref:System.Data.DataSet>. Žádné [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]– na základě aplikace můžete použít třídy v <xref:System.Xml> obor názvů pro přístup k a manipulaci s XML dokumenty a relačními daty v <xref:System.Xml.XmlDataDocument>. Tato implementace podporuje n vrstvé architektury pro shromažďování a distribuci dat. Další informace najdete v tématu [integrace XML s relačními daty a ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md).  
  
## <a name="see-also"></a>Viz také:

- [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
