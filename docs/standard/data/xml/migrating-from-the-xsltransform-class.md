---
title: "Migrace z XslTransform – třída"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 9404d758-679f-4ffb-995d-3d07d817659e
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1fe2848deadd8de4494f485d792604663515686e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="migrating-from-the-xsltransform-class"></a><span data-ttu-id="80176-102">Migrace z XslTransform – třída</span><span class="sxs-lookup"><span data-stu-id="80176-102">Migrating From the XslTransform Class</span></span>
<span data-ttu-id="80176-103">Architektura XSLT byla změněna v [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)] verzi.</span><span class="sxs-lookup"><span data-stu-id="80176-103">The XSLT architecture was redesigned in the [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)] release.</span></span> <span data-ttu-id="80176-104"><xref:System.Xml.Xsl.XslTransform> Třída nahradila <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="80176-104">The <xref:System.Xml.Xsl.XslTransform> class has been replaced by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
 <span data-ttu-id="80176-105">Následující části popisují některé hlavní rozdíly mezi <xref:System.Xml.Xsl.XslCompiledTransform> a <xref:System.Xml.Xsl.XslTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="80176-105">The following sections describe some of the main differences between the <xref:System.Xml.Xsl.XslCompiledTransform> and the <xref:System.Xml.Xsl.XslTransform> classes.</span></span>  
  
