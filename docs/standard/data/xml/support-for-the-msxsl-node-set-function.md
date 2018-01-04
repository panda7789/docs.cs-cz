---
title: "Podpora pro msxsl:node-set() – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0cbf517-d9f6-4097-9851-4fa62903decd
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7cd79acbdef09acb0a05c818d8358cd612c3bcdf
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="support-for-the-msxslnode-set-function"></a><span data-ttu-id="c0a39-102">Podpora pro msxsl:node-set() – funkce</span><span class="sxs-lookup"><span data-stu-id="c0a39-102">Support for the msxsl:node-set() Function</span></span>
<span data-ttu-id="c0a39-103">`msxsl:node-set` Funkce umožňuje převést fragment stromu výsledek sada uzlů.</span><span class="sxs-lookup"><span data-stu-id="c0a39-103">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="c0a39-104">Výsledný uzlu nastavení vždy obsahuje jeden uzel a je kořenový uzel stromu.</span><span class="sxs-lookup"><span data-stu-id="c0a39-104">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c0a39-105"><xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c0a39-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="c0a39-106">Můžete provést jazyk XSL pro transformace transformace XSLT () pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="c0a39-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="c0a39-107">V tématu [pomocí třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="c0a39-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="c0a39-108">`msxsl:node-set` Funkce umožňuje převést fragment stromu výsledek sada uzlů.</span><span class="sxs-lookup"><span data-stu-id="c0a39-108">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="c0a39-109">Výsledný uzlu nastavení vždy obsahuje jeden uzel a je kořenový uzel stromu.</span><span class="sxs-lookup"><span data-stu-id="c0a39-109">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0a39-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="c0a39-110">Example</span></span>  
 <span data-ttu-id="c0a39-111">V následujícím příkladu `$var` je proměnná, která je uzel stromu v šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="c0a39-111">In the following example, `$var` is a variable that is a node tree in the style sheet.</span></span> <span data-ttu-id="c0a39-112">Pro každý příkaz v kombinaci s `node-set` funkce umožňuje uživateli iterace v tohoto uzlu stromu jako sada uzlů.</span><span class="sxs-lookup"><span data-stu-id="c0a39-112">The for-each statement combined with the `node-set` function allows the user to iterate over this node tree as a node set.</span></span>  
  
## <a name="nodesetxsl"></a><span data-ttu-id="c0a39-113">NodeSet.xsl</span><span class="sxs-lookup"><span data-stu-id="c0a39-113">nodeset.xsl</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
                xmlns:user="http://www.contoso.com"  
                version="1.0">  
    <xsl:variable name="books">  
        <book author="Michael Howard">Writing Secure Code</book>  
        <book author="Michael Kay">XSLT Reference</book>  
    </xsl:variable>  
  
    <xsl:template match="/">  
        <authors>  
            <xsl:for-each select="msxsl:node-set($books)/book">   
                <author><xsl:value-of select="@author"/)</author>  
            </xsl:for-each>  
        </authors>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a><span data-ttu-id="c0a39-114">Výstup</span><span class="sxs-lookup"><span data-stu-id="c0a39-114">Output</span></span>  
 <span data-ttu-id="c0a39-115">Výstup transformace</span><span class="sxs-lookup"><span data-stu-id="c0a39-115">The output of the transformation is</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<authors><author>Michael Howard</author><author>Michael Kay</author></authors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c0a39-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0a39-116">See Also</span></span>  
 [<span data-ttu-id="c0a39-117">Třída XslTransform implementuje procesor XSLT</span><span class="sxs-lookup"><span data-stu-id="c0a39-117">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
