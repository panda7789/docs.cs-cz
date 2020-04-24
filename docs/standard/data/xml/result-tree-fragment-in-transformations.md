---
title: Fragment stromu výsledků v transformacích
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: df363480-ba02-4233-9ddf-8434e421c4f1
ms.openlocfilehash: e454c1194e8c280042857f106e22d0d0509417e3
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156358"
---
# <a name="result-tree-fragment-in-transformations"></a><span data-ttu-id="389d6-102">Fragment stromu výsledků v transformacích</span><span class="sxs-lookup"><span data-stu-id="389d6-102">Result Tree Fragment in Transformations</span></span>

> [!NOTE]
> <span data-ttu-id="389d6-103"><xref:System.Xml.Xsl.XslTransform> Třída je zastaralá v .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="389d6-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="389d6-104">Transformace XSLT (Extensible Stylesheet Language) můžete použít k <xref:System.Xml.Xsl.XslCompiledTransform> transformaci pomocí třídy.</span><span class="sxs-lookup"><span data-stu-id="389d6-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="389d6-105">Další informace najdete v tématu [použití třídy XslCompiledTransform](using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="389d6-105">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>

 <span data-ttu-id="389d6-106">Fragmenty stromové struktury výsledků, označované také jako fragmenty stromové struktury výsledků, nejsou žádné více než speciální typ sady uzlů.</span><span class="sxs-lookup"><span data-stu-id="389d6-106">Result tree fragments, also known as result tree fragments, are nothing more than a special type of node set.</span></span> <span data-ttu-id="389d6-107">Můžete na nich provádět libovolné funkce, které lze provést v sadě uzlů.</span><span class="sxs-lookup"><span data-stu-id="389d6-107">You can perform any function on them that can be performed on a node set.</span></span> <span data-ttu-id="389d6-108">Nebo můžete také převést fragment stromu výsledků na sadu uzlů pomocí `node-set()` funkce a následně jej použít na místo, kde lze použít sadu uzlů.</span><span class="sxs-lookup"><span data-stu-id="389d6-108">Or, you can also convert a result tree fragment to a node set using the `node-set()` function and subsequently use it any place that a node set can be used.</span></span>

 <span data-ttu-id="389d6-109">Fragment stromové struktury výsledek je vytvořen jako výsledek použití prvku `<xsl:variable>` nebo `<xsl:param>` v konkrétním způsobu v šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="389d6-109">A result tree fragment is created as a result of using an `<xsl:variable>` or `<xsl:param>` element in a specific manner in a style sheet.</span></span> <span data-ttu-id="389d6-110">Syntaxe pro prvky `variable` a `parameter` je následující:</span><span class="sxs-lookup"><span data-stu-id="389d6-110">The syntax for the `variable` and `parameter` elements is as follows:</span></span>

```xml
<xsl:param name=Qname select= XPath Expression >
    template body
</xsl:param>

<xsl:variable name=Qname select=XPath Expression >
    template body
</xsl:variable>
```

<span data-ttu-id="389d6-111">Pro `parameter` element je hodnota přiřazena k kvalifikovanému názvu (`Qname`) několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="389d6-111">For the `parameter` element, the value is assigned to the qualified name (`Qname`) in several ways.</span></span> <span data-ttu-id="389d6-112">Můžete určit výchozí hodnotu parametru vrácením obsahu z výrazu jazyka XML Path (XPath) v `select` atributu nebo přiřazením obsahu textu šablony.</span><span class="sxs-lookup"><span data-stu-id="389d6-112">You can assign a default value to the parameter by returning content from the XML Path Language (XPath) expression in the `select` attribute, or by assigning it the contents of the template body.</span></span>

<span data-ttu-id="389d6-113">Pro `variable` element je hodnota také přiřazena několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="389d6-113">For the `variable` element, the value is also assigned in several ways.</span></span> <span data-ttu-id="389d6-114">Můžete ji přiřadit vrácením obsahu z výrazu XPath v `select` atributu nebo přiřazením obsahu textu šablony.</span><span class="sxs-lookup"><span data-stu-id="389d6-114">You can assign it by returning content from the XPath expression in the `select` attribute, or by assigning it the contents of the template body.</span></span>

<span data-ttu-id="389d6-115">Pro elementy `parameter` a `variable` platí, že pokud je hodnota přiřazena pomocí výrazu XPath, pak bude vrácen jeden ze čtyř základních typů XPath: Boolean, String, Number nebo set Node.</span><span class="sxs-lookup"><span data-stu-id="389d6-115">For both the `parameter` and `variable` elements, if a value is assigned by the XPath expression, then one of the four basic XPath types will be returned: Boolean, string, number, or node set.</span></span> <span data-ttu-id="389d6-116">Pokud je hodnota zadána pomocí neprázdného těla šablony, pak je vrácen datový typ, který není XPath, a který bude fragmentem stromu výsledek.</span><span class="sxs-lookup"><span data-stu-id="389d6-116">When the value is given by using a non-empty template body, then a non-XPath data type is returned, and that will be a result tree fragment.</span></span>

<span data-ttu-id="389d6-117">Pokud je proměnná svázána s fragmentem stromu výsledek místo jednoho ze čtyř základních datových typů XPath, je to jediná doba, kterou dotaz XPath vrátí typ, který není jedním ze čtyř typů objektů XPath.</span><span class="sxs-lookup"><span data-stu-id="389d6-117">When a variable is bound to a result tree fragment instead of one of the four basic XPath data types, this is the only time that an XPath query returns a type that is not one of the four XPath object types.</span></span> <span data-ttu-id="389d6-118">Fragmenty stromu výsledků a jejich chování jsou popsány v tématu [specifikace konsorcium World Wide Web (W3C)](https://www.w3.org/TR/xslt-10/), [fragmenty stromu výsledků oddílu 11,1](https://www.w3.org/TR/xslt-10/#section-Result-Tree-Fragments) až do [části 11,6 předání parametrů do šablon](https://www.w3.org/TR/xslt-10/#section-Passing-Parameters-to-Templates).</span><span class="sxs-lookup"><span data-stu-id="389d6-118">Result tree fragments and their behavior are discussed in the [World Wide Web Consortium (W3C) specification](https://www.w3.org/TR/xslt-10/), [section 11.1 Result Tree Fragments](https://www.w3.org/TR/xslt-10/#section-Result-Tree-Fragments) through [section 11.6 Passing Parameters to Templates](https://www.w3.org/TR/xslt-10/#section-Passing-Parameters-to-Templates).</span></span> <span data-ttu-id="389d6-119">[Oddíl 1 Úvod](https://www.w3.org/TR/xslt-10/#section-Introduction) popisuje, jak šablony mohou obsahovat prvky z oboru názvů XSLT, který vrací nebo vytváří fragmenty stromu výsledků.</span><span class="sxs-lookup"><span data-stu-id="389d6-119">Also, [section 1 Introduction](https://www.w3.org/TR/xslt-10/#section-Introduction) discusses how templates can contain elements from the XSLT namespace that return or create result tree fragments.</span></span>

<span data-ttu-id="389d6-120">Fragment stromu výsledku v konceptu se chová jako sada uzlů s nevětším než jedním kořenovým uzlem.</span><span class="sxs-lookup"><span data-stu-id="389d6-120">A result tree fragment, in concept, behaves like a node set with nothing more than a single root node.</span></span> <span data-ttu-id="389d6-121">Zbývající uzly vráceny ale jsou podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="389d6-121">However, the rest of the nodes returned are child nodes.</span></span> <span data-ttu-id="389d6-122">Pro programové zobrazení podřízených uzlů zkopírujte fragment stromu výsledek do stromu výsledek pomocí `<xsl:copy-of>` elementu.</span><span class="sxs-lookup"><span data-stu-id="389d6-122">To programmatically see the child nodes, copy the result tree fragment to the result tree using the `<xsl:copy-of>` element.</span></span> <span data-ttu-id="389d6-123">Po provedení kopie jsou všechny podřízené uzly zkopírovány také do stromu výsledek v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="389d6-123">When the copy-of is performed, all the child nodes are also copied to the result tree in sequence.</span></span> <span data-ttu-id="389d6-124">Dokud se `copy` nepoužije nebo `copy-of` , fragment stromu výsledku není součástí stromu výsledku nebo výstupem transformace.</span><span class="sxs-lookup"><span data-stu-id="389d6-124">Until a `copy` or `copy-of` is used, a result tree fragment is not part of the result tree or the output from the transformation.</span></span>

<span data-ttu-id="389d6-125">Pro iteraci na vrácených uzlech fragmentu stromu výsledek <xref:System.Xml.XPath.XPathNavigator> se použije.</span><span class="sxs-lookup"><span data-stu-id="389d6-125">To iterate over the returned nodes of a result tree fragment, an <xref:System.Xml.XPath.XPathNavigator> is used.</span></span> <span data-ttu-id="389d6-126">Následující ukázka kódu ukazuje, jak vytvořit fragment stromu výsledku v rámci předlohy se styly voláním funkce s parametrem `fragment`, který obsahuje XML.</span><span class="sxs-lookup"><span data-stu-id="389d6-126">The following code sample shows how to create a result tree fragment within a style sheet by calling the function with a parameter `fragment`, which contains XML.</span></span>

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

<span data-ttu-id="389d6-127">Tady je další ukázka ukazující proměnnou, která je ve formátu RTF (Rich Text Format), a proto typ fragmentu stromu výsledků, který není převeden na sadu uzlů.</span><span class="sxs-lookup"><span data-stu-id="389d6-127">Here is another sample showing a variable, which is in Rich Text Format (RTF), and hence, a type of result tree fragment, that is not converted to a node set.</span></span> <span data-ttu-id="389d6-128">Místo toho je předán do funkce skriptu a <xref:System.Xml.XPath.XPathNavigator> používá se k procházení uzlů.</span><span class="sxs-lookup"><span data-stu-id="389d6-128">Instead, it is passed to a script function, and the <xref:System.Xml.XPath.XPathNavigator> is used to navigate over the nodes.</span></span>

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

<span data-ttu-id="389d6-129">Výsledek transformace jakéhokoli XML s touto šablonou stylů je zobrazen v následujícím výstupu.</span><span class="sxs-lookup"><span data-stu-id="389d6-129">The result of transforming any XML with this style sheet is shown in the following output.</span></span>

## <a name="output"></a><span data-ttu-id="389d6-130">Výstup</span><span class="sxs-lookup"><span data-stu-id="389d6-130">Output</span></span>

```xml
<first_book xmlns:user="urn:books">Book1</first_book>
```

<span data-ttu-id="389d6-131">Jak je uvedeno výše, `node-set` funkce umožňuje převést fragment stromu výsledků na sadu uzlů.</span><span class="sxs-lookup"><span data-stu-id="389d6-131">As stated above, the `node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="389d6-132">Výsledný uzel vždy obsahuje jeden uzel, který je kořenovým uzlem stromu.</span><span class="sxs-lookup"><span data-stu-id="389d6-132">The resulting node always contains a single node that is the root node of the tree.</span></span> <span data-ttu-id="389d6-133">Převedete-li fragment stromu výsledků na sadu uzlů, můžete jej použít kdekoli, kde je použita běžná sada uzlů, například v příkazu for-each nebo v hodnotě `select` atributu.</span><span class="sxs-lookup"><span data-stu-id="389d6-133">If you convert a result tree fragment to a node set, then you can use it anywhere a regular node set is used, such as in a for-each statement or in the value of a `select` attribute.</span></span> <span data-ttu-id="389d6-134">Následující řádky kódu znázorňují fragment, který je převeden na sadu uzlů a který se používá jako sada uzlů:</span><span class="sxs-lookup"><span data-stu-id="389d6-134">The following lines of code show the fragment being converted to a node set and used as a node set:</span></span>

`<xsl:for-each select="msxsl:node-set($node-fragment)">`

`<xsl:value-of select="user:func(msxsl:node-set($node-fragment))"/>`

<span data-ttu-id="389d6-135">Když je fragment převeden na sadu uzlů, již nebudete používat <xref:System.Xml.XPath.XPathNavigator> k procházení.</span><span class="sxs-lookup"><span data-stu-id="389d6-135">When a fragment is converted to a node set, you no longer use the <xref:System.Xml.XPath.XPathNavigator> to navigate over it.</span></span> <span data-ttu-id="389d6-136">V <xref:System.Xml.XPath.XPathNodeIterator> případě sady uzlů použijete místo něj.</span><span class="sxs-lookup"><span data-stu-id="389d6-136">For a node set, you use the <xref:System.Xml.XPath.XPathNodeIterator> instead.</span></span>

<span data-ttu-id="389d6-137">V následujícím příkladu `$var` je proměnná, která je stromem uzlu v šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="389d6-137">In the following example, `$var` is a variable that is a node tree in the style sheet.</span></span> <span data-ttu-id="389d6-138">Příkaz for-each v kombinaci s `node-set` funkcí umožňuje uživateli iterovat v rámci tohoto stromu jako sadu uzlů.</span><span class="sxs-lookup"><span data-stu-id="389d6-138">The for-each statement, combined with the `node-set` function, allows the user to iterate over this tree as a node set.</span></span>

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

<span data-ttu-id="389d6-139">Tady je další příklad proměnné, která je ve formátu RTF, a proto fragment stromu výsledku typu, která je převedená na uzel, než se předává do funkce skriptu jako objekt XPathNodeIterator.</span><span class="sxs-lookup"><span data-stu-id="389d6-139">Here is another example of a variable that is in RTF, and hence of type result tree fragment, that is converted to a node set before being passed to a script function as XPathNodeIterator.</span></span>

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

<span data-ttu-id="389d6-140">Následuje výsledek transformace XML s touto šablonou stylů:</span><span class="sxs-lookup"><span data-stu-id="389d6-140">The following is the result of transforming XML with this style sheet:</span></span>

```xml
<books xmlns:user="urn:books">Book1Book2Book3Book4</books>
```

## <a name="see-also"></a><span data-ttu-id="389d6-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="389d6-141">See also</span></span>

- <xref:System.Xml.XPath.XPathNodeIterator>
- [<span data-ttu-id="389d6-142">Transformace XSLT s třídou XslTransform</span><span class="sxs-lookup"><span data-stu-id="389d6-142">XSLT Transformations with the XslTransform Class</span></span>](xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="389d6-143">Třída XslTransform implementuje procesor XSLT</span><span class="sxs-lookup"><span data-stu-id="389d6-143">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
