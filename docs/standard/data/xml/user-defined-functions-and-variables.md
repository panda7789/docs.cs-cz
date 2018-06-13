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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570461"
---
# <a name="user-defined-functions-and-variables"></a><span data-ttu-id="11928-102">Uživatelem definované funkce a proměnné</span><span class="sxs-lookup"><span data-stu-id="11928-102">User Defined Functions and Variables</span></span>
<span data-ttu-id="11928-103"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje sadu metod, které se používají k interakci s <xref:System.Xml.XPath.XPathDocument> data.</span><span class="sxs-lookup"><span data-stu-id="11928-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods that are used to interact with <xref:System.Xml.XPath.XPathDocument> data.</span></span> <span data-ttu-id="11928-104">Standardní funkce jazyka XPath lze rozšířit implementací rozšíření funkce a proměnné pro použití ve výrazech dotazů XPath.</span><span class="sxs-lookup"><span data-stu-id="11928-104">You can supplement the standard XPath functions by implementing extension functions and variables for use by XPath query expressions.</span></span> <span data-ttu-id="11928-105"><xref:System.Xml.XPath.XPathExpression.SetContext%2A> Metoda může přijmout odvozené z kontextu uživatelsky definované <xref:System.Xml.Xsl.XsltContext>.</span><span class="sxs-lookup"><span data-stu-id="11928-105">The <xref:System.Xml.XPath.XPathExpression.SetContext%2A> method can accept a user defined context derived from <xref:System.Xml.Xsl.XsltContext>.</span></span> <span data-ttu-id="11928-106">Uživatelem definované funkce se vyřeší kontext vlastní.</span><span class="sxs-lookup"><span data-stu-id="11928-106">User defined functions are resolved by the custom context.</span></span>  
  
 <span data-ttu-id="11928-107">Rozšíření funkce a proměnné může být užitečné při prevenci útoků vkládání XML.</span><span class="sxs-lookup"><span data-stu-id="11928-107">Extension functions and variables can be useful in prevention of XML injection attacks.</span></span> <span data-ttu-id="11928-108">Uživatelský vstup je v těchto scénářích přiřazené vlastní proměnné a zpracovává rozšíření funkce, nikoli jako nezpracovaná vstup zřetězen s pokynů pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="11928-108">In these scenarios user input is assigned to custom variables and processed by extension functions, not as raw input concatenated with processing instructions.</span></span> <span data-ttu-id="11928-109">Rozšíření funkce a proměnné obsahovat uživatelský vstup, aby ho pouze funguje na XML data tak, jak má v designeru.</span><span class="sxs-lookup"><span data-stu-id="11928-109">Extension functions and variables contain user input so that it only acts on XML data as intended by the designer.</span></span>  
  
 <span data-ttu-id="11928-110">Pokud chcete rozšíření použít implementovat vlastní <xref:System.Xml.Xsl.XsltContext> třída společně s rozhraní <xref:System.Xml.Xsl.IXsltContextFunction> a <xref:System.Xml.Xsl.IXsltContextVariable> podporující rozšíření funkce a proměnné.</span><span class="sxs-lookup"><span data-stu-id="11928-110">To use extensions you implement a custom <xref:System.Xml.Xsl.XsltContext> class along with the interfaces <xref:System.Xml.Xsl.IXsltContextFunction> and <xref:System.Xml.Xsl.IXsltContextVariable> that support extension functions and variables.</span></span> <span data-ttu-id="11928-111"><xref:System.Xml.XPath.XPathExpression> Přidá vstup uživatele s jeho <xref:System.Xml.Xsl.XsltArgumentList> na vlastní <xref:System.Xml.Xsl.XsltContext>.</span><span class="sxs-lookup"><span data-stu-id="11928-111">An <xref:System.Xml.XPath.XPathExpression> adds user input with its <xref:System.Xml.Xsl.XsltArgumentList> to the custom <xref:System.Xml.Xsl.XsltContext>.</span></span>  
  
 <span data-ttu-id="11928-112"><xref:System.Xml.XPath.XPathExpression> Představuje kompilované dotaz, který <xref:System.Xml.XPath.XPathNavigator> používá k vyhledání a zpracovat uzly identifikovaný výraz.</span><span class="sxs-lookup"><span data-stu-id="11928-112">The <xref:System.Xml.XPath.XPathExpression> represents a compiled query that <xref:System.Xml.XPath.XPathNavigator> uses to find and process the nodes identified by the expression.</span></span>  
  
 <span data-ttu-id="11928-113">Následující příklad ukazuje implementaci vlastní kontextu třídy odvozené od <xref:System.Xml.Xsl.XsltContext>.</span><span class="sxs-lookup"><span data-stu-id="11928-113">The following example shows implementation of a custom context class derived from <xref:System.Xml.Xsl.XsltContext>.</span></span> <span data-ttu-id="11928-114">Komentáře v kódu popisují členy třídy a jejich využití v vlastní funkce.</span><span class="sxs-lookup"><span data-stu-id="11928-114">Comments in the code describe class members and their use in custom functions.</span></span> <span data-ttu-id="11928-115">Implementace funkce a proměnné a ukázkové aplikace, která používá tyto implementace postupujte podle tohoto segmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="11928-115">Function and variable implementations and a sample application that uses these implementations follow this code segment.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#2](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#2)]
 [!code-vb[XPathExtensionFunctions#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#2)]  
  
 <span data-ttu-id="11928-116">Následující kód implementuje <xref:System.Xml.Xsl.IXsltContextFunction>.</span><span class="sxs-lookup"><span data-stu-id="11928-116">The following code implements <xref:System.Xml.Xsl.IXsltContextFunction>.</span></span> <span data-ttu-id="11928-117">Třídu, která implementuje <xref:System.Xml.Xsl.IXsltContextFunction> vyřeší a provede uživatelsky definované funkce.</span><span class="sxs-lookup"><span data-stu-id="11928-117">The class that implements <xref:System.Xml.Xsl.IXsltContextFunction> resolves and executes user-defined functions.</span></span> <span data-ttu-id="11928-118">Tento příklad používá funkci identifikovaný deklaraci: `private int CountChar(string title, char charTocount)`.</span><span class="sxs-lookup"><span data-stu-id="11928-118">This example uses the function identified by the declaration: `private int CountChar(string title, char charTocount)`.</span></span>  
  
 <span data-ttu-id="11928-119">Komentáře kódu popisují členy třídy.</span><span class="sxs-lookup"><span data-stu-id="11928-119">Code comments describe class members.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#3](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#3)]
 [!code-vb[XPathExtensionFunctions#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#3)]  
  
 <span data-ttu-id="11928-120">Následující kód implementuje <xref:System.Xml.Xsl.IXsltContextVariable>.</span><span class="sxs-lookup"><span data-stu-id="11928-120">The following code implements <xref:System.Xml.Xsl.IXsltContextVariable>.</span></span> <span data-ttu-id="11928-121">Tato třída přeloží odkazy na uživatelem definované proměnné ve výrazech XPath dotazů za běhu.</span><span class="sxs-lookup"><span data-stu-id="11928-121">This class resolves references to user-defined variables in XPath query expressions at run time.</span></span> <span data-ttu-id="11928-122">Instance této třídy je vytvořen a vrácený přepsané <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> metoda vlastní <xref:System.Xml.Xsl.XsltContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="11928-122">An instance of this class is created and returned by the overridden <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> method of the custom <xref:System.Xml.Xsl.XsltContext> class.</span></span>  
  
 <span data-ttu-id="11928-123">Komentáře kódu popisují členy třídy.</span><span class="sxs-lookup"><span data-stu-id="11928-123">Code comments describe the class members.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#4](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#4)]
 [!code-vb[XPathExtensionFunctions#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#4)]  
  
 <span data-ttu-id="11928-124">Předchozí definicemi – třída v oboru, následující kód používá vlastní funkce pro počet znaků v elementech `Tasks.xml` dokumentu.</span><span class="sxs-lookup"><span data-stu-id="11928-124">With the previous class definitions in scope, the following code uses the custom function to count characters in the elements of the `Tasks.xml` document.</span></span> <span data-ttu-id="11928-125">Komentáře v kódu popisují kód, který sestavuje vlastní funkce a spouští se před `Tasks.xml` dokumentu.</span><span class="sxs-lookup"><span data-stu-id="11928-125">Comments in the code describe the code that compiles the custom function and runs it against the `Tasks.xml` document.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#1](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#1)]
 [!code-vb[XPathExtensionFunctions#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#1)]  
  
 <span data-ttu-id="11928-126">Tento příklad používá následující data XML.</span><span class="sxs-lookup"><span data-stu-id="11928-126">This example uses the following XML data.</span></span>  
  
 [!code-xml[XPathExtensionFunctions#5](../../../../samples/snippets/xml/VS_Snippets_Data/xpathextensionfunctions/XML/tasks.xml#5)]
