---
title: Migrace z třídy XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9404d758-679f-4ffb-995d-3d07d817659e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b0536607faa629e6113db0012056622d1adb541
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62027144"
---
# <a name="migrating-from-the-xsltransform-class"></a><span data-ttu-id="4cc7b-102">Migrace z třídy XslTransform</span><span class="sxs-lookup"><span data-stu-id="4cc7b-102">Migrating From the XslTransform Class</span></span>

<span data-ttu-id="4cc7b-103">Architektura XSLT byla přepracována ve verzi Visual Studio 2005.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-103">The XSLT architecture was redesigned in the Visual Studio 2005 release.</span></span> <span data-ttu-id="4cc7b-104"><xref:System.Xml.Xsl.XslTransform> Byl nahrazen třídy <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-104">The <xref:System.Xml.Xsl.XslTransform> class was replaced by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>

<span data-ttu-id="4cc7b-105">Následující části popisují některé hlavní rozdíly mezi <xref:System.Xml.Xsl.XslCompiledTransform> a <xref:System.Xml.Xsl.XslTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-105">The following sections describe some of the main differences between the <xref:System.Xml.Xsl.XslCompiledTransform> and the <xref:System.Xml.Xsl.XslTransform> classes.</span></span>

## <a name="performance"></a><span data-ttu-id="4cc7b-106">Výkon</span><span class="sxs-lookup"><span data-stu-id="4cc7b-106">Performance</span></span>

<span data-ttu-id="4cc7b-107"><xref:System.Xml.Xsl.XslCompiledTransform> Třída zahrnuje mnoho vylepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-107">The <xref:System.Xml.Xsl.XslCompiledTransform> class includes many performance improvements.</span></span> <span data-ttu-id="4cc7b-108">Zkompiluje nový procesoru XSLT šablony stylů XSLT na běžné mezilehlého formátu, podobně jako na modul CLR (CLR) nemá pro jiných programovacích jazycích.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-108">The new XSLT processor compiles the XSLT style sheet down to a common intermediate format, similar to what the common language runtime (CLR) does for other programming languages.</span></span> <span data-ttu-id="4cc7b-109">Jakmile je zkompilován šablony stylů, může do mezipaměti a znovu použít.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-109">Once the style sheet is compiled, it can be cached and reused.</span></span>

<span data-ttu-id="4cc7b-110"><xref:System.Xml.Xsl.XslCompiledTransform> Třída také obsahuje další optimalizace, které usnadňují mnohem rychlejší než <xref:System.Xml.Xsl.XslTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-110">The <xref:System.Xml.Xsl.XslCompiledTransform> class also includes other optimizations that make it much faster than the <xref:System.Xml.Xsl.XslTransform> class.</span></span>

> [!NOTE]
> <span data-ttu-id="4cc7b-111">I když celkový výkon <xref:System.Xml.Xsl.XslCompiledTransform> třída je lepší, než <xref:System.Xml.Xsl.XslTransform> třídy, <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metodu <xref:System.Xml.Xsl.XslCompiledTransform> třídy můžou provádět více pomalu než <xref:System.Xml.Xsl.XslTransform.Load%2A> metodu <xref:System.Xml.Xsl.XslTransform> třída první, když je volán na transformaci.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-111">Although the overall performance of the <xref:System.Xml.Xsl.XslCompiledTransform> class is better than the <xref:System.Xml.Xsl.XslTransform> class, the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslCompiledTransform> class might perform more slowly than the <xref:System.Xml.Xsl.XslTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslTransform> class the first time it is called on a transformation.</span></span> <span data-ttu-id="4cc7b-112">Je to proto musí být kompilován soubor XSLT, předtím, než je načten.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-112">This is because the XSLT file must be compiled before it is loaded.</span></span> <span data-ttu-id="4cc7b-113">Další informace najdete v následujícím blogovém příspěvku: [Pomalejší než XslTransform XslCompiledTransform?](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/)</span><span class="sxs-lookup"><span data-stu-id="4cc7b-113">For more information, see the following blog post: [XslCompiledTransform Slower than XslTransform?](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/)</span></span>

