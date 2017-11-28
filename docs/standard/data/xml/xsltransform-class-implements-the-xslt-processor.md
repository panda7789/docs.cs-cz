---
title: "Třída XslTransform implementuje procesoru XSLT"
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
ms.assetid: 88373fe2-4a6b-44f9-8a62-8a3e348e3a46
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 167cd81ecbc25ca243e3b4a7a6aa7327679528e0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xsltransform-class-implements-the-xslt-processor"></a><span data-ttu-id="2e65a-102">Třída XslTransform implementuje procesoru XSLT</span><span class="sxs-lookup"><span data-stu-id="2e65a-102">XslTransform Class Implements the XSLT Processor</span></span>
> [!NOTE]
>  <span data-ttu-id="2e65a-103"><xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e65a-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="2e65a-104">Můžete provést jazyk XSL pro transformace transformace XSLT () pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="2e65a-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="2e65a-105">V tématu [pomocí třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="2e65a-105">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="2e65a-106"><xref:System.Xml.Xsl.XslTransform> Třída je procesor XSLT implementace doporučení XSL transformace XSLT () verze 1.0.</span><span class="sxs-lookup"><span data-stu-id="2e65a-106">The <xref:System.Xml.Xsl.XslTransform> class is an XSLT processor implementing the XSL Transformations (XSLT) Version 1.0 recommendation.</span></span> <span data-ttu-id="2e65a-107"><xref:System.Xml.Xsl.XslTransform.Load%2A> Metoda vyhledá a načte šablony stylů a <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda transformuje dané zdrojový dokument.</span><span class="sxs-lookup"><span data-stu-id="2e65a-107">The <xref:System.Xml.Xsl.XslTransform.Load%2A> method locates and reads style sheets, and the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method transforms the given source document.</span></span> <span data-ttu-id="2e65a-108">Jakékoli úložiště, který implementuje <xref:System.Xml.XPath.IXPathNavigable> rozhraní lze použít jako zdroj dokumentu <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="2e65a-108">Any store that implements the <xref:System.Xml.XPath.IXPathNavigable> interface can be used as the source document for the <xref:System.Xml.Xsl.XslTransform>.</span></span> <span data-ttu-id="2e65a-109">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Aktuálně implementuje <xref:System.Xml.XPath.IXPathNavigable> rozhraní na <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument>a <xref:System.Xml.XPath.XPathDocument>, takže všechny tyto lze použít jako vstupní zdroj dokumentu, který má transformace.</span><span class="sxs-lookup"><span data-stu-id="2e65a-109">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] currently implements the <xref:System.Xml.XPath.IXPathNavigable> interface on the <xref:System.Xml.XmlDocument>, the <xref:System.Xml.XmlDataDocument>, and the <xref:System.Xml.XPath.XPathDocument>, so all of these can be used as the input source document to a transformation.</span></span>  
  
 <span data-ttu-id="2e65a-110"><xref:System.Xml.Xsl.XslTransform> Objekt v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] podporuje pouze specifikaci XSLT 1.0, definovanou s následujícím oborem názvů:</span><span class="sxs-lookup"><span data-stu-id="2e65a-110">The <xref:System.Xml.Xsl.XslTransform> object in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] only supports the XSLT 1.0 specification, defined with the following namespace:</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">    
