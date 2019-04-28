---
title: Porovnání jazyka XPath a technologie LINQ to XML
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: afd8701c6a37fd981d9fc23b57904da80eabf86e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61668390"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a><span data-ttu-id="9d811-102">Porovnání jazyka XPath a technologie LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="9d811-102">Comparison of XPath and LINQ to XML</span></span>
<span data-ttu-id="9d811-103">Výraz XPath a technologie LINQ to XML nabízejí některé podobné funkce.</span><span class="sxs-lookup"><span data-stu-id="9d811-103">XPath and LINQ to XML offer some similar functionality.</span></span> <span data-ttu-id="9d811-104">Jak lze použít k dotazování stromu XML, vrátí tyto výsledky jako kolekci elementů, kolekce atributů, kolekce uzlů nebo hodnotu elementu nebo atributu.</span><span class="sxs-lookup"><span data-stu-id="9d811-104">Both can be used to query an XML tree, returning such results as a collection of elements, a collection of attributes, a collection of nodes, or the value of an element or attribute.</span></span> <span data-ttu-id="9d811-105">Existují však také několik rozdílů.</span><span class="sxs-lookup"><span data-stu-id="9d811-105">However, there are also some differences.</span></span>  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a><span data-ttu-id="9d811-106">Rozdíly mezi XPath a technologie LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="9d811-106">Differences Between XPath and LINQ to XML</span></span>  
 <span data-ttu-id="9d811-107">Výraz XPath není povolena projekce nových typů.</span><span class="sxs-lookup"><span data-stu-id="9d811-107">XPath does not allow projection of new types.</span></span> <span data-ttu-id="9d811-108">To může vrátit pouze kolekce uzlů ze stromu, zatímco LINQ to XML můžete spustit dotaz a projekt grafu objektu nebo stromu XML v nový tvar.</span><span class="sxs-lookup"><span data-stu-id="9d811-108">It can only return collections of nodes from the tree, whereas LINQ to XML can execute a query and project an object graph or an XML tree in a new shape.</span></span> <span data-ttu-id="9d811-109">Technologie LINQ to XML dotazů zvětšíte mnohem víc funkcí a jsou výrazně výkonnější než výrazy XPath.</span><span class="sxs-lookup"><span data-stu-id="9d811-109">LINQ to XML queries encompass much more functionality and are much more powerful than XPath expressions.</span></span>  
  
 <span data-ttu-id="9d811-110">Výrazy XPath existovat samostatně v rámci řetězce.</span><span class="sxs-lookup"><span data-stu-id="9d811-110">XPath expressions exist in isolation within a string.</span></span> <span data-ttu-id="9d811-111">Kompilátor jazyka C# vám nemůže pomoci parsovat výraz XPath v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="9d811-111">The C# compiler cannot help parse the XPath expression at compile time.</span></span> <span data-ttu-id="9d811-112">Naopak LINQ to XML dotazy jsou analyzovány a zkompilovány kompilátorem jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="9d811-112">By contrast, LINQ to XML queries are parsed and compiled by the C# compiler.</span></span> <span data-ttu-id="9d811-113">Kompilátoru je moci zachytávat chyby mnoho dotazů.</span><span class="sxs-lookup"><span data-stu-id="9d811-113">The compiler is able to catch many query errors.</span></span>  
  
 <span data-ttu-id="9d811-114">Výraz XPath výsledky nejsou silného typu.</span><span class="sxs-lookup"><span data-stu-id="9d811-114">XPath results are not strongly typed.</span></span> <span data-ttu-id="9d811-115">V počtu situací je výsledkem vyhodnocení výrazu XPath objektu a je vývojářům určit správný typ a přetypujte výsledek podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="9d811-115">In a number of circumstances, the result of evaluating an XPath expression is an object, and it is up to the developer to determine the proper type and cast the result as necessary.</span></span> <span data-ttu-id="9d811-116">Naopak projekce v LINQ dotazu XML jsou silného typu.</span><span class="sxs-lookup"><span data-stu-id="9d811-116">By contrast, the projections from a LINQ to XML query are strongly typed.</span></span>  
  
