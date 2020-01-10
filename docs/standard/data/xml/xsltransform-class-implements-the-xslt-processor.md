---
title: Třída XslTransform implementuje procesor XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 88373fe2-4a6b-44f9-8a62-8a3e348e3a46
ms.openlocfilehash: 73a432db9a3fcb6587184e27e6dfe9ba49010e92
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709605"
---
# <a name="xsltransform-class-implements-the-xslt-processor"></a><span data-ttu-id="6f7c7-102">Třída XslTransform implementuje procesor XSLT</span><span class="sxs-lookup"><span data-stu-id="6f7c7-102">XslTransform Class Implements the XSLT Processor</span></span>

> [!NOTE]
> <span data-ttu-id="6f7c7-103">Třída <xref:System.Xml.Xsl.XslTransform> je v .NET Framework 2,0 zastaralá.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="6f7c7-104">Pomocí třídy <xref:System.Xml.Xsl.XslCompiledTransform> můžete provádět transformace XSLT (Extensible Stylesheet Language).</span><span class="sxs-lookup"><span data-stu-id="6f7c7-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="6f7c7-105">Další informace najdete v tématu [použití třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="6f7c7-105">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>

<span data-ttu-id="6f7c7-106">Třída <xref:System.Xml.Xsl.XslTransform> je procesor XSLT implementující doporučení XSL transformace (XSLT) verze 1,0.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-106">The <xref:System.Xml.Xsl.XslTransform> class is an XSLT processor implementing the XSL Transformations (XSLT) Version 1.0 recommendation.</span></span> <span data-ttu-id="6f7c7-107">Metoda <xref:System.Xml.Xsl.XslTransform.Load%2A> vyhledá a přečte šablony stylů a metoda <xref:System.Xml.Xsl.XslTransform.Transform%2A> transformuje daný zdrojový dokument.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-107">The <xref:System.Xml.Xsl.XslTransform.Load%2A> method locates and reads style sheets, and the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method transforms the given source document.</span></span> <span data-ttu-id="6f7c7-108">Jakékoli úložiště, které implementuje rozhraní <xref:System.Xml.XPath.IXPathNavigable>, lze použít jako zdrojový dokument pro <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-108">Any store that implements the <xref:System.Xml.XPath.IXPathNavigable> interface can be used as the source document for the <xref:System.Xml.Xsl.XslTransform>.</span></span> <span data-ttu-id="6f7c7-109">.NET Framework aktuálně implementuje rozhraní <xref:System.Xml.XPath.IXPathNavigable> na <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument>a <xref:System.Xml.XPath.XPathDocument>, takže všechny tyto hodnoty lze použít jako vstupní zdrojový dokument pro transformaci.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-109">The .NET Framework currently implements the <xref:System.Xml.XPath.IXPathNavigable> interface on the <xref:System.Xml.XmlDocument>, the <xref:System.Xml.XmlDataDocument>, and the <xref:System.Xml.XPath.XPathDocument>, so all of these can be used as the input source document to a transformation.</span></span>

<span data-ttu-id="6f7c7-110">Objekt <xref:System.Xml.Xsl.XslTransform> v .NET Framework podporuje pouze specifikaci XSLT 1,0, která je definována s následujícím oborem názvů:</span><span class="sxs-lookup"><span data-stu-id="6f7c7-110">The <xref:System.Xml.Xsl.XslTransform> object in the .NET Framework only supports the XSLT 1.0 specification, defined with the following namespace:</span></span>

```xml
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
```

<span data-ttu-id="6f7c7-111">Šablonu stylů lze načíst pomocí metody <xref:System.Xml.Xsl.XslTransform.Load%2A> z jedné z následujících tříd:</span><span class="sxs-lookup"><span data-stu-id="6f7c7-111">The style sheet can be loaded, using the <xref:System.Xml.Xsl.XslTransform.Load%2A> method, from one of the following classes:</span></span>

- <span data-ttu-id="6f7c7-112">Objekt</span><span class="sxs-lookup"><span data-stu-id="6f7c7-112">XPathNavigator</span></span>