```  
  
 <span data-ttu-id="2e65a-111">Šablony stylů mohou být načteny, pomocí <xref:System.Xml.Xsl.XslTransform.Load%2A> metoda z jednoho z následujících tříd:</span><span class="sxs-lookup"><span data-stu-id="2e65a-111">The style sheet can be loaded, using the <xref:System.Xml.Xsl.XslTransform.Load%2A> method, from one of the following classes:</span></span>  
  
-   <span data-ttu-id="2e65a-112">Objektem XPathNavigator nastaveným na</span><span class="sxs-lookup"><span data-stu-id="2e65a-112">XPathNavigator</span></span>  
  
-   <span data-ttu-id="2e65a-113">XmlReader</span><span class="sxs-lookup"><span data-stu-id="2e65a-113">XmlReader</span></span>  
  
-   <span data-ttu-id="2e65a-114">Řetězec představující adresu URL</span><span class="sxs-lookup"><span data-stu-id="2e65a-114">A string representing a URL</span></span>  
  
 <span data-ttu-id="2e65a-115">Existuje jiné <xref:System.Xml.Xsl.XslTransform.Load%2A> metoda pro každou z výše uvedených vstupní tříd.</span><span class="sxs-lookup"><span data-stu-id="2e65a-115">There is a different <xref:System.Xml.Xsl.XslTransform.Load%2A> method for each of the above input classes.</span></span> <span data-ttu-id="2e65a-116">Některé metody proveďte jednu z těchto tříd kombinace a <xref:System.Xml.XmlResolver> třída jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="2e65a-116">Some methods take in a combination of one of these classes and the <xref:System.Xml.XmlResolver> class as arguments.</span></span> <span data-ttu-id="2e65a-117"><xref:System.Xml.XmlResolver> Vyhledá prostředky odkazuje `<xsl:import>` nebo `<xsl:include>` najít v šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="2e65a-117">The <xref:System.Xml.XmlResolver> locates resources referenced by `<xsl:import>` or `<xsl:include>` found in the style sheet.</span></span> <span data-ttu-id="2e65a-118">Tyto metody přijímají řetězce <xref:System.Xml.XmlReader>, nebo <xref:System.Xml.XPath.XPathNavigator> jako vstup.</span><span class="sxs-lookup"><span data-stu-id="2e65a-118">The following methods take a string, <xref:System.Xml.XmlReader>, or <xref:System.Xml.XPath.XPathNavigator> as input.</span></span>  
  
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
  
 <span data-ttu-id="2e65a-119">Většina <xref:System.Xml.Xsl.XslTransform.Load%2A> metody uvedené výše proveďte <xref:System.Xml.XmlResolver> jako parametr.</span><span class="sxs-lookup"><span data-stu-id="2e65a-119">Most of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods shown above take an <xref:System.Xml.XmlResolver> as a parameter.</span></span> <span data-ttu-id="2e65a-120"><xref:System.Xml.XmlResolver> Slouží k načtení šablony stylů a všechny styl listy, kterou se odkazuje v xsl:import a xsl: zahrnují elementy.</span><span class="sxs-lookup"><span data-stu-id="2e65a-120">The <xref:System.Xml.XmlResolver> is used to load the style sheet and any style sheet(s) referenced in xsl:import and xsl:include elements.</span></span>  
  
 <span data-ttu-id="2e65a-121">Většina <xref:System.Xml.Xsl.XslTransform.Load%2A> metody také přijímají důkaz jako parametr.</span><span class="sxs-lookup"><span data-stu-id="2e65a-121">Most of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods also take evidence as a parameter.</span></span> <span data-ttu-id="2e65a-122">Je parametr důkaz <xref:System.Security.Policy.Evidence> je spojeno s šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="2e65a-122">The evidence parameter is the <xref:System.Security.Policy.Evidence> that is associated with the style sheet.</span></span> <span data-ttu-id="2e65a-123">Úroveň zabezpečení šablony stylů ovlivňuje všechny následné prostředky odkazuje na úroveň zabezpečení, jako je například skript obsahuje, všechny `document()` používá funkce a všechny objekty rozšíření používané <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="2e65a-123">The security level of the style sheet affects the security level of any subsequent resources it references, such as the script it contains, any `document()` functions it uses, and any extension objects used by the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>  
  
 <span data-ttu-id="2e65a-124">Pokud je načten pomocí šablony stylů <xref:System.Xml.Xsl.XslTransform.Load%2A> poskytuje metodu, která obsahuje parametr adresy URL a žádné důkaz, důkaz šablony stylů se počítá kombinací dané adrese URL s jeho lokality a zóny.</span><span class="sxs-lookup"><span data-stu-id="2e65a-124">If the style sheet is loaded using a <xref:System.Xml.Xsl.XslTransform.Load%2A> method that contains a URL parameter and no evidence is provided, the evidence of the style sheet is calculated by combining the given URL with its site and zone.</span></span>  
  
 <span data-ttu-id="2e65a-125">Pokud je zadaný žádný identifikátor URI nebo důkaz, je důkaz nastavení pro šablony stylů plně důvěryhodný.</span><span class="sxs-lookup"><span data-stu-id="2e65a-125">If no URI or evidence is provided, then the evidence set for the style sheet is fully trusted.</span></span> <span data-ttu-id="2e65a-126">Nezadávejte načtení šablony stylů z nedůvěryhodných zdrojů nebo přidat objekty nedůvěryhodné rozšíření do <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="2e65a-126">Do not load style sheets from untrusted sources, or add untrusted extension objects into the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>  
  
 <span data-ttu-id="2e65a-127">Další informace o úrovně zabezpečení a důkaz a jak ovlivňuje skriptování najdete v tématu [XSLT skriptování pomocí šablony stylů \<msxsl:script >](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md).</span><span class="sxs-lookup"><span data-stu-id="2e65a-127">For more information about security levels and evidence and how it affects scripting, see [XSLT Stylesheet Scripting Using \<msxsl:script>](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md).</span></span> <span data-ttu-id="2e65a-128">Informace o úrovně zabezpečení a důkaz a jak ovlivňuje objektů rozšíření najdete v tématu [třída XsltArgumentList pro parametry list stylu a rozšíření objekty](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).</span><span class="sxs-lookup"><span data-stu-id="2e65a-128">For information about security levels and evidence and how it affects extension objects, see [XsltArgumentList for Style Sheet Parameters and Extension Objects](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).</span></span>  
  
 <span data-ttu-id="2e65a-129">Informace o úrovně zabezpečení a důkaz a jak ovlivňuje `document()` funkce najdete v tématu [řešení externí XSLT šablony stylů a dokumenty](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md).</span><span class="sxs-lookup"><span data-stu-id="2e65a-129">For information about security levels and evidence and how it affects the `document()` function, see [Resolving External XSLT Style Sheets and Documents](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md).</span></span>  
  
 <span data-ttu-id="2e65a-130">Šablony stylů můžete zadat s počtem vstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="2e65a-130">A style sheet can be supplied with a number of input parameters.</span></span> <span data-ttu-id="2e65a-131">Funkce pro objekty rozšíření můžete také volat šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="2e65a-131">The style sheet can also call functions on extension objects.</span></span> <span data-ttu-id="2e65a-132">Parametry a objektů rozšíření jsou zadaná na list stylu pomocí <xref:System.Xml.Xsl.XsltArgumentList> třídy.</span><span class="sxs-lookup"><span data-stu-id="2e65a-132">Both parameters and extension objects are supplied to the style sheet using the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span> <span data-ttu-id="2e65a-133">Další informace o <xref:System.Xml.Xsl.XsltArgumentList>, najdete v části <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="2e65a-133">For more information about the <xref:System.Xml.Xsl.XsltArgumentList>, see <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>  
  
## <a name="recommended-secure-use-of-xsltransform-class"></a><span data-ttu-id="2e65a-134">Doporučené zabezpečení použití XslTransform – třída</span><span class="sxs-lookup"><span data-stu-id="2e65a-134">Recommended Secure Use of XslTransform Class</span></span>  
 <span data-ttu-id="2e65a-135">Oprávnění zabezpečení šablony stylů závisí na důkaz zadat.</span><span class="sxs-lookup"><span data-stu-id="2e65a-135">The security privileges of the style sheet depend on the evidence provided.</span></span> <span data-ttu-id="2e65a-136">Následující tabulka shrnuje umístění šablony stylů a vysvětluje, co typu důkaz poskytnout.</span><span class="sxs-lookup"><span data-stu-id="2e65a-136">The following table summarizes the location of the style sheet and gives an explanation of what type of evidence to give.</span></span>  
  
-   <span data-ttu-id="2e65a-137">Styl XSLT nemá žádné externí odkazy nebo šablony stylů pochází od základu kódu, které důvěřujete.</span><span class="sxs-lookup"><span data-stu-id="2e65a-137">The XSLT style sheet has no external references, or the style sheet comes from a code base that you trust.</span></span>  
  
    -   <span data-ttu-id="2e65a-138">Prokázání vaší sestavení:</span><span class="sxs-lookup"><span data-stu-id="2e65a-138">Provide the evidence from your assembly:</span></span>  
  
         `Dim xslt = New XslTransform() xslt.Load(stylesheet, resolver, Me.GetType().Assembly.Evidence)`  
  
         `XsltTransform xslt = new XslTransform();  xslt.Load(stylesheet, resolver, this.GetType().Assembly.Evidence);`  
  
-   <span data-ttu-id="2e65a-139">Styl XSLT pochází z vnějšího zdroje.</span><span class="sxs-lookup"><span data-stu-id="2e65a-139">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="2e65a-140">Je známý původ zdroje a je ověřitelná identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="2e65a-140">The origin of the source is known and there is a verifiable URI.</span></span>  
  
    -   <span data-ttu-id="2e65a-141">Vytvořte důkaz pomocí identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="2e65a-141">Create evidence using the URI.</span></span>  
  
         `Dim xslt As New XslTransform() Dim ev As Evidence = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri) xslt.Load(stylesheet, resolver, evidence)`  
  
         `XslTransform xslt = new XslTransform(); Evidence ev = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri); xslt.Load(stylesheet, resolver, evidence);`  
  
-   <span data-ttu-id="2e65a-142">Styl XSLT pochází z vnějšího zdroje.</span><span class="sxs-lookup"><span data-stu-id="2e65a-142">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="2e65a-143">Původ zdroje není znám.</span><span class="sxs-lookup"><span data-stu-id="2e65a-143">The origin of the source is not known.</span></span>  
  
    -   <span data-ttu-id="2e65a-144">Nastavte na důkaz `null`.</span><span class="sxs-lookup"><span data-stu-id="2e65a-144">Set evidence to `null`.</span></span> <span data-ttu-id="2e65a-145">Bloky Script nebudou zpracovány, XSLT `document()` funkce není podporována a objektů privilegované rozšíření nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="2e65a-145">Script blocks are not processed, the XSLT `document()` function is not supported, and privileged extension objects are disallowed.</span></span>  
  
         <span data-ttu-id="2e65a-146">Kromě toho můžete také nastavit `resolver` parametru `null` to zajistí, že `xsl:import` a `xsl:include` elementy nejsou předmětem zpracování.</span><span class="sxs-lookup"><span data-stu-id="2e65a-146">Additionally, you can also set the `resolver` parameter to `null` This ensures that `xsl:import` and `xsl:include` elements are not processed.</span></span>  
  
-   <span data-ttu-id="2e65a-147">Styl XSLT pochází z vnějšího zdroje.</span><span class="sxs-lookup"><span data-stu-id="2e65a-147">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="2e65a-148">Původ zdroje není znám, ale budete potřebovat podporu skriptu.</span><span class="sxs-lookup"><span data-stu-id="2e65a-148">The origin of the source is not known, but you require script support.</span></span>  
  
    -   <span data-ttu-id="2e65a-149">Požadovat doklad volající.</span><span class="sxs-lookup"><span data-stu-id="2e65a-149">Request evidence from the caller.</span></span>  
  
## <a name="transformation-of-xml-data"></a><span data-ttu-id="2e65a-150">Transformace dat XML</span><span class="sxs-lookup"><span data-stu-id="2e65a-150">Transformation of XML Data</span></span>  
 <span data-ttu-id="2e65a-151">Po načtení šablony stylů transformace začne volání jedné z <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody a poskytnutí dokument vstupní zdroj.</span><span class="sxs-lookup"><span data-stu-id="2e65a-151">Once a style sheet is loaded, the transformation starts by calling one of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> methods and supplying an input source document.</span></span> <span data-ttu-id="2e65a-152"><xref:System.Xml.Xsl.XslTransform.Transform%2A> Metoda je přetížena zajistit výstupy různých transformace.</span><span class="sxs-lookup"><span data-stu-id="2e65a-152">The <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is overloaded to provide different transformation outputs.</span></span> <span data-ttu-id="2e65a-153">Transformace může mít za následek následující formáty výstup:</span><span class="sxs-lookup"><span data-stu-id="2e65a-153">The transformation can result in the following output formats:</span></span>  
  
-   <xref:System.Xml.XmlReader>  
  
-   <xref:System.Xml.XmlWriter>  
  
-   <xref:System.IO.TextWriter>  
  
-   <xref:System.IO.Stream>  
  
-   <span data-ttu-id="2e65a-154">Adresa URL řetězec souboru</span><span class="sxs-lookup"><span data-stu-id="2e65a-154">String URL of file</span></span>  
  
 <span data-ttu-id="2e65a-155">Tento poslední formát adresu URL řetězec poskytuje běžně používané scénáři transformace vstupní dokument umístěný v adrese URL a zápis dokumentu na adresu URL výstup.</span><span class="sxs-lookup"><span data-stu-id="2e65a-155">This last format, the string URL, provides for a commonly used scenario in transforming an input document located in a URL and writing the document to the output URL.</span></span> <span data-ttu-id="2e65a-156">To <xref:System.Xml.Xsl.XslTransform.Transform%2A> je užitečný způsob k načítání dokumentu XML ze souboru, provést transformace XSLT a zapisovat výstup do souboru.</span><span class="sxs-lookup"><span data-stu-id="2e65a-156">This <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is a convenience method to load an XML document from a file, perform the XSLT transformation, and write the output to a file.</span></span> <span data-ttu-id="2e65a-157">To zabrání nutnosti vytvoření a načtení dokumentu vstupní zdroj a pak zápis do datového proudu souboru.</span><span class="sxs-lookup"><span data-stu-id="2e65a-157">This prevents you from having to create and load the input source document, and then write to a file stream.</span></span> <span data-ttu-id="2e65a-158">Následující příklad kódu ukazuje, toto využití <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda pomocí adresy URL řetězec jako vstup a výstup:</span><span class="sxs-lookup"><span data-stu-id="2e65a-158">The following code sample shows this use of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method using the string URL as input and output:</span></span>  
  
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
  
## <a name="transforming-a-section-of-an-xml-document"></a><span data-ttu-id="2e65a-159">Transformace části dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="2e65a-159">Transforming a Section of an XML Document</span></span>  
 <span data-ttu-id="2e65a-160">Transformace se vztahují k dokumentu jako celku.</span><span class="sxs-lookup"><span data-stu-id="2e65a-160">Transformations apply to the document as a whole.</span></span> <span data-ttu-id="2e65a-161">Jinými slovy Pokud předáte v uzlu než kořenový uzel dokumentu, toto nezabrání proces transformace přístup na všechny uzly v načíst dokumentu.</span><span class="sxs-lookup"><span data-stu-id="2e65a-161">In other words, if you pass in a node other than the document root node, this does not prevent the transformation process from accessing all nodes in the loaded document.</span></span> <span data-ttu-id="2e65a-162">K transformaci fragment výsledek stromu, musíte vytvořit <xref:System.Xml.XmlDocument> obsahující jenom stromu výsledek fragmentovat a předejte který <xref:System.Xml.XmlDocument> k <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="2e65a-162">To transform a result tree fragment, you must create an <xref:System.Xml.XmlDocument> containing just the result tree fragment and pass that <xref:System.Xml.XmlDocument> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span> <span data-ttu-id="2e65a-163">Následující příklad provádí transformaci fragment stromu výsledek.</span><span class="sxs-lookup"><span data-stu-id="2e65a-163">The following example performs a transformation on a result tree fragment.</span></span>  
  
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
  
 <span data-ttu-id="2e65a-164">V příkladu se používá library.xml a print_root.xsl soubory jako vstupy a výstupy následující ke konzole.</span><span class="sxs-lookup"><span data-stu-id="2e65a-164">The example uses the library.xml and print_root.xsl files as input and outputs the following to the console.</span></span>  
  
```  
Passing <book genre="novel" ISBN="1-861001-57-5"><title>Pride And Prejudice</title></book> to print_root.xsl   
Root node is book.  
```  
  
 <span data-ttu-id="2e65a-165">Library.XML</span><span class="sxs-lookup"><span data-stu-id="2e65a-165">library.xml</span></span>  
  
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
  
 <span data-ttu-id="2e65a-166">print_root.xsl</span><span class="sxs-lookup"><span data-stu-id="2e65a-166">print_root.xsl</span></span>  
  
```xml  
<stylesheet version="1.0" xmlns="http://www.w3.org/1999/XSL/Transform" >  
  <output method="text" />   
  <template match="/">  
     Root node is  <value-of select="local-name(//*[position() = 1])" />   
  </template>  
