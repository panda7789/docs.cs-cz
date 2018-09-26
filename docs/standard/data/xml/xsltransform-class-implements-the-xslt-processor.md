---
title: Třída XslTransform implementuje procesor XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 88373fe2-4a6b-44f9-8a62-8a3e348e3a46
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 81d0ce4f697935908b8ad7084560bd1adacbdf2d
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47090419"
---
# <a name="xsltransform-class-implements-the-xslt-processor"></a><span data-ttu-id="74765-102">Třída XslTransform implementuje procesor XSLT</span><span class="sxs-lookup"><span data-stu-id="74765-102">XslTransform Class Implements the XSLT Processor</span></span>
> [!NOTE]
>  <span data-ttu-id="74765-103"><xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="74765-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="74765-104">Můžete provádět rozšiřitelný jazyk šablony stylů transformace XSLT () transformaci pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="74765-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="74765-105">Zobrazit [používání třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="74765-105">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="74765-106"><xref:System.Xml.Xsl.XslTransform> Třída je procesor XSLT implementaci transformace XSL (XSLT) verze 1.0 doporučení.</span><span class="sxs-lookup"><span data-stu-id="74765-106">The <xref:System.Xml.Xsl.XslTransform> class is an XSLT processor implementing the XSL Transformations (XSLT) Version 1.0 recommendation.</span></span> <span data-ttu-id="74765-107"><xref:System.Xml.Xsl.XslTransform.Load%2A> Metoda vyhledá a načte šablony stylů a <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda transformuje daném zdrojovém dokumentu.</span><span class="sxs-lookup"><span data-stu-id="74765-107">The <xref:System.Xml.Xsl.XslTransform.Load%2A> method locates and reads style sheets, and the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method transforms the given source document.</span></span> <span data-ttu-id="74765-108">Jakékoli úložiště, který implementuje <xref:System.Xml.XPath.IXPathNavigable> rozhraní lze použít jako zdrojový dokument pro <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="74765-108">Any store that implements the <xref:System.Xml.XPath.IXPathNavigable> interface can be used as the source document for the <xref:System.Xml.Xsl.XslTransform>.</span></span> <span data-ttu-id="74765-109">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Aktuálně implementuje <xref:System.Xml.XPath.IXPathNavigable> rozhraní na <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument>a <xref:System.Xml.XPath.XPathDocument>, takže všechny z nich může sloužit jako vstupní zdrojový dokument k transformaci.</span><span class="sxs-lookup"><span data-stu-id="74765-109">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] currently implements the <xref:System.Xml.XPath.IXPathNavigable> interface on the <xref:System.Xml.XmlDocument>, the <xref:System.Xml.XmlDataDocument>, and the <xref:System.Xml.XPath.XPathDocument>, so all of these can be used as the input source document to a transformation.</span></span>  
  
 <span data-ttu-id="74765-110"><xref:System.Xml.Xsl.XslTransform> Objekt [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] podporuje pouze specifikaci XSLT 1.0, definované pomocí následující obor názvů:</span><span class="sxs-lookup"><span data-stu-id="74765-110">The <xref:System.Xml.Xsl.XslTransform> object in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] only supports the XSLT 1.0 specification, defined with the following namespace:</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">    
