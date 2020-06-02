---
title: Překlad externích šablon stylů a dokumentů XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 920cfe3b-d525-4bb2-abf6-9431651f9cf9
ms.openlocfilehash: 8e7f66d67f2520b47c30307a98ed2f3fb08455df
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291471"
---
# <a name="resolving-external-xslt-style-sheets-and-documents"></a>Překlad externích šablon stylů a dokumentů XSLT
V průběhu transformace se může několikrát vyhodnotit, když budete potřebovat přeložit externí prostředky.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform>Třída je zastaralá v .NET Framework 2,0. Transformace XSLT (Extensible Stylesheet Language) můžete použít k transformaci pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
 V průběhu transformace se může několikrát vyhodnotit, když budete potřebovat vyřešit externí prostředky:  
  
- Při <xref:System.Xml.Xsl.XslTransform.Load%2A> hledání externího listu stylů.  
  
- <xref:System.Xml.Xsl.XslTransform.Load%2A>V průběhu vyřešte `<xsl:include>` všechny `<xsl:import>` prvky nebo nalezené v šabloně stylů.  
  
- Během <xref:System.Xml.Xsl.XslTransform.Transform%2A> řešení všech `document()` funkcí.  
  
## <a name="using-the-xmlresolver-class"></a>Použití třídy objekt XmlResolver  
 Pokud je vyžadováno ověřování pro přístup k síťovému prostředku, použijte <xref:System.Xml.Xsl.XslTransform.Load%2A> metody, které mají <xref:System.Xml.XmlResolver> parametr pro předání <xref:System.Xml.XmlResolver> objektu, který má nastavené vlastnosti nezbytných přihlašovacích údajů.  
  
 Máte-li vlastní <xref:System.Xml.XmlResolver> , který chcete použít, nebo pokud potřebujete zadat jiné přihlašovací údaje, v závislosti na tom, kdy externí prostředek potřebuje řešení, je v následující tabulce uvedena požadovaná úloha.  
  
|Jaký proces vyžaduje řešení|Je vyžadován úkol|  
|--------------------------------------|-------------------|  
|Během <xref:System.Xml.Xsl.XslTransform.Load%2A> hledání předlohy se styly.|Zadejte přetíženou metodu, <xref:System.Xml.Xsl.XslTransform.Load%2A> která přebírá jako parametr, <xref:System.Xml.XmlResolver> Pokud je šablona stylů na prostředku, který vyžaduje přihlašovací údaje.|  
|Během <xref:System.Xml.Xsl.XslTransform.Load%2A> řešení `<xsl:include>` nebo `<xsl:import>` .|Zadejte přetíženou metodu, <xref:System.Xml.Xsl.XslTransform.Load%2A> která přijímá jako parametr <xref:System.Xml.XmlResolver> . <xref:System.Xml.XmlResolver>Slouží k načtení šablon stylů, na které odkazují `import` `include` příkazy nebo. Pokud předáte `null` , externí prostředky nebudou vyřešeny.|  
|Během transformace k vyřešení jakýchkoli `document()` funkcí.|Určete <xref:System.Xml.XmlResolver> při transformaci pomocí <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody, která přebírá <xref:System.Xml.XmlResolver> argument.|  
  
 `document()`Funkce načte další prostředky XML ze šablon stylů kromě počátečních dat XML poskytnutých vstupním datovým proudem. Vzhledem k tomu, že tato funkce umožňuje zahrnutí dat XML, která lze umístit jinde, a <xref:System.Xml.XmlResolver> s `null` hodnotou poskytnutou <xref:System.Xml.Xsl.XslTransform.Transform%2A> metodě brání `document()` spuštění funkce. Chcete-li použít `document()` funkci, použijte <xref:System.Xml.Xsl.XslTransform.Transform%2A> metodu, která přijímá <xref:System.Xml.XmlResolver> jako parametr, kromě toho, že má odpovídající sadu oprávnění.  
  
 Další informace o <xref:System.Xml.Xsl.XslTransform.Load%2A> metodě a jejím použití <xref:System.Xml.XmlResolver> naleznete v tématu <xref:System.Xml.Xsl.XslTransform.Load%28System.String%2CSystem.Xml.XmlResolver%29?displayProperty=nameWithType> .  
  
 Při <xref:System.Xml.Xsl.XslTransform.Transform%2A> volání metody se oprávnění vypočítávají proti legitimaci poskytnuté v době načítání a tato sada oprávnění je přiřazena k celému procesu transformace. Pokud se `document()` funkce pokusí zahájit akci, která vyžaduje oprávnění, která nebyla v sadě nalezena, je vyvolána výjimka.  
  
## <a name="see-also"></a>Viz také

- [Transformace XSLT s třídou XslTransform](xslt-transformations-with-the-xsltransform-class.md)
- [Třída XslTransform implementuje procesor XSLT](xsltransform-class-implements-the-xslt-processor.md)
- [Výstupy z XslTransform](outputs-from-an-xsltransform.md)
- [Transformace XSLT v různých úložištích](xslt-transformations-over-different-stores.md)
- [XsltArgumentList pro parametry šablon stylů a objektů rozšíření](xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md)
- [Skriptování šablony stylů XSLT pomocí\<msxsl:script>](xslt-stylesheet-scripting-using-msxsl-script.md)
- [Podpora pro funkci msxsl:node-set()](support-for-the-msxsl-node-set-function.md)
- [XPathNavigator v transformacích](xpathnavigator-in-transformations.md)
- [XPathNodeIterator v transformacích](xpathnodeiterator-in-transformations.md)
- [Vstup XPathDocument do XslTransform](xpathdocument-input-to-xsltransform.md)
- [Vstup XmlDataDocument do XslTransform](xmldatadocument-input-to-xsltransform.md)
- [Vstup XmlDocument do XslTransform](xmldocument-input-to-xsltransform.md)
