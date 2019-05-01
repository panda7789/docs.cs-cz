---
title: Uživatelem definované funkce a proměnné
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 4772f20e-1e7f-496e-93c2-1484473be555
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c2ce474dac44de1ac72811ecd3bc294ba57ce40a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61952019"
---
# <a name="user-defined-functions-and-variables"></a><span data-ttu-id="ccd3d-102">Uživatelem definované funkce a proměnné</span><span class="sxs-lookup"><span data-stu-id="ccd3d-102">User Defined Functions and Variables</span></span>
<span data-ttu-id="ccd3d-103"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje sadu metod, které se používají k interakci s <xref:System.Xml.XPath.XPathDocument> data.</span><span class="sxs-lookup"><span data-stu-id="ccd3d-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods that are used to interact with <xref:System.Xml.XPath.XPathDocument> data.</span></span> <span data-ttu-id="ccd3d-104">Standardní funkce XPath můžete doplnit prostřednictvím implementace rozšíření funkce a proměnné pro použití ve výrazech dotazů XPath.</span><span class="sxs-lookup"><span data-stu-id="ccd3d-104">You can supplement the standard XPath functions by implementing extension functions and variables for use by XPath query expressions.</span></span> <span data-ttu-id="ccd3d-105"><xref:System.Xml.XPath.XPathExpression.SetContext%2A> Metoda může přijímat kontext uživatelem definované odvozený od <xref:System.Xml.Xsl.XsltContext>.</span><span class="sxs-lookup"><span data-stu-id="ccd3d-105">The <xref:System.Xml.XPath.XPathExpression.SetContext%2A> method can accept a user defined context derived from <xref:System.Xml.Xsl.XsltContext>.</span></span> <span data-ttu-id="ccd3d-106">Uživatelem definované funkce jsou vyřešené prostřednictvím vlastní místní.</span><span class="sxs-lookup"><span data-stu-id="ccd3d-106">User defined functions are resolved by the custom context.</span></span>  
  
 <span data-ttu-id="ccd3d-107">Rozšíření funkcí a proměnných, může být užitečné při prevenci útoků prostřednictvím injektáže XML.</span><span class="sxs-lookup"><span data-stu-id="ccd3d-107">Extension functions and variables can be useful in prevention of XML injection attacks.</span></span> <span data-ttu-id="ccd3d-108">V těchto scénářích uživatelský vstup je přiřazená vlastní proměnné a zpracovat pomocí funkcí rozšíření, nikoli jako vstup nezpracovaných dat, které jsou spojeny s instrukce pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="ccd3d-108">In these scenarios user input is assigned to custom variables and processed by extension functions, not as raw input concatenated with processing instructions.</span></span> <span data-ttu-id="ccd3d-109">Rozšíření funkcí a proměnných obsahují uživatelský vstup, aby funguje jen na XML data tak, jak má návrhářem.</span><span class="sxs-lookup"><span data-stu-id="ccd3d-109">Extension functions and variables contain user input so that it only acts on XML data as intended by the designer.</span></span>  
  
 <span data-ttu-id="ccd3d-110">Použití rozšíření implementovat vlastní <xref:System.Xml.Xsl.XsltContext> třídy společně s rozhraní <xref:System.Xml.Xsl.IXsltContextFunction> a <xref:System.Xml.Xsl.IXsltContextVariable> , které podporují funkce rozšíření a proměnné.</span><span class="sxs-lookup"><span data-stu-id="ccd3d-110">To use extensions you implement a custom <xref:System.Xml.Xsl.XsltContext> class along with the interfaces <xref:System.Xml.Xsl.IXsltContextFunction> and <xref:System.Xml.Xsl.IXsltContextVariable> that support extension functions and variables.</span></span> <span data-ttu-id="ccd3d-111"><xref:System.Xml.XPath.XPathExpression> Přidá vstupu uživatele s jeho <xref:System.Xml.Xsl.XsltArgumentList> vlastního <xref:System.Xml.Xsl.XsltContext>.</span><span class="sxs-lookup"><span data-stu-id="ccd3d-111">An <xref:System.Xml.XPath.XPathExpression> adds user input with its <xref:System.Xml.Xsl.XsltArgumentList> to the custom <xref:System.Xml.Xsl.XsltContext>.</span></span>  
  
 <span data-ttu-id="ccd3d-112"><xref:System.Xml.XPath.XPathExpression> Představuje kompilované dotaz, který <xref:System.Xml.XPath.XPathNavigator> používá k vyhledání a zpracování uzly identifikovaný výraz.</span><span class="sxs-lookup"><span data-stu-id="ccd3d-112">The <xref:System.Xml.XPath.XPathExpression> represents a compiled query that <xref:System.Xml.XPath.XPathNavigator> uses to find and process the nodes identified by the expression.</span></span>  
  
 <span data-ttu-id="ccd3d-113">Následující příklad ukazuje implementaci vlastní místní třídy odvozené z <xref:System.Xml.Xsl.XsltContext>.</span><span class="sxs-lookup"><span data-stu-id="ccd3d-113">The following example shows implementation of a custom context class derived from <xref:System.Xml.Xsl.XsltContext>.</span></span> <span data-ttu-id="ccd3d-114">Komentáře v kódu popisují členy třídy a jejich použití v vlastní funkce.</span><span class="sxs-lookup"><span data-stu-id="ccd3d-114">Comments in the code describe class members and their use in custom functions.</span></span> <span data-ttu-id="ccd3d-115">Implementace funkce a proměnné a ukázkové aplikace, která používá tyto implementace postupujte podle tohoto segmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="ccd3d-115">Function and variable implementations and a sample application that uses these implementations follow this code segment.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#2](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#2)]
 [!code-vb[XPathExtensionFunctions#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#2)]  
  
 <span data-ttu-id="ccd3d-116">Následující kód implementuje <xref:System.Xml.Xsl.IXsltContextFunction>.</span><span class="sxs-lookup"><span data-stu-id="ccd3d-116">The following code implements <xref:System.Xml.Xsl.IXsltContextFunction>.</span></span> <span data-ttu-id="ccd3d-117">Třída, která implementuje <xref:System.Xml.Xsl.IXsltContextFunction> rozpozná a spustí uživatelem definované funkce.</span><span class="sxs-lookup"><span data-stu-id="ccd3d-117">The class that implements <xref:System.Xml.Xsl.IXsltContextFunction> resolves and executes user-defined functions.</span></span> <span data-ttu-id="ccd3d-118">Tento příklad používá funkci identifikovaný deklarace: `private int CountChar(string title, char charTocount)`.</span><span class="sxs-lookup"><span data-stu-id="ccd3d-118">This example uses the function identified by the declaration: `private int CountChar(string title, char charTocount)`.</span></span>  
  
 <span data-ttu-id="ccd3d-119">Komentáře kódu popisují členy třídy.</span><span class="sxs-lookup"><span data-stu-id="ccd3d-119">Code comments describe class members.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#3](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#3)]
 [!code-vb[XPathExtensionFunctions#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#3)]  
  
 <span data-ttu-id="ccd3d-120">Následující kód implementuje <xref:System.Xml.Xsl.IXsltContextVariable>.</span><span class="sxs-lookup"><span data-stu-id="ccd3d-120">The following code implements <xref:System.Xml.Xsl.IXsltContextVariable>.</span></span> <span data-ttu-id="ccd3d-121">Tato třída překládá odkazy na uživatelské proměnné ve výrazech dotazů XPath v době běhu.</span><span class="sxs-lookup"><span data-stu-id="ccd3d-121">This class resolves references to user-defined variables in XPath query expressions at run time.</span></span> <span data-ttu-id="ccd3d-122">Instance této třídy se vytvoří a vrátí přepsané <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> metoda vlastní <xref:System.Xml.Xsl.XsltContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="ccd3d-122">An instance of this class is created and returned by the overridden <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> method of the custom <xref:System.Xml.Xsl.XsltContext> class.</span></span>  
  
 <span data-ttu-id="ccd3d-123">Komentáře kódu popisují členy třídy.</span><span class="sxs-lookup"><span data-stu-id="ccd3d-123">Code comments describe the class members.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#4](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#4)]
 [!code-vb[XPathExtensionFunctions#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#4)]  
  
 <span data-ttu-id="ccd3d-124">S předchozí definice tříd v oboru, následující kód používá vlastní funkce k počítání znaků v elementech `Tasks.xml` dokumentu.</span><span class="sxs-lookup"><span data-stu-id="ccd3d-124">With the previous class definitions in scope, the following code uses the custom function to count characters in the elements of the `Tasks.xml` document.</span></span> <span data-ttu-id="ccd3d-125">Komentáře v kódu popisují kód, který zkompiluje vlastní funkce a spustí ho proti `Tasks.xml` dokumentu.</span><span class="sxs-lookup"><span data-stu-id="ccd3d-125">Comments in the code describe the code that compiles the custom function and runs it against the `Tasks.xml` document.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#1](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#1)]
 [!code-vb[XPathExtensionFunctions#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#1)]  
  
 <span data-ttu-id="ccd3d-126">Tento příklad používá následující data XML.</span><span class="sxs-lookup"><span data-stu-id="ccd3d-126">This example uses the following XML data.</span></span>  
  
 [!code-xml[XPathExtensionFunctions#5](../../../../samples/snippets/xml/VS_Snippets_Data/xpathextensionfunctions/XML/tasks.xml#5)]
