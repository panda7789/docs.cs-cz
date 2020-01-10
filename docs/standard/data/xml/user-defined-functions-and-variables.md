---
title: Uživatelem definované funkce a proměnné
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 4772f20e-1e7f-496e-93c2-1484473be555
ms.openlocfilehash: 7040c2ccf6e3bfc6efcbec3505c633c6c3c6508f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710060"
---
# <a name="user-defined-functions-and-variables"></a><span data-ttu-id="ade51-102">Uživatelem definované funkce a proměnné</span><span class="sxs-lookup"><span data-stu-id="ade51-102">User Defined Functions and Variables</span></span>
<span data-ttu-id="ade51-103">Třída <xref:System.Xml.XPath.XPathNavigator> poskytuje sadu metod, které slouží k interakci s daty <xref:System.Xml.XPath.XPathDocument>.</span><span class="sxs-lookup"><span data-stu-id="ade51-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods that are used to interact with <xref:System.Xml.XPath.XPathDocument> data.</span></span> <span data-ttu-id="ade51-104">Standardní funkce XPath můžete doplnit implementací funkcí rozšíření a proměnných pro použití ve výrazech dotazů XPath.</span><span class="sxs-lookup"><span data-stu-id="ade51-104">You can supplement the standard XPath functions by implementing extension functions and variables for use by XPath query expressions.</span></span> <span data-ttu-id="ade51-105">Metoda <xref:System.Xml.XPath.XPathExpression.SetContext%2A> může přijmout uživatelsky definovaný kontext odvozený od <xref:System.Xml.Xsl.XsltContext>.</span><span class="sxs-lookup"><span data-stu-id="ade51-105">The <xref:System.Xml.XPath.XPathExpression.SetContext%2A> method can accept a user defined context derived from <xref:System.Xml.Xsl.XsltContext>.</span></span> <span data-ttu-id="ade51-106">Uživatelsky definované funkce jsou vyřešeny vlastním kontextem.</span><span class="sxs-lookup"><span data-stu-id="ade51-106">User defined functions are resolved by the custom context.</span></span>  
  
 <span data-ttu-id="ade51-107">Funkce a proměnné rozšíření mohou být užitečné při prevenci útoků injektáže XML.</span><span class="sxs-lookup"><span data-stu-id="ade51-107">Extension functions and variables can be useful in prevention of XML injection attacks.</span></span> <span data-ttu-id="ade51-108">V těchto scénářích je uživatelský vstup přiřazen k vlastním proměnným a zpracován funkcí rozšíření, nikoli jako nezpracovaný vstup zřetězený s pokyny pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="ade51-108">In these scenarios user input is assigned to custom variables and processed by extension functions, not as raw input concatenated with processing instructions.</span></span> <span data-ttu-id="ade51-109">Funkce rozšíření a proměnné obsahují uživatelský vstup, takže fungují pouze na datech XML, která jsou určena návrhářem.</span><span class="sxs-lookup"><span data-stu-id="ade51-109">Extension functions and variables contain user input so that it only acts on XML data as intended by the designer.</span></span>  
  
 <span data-ttu-id="ade51-110">Chcete-li použít rozšíření, implementujte vlastní třídu <xref:System.Xml.Xsl.XsltContext> spolu s rozhraními <xref:System.Xml.Xsl.IXsltContextFunction> a <xref:System.Xml.Xsl.IXsltContextVariable>, které podporují funkce a proměnné rozšíření.</span><span class="sxs-lookup"><span data-stu-id="ade51-110">To use extensions you implement a custom <xref:System.Xml.Xsl.XsltContext> class along with the interfaces <xref:System.Xml.Xsl.IXsltContextFunction> and <xref:System.Xml.Xsl.IXsltContextVariable> that support extension functions and variables.</span></span> <span data-ttu-id="ade51-111"><xref:System.Xml.XPath.XPathExpression> přidá vstup uživatele s jeho <xref:System.Xml.Xsl.XsltArgumentList> do vlastního <xref:System.Xml.Xsl.XsltContext>.</span><span class="sxs-lookup"><span data-stu-id="ade51-111">An <xref:System.Xml.XPath.XPathExpression> adds user input with its <xref:System.Xml.Xsl.XsltArgumentList> to the custom <xref:System.Xml.Xsl.XsltContext>.</span></span>  
  
 <span data-ttu-id="ade51-112"><xref:System.Xml.XPath.XPathExpression> představuje kompilovaný dotaz, který <xref:System.Xml.XPath.XPathNavigator> používá k vyhledání a zpracování uzlů identifikovaných výrazem.</span><span class="sxs-lookup"><span data-stu-id="ade51-112">The <xref:System.Xml.XPath.XPathExpression> represents a compiled query that <xref:System.Xml.XPath.XPathNavigator> uses to find and process the nodes identified by the expression.</span></span>  
  
 <span data-ttu-id="ade51-113">Následující příklad ukazuje implementaci třídy vlastního kontextu odvozenou z <xref:System.Xml.Xsl.XsltContext>.</span><span class="sxs-lookup"><span data-stu-id="ade51-113">The following example shows implementation of a custom context class derived from <xref:System.Xml.Xsl.XsltContext>.</span></span> <span data-ttu-id="ade51-114">Komentáře v kódu popisují členy třídy a jejich použití ve vlastních funkcích.</span><span class="sxs-lookup"><span data-stu-id="ade51-114">Comments in the code describe class members and their use in custom functions.</span></span> <span data-ttu-id="ade51-115">Implementace funkcí a proměnných a ukázková aplikace, která používá tyto implementace, se řídí tímto segmentem kódu.</span><span class="sxs-lookup"><span data-stu-id="ade51-115">Function and variable implementations and a sample application that uses these implementations follow this code segment.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#2](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#2)]
 [!code-vb[XPathExtensionFunctions#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#2)]  
  
 <span data-ttu-id="ade51-116">Následující kód implementuje <xref:System.Xml.Xsl.IXsltContextFunction>.</span><span class="sxs-lookup"><span data-stu-id="ade51-116">The following code implements <xref:System.Xml.Xsl.IXsltContextFunction>.</span></span> <span data-ttu-id="ade51-117">Třída, která implementuje <xref:System.Xml.Xsl.IXsltContextFunction> řeší a provádí uživatelsky definované funkce.</span><span class="sxs-lookup"><span data-stu-id="ade51-117">The class that implements <xref:System.Xml.Xsl.IXsltContextFunction> resolves and executes user-defined functions.</span></span> <span data-ttu-id="ade51-118">Tento příklad používá funkci identifikovanou deklarací: `private int CountChar(string title, char charTocount)`.</span><span class="sxs-lookup"><span data-stu-id="ade51-118">This example uses the function identified by the declaration: `private int CountChar(string title, char charTocount)`.</span></span>  
  
 <span data-ttu-id="ade51-119">Komentáře kódu popisují členy třídy.</span><span class="sxs-lookup"><span data-stu-id="ade51-119">Code comments describe class members.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#3](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#3)]
 [!code-vb[XPathExtensionFunctions#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#3)]  
  
 <span data-ttu-id="ade51-120">Následující kód implementuje <xref:System.Xml.Xsl.IXsltContextVariable>.</span><span class="sxs-lookup"><span data-stu-id="ade51-120">The following code implements <xref:System.Xml.Xsl.IXsltContextVariable>.</span></span> <span data-ttu-id="ade51-121">Tato třída překládá odkazy na uživatelsky definované proměnné ve výrazech dotazů XPath za běhu.</span><span class="sxs-lookup"><span data-stu-id="ade51-121">This class resolves references to user-defined variables in XPath query expressions at run time.</span></span> <span data-ttu-id="ade51-122">Instance této třídy je vytvořena a vrácena přepsanou metodou <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> třídy Custom <xref:System.Xml.Xsl.XsltContext>.</span><span class="sxs-lookup"><span data-stu-id="ade51-122">An instance of this class is created and returned by the overridden <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> method of the custom <xref:System.Xml.Xsl.XsltContext> class.</span></span>  
  
 <span data-ttu-id="ade51-123">Komentáře kódu popisují členy třídy.</span><span class="sxs-lookup"><span data-stu-id="ade51-123">Code comments describe the class members.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#4](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#4)]
 [!code-vb[XPathExtensionFunctions#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#4)]  
  
 <span data-ttu-id="ade51-124">S definicemi předchozí třídy v oboru používá následující kód vlastní funkci pro počítání znaků v prvcích `Tasks.xml` dokumentu.</span><span class="sxs-lookup"><span data-stu-id="ade51-124">With the previous class definitions in scope, the following code uses the custom function to count characters in the elements of the `Tasks.xml` document.</span></span> <span data-ttu-id="ade51-125">Komentáře v kódu popisují kód, který zkompiluje vlastní funkci a spustí jej v dokumentu `Tasks.xml`.</span><span class="sxs-lookup"><span data-stu-id="ade51-125">Comments in the code describe the code that compiles the custom function and runs it against the `Tasks.xml` document.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#1](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#1)]
 [!code-vb[XPathExtensionFunctions#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#1)]  
  
 <span data-ttu-id="ade51-126">Tento příklad používá následující data XML.</span><span class="sxs-lookup"><span data-stu-id="ade51-126">This example uses the following XML data.</span></span>  
  
 [!code-xml[XPathExtensionFunctions#5](../../../../samples/snippets/xml/VS_Snippets_Data/xpathextensionfunctions/XML/tasks.xml#5)]