```  
  
 <span data-ttu-id="74765-111">Šablony stylů můžete načíst pomocí <xref:System.Xml.Xsl.XslTransform.Load%2A> metoda z jednoho z následujících tříd:</span><span class="sxs-lookup"><span data-stu-id="74765-111">The style sheet can be loaded, using the <xref:System.Xml.Xsl.XslTransform.Load%2A> method, from one of the following classes:</span></span>  
  
-   <span data-ttu-id="74765-112">XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="74765-112">XPathNavigator</span></span>  
  
-   <span data-ttu-id="74765-113">Objekt XmlReader</span><span class="sxs-lookup"><span data-stu-id="74765-113">XmlReader</span></span>  
  
-   <span data-ttu-id="74765-114">Řetězec představující adresu URL</span><span class="sxs-lookup"><span data-stu-id="74765-114">A string representing a URL</span></span>  
  
 <span data-ttu-id="74765-115">Existuje jiný <xref:System.Xml.Xsl.XslTransform.Load%2A> metoda pro každou z výše uvedených vstupní tříd.</span><span class="sxs-lookup"><span data-stu-id="74765-115">There is a different <xref:System.Xml.Xsl.XslTransform.Load%2A> method for each of the above input classes.</span></span> <span data-ttu-id="74765-116">Některé metody trvat, než se kombinace jedné z těchto tříd a <xref:System.Xml.XmlResolver> třídu jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="74765-116">Some methods take in a combination of one of these classes and the <xref:System.Xml.XmlResolver> class as arguments.</span></span> <span data-ttu-id="74765-117"><xref:System.Xml.XmlResolver> Vyhledává prostředky odkazuje `<xsl:import>` nebo `<xsl:include>` najít v šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="74765-117">The <xref:System.Xml.XmlResolver> locates resources referenced by `<xsl:import>` or `<xsl:include>` found in the style sheet.</span></span> <span data-ttu-id="74765-118">Následující metody přijímají řetězce, <xref:System.Xml.XmlReader>, nebo <xref:System.Xml.XPath.XPathNavigator> jako vstup.</span><span class="sxs-lookup"><span data-stu-id="74765-118">The following methods take a string, <xref:System.Xml.XmlReader>, or <xref:System.Xml.XPath.XPathNavigator> as input.</span></span>  
  
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
  
 <span data-ttu-id="74765-119">Většina <xref:System.Xml.Xsl.XslTransform.Load%2A> metody uvedené nahoře využijte <xref:System.Xml.XmlResolver> jako parametr.</span><span class="sxs-lookup"><span data-stu-id="74765-119">Most of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods shown above take an <xref:System.Xml.XmlResolver> as a parameter.</span></span> <span data-ttu-id="74765-120"><xref:System.Xml.XmlResolver> Slouží k načtení šablony stylů a všechny seznamy stylu odkazuje XSL: Import a xsl: zahrnout elementy.</span><span class="sxs-lookup"><span data-stu-id="74765-120">The <xref:System.Xml.XmlResolver> is used to load the style sheet and any style sheet(s) referenced in xsl:import and xsl:include elements.</span></span>  
  
 <span data-ttu-id="74765-121">Většina <xref:System.Xml.Xsl.XslTransform.Load%2A> taky využít důkazy jako parametr metody.</span><span class="sxs-lookup"><span data-stu-id="74765-121">Most of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods also take evidence as a parameter.</span></span> <span data-ttu-id="74765-122">Parametr důkazy je <xref:System.Security.Policy.Evidence> přidružený k šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="74765-122">The evidence parameter is the <xref:System.Security.Policy.Evidence> that is associated with the style sheet.</span></span> <span data-ttu-id="74765-123">Úroveň zabezpečení šablony stylů má vliv na následné prostředků, odkazuje na úroveň zabezpečení, jako je například skript obsahuje, všechny `document()` funkce používá a všechny objekty, rozšíření používané <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="74765-123">The security level of the style sheet affects the security level of any subsequent resources it references, such as the script it contains, any `document()` functions it uses, and any extension objects used by the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>  
  
 <span data-ttu-id="74765-124">Pokud je načten pomocí šablony stylů <xref:System.Xml.Xsl.XslTransform.Load%2A> poskytuje metodu, která obsahuje parametr adresy URL a žádné legitimaci, díky kombinaci dané adrese URL s jeho lokality a zóny se počítá doklad o šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="74765-124">If the style sheet is loaded using a <xref:System.Xml.Xsl.XslTransform.Load%2A> method that contains a URL parameter and no evidence is provided, the evidence of the style sheet is calculated by combining the given URL with its site and zone.</span></span>  
  
 <span data-ttu-id="74765-125">Pokud je k dispozici žádný identifikátor URI nebo doklad, důkazy pro šablony stylů je plně důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="74765-125">If no URI or evidence is provided, then the evidence set for the style sheet is fully trusted.</span></span> <span data-ttu-id="74765-126">Načtení šablony stylů z nedůvěryhodných zdrojů, ani přidat objekty nedůvěryhodné rozšíření do <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="74765-126">Do not load style sheets from untrusted sources, or add untrusted extension objects into the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>  
  
 <span data-ttu-id="74765-127">Další informace o úrovně zabezpečení a důkazy a o jejím dopadu skriptování najdete v tématu [pomocí skriptování šablony stylů XSLT \<msxsl: script >](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md).</span><span class="sxs-lookup"><span data-stu-id="74765-127">For more information about security levels and evidence and how it affects scripting, see [XSLT Stylesheet Scripting Using \<msxsl:script>](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md).</span></span> <span data-ttu-id="74765-128">Informace o úrovně zabezpečení a důkazy a o jejím dopadu objektů rozšíření najdete v tématu [třída XsltArgumentList pro parametry list stylu a objektů rozšíření](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).</span><span class="sxs-lookup"><span data-stu-id="74765-128">For information about security levels and evidence and how it affects extension objects, see [XsltArgumentList for Style Sheet Parameters and Extension Objects](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).</span></span>  
  
 <span data-ttu-id="74765-129">Informace o úrovně zabezpečení a důkazy a o jejím dopadu `document()` funkce naleznete v tématu [překlad externích šablon stylů XSLT a dokumenty](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md).</span><span class="sxs-lookup"><span data-stu-id="74765-129">For information about security levels and evidence and how it affects the `document()` function, see [Resolving External XSLT Style Sheets and Documents](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md).</span></span>  
  
 <span data-ttu-id="74765-130">Šablona stylů můžete zadat s počtem vstupních parametrů.</span><span class="sxs-lookup"><span data-stu-id="74765-130">A style sheet can be supplied with a number of input parameters.</span></span> <span data-ttu-id="74765-131">Funkce šablony stylů můžete také volat u objektů rozšíření.</span><span class="sxs-lookup"><span data-stu-id="74765-131">The style sheet can also call functions on extension objects.</span></span> <span data-ttu-id="74765-132">Parametry a objektů rozšíření jsou dodávány pomocí list stylu <xref:System.Xml.Xsl.XsltArgumentList> třídy.</span><span class="sxs-lookup"><span data-stu-id="74765-132">Both parameters and extension objects are supplied to the style sheet using the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span> <span data-ttu-id="74765-133">Další informace o <xref:System.Xml.Xsl.XsltArgumentList>, naleznete v tématu <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="74765-133">For more information about the <xref:System.Xml.Xsl.XsltArgumentList>, see <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>  
  
## <a name="recommended-secure-use-of-xsltransform-class"></a><span data-ttu-id="74765-134">Doporučené zabezpečení použití třídy XslTransform</span><span class="sxs-lookup"><span data-stu-id="74765-134">Recommended Secure Use of XslTransform Class</span></span>  
 <span data-ttu-id="74765-135">Oprávnění zabezpečení šablony stylů, závisí na důkazy, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="74765-135">The security privileges of the style sheet depend on the evidence provided.</span></span> <span data-ttu-id="74765-136">Následující tabulka shrnuje umístění šablony stylů a poskytuje vysvětlení, co typu legitimací poskytnout.</span><span class="sxs-lookup"><span data-stu-id="74765-136">The following table summarizes the location of the style sheet and gives an explanation of what type of evidence to give.</span></span>  
  
-   <span data-ttu-id="74765-137">Šablony stylů XSLT nemá žádné externí odkazy nebo šablony stylů pochází ze základu kódu, které důvěřujete.</span><span class="sxs-lookup"><span data-stu-id="74765-137">The XSLT style sheet has no external references, or the style sheet comes from a code base that you trust.</span></span>  
  
    -   <span data-ttu-id="74765-138">Poskytnout důkazy z vašeho sestavení:</span><span class="sxs-lookup"><span data-stu-id="74765-138">Provide the evidence from your assembly:</span></span>  
  
         `Dim xslt = New XslTransform() xslt.Load(stylesheet, resolver, Me.GetType().Assembly.Evidence)`  
  
         `XsltTransform xslt = new XslTransform();  xslt.Load(stylesheet, resolver, this.GetType().Assembly.Evidence);`  
  
-   <span data-ttu-id="74765-139">Šablony stylů XSLT pochází z vnějšího zdroje.</span><span class="sxs-lookup"><span data-stu-id="74765-139">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="74765-140">Označuje původu zdroje a není ověřitelný identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="74765-140">The origin of the source is known and there is a verifiable URI.</span></span>  
  
    -   <span data-ttu-id="74765-141">Vytvoření důkazy použitím tohoto identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="74765-141">Create evidence using the URI.</span></span>  
  
         `Dim xslt As New XslTransform() Dim ev As Evidence = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri) xslt.Load(stylesheet, resolver, evidence)`  
  
         `XslTransform xslt = new XslTransform(); Evidence ev = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri); xslt.Load(stylesheet, resolver, evidence);`  
  
-   <span data-ttu-id="74765-142">Šablony stylů XSLT pochází z vnějšího zdroje.</span><span class="sxs-lookup"><span data-stu-id="74765-142">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="74765-143">Původní zdroj není známý.</span><span class="sxs-lookup"><span data-stu-id="74765-143">The origin of the source is not known.</span></span>  
  
    -   <span data-ttu-id="74765-144">Nastavte na důkaz `null`.</span><span class="sxs-lookup"><span data-stu-id="74765-144">Set evidence to `null`.</span></span> <span data-ttu-id="74765-145">Bloky kódu skriptu nejsou zpracovány, XSLT `document()` funkce není podporována a objektů privilegovaných rozšíření jsou zakázána.</span><span class="sxs-lookup"><span data-stu-id="74765-145">Script blocks are not processed, the XSLT `document()` function is not supported, and privileged extension objects are disallowed.</span></span>  
  
         <span data-ttu-id="74765-146">Kromě toho můžete také nastavit `resolver` parametr `null` to zajistí, že `xsl:import` a `xsl:include` nejsou zpracovávány elementy.</span><span class="sxs-lookup"><span data-stu-id="74765-146">Additionally, you can also set the `resolver` parameter to `null` This ensures that `xsl:import` and `xsl:include` elements are not processed.</span></span>  
  
-   <span data-ttu-id="74765-147">Šablony stylů XSLT pochází z vnějšího zdroje.</span><span class="sxs-lookup"><span data-stu-id="74765-147">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="74765-148">Původní zdroj není znám, ale budete potřebovat podporu skriptu.</span><span class="sxs-lookup"><span data-stu-id="74765-148">The origin of the source is not known, but you require script support.</span></span>  
  
    -   <span data-ttu-id="74765-149">Žádost o legitimaci od volajícího.</span><span class="sxs-lookup"><span data-stu-id="74765-149">Request evidence from the caller.</span></span>  
  
## <a name="transformation-of-xml-data"></a><span data-ttu-id="74765-150">Transformaci dat XML</span><span class="sxs-lookup"><span data-stu-id="74765-150">Transformation of XML Data</span></span>  
 <span data-ttu-id="74765-151">Po načtení šablony stylů transformace začíná voláním jedné z <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody a poskytnutí vstupní zdrojový dokument.</span><span class="sxs-lookup"><span data-stu-id="74765-151">Once a style sheet is loaded, the transformation starts by calling one of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> methods and supplying an input source document.</span></span> <span data-ttu-id="74765-152"><xref:System.Xml.Xsl.XslTransform.Transform%2A> Je přetížena metoda poskytnout různé transformace výstupy.</span><span class="sxs-lookup"><span data-stu-id="74765-152">The <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is overloaded to provide different transformation outputs.</span></span> <span data-ttu-id="74765-153">Transformace může mít za následek následující formáty výstupu:</span><span class="sxs-lookup"><span data-stu-id="74765-153">The transformation can result in the following output formats:</span></span>  
  
-   <xref:System.Xml.XmlReader>  
  
-   <xref:System.Xml.XmlWriter>  
  
-   <xref:System.IO.TextWriter>  
  
-   <xref:System.IO.Stream>  
  
-   <span data-ttu-id="74765-154">Adresa URL řetězec souboru</span><span class="sxs-lookup"><span data-stu-id="74765-154">String URL of file</span></span>  
  
 <span data-ttu-id="74765-155">Tento poslední formát URL řetězec poskytuje běžně používané scénáři transformují vstupní dokument nachází v adrese URL a zápis dokumentu do výstupní adresy URL.</span><span class="sxs-lookup"><span data-stu-id="74765-155">This last format, the string URL, provides for a commonly used scenario in transforming an input document located in a URL and writing the document to the output URL.</span></span> <span data-ttu-id="74765-156">To <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda je metoda pohodlí k načítání dokumentu XML ze souboru, provedení transformace XSLT a zapisovat výstup do souboru.</span><span class="sxs-lookup"><span data-stu-id="74765-156">This <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is a convenience method to load an XML document from a file, perform the XSLT transformation, and write the output to a file.</span></span> <span data-ttu-id="74765-157">To zabrání by bylo nutné vytvořit a načíst vstupní zdrojový dokument a pak zápis do datového proudu souboru.</span><span class="sxs-lookup"><span data-stu-id="74765-157">This prevents you from having to create and load the input source document, and then write to a file stream.</span></span> <span data-ttu-id="74765-158">Následující příklad kódu ukazuje toto použití <xref:System.Xml.Xsl.XslTransform.Transform%2A> metodu pomocí adresy URL řetězec jako vstup a výstup:</span><span class="sxs-lookup"><span data-stu-id="74765-158">The following code sample shows this use of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method using the string URL as input and output:</span></span>  
  
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
  
## <a name="transforming-a-section-of-an-xml-document"></a><span data-ttu-id="74765-159">Transformace část dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="74765-159">Transforming a Section of an XML Document</span></span>  
 <span data-ttu-id="74765-160">Transformace se vztahují k dokumentu jako celek.</span><span class="sxs-lookup"><span data-stu-id="74765-160">Transformations apply to the document as a whole.</span></span> <span data-ttu-id="74765-161">Jinými slovy Pokud předáte v uzlu, než je kořenový uzel dokumentu, toto nezabraňuje proces transformace přístup na všechny uzly v načtený dokument.</span><span class="sxs-lookup"><span data-stu-id="74765-161">In other words, if you pass in a node other than the document root node, this does not prevent the transformation process from accessing all nodes in the loaded document.</span></span> <span data-ttu-id="74765-162">K transformaci fragment stromu výsledek, musíte vytvořit <xref:System.Xml.XmlDocument> obsahující stromu výsledek fragment a předat ho <xref:System.Xml.XmlDocument> k <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="74765-162">To transform a result tree fragment, you must create an <xref:System.Xml.XmlDocument> containing just the result tree fragment and pass that <xref:System.Xml.XmlDocument> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span> <span data-ttu-id="74765-163">Následující příklad provede transformaci fragment stromu výsledek.</span><span class="sxs-lookup"><span data-stu-id="74765-163">The following example performs a transformation on a result tree fragment.</span></span>  
  
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
  
 <span data-ttu-id="74765-164">V příkladu se používá library.xml print_root.xsl soubory a jako vstup a vrátí tento výstup do konzoly.</span><span class="sxs-lookup"><span data-stu-id="74765-164">The example uses the library.xml and print_root.xsl files as input and outputs the following to the console.</span></span>  
  
```  
Passing <book genre="novel" ISBN="1-861001-57-5"><title>Pride And Prejudice</title></book> to print_root.xsl   
Root node is book.  
```  
  
 <span data-ttu-id="74765-165">Library.XML</span><span class="sxs-lookup"><span data-stu-id="74765-165">library.xml</span></span>  
  
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
  
 <span data-ttu-id="74765-166">print_root.xsl</span><span class="sxs-lookup"><span data-stu-id="74765-166">print_root.xsl</span></span>  
  
```xml  
<stylesheet version="1.0" xmlns="http://www.w3.org/1999/XSL/Transform" >  
  <output method="text" />   
  <template match="/">  
     Root node is  <value-of select="local-name(//*[position() = 1])" />   
  </template>  
