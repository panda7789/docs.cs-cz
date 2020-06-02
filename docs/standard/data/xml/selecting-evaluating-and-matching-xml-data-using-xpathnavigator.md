---
title: Výběr, vyhodnocení a spárování dat XML pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 46e059f8-4dc8-4185-9236-784be95228ed
ms.openlocfilehash: 1418e768db2f5f860ec40cf4e1351b4ec4a14a08
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282204"
---
# <a name="selecting-evaluating-and-matching-xml-data-using-xpathnavigator"></a><span data-ttu-id="b9d74-102">Výběr, vyhodnocení a spárování dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="b9d74-102">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>
<span data-ttu-id="b9d74-103"><xref:System.Xml.XPath.XPathNavigator>Třída poskytuje metody pro výběr uzlů v <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> objektu nebo pomocí dotazu XPath, vyhodnocení a přezkoumání výsledků výrazu XPath a určení, zda uzel v <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> objektu nebo odpovídá danému výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="b9d74-103">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to select nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath query, evaluate and examine the results of an XPath expression, and determine if a node in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object matches a given XPath expression.</span></span> <span data-ttu-id="b9d74-104">Tyto a další pojmy, které se vztahují k výběru, vyhodnocení a shodě uzlů <xref:System.Xml.XPath.XPathDocument> v <xref:System.Xml.XmlDocument> objektu nebo, jsou popsány v následujících tématech.</span><span class="sxs-lookup"><span data-stu-id="b9d74-104">These and other concepts that relate to selecting, evaluating and matching nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object are described in the following topics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b9d74-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b9d74-105">In This Section</span></span>  
 [<span data-ttu-id="b9d74-106">Výběr dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="b9d74-106">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="b9d74-107">Popisuje sadu <xref:System.Xml.XPath.XPathNavigator> metod třídy, které slouží k výběru sady uzlů v <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> objektu nebo pomocí výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="b9d74-107">Describes the set of <xref:System.Xml.XPath.XPathNavigator> class methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span>  
  
 [<span data-ttu-id="b9d74-108">Vyhodnocení výrazů XPath pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="b9d74-108">Evaluate XPath Expressions using XPathNavigator</span></span>](evaluate-xpath-expressions-using-xpathnavigator.md)  
 <span data-ttu-id="b9d74-109">Popisuje <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metodu <xref:System.Xml.XPath.XPathNavigator> třídy použitou k vyhodnocení výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="b9d74-109">Describes the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to evaluate an XPath expression.</span></span>  
  
 [<span data-ttu-id="b9d74-110">Párování uzlů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="b9d74-110">Matching Nodes using XPathNavigator</span></span>](matching-nodes-using-xpathnavigator.md)  
 <span data-ttu-id="b9d74-111">Popisuje <xref:System.Xml.XPath.XPathNavigator.Matches%2A> metodu <xref:System.Xml.XPath.XPathNavigator> třídy sloužící k určení, zda uzel odpovídá výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="b9d74-111">Describes the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to determine if a node matches an XPath expression.</span></span>  
  
 [<span data-ttu-id="b9d74-112">Rozpoznané typy uzlů s dotazy XPath</span><span class="sxs-lookup"><span data-stu-id="b9d74-112">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)  
 <span data-ttu-id="b9d74-113">Popisuje typy uzlů rozpoznané v dotazu XPath.</span><span class="sxs-lookup"><span data-stu-id="b9d74-113">Describes the types of nodes recognized in an XPath query.</span></span>  
  
 [<span data-ttu-id="b9d74-114">Dotazy a obory názvů XPath</span><span class="sxs-lookup"><span data-stu-id="b9d74-114">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)  
 <span data-ttu-id="b9d74-115">Popisuje použití oborů názvů v dotazu XPath.</span><span class="sxs-lookup"><span data-stu-id="b9d74-115">Describes the use of namespaces in an XPath query.</span></span>  
  
 [<span data-ttu-id="b9d74-116">Zkompilované výrazy XPath</span><span class="sxs-lookup"><span data-stu-id="b9d74-116">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)  
 <span data-ttu-id="b9d74-117">Popisuje <xref:System.Xml.XPath.XPathExpression> třídu, která představuje kompilovaný dotaz XPath.</span><span class="sxs-lookup"><span data-stu-id="b9d74-117">Describes the <xref:System.Xml.XPath.XPathExpression> class that represents a compiled XPath query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9d74-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9d74-118">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="b9d74-119">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="b9d74-119">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="b9d74-120">Načítání dat XML pomocí XPathDocument a XmlDocument</span><span class="sxs-lookup"><span data-stu-id="b9d74-120">Reading XML Data using XPathDocument and XmlDocument</span></span>](reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [<span data-ttu-id="b9d74-121">Přístup k datům XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="b9d74-121">Accessing XML Data using XPathNavigator</span></span>](accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="b9d74-122">Úpravy dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="b9d74-122">Editing XML Data using XPathNavigator</span></span>](editing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="b9d74-123">Ověření schématu pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="b9d74-123">Schema Validation using XPathNavigator</span></span>](schema-validation-using-xpathnavigator.md)