- <span data-ttu-id="6f7c7-113">XmlReader</span><span class="sxs-lookup"><span data-stu-id="6f7c7-113">XmlReader</span></span>

- <span data-ttu-id="6f7c7-114">Řetězec představující adresu URL</span><span class="sxs-lookup"><span data-stu-id="6f7c7-114">A string representing a URL</span></span>

<span data-ttu-id="6f7c7-115">Pro každou z výše uvedených tříd Input existuje odlišná <xref:System.Xml.Xsl.XslTransform.Load%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-115">There is a different <xref:System.Xml.Xsl.XslTransform.Load%2A> method for each of the above input classes.</span></span> <span data-ttu-id="6f7c7-116">Některé metody přebírají kombinaci jedné z těchto tříd a třídu <xref:System.Xml.XmlResolver> jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-116">Some methods take in a combination of one of these classes and the <xref:System.Xml.XmlResolver> class as arguments.</span></span> <span data-ttu-id="6f7c7-117"><xref:System.Xml.XmlResolver> vyhledá prostředky, na které odkazuje `<xsl:import>` nebo `<xsl:include>` nalezené v šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-117">The <xref:System.Xml.XmlResolver> locates resources referenced by `<xsl:import>` or `<xsl:include>` found in the style sheet.</span></span> <span data-ttu-id="6f7c7-118">Následující metody přebírají jako vstup řetězec, <xref:System.Xml.XmlReader>nebo <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-118">The following methods take a string, <xref:System.Xml.XmlReader>, or <xref:System.Xml.XPath.XPathNavigator> as input.</span></span>

```vb
Overloads Public Sub Load(String)
```

```csharp
public void Load(string);
```

```vb
Overloads Public Sub Load(String, XmlResolver)
```

```csharp
public void Load(string, XmlResolver);
```

```vb
Overloads Public Sub Load(XmlReader, XmlResolver, Evidence)
```

```csharp
public void Load(XmlReader, XmlResolver, Evidence);
```

```vb
Overloads Public Sub Load(XPathNavigator, XmlResolver, Evidence)
```

```csharp
public void Load(XPathNavigator, XmlResolver, Evidence);
```

<span data-ttu-id="6f7c7-119">Většina výše uvedených metod <xref:System.Xml.Xsl.XslTransform.Load%2A> převezme <xref:System.Xml.XmlResolver> jako parametr.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-119">Most of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods shown above take an <xref:System.Xml.XmlResolver> as a parameter.</span></span> <span data-ttu-id="6f7c7-120"><xref:System.Xml.XmlResolver> slouží k načtení šablony stylů a všech šablon stylů, na které se odkazuje v elementech xsl: Import a xsl: include.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-120">The <xref:System.Xml.XmlResolver> is used to load the style sheet and any style sheet(s) referenced in xsl:import and xsl:include elements.</span></span>

<span data-ttu-id="6f7c7-121">Většina metod <xref:System.Xml.Xsl.XslTransform.Load%2A> také převezme legitimaci jako parametr.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-121">Most of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods also take evidence as a parameter.</span></span> <span data-ttu-id="6f7c7-122">Parametr legitimace je <xref:System.Security.Policy.Evidence>, která je přidružena k šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-122">The evidence parameter is the <xref:System.Security.Policy.Evidence> that is associated with the style sheet.</span></span> <span data-ttu-id="6f7c7-123">Úroveň zabezpečení šablon stylů má vliv na úroveň zabezpečení všech dalších prostředků, na které odkazuje, jako je například skript, který obsahuje, všechny `document()` funkce, které používá, a všechny objekty rozšíření používané <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-123">The security level of the style sheet affects the security level of any subsequent resources it references, such as the script it contains, any `document()` functions it uses, and any extension objects used by the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>

<span data-ttu-id="6f7c7-124">Pokud je šablona stylů načtena pomocí <xref:System.Xml.Xsl.XslTransform.Load%2A> metoda, která obsahuje parametr adresy URL a nejsou k dispozici žádné legitimace, je vypočítán důkaz pro šablonu stylů kombinací dané adresy URL k jejímu webu a zóně.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-124">If the style sheet is loaded using a <xref:System.Xml.Xsl.XslTransform.Load%2A> method that contains a URL parameter and no evidence is provided, the evidence of the style sheet is calculated by combining the given URL with its site and zone.</span></span>

