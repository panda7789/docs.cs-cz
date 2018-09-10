---
title: Fragment stromu výsledků v transformacích
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: df363480-ba02-4233-9ddf-8434e421c4f1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 10449867a37863798a0da2df9111bcd7addfc6ef
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44269173"
---
# <a name="result-tree-fragment-in-transformations"></a><span data-ttu-id="8289e-102">Fragment stromu výsledků v transformacích</span><span class="sxs-lookup"><span data-stu-id="8289e-102">Result Tree Fragment in Transformations</span></span>

> [!NOTE]
> <span data-ttu-id="8289e-103"><xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8289e-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="8289e-104">Můžete provádět rozšiřitelný jazyk šablony stylů transformace XSLT () transformaci pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="8289e-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="8289e-105">Zobrazit [používání třídy XslCompiledTransform](using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](migrating-from-the-xsltransform-class.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="8289e-105">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>

 <span data-ttu-id="8289e-106">Fragmenty stromu výsledek, označované také jako fragmenty stromu výsledek nejsou nic jiného než speciální typ sady uzlů.</span><span class="sxs-lookup"><span data-stu-id="8289e-106">Result tree fragments, also known as result tree fragments, are nothing more than a special type of node set.</span></span> <span data-ttu-id="8289e-107">Všechny funkce můžete provádět s nimi, které lze provést na sadu uzlu.</span><span class="sxs-lookup"><span data-stu-id="8289e-107">You can perform any function on them that can be performed on a node set.</span></span> <span data-ttu-id="8289e-108">Nebo můžete také převést fragment stromu výsledek uzel sady s použitím `node-set()` funkce a následně ji jakéhokoli místa, že sada uzlů je možné použít.</span><span class="sxs-lookup"><span data-stu-id="8289e-108">Or, you can also convert a result tree fragment to a node set using the `node-set()` function and subsequently use it any place that a node set can be used.</span></span>

 <span data-ttu-id="8289e-109">Fragment stromu výsledek je vytvořen pomocí `<xsl:variable>` nebo `<xsl:param>` element specifickým způsobem v šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="8289e-109">A result tree fragment is created as a result of using an `<xsl:variable>` or `<xsl:param>` element in a specific manner in a style sheet.</span></span> <span data-ttu-id="8289e-110">Syntaxe `variable` a `parameter` prvky vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="8289e-110">The syntax for the `variable` and `parameter` elements is as follows:</span></span>

```xml
<xsl:param name=Qname select= XPath Expression >
    template body
</xsl:param>

<xsl:variable name=Qname select=XPath Expression >
    template body
</xsl:variable>
```

<span data-ttu-id="8289e-111">Pro `parameter` elementu, je hodnota přiřazena kvalifikovaný název (`Qname`) několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="8289e-111">For the `parameter` element, the value is assigned to the qualified name (`Qname`) in several ways.</span></span> <span data-ttu-id="8289e-112">Můžete přiřadit výchozí hodnotu parametru tak, že vrací obsah z výraz jazyk XML Path (XPath) v `select` atribut, nebo za její přiřazení obsahu těla šablony.</span><span class="sxs-lookup"><span data-stu-id="8289e-112">You can assign a default value to the parameter by returning content from the XML Path Language (XPath) expression in the `select` attribute, or by assigning it the contents of the template body.</span></span>

<span data-ttu-id="8289e-113">Pro `variable` elementu, hodnota je také přiřazený několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="8289e-113">For the `variable` element, the value is also assigned in several ways.</span></span> <span data-ttu-id="8289e-114">Vrácením obsahu z výrazu XPath v ji můžete přiřadit `select` atribut, nebo za její přiřazení obsahu těla šablony.</span><span class="sxs-lookup"><span data-stu-id="8289e-114">You can assign it by returning content from the XPath expression in the `select` attribute, or by assigning it the contents of the template body.</span></span>

<span data-ttu-id="8289e-115">Pro obě `parameter` a `variable` prvky, pokud je hodnota přiřazena pomocí výrazu XPath, pak jednu z čtyři základní typy jazyka XPath bude vrácen: logická hodnota, řetězec, číslo nebo uzel nastavení.</span><span class="sxs-lookup"><span data-stu-id="8289e-115">For both the `parameter` and `variable` elements, if a value is assigned by the XPath expression, then one of the four basic XPath types will be returned: Boolean, string, number, or node set.</span></span> <span data-ttu-id="8289e-116">Pokud hodnota je uvedená pomocí prázdné šablony textu, pak je vrácený datový typ výraz XPath a bude fragment stromu výsledek.</span><span class="sxs-lookup"><span data-stu-id="8289e-116">When the value is given by using a non-empty template body, then a non-XPath data type is returned, and that will be a result tree fragment.</span></span>

