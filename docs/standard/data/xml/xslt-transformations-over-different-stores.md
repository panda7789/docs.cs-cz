---
title: Transformace XSLT v různých úložištích
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 369850e9-004a-45d2-b5c3-5060d9135adb
ms.openlocfilehash: 490ac30a3e4f0c50cb5d011f1d583c6e5ce9e672
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709657"
---
# <a name="xslt-transformations-over-different-stores"></a>Transformace XSLT v různých úložištích
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá v .NET Framework 2,0. Transformace XSLT (Extensible Stylesheet Language) můžete použít k <xref:System.Xml.Xsl.XslCompiledTransform> transformaci pomocí třídy. Další informace najdete v tématu [použití třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 ADO.NET a třídy XML v .NET Framework poskytují jednotný programovací model pro přístup k datům. Tato data jsou reprezentována jako data XML, což je text oddělený pomocí značek a relačních dat, což je tabulka skládající se z řádků a sloupců. XML v .NET Framework čte data XML z libovolného datového proudu do stromů uzlů XML model DOM (Document Object Model) (DOM), kde lze data přistupovat programově, zatímco ADO.NET poskytuje prostředky pro přístup k relačním datům v rámci <xref:System.Data.DataSet> objektu a manipulaci s nimi.  
  
 Model DOM XML poskytuje přístup k datům v dokumentech XML a dalším třídám pro čtení, zápis a navigaci v dokumentech XML. Tyto třídy jsou podporovány v <xref:System.Xml> oboru názvů, který také sjednocuje XML DOM se službami pro přístup k datům, které poskytuje ADO.NET. <xref:System.Xml.XmlDataDocument> Poskytuje relační přístup k datům. <xref:System.Xml.XmlDataDocument> Mapuje XML na relační data v ADO.NET <xref:System.Data.DataSet>. Jakákoli .NET Frameworková aplikace může použít třídy v <xref:System.Xml> oboru názvů pro přístup k dokumentům XML a relačním datům v. <xref:System.Xml.XmlDataDocument> Tato implementace podporuje n-vrstvé architektury pro shromažďování a distribuci dat. Další informace najdete v tématu [integrace XML s relačními daty a ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md).  
  
## <a name="see-also"></a>Viz také

- [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
