---
title: Přístup k datům XML pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: c57b46e6-5c77-408f-bc4e-67a5dcc9cc05
ms.openlocfilehash: 717937ebca9b5775619b0dde749f0566c73ca116
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290925"
---
# <a name="accessing-xml-data-using-xpathnavigator"></a><span data-ttu-id="57c94-102">Přístup k datům XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="57c94-102">Accessing XML Data using XPathNavigator</span></span>
<span data-ttu-id="57c94-103"><xref:System.Xml.XPath.XPathNavigator>Třída poskytuje metody pro navigaci v uzlech, extrakci dat XML a přístup k datům XML silného typu v <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> objektu or.</span><span class="sxs-lookup"><span data-stu-id="57c94-103">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to navigate nodes, extract XML data and access strongly typed XML data in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="57c94-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="57c94-104">In This Section</span></span>  
 [<span data-ttu-id="57c94-105">Navigace v sadě uzlů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="57c94-105">Node Set Navigation Using XPathNavigator</span></span>](node-set-navigation-using-xpathnavigator.md)  
 <span data-ttu-id="57c94-106">Popisuje, jak nastavit navigační metody <xref:System.Xml.XPath.XPathNavigator> třídy používané pro navigaci uzlů v <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> objektu nebo.</span><span class="sxs-lookup"><span data-stu-id="57c94-106">Describes the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class used to navigate nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="57c94-107">Navigace v uzlu oborů názvů a atributů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="57c94-107">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
 <span data-ttu-id="57c94-108">Popisuje metody a vlastnosti navigace v uzlu oboru názvů <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="57c94-108">Describes the attribute and namespace node navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 [<span data-ttu-id="57c94-109">Extrahování dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="57c94-109">Extract XML Data Using XPathNavigator</span></span>](extract-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="57c94-110">Popisuje různé metody extrakce dat XML z <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> objektu nebo.</span><span class="sxs-lookup"><span data-stu-id="57c94-110">Describes the various methods of extracting XML data from an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="57c94-111">Přístup k datům XML silného typu pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="57c94-111">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](accessing-strongly-typed-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="57c94-112">Popisuje přístup k datům XML se silným typem v <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> objektu nebo pomocí <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="57c94-112">Describes accessing strongly typed XML data in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 [<span data-ttu-id="57c94-113">Uživatelem definované funkce a proměnné</span><span class="sxs-lookup"><span data-stu-id="57c94-113">User Defined Functions and Variables</span></span>](user-defined-functions-and-variables.md)  
 <span data-ttu-id="57c94-114">Popisuje implementaci vlastní <xref:System.Xml.Xsl.XsltContext> třídy spolu s rozhraními <xref:System.Xml.Xsl.IXsltContextFunction> a podporující <xref:System.Xml.Xsl.IXsltContextVariable> funkce rozšíření a proměnné.</span><span class="sxs-lookup"><span data-stu-id="57c94-114">Describes implementing a custom <xref:System.Xml.Xsl.XsltContext> class along with the interfaces <xref:System.Xml.Xsl.IXsltContextFunction> and <xref:System.Xml.Xsl.IXsltContextVariable> that support extension functions and variables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57c94-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="57c94-115">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="57c94-116">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="57c94-116">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="57c94-117">Načítání dat XML pomocí XPathDocument a XmlDocument</span><span class="sxs-lookup"><span data-stu-id="57c94-117">Reading XML Data using XPathDocument and XmlDocument</span></span>](reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [<span data-ttu-id="57c94-118">Výběr, vyhodnocení a spárování dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="57c94-118">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="57c94-119">Úpravy dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="57c94-119">Editing XML Data using XPathNavigator</span></span>](editing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="57c94-120">Ověření schématu pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="57c94-120">Schema Validation using XPathNavigator</span></span>](schema-validation-using-xpathnavigator.md)
