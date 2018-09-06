---
title: Sady uzlů v transformacích
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ad034f0e-ff8b-4a71-9a4c-528c754263c4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f33320603b175f04d0372fd5f2a2ee16d286d7b3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43866816"
---
# <a name="node-sets-in-transformations"></a><span data-ttu-id="2c5d0-102">Sady uzlů v transformacích</span><span class="sxs-lookup"><span data-stu-id="2c5d0-102">Node Sets in Transformations</span></span>
<span data-ttu-id="2c5d0-103">Sad uzlů jsou jedním z čtyři základní typy dat, které jsou vráceny z výrazů jazyk XML Path (XPath).</span><span class="sxs-lookup"><span data-stu-id="2c5d0-103">Node sets are one of four basic data types that are returned from XML Path Language (XPath) expressions.</span></span> <span data-ttu-id="2c5d0-104">Sada uzlů, které je neuspořádanou sadu uzlů bez duplicity, které jsou vytvořeny v pořadí dokumentů, je možné přiřadit k proměnné v šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="2c5d0-104">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c5d0-105"><xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2c5d0-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="2c5d0-106">Můžete provádět rozšiřitelný jazyk šablony stylů transformace XSLT () transformaci pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="2c5d0-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="2c5d0-107">Zobrazit [používání třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="2c5d0-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="2c5d0-108">Sad uzlů jsou jedním z čtyři základní typy dat, které jsou vráceny z výrazů XPath.</span><span class="sxs-lookup"><span data-stu-id="2c5d0-108">Node sets are one of four basic data types that are returned from XPath expressions.</span></span> <span data-ttu-id="2c5d0-109">Sada uzlů, které je neuspořádanou sadu uzlů bez duplicity, které jsou vytvořeny v pořadí dokumentů, je možné přiřadit k proměnné v šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="2c5d0-109">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span> <span data-ttu-id="2c5d0-110">Tento uzel sadu, která je výsledkem používaných pro výraz XPath `select` atribut v transformaci, má stejné chování jako uzel nastavení z XML Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="2c5d0-110">This node set, which is a result of an XPath expression used in a `select` attribute in a transformation, has the same behavior as a node set from the XML Document Object Model (DOM).</span></span> <span data-ttu-id="2c5d0-111">Sada s použitím sadu metod, které jsou zobrazeny v uzlu se můžete dostat [uzlu nastavení navigace pomocí XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), na rozdíl od fragment stromu výsledek nebo fragment stromu výsledek, který používá <xref:System.Xml.XPath.XPathNodeIterator> pro navigaci.</span><span class="sxs-lookup"><span data-stu-id="2c5d0-111">You can navigate a node set using a set of methods shown in [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), unlike a result tree fragment or result tree fragment, which uses the <xref:System.Xml.XPath.XPathNodeIterator> for navigation.</span></span>  
  
 <span data-ttu-id="2c5d0-112">Následující příklad kódu ukazuje, jak k iteraci přes uzel nastavena, když `variable` nebo `parameter` element v šabloně stylů je vyhodnocen jako sada uzlů.</span><span class="sxs-lookup"><span data-stu-id="2c5d0-112">The following code sample shows how to iterate over a node set when a `variable` or `parameter` element in a style sheet evaluates to a node set.</span></span>  
  
## <a name="style-sheet"></a><span data-ttu-id="2c5d0-113">Šablona stylů</span><span class="sxs-lookup"><span data-stu-id="2c5d0-113">Style Sheet</span></span>  
  
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
  
## <a name="input"></a><span data-ttu-id="2c5d0-114">Vstup</span><span class="sxs-lookup"><span data-stu-id="2c5d0-114">Input</span></span>  
  
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
  
## <a name="output"></a><span data-ttu-id="2c5d0-115">Výstup</span><span class="sxs-lookup"><span data-stu-id="2c5d0-115">Output</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2c5d0-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2c5d0-116">See also</span></span>

- <xref:System.Xml.XPath.XPathNodeIterator>  
- [<span data-ttu-id="2c5d0-117">Transformace XSLT s třídou XslTransform</span><span class="sxs-lookup"><span data-stu-id="2c5d0-117">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
- [<span data-ttu-id="2c5d0-118">Třída XslTransform implementuje procesor XSLT</span><span class="sxs-lookup"><span data-stu-id="2c5d0-118">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