<span data-ttu-id="6f7c7-125">Pokud nejsou zadány žádné identifikátory URI ani legitimace, pak je sada legitimace pro šablonu stylů plně důvěryhodná.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-125">If no URI or evidence is provided, then the evidence set for the style sheet is fully trusted.</span></span> <span data-ttu-id="6f7c7-126">Nečtěte šablony stylů z nedůvěryhodných zdrojů nebo přidejte nedůvěryhodné objekty rozšíření do <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-126">Do not load style sheets from untrusted sources, or add untrusted extension objects into the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>

<span data-ttu-id="6f7c7-127">Další informace o úrovních a důkazech zabezpečení a o tom, jak ovlivňují skriptování, najdete v tématu [skriptování XSLT XSLT pomocí \<msxsl: > skriptu](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md).</span><span class="sxs-lookup"><span data-stu-id="6f7c7-127">For more information about security levels and evidence and how it affects scripting, see [XSLT Stylesheet Scripting Using \<msxsl:script>](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md).</span></span> <span data-ttu-id="6f7c7-128">Informace o úrovních zabezpečení a legitimaci a o tom, jak ovlivňují objekty rozšíření, naleznete v tématu [třída XsltArgumentList pro parametry a objekty rozšíření šablon stylů](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).</span><span class="sxs-lookup"><span data-stu-id="6f7c7-128">For information about security levels and evidence and how it affects extension objects, see [XsltArgumentList for Style Sheet Parameters and Extension Objects](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).</span></span>

<span data-ttu-id="6f7c7-129">Informace o úrovních zabezpečení a legitimaci a o tom, jak ovlivňují funkci `document()`, naleznete v tématu [řešení externích šablon stylů XSLT a dokumentů](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md).</span><span class="sxs-lookup"><span data-stu-id="6f7c7-129">For information about security levels and evidence and how it affects the `document()` function, see [Resolving External XSLT Style Sheets and Documents](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md).</span></span>

<span data-ttu-id="6f7c7-130">Šablonu stylů lze zadat s počtem vstupních parametrů.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-130">A style sheet can be supplied with a number of input parameters.</span></span> <span data-ttu-id="6f7c7-131">Šablona stylů může také volat funkce objektů rozšíření.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-131">The style sheet can also call functions on extension objects.</span></span> <span data-ttu-id="6f7c7-132">Parametry a objekty rozšíření jsou dodány do předlohy stylů pomocí třídy <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-132">Both parameters and extension objects are supplied to the style sheet using the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span> <span data-ttu-id="6f7c7-133">Další informace o <xref:System.Xml.Xsl.XsltArgumentList>najdete v tématu <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-133">For more information about the <xref:System.Xml.Xsl.XsltArgumentList>, see <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>

## <a name="recommended-secure-use-of-xsltransform-class"></a><span data-ttu-id="6f7c7-134">Doporučené zabezpečené použití třídy XslTransform</span><span class="sxs-lookup"><span data-stu-id="6f7c7-134">Recommended Secure Use of XslTransform Class</span></span>

<span data-ttu-id="6f7c7-135">Oprávnění zabezpečení pro šablonu stylů závisí na poskytnutých důkazech.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-135">The security privileges of the style sheet depend on the evidence provided.</span></span> <span data-ttu-id="6f7c7-136">Následující tabulka shrnuje umístění předlohy se styly a poskytuje vysvětlení, jaký typ legitimace má poskytnout.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-136">The following table summarizes the location of the style sheet and gives an explanation of what type of evidence to give.</span></span>

