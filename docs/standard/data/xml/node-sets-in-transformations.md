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
ms.openlocfilehash: e4d6d2f5a68ce5cef9937edc136e52efcd5366df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="node-sets-in-transformations"></a><span data-ttu-id="dc4d6-102">Uzel nastaví v transformace</span><span class="sxs-lookup"><span data-stu-id="dc4d6-102">Node Sets in Transformations</span></span>
<span data-ttu-id="dc4d6-103">Nastavuje uzlu jsou jedním ze čtyř typů základní data, které jsou vráceny z výrazů XML Path Language (XPath).</span><span class="sxs-lookup"><span data-stu-id="dc4d6-103">Node sets are one of four basic data types that are returned from XML Path Language (XPath) expressions.</span></span> <span data-ttu-id="dc4d6-104">Sada uzlů, které je neuspořádaného kolekce, uzlů bez duplikáty, vytvořené v pořadí dokumentů, může být přiřazený k proměnné v šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="dc4d6-104">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc4d6-105"><xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dc4d6-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="dc4d6-106">Můžete provést jazyk XSL pro transformace transformace XSLT () pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="dc4d6-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="dc4d6-107">V tématu [pomocí třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="dc4d6-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="dc4d6-108">Nastavuje uzlu jsou jedním ze čtyř typů základní data, které jsou vráceny z výrazech XPath.</span><span class="sxs-lookup"><span data-stu-id="dc4d6-108">Node sets are one of four basic data types that are returned from XPath expressions.</span></span> <span data-ttu-id="dc4d6-109">Sada uzlů, které je neuspořádaného kolekce, uzlů bez duplikáty, vytvořené v pořadí dokumentů, může být přiřazený k proměnné v šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="dc4d6-109">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span> <span data-ttu-id="dc4d6-110">Tato sada uzlu, který je výsledkem v použit výraz XPath `select` atribut v transformaci, má stejné chování jako uzel nastavit z XML modelu DOM (Document Object).</span><span class="sxs-lookup"><span data-stu-id="dc4d6-110">This node set, which is a result of an XPath expression used in a `select` attribute in a transformation, has the same behavior as a node set from the XML Document Object Model (DOM).</span></span> <span data-ttu-id="dc4d6-111">Můžete přejít nastavit pomocí sady metody uvedené v uzlu [uzlu nastavit navigační pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), na rozdíl od výsledku stromu fragment nebo fragmentu stromu výsledek, který používá <xref:System.Xml.XPath.XPathNodeIterator> pro navigaci.</span><span class="sxs-lookup"><span data-stu-id="dc4d6-111">You can navigate a node set using a set of methods shown in [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), unlike a result tree fragment or result tree fragment, which uses the <xref:System.Xml.XPath.XPathNodeIterator> for navigation.</span></span>  
  
 <span data-ttu-id="dc4d6-112">Následující příklad kódu ukazuje, jak k iteraci přes uzel nastavena, když `variable` nebo `parameter` element v šabloně stylů vyhodnocen jako sada uzlů.</span><span class="sxs-lookup"><span data-stu-id="dc4d6-112">The following code sample shows how to iterate over a node set when a `variable` or `parameter` element in a style sheet evaluates to a node set.</span></span>  
  
## <a name="style-sheet"></a><span data-ttu-id="dc4d6-113">Šablony stylů</span><span class="sxs-lookup"><span data-stu-id="dc4d6-113">Style Sheet</span></span>  
  
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
  
## <a name="input"></a><span data-ttu-id="dc4d6-114">Vstup</span><span class="sxs-lookup"><span data-stu-id="dc4d6-114">Input</span></span>  
  
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
  
## <a name="output"></a><span data-ttu-id="dc4d6-115">Výstup</span><span class="sxs-lookup"><span data-stu-id="dc4d6-115">Output</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dc4d6-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc4d6-116">See Also</span></span>  
 <xref:System.Xml.XPath.XPathNodeIterator>  
 [<span data-ttu-id="dc4d6-117">Transformace XSLT pomocí XslTransform – třída</span><span class="sxs-lookup"><span data-stu-id="dc4d6-117">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [<span data-ttu-id="dc4d6-118">Třída XslTransform implementuje procesoru XSLT</span><span class="sxs-lookup"><span data-stu-id="dc4d6-118">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
