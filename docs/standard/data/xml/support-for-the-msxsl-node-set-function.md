---
title: Podpora pro funkci msxsl:node-set()
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d0cbf517-d9f6-4097-9851-4fa62903decd
ms.openlocfilehash: 747a0ff8c155f7635d5a6d2ebc76f287cf8646d4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291445"
---
# <a name="support-for-the-msxslnode-set-function"></a><span data-ttu-id="f417a-102">Podpora pro funkci msxsl:node-set()</span><span class="sxs-lookup"><span data-stu-id="f417a-102">Support for the msxsl:node-set() Function</span></span>
<span data-ttu-id="f417a-103">`msxsl:node-set`Funkce umožňuje převést fragment stromu výsledků na sadu uzlů.</span><span class="sxs-lookup"><span data-stu-id="f417a-103">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="f417a-104">Výsledná sada uzlů vždy obsahuje jeden uzel a je kořenovým uzlem stromu.</span><span class="sxs-lookup"><span data-stu-id="f417a-104">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f417a-105"><xref:System.Xml.Xsl.XslTransform>Třída je zastaralá v .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="f417a-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="f417a-106">Transformace XSLT (Extensible Stylesheet Language) můžete použít k transformaci pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="f417a-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="f417a-107">Další informace najdete v tématu [použití třídy XslCompiledTransform](using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="f417a-107">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="f417a-108">`msxsl:node-set`Funkce umožňuje převést fragment stromu výsledků na sadu uzlů.</span><span class="sxs-lookup"><span data-stu-id="f417a-108">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="f417a-109">Výsledná sada uzlů vždy obsahuje jeden uzel a je kořenovým uzlem stromu.</span><span class="sxs-lookup"><span data-stu-id="f417a-109">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f417a-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="f417a-110">Example</span></span>  
 <span data-ttu-id="f417a-111">V následujícím příkladu `$var` je proměnná, která je stromem uzlu v šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="f417a-111">In the following example, `$var` is a variable that is a node tree in the style sheet.</span></span> <span data-ttu-id="f417a-112">Příkaz for-each v kombinaci s `node-set` funkcí umožňuje uživateli iterovat v rámci tohoto stromu uzlů jako sadu uzlů.</span><span class="sxs-lookup"><span data-stu-id="f417a-112">The for-each statement combined with the `node-set` function allows the user to iterate over this node tree as a node set.</span></span>  
  
## <a name="nodesetxsl"></a><span data-ttu-id="f417a-113">uzlů. xsl</span><span class="sxs-lookup"><span data-stu-id="f417a-113">nodeset.xsl</span></span>  
  
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
                <author><xsl:value-of select="@author"/></author>  
            </xsl:for-each>  
        </authors>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a><span data-ttu-id="f417a-114">Výstup</span><span class="sxs-lookup"><span data-stu-id="f417a-114">Output</span></span>  
 <span data-ttu-id="f417a-115">Výstup transformace je</span><span class="sxs-lookup"><span data-stu-id="f417a-115">The output of the transformation is</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<authors><author>Michael Howard</author><author>Michael Kay</author></authors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f417a-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="f417a-116">See also</span></span>

- [<span data-ttu-id="f417a-117">Třída XslTransform implementuje procesor XSLT</span><span class="sxs-lookup"><span data-stu-id="f417a-117">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