- <span data-ttu-id="6f7c7-137">Šablona stylů XSLT neobsahuje žádné externí odkazy nebo šablona stylů pochází ze základu kódu, kterému důvěřujete.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-137">The XSLT style sheet has no external references, or the style sheet comes from a code base that you trust.</span></span>

  - <span data-ttu-id="6f7c7-138">Zadejte legitimaci ze sestavení:</span><span class="sxs-lookup"><span data-stu-id="6f7c7-138">Provide the evidence from your assembly:</span></span>

    ```vb
    Dim xslt = New XslTransform() xslt.Load(stylesheet, resolver, Me.GetType().Assembly.Evidence)

    XsltTransform xslt = new XslTransform();  xslt.Load(stylesheet, resolver, this.GetType().Assembly.Evidence);
    ```

- <span data-ttu-id="6f7c7-139">Šablona stylů XSLT pochází z vnějšího zdroje.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-139">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="6f7c7-140">Původ zdroje je známý a existuje ověřitelný identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-140">The origin of the source is known and there is a verifiable URI.</span></span>

  - <span data-ttu-id="6f7c7-141">Vytvořte legitimaci pomocí identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-141">Create evidence using the URI.</span></span>

    ```vb
    Dim xslt As New XslTransform() Dim ev As Evidence = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri) xslt.Load(stylesheet, resolver, evidence)

    XslTransform xslt = new XslTransform(); Evidence ev = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri); xslt.Load(stylesheet, resolver, evidence);
    ```

- <span data-ttu-id="6f7c7-142">Šablona stylů XSLT pochází z vnějšího zdroje.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-142">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="6f7c7-143">Původ zdroje není známý.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-143">The origin of the source is not known.</span></span>

  - <span data-ttu-id="6f7c7-144">Nastavte legitimaci na `null`.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-144">Set evidence to `null`.</span></span> <span data-ttu-id="6f7c7-145">Bloky skriptu nejsou zpracovány, funkce `document()` XSLT není podporována a objekty privilegovaného rozšíření nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-145">Script blocks are not processed, the XSLT `document()` function is not supported, and privileged extension objects are disallowed.</span></span>

    <span data-ttu-id="6f7c7-146">Kromě toho můžete také nastavit parametr `resolver` pro `null` tím zajistíte, že `xsl:import` a `xsl:include` prvky nebudou zpracovány.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-146">Additionally, you can also set the `resolver` parameter to `null` This ensures that `xsl:import` and `xsl:include` elements are not processed.</span></span>

- <span data-ttu-id="6f7c7-147">Šablona stylů XSLT pochází z vnějšího zdroje.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-147">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="6f7c7-148">Původ zdroje není známý, ale vyžadujete podporu skriptů.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-148">The origin of the source is not known, but you require script support.</span></span>

  - <span data-ttu-id="6f7c7-149">Požaduje se legitimace od volajícího.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-149">Request evidence from the caller.</span></span>

## <a name="transformation-of-xml-data"></a><span data-ttu-id="6f7c7-150">Transformace dat XML</span><span class="sxs-lookup"><span data-stu-id="6f7c7-150">Transformation of XML Data</span></span>

<span data-ttu-id="6f7c7-151">Po načtení šablon stylů se transformace spustí voláním jedné z <xref:System.Xml.Xsl.XslTransform.Transform%2A> metod a zadáním vstupního zdrojového dokumentu.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-151">Once a style sheet is loaded, the transformation starts by calling one of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> methods and supplying an input source document.</span></span> <span data-ttu-id="6f7c7-152">Metoda <xref:System.Xml.Xsl.XslTransform.Transform%2A> je přetížena, aby poskytovala různé výstupy transformace.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-152">The <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is overloaded to provide different transformation outputs.</span></span> <span data-ttu-id="6f7c7-153">Transformace může mít za následek následující formáty výstupu:</span><span class="sxs-lookup"><span data-stu-id="6f7c7-153">The transformation can result in the following output formats:</span></span>

- <xref:System.Xml.XmlReader>

- <xref:System.Xml.XmlWriter>

- <xref:System.IO.TextWriter>

- <xref:System.IO.Stream>

- <span data-ttu-id="6f7c7-154">Adresa URL řetězce souboru</span><span class="sxs-lookup"><span data-stu-id="6f7c7-154">String URL of file</span></span>

