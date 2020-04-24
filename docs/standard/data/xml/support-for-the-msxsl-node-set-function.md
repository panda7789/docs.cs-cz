---
title: Podpora pro funkci msxsl:node-set()
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d0cbf517-d9f6-4097-9851-4fa62903decd
ms.openlocfilehash: 5022b298cb20796edbc54e951d8b06043697d832
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155591"
---
# <a name="support-for-the-msxslnode-set-function"></a><span data-ttu-id="9e70f-102">Podpora pro funkci msxsl:node-set()</span><span class="sxs-lookup"><span data-stu-id="9e70f-102">Support for the msxsl:node-set() Function</span></span>
<span data-ttu-id="9e70f-103">`msxsl:node-set` Funkce umožňuje převést fragment stromu výsledků na sadu uzlů.</span><span class="sxs-lookup"><span data-stu-id="9e70f-103">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="9e70f-104">Výsledná sada uzlů vždy obsahuje jeden uzel a je kořenovým uzlem stromu.</span><span class="sxs-lookup"><span data-stu-id="9e70f-104">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9e70f-105"><xref:System.Xml.Xsl.XslTransform> Třída je zastaralá v .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="9e70f-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="9e70f-106">Transformace XSLT (Extensible Stylesheet Language) můžete použít k <xref:System.Xml.Xsl.XslCompiledTransform> transformaci pomocí třídy.</span><span class="sxs-lookup"><span data-stu-id="9e70f-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="9e70f-107">Další informace najdete v tématu [použití třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="9e70f-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="9e70f-108">`msxsl:node-set` Funkce umožňuje převést fragment stromu výsledků na sadu uzlů.</span><span class="sxs-lookup"><span data-stu-id="9e70f-108">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="9e70f-109">Výsledná sada uzlů vždy obsahuje jeden uzel a je kořenovým uzlem stromu.</span><span class="sxs-lookup"><span data-stu-id="9e70f-109">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e70f-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="9e70f-110">Example</span></span>  
 <span data-ttu-id="9e70f-111">V následujícím příkladu `$var` je proměnná, která je stromem uzlu v šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="9e70f-111">In the following example, `$var` is a variable that is a node tree in the style sheet.</span></span> <span data-ttu-id="9e70f-112">Příkaz for-each v kombinaci s `node-set` funkcí umožňuje uživateli iterovat v rámci tohoto stromu uzlů jako sadu uzlů.</span><span class="sxs-lookup"><span data-stu-id="9e70f-112">The for-each statement combined with the `node-set` function allows the user to iterate over this node tree as a node set.</span></span>  
  
## <a name="nodesetxsl"></a><span data-ttu-id="9e70f-113">uzlů. xsl</span><span class="sxs-lookup"><span data-stu-id="9e70f-113">nodeset.xsl</span></span>  
  
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
  
## <a name="output"></a><span data-ttu-id="9e70f-114">Výstup</span><span class="sxs-lookup"><span data-stu-id="9e70f-114">Output</span></span>  
 <span data-ttu-id="9e70f-115">Výstup transformace je</span><span class="sxs-lookup"><span data-stu-id="9e70f-115">The output of the transformation is</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<authors><author>Michael Howard</author><author>Michael Kay</author></authors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9e70f-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e70f-116">See also</span></span>

- [<span data-ttu-id="9e70f-117">Třída XslTransform implementuje procesor XSLT</span><span class="sxs-lookup"><span data-stu-id="9e70f-117">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
