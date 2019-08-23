---
title: Sady uzlů v transformacích
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ad034f0e-ff8b-4a71-9a4c-528c754263c4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a84234ee797dac7487492dc92af2de4fa7ef503
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962551"
---
# <a name="node-sets-in-transformations"></a><span data-ttu-id="ee912-102">Sady uzlů v transformacích</span><span class="sxs-lookup"><span data-stu-id="ee912-102">Node Sets in Transformations</span></span>
<span data-ttu-id="ee912-103">Sady uzlů jsou jedním ze čtyř základních datových typů, které jsou vráceny ze výrazů jazyka XML Path (XPath).</span><span class="sxs-lookup"><span data-stu-id="ee912-103">Node sets are one of four basic data types that are returned from XML Path Language (XPath) expressions.</span></span> <span data-ttu-id="ee912-104">Sada uzlů, což je neuspořádaná kolekce uzlů bez duplicit, vytvořená v pořadí dokumentů, může být přiřazena proměnné v šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="ee912-104">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee912-105"><xref:System.Xml.Xsl.XslTransform> Třída je zastaralá v .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="ee912-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="ee912-106">Transformace XSLT (Extensible Stylesheet Language) můžete použít k <xref:System.Xml.Xsl.XslCompiledTransform> transformaci pomocí třídy.</span><span class="sxs-lookup"><span data-stu-id="ee912-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="ee912-107">Další informace najdete v tématu [použití třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="ee912-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="ee912-108">Sady uzlů jsou jedním ze čtyř základních datových typů, které jsou vráceny ze výrazů XPath.</span><span class="sxs-lookup"><span data-stu-id="ee912-108">Node sets are one of four basic data types that are returned from XPath expressions.</span></span> <span data-ttu-id="ee912-109">Sada uzlů, což je neuspořádaná kolekce uzlů bez duplicit, vytvořená v pořadí dokumentů, může být přiřazena proměnné v šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="ee912-109">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span> <span data-ttu-id="ee912-110">Tato sada uzlů, která je výsledkem výrazu XPath použitého v `select` atributu transformace, má stejné chování jako sada uzlů z XML model DOM (Document Object Model) (DOM).</span><span class="sxs-lookup"><span data-stu-id="ee912-110">This node set, which is a result of an XPath expression used in a `select` attribute in a transformation, has the same behavior as a node set from the XML Document Object Model (DOM).</span></span> <span data-ttu-id="ee912-111">Můžete procházet sadu uzlů pomocí sady metod, které jsou uvedeny v [uzlu nastavení navigace pomocí XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), na rozdíl od fragmentu stromu výsledku nebo fragmentu stromu výsledků, který používá <xref:System.Xml.XPath.XPathNodeIterator> pro navigaci.</span><span class="sxs-lookup"><span data-stu-id="ee912-111">You can navigate a node set using a set of methods shown in [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), unlike a result tree fragment or result tree fragment, which uses the <xref:System.Xml.XPath.XPathNodeIterator> for navigation.</span></span>  
  
 <span data-ttu-id="ee912-112">Následující ukázka kódu ukazuje, jak iterovat v rámci sady uzlů, když je `variable` element `parameter` nebo v šabloně stylů vyhodnocen jako sada uzlů.</span><span class="sxs-lookup"><span data-stu-id="ee912-112">The following code sample shows how to iterate over a node set when a `variable` or `parameter` element in a style sheet evaluates to a node set.</span></span>  
  
## <a name="style-sheet"></a><span data-ttu-id="ee912-113">Šablona stylů</span><span class="sxs-lookup"><span data-stu-id="ee912-113">Style Sheet</span></span>  
  
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
  
## <a name="input"></a><span data-ttu-id="ee912-114">Vstup</span><span class="sxs-lookup"><span data-stu-id="ee912-114">Input</span></span>  
  
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
  
## <a name="output"></a><span data-ttu-id="ee912-115">Výstup</span><span class="sxs-lookup"><span data-stu-id="ee912-115">Output</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ee912-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee912-116">See also</span></span>

- <xref:System.Xml.XPath.XPathNodeIterator>
- [<span data-ttu-id="ee912-117">Transformace XSLT s třídou XslTransform</span><span class="sxs-lookup"><span data-stu-id="ee912-117">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="ee912-118">Třída XslTransform implementuje procesor XSLT</span><span class="sxs-lookup"><span data-stu-id="ee912-118">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