<span data-ttu-id="6f7c7-155">V tomto posledním formátu adresa URL řetězce poskytuje často používaný scénář pro transformaci vstupního dokumentu umístěného v adrese URL a zápis dokumentu do výstupní adresy URL.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-155">This last format, the string URL, provides for a commonly used scenario in transforming an input document located in a URL and writing the document to the output URL.</span></span> <span data-ttu-id="6f7c7-156">Tato <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda je pohodlnější způsob, jak načíst dokument XML ze souboru, provést transformaci XSLT a zapsat výstup do souboru.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-156">This <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is a convenience method to load an XML document from a file, perform the XSLT transformation, and write the output to a file.</span></span> <span data-ttu-id="6f7c7-157">Tím zabráníte tomu, abyste vytvořili a načetli vstupní zdrojový dokument a potom zapsali do datového proudu souboru.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-157">This prevents you from having to create and load the input source document, and then write to a file stream.</span></span> <span data-ttu-id="6f7c7-158">Následující ukázka kódu ukazuje toto použití metody <xref:System.Xml.Xsl.XslTransform.Transform%2A> s použitím adresy URL řetězce jako vstupu a výstupu:</span><span class="sxs-lookup"><span data-stu-id="6f7c7-158">The following code sample shows this use of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method using the string URL as input and output:</span></span>

```vb
Dim xsltransform As XslTransform = New XslTransform()
xsltransform.Load("favorite.xsl")
xsltransform.Transform("MyDocument.Xml", "TransformResult.xml", Nothing)
```

```csharp
XslTransform xsltransform = new XslTransform();
xsltransform.Load("favorite.xsl");
xsltransform.Transform("MyDocument.xml", "TransformResult.xml", null);
```

## <a name="transforming-a-section-of-an-xml-document"></a><span data-ttu-id="6f7c7-159">Transformace oddílu dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="6f7c7-159">Transforming a Section of an XML Document</span></span>

<span data-ttu-id="6f7c7-160">Transformace se vztahují na dokument jako celek.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-160">Transformations apply to the document as a whole.</span></span> <span data-ttu-id="6f7c7-161">Jinými slovy, Pokud předáte v jiném než kořenovém uzlu dokumentu, nezabrání to procesu transformace v přístupu ke všem uzlům v načteném dokumentu.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-161">In other words, if you pass in a node other than the document root node, this does not prevent the transformation process from accessing all nodes in the loaded document.</span></span> <span data-ttu-id="6f7c7-162">Chcete-li transformovat fragment stromu výsledků, je nutné vytvořit <xref:System.Xml.XmlDocument> obsahující pouze fragment stromu výsledek a předat tento <xref:System.Xml.XmlDocument> metodě <xref:System.Xml.Xsl.XslTransform.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-162">To transform a result tree fragment, you must create an <xref:System.Xml.XmlDocument> containing just the result tree fragment and pass that <xref:System.Xml.XmlDocument> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span> <span data-ttu-id="6f7c7-163">Následující příklad provede transformaci fragmentu stromu výsledek.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-163">The following example performs a transformation on a result tree fragment.</span></span>

```vb
Dim xslt As New XslTransform()
xslt.Load("print_root.xsl")
Dim doc As New XmlDocument()
doc.Load("library.xml")
' Create a new document containing just the result tree fragment.
Dim testNode As XmlNode = doc.DocumentElement.FirstChild
Dim tmpDoc As New XmlDocument()
tmpDoc.LoadXml(testNode.OuterXml)
' Pass the document containing the result tree fragment
' to the Transform method.
Console.WriteLine(("Passing " + tmpDoc.OuterXml + " to print_root.xsl"))
xslt.Transform(tmpDoc, Nothing, Console.Out, Nothing)
```

```csharp
XslTransform xslt = new XslTransform();
xslt.Load("print_root.xsl");
XmlDocument doc = new XmlDocument();
doc.Load("library.xml");
// Create a new document containing just the result tree fragment.
XmlNode testNode = doc.DocumentElement.FirstChild;
XmlDocument tmpDoc = new XmlDocument();
tmpDoc.LoadXml(testNode.OuterXml);
// Pass the document containing the result tree fragment
// to the Transform method.
Console.WriteLine("Passing " + tmpDoc.OuterXml + " to print_root.xsl");
xslt.Transform(tmpDoc, null, Console.Out, null);
```