</stylesheet>  
```  
  
## <a name="migration-of-xslt-from-net-framework-version-10-to-net-framework-version-11"></a><span data-ttu-id="2e65a-167">Migrace XSLT z rozhraní .NET Framework verze 1.0 pro rozhraní .NET Framework verze 1.1</span><span class="sxs-lookup"><span data-stu-id="2e65a-167">Migration of XSLT from .NET Framework version 1.0 to .NET Framework version 1.1</span></span>  
 <span data-ttu-id="2e65a-168">V následující tabulce jsou uvedeny zastaralé [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] metody verze 1.0 a nové [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] metody verze 1.1 <xref:System.Xml.Xsl.XslTransform.Load%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="2e65a-168">The following table shows the obsolete [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.0 methods and new [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.1 methods for the <xref:System.Xml.Xsl.XslTransform.Load%2A> method.</span></span> <span data-ttu-id="2e65a-169">Nové metody umožňují omezit oprávnění šablony stylů zadáním důkaz.</span><span class="sxs-lookup"><span data-stu-id="2e65a-169">The new methods enable you to limit the permissions of the style sheet by specifying evidence.</span></span>  
  
|<span data-ttu-id="2e65a-170">Zastaralé metody zatížení rozhraní .NET Framework verze 1.0</span><span class="sxs-lookup"><span data-stu-id="2e65a-170">Obsolete .NET Framework version 1.0 Load Methods</span></span>|<span data-ttu-id="2e65a-171">Nahrazení rozhraní .NET Framework verze 1.1 zatížení metody</span><span class="sxs-lookup"><span data-stu-id="2e65a-171">Replacement .NET Framework version 1.1 Load Methods</span></span>|  
|------------------------------------------------------|---------------------------------------------------------|  
|<span data-ttu-id="2e65a-172">Načíst (objektem XPathNavigator nastaveným na vstup);</span><span class="sxs-lookup"><span data-stu-id="2e65a-172">Load(XPathNavigator input);</span></span><br /><br /> <span data-ttu-id="2e65a-173">Zatížení (objektem XPathNavigator nastaveným na vstupu, objekt XmlResolver překladač);</span><span class="sxs-lookup"><span data-stu-id="2e65a-173">Load(XPathNavigator input, XmlResolver resolver);</span></span>|<span data-ttu-id="2e65a-174">Zatížení (objektem XPathNavigator nastaveným na šablony stylů, objekt XmlResolver překladač důkaz důkaz);</span><span class="sxs-lookup"><span data-stu-id="2e65a-174">Load(XPathNavigator stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|  
|<span data-ttu-id="2e65a-175">Načíst (IXPathNavigable šablony stylů);</span><span class="sxs-lookup"><span data-stu-id="2e65a-175">Load(IXPathNavigable stylesheet);</span></span><br /><br /> <span data-ttu-id="2e65a-176">Zatížení (IXPathNavigable stylů, objekt XmlResolver překladač);</span><span class="sxs-lookup"><span data-stu-id="2e65a-176">Load(IXPathNavigable stylesheet, XmlResolver resolver);</span></span>|<span data-ttu-id="2e65a-177">Zatížení (IXPathNavigable stylů, objekt XmlResolver překladač důkaz důkaz);</span><span class="sxs-lookup"><span data-stu-id="2e65a-177">Load(IXPathNavigable stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|  
|<span data-ttu-id="2e65a-178">Načíst (XmlReader šablony stylů);</span><span class="sxs-lookup"><span data-stu-id="2e65a-178">Load(XmlReader stylesheet);</span></span><br /><br /> <span data-ttu-id="2e65a-179">Zatížení (XmlReader stylů, objekt XmlResolver překladač);</span><span class="sxs-lookup"><span data-stu-id="2e65a-179">Load(XmlReader stylesheet, XmlResolver resolver);</span></span>|<span data-ttu-id="2e65a-180">Zatížení (XmlReader stylů, objekt XmlResolver překladač důkaz důkaz);</span><span class="sxs-lookup"><span data-stu-id="2e65a-180">Load(XmlReader stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|  
  
 <span data-ttu-id="2e65a-181">V následující tabulce jsou zastaralé a nové metody pro <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="2e65a-181">The following table shows the obsolete and new methods for the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span> <span data-ttu-id="2e65a-182">Nové metody přijímají <xref:System.Xml.XmlResolver> objektu.</span><span class="sxs-lookup"><span data-stu-id="2e65a-182">The new methods take an <xref:System.Xml.XmlResolver> object.</span></span>  
  
|<span data-ttu-id="2e65a-183">Zastaralé metody transformace rozhraní .NET Framework verze 1.0</span><span class="sxs-lookup"><span data-stu-id="2e65a-183">Obsolete .NET Framework version 1.0 Transform Methods</span></span>|<span data-ttu-id="2e65a-184">Nahrazení rozhraní .NET Framework verze 1.1 metody transformace</span><span class="sxs-lookup"><span data-stu-id="2e65a-184">Replacement .NET Framework version Transform 1.1 Methods</span></span>|  
|-----------------------------------------------------------|--------------------------------------------------------------|  
|<span data-ttu-id="2e65a-185">XmlReader Transform(XPathNavigator input, XsltArgumentList args)</span><span class="sxs-lookup"><span data-stu-id="2e65a-185">XmlReader Transform(XPathNavigator input, XsltArgumentList args)</span></span>|<span data-ttu-id="2e65a-186">XmlReader Transform(XPathNavigator input, XsltArgumentList args, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="2e65a-186">XmlReader Transform(XPathNavigator  input, XsltArgumentList args, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="2e65a-187">XmlReader Transform(IXPathNavigable input, XsltArgumentList args)</span><span class="sxs-lookup"><span data-stu-id="2e65a-187">XmlReader Transform(IXPathNavigable input, XsltArgumentList args)</span></span>|<span data-ttu-id="2e65a-188">XmlReader Transform(IXPathNavigable input, XsltArgumentList args, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="2e65a-188">XmlReader Transform(IXPathNavigable input, XsltArgumentList args, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="2e65a-189">Transformace void (objektem XPathNavigator nastaveným na vstup, třída XsltArgumentList argumentů, XmlWriter výstup)</span><span class="sxs-lookup"><span data-stu-id="2e65a-189">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output)</span></span>|<span data-ttu-id="2e65a-190">Transformace void (objektem XPathNavigator nastaveným na vstup, třída XsltArgumentList argumentů, XmlWriter výstup, objekt XmlResolver překladač)</span><span class="sxs-lookup"><span data-stu-id="2e65a-190">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="2e65a-191">Transformace void (IXPathNavigable vstup, třída XsltArgumentList argumentů, XmlWriter výstup)</span><span class="sxs-lookup"><span data-stu-id="2e65a-191">Void Transform(IXPathNavigable input, XsltArgumentList args, XmlWriter output)</span></span>|<span data-ttu-id="2e65a-192">Transformace void (IXpathNavigable vstup, třída XsltArgumentList argumentů, XmlWriter výstup, objekt XmlResolver překladač)</span><span class="sxs-lookup"><span data-stu-id="2e65a-192">Void Transform(IXpathNavigable input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="2e65a-193">Transformace void (objektem XPathNavigator nastaveným na vstup, třída XsltArgumentList argumentů výstup TextWriter.)</span><span class="sxs-lookup"><span data-stu-id="2e65a-193">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output)</span></span>|<span data-ttu-id="2e65a-194">Transformace void (objektem XPathNavigator nastaveným na vstup, třída XsltArgumentList argumentů, výstup TextWriter, objekt XmlResolver překladač)</span><span class="sxs-lookup"><span data-stu-id="2e65a-194">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="2e65a-195">Transformace void (IXPathNavigable vstup, třída XsltArgumentList argumentů výstup TextWriter.)</span><span class="sxs-lookup"><span data-stu-id="2e65a-195">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output)</span></span>|<span data-ttu-id="2e65a-196">Transformace void (IXPathNavigable vstup, třída XsltArgumentList argumentů, výstup TextWriter, objekt XmlResolver překladač)</span><span class="sxs-lookup"><span data-stu-id="2e65a-196">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="2e65a-197">Transformace void (objektem XPathNavigator nastaveným na vstup, třída XsltArgumentList argumentů výstup datového proudu.)</span><span class="sxs-lookup"><span data-stu-id="2e65a-197">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output)</span></span>|<span data-ttu-id="2e65a-198">Transformace void (objektem XPathNavigator nastaveným na vstup, třída XsltArgumentList argumentů, výstup datového proudu, objekt XmlResolver překladač)</span><span class="sxs-lookup"><span data-stu-id="2e65a-198">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="2e65a-199">Transformace void (IXPathNavigable vstup, třída XsltArgumentList argumentů výstup datového proudu.)</span><span class="sxs-lookup"><span data-stu-id="2e65a-199">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output)</span></span>|<span data-ttu-id="2e65a-200">Transformace void (IXPathNavigable vstup, třída XsltArgumentList argumentů, výstup datového proudu, objekt XmlResolver překladač)</span><span class="sxs-lookup"><span data-stu-id="2e65a-200">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="2e65a-201">Void transformace (řetězec vstupní, výstupní řetězec);</span><span class="sxs-lookup"><span data-stu-id="2e65a-201">Void Transform(String input, String output);</span></span>|<span data-ttu-id="2e65a-202">Void transformace (řetězec vstupní, výstupní řetězec, objekt XmlResolver překladač);</span><span class="sxs-lookup"><span data-stu-id="2e65a-202">Void Transform(String input, String output, XmlResolver resolver);</span></span>|  
  
 <span data-ttu-id="2e65a-203"><xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> Vlastnost je zastaralá ve [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.1.</span><span class="sxs-lookup"><span data-stu-id="2e65a-203">The <xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> property is obsolete in [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.1.</span></span> <span data-ttu-id="2e65a-204">Místo toho použít novou <xref:System.Xml.Xsl.XslTransform.Transform%2A> přetížení, která berou <xref:System.Xml.XmlResolver> objektu.</span><span class="sxs-lookup"><span data-stu-id="2e65a-204">Instead, use the new <xref:System.Xml.Xsl.XslTransform.Transform%2A> overloads which take an <xref:System.Xml.XmlResolver> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e65a-205">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e65a-205">See Also</span></span>  
 <xref:System.Xml.Xsl.XslTransform>  
 [<span data-ttu-id="2e65a-206">Transformace XSLT pomocí XslTransform – třída</span><span class="sxs-lookup"><span data-stu-id="2e65a-206">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [<span data-ttu-id="2e65a-207">Objektem XPathNavigator nastaveným v transformace</span><span class="sxs-lookup"><span data-stu-id="2e65a-207">XPathNavigator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [<span data-ttu-id="2e65a-208">XPathNodeIterator v transformace</span><span class="sxs-lookup"><span data-stu-id="2e65a-208">XPathNodeIterator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [<span data-ttu-id="2e65a-209">Vstup XPathDocument XslTransform</span><span class="sxs-lookup"><span data-stu-id="2e65a-209">XPathDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [<span data-ttu-id="2e65a-210">XmlDataDocument vstup XslTransform</span><span class="sxs-lookup"><span data-stu-id="2e65a-210">XmlDataDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
 [<span data-ttu-id="2e65a-211">Třídou XMLDocument nastavenou na vstup XslTransform</span><span class="sxs-lookup"><span data-stu-id="2e65a-211">XmlDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