## <a name="security"></a><span data-ttu-id="4cc7b-114">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="4cc7b-114">Security</span></span>

<span data-ttu-id="4cc7b-115">Ve výchozím nastavení <xref:System.Xml.Xsl.XslCompiledTransform> třídy zakáže podporu pro XSLT `document()` funkce a vložené skriptování.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-115">By default, the <xref:System.Xml.Xsl.XslCompiledTransform> class disables support for the XSLT `document()` function and embedded scripting.</span></span> <span data-ttu-id="4cc7b-116">Tyto funkce se dá nastavit tak, že vytvoříte <xref:System.Xml.Xsl.XsltSettings> objekt, který má funkce povolena a předá se <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-116">These features can be enabled by creating an <xref:System.Xml.Xsl.XsltSettings> object that has the features enabled and passing it to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span> <span data-ttu-id="4cc7b-117">Následující příklad ukazuje, jak povolit skriptování a provedení transformace XSLT.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-117">The following example shows how to enable scripting and perform an XSLT transformation.</span></span>

[!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
[!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]

<span data-ttu-id="4cc7b-118">Další informace najdete v tématu [aspekty zabezpečení XSLT](../../../../docs/standard/data/xml/xslt-security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="4cc7b-118">For more information, see [XSLT Security Considerations](../../../../docs/standard/data/xml/xslt-security-considerations.md).</span></span>

## <a name="new-features"></a><span data-ttu-id="4cc7b-119">Nové funkce</span><span class="sxs-lookup"><span data-stu-id="4cc7b-119">New Features</span></span>

### <a name="temporary-files"></a><span data-ttu-id="4cc7b-120">Dočasné soubory</span><span class="sxs-lookup"><span data-stu-id="4cc7b-120">Temporary Files</span></span>

<span data-ttu-id="4cc7b-121">Dočasné soubory jsou vygenerovány někdy během XSLT zpracování.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-121">Temporary files are sometimes generated during XSLT processing.</span></span> <span data-ttu-id="4cc7b-122">Pokud šablona stylů obsahuje bloky kódu skriptu, nebo pokud je kompilován nastavení ladění je nastavená na hodnotu true, dočasné soubory může vytvořit ve složce % TEMP %.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-122">If a style sheet contains script blocks, or if it is compiled with the debug setting set to true, temporary files may be created in the %TEMP% folder.</span></span> <span data-ttu-id="4cc7b-123">Může existovat instancí se neodstraní některé dočasné soubory z důvodu problémy načasování.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-123">There may be instances when some temporary files are not deleted due to timing issues.</span></span> <span data-ttu-id="4cc7b-124">Například, pokud jsou soubory používá aktuální domény aplikace nebo pomocí ladicího programu, finalizační metodu <xref:System.CodeDom.Compiler.TempFileCollection> objekt nebude možné je odstranit.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-124">For example, if the files are in use by the current AppDomain or by the debugger, the finalizer of the <xref:System.CodeDom.Compiler.TempFileCollection> object will not be able to remove them.</span></span>

<span data-ttu-id="4cc7b-125"><xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> Vlastnost lze použít pro další čištění. abyste měli jistotu, že všechny dočasné soubory byly odebrány z klienta.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-125">The <xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> property can be used for additional cleanup to make sure that all temporary files are removed from the client.</span></span>

### <a name="support-for-the-xsloutput-element-and-xmlwriter"></a><span data-ttu-id="4cc7b-126">Podpora pro elementu xsl: Output elementu a XmlWriter</span><span class="sxs-lookup"><span data-stu-id="4cc7b-126">Support for the xsl:output Element and XmlWriter</span></span>

<span data-ttu-id="4cc7b-127"><xref:System.Xml.Xsl.XslTransform> Třídy Ignorovat `xsl:output` nastavení při výstupu transformace byla odeslána do <xref:System.Xml.XmlWriter> objektu.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-127">The <xref:System.Xml.Xsl.XslTransform> class ignored `xsl:output` settings when the transform output was sent to an <xref:System.Xml.XmlWriter> object.</span></span> <span data-ttu-id="4cc7b-128"><xref:System.Xml.Xsl.XslCompiledTransform> Třída má <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> vlastnost, která vrátí <xref:System.Xml.XmlWriterSettings> objekt obsahující informace o výstupu odvozený od `xsl:output` elementu šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-128">The <xref:System.Xml.Xsl.XslCompiledTransform> class has an <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> property that returns an <xref:System.Xml.XmlWriterSettings> object containing the output information derived from the `xsl:output` element of the style sheet.</span></span> <span data-ttu-id="4cc7b-129"><xref:System.Xml.XmlWriterSettings> Objektu se používá k vytvoření <xref:System.Xml.XmlWriter> objekt se správným nastavením, které mohou být předány <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-129">The <xref:System.Xml.XmlWriterSettings> object is used to create an <xref:System.Xml.XmlWriter> object with the correct settings that can be passed to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span> <span data-ttu-id="4cc7b-130">Následující kód jazyka C# ukazuje toto chování:</span><span class="sxs-lookup"><span data-stu-id="4cc7b-130">The following C# code illustrates this behavior:</span></span>

```csharp
// Create the XslTransform object and load the style sheet.
XslCompiledTransform xslt = new XslCompiledTransform();
xslt.Load(stylesheet);

// Load the file to transform.
XPathDocument doc = new XPathDocument(filename);

// Create the writer.
XmlWriter writer = XmlWriter.Create(Console.Out, xslt.OutputSettings);

// Transform the file and send the output to the console.
xslt.Transform(doc, writer);
writer.Close();
```

### <a name="debug-option"></a><span data-ttu-id="4cc7b-131">Debug – možnost</span><span class="sxs-lookup"><span data-stu-id="4cc7b-131">Debug Option</span></span>

<span data-ttu-id="4cc7b-132"><xref:System.Xml.Xsl.XslCompiledTransform> Třída může generovat ladicí informace, které umožňuje provádět ladění stylů se Microsoft Visual Studio Debugger.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-132">The <xref:System.Xml.Xsl.XslCompiledTransform> class can generate debug information, which enables you to debug the style sheet with the Microsoft Visual Studio Debugger.</span></span> <span data-ttu-id="4cc7b-133">Další informace naleznete v tématu <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29>.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-133">See <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29> for more information.</span></span>

## <a name="behavioral-differences"></a><span data-ttu-id="4cc7b-134">Behaviorální rozdíly</span><span class="sxs-lookup"><span data-stu-id="4cc7b-134">Behavioral Differences</span></span>

### <a name="transforming-to-an-xmlreader"></a><span data-ttu-id="4cc7b-135">Transformace do třídy XmlReader</span><span class="sxs-lookup"><span data-stu-id="4cc7b-135">Transforming to an XmlReader</span></span>

<span data-ttu-id="4cc7b-136"><xref:System.Xml.Xsl.XslTransform> Třída má několik přetížení transformace, které vracejí výsledky transformace jako <xref:System.Xml.XmlReader> objektu.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-136">The <xref:System.Xml.Xsl.XslTransform> class has several Transform overloads that return transformation results as an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="4cc7b-137">Tato přetížení slouží k načtení výsledků transformace do reprezentaci v paměti (například <xref:System.Xml.XmlDocument> nebo <xref:System.Xml.XPath.XPathDocument>) bez dalších nákladů na režii serializace a deserializace výsledného kódu XML stromu.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-137">These overloads can be used to load the transformation results into an in-memory representation (such as <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument>) without incurring the overhead of serialization and deserialization of the resulting XML tree.</span></span> <span data-ttu-id="4cc7b-138">Následující kód jazyka C# ukazuje, jak načíst výsledky transformace do <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-138">The following C# code shows how to load the transformation results into an <xref:System.Xml.XmlDocument> object.</span></span>

```csharp
// Load the style sheet
XslTransform xslt = new XslTransform();
xslt.Load("MyStylesheet.xsl");

// Transform input document to XmlDocument for additional processing
XmlDocument doc = new XmlDocument();
doc.Load(xslt.Transform(input, (XsltArgumentList)null));
```

<span data-ttu-id="4cc7b-139"><xref:System.Xml.Xsl.XslCompiledTransform> Třída nepodporuje transformaci na <xref:System.Xml.XmlReader> objektu.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-139">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not support transforming to an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="4cc7b-140">Ale můžete udělat něco podobného podle pomocí <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> metodu pro načtení výsledný XML stromu přímo z <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-140">However, you can do something similar by using the <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> method to load the resulting XML tree directly from an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="4cc7b-141">Následující kód jazyka C# ukazuje, jak provést stejný úkol pomocí <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-141">The following C# code shows how to accomplish the same task using <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

```csharp
// Transform input document to XmlDocument for additional processing
XmlDocument doc = new XmlDocument();
using (XmlWriter writer = doc.CreateNavigator().AppendChild()) {
    xslt.Transform(input, (XsltArgumentList)null, writer);
}
```

### <a name="discretionary-behavior"></a><span data-ttu-id="4cc7b-142">Volitelné chování</span><span class="sxs-lookup"><span data-stu-id="4cc7b-142">Discretionary Behavior</span></span>

<span data-ttu-id="4cc7b-143">Verze 1.0 doporučení W3C transformace XSL (XSLT) zahrnuje oblasti, ve kterých může implementaci zprostředkovatele rozhodování o způsobu zpracování situaci.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-143">The W3C XSL Transformations (XSLT) Version 1.0 Recommendation includes areas in which the implementation provider may decide how to handle a situation.</span></span> <span data-ttu-id="4cc7b-144">Tyto oblasti jsou považovány za volitelného chování.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-144">These areas are considered to be discretionary behavior.</span></span> <span data-ttu-id="4cc7b-145">Existuje několik oblastí kde <xref:System.Xml.Xsl.XslCompiledTransform> chová jinak než <xref:System.Xml.Xsl.XslTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-145">There are several areas where the <xref:System.Xml.Xsl.XslCompiledTransform> behaves differently than the <xref:System.Xml.Xsl.XslTransform> class.</span></span> <span data-ttu-id="4cc7b-146">Další informace najdete v tématu [obnovitelné chyby XSLT](../../../../docs/standard/data/xml/recoverable-xslt-errors.md).</span><span class="sxs-lookup"><span data-stu-id="4cc7b-146">For more information, see [Recoverable XSLT Errors](../../../../docs/standard/data/xml/recoverable-xslt-errors.md).</span></span>

### <a name="extension-objects-and-script-functions"></a><span data-ttu-id="4cc7b-147">Rozšíření objektů a funkcí skriptu</span><span class="sxs-lookup"><span data-stu-id="4cc7b-147">Extension Objects and Script Functions</span></span>

<span data-ttu-id="4cc7b-148"><xref:System.Xml.Xsl.XslCompiledTransform> přináší například tato dvě nová omezení týkající se použití funkce skriptu:</span><span class="sxs-lookup"><span data-stu-id="4cc7b-148"><xref:System.Xml.Xsl.XslCompiledTransform> introduces two new restrictions on the use of script functions:</span></span>

- <span data-ttu-id="4cc7b-149">Výrazy XPath může být volána pouze veřejné metody.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-149">Only public methods may be called from XPath expressions.</span></span>

- <span data-ttu-id="4cc7b-150">Přetížení se liší od sebe navzájem na základě počtu argumentů.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-150">Overloads are distinguishable from each other based on the number of arguments.</span></span> <span data-ttu-id="4cc7b-151">Pokud více než jednomu přetížení má stejný počet argumentů, bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-151">If more than one overload has the same number of arguments, an exception will be raised.</span></span>

<span data-ttu-id="4cc7b-152">V <xref:System.Xml.Xsl.XslCompiledTransform>vazbu (metoda vyhledávání názvu) do funkce skriptu dochází v době kompilace a šablony stylů, které ve spolupráci s XslTransform mohou způsobit výjimku, pokud jsou načtené <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-152">In <xref:System.Xml.Xsl.XslCompiledTransform>, a binding (method name lookup) to script functions occurs at compile time, and style sheets that worked with XslTransform may cause an exception when they are loaded with <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

<span data-ttu-id="4cc7b-153"><xref:System.Xml.Xsl.XslCompiledTransform> podporuje s `msxsl:using` a `msxsl:assembly` podřízených elementů v rámci `msxsl:script` elementu.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-153"><xref:System.Xml.Xsl.XslCompiledTransform> supports having `msxsl:using` and `msxsl:assembly` child elements within the `msxsl:script` element.</span></span> <span data-ttu-id="4cc7b-154">`msxsl:using` a `msxsl:assembly` elementy se používají k deklarování další obory názvů a sestavení pro použití v bloku skriptu.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-154">The `msxsl:using` and `msxsl:assembly` elements are used to declare additional namespaces and assemblies for use in the script block.</span></span> <span data-ttu-id="4cc7b-155">Zobrazit [bloky skriptu s použitím msxsl: script](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-155">See [Script Blocks Using msxsl:script](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md) for more information.</span></span>

<span data-ttu-id="4cc7b-156"><xref:System.Xml.Xsl.XslCompiledTransform> zakazuje rozšíření objekty, které mají více přetížení se stejným číslem argumenty.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-156"><xref:System.Xml.Xsl.XslCompiledTransform> prohibits extension objects that have multiple overloads with the same number of arguments.</span></span>

### <a name="msxml-functions"></a><span data-ttu-id="4cc7b-157">MSXML funkce</span><span class="sxs-lookup"><span data-stu-id="4cc7b-157">MSXML Functions</span></span>

<span data-ttu-id="4cc7b-158">Podpora pro další MSXML funkce byly přidány do <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-158">Support for additional MSXML functions have been added to the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="4cc7b-159">Následující seznam popisuje nové nebo vylepšené funkce:</span><span class="sxs-lookup"><span data-stu-id="4cc7b-159">The following list describes new or improved functionality:</span></span>

- <span data-ttu-id="4cc7b-160">msxsl:node-nastavit: <xref:System.Xml.Xsl.XslTransform> vyžaduje argument [funkce sada uzlů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256197(v=vs.100)) funkci fragment stromu výsledek.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-160">msxsl:node-set: <xref:System.Xml.Xsl.XslTransform> required the argument of the [node-set Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256197(v=vs.100)) function to be a result tree fragment.</span></span> <span data-ttu-id="4cc7b-161"><xref:System.Xml.Xsl.XslCompiledTransform> Třída nemá tento požadavek.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-161">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not have this requirement.</span></span>

- <span data-ttu-id="4cc7b-162">msxsl:Version: Tato funkce není podporována v <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-162">msxsl:version: This function is supported in <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

- <span data-ttu-id="4cc7b-163">Funkce rozšíření XPath: [Ms:string-compare – funkce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256114(v=vs.100)), [ms:utc funkce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256474(v=vs.100)), [MS: namespace-uri funkce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256231(v=vs.100)), [ms:local – název funkce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256055(v=vs.100)), [ms:number – funkce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256155(v=vs.100)), [ms:format-datum funkce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256099(v=vs.100)), a [ms:format – čas funkce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256467(v=vs.100)) funkce jsou nyní podporovány.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-163">XPath extension functions: The [ms:string-compare Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256114(v=vs.100)), [ms:utc Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256474(v=vs.100)), [ms:namespace-uri Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256231(v=vs.100)), [ms:local-name Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256055(v=vs.100)), [ms:number Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256155(v=vs.100)), [ms:format-date Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256099(v=vs.100)), and [ms:format-time Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256467(v=vs.100)) functions are now supported.</span></span>

- <span data-ttu-id="4cc7b-164">Schéma souvisejících funkcí rozšíření XPath: Tyto funkce nepodporuje nativně podle <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-164">Schema-related XPath extension functions: These functions are not supported natively by <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span> <span data-ttu-id="4cc7b-165">Ale že je možné implementovat jako funkcí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="4cc7b-165">However, they can be implemented as extension functions.</span></span>

## <a name="see-also"></a><span data-ttu-id="4cc7b-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4cc7b-166">See also</span></span>

- [<span data-ttu-id="4cc7b-167">Transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="4cc7b-167">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
- [<span data-ttu-id="4cc7b-168">Používání třídy XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="4cc7b-168">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
