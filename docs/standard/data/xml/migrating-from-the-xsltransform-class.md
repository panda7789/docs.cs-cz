---
title: Migrace z třídy XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9404d758-679f-4ffb-995d-3d07d817659e
ms.openlocfilehash: 8383d8cb3e5819c46a0716c59323e492bb9add8e
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937993"
---
# <a name="migrating-from-the-xsltransform-class"></a><span data-ttu-id="6e1ee-102">Migrace z třídy XslTransform</span><span class="sxs-lookup"><span data-stu-id="6e1ee-102">Migrating From the XslTransform Class</span></span>

<span data-ttu-id="6e1ee-103">Architektura XSLT byla přepracována v vydání sady Visual Studio 2005.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-103">The XSLT architecture was redesigned in the Visual Studio 2005 release.</span></span> <span data-ttu-id="6e1ee-104"><xref:System.Xml.Xsl.XslTransform> Třída byla nahrazena <xref:System.Xml.Xsl.XslCompiledTransform> třídou.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-104">The <xref:System.Xml.Xsl.XslTransform> class was replaced by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>

<span data-ttu-id="6e1ee-105">V následujících částech jsou popsány některé hlavní rozdíly mezi <xref:System.Xml.Xsl.XslCompiledTransform> <xref:System.Xml.Xsl.XslTransform> třídami a.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-105">The following sections describe some of the main differences between the <xref:System.Xml.Xsl.XslCompiledTransform> and the <xref:System.Xml.Xsl.XslTransform> classes.</span></span>

## <a name="performance"></a><span data-ttu-id="6e1ee-106">Výkon</span><span class="sxs-lookup"><span data-stu-id="6e1ee-106">Performance</span></span>

<span data-ttu-id="6e1ee-107"><xref:System.Xml.Xsl.XslCompiledTransform> Třída obsahuje mnoho vylepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-107">The <xref:System.Xml.Xsl.XslCompiledTransform> class includes many performance improvements.</span></span> <span data-ttu-id="6e1ee-108">Nový procesor XSLT zkompiluje šablonu stylů XSLT dolů do společného mezilehlého formátu, podobně jako modul CLR (Common Language Runtime) pro jiné programovací jazyky.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-108">The new XSLT processor compiles the XSLT style sheet down to a common intermediate format, similar to what the common language runtime (CLR) does for other programming languages.</span></span> <span data-ttu-id="6e1ee-109">Jakmile je šablona stylů zkompilována, může být uložena do mezipaměti a znovu použita.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-109">Once the style sheet is compiled, it can be cached and reused.</span></span>

<span data-ttu-id="6e1ee-110"><xref:System.Xml.Xsl.XslCompiledTransform> Třída také obsahuje další optimalizace, které jsou mnohem rychlejší než <xref:System.Xml.Xsl.XslTransform> třída.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-110">The <xref:System.Xml.Xsl.XslCompiledTransform> class also includes other optimizations that make it much faster than the <xref:System.Xml.Xsl.XslTransform> class.</span></span>

