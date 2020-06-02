---
title: Párování uzlů pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
ms.openlocfilehash: 47b0ba7e705ad602825dcca3f24c207362174a4c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289119"
---
# <a name="matching-nodes-using-xpathnavigator"></a><span data-ttu-id="eb0b0-102">Párování uzlů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="eb0b0-102">Matching Nodes using XPathNavigator</span></span>
<span data-ttu-id="eb0b0-103"><xref:System.Xml.XPath.XPathNavigator>Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.Matches%2A> metodu pro určení, zda uzel odpovídá výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="eb0b0-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method to determine if a node matches an XPath expression.</span></span> <span data-ttu-id="eb0b0-104"><xref:System.Xml.XPath.XPathNavigator.Matches%2A>Metoda přijímá výraz XPath jako vstup a vrátí hodnotu <xref:System.Boolean> , která označuje, zda aktuální uzel odpovídá danému výrazu XPath nebo danému kompilovanému <xref:System.Xml.XPath.XPathExpression> objektu.</span><span class="sxs-lookup"><span data-stu-id="eb0b0-104">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method takes an XPath expression as input and returns a <xref:System.Boolean> that indicates if the current node matches the given XPath expression or the given compiled <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
## <a name="matching-nodes"></a><span data-ttu-id="eb0b0-105">Vyhovující uzly</span><span class="sxs-lookup"><span data-stu-id="eb0b0-105">Matching Nodes</span></span>  
 <span data-ttu-id="eb0b0-106"><xref:System.Xml.XPath.XPathNavigator.Matches%2A>Metoda vrátí, `true` Pokud aktuální uzel odpovídá zadanému výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="eb0b0-106">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method returns `true` if the current node matches the XPath expression specified.</span></span> <span data-ttu-id="eb0b0-107">Například v následujícím příkladu kódu <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Metoda vrátí, `true` Pokud je aktuální uzel element `b` a element `b` má atribut `c` .</span><span class="sxs-lookup"><span data-stu-id="eb0b0-107">For example, in the code example that follows, the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method will return `true` if the current node is the element `b`, and element `b` has an attribute `c`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eb0b0-108"><xref:System.Xml.XPath.XPathNavigator.Matches%2A>Metoda nemění stav <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="eb0b0-108">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method does not change the state of the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eb0b0-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb0b0-109">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="eb0b0-110">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="eb0b0-110">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="eb0b0-111">Výběr dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="eb0b0-111">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="eb0b0-112">Vyhodnocení výrazů XPath pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="eb0b0-112">Evaluate XPath Expressions using XPathNavigator</span></span>](evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="eb0b0-113">Rozpoznané typy uzlů s dotazy XPath</span><span class="sxs-lookup"><span data-stu-id="eb0b0-113">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="eb0b0-114">Dotazy a obory názvů XPath</span><span class="sxs-lookup"><span data-stu-id="eb0b0-114">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)
- [<span data-ttu-id="eb0b0-115">Zkompilované výrazy XPath</span><span class="sxs-lookup"><span data-stu-id="eb0b0-115">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)