<span data-ttu-id="6f7c7-164">V příkladu se jako vstup používá soubor Library. XML a print_root. XSL a v konzole se vytvoří výstup následujícího:</span><span class="sxs-lookup"><span data-stu-id="6f7c7-164">The example uses the library.xml and print_root.xsl files as input and outputs the following to the console:</span></span>

```console
Passing <book genre="novel" ISBN="1-861001-57-5"><title>Pride And Prejudice</title></book> to print_root.xsl
Root node is book.
```

<span data-ttu-id="6f7c7-165">Library. XML</span><span class="sxs-lookup"><span data-stu-id="6f7c7-165">library.xml</span></span>

```xml
<library>
  <book genre='novel' ISBN='1-861001-57-5'>
     <title>Pride And Prejudice</title>
  </book>
  <book genre='novel' ISBN='1-81920-21-2'>
     <title>Hook</title>
  </book>
</library>
```

<span data-ttu-id="6f7c7-166">print_root. xsl</span><span class="sxs-lookup"><span data-stu-id="6f7c7-166">print_root.xsl</span></span>

```xml
<stylesheet version="1.0" xmlns="http://www.w3.org/1999/XSL/Transform" >
  <output method="text" />
  <template match="/">
     Root node is  <value-of select="local-name(//*[position() = 1])" />
  </template>
</stylesheet>
```

## <a name="migration-of-xslt-from-net-framework-version-10-to-net-framework-version-11"></a><span data-ttu-id="6f7c7-167">Migrace XSLT z verze .NET Framework 1,0 na .NET Framework verze 1,1</span><span class="sxs-lookup"><span data-stu-id="6f7c7-167">Migration of XSLT from .NET Framework version 1.0 to .NET Framework version 1.1</span></span>

<span data-ttu-id="6f7c7-168">V následující tabulce jsou uvedeny zastaralé metody verze 1,0 .NET Framework a nové .NET Framework verze 1,1 metody <xref:System.Xml.Xsl.XslTransform.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-168">The following table shows the obsolete .NET Framework version 1.0 methods and new .NET Framework version 1.1 methods for the <xref:System.Xml.Xsl.XslTransform.Load%2A> method.</span></span> <span data-ttu-id="6f7c7-169">Nové metody umožňují omezit oprávnění k šabloně stylů zadáním legitimace.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-169">The new methods enable you to limit the permissions of the style sheet by specifying evidence.</span></span>