<span data-ttu-id="8289e-117">Pokud proměnná je vázán k fragment stromu výsledek místo jedné z čtyři základní typy dat XPath, pak toto je pouze, že dotaz XPath vrátí typ, který není jedním ze čtyř typů objektů jazyka XPath.</span><span class="sxs-lookup"><span data-stu-id="8289e-117">When a variable is bound to a result tree fragment instead of one of the four basic XPath data types, this is the only time that an XPath query returns a type that is not one of the four XPath object types.</span></span> <span data-ttu-id="8289e-118">Jejich chování a výsledků fragmenty jsou popsány v [specifikace World Wide Web Consortium (W3C)](https://www.w3.org/TR/xslt-10/), [části 11.1 výsledků fragmenty](https://www.w3.org/TR/xslt-10/#section-Result-Tree-Fragments) prostřednictvím [části 11.6 předávání Parametry šablony](https://www.w3.org/TR/xslt-10/#section-Passing-Parameters-to-Templates).</span><span class="sxs-lookup"><span data-stu-id="8289e-118">Result tree fragments and their behavior are discussed in the [World Wide Web Consortium (W3C) specification](https://www.w3.org/TR/xslt-10/), [section 11.1 Result Tree Fragments](https://www.w3.org/TR/xslt-10/#section-Result-Tree-Fragments) through [section 11.6 Passing Parameters to Templates](https://www.w3.org/TR/xslt-10/#section-Passing-Parameters-to-Templates).</span></span> <span data-ttu-id="8289e-119">Navíc [části 1 Úvod](https://www.w3.org/TR/xslt-10/#section-Introduction) popisuje, jak šablony může obsahovat elementy z oboru názvů XSLT, které vrátí nebo vytvoří výsledků fragmenty stromu.</span><span class="sxs-lookup"><span data-stu-id="8289e-119">Also, [section 1 Introduction](https://www.w3.org/TR/xslt-10/#section-Introduction) discusses how templates can contain elements from the XSLT namespace that return or create result tree fragments.</span></span>

<span data-ttu-id="8289e-120">Fragment stromu výsledek koncept, se chová jako uzel nastavení, není nic víc než jeden kořenový uzel.</span><span class="sxs-lookup"><span data-stu-id="8289e-120">A result tree fragment, in concept, behaves like a node set with nothing more than a single root node.</span></span> <span data-ttu-id="8289e-121">Ostatní uzly vrátil jsou však podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="8289e-121">However, the rest of the nodes returned are child nodes.</span></span> <span data-ttu-id="8289e-122">Programově zobrazit podřízené uzly, zkopírujte do stromu výsledek pomocí stromu fragmentu výsledek `<xsl:copy-of>` elementu.</span><span class="sxs-lookup"><span data-stu-id="8289e-122">To programmatically see the child nodes, copy the result tree fragment to the result tree using the `<xsl:copy-of>` element.</span></span> <span data-ttu-id="8289e-123">Při kopírování sady se provádí, všechny podřízené uzly jsou zkopírovány také do stromu výsledek v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="8289e-123">When the copy-of is performed, all the child nodes are also copied to the result tree in sequence.</span></span> <span data-ttu-id="8289e-124">Dokud `copy` nebo `copy-of` se používá, fragment stromu výsledek není součástí stromu výsledek nebo výstup z transformace.</span><span class="sxs-lookup"><span data-stu-id="8289e-124">Until a `copy` or `copy-of` is used, a result tree fragment is not part of the result tree or the output from the transformation.</span></span>

<span data-ttu-id="8289e-125">K iteraci přes vrácená uzlů fragment stromu výsledek <xref:System.Xml.XPath.XPathNavigator> se používá.</span><span class="sxs-lookup"><span data-stu-id="8289e-125">To iterate over the returned nodes of a result tree fragment, an <xref:System.Xml.XPath.XPathNavigator> is used.</span></span> <span data-ttu-id="8289e-126">Následující příklad kódu ukazuje, jak vytvořit fragment stromu výsledek předloze se styly voláním funkce s parametrem `fragment`, který obsahuje XML.</span><span class="sxs-lookup"><span data-stu-id="8289e-126">The following code sample shows how to create a result tree fragment within a style sheet by calling the function with a parameter `fragment`, which contains XML.</span></span>

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

<span data-ttu-id="8289e-127">Tady je další ukázku zobrazující proměnnou, která je ve formátu RTF (RICH Text Format), a proto nastavení typu stromu fragmentu výsledek, který není převedena na uzlu.</span><span class="sxs-lookup"><span data-stu-id="8289e-127">Here is another sample showing a variable, which is in Rich Text Format (RTF), and hence, a type of result tree fragment, that is not converted to a node set.</span></span> <span data-ttu-id="8289e-128">Místo toho je předán do funkce skriptu a <xref:System.Xml.XPath.XPathNavigator> slouží k navigaci v uzlech.</span><span class="sxs-lookup"><span data-stu-id="8289e-128">Instead, it is passed to a script function, and the <xref:System.Xml.XPath.XPathNavigator> is used to navigate over the nodes.</span></span>

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

<span data-ttu-id="8289e-129">Výsledek transformace všechny XML pomocí této šablony stylů se zobrazí následující výstup.</span><span class="sxs-lookup"><span data-stu-id="8289e-129">The result of transforming any XML with this style sheet is shown in the following output.</span></span>

## <a name="output"></a><span data-ttu-id="8289e-130">Výstup</span><span class="sxs-lookup"><span data-stu-id="8289e-130">Output</span></span>

```xml
<first_book xmlns:user="urn:books">Book1</first_book>
```

<span data-ttu-id="8289e-131">Jak je uvedeno výše, `node-set` funkce lze převést na sadu uzlu fragment stromu výsledek.</span><span class="sxs-lookup"><span data-stu-id="8289e-131">As stated above, the `node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="8289e-132">Výsledný uzel vždy obsahuje jeden uzel, který je kořenový uzel stromu.</span><span class="sxs-lookup"><span data-stu-id="8289e-132">The resulting node always contains a single node that is the root node of the tree.</span></span> <span data-ttu-id="8289e-133">Pokud převedete fragment výsledkového stromu na uzel nastavena, pak jste ji mohli používat kdekoli sadu regulární uzlu se používá, například jako v pro každý příkaz nebo v hodnotě `select` atribut.</span><span class="sxs-lookup"><span data-stu-id="8289e-133">If you convert a result tree fragment to a node set, then you can use it anywhere a regular node set is used, such as in a for-each statement or in the value of a `select` attribute.</span></span> <span data-ttu-id="8289e-134">Následující řádky kódu zobrazit fragment převáděn na nastavit a použít jako sada uzlů uzlu:</span><span class="sxs-lookup"><span data-stu-id="8289e-134">The following lines of code show the fragment being converted to a node set and used as a node set:</span></span>

`<xsl:for-each select="msxsl:node-set($node-fragment)">`

`<xsl:value-of select="user:func(msxsl:node-set($node-fragment))"/>`

<span data-ttu-id="8289e-135">Když fragment je převést na sadu uzlu, kterou již nebudete používat <xref:System.Xml.XPath.XPathNavigator> přejít nad ním.</span><span class="sxs-lookup"><span data-stu-id="8289e-135">When a fragment is converted to a node set, you no longer use the <xref:System.Xml.XPath.XPathNavigator> to navigate over it.</span></span> <span data-ttu-id="8289e-136">Pro sadu uzlu, je použít <xref:System.Xml.XPath.XPathNodeIterator> místo.</span><span class="sxs-lookup"><span data-stu-id="8289e-136">For a node set, you use the <xref:System.Xml.XPath.XPathNodeIterator> instead.</span></span>

<span data-ttu-id="8289e-137">V následujícím příkladu `$var` je proměnná, která je uzel stromu v šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="8289e-137">In the following example, `$var` is a variable that is a node tree in the style sheet.</span></span> <span data-ttu-id="8289e-138">Pro každý příkaz v kombinaci s `node-set` fungovala, umožňuje uživateli k iteraci přes tento strom jako sada uzlů.</span><span class="sxs-lookup"><span data-stu-id="8289e-138">The for-each statement, combined with the `node-set` function, allows the user to iterate over this tree as a node set.</span></span>

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

<span data-ttu-id="8289e-139">Tady je další příklad proměnné, která je ve formátu RTF, a proto z modulu snap-in fragment stromu výsledek typu, který je převeden na uzel nastaven před předáním funkci skript tak, aby objekt XPathNodeIterator.</span><span class="sxs-lookup"><span data-stu-id="8289e-139">Here is another example of a variable that is in RTF, and hence of type result tree fragment, that is converted to a node set before being passed to a script function as XPathNodeIterator.</span></span>

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

<span data-ttu-id="8289e-140">Výsledek transformace XML pomocí této šablony stylů je následující:</span><span class="sxs-lookup"><span data-stu-id="8289e-140">The following is the result of transforming XML with this style sheet:</span></span>

```xml
<books xmlns:user="urn:books">Book1Book2Book3Book4</books>
```

## <a name="see-also"></a><span data-ttu-id="8289e-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8289e-141">See also</span></span>

- <xref:System.Xml.XPath.XPathNodeIterator>  
- <xref:System.Xml.XPath.XPathNodeIterator>  
- [<span data-ttu-id="8289e-142">Transformace XSLT s třídou XslTransform</span><span class="sxs-lookup"><span data-stu-id="8289e-142">XSLT Transformations with the XslTransform Class</span></span>](xslt-transformations-with-the-xsltransform-class.md)  
- [<span data-ttu-id="8289e-143">Třída XslTransform implementuje procesor XSLT</span><span class="sxs-lookup"><span data-stu-id="8289e-143">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)  
