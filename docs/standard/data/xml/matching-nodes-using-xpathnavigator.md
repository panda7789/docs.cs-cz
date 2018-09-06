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
ms.openlocfilehash: 10aff89679d5c8099d5128540521879f10e3e294
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44041194"
---
# <a name="matching-nodes-using-xpathnavigator"></a><span data-ttu-id="d494e-102">Párování uzlů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="d494e-102">Matching Nodes using XPathNavigator</span></span>
<span data-ttu-id="d494e-103"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.Matches%2A> metodou ke zjištění, pokud uzel odpovídá výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="d494e-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method to determine if a node matches an XPath expression.</span></span> <span data-ttu-id="d494e-104"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> Metoda výraz XPath jako vstup převezme a vrátí <xref:System.Boolean> , která indikuje, jestli aktuální uzel odpovídá dané výraz XPath nebo zadaný kompilované <xref:System.Xml.XPath.XPathExpression> objektu.</span><span class="sxs-lookup"><span data-stu-id="d494e-104">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method takes an XPath expression as input and returns a <xref:System.Boolean> that indicates if the current node matches the given XPath expression or the given compiled <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
## <a name="matching-nodes"></a><span data-ttu-id="d494e-105">Odpovídající uzly</span><span class="sxs-lookup"><span data-stu-id="d494e-105">Matching Nodes</span></span>  
 <span data-ttu-id="d494e-106"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> Vrátí metoda `true` Pokud výraz XPath určeného odpovídá aktuální uzel.</span><span class="sxs-lookup"><span data-stu-id="d494e-106">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method returns `true` if the current node matches the XPath expression specified.</span></span> <span data-ttu-id="d494e-107">Například v následujícím příkladu kódu <xref:System.Xml.XPath.XPathNavigator.Matches%2A> vrátí metoda `true` Pokud je aktuální uzel elementu `b`a element `b` má atribut `c`.</span><span class="sxs-lookup"><span data-stu-id="d494e-107">For example, in the code example that follows, the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method will return `true` if the current node is the element `b`, and element `b` has an attribute `c`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d494e-108"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> Metoda nezmění stav <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="d494e-108">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method does not change the state of the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d494e-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d494e-109">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [<span data-ttu-id="d494e-110">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="d494e-110">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [<span data-ttu-id="d494e-111">Výběr dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="d494e-111">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="d494e-112">Vyhodnocení výrazů XPath pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="d494e-112">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
- [<span data-ttu-id="d494e-113">Rozpoznané typy uzlů s dotazy XPath</span><span class="sxs-lookup"><span data-stu-id="d494e-113">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
- [<span data-ttu-id="d494e-114">Dotazy XPath a obory názvů</span><span class="sxs-lookup"><span data-stu-id="d494e-114">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
- [<span data-ttu-id="d494e-115">Zkompilované výrazy XPath</span><span class="sxs-lookup"><span data-stu-id="d494e-115">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