> [!NOTE]
> <span data-ttu-id="6e1ee-111"><xref:System.Xml.Xsl.XslCompiledTransform> I když je celkový výkon třídy lepší než <xref:System.Xml.Xsl.XslTransform> třída, <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metoda <xref:System.Xml.Xsl.XslCompiledTransform> třídy může při prvním volání transformace pracovat pomaleji než <xref:System.Xml.Xsl.XslTransform.Load%2A> metoda <xref:System.Xml.Xsl.XslTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-111">Although the overall performance of the <xref:System.Xml.Xsl.XslCompiledTransform> class is better than the <xref:System.Xml.Xsl.XslTransform> class, the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslCompiledTransform> class might perform more slowly than the <xref:System.Xml.Xsl.XslTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslTransform> class the first time it is called on a transformation.</span></span> <span data-ttu-id="6e1ee-112">Důvodem je, že soubor XSLT musí být zkompilován před jeho načtením.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-112">This is because the XSLT file must be compiled before it is loaded.</span></span> <span data-ttu-id="6e1ee-113">Další informace najdete v tomto blogovém příspěvku: [XslCompiledTransform pomalejší než XslTransform?](https://docs.microsoft.com/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)</span><span class="sxs-lookup"><span data-stu-id="6e1ee-113">For more information, see the following blog post: [XslCompiledTransform Slower than XslTransform?](https://docs.microsoft.com/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)</span></span>

## <a name="security"></a><span data-ttu-id="6e1ee-114">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="6e1ee-114">Security</span></span>

<span data-ttu-id="6e1ee-115">Ve výchozím nastavení <xref:System.Xml.Xsl.XslCompiledTransform> třída zakáže podporu funkce XSLT `document()` a vloženého skriptování.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-115">By default, the <xref:System.Xml.Xsl.XslCompiledTransform> class disables support for the XSLT `document()` function and embedded scripting.</span></span> <span data-ttu-id="6e1ee-116">Tyto funkce lze povolit vytvořením <xref:System.Xml.Xsl.XsltSettings> objektu, který má povolené funkce a předáním do <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-116">These features can be enabled by creating an <xref:System.Xml.Xsl.XsltSettings> object that has the features enabled and passing it to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span> <span data-ttu-id="6e1ee-117">Následující příklad ukazuje, jak povolit skriptování a provést transformaci XSLT.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-117">The following example shows how to enable scripting and perform an XSLT transformation.</span></span>

[!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
[!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]

<span data-ttu-id="6e1ee-118">Další informace najdete v tématu věnovaném [bezpečnostním hlediskům XSLT](../../../../docs/standard/data/xml/xslt-security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="6e1ee-118">For more information, see [XSLT Security Considerations](../../../../docs/standard/data/xml/xslt-security-considerations.md).</span></span>

## <a name="new-features"></a><span data-ttu-id="6e1ee-119">Nové funkce</span><span class="sxs-lookup"><span data-stu-id="6e1ee-119">New Features</span></span>

### <a name="temporary-files"></a><span data-ttu-id="6e1ee-120">Dočasné soubory</span><span class="sxs-lookup"><span data-stu-id="6e1ee-120">Temporary Files</span></span>

<span data-ttu-id="6e1ee-121">Dočasné soubory jsou někdy generovány během zpracování XSLT.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-121">Temporary files are sometimes generated during XSLT processing.</span></span> <span data-ttu-id="6e1ee-122">Pokud šablona stylů obsahuje bloky skriptu nebo pokud je zkompilována s nastavením ladění nastaveným na hodnotu true, mohou být ve složce% TEMP% vytvořeny dočasné soubory.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-122">If a style sheet contains script blocks, or if it is compiled with the debug setting set to true, temporary files may be created in the %TEMP% folder.</span></span> <span data-ttu-id="6e1ee-123">Můžou nastat případy, kdy se některé dočasné soubory neodstraní kvůli problémům s časováním.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-123">There may be instances when some temporary files are not deleted due to timing issues.</span></span> <span data-ttu-id="6e1ee-124">Například pokud jsou soubory používány aktuální aplikací AppDomain nebo ladicím programem, finalizační metoda <xref:System.CodeDom.Compiler.TempFileCollection> objektu nebude schopna je odebrat.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-124">For example, if the files are in use by the current AppDomain or by the debugger, the finalizer of the <xref:System.CodeDom.Compiler.TempFileCollection> object will not be able to remove them.</span></span>

<span data-ttu-id="6e1ee-125"><xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> Vlastnost může být použita k dalšímu vyčištění, aby bylo zajištěno, že všechny dočasné soubory budou odebrány z klienta.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-125">The <xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> property can be used for additional cleanup to make sure that all temporary files are removed from the client.</span></span>

### <a name="support-for-the-xsloutput-element-and-xmlwriter"></a><span data-ttu-id="6e1ee-126">Podpora elementu xsl: output a XmlWriter</span><span class="sxs-lookup"><span data-stu-id="6e1ee-126">Support for the xsl:output Element and XmlWriter</span></span>

<span data-ttu-id="6e1ee-127"><xref:System.Xml.Xsl.XslTransform> Třída ignorovala `xsl:output` nastavení při odeslání výstupu transformace do <xref:System.Xml.XmlWriter> objektu.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-127">The <xref:System.Xml.Xsl.XslTransform> class ignored `xsl:output` settings when the transform output was sent to an <xref:System.Xml.XmlWriter> object.</span></span> <span data-ttu-id="6e1ee-128"><xref:System.Xml.Xsl.XslCompiledTransform> Třída <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> má vlastnost, která vrací <xref:System.Xml.XmlWriterSettings> objekt obsahující výstupní informace odvozené z `xsl:output` prvku v šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-128">The <xref:System.Xml.Xsl.XslCompiledTransform> class has an <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> property that returns an <xref:System.Xml.XmlWriterSettings> object containing the output information derived from the `xsl:output` element of the style sheet.</span></span> <span data-ttu-id="6e1ee-129"><xref:System.Xml.XmlWriterSettings> Objekt se používá k vytvoření <xref:System.Xml.XmlWriter> objektu se správným nastavením, které lze předat <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metodě.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-129">The <xref:System.Xml.XmlWriterSettings> object is used to create an <xref:System.Xml.XmlWriter> object with the correct settings that can be passed to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span> <span data-ttu-id="6e1ee-130">Toto chování ilustruje následující kód jazyka C#:</span><span class="sxs-lookup"><span data-stu-id="6e1ee-130">The following C# code illustrates this behavior:</span></span>

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

### <a name="debug-option"></a><span data-ttu-id="6e1ee-131">Možnost ladění</span><span class="sxs-lookup"><span data-stu-id="6e1ee-131">Debug Option</span></span>

<span data-ttu-id="6e1ee-132"><xref:System.Xml.Xsl.XslCompiledTransform> Třída může generovat ladicí informace, které vám umožní ladit šablonu stylů pomocí ladicího programu Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-132">The <xref:System.Xml.Xsl.XslCompiledTransform> class can generate debug information, which enables you to debug the style sheet with the Microsoft Visual Studio Debugger.</span></span> <span data-ttu-id="6e1ee-133">Další informace naleznete v tématu <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29>.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-133">See <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29> for more information.</span></span>

## <a name="behavioral-differences"></a><span data-ttu-id="6e1ee-134">Rozdíly v chování</span><span class="sxs-lookup"><span data-stu-id="6e1ee-134">Behavioral Differences</span></span>

### <a name="transforming-to-an-xmlreader"></a><span data-ttu-id="6e1ee-135">Transformace na objekt XmlReader</span><span class="sxs-lookup"><span data-stu-id="6e1ee-135">Transforming to an XmlReader</span></span>

<span data-ttu-id="6e1ee-136"><xref:System.Xml.Xsl.XslTransform> Třída má několik přetížení transformace, které vracejí výsledky transformace jako <xref:System.Xml.XmlReader> objekt.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-136">The <xref:System.Xml.Xsl.XslTransform> class has several Transform overloads that return transformation results as an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="6e1ee-137">Tato přetížení lze použít k načtení výsledků transformace do reprezentace v paměti (například <xref:System.Xml.XmlDocument> nebo <xref:System.Xml.XPath.XPathDocument>) bez toho, aby vznikla režie serializace a deserializace výsledného stromu XML.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-137">These overloads can be used to load the transformation results into an in-memory representation (such as <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument>) without incurring the overhead of serialization and deserialization of the resulting XML tree.</span></span> <span data-ttu-id="6e1ee-138">Následující kód jazyka C# ukazuje, jak načíst výsledky transformace do <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-138">The following C# code shows how to load the transformation results into an <xref:System.Xml.XmlDocument> object.</span></span>

```csharp
// Load the style sheet
XslTransform xslt = new XslTransform();
xslt.Load("MyStylesheet.xsl");

// Transform input document to XmlDocument for additional processing
XmlDocument doc = new XmlDocument();
doc.Load(xslt.Transform(input, (XsltArgumentList)null));
```

<span data-ttu-id="6e1ee-139"><xref:System.Xml.Xsl.XslCompiledTransform> Třída nepodporuje transformaci na <xref:System.Xml.XmlReader> objekt.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-139">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not support transforming to an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="6e1ee-140">Můžete však něco podobného pomocí <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> metody načíst výsledný strom XML přímo z. <xref:System.Xml.XmlWriter></span><span class="sxs-lookup"><span data-stu-id="6e1ee-140">However, you can do something similar by using the <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> method to load the resulting XML tree directly from an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="6e1ee-141">Následující kód jazyka C# ukazuje, jak provést stejnou úlohu pomocí <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-141">The following C# code shows how to accomplish the same task using <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

```csharp
// Transform input document to XmlDocument for additional processing
XmlDocument doc = new XmlDocument();
using (XmlWriter writer = doc.CreateNavigator().AppendChild()) {
    xslt.Transform(input, (XsltArgumentList)null, writer);
}
```

### <a name="discretionary-behavior"></a><span data-ttu-id="6e1ee-142">Volitelné chování</span><span class="sxs-lookup"><span data-stu-id="6e1ee-142">Discretionary Behavior</span></span>

<span data-ttu-id="6e1ee-143">Doporučení W3C XSL Transformers (XSLT) verze 1,0 obsahuje oblasti, ve kterých se může poskytovatel implementace rozhodnout, jak tuto situaci zpracovat.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-143">The W3C XSL Transformations (XSLT) Version 1.0 Recommendation includes areas in which the implementation provider may decide how to handle a situation.</span></span> <span data-ttu-id="6e1ee-144">Tyto oblasti se považují za volitelné chování.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-144">These areas are considered to be discretionary behavior.</span></span> <span data-ttu-id="6e1ee-145">Existuje několik oblastí, kde se <xref:System.Xml.Xsl.XslCompiledTransform> chová jinak než <xref:System.Xml.Xsl.XslTransform> třída.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-145">There are several areas where the <xref:System.Xml.Xsl.XslCompiledTransform> behaves differently than the <xref:System.Xml.Xsl.XslTransform> class.</span></span> <span data-ttu-id="6e1ee-146">Další informace najdete v tématu [obnovitelné chyby XSLT](../../../../docs/standard/data/xml/recoverable-xslt-errors.md).</span><span class="sxs-lookup"><span data-stu-id="6e1ee-146">For more information, see [Recoverable XSLT Errors](../../../../docs/standard/data/xml/recoverable-xslt-errors.md).</span></span>

### <a name="extension-objects-and-script-functions"></a><span data-ttu-id="6e1ee-147">Objekty rozšíření a funkce skriptu</span><span class="sxs-lookup"><span data-stu-id="6e1ee-147">Extension Objects and Script Functions</span></span>

<span data-ttu-id="6e1ee-148"><xref:System.Xml.Xsl.XslCompiledTransform>zavádí dvě nová omezení používání funkcí skriptu:</span><span class="sxs-lookup"><span data-stu-id="6e1ee-148"><xref:System.Xml.Xsl.XslCompiledTransform> introduces two new restrictions on the use of script functions:</span></span>

- <span data-ttu-id="6e1ee-149">Z výrazů XPath mohou být volány pouze veřejné metody.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-149">Only public methods may be called from XPath expressions.</span></span>

- <span data-ttu-id="6e1ee-150">Přetížení lze odlišit od ostatních v závislosti na počtu argumentů.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-150">Overloads are distinguishable from each other based on the number of arguments.</span></span> <span data-ttu-id="6e1ee-151">Pokud má více než jedno přetížení stejný počet argumentů, bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-151">If more than one overload has the same number of arguments, an exception will be raised.</span></span>

<span data-ttu-id="6e1ee-152">V <xref:System.Xml.Xsl.XslCompiledTransform>nástroji je vazba (vyhledávání názvů metod) na funkce skriptu vyvolána v době kompilace a šablony stylů, které pracovaly s XslTransform, mohou způsobit výjimku, když jsou načteny pomocí <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-152">In <xref:System.Xml.Xsl.XslCompiledTransform>, a binding (method name lookup) to script functions occurs at compile time, and style sheets that worked with XslTransform may cause an exception when they are loaded with <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

<span data-ttu-id="6e1ee-153"><xref:System.Xml.Xsl.XslCompiledTransform>podporuje elementy `msxsl:using` s `msxsl:assembly` a podřízenými prvky `msxsl:script` v rámci elementu.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-153"><xref:System.Xml.Xsl.XslCompiledTransform> supports having `msxsl:using` and `msxsl:assembly` child elements within the `msxsl:script` element.</span></span> <span data-ttu-id="6e1ee-154">Elementy `msxsl:using` a `msxsl:assembly` slouží k deklaraci dalších oborů názvů a sestavení pro použití v bloku skriptu.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-154">The `msxsl:using` and `msxsl:assembly` elements are used to declare additional namespaces and assemblies for use in the script block.</span></span> <span data-ttu-id="6e1ee-155">Další informace najdete v tématu [bloky skriptu pomocí msxsl: Script](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md) .</span><span class="sxs-lookup"><span data-stu-id="6e1ee-155">See [Script Blocks Using msxsl:script](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md) for more information.</span></span>

<span data-ttu-id="6e1ee-156"><xref:System.Xml.Xsl.XslCompiledTransform>zakáže objekty rozšíření, které mají více přetížení se stejným počtem argumentů.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-156"><xref:System.Xml.Xsl.XslCompiledTransform> prohibits extension objects that have multiple overloads with the same number of arguments.</span></span>

### <a name="msxml-functions"></a><span data-ttu-id="6e1ee-157">Funkce MSXML</span><span class="sxs-lookup"><span data-stu-id="6e1ee-157">MSXML Functions</span></span>

<span data-ttu-id="6e1ee-158">Do <xref:System.Xml.Xsl.XslCompiledTransform> třídy se přidala podpora pro další funkce MSXML.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-158">Support for additional MSXML functions have been added to the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="6e1ee-159">Následující seznam popisuje nové nebo vylepšené funkce:</span><span class="sxs-lookup"><span data-stu-id="6e1ee-159">The following list describes new or improved functionality:</span></span>

- <span data-ttu-id="6e1ee-160">msxsl: node-set: <xref:System.Xml.Xsl.XslTransform> vyžaduje se, aby argument funkce [funkce sady uzlů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256197(v=vs.100)) byl fragmentem stromu výsledku.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-160">msxsl:node-set: <xref:System.Xml.Xsl.XslTransform> required the argument of the [node-set Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256197(v=vs.100)) function to be a result tree fragment.</span></span> <span data-ttu-id="6e1ee-161"><xref:System.Xml.Xsl.XslCompiledTransform> Třída nemá tento požadavek.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-161">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not have this requirement.</span></span>

- <span data-ttu-id="6e1ee-162">msxsl: verze: Tato funkce je podporována v <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-162">msxsl:version: This function is supported in <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

- <span data-ttu-id="6e1ee-163">Funkce rozšíření XPath: [funkce MS: String-Compare](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256114(v=vs.100)), [MS: UTC](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256474(v=vs.100)), [MS: Namespace-URI](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256231(v=vs.100)), [MS: funkce local-Name](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256055(v=vs.100)), [MS: Number Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256155(v=vs.100)), [MS: Format-Date](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256099(v=vs.100))a MS: funkce funkcí v [době formátování](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256467(v=vs.100)) jsou nyní podporovány.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-163">XPath extension functions: The [ms:string-compare Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256114(v=vs.100)), [ms:utc Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256474(v=vs.100)), [ms:namespace-uri Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256231(v=vs.100)), [ms:local-name Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256055(v=vs.100)), [ms:number Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256155(v=vs.100)), [ms:format-date Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256099(v=vs.100)), and [ms:format-time Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256467(v=vs.100)) functions are now supported.</span></span>

- <span data-ttu-id="6e1ee-164">Funkce rozšíření XPath související se schématem: tyto funkce nejsou nativně podporovány nástrojem <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-164">Schema-related XPath extension functions: These functions are not supported natively by <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span> <span data-ttu-id="6e1ee-165">Lze je však implementovat jako funkce rozšíření.</span><span class="sxs-lookup"><span data-stu-id="6e1ee-165">However, they can be implemented as extension functions.</span></span>

## <a name="see-also"></a><span data-ttu-id="6e1ee-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e1ee-166">See also</span></span>

- [<span data-ttu-id="6e1ee-167">Transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="6e1ee-167">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
- [<span data-ttu-id="6e1ee-168">Používání třídy XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="6e1ee-168">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
