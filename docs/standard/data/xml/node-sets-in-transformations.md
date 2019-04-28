---
title: Sady uzlů v transformacích
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ad034f0e-ff8b-4a71-9a4c-528c754263c4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 23632a5df10c1ab2d1afa654d5438a4ebd903d5f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698834"
---
# <a name="node-sets-in-transformations"></a>Sady uzlů v transformacích
Sad uzlů jsou jedním z čtyři základní typy dat, které jsou vráceny z výrazů jazyk XML Path (XPath). Sada uzlů, které je neuspořádanou sadu uzlů bez duplicity, které jsou vytvořeny v pořadí dokumentů, je možné přiřadit k proměnné v šabloně stylů.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Můžete provádět rozšiřitelný jazyk šablony stylů transformace XSLT () transformaci pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy. Zobrazit [používání třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.  
  
 Sad uzlů jsou jedním z čtyři základní typy dat, které jsou vráceny z výrazů XPath. Sada uzlů, které je neuspořádanou sadu uzlů bez duplicity, které jsou vytvořeny v pořadí dokumentů, je možné přiřadit k proměnné v šabloně stylů. Tento uzel sadu, která je výsledkem používaných pro výraz XPath `select` atribut v transformaci, má stejné chování jako uzel nastavení z XML Document Object Model (DOM). Sada s použitím sadu metod, které jsou zobrazeny v uzlu se můžete dostat [uzlu nastavení navigace pomocí XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), na rozdíl od fragment stromu výsledek nebo fragment stromu výsledek, který používá <xref:System.Xml.XPath.XPathNodeIterator> pro navigaci.  
  
 Následující příklad kódu ukazuje, jak k iteraci přes uzel nastavena, když `variable` nebo `parameter` element v šabloně stylů je vyhodnocen jako sada uzlů.  
  
## <a name="style-sheet"></a>Šablona stylů  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
  
    <xsl:variable name="x" select="bookstore/book/title"></xsl:variable>  
  
    <xsl:template match="/">  
        <xsl:for-each select="$x">  
            ******  
            <xsl:value-of select="."></xsl:value-of>  
            ******  
        </xsl:for-each>  
    </xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="input"></a>Vstup  
  
```xml  
<bookstore>  
   <book style="autobiography">  
      <title>Seven Years in Trenton</title>  
   </book>  
  
   <book style="autobiography">  
      <title>Seven Years in Trenton2</title>  
   </book>  
  
   <book style="textbook">  
      <title>History of Trenton Vol 3</title>  
   </book>  
</bookstore>  
```  
  
## <a name="output"></a>Výstup  
  
```  
******  
Seven Years in Trenton  
******  
  
******  
Seven Years in Trenton2  
******  
  
******  
History of Trenton Vol 3  
******  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XPath.XPathNodeIterator>
- [Transformace XSLT s třídou XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