</stylesheet>  
```  
  
## <a name="migration-of-xslt-from-net-framework-version-10-to-net-framework-version-11"></a><span data-ttu-id="74765-167">Migrace XSLT v rozhraní .NET Framework verze 1.0 rozhraní .NET Framework verze 1.1</span><span class="sxs-lookup"><span data-stu-id="74765-167">Migration of XSLT from .NET Framework version 1.0 to .NET Framework version 1.1</span></span>  
 <span data-ttu-id="74765-168">V následující tabulce jsou uvedeny zastaralý [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] metody verze 1.0 a nové [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] metody verze 1.1 <xref:System.Xml.Xsl.XslTransform.Load%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="74765-168">The following table shows the obsolete [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.0 methods and new [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.1 methods for the <xref:System.Xml.Xsl.XslTransform.Load%2A> method.</span></span> <span data-ttu-id="74765-169">Nové metody umožňují omezit oprávnění šablony stylů zadáním důkaz.</span><span class="sxs-lookup"><span data-stu-id="74765-169">The new methods enable you to limit the permissions of the style sheet by specifying evidence.</span></span>  
  
|<span data-ttu-id="74765-170">Zastaralé metod rozhraní .NET Framework verze 1.0 zatížení</span><span class="sxs-lookup"><span data-stu-id="74765-170">Obsolete .NET Framework version 1.0 Load Methods</span></span>|<span data-ttu-id="74765-171">Náhradní rozhraní .NET Framework verze 1.1 zatížení metody</span><span class="sxs-lookup"><span data-stu-id="74765-171">Replacement .NET Framework version 1.1 Load Methods</span></span>|  
|------------------------------------------------------|---------------------------------------------------------|  
|<span data-ttu-id="74765-172">Načtení (objektem XPathNavigator nastaveným na vstupu);</span><span class="sxs-lookup"><span data-stu-id="74765-172">Load(XPathNavigator input);</span></span><br /><br /> <span data-ttu-id="74765-173">Load (objektem XPathNavigator nastaveným na vstupu, objekt XmlResolver překladač);</span><span class="sxs-lookup"><span data-stu-id="74765-173">Load(XPathNavigator input, XmlResolver resolver);</span></span>|<span data-ttu-id="74765-174">Zatížení (Šablona stylů objektem XPathNavigator nastaveným na, objekt XmlResolver překladače, důkazy důkazy);</span><span class="sxs-lookup"><span data-stu-id="74765-174">Load(XPathNavigator stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|  
|<span data-ttu-id="74765-175">Zatížení (Šablona stylů IXPathNavigable);</span><span class="sxs-lookup"><span data-stu-id="74765-175">Load(IXPathNavigable stylesheet);</span></span><br /><br /> <span data-ttu-id="74765-176">Zatížení (Šablona stylů IXPathNavigable, objekt XmlResolver překladač);</span><span class="sxs-lookup"><span data-stu-id="74765-176">Load(IXPathNavigable stylesheet, XmlResolver resolver);</span></span>|<span data-ttu-id="74765-177">Zatížení (Šablona stylů IXPathNavigable, objekt XmlResolver překladače, důkazy důkazy);</span><span class="sxs-lookup"><span data-stu-id="74765-177">Load(IXPathNavigable stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|  
|<span data-ttu-id="74765-178">Zatížení (Šablona stylů XmlReader);</span><span class="sxs-lookup"><span data-stu-id="74765-178">Load(XmlReader stylesheet);</span></span><br /><br /> <span data-ttu-id="74765-179">Zatížení (Šablona stylů XmlReader, objekt XmlResolver překladač);</span><span class="sxs-lookup"><span data-stu-id="74765-179">Load(XmlReader stylesheet, XmlResolver resolver);</span></span>|<span data-ttu-id="74765-180">Zatížení (Šablona stylů XmlReader, objekt XmlResolver překladač, důkazy důkazy);</span><span class="sxs-lookup"><span data-stu-id="74765-180">Load(XmlReader stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|  
  
 <span data-ttu-id="74765-181">V následující tabulce jsou uvedeny zastaralé a nové metody pro <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="74765-181">The following table shows the obsolete and new methods for the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span> <span data-ttu-id="74765-182">Využijte nové metody <xref:System.Xml.XmlResolver> objektu.</span><span class="sxs-lookup"><span data-stu-id="74765-182">The new methods take an <xref:System.Xml.XmlResolver> object.</span></span>  
  
|<span data-ttu-id="74765-183">Zastaralé metody transformace rozhraní .NET Framework verze 1.0</span><span class="sxs-lookup"><span data-stu-id="74765-183">Obsolete .NET Framework version 1.0 Transform Methods</span></span>|<span data-ttu-id="74765-184">Nahrazení verzi rozhraní .NET Framework 1.1 metody transformace</span><span class="sxs-lookup"><span data-stu-id="74765-184">Replacement .NET Framework version Transform 1.1 Methods</span></span>|  
|-----------------------------------------------------------|--------------------------------------------------------------|  
|<span data-ttu-id="74765-185">Objekt XmlReader Transform(XPathNavigator input, XsltArgumentList args)</span><span class="sxs-lookup"><span data-stu-id="74765-185">XmlReader Transform(XPathNavigator input, XsltArgumentList args)</span></span>|<span data-ttu-id="74765-186">Objekt XmlReader Transform(XPathNavigator input, XsltArgumentList args, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="74765-186">XmlReader Transform(XPathNavigator  input, XsltArgumentList args, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="74765-187">Objekt XmlReader Transform(IXPathNavigable input, XsltArgumentList args)</span><span class="sxs-lookup"><span data-stu-id="74765-187">XmlReader Transform(IXPathNavigable input, XsltArgumentList args)</span></span>|<span data-ttu-id="74765-188">Objekt XmlReader Transform(IXPathNavigable input, XsltArgumentList args, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="74765-188">XmlReader Transform(IXPathNavigable input, XsltArgumentList args, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="74765-189">Transformace void (objektem XPathNavigator nastaveným na vstup, třída XsltArgumentList argumentů, XmlWriter výstup)</span><span class="sxs-lookup"><span data-stu-id="74765-189">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output)</span></span>|<span data-ttu-id="74765-190">Void transformace (objektem XPathNavigator nastaveným na vstup, třída XsltArgumentList argumentů, výstup XmlWriter, objekt XmlResolver překladač)</span><span class="sxs-lookup"><span data-stu-id="74765-190">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="74765-191">Transformace void (IXPathNavigable vstup, třída XsltArgumentList argumentů, XmlWriter výstup)</span><span class="sxs-lookup"><span data-stu-id="74765-191">Void Transform(IXPathNavigable input, XsltArgumentList args, XmlWriter output)</span></span>|<span data-ttu-id="74765-192">Transformace void (IXpathNavigable vstup, třída XsltArgumentList argumentů, výstup XmlWriter, objekt XmlResolver překladač)</span><span class="sxs-lookup"><span data-stu-id="74765-192">Void Transform(IXpathNavigable input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="74765-193">Transformace void (objektem XPathNavigator nastaveným na vstup, třída XsltArgumentList argumentů, TextWriter výstup)</span><span class="sxs-lookup"><span data-stu-id="74765-193">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output)</span></span>|<span data-ttu-id="74765-194">Transformace void (objektem XPathNavigator nastaveným na vstup, třída XsltArgumentList argumentů, TextWriter výstup, objekt XmlResolver překladač)</span><span class="sxs-lookup"><span data-stu-id="74765-194">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="74765-195">Transformace void (IXPathNavigable vstup, třída XsltArgumentList argumentů, TextWriter výstup)</span><span class="sxs-lookup"><span data-stu-id="74765-195">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output)</span></span>|<span data-ttu-id="74765-196">Transformace void (IXPathNavigable vstup, třída XsltArgumentList argumentů, TextWriter výstup, objekt XmlResolver překladač)</span><span class="sxs-lookup"><span data-stu-id="74765-196">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="74765-197">Transformace void (objektem XPathNavigator nastaveným na vstup, třída XsltArgumentList argumentů, Stream výstup)</span><span class="sxs-lookup"><span data-stu-id="74765-197">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output)</span></span>|<span data-ttu-id="74765-198">Void transformace (objektem XPathNavigator nastaveným na vstup, třída XsltArgumentList argumentů, výstupní Stream, objekt XmlResolver překladač)</span><span class="sxs-lookup"><span data-stu-id="74765-198">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="74765-199">Transformace void (IXPathNavigable vstup, třída XsltArgumentList argumentů, Stream výstup)</span><span class="sxs-lookup"><span data-stu-id="74765-199">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output)</span></span>|<span data-ttu-id="74765-200">Transformace void (IXPathNavigable vstup, třída XsltArgumentList argumentů, výstupní Stream, objekt XmlResolver překladač)</span><span class="sxs-lookup"><span data-stu-id="74765-200">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="74765-201">Zrušit transformaci (řetězec vstupní, výstupní řetězec);</span><span class="sxs-lookup"><span data-stu-id="74765-201">Void Transform(String input, String output);</span></span>|<span data-ttu-id="74765-202">Zrušit transformaci (řetězec vstupní, výstupní řetězec, objekt XmlResolver překladač);</span><span class="sxs-lookup"><span data-stu-id="74765-202">Void Transform(String input, String output, XmlResolver resolver);</span></span>|  
  
 <span data-ttu-id="74765-203"><xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> Vlastnost je zastaralá v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.1.</span><span class="sxs-lookup"><span data-stu-id="74765-203">The <xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> property is obsolete in [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.1.</span></span> <span data-ttu-id="74765-204">Místo toho použijte nové <xref:System.Xml.Xsl.XslTransform.Transform%2A> přetížení, která berou <xref:System.Xml.XmlResolver> objektu.</span><span class="sxs-lookup"><span data-stu-id="74765-204">Instead, use the new <xref:System.Xml.Xsl.XslTransform.Transform%2A> overloads which take an <xref:System.Xml.XmlResolver> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74765-205">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74765-205">See also</span></span>

- <xref:System.Xml.Xsl.XslTransform>  
- [<span data-ttu-id="74765-206">Transformace XSLT s třídou XslTransform</span><span class="sxs-lookup"><span data-stu-id="74765-206">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
- [<span data-ttu-id="74765-207">XPathNavigator v transformacích</span><span class="sxs-lookup"><span data-stu-id="74765-207">XPathNavigator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
- [<span data-ttu-id="74765-208">XPathNodeIterator v transformacích</span><span class="sxs-lookup"><span data-stu-id="74765-208">XPathNodeIterator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
- [<span data-ttu-id="74765-209">Vstup XPathDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="74765-209">XPathDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
- [<span data-ttu-id="74765-210">Vstup XmlDataDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="74765-210">XmlDataDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
- [<span data-ttu-id="74765-211">Vstup XmlDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="74765-211">XmlDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
