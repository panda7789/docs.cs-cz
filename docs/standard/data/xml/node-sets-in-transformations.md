---
title: "Uzel nastaví v transformace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad034f0e-ff8b-4a71-9a4c-528c754263c4
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 95df2f2888899093943feda35768694bf414de84
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="node-sets-in-transformations"></a>Uzel nastaví v transformace
Nastavuje uzlu jsou jedním ze čtyř typů základní data, které jsou vráceny z výrazů XML Path Language (XPath). Sada uzlů, které je neuspořádaného kolekce, uzlů bez duplikáty, vytvořené v pořadí dokumentů, může být přiřazený k proměnné v šabloně stylů.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Můžete provést jazyk XSL pro transformace transformace XSLT () pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy. V tématu [pomocí třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.  
  
 Nastavuje uzlu jsou jedním ze čtyř typů základní data, které jsou vráceny z výrazech XPath. Sada uzlů, které je neuspořádaného kolekce, uzlů bez duplikáty, vytvořené v pořadí dokumentů, může být přiřazený k proměnné v šabloně stylů. Tato sada uzlu, který je výsledkem v použit výraz XPath `select` atribut v transformaci, má stejné chování jako uzel nastavit z XML modelu DOM (Document Object). Můžete přejít nastavit pomocí sady metody uvedené v uzlu [uzlu nastavit navigační pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), na rozdíl od výsledku stromu fragment nebo fragmentu stromu výsledek, který používá <xref:System.Xml.XPath.XPathNodeIterator> pro navigaci.  
  
 Následující příklad kódu ukazuje, jak k iteraci přes uzel nastavena, když `variable` nebo `parameter` element v šabloně stylů vyhodnocen jako sada uzlů.  
  
## <a name="style-sheet"></a>Šablony stylů  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.XPath.XPathNodeIterator>  
 [Transformace XSLT s třídou XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
