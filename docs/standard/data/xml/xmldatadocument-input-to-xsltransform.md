---
title: Vstup XmlDataDocument do XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a0b536b6-cdb3-4a44-86c2-3b2ebc7bd4c9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e7fb30104f36a565f4e6742c8f808c48e4ef39ec
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46696765"
---
# <a name="xmldatadocument-input-to-xsltransform"></a>Vstup XmlDataDocument do XslTransform
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Můžete provádět rozšiřitelný jazyk šablony stylů transformace XSLT () transformaci pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy. Zobrazit [používání třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.  
  
 Microsoft [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] implementuje XML Document Object Model (DOM) a zajistit tak přístup k datům v dokumentech XML a další třídy pro čtení, zápisu a přejděte v dokumentech XML. <xref:System.Xml.XmlDataDocument>Byl nalezen v <xref:System.Xml> obor názvů, poskytuje schopnost synchronizovat s relačními daty v relační přístup k datům <xref:System.Data.DataSet>. Najednou můžete zobrazit a pracovat s strukturovaná data XML do relační reprezentace <xref:System.Data.DataSet> částečně strukturovaných XML pomocí modelu DOM reprezentace pro práci s nimi <xref:System.Xml.XmlDataDocument>. <xref:System.Xml.XmlDataDocument> Proto překročí hranice XML a relační světů.  
  
 Pokud chcete, aby vstup k transformaci XSLT, data se ukládají do relační struktury můžete načíst relačních dat do <xref:System.Data.DataSet> a přidružte jej k <xref:System.Xml.XmlDataDocument>. <xref:System.Xml.XPath.XPathNavigator>, Vstup <xref:System.Xml.Xsl.XslTransform>, se implementuje na <xref:System.Xml.XmlDataDocument> prostřednictvím <xref:System.Xml.XPath.IXPathNavigable> rozhraní. Provedením relačních dat načítání do aplikace <xref:System.Data.DataSet>a pomocí synchronizace v rámci <xref:System.Xml.XmlDataDocument>, relačních dat teď můžou mít transformace XSLT provádí.  
  
 Další informace o použití transformace na relační data, najdete v tématu [použití transformaci XSLT na datovou sadu](../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlDataDocument>  
- [Synchronizace datové sady a datového dokumentu XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)  
- [Transformace XSLT s třídou XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
- [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
- [XPathNavigator v transformacích](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
- [XPathNodeIterator v transformacích](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
- [Vstup XPathDocument do XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
- [Vstup XmlDocument do XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
