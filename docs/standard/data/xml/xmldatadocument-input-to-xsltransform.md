---
title: XmlDataDocument vstup XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a0b536b6-cdb3-4a44-86c2-3b2ebc7bd4c9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 283681946702d80d746d40682eec2539ebfa68f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="xmldatadocument-input-to-xsltransform"></a>XmlDataDocument vstup XslTransform
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Můžete provést jazyk XSL pro transformace transformace XSLT () pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy. V tématu [pomocí třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.  
  
 Microsoft [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] implementuje XML modelu DOM (Document Object) k poskytování přístupu k datům v XML – dokumenty a další třídy pro čtení, zápisu a přejděte do dokumentů XML. <xref:System.Xml.XmlDataDocument>, Který se nachází v <xref:System.Xml> obor názvů, poskytuje schopnost synchronizovat s relační data v relační přístup k datům <xref:System.Data.DataSet>. Najednou můžete zobrazit a pracovat s strukturovaných XML prostřednictvím relační reprezentace <xref:System.Data.DataSet> částečně strukturovaných XML pomocí modelu DOM reprezentace pro práci s nimi <xref:System.Xml.XmlDataDocument>. <xref:System.Xml.XmlDataDocument> Proto hranice soubor XML a relační světů protíná.  
  
 Pokud jsou data uložena v relační struktura a má být vstup k transformaci XSLT, můžete načíst relačních dat do <xref:System.Data.DataSet> a přidružte ji s <xref:System.Xml.XmlDataDocument>. <xref:System.Xml.XPath.XPathNavigator>, Vstup <xref:System.Xml.Xsl.XslTransform>, se implementuje na <xref:System.Xml.XmlDataDocument> prostřednictvím <xref:System.Xml.XPath.IXPathNavigable> rozhraní. Provedením relačních dat načítání do aplikace <xref:System.Data.DataSet>a pomocí synchronizace v rámci <xref:System.Xml.XmlDataDocument>, relačních dat může mít nyní provádí transformace XSLT.  
  
 Další informace o použití transformace na relační data, najdete v části [použití transformaci XSLT na datovou sadu](../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.XmlDataDocument>  
 [Synchronizace datové sady a datového dokumentu XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)  
 [Transformace XSLT s třídou XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [XPathNavigator v transformacích](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [XPathNodeIterator v transformacích](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [Vstup XPathDocument do XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [Vstup XmlDocument do XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
