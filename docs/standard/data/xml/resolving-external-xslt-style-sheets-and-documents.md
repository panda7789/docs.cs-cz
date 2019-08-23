---
title: Překlad externích šablon stylů a dokumentů XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 920cfe3b-d525-4bb2-abf6-9431651f9cf9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 381b7c1eb091bafbcdc8ea842597c539c6be3a57
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945634"
---
# <a name="resolving-external-xslt-style-sheets-and-documents"></a>Překlad externích šablon stylů a dokumentů XSLT
V průběhu transformace se může několikrát vyhodnotit, když budete potřebovat přeložit externí prostředky.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá v .NET Framework 2,0. Transformace XSLT (Extensible Stylesheet Language) můžete použít k <xref:System.Xml.Xsl.XslCompiledTransform> transformaci pomocí třídy.  
  
 V průběhu transformace se může několikrát vyhodnotit, když budete potřebovat vyřešit externí prostředky:  
  
- <xref:System.Xml.Xsl.XslTransform.Load%2A> Při hledání externího listu stylů.  
  
- V <xref:System.Xml.Xsl.XslTransform.Load%2A> průběhu vyřešte `<xsl:include>` všechny `<xsl:import>` prvky nebo nalezené v šabloně stylů.  
  
- Během <xref:System.Xml.Xsl.XslTransform.Transform%2A> řešení všech `document()` funkcí.  
  
## <a name="using-the-xmlresolver-class"></a>Použití třídy objekt XmlResolver  
 Pokud je vyžadováno ověřování pro přístup k síťovému prostředku, použijte <xref:System.Xml.Xsl.XslTransform.Load%2A> metody, které <xref:System.Xml.XmlResolver> mají parametr pro předání <xref:System.Xml.XmlResolver> objektu, který má nastavené vlastnosti nezbytných přihlašovacích údajů.  
  
 Máte-li vlastní <xref:System.Xml.XmlResolver> , který chcete použít, nebo pokud potřebujete zadat jiné přihlašovací údaje, v závislosti na tom, kdy externí prostředek potřebuje řešení, je v následující tabulce uvedena požadovaná úloha.  
  
|Jaký proces vyžaduje řešení|Je vyžadován úkol|  
|--------------------------------------|-------------------|  
|Během <xref:System.Xml.Xsl.XslTransform.Load%2A> hledání předlohy se styly.|Zadejte přetíženou <xref:System.Xml.Xsl.XslTransform.Load%2A> metodu, která přebírá jako parametr <xref:System.Xml.XmlResolver> , pokud je šablona stylů na prostředku, který vyžaduje přihlašovací údaje.|  
|Během <xref:System.Xml.Xsl.XslTransform.Load%2A> řešení `<xsl:include>` nebo .`<xsl:import>`|Zadejte přetíženou <xref:System.Xml.Xsl.XslTransform.Load%2A> metodu, která přijímá jako parametr <xref:System.Xml.XmlResolver>. Slouží k načtení šablon stylů, na které odkazují `import` příkazy nebo `include`. <xref:System.Xml.XmlResolver> Pokud předáte `null`, externí prostředky nebudou vyřešeny.|  
|Během transformace k vyřešení jakýchkoli `document()` funkcí.|Určete při transformaci <xref:System.Xml.Xsl.XslTransform.Transform%2A> pomocí metody, která přebírá <xref:System.Xml.XmlResolver> argument. <xref:System.Xml.XmlResolver>|  
  
 `document()` Funkce načte další prostředky XML ze šablon stylů kromě počátečních dat XML poskytnutých vstupním datovým proudem. Vzhledem k tomu, že tato funkce umožňuje zahrnutí dat XML, která lze umístit jinde <xref:System.Xml.XmlResolver> , a `null` s hodnotou poskytnutou <xref:System.Xml.Xsl.XslTransform.Transform%2A> metodě brání `document()` spuštění funkce. Chcete-li použít `document()` funkci, <xref:System.Xml.Xsl.XslTransform.Transform%2A> použijte metodu, která přijímá <xref:System.Xml.XmlResolver> jako parametr, kromě toho, že má odpovídající sadu oprávnění.  
  
 Další informace o <xref:System.Xml.Xsl.XslTransform.Load%2A> metodě a jejím použití <xref:System.Xml.XmlResolver>naleznete v tématu <xref:System.Xml.Xsl.XslTransform.Load%28System.String%2CSystem.Xml.XmlResolver%29?displayProperty=nameWithType>.  
  
 Při volání <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody se oprávnění vypočítávají proti legitimaci poskytnuté v době načítání a tato sada oprávnění je přiřazena k celému procesu transformace. Pokud se `document()` funkce pokusí zahájit akci, která vyžaduje oprávnění, která nebyla v sadě nalezena, je vyvolána výjimka.  
  
## <a name="see-also"></a>Viz také:

- [Transformace XSLT s třídou XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
- [Výstupy z XslTransform](../../../../docs/standard/data/xml/outputs-from-an-xsltransform.md)
- [Transformace XSLT v různých úložištích](../../../../docs/standard/data/xml/xslt-transformations-over-different-stores.md)
- [XsltArgumentList pro parametry šablon stylů a objektů rozšíření](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md)
- [Skriptování šablony stylů XSLT \<pomocí msxsl: skript >](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md)
- [Podpora pro funkci msxsl:node-set()](../../../../docs/standard/data/xml/support-for-the-msxsl-node-set-function.md)
- [XPathNavigator v transformacích](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [XPathNodeIterator v transformacích](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [Vstup XPathDocument do XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [Vstup XmlDataDocument do XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
- [Vstup XmlDocument do XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
