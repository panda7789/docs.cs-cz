---
title: Překlad externích šablon stylů a dokumentů XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 920cfe3b-d525-4bb2-abf6-9431651f9cf9
ms.openlocfilehash: 504519532d9a6988209cf04fd6b6196796f929f8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710294"
---
# <a name="resolving-external-xslt-style-sheets-and-documents"></a>Překlad externích šablon stylů a dokumentů XSLT
V průběhu transformace se může několikrát vyhodnotit, když budete potřebovat přeložit externí prostředky.  
  
> [!NOTE]
> Třída <xref:System.Xml.Xsl.XslTransform> je v .NET Framework 2,0 zastaralá. Pomocí třídy <xref:System.Xml.Xsl.XslCompiledTransform> můžete provádět transformace XSLT (Extensible Stylesheet Language).  
  
 V průběhu transformace se může několikrát vyhodnotit, když budete potřebovat vyřešit externí prostředky:  
  
- Během <xref:System.Xml.Xsl.XslTransform.Load%2A> vyhledat externí šablonu stylů.  
  
- Během <xref:System.Xml.Xsl.XslTransform.Load%2A> pro řešení `<xsl:include>` nebo `<xsl:import>` prvků nalezených v šabloně stylů.  
  
- Během <xref:System.Xml.Xsl.XslTransform.Transform%2A> vyřešit jakékoli `document()` funkce.  
  
## <a name="using-the-xmlresolver-class"></a>Použití třídy objekt XmlResolver  
 Pokud je vyžadováno ověřování pro přístup k síťovému prostředku, použijte <xref:System.Xml.Xsl.XslTransform.Load%2A> metody, které mají parametr <xref:System.Xml.XmlResolver> k předání objektu <xref:System.Xml.XmlResolver>, který má nastavené vlastnosti nezbytných přihlašovacích údajů.  
  
 Pokud máte vlastní <xref:System.Xml.XmlResolver>, kterou chcete použít, nebo pokud potřebujete zadat jiné přihlašovací údaje, v závislosti na tom, kdy externí prostředek potřebuje řešení, je v následující tabulce uveden požadovaný úkol.  
  
|Jaký proces vyžaduje řešení|Je vyžadován úkol|  
|--------------------------------------|-------------------|  
|Během <xref:System.Xml.Xsl.XslTransform.Load%2A> najít šablonu stylů.|Určete přetíženou <xref:System.Xml.Xsl.XslTransform.Load%2A> metodu, která přebírá jako parametr <xref:System.Xml.XmlResolver>, pokud je šablona stylů na prostředku, který vyžaduje přihlašovací údaje.|  
|Během <xref:System.Xml.Xsl.XslTransform.Load%2A> vyřešit `<xsl:include>` nebo `<xsl:import>`.|Zadejte přetíženou <xref:System.Xml.Xsl.XslTransform.Load%2A> metodu, která přijímá jako parametr <xref:System.Xml.XmlResolver>. <xref:System.Xml.XmlResolver> slouží k načtení šablon stylů, na které odkazují příkazy `import` nebo `include`. Pokud předáte `null`, externí prostředky se nevyřeší.|  
|Během transformace k vyřešení všech funkcí `document()`.|Zadejte <xref:System.Xml.XmlResolver> při transformaci pomocí metody <xref:System.Xml.Xsl.XslTransform.Transform%2A>, která přebírá <xref:System.Xml.XmlResolver> argument.|  
  
 Funkce `document()` načítá další prostředky XML ze šablon stylů kromě počátečních dat XML poskytnutých vstupním datovým proudem. Vzhledem k tomu, že tato funkce umožňuje zahrnutí dat XML, která lze umístit jinde, <xref:System.Xml.XmlResolver> s hodnotou `null` poskytnutou metodě <xref:System.Xml.Xsl.XslTransform.Transform%2A> brání spuštění funkce `document()`. Pokud chcete použít funkci `document()`, použijte metodu <xref:System.Xml.Xsl.XslTransform.Transform%2A>, která přebírá <xref:System.Xml.XmlResolver> jako parametr, kromě toho, že má příslušnou sadu oprávnění.  
  
 Další informace o metodě <xref:System.Xml.Xsl.XslTransform.Load%2A> a jejím použití <xref:System.Xml.XmlResolver>naleznete v tématu <xref:System.Xml.Xsl.XslTransform.Load%28System.String%2CSystem.Xml.XmlResolver%29?displayProperty=nameWithType>.  
  
 Při volání metody <xref:System.Xml.Xsl.XslTransform.Transform%2A> se oprávnění vypočítávají proti legitimaci poskytnuté v době načítání a tato sada oprávnění je přiřazena k celému procesu transformace. Pokud se funkce `document()` pokusí zahájit akci, která vyžaduje oprávnění, která nebyla v sadě nalezena, je vyvolána výjimka.  
  
## <a name="see-also"></a>Viz také:

- [Transformace XSLT s třídou XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
- [Výstupy z XslTransform](../../../../docs/standard/data/xml/outputs-from-an-xsltransform.md)
- [Transformace XSLT v různých úložištích](../../../../docs/standard/data/xml/xslt-transformations-over-different-stores.md)
- [XsltArgumentList pro parametry šablon stylů a objektů rozšíření](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md)
- [Skriptování šablony stylů XSLT pomocí \<msxsl: > skriptu](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md)
- [Podpora pro funkci msxsl:node-set()](../../../../docs/standard/data/xml/support-for-the-msxsl-node-set-function.md)
- [XPathNavigator v transformacích](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [XPathNodeIterator v transformacích](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [Vstup XPathDocument do XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [Vstup XmlDataDocument do XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
- [Vstup XmlDocument do XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
