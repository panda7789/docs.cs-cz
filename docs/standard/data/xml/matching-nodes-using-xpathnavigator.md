---
title: Párování uzlů pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 882e92c6c8cb6e638ca299ed4c43b9da8f4bf235
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923330"
---
# <a name="matching-nodes-using-xpathnavigator"></a><span data-ttu-id="732ac-102">Párování uzlů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="732ac-102">Matching Nodes using XPathNavigator</span></span>
<span data-ttu-id="732ac-103"><xref:System.Xml.XPath.XPathNavigator> Třída<xref:System.Xml.XPath.XPathNavigator.Matches%2A> poskytuje metodu pro určení, zda uzel odpovídá výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="732ac-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method to determine if a node matches an XPath expression.</span></span> <span data-ttu-id="732ac-104">Metoda přijímá výraz XPath jako vstup a <xref:System.Boolean> vrátí hodnotu, která označuje, zda aktuální uzel odpovídá danému výrazu XPath nebo danému kompilovanému <xref:System.Xml.XPath.XPathExpression> objektu. <xref:System.Xml.XPath.XPathNavigator.Matches%2A></span><span class="sxs-lookup"><span data-stu-id="732ac-104">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method takes an XPath expression as input and returns a <xref:System.Boolean> that indicates if the current node matches the given XPath expression or the given compiled <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
## <a name="matching-nodes"></a><span data-ttu-id="732ac-105">Vyhovující uzly</span><span class="sxs-lookup"><span data-stu-id="732ac-105">Matching Nodes</span></span>  
 <span data-ttu-id="732ac-106"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> Metoda vrátí`true` , pokud aktuální uzel odpovídá zadanému výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="732ac-106">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method returns `true` if the current node matches the XPath expression specified.</span></span> <span data-ttu-id="732ac-107">Například <xref:System.Xml.XPath.XPathNavigator.Matches%2A> v následujícím příkladu kódu metoda vrátí `b` `true` , pokud je aktuální uzel element a element `b` má atribut `c`.</span><span class="sxs-lookup"><span data-stu-id="732ac-107">For example, in the code example that follows, the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method will return `true` if the current node is the element `b`, and element `b` has an attribute `c`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="732ac-108">Metoda nemění stav <xref:System.Xml.XPath.XPathNavigator>. <xref:System.Xml.XPath.XPathNavigator.Matches%2A></span><span class="sxs-lookup"><span data-stu-id="732ac-108">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method does not change the state of the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
```vb  
Dim document as XPathDocument = New XPathDocument("input.xml")  
Dim navigator as XPathNavigator = document.CreateNavigator()  
  
navigator.Matches("b[@c]")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("input.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.Matches("b[@c]");  
```  
  
## <a name="see-also"></a><span data-ttu-id="732ac-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="732ac-109">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="732ac-110">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="732ac-110">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="732ac-111">Výběr dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="732ac-111">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="732ac-112">Vyhodnocení výrazů XPath pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="732ac-112">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="732ac-113">Rozpoznané typy uzlů s dotazy XPath</span><span class="sxs-lookup"><span data-stu-id="732ac-113">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="732ac-114">Dotazy XPath a obory názvů</span><span class="sxs-lookup"><span data-stu-id="732ac-114">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [<span data-ttu-id="732ac-115">Zkompilované výrazy XPath</span><span class="sxs-lookup"><span data-stu-id="732ac-115">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