## <a name="result-ordering"></a><span data-ttu-id="9d811-117">Výsledek řazení</span><span class="sxs-lookup"><span data-stu-id="9d811-117">Result Ordering</span></span>  
 <span data-ttu-id="9d811-118">Výraz XPath 1.0 doporučení uvádí, že kolekce, která je výsledkem vyhodnocení výrazu XPath Neseřazený.</span><span class="sxs-lookup"><span data-stu-id="9d811-118">The XPath 1.0 Recommendation states that a collection that is the result of evaluating an XPath expression is unordered.</span></span>  
  
 <span data-ttu-id="9d811-119">Ale když iterace v kolekci vrácené LINQ metody osy XML XPath, uzly v kolekci jsou vráceny v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="9d811-119">However, when iterating through a collection returned by a LINQ to XML XPath axis method, the nodes in the collection are returned in document order.</span></span> <span data-ttu-id="9d811-120">To platí i v případě, že přístup k osy XPath kde predikáty se vyjadřují v pořadí reverzní dokumentů, jako například `preceding` a `preceding-sibling`.</span><span class="sxs-lookup"><span data-stu-id="9d811-120">This is the case even when accessing the XPath axes where predicates are expressed in terms of reverse document order, such as `preceding` and `preceding-sibling`.</span></span>  
  
 <span data-ttu-id="9d811-121">Naopak většina technologie LINQ to XML osy vrací kolekce v pořadí dokumentů, ale dva z nich, <xref:System.Xml.Linq.XNode.Ancestors%2A> a <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, vrací kolekce v pořadí reverzní dokumentů.</span><span class="sxs-lookup"><span data-stu-id="9d811-121">By contrast, most of the LINQ to XML axes return collections in document order, but two of them, <xref:System.Xml.Linq.XNode.Ancestors%2A> and <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, return collections in reverse document order.</span></span> <span data-ttu-id="9d811-122">V následující tabulce vytvoří výčet OS a určuje pořadí kolekce pro jednotlivé:</span><span class="sxs-lookup"><span data-stu-id="9d811-122">The following table enumerates the axes, and indicates collection order for each:</span></span>  
  
|<span data-ttu-id="9d811-123">Technologie LINQ to XML – osa</span><span class="sxs-lookup"><span data-stu-id="9d811-123">LINQ to XML axis</span></span>|<span data-ttu-id="9d811-124">Řazení</span><span class="sxs-lookup"><span data-stu-id="9d811-124">Ordering</span></span>|  
|----------------------|--------------|  
|<span data-ttu-id="9d811-125">XContainer.DescendantNodes</span><span class="sxs-lookup"><span data-stu-id="9d811-125">XContainer.DescendantNodes</span></span>|<span data-ttu-id="9d811-126">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="9d811-126">Document order</span></span>|  
|<span data-ttu-id="9d811-127">XContainer.Descendants</span><span class="sxs-lookup"><span data-stu-id="9d811-127">XContainer.Descendants</span></span>|<span data-ttu-id="9d811-128">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="9d811-128">Document order</span></span>|  
|<span data-ttu-id="9d811-129">XContainer.Elements</span><span class="sxs-lookup"><span data-stu-id="9d811-129">XContainer.Elements</span></span>|<span data-ttu-id="9d811-130">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="9d811-130">Document order</span></span>|  
|<span data-ttu-id="9d811-131">XContainer.Nodes</span><span class="sxs-lookup"><span data-stu-id="9d811-131">XContainer.Nodes</span></span>|<span data-ttu-id="9d811-132">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="9d811-132">Document order</span></span>|  
|<span data-ttu-id="9d811-133">XContainer.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="9d811-133">XContainer.NodesAfterSelf</span></span>|<span data-ttu-id="9d811-134">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="9d811-134">Document order</span></span>|  
|<span data-ttu-id="9d811-135">XContainer.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="9d811-135">XContainer.NodesBeforeSelf</span></span>|<span data-ttu-id="9d811-136">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="9d811-136">Document order</span></span>|  
|<span data-ttu-id="9d811-137">XElement.AncestorsAndSelf</span><span class="sxs-lookup"><span data-stu-id="9d811-137">XElement.AncestorsAndSelf</span></span>|<span data-ttu-id="9d811-138">Pořadí reverzní dokumentů</span><span class="sxs-lookup"><span data-stu-id="9d811-138">Reverse document order</span></span>|  
|<span data-ttu-id="9d811-139">XElement.Attributes</span><span class="sxs-lookup"><span data-stu-id="9d811-139">XElement.Attributes</span></span>|<span data-ttu-id="9d811-140">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="9d811-140">Document order</span></span>|  
|<span data-ttu-id="9d811-141">XElement.DescendantNodesAndSelf</span><span class="sxs-lookup"><span data-stu-id="9d811-141">XElement.DescendantNodesAndSelf</span></span>|<span data-ttu-id="9d811-142">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="9d811-142">Document order</span></span>|  
|<span data-ttu-id="9d811-143">XElement.DescendantsAndSelf</span><span class="sxs-lookup"><span data-stu-id="9d811-143">XElement.DescendantsAndSelf</span></span>|<span data-ttu-id="9d811-144">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="9d811-144">Document order</span></span>|  
|<span data-ttu-id="9d811-145">XNode.Ancestors</span><span class="sxs-lookup"><span data-stu-id="9d811-145">XNode.Ancestors</span></span>|<span data-ttu-id="9d811-146">Pořadí reverzní dokumentů</span><span class="sxs-lookup"><span data-stu-id="9d811-146">Reverse document order</span></span>|  
|<span data-ttu-id="9d811-147">XNode.ElementsAfterSelf</span><span class="sxs-lookup"><span data-stu-id="9d811-147">XNode.ElementsAfterSelf</span></span>|<span data-ttu-id="9d811-148">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="9d811-148">Document order</span></span>|  
|<span data-ttu-id="9d811-149">XNode.ElementsBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="9d811-149">XNode.ElementsBeforeSelf</span></span>|<span data-ttu-id="9d811-150">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="9d811-150">Document order</span></span>|  
|<span data-ttu-id="9d811-151">XNode.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="9d811-151">XNode.NodesAfterSelf</span></span>|<span data-ttu-id="9d811-152">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="9d811-152">Document order</span></span>|  
|<span data-ttu-id="9d811-153">XNode.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="9d811-153">XNode.NodesBeforeSelf</span></span>|<span data-ttu-id="9d811-154">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="9d811-154">Document order</span></span>|  
  