## <a name="performance"></a><span data-ttu-id="80176-106">Výkon</span><span class="sxs-lookup"><span data-stu-id="80176-106">Performance</span></span>  
 <span data-ttu-id="80176-107"><xref:System.Xml.Xsl.XslCompiledTransform> Třída obsahuje mnoho vylepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="80176-107">The <xref:System.Xml.Xsl.XslCompiledTransform> class includes many performance improvements.</span></span> <span data-ttu-id="80176-108">Nové procesoru XSLT zkompiluje Styl XSLT dolů common mezilehlá formátu, podobná common language runtime (CLR) nebude pro ostatní programovací jazyky.</span><span class="sxs-lookup"><span data-stu-id="80176-108">The new XSLT processor compiles the XSLT style sheet down to a common intermediate format, similar to what the common language runtime (CLR) does for other programming languages.</span></span> <span data-ttu-id="80176-109">Jakmile je zkompilován šablony stylů, můžete do mezipaměti a znovu použít.</span><span class="sxs-lookup"><span data-stu-id="80176-109">Once the style sheet is compiled, it can be cached and reused.</span></span>  
  
 <span data-ttu-id="80176-110"><xref:System.Xml.Xsl.XslCompiledTransform> Třída také obsahuje další optimalizace, které mnohem rychlejší než <xref:System.Xml.Xsl.XslTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="80176-110">The <xref:System.Xml.Xsl.XslCompiledTransform> class also includes other optimizations that make it much faster than the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="80176-111">I když celkový výkon <xref:System.Xml.Xsl.XslCompiledTransform> třída je lepší, než <xref:System.Xml.Xsl.XslTransform> třídy, <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metodu <xref:System.Xml.Xsl.XslCompiledTransform> třída může provádět další pomalu než <xref:System.Xml.Xsl.XslTransform.Load%2A> metodu <xref:System.Xml.Xsl.XslTransform> třída první, když je volána na transformaci.</span><span class="sxs-lookup"><span data-stu-id="80176-111">Although the overall performance of the <xref:System.Xml.Xsl.XslCompiledTransform> class is better than the <xref:System.Xml.Xsl.XslTransform> class, the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslCompiledTransform> class might perform more slowly than the <xref:System.Xml.Xsl.XslTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslTransform> class the first time it is called on a transformation.</span></span> <span data-ttu-id="80176-112">Je to proto, že soubor XSLT musí být zkompilovány, než je načten.</span><span class="sxs-lookup"><span data-stu-id="80176-112">This is because the XSLT file must be compiled before it is loaded.</span></span> <span data-ttu-id="80176-113">Další informace najdete v příspěvku blogu: [XslCompiledTransform nižší než XslTransform?](http://go.microsoft.com/fwlink/?LinkId=130590)</span><span class="sxs-lookup"><span data-stu-id="80176-113">For more information, see the following blog post: [XslCompiledTransform Slower than XslTransform?](http://go.microsoft.com/fwlink/?LinkId=130590)</span></span>  
  
## <a name="security"></a><span data-ttu-id="80176-114">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="80176-114">Security</span></span>  
 <span data-ttu-id="80176-115">Ve výchozím nastavení <xref:System.Xml.Xsl.XslCompiledTransform> třída zakáže podporu pro XSLT `document()` funkce a embedded skriptování.</span><span class="sxs-lookup"><span data-stu-id="80176-115">By default, the <xref:System.Xml.Xsl.XslCompiledTransform> class disables support for the XSLT `document()` function and embedded scripting.</span></span> <span data-ttu-id="80176-116">Tyto funkce se dá nastavit tak, že vytvoříte <xref:System.Xml.Xsl.XsltSettings> objekt, který má funkce povolena a předání do <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="80176-116">These features can be enabled by creating an <xref:System.Xml.Xsl.XsltSettings> object that has the features enabled and passing it to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span> <span data-ttu-id="80176-117">Následující příklad ukazuje, jak povolit skriptování a provedení transformace XSLT.</span><span class="sxs-lookup"><span data-stu-id="80176-117">The following example shows how to enable scripting and perform an XSLT transformation.</span></span>  
  
 [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
 [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
 <span data-ttu-id="80176-118">Další informace najdete v tématu [aspekty zabezpečení XSLT](../../../../docs/standard/data/xml/xslt-security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="80176-118">For more information, see [XSLT Security Considerations](../../../../docs/standard/data/xml/xslt-security-considerations.md).</span></span>  
  
## <a name="new-features"></a><span data-ttu-id="80176-119">Nové funkce</span><span class="sxs-lookup"><span data-stu-id="80176-119">New Features</span></span>  
  
### <a name="temporary-files"></a><span data-ttu-id="80176-120">Dočasné soubory</span><span class="sxs-lookup"><span data-stu-id="80176-120">Temporary Files</span></span>  
 <span data-ttu-id="80176-121">Dočasné soubory jsou někdy generována během XSLT zpracování.</span><span class="sxs-lookup"><span data-stu-id="80176-121">Temporary files are sometimes generated during XSLT processing.</span></span> <span data-ttu-id="80176-122">Pokud list stylu obsahuje blocích skriptu, nebo pokud je kompilován s nastavení ladění na hodnotu true, dočasné soubory může vytvořit ve složce % TEMP %.</span><span class="sxs-lookup"><span data-stu-id="80176-122">If a style sheet contains script blocks, or if it is compiled with the debug setting set to true, temporary files may be created in the %TEMP% folder.</span></span> <span data-ttu-id="80176-123">Může existovat instance některé dočasné soubory nejsou odstraněné v důsledku problémy načasování.</span><span class="sxs-lookup"><span data-stu-id="80176-123">There may be instances when some temporary files are not deleted due to timing issues.</span></span> <span data-ttu-id="80176-124">Například, pokud jsou soubory v používá aktuální domény aplikace nebo ladicí program finalizační metodu z <xref:System.CodeDom.Compiler.TempFileCollection> objekt nebude možné je odebrat.</span><span class="sxs-lookup"><span data-stu-id="80176-124">For example, if the files are in use by the current AppDomain or by the debugger, the finalizer of the <xref:System.CodeDom.Compiler.TempFileCollection> object will not be able to remove them.</span></span>  
  
 <span data-ttu-id="80176-125"><xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> Vlastnost lze použít pro další čištění a ujistěte se, že všechny dočasné soubory byly odebrány z klienta.</span><span class="sxs-lookup"><span data-stu-id="80176-125">The <xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> property can be used for additional cleanup to make sure that all temporary files are removed from the client.</span></span>  
  
### <a name="support-for-the-xsloutput-element-and-xmlwriter"></a><span data-ttu-id="80176-126">Podpora pro elementu xsl: Output elementu a XmlWriter</span><span class="sxs-lookup"><span data-stu-id="80176-126">Support for the xsl:output Element and XmlWriter</span></span>  
 <span data-ttu-id="80176-127"><xref:System.Xml.Xsl.XslTransform> Třída Ignorovat `xsl:output` nastavení, když byla odeslána výstup transformace <xref:System.Xml.XmlWriter> objektu.</span><span class="sxs-lookup"><span data-stu-id="80176-127">The <xref:System.Xml.Xsl.XslTransform> class ignored `xsl:output` settings when the transform output was sent to an <xref:System.Xml.XmlWriter> object.</span></span> <span data-ttu-id="80176-128"><xref:System.Xml.Xsl.XslCompiledTransform> Třída má <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> vlastnost, která vrací <xref:System.Xml.XmlWriterSettings> objekt obsahující informace výstup odvozen od `xsl:output` element šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="80176-128">The <xref:System.Xml.Xsl.XslCompiledTransform> class has an <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> property that returns an <xref:System.Xml.XmlWriterSettings> object containing the output information derived from the `xsl:output` element of the style sheet.</span></span> <span data-ttu-id="80176-129"><xref:System.Xml.XmlWriterSettings> Objekt se používá k vytvoření <xref:System.Xml.XmlWriter> objekt s správné nastavení, které lze předat <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="80176-129">The <xref:System.Xml.XmlWriterSettings> object is used to create an <xref:System.Xml.XmlWriter> object with the correct settings that can be passed to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span> <span data-ttu-id="80176-130">Následující kód C# znázorňuje toto chování:</span><span class="sxs-lookup"><span data-stu-id="80176-130">The following C# code illustrates this behavior:</span></span>  
  
```  
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
  
### <a name="debug-option"></a><span data-ttu-id="80176-131">Debug – možnost</span><span class="sxs-lookup"><span data-stu-id="80176-131">Debug Option</span></span>  
 <span data-ttu-id="80176-132"><xref:System.Xml.Xsl.XslCompiledTransform> Třída může generovat ladicí informace, které umožňuje provádět ladění šablony stylů s Microsoft [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] ladicí program.</span><span class="sxs-lookup"><span data-stu-id="80176-132">The <xref:System.Xml.Xsl.XslCompiledTransform> class can generate debug information, which enables you to debug the style sheet with the Microsoft [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] Debugger.</span></span> <span data-ttu-id="80176-133">Další informace naleznete v tématu <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29>.</span><span class="sxs-lookup"><span data-stu-id="80176-133">See <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29> for more information.</span></span>  
  
## <a name="behavioral-differences"></a><span data-ttu-id="80176-134">Rozdíly v chování</span><span class="sxs-lookup"><span data-stu-id="80176-134">Behavioral Differences</span></span>  
  
### <a name="transforming-to-an-xmlreader"></a><span data-ttu-id="80176-135">Transformace na objekt XmlReader</span><span class="sxs-lookup"><span data-stu-id="80176-135">Transforming to an XmlReader</span></span>  
 <span data-ttu-id="80176-136"><xref:System.Xml.Xsl.XslTransform> Třída má několik přetížení transformace, které vracejí výsledky transformace jako <xref:System.Xml.XmlReader> objektu.</span><span class="sxs-lookup"><span data-stu-id="80176-136">The <xref:System.Xml.Xsl.XslTransform> class has several Transform overloads that return transformation results as an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="80176-137">Tato přetížení slouží k načtení transformace výsledky do reprezentaci v paměti (například <xref:System.Xml.XmlDocument> nebo <xref:System.Xml.XPath.XPathDocument>) aniž by docházelo k režii serializace a deserializace výsledný soubor XML stromu.</span><span class="sxs-lookup"><span data-stu-id="80176-137">These overloads can be used to load the transformation results into an in-memory representation (such as <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument>) without incurring the overhead of serialization and deserialization of the resulting XML tree.</span></span> <span data-ttu-id="80176-138">Následující kód C# ukazuje, jak načíst výsledky transformace do <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="80176-138">The following C# code shows how to load the transformation results into an <xref:System.Xml.XmlDocument> object.</span></span>  
  
```  
// Load the style sheet  
XslTransform xslt = new XslTransform();  
xslt.Load("MyStylesheet.xsl");  
  
// Transform input document to XmlDocument for additional processing  
XmlDocument doc = new XmlDocument();  
doc.Load(xslt.Transform(input, (XsltArgumentList)null));  
```  
  
 <span data-ttu-id="80176-139"><xref:System.Xml.Xsl.XslCompiledTransform> Třída nepodporuje transformace na <xref:System.Xml.XmlReader> objektu.</span><span class="sxs-lookup"><span data-stu-id="80176-139">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not support transforming to an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="80176-140">Však můžete provést něco podobného podle pomocí <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> metodu za účelem načtení XML výsledný strom přímo z <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="80176-140">However, you can do something similar by using the <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> method to load the resulting XML tree directly from an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="80176-141">Následující kód C# ukazuje, jak provádět stejné úlohy pomocí <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="80176-141">The following C# code shows how to accomplish the same task using <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
```  
// Transform input document to XmlDocument for additional processing  
XmlDocument doc = new XmlDocument();  
using (XmlWriter writer = doc.CreateNavigator().AppendChild()) {  
    xslt.Transform(input, (XsltArgumentList)null, writer);  
}  
```  
  
### <a name="discretionary-behavior"></a><span data-ttu-id="80176-142">Volitelné chování</span><span class="sxs-lookup"><span data-stu-id="80176-142">Discretionary Behavior</span></span>  
 <span data-ttu-id="80176-143">Doporučení W3C XSL transformace XSLT () verze 1.0 zahrnuje oblasti, ve kterých může implementaci zprostředkovatele rozhodování o způsobu zpracování situaci.</span><span class="sxs-lookup"><span data-stu-id="80176-143">The W3C XSL Transformations (XSLT) Version 1.0 Recommendation includes areas in which the implementation provider may decide how to handle a situation.</span></span> <span data-ttu-id="80176-144">Tyto oblasti jsou považovány za volitelné chování.</span><span class="sxs-lookup"><span data-stu-id="80176-144">These areas are considered to be discretionary behavior.</span></span> <span data-ttu-id="80176-145">Existují několik oblasti, kde <xref:System.Xml.Xsl.XslCompiledTransform> chová jinak než <xref:System.Xml.Xsl.XslTransform> – třída.</span><span class="sxs-lookup"><span data-stu-id="80176-145">There are several areas where the <xref:System.Xml.Xsl.XslCompiledTransform> behaves differently than the <xref:System.Xml.Xsl.XslTransform> class.</span></span> <span data-ttu-id="80176-146">Další informace najdete v tématu [obnovitelné chyby XSLT](../../../../docs/standard/data/xml/recoverable-xslt-errors.md).</span><span class="sxs-lookup"><span data-stu-id="80176-146">For more information, see [Recoverable XSLT Errors](../../../../docs/standard/data/xml/recoverable-xslt-errors.md).</span></span>  
  
### <a name="extension-objects-and-script-functions"></a><span data-ttu-id="80176-147">Rozšíření objektů a funkcí skriptu</span><span class="sxs-lookup"><span data-stu-id="80176-147">Extension Objects and Script Functions</span></span>  
 <span data-ttu-id="80176-148"><xref:System.Xml.Xsl.XslCompiledTransform>zavádí dvě nové omezení použití skriptu funkcí:</span><span class="sxs-lookup"><span data-stu-id="80176-148"><xref:System.Xml.Xsl.XslCompiledTransform> introduces two new restrictions on the use of script functions:</span></span>  
  
-   <span data-ttu-id="80176-149">Může být volána pouze veřejné metody výrazech XPath.</span><span class="sxs-lookup"><span data-stu-id="80176-149">Only public methods may be called from XPath expressions.</span></span>  
  
-   <span data-ttu-id="80176-150">Přetížení se liší od sebe navzájem podle počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="80176-150">Overloads are distinguishable from each other based on the number of arguments.</span></span> <span data-ttu-id="80176-151">Pokud má více než jedním přetížením stejný počet argumentů, bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="80176-151">If more than one overload has the same number of arguments, an exception will be raised.</span></span>  
  
 <span data-ttu-id="80176-152">V <xref:System.Xml.Xsl.XslCompiledTransform>, vazbu (vyhledání názvu metoda) ke skriptu funkce nastane při kompilaci a stylů, které fungovaly s XslTranform může způsobit výjimku při načtení s <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="80176-152">In <xref:System.Xml.Xsl.XslCompiledTransform>, a binding (method name lookup) to script functions occurs at compile time, and style sheets that worked with XslTranform may cause an exception when they are loaded with <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
 <span data-ttu-id="80176-153"><xref:System.Xml.Xsl.XslCompiledTransform>podporuje s `msxsl:using` a `msxsl:assembly` podřízených elementů v rámci `msxsl:script` elementu.</span><span class="sxs-lookup"><span data-stu-id="80176-153"><xref:System.Xml.Xsl.XslCompiledTransform> supports having `msxsl:using` and `msxsl:assembly` child elements within the `msxsl:script` element.</span></span> <span data-ttu-id="80176-154">`msxsl:using` a `msxsl:assembly` prvky se používá k deklaraci další obory názvů a sestavení pro použití v bloku skriptu.</span><span class="sxs-lookup"><span data-stu-id="80176-154">The `msxsl:using` and `msxsl:assembly` elements are used to declare additional namespaces and assemblies for use in the script block.</span></span> <span data-ttu-id="80176-155">V tématu [pomocí bloky skriptu msxsl:script](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="80176-155">See [Script Blocks Using msxsl:script](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md) for more information.</span></span>  
  
 <span data-ttu-id="80176-156"><xref:System.Xml.Xsl.XslCompiledTransform>zakazuje rozšíření objekty, které mají více přetížení se stejný počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="80176-156"><xref:System.Xml.Xsl.XslCompiledTransform> prohibits extension objects that have multiple overloads with the same number of arguments.</span></span>  
  
### <a name="msxml-functions"></a><span data-ttu-id="80176-157">Funkce MSXML</span><span class="sxs-lookup"><span data-stu-id="80176-157">MSXML Functions</span></span>  
 <span data-ttu-id="80176-158">Podpora pro další MSXML funkce přidané <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="80176-158">Support for additional MSXML functions have been added to the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="80176-159">Následující seznam popisuje nové nebo vylepšené funkce:</span><span class="sxs-lookup"><span data-stu-id="80176-159">The following list describes new or improved functionality:</span></span>  
  
-   <span data-ttu-id="80176-160">msxsl:node-nastavit: <xref:System.Xml.Xsl.XslTransform> vyžaduje argument [sada uzlů funkce](http://msdn.microsoft.com/en-us/87b6b3f4-16f4-4fa3-8103-d62a679ac2a7) funkce, která má být fragment stromu výsledek.</span><span class="sxs-lookup"><span data-stu-id="80176-160">msxsl:node-set: <xref:System.Xml.Xsl.XslTransform> required the argument of the [node-set Function](http://msdn.microsoft.com/en-us/87b6b3f4-16f4-4fa3-8103-d62a679ac2a7) function to be a result tree fragment.</span></span> <span data-ttu-id="80176-161"><xref:System.Xml.Xsl.XslCompiledTransform> Třída nemá tento požadavek.</span><span class="sxs-lookup"><span data-stu-id="80176-161">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not have this requirement.</span></span>  
  
-   <span data-ttu-id="80176-162">msxsl:Version: Tato funkce není podporována v <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="80176-162">msxsl:version: This function is supported in <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
-   <span data-ttu-id="80176-163">Funkce rozšíření XPath: [ms:string-compare – funkce](http://msdn.microsoft.com/en-us/20616b82-9e27-444c-b714-4f1e09b73aee), [ms:utc funkce](http://msdn.microsoft.com/en-us/ef26fc88-84c6-4fb9-9c3b-f2f5264b864f), [ms:namespace-uri funkce](http://msdn.microsoft.com/en-us/91f9cabf-ab93-4dbe-9c12-e6a75214f4c7), [ms:local-název funkce](http://msdn.microsoft.com/en-us/10ed60a1-17a9-4d74-8b98-7940ac97c0b5), [ms:number funkce](http://msdn.microsoft.com/en-us/b94fc08e-1f31-4f48-b1a8-6d78c1b5d954), [ms:format-datum funkce](http://msdn.microsoft.com/en-us/51f35609-89a9-4098-a166-88bf01300bf5), a [ms:format-čas funkce](http://msdn.microsoft.com/en-us/e5c2df2d-e8fb-4a8f-bfc0-db84ea12a5d5) funkce jsou nyní podporovány.</span><span class="sxs-lookup"><span data-stu-id="80176-163">XPath extension functions: The [ms:string-compare Function](http://msdn.microsoft.com/en-us/20616b82-9e27-444c-b714-4f1e09b73aee), [ms:utc Function](http://msdn.microsoft.com/en-us/ef26fc88-84c6-4fb9-9c3b-f2f5264b864f), [ms:namespace-uri Function](http://msdn.microsoft.com/en-us/91f9cabf-ab93-4dbe-9c12-e6a75214f4c7), [ms:local-name Function](http://msdn.microsoft.com/en-us/10ed60a1-17a9-4d74-8b98-7940ac97c0b5), [ms:number Function](http://msdn.microsoft.com/en-us/b94fc08e-1f31-4f48-b1a8-6d78c1b5d954), [ms:format-date Function](http://msdn.microsoft.com/en-us/51f35609-89a9-4098-a166-88bf01300bf5), and [ms:format-time Function](http://msdn.microsoft.com/en-us/e5c2df2d-e8fb-4a8f-bfc0-db84ea12a5d5) functions are now supported.</span></span>  
  
-   <span data-ttu-id="80176-164">Schéma související funkce rozšíření XPath: tyto funkce nejsou podporovány nativně pomocí <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="80176-164">Schema-related XPath extension functions: These functions are not supported natively by <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span> <span data-ttu-id="80176-165">Však mohou být provedeny jako rozšíření funkce.</span><span class="sxs-lookup"><span data-stu-id="80176-165">However, they can be implemented as extension functions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80176-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="80176-166">See Also</span></span>  
 [<span data-ttu-id="80176-167">Transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="80176-167">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [<span data-ttu-id="80176-168">Používání třídy XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="80176-168">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