|<span data-ttu-id="6f7c7-170">Zastaralé metody Load .NET Framework verze 1,0</span><span class="sxs-lookup"><span data-stu-id="6f7c7-170">Obsolete .NET Framework version 1.0 Load Methods</span></span>|<span data-ttu-id="6f7c7-171">Nahrazení metod Load .NET Framework verze 1,1</span><span class="sxs-lookup"><span data-stu-id="6f7c7-171">Replacement .NET Framework version 1.1 Load Methods</span></span>|
|------------------------------------------------------|---------------------------------------------------------|
|<span data-ttu-id="6f7c7-172">Load (vstup XPathNavigator);</span><span class="sxs-lookup"><span data-stu-id="6f7c7-172">Load(XPathNavigator input);</span></span><br /><br /> <span data-ttu-id="6f7c7-173">Load (vstup XPathNavigator, překladač objekt XmlResolver);</span><span class="sxs-lookup"><span data-stu-id="6f7c7-173">Load(XPathNavigator input, XmlResolver resolver);</span></span>|<span data-ttu-id="6f7c7-174">Load (šablona XPathNavigator, překladač objekt XmlResolver, legitimace legitimace);</span><span class="sxs-lookup"><span data-stu-id="6f7c7-174">Load(XPathNavigator stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|
|<span data-ttu-id="6f7c7-175">Načíst (IXPathNavigable StyleSheet);</span><span class="sxs-lookup"><span data-stu-id="6f7c7-175">Load(IXPathNavigable stylesheet);</span></span><br /><br /> <span data-ttu-id="6f7c7-176">Load (IXPathNavigable StyleSheet; objekt XmlResolver resolver);</span><span class="sxs-lookup"><span data-stu-id="6f7c7-176">Load(IXPathNavigable stylesheet, XmlResolver resolver);</span></span>|<span data-ttu-id="6f7c7-177">Load (šablona stylů IXPathNavigable, překladač objekt XmlResolver, legitimace legitimace);</span><span class="sxs-lookup"><span data-stu-id="6f7c7-177">Load(IXPathNavigable stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|
|<span data-ttu-id="6f7c7-178">Načíst (předloha XmlReader);</span><span class="sxs-lookup"><span data-stu-id="6f7c7-178">Load(XmlReader stylesheet);</span></span><br /><br /> <span data-ttu-id="6f7c7-179">Load (šablona XmlReader, překladač objekt XmlResolver);</span><span class="sxs-lookup"><span data-stu-id="6f7c7-179">Load(XmlReader stylesheet, XmlResolver resolver);</span></span>|<span data-ttu-id="6f7c7-180">Load (šablona XmlReader, překladač objekt XmlResolver, legitimace legitimace);</span><span class="sxs-lookup"><span data-stu-id="6f7c7-180">Load(XmlReader stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|

<span data-ttu-id="6f7c7-181">V následující tabulce jsou uvedeny zastaralé a nové metody pro metodu <xref:System.Xml.Xsl.XslTransform.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-181">The following table shows the obsolete and new methods for the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span> <span data-ttu-id="6f7c7-182">Nové metody přebírají objekt <xref:System.Xml.XmlResolver>.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-182">The new methods take an <xref:System.Xml.XmlResolver> object.</span></span>

|<span data-ttu-id="6f7c7-183">Zastaralé metody transformace verze 1,0 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6f7c7-183">Obsolete .NET Framework version 1.0 Transform Methods</span></span>|<span data-ttu-id="6f7c7-184">Náhrada .NET Framework metod transformace verze 1,1</span><span class="sxs-lookup"><span data-stu-id="6f7c7-184">Replacement .NET Framework version Transform 1.1 Methods</span></span>|
|-----------------------------------------------------------|--------------------------------------------------------------|
|<span data-ttu-id="6f7c7-185">XmlReader Transform (vstup XPathNavigator, třída XsltArgumentList args)</span><span class="sxs-lookup"><span data-stu-id="6f7c7-185">XmlReader Transform(XPathNavigator input, XsltArgumentList args)</span></span>|<span data-ttu-id="6f7c7-186">XmlReader Transform (Input XPathNavigator, třída XsltArgumentList args, překladač objekt XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="6f7c7-186">XmlReader Transform(XPathNavigator  input, XsltArgumentList args, XmlResolver resolver)</span></span>|
|<span data-ttu-id="6f7c7-187">Transformace XmlReader (IXPathNavigable Input, třída XsltArgumentList args)</span><span class="sxs-lookup"><span data-stu-id="6f7c7-187">XmlReader Transform(IXPathNavigable input, XsltArgumentList args)</span></span>|<span data-ttu-id="6f7c7-188">Transformace XmlReader (IXPathNavigable Input, třída XsltArgumentList args, překladač objekt XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="6f7c7-188">XmlReader Transform(IXPathNavigable input, XsltArgumentList args, XmlResolver resolver)</span></span>|
|<span data-ttu-id="6f7c7-189">Void – transformace (vstup XPathNavigator, argumenty třída XsltArgumentList, výstup XmlWriter)</span><span class="sxs-lookup"><span data-stu-id="6f7c7-189">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output)</span></span>|<span data-ttu-id="6f7c7-190">Void – transformace (vstup XPathNavigator, argumenty třída XsltArgumentList, výstup XmlWriter, překladač objekt XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="6f7c7-190">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="6f7c7-191">Void Transform (IXPathNavigable Input, třída XsltArgumentList args, XmlWriter Output)</span><span class="sxs-lookup"><span data-stu-id="6f7c7-191">Void Transform(IXPathNavigable input, XsltArgumentList args, XmlWriter output)</span></span>|<span data-ttu-id="6f7c7-192">Void Transform (IXpathNavigable Input, třída XsltArgumentList args, XmlWriter Output, překladač objekt XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="6f7c7-192">Void Transform(IXpathNavigable input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="6f7c7-193">Void – transformace (vstup XPathNavigator, třída XsltArgumentList argumenty, TextWriter výstup)</span><span class="sxs-lookup"><span data-stu-id="6f7c7-193">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output)</span></span>|<span data-ttu-id="6f7c7-194">Void – transformace (vstup XPathNavigator, třída XsltArgumentList args, TextWriter Output, překladač objekt XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="6f7c7-194">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="6f7c7-195">Void Transform (IXPathNavigable Input, třída XsltArgumentList args, TextWriter Output)</span><span class="sxs-lookup"><span data-stu-id="6f7c7-195">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output)</span></span>|<span data-ttu-id="6f7c7-196">Void Transform (IXPathNavigable Input, třída XsltArgumentList args, TextWriter Output, překladač objekt XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="6f7c7-196">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="6f7c7-197">Void – transformace (vstup XPathNavigator, třída XsltArgumentList argumenty, výstup datového proudu)</span><span class="sxs-lookup"><span data-stu-id="6f7c7-197">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output)</span></span>|<span data-ttu-id="6f7c7-198">Void – transformace (vstup XPathNavigator, třída XsltArgumentList argumenty, výstup datového proudu, překladač objekt XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="6f7c7-198">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="6f7c7-199">Void Transform (vstup IXPathNavigable, argumenty třída XsltArgumentList, výstup datového proudu)</span><span class="sxs-lookup"><span data-stu-id="6f7c7-199">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output)</span></span>|<span data-ttu-id="6f7c7-200">Void Transform (vstup IXPathNavigable, třída XsltArgumentList argumenty, výstup datového proudu, překladač objekt XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="6f7c7-200">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="6f7c7-201">Void – transformace (vstup řetězce, výstup řetězce);</span><span class="sxs-lookup"><span data-stu-id="6f7c7-201">Void Transform(String input, String output);</span></span>|<span data-ttu-id="6f7c7-202">Void – transformace (vstup řetězce, výstup řetězce, překladač objekt XmlResolver);</span><span class="sxs-lookup"><span data-stu-id="6f7c7-202">Void Transform(String input, String output, XmlResolver resolver);</span></span>|

<span data-ttu-id="6f7c7-203">Vlastnost <xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> je zastaralá v .NET Framework verze 1,1.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-203">The <xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> property is obsolete in .NET Framework version 1.1.</span></span> <span data-ttu-id="6f7c7-204">Místo toho použijte nová přetížení <xref:System.Xml.Xsl.XslTransform.Transform%2A>, která přijímají objekt <xref:System.Xml.XmlResolver>.</span><span class="sxs-lookup"><span data-stu-id="6f7c7-204">Instead, use the new <xref:System.Xml.Xsl.XslTransform.Transform%2A> overloads which take an <xref:System.Xml.XmlResolver> object.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f7c7-205">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6f7c7-205">See also</span></span>

- <xref:System.Xml.Xsl.XslTransform>
- [<span data-ttu-id="6f7c7-206">Transformace XSLT s třídou XslTransform</span><span class="sxs-lookup"><span data-stu-id="6f7c7-206">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="6f7c7-207">XPathNavigator v transformacích</span><span class="sxs-lookup"><span data-stu-id="6f7c7-207">XPathNavigator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [<span data-ttu-id="6f7c7-208">XPathNodeIterator v transformacích</span><span class="sxs-lookup"><span data-stu-id="6f7c7-208">XPathNodeIterator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [<span data-ttu-id="6f7c7-209">Vstup XPathDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="6f7c7-209">XPathDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [<span data-ttu-id="6f7c7-210">Vstup XmlDataDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="6f7c7-210">XmlDataDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
- [<span data-ttu-id="6f7c7-211">Vstup XmlDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="6f7c7-211">XmlDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