## <a name="positional-predicates"></a><span data-ttu-id="9d811-155">Poziční predikáty.</span><span class="sxs-lookup"><span data-stu-id="9d811-155">Positional Predicates</span></span>  
 <span data-ttu-id="9d811-156">Ve výrazu XPath poziční predikáty se vyjadřují v pořadí dokumentů pro mnoho osy, ale jsou vyjádřeny v pořadí reverzní dokumentů pro reverzní osy, které jsou `preceding`, `preceding-sibling`, `ancestor`, a `ancestor-or-self`.</span><span class="sxs-lookup"><span data-stu-id="9d811-156">Within an XPath expression, positional predicates are expressed in terms of document order for many axes, but are expressed in reverse document order for reverse axes, which are `preceding`, `preceding-sibling`, `ancestor`, and `ancestor-or-self`.</span></span> <span data-ttu-id="9d811-157">Například výraz XPath `preceding-sibling::*[1]` vrátí bezprostředně předcházející na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="9d811-157">For example, the XPath expression `preceding-sibling::*[1]` returns the immediately preceding sibling.</span></span> <span data-ttu-id="9d811-158">To platí i v případě, že sada konečný výsledek se zobrazí v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="9d811-158">This is the case even though the final result set is presented in document order.</span></span>  
  
 <span data-ttu-id="9d811-159">Naopak všechny predikáty poziční v technologii LINQ to XML se vždy vyjadřují v pořadí osy.</span><span class="sxs-lookup"><span data-stu-id="9d811-159">By contrast, all positional predicates in LINQ to XML are always expressed in terms of the order of the axis.</span></span> <span data-ttu-id="9d811-160">Například `anElement.ElementsBeforeSelf().ElementAt(0)` vrátí první podřízený element nadřazeného elementu poslal dotaz, ne okamžité předcházející na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="9d811-160">For example, `anElement.ElementsBeforeSelf().ElementAt(0)` returns the first child element of the parent of the queried element, not the immediate preceding sibling.</span></span> <span data-ttu-id="9d811-161">Další příklad: `anElement.Ancestors().ElementAt(0)` vrátí nadřazeného elementu.</span><span class="sxs-lookup"><span data-stu-id="9d811-161">Another example: `anElement.Ancestors().ElementAt(0)` returns the parent element.</span></span>  
  
 <span data-ttu-id="9d811-162">Pokud byste chtěli najít bezprostředně předcházející prvek v technologii LINQ to XML, měli byste napsat následující výraz:</span><span class="sxs-lookup"><span data-stu-id="9d811-162">If you wanted to find the immediately preceding element in LINQ to XML, you would write the following expression:</span></span>  
  
```csharp
ElementsBeforeSelf().Last()
```
  
```vb
ElementsBeforeSelf().Last()
```
  
## <a name="performance-differences"></a><span data-ttu-id="9d811-163">Rozdíly ve výkonu</span><span class="sxs-lookup"><span data-stu-id="9d811-163">Performance Differences</span></span>  
 <span data-ttu-id="9d811-164">Dotazy XPath, které používají funkce XPath v technologii LINQ to XML nebude provádět, tak LINQ dotazy XML.</span><span class="sxs-lookup"><span data-stu-id="9d811-164">XPath queries that use the XPath functionality in LINQ to XML will not perform as well as LINQ to XML queries.</span></span>  
  
