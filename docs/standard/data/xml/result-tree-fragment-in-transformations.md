---
title: Fragment stromu výsledek v transformace
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: df363480-ba02-4233-9ddf-8434e421c4f1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2c64baef3037cdb7b45ede3febacdbc1e76304c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574696"
---
# <a name="result-tree-fragment-in-transformations"></a><span data-ttu-id="c6d1c-102">Fragment stromu výsledek v transformace</span><span class="sxs-lookup"><span data-stu-id="c6d1c-102">Result Tree Fragment in Transformations</span></span>
> [!NOTE]
>  <span data-ttu-id="c6d1c-103"><xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c6d1c-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="c6d1c-104">Můžete provést jazyk XSL pro transformace transformace XSLT () pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="c6d1c-105">V tématu [pomocí třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-105">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="c6d1c-106">Výsledek stromu fragmenty, také známé jako výsledek stromu fragmenty, jsou nic jiného než zvláštním typem sada uzlů.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-106">Result tree fragments, also known as result tree fragments, are nothing more than a special type of node set.</span></span> <span data-ttu-id="c6d1c-107">Můžete provádět žádné funkce na nich, které lze provést na sada uzlů.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-107">You can perform any function on them that can be performed on a node set.</span></span> <span data-ttu-id="c6d1c-108">Nebo můžete také převést fragment výsledek stromu na uzel nastavit pomocí `node-set()` funkce a následně použít jakékoli místo lze sada uzlů.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-108">Or, you can also convert a result tree fragment to a node set using the `node-set()` function and subsequently use it any place that a node set can be used.</span></span>  
  
 <span data-ttu-id="c6d1c-109">Fragment stromu výsledek je vytvořen v důsledku použití `<xsl:variable>` nebo `<xsl:param>` element konkrétní způsobem v šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-109">A result tree fragment is created as a result of using an `<xsl:variable>` or `<xsl:param>` element in a specific manner in a style sheet.</span></span> <span data-ttu-id="c6d1c-110">Syntaxe `variable` a `parameter` elementy vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="c6d1c-110">The syntax for the `variable` and `parameter` elements is as follows:</span></span>  
  
```xml  
<xsl:param name=Qname select= XPath Expression >  
    template body  
</xsl:param>  
  
<xsl:variable name=Qname select=XPath Expression >  
    template body  
</xsl:variable>  
```  
  
 <span data-ttu-id="c6d1c-111">Pro `parameter` element, hodnota je přiřazen k úplný název (`Qname`) několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-111">For the `parameter` element, the value is assigned to the qualified name (`Qname`) in several ways.</span></span> <span data-ttu-id="c6d1c-112">Můžete přiřadit výchozí hodnotu parametru vrácením obsah z výrazu XML Path Language (XPath) v `select` atribut, nebo pomocí jeho přiřazení obsah textu šablony.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-112">You can assign a default value to the parameter by returning content from the XML Path Language (XPath) expression in the `select` attribute, or by assigning it the contents of the template body.</span></span>  
  
 <span data-ttu-id="c6d1c-113">Pro `variable` elementu, hodnota je také přiřazený několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-113">For the `variable` element, the value is also assigned in several ways.</span></span> <span data-ttu-id="c6d1c-114">Můžete je přiřadit vrácením obsah z výraz XPath v `select` atribut, nebo pomocí jeho přiřazení obsah textu šablony.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-114">You can assign it by returning content from the XPath expression in the `select` attribute, or by assigning it the contents of the template body.</span></span>  
  
 <span data-ttu-id="c6d1c-115">Pro oba `parameter` a `variable` prvky, pokud hodnota je přiřazena službou výraz XPath, pak jedním ze čtyř základních typů XPath, bude vrácen: logická hodnota, řetězec, číslo nebo uzel nastavit.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-115">For both the `parameter` and `variable` elements, if a value is assigned by the XPath expression, then one of the four basic XPath types will be returned: Boolean, string, number, or node set.</span></span> <span data-ttu-id="c6d1c-116">Pokud je zadána hodnota pomocí šablony neprázdný text vracen datový typ jiný XPath a který bude fragment stromu výsledek.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-116">When the value is given by using a non-empty template body, then a non-XPath data type is returned, and that will be a result tree fragment.</span></span>  
  
 <span data-ttu-id="c6d1c-117">Pokud proměnnou je vázán na fragment výsledek stromu místo jedním ze čtyř typů dat základní XPath, to je jenom jednou, dotaz XPath vrátí typ, který není jedním z čtyři typy objektů jazyka XPath.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-117">When a variable is bound to a result tree fragment instead of one of the four basic XPath data types, this is the only time that an XPath query returns a type that is not one of the four XPath object types.</span></span> <span data-ttu-id="c6d1c-118">Výsledek stromu fragmenty a jejich chování jsou popsané v specifikace World Wide Web Consortium (W3C) na www.w3.org/XSLT, část 11.1 výsledek stromu fragmenty prostřednictvím části 11.6 předání parametrů šablon.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-118">Result tree fragments and their behavior are discussed in the World Wide Web Consortium (W3C) specification at www.w3.org/XSLT, section 11.1 Result Tree Fragments through section 11.6 Passing Parameters to Templates.</span></span> <span data-ttu-id="c6d1c-119">Také část 1 Úvod popisuje, jak šablony může obsahovat elementy z oboru názvů XSLT, které vrátí nebo vytvoří výsledek fragmenty stromu.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-119">Also, section 1 Introduction discusses how templates can contain elements from the XSLT namespace that return or create result tree fragments.</span></span>  
  
 <span data-ttu-id="c6d1c-120">Fragment stromu výsledek koncept, se chová jako uzel s nic jiného než jediném kořenovém uzlu.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-120">A result tree fragment, in concept, behaves like a node set with nothing more than a single root node.</span></span> <span data-ttu-id="c6d1c-121">Zbývající uzly vrátil jsou však podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-121">However, the rest of the nodes returned are child nodes.</span></span> <span data-ttu-id="c6d1c-122">Podřízené uzly prostřednictvím kódu programu najdete zkopírujte fragment stromu výsledek výsledek stromu pomocí `<xsl:copy-of>` elementu.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-122">To programmatically see the child nodes, copy the result tree fragment to the result tree using the `<xsl:copy-of>` element.</span></span> <span data-ttu-id="c6d1c-123">Při kopírování z provádí, jsou všechny podřízené uzly také zkopírován do stromu výsledek v pořadí.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-123">When the copy-of is performed, all the child nodes are also copied to the result tree in sequence.</span></span> <span data-ttu-id="c6d1c-124">Dokud `copy` nebo `copy-of` se používá, fragment stromu výsledek není součástí stromu výsledek nebo výstup transformace.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-124">Until a `copy` or `copy-of` is used, a result tree fragment is not part of the result tree or the output from the transformation.</span></span>  
  
 <span data-ttu-id="c6d1c-125">Iterace nad vrácený uzly stromu fragment výsledek <xref:System.Xml.XPath.XPathNavigator> se používá.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-125">To iterate over the returned nodes of a result tree fragment, an <xref:System.Xml.XPath.XPathNavigator> is used.</span></span> <span data-ttu-id="c6d1c-126">Následující ukázka kódu ukazuje, jak vytvořit fragment výsledek stromové struktury v rámci šablony stylů voláním funkce s parametrem `fragment`, který obsahuje XML.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-126">The following code sample shows how to create a result tree fragment within a style sheet by calling the function with a parameter `fragment`, which contains XML.</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
                xmlns:user="http://www.adventure-works.com"  
                version="1.0">  
    <xsl:var name="fragment">  
        <node1>  
            <node2/>  
        </node1>  
    <xsl:var>  
  
  <msxsl:script language="C#" implements-prefix="user">  
    function NodeFragment(XPathNavigator nav)  
    {  
      if (nav.HasSelection == false)  
        XPathNavigator.MoveToNext();  
      return;  
    }  
  </msxsl:script>  
  
    <xsl:template match="/">  
            <xsl:value-of select="user:NodeFragment(msxml:node-set($fragment))"/>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
 <span data-ttu-id="c6d1c-127">Zde je další ukázku zobrazující proměnnou, která je ve formátu RTF (RICH Text Format), a proto nastavte typ fragment stromu výsledek, který není převeden do uzlu.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-127">Here is another sample showing a variable, which is in Rich Text Format (RTF), and hence, a type of result tree fragment, that is not converted to a node set.</span></span> <span data-ttu-id="c6d1c-128">Místo toho je předán do funkce skript a <xref:System.Xml.XPath.XPathNavigator> se používá k přejděte přes uzly.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-128">Instead, it is passed to a script function, and the <xref:System.Xml.XPath.XPathNavigator> is used to navigate over the nodes.</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
        xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
        xmlns:user="urn:books"  
        exclude-result-prefixes="msxsl">  
  
<xsl:output method="xml" indent="yes" omit-xml-declaration="yes"/>  
  
<xsl:variable name="node-fragment">  
    <book>Book1</book>  
    <book>Book2</book>  
    <book>Book3</book>  
    <book>Book4</book>  
</xsl:variable>  
  
<msxsl:script implements-prefix="user" language="c#">  
  
<![CDATA[  
    string func(XPathNavigator nav)  
    {  
        bool b = nav.MoveToFirstChild();  
        if (b)  
            return nav.Value;  
        else  
            return "Does not exist";  
    }  
  
]]>  
  
</msxsl:script>  
  
<xsl:template match="/">  
    <first_book>  
        <xsl:value-of select="user:func($node-fragment)"/>  
    </first_book>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
 <span data-ttu-id="c6d1c-129">Výsledek převod žádné XML pomocí této šablony stylů se zobrazí v následující výstup.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-129">The result of transforming any XML with this style sheet is shown in the following output.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c6d1c-130">Výstup</span><span class="sxs-lookup"><span data-stu-id="c6d1c-130">Output</span></span>  
  
```xml  
<first_book xmlns:user="urn:books">Book1</first_book>  
```  
  
 <span data-ttu-id="c6d1c-131">Jak jsme uvedli výše, `node-set` funkce umožňuje převést fragment stromu výsledek sada uzlů.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-131">As stated above, the `node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="c6d1c-132">Výsledný uzel vždy obsahuje jeden uzel, který je kořenový uzel stromu.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-132">The resulting node always contains a single node that is the root node of the tree.</span></span> <span data-ttu-id="c6d1c-133">Pokud převedete fragment výsledek stromu na uzel nastavit, a můžete ji použít kdekoli sada regulární uzlů se používá, například jako pro každý příkaz nebo v hodnotě `select` atribut.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-133">If you convert a result tree fragment to a node set, then you can use it anywhere a regular node set is used, such as in a for-each statement or in the value of a `select` attribute.</span></span> <span data-ttu-id="c6d1c-134">Následující řádky kódu ukazují fragment převáděn na uzlu nastavení a použita jako sada uzlů:</span><span class="sxs-lookup"><span data-stu-id="c6d1c-134">The following lines of code show the fragment being converted to a node set and used as a node set:</span></span>  
  
 `<xsl:for-each select="msxsl:node-set($node-fragment)">`  
  
 `<xsl:value-of select="user:func(msxsl:node-set($node-fragment))"/>`  
  
 <span data-ttu-id="c6d1c-135">Při převodu fragment sada uzlů, nadále používat <xref:System.Xml.XPath.XPathNavigator> přejděte nad ním.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-135">When a fragment is converted to a node set, you no longer use the <xref:System.Xml.XPath.XPathNavigator> to navigate over it.</span></span> <span data-ttu-id="c6d1c-136">Pro sada uzlů můžete použít <xref:System.Xml.XPath.XPathNodeIterator> místo.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-136">For a node set, you use the <xref:System.Xml.XPath.XPathNodeIterator> instead.</span></span>  
  
 <span data-ttu-id="c6d1c-137">V následujícím příkladu `$var` je proměnná, která je uzel stromu v šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-137">In the following example, `$var` is a variable that is a node tree in the style sheet.</span></span> <span data-ttu-id="c6d1c-138">Příkaz pro každou kombinaci s `node-set` fungovat, umožňuje uživatelům Iterujte přes tento strom jako sada uzlů.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-138">The for-each statement, combined with the `node-set` function, allows the user to iterate over this tree as a node set.</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
                xmlns:user="http://www.adventure-works.com"  
                version="1.0">  
    <xsl:variable name="states">  
        <node1>AL</node1>  
        <node1>CA</node1>  
        <node1>CO</node1>  
        <node1>WA</node1>  
    </xsl:variable>  
  
    <xsl:template match="/">  
            <xsl:for-each select="msxsl:node-set($states)"/>   
    </xsl:template>  
</xsl:stylesheet>  
```  
  
 <span data-ttu-id="c6d1c-139">Dalším příkladem proměnné, která je ve formátu RTF, a proto fragment stromu výsledek typu, který je převést na uzlu nastavit před předáním funkce skriptu jako XPathNodeIterator.</span><span class="sxs-lookup"><span data-stu-id="c6d1c-139">Here is another example of a variable that is in RTF, and hence of type result tree fragment, that is converted to a node set before being passed to a script function as XPathNodeIterator.</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
        xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
        xmlns:user="urn:books"  
        exclude-result-prefixes="msxsl">  
  
<xsl:output method="xml" indent="yes" omit-xml-declaration="yes"/>  
  
<xsl:variable name="node-fragment">  
    <book>Book1</book>  
    <book>Book2</book>  
    <book>Book3</book>  
    <book>Book4</book>  
</xsl:variable>  
  
<msxsl:script implements-prefix="user" language="c#">  
  
<![CDATA[  
    string func(XPathNodeIterator it)  
    {  
        it.MoveNext();   
        return it.Current.Value;   
        //it.Current returns XPathNavigator positioned on the current node  
    }  
  
]]>  
  
</msxsl:script>  
<xsl:template match="/">  
    <books>  
        <xsl:value-of select="user:func(msxsl:node-set($node-fragment))"/>  
    </books>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
 <span data-ttu-id="c6d1c-140">Toto je výsledek transformace XML pomocí této šablony stylů:</span><span class="sxs-lookup"><span data-stu-id="c6d1c-140">The following is the result of transforming XML with this style sheet:</span></span>  
  
```xml  
<books xmlns:user="urn:books">Book1Book2Book3Book4</books>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c6d1c-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6d1c-141">See Also</span></span>  
 <xref:System.Xml.XPath.XPathNodeIterator>  
 <xref:System.Xml.XPath.XPathNodeIterator>  
 [<span data-ttu-id="c6d1c-142">Transformace XSLT s třídou XslTransform</span><span class="sxs-lookup"><span data-stu-id="c6d1c-142">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [<span data-ttu-id="c6d1c-143">Třída XslTransform implementuje procesor XSLT</span><span class="sxs-lookup"><span data-stu-id="c6d1c-143">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