## <a name="comparison-of-composition"></a><span data-ttu-id="9d811-165">Porovnání složení</span><span class="sxs-lookup"><span data-stu-id="9d811-165">Comparison of Composition</span></span>  
 <span data-ttu-id="9d811-166">Složení LINQ to XML dotazu je poněkud paralelní složení výraz XPath, ale velmi odlišné v syntaxi.</span><span class="sxs-lookup"><span data-stu-id="9d811-166">Composition of a LINQ to XML query is somewhat parallel to composition of an XPath expression, although very different in syntax.</span></span>  
  
 <span data-ttu-id="9d811-167">Například, pokud máte v proměnné s názvem elementu `customers`, a vy chcete najít podřízený element s názvem `CompanyName` v rámci všech podřízených elementů s názvem `Customer`, měli byste napsat výraz XPath následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9d811-167">For example, if you have an element in a variable named `customers`, and you want to find a grandchild element named `CompanyName` under all child elements named `Customer`, you would write an XPath expression as follows:</span></span>  
  
```csharp  
customers.XPathSelectElements("./Customer/CompanyName")
```  
  
```vb
customers.XPathSelectElements("./Customer/CompanyName")
```

 <span data-ttu-id="9d811-168">Je ekvivalentní LINQ to XML dotazu:</span><span class="sxs-lookup"><span data-stu-id="9d811-168">The equivalent LINQ to XML query is:</span></span>  
  
```csharp  
customers.Elements("Customer").Elements("CompanyName")
```  
  
```vb
customers.Elements("Customer").Elements("CompanyName")
```  

 <span data-ttu-id="9d811-169">Jsou podobné parallels pro každý OS XPath.</span><span class="sxs-lookup"><span data-stu-id="9d811-169">There are similar parallels for each of the XPath axes.</span></span>  
  
|<span data-ttu-id="9d811-170">Výraz XPath osy</span><span class="sxs-lookup"><span data-stu-id="9d811-170">XPath axis</span></span>|<span data-ttu-id="9d811-171">Technologie LINQ to XML – osa</span><span class="sxs-lookup"><span data-stu-id="9d811-171">LINQ to XML axis</span></span>|  
|----------------|----------------------|  
|<span data-ttu-id="9d811-172">podřízený (na ose výchozí)</span><span class="sxs-lookup"><span data-stu-id="9d811-172">child (the default axis)</span></span>|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9d811-173">Nadřazené (.)</span><span class="sxs-lookup"><span data-stu-id="9d811-173">Parent (..)</span></span>|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9d811-174">atribut osy (@)</span><span class="sxs-lookup"><span data-stu-id="9d811-174">attribute axis (@)</span></span>|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="9d811-175">or</span><span class="sxs-lookup"><span data-stu-id="9d811-175">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9d811-176">předchůdce osy</span><span class="sxs-lookup"><span data-stu-id="9d811-176">ancestor axis</span></span>|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9d811-177">předchůdce nebo self OS</span><span class="sxs-lookup"><span data-stu-id="9d811-177">ancestor-or-self axis</span></span>|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9d811-178">Následnické osy (/ /)</span><span class="sxs-lookup"><span data-stu-id="9d811-178">descendant axis (//)</span></span>|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="9d811-179">or</span><span class="sxs-lookup"><span data-stu-id="9d811-179">or</span></span><br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9d811-180">descendant-or-self</span><span class="sxs-lookup"><span data-stu-id="9d811-180">descendant-or-self</span></span>|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="9d811-181">or</span><span class="sxs-lookup"><span data-stu-id="9d811-181">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9d811-182">Následující na stejné úrovni</span><span class="sxs-lookup"><span data-stu-id="9d811-182">following-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="9d811-183">or</span><span class="sxs-lookup"><span data-stu-id="9d811-183">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9d811-184">preceding-sibling</span><span class="sxs-lookup"><span data-stu-id="9d811-184">preceding-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="9d811-185">or</span><span class="sxs-lookup"><span data-stu-id="9d811-185">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9d811-186">Následující</span><span class="sxs-lookup"><span data-stu-id="9d811-186">following</span></span>|<span data-ttu-id="9d811-187">Žádný přímý ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="9d811-187">No direct equivalent.</span></span>|  
|<span data-ttu-id="9d811-188">předchozí</span><span class="sxs-lookup"><span data-stu-id="9d811-188">preceding</span></span>|<span data-ttu-id="9d811-189">Žádný přímý ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="9d811-189">No direct equivalent.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9d811-190">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d811-190">See also</span></span>

- [<span data-ttu-id="9d811-191">LINQ to XML pro uživatele jazyka XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="9d811-191">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
