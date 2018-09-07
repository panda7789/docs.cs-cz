---
title: Porovnání jazyka XPath a technologie LINQ to XML
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: e27fbe2c45e331a90261da3c0c575f1a472db88f
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44087375"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a><span data-ttu-id="a223e-102">Porovnání jazyka XPath a technologie LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="a223e-102">Comparison of XPath and LINQ to XML</span></span>
<span data-ttu-id="a223e-103">Výraz XPath a technologie LINQ to XML nabízejí některé podobné funkce.</span><span class="sxs-lookup"><span data-stu-id="a223e-103">XPath and LINQ to XML offer some similar functionality.</span></span> <span data-ttu-id="a223e-104">Jak lze použít k dotazování stromu XML, vrátí tyto výsledky jako kolekci elementů, kolekce atributů, kolekce uzlů nebo hodnotu elementu nebo atributu.</span><span class="sxs-lookup"><span data-stu-id="a223e-104">Both can be used to query an XML tree, returning such results as a collection of elements, a collection of attributes, a collection of nodes, or the value of an element or attribute.</span></span> <span data-ttu-id="a223e-105">Existují však také několik rozdílů.</span><span class="sxs-lookup"><span data-stu-id="a223e-105">However, there are also some differences.</span></span>  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a><span data-ttu-id="a223e-106">Rozdíly mezi XPath a technologie LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="a223e-106">Differences Between XPath and LINQ to XML</span></span>  
 <span data-ttu-id="a223e-107">Výraz XPath není povolena projekce nových typů.</span><span class="sxs-lookup"><span data-stu-id="a223e-107">XPath does not allow projection of new types.</span></span> <span data-ttu-id="a223e-108">To může vrátit pouze kolekce uzlů ze stromu, zatímco LINQ to XML můžete spustit dotaz a projekt grafu objektu nebo stromu XML v nový tvar.</span><span class="sxs-lookup"><span data-stu-id="a223e-108">It can only return collections of nodes from the tree, whereas LINQ to XML can execute a query and project an object graph or an XML tree in a new shape.</span></span> <span data-ttu-id="a223e-109">Technologie LINQ to XML dotazů zvětšíte mnohem víc funkcí a jsou výrazně výkonnější než výrazy XPath.</span><span class="sxs-lookup"><span data-stu-id="a223e-109">LINQ to XML queries encompass much more functionality and are much more powerful than XPath expressions.</span></span>  
  
 <span data-ttu-id="a223e-110">Výrazy XPath existovat samostatně v rámci řetězce.</span><span class="sxs-lookup"><span data-stu-id="a223e-110">XPath expressions exist in isolation within a string.</span></span> <span data-ttu-id="a223e-111">Kompilátor jazyka C# vám nemůže pomoci parsovat výraz XPath v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="a223e-111">The C# compiler cannot help parse the XPath expression at compile time.</span></span> <span data-ttu-id="a223e-112">Naopak LINQ to XML dotazy jsou analyzovány a zkompilovány kompilátorem jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="a223e-112">By contrast, LINQ to XML queries are parsed and compiled by the C# compiler.</span></span> <span data-ttu-id="a223e-113">Kompilátoru je moci zachytávat chyby mnoho dotazů.</span><span class="sxs-lookup"><span data-stu-id="a223e-113">The compiler is able to catch many query errors.</span></span>  
  
 <span data-ttu-id="a223e-114">Výraz XPath výsledky nejsou silného typu.</span><span class="sxs-lookup"><span data-stu-id="a223e-114">XPath results are not strongly typed.</span></span> <span data-ttu-id="a223e-115">V počtu situací je výsledkem vyhodnocení výrazu XPath objektu a je vývojářům určit správný typ a přetypujte výsledek podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="a223e-115">In a number of circumstances, the result of evaluating an XPath expression is an object, and it is up to the developer to determine the proper type and cast the result as necessary.</span></span> <span data-ttu-id="a223e-116">Naopak projekce v LINQ dotazu XML jsou silného typu.</span><span class="sxs-lookup"><span data-stu-id="a223e-116">By contrast, the projections from a LINQ to XML query are strongly typed.</span></span>  
  
## <a name="result-ordering"></a><span data-ttu-id="a223e-117">Výsledek řazení</span><span class="sxs-lookup"><span data-stu-id="a223e-117">Result Ordering</span></span>  
 <span data-ttu-id="a223e-118">Výraz XPath 1.0 doporučení uvádí, že kolekce, která je výsledkem vyhodnocení výrazu XPath Neseřazený.</span><span class="sxs-lookup"><span data-stu-id="a223e-118">The XPath 1.0 Recommendation states that a collection that is the result of evaluating an XPath expression is unordered.</span></span>  
  
 <span data-ttu-id="a223e-119">Ale když iterace v kolekci vrácené LINQ metody osy XML XPath, uzly v kolekci jsou vráceny v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="a223e-119">However, when iterating through a collection returned by a LINQ to XML XPath axis method, the nodes in the collection are returned in document order.</span></span> <span data-ttu-id="a223e-120">To platí i v případě, že přístup k osy XPath kde predikáty se vyjadřují v pořadí reverzní dokumentů, jako například `preceding` a `preceding-sibling`.</span><span class="sxs-lookup"><span data-stu-id="a223e-120">This is the case even when accessing the XPath axes where predicates are expressed in terms of reverse document order, such as `preceding` and `preceding-sibling`.</span></span>  
  
 <span data-ttu-id="a223e-121">Naopak většina technologie LINQ to XML osy vrací kolekce v pořadí dokumentů, ale dva z nich, <xref:System.Xml.Linq.XNode.Ancestors%2A> a <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, vrací kolekce v pořadí reverzní dokumentů.</span><span class="sxs-lookup"><span data-stu-id="a223e-121">By contrast, most of the LINQ to XML axes return collections in document order, but two of them, <xref:System.Xml.Linq.XNode.Ancestors%2A> and <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, return collections in reverse document order.</span></span> <span data-ttu-id="a223e-122">V následující tabulce vytvoří výčet OS a určuje pořadí kolekce pro jednotlivé:</span><span class="sxs-lookup"><span data-stu-id="a223e-122">The following table enumerates the axes, and indicates collection order for each:</span></span>  
  
|<span data-ttu-id="a223e-123">Technologie LINQ to XML – osa</span><span class="sxs-lookup"><span data-stu-id="a223e-123">LINQ to XML axis</span></span>|<span data-ttu-id="a223e-124">Řazení</span><span class="sxs-lookup"><span data-stu-id="a223e-124">Ordering</span></span>|  
|----------------------|--------------|  
|<span data-ttu-id="a223e-125">XContainer.DescendantNodes</span><span class="sxs-lookup"><span data-stu-id="a223e-125">XContainer.DescendantNodes</span></span>|<span data-ttu-id="a223e-126">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="a223e-126">Document order</span></span>|  
|<span data-ttu-id="a223e-127">XContainer.Descendants</span><span class="sxs-lookup"><span data-stu-id="a223e-127">XContainer.Descendants</span></span>|<span data-ttu-id="a223e-128">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="a223e-128">Document order</span></span>|  
|<span data-ttu-id="a223e-129">XContainer.Elements</span><span class="sxs-lookup"><span data-stu-id="a223e-129">XContainer.Elements</span></span>|<span data-ttu-id="a223e-130">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="a223e-130">Document order</span></span>|  
|<span data-ttu-id="a223e-131">XContainer.Nodes</span><span class="sxs-lookup"><span data-stu-id="a223e-131">XContainer.Nodes</span></span>|<span data-ttu-id="a223e-132">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="a223e-132">Document order</span></span>|  
|<span data-ttu-id="a223e-133">XContainer.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="a223e-133">XContainer.NodesAfterSelf</span></span>|<span data-ttu-id="a223e-134">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="a223e-134">Document order</span></span>|  
|<span data-ttu-id="a223e-135">XContainer.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="a223e-135">XContainer.NodesBeforeSelf</span></span>|<span data-ttu-id="a223e-136">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="a223e-136">Document order</span></span>|  
|<span data-ttu-id="a223e-137">XElement.AncestorsAndSelf</span><span class="sxs-lookup"><span data-stu-id="a223e-137">XElement.AncestorsAndSelf</span></span>|<span data-ttu-id="a223e-138">Pořadí reverzní dokumentů</span><span class="sxs-lookup"><span data-stu-id="a223e-138">Reverse document order</span></span>|  
|<span data-ttu-id="a223e-139">XElement.Attributes</span><span class="sxs-lookup"><span data-stu-id="a223e-139">XElement.Attributes</span></span>|<span data-ttu-id="a223e-140">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="a223e-140">Document order</span></span>|  
|<span data-ttu-id="a223e-141">XElement.DescendantNodesAndSelf</span><span class="sxs-lookup"><span data-stu-id="a223e-141">XElement.DescendantNodesAndSelf</span></span>|<span data-ttu-id="a223e-142">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="a223e-142">Document order</span></span>|  
|<span data-ttu-id="a223e-143">XElement.DescendantsAndSelf</span><span class="sxs-lookup"><span data-stu-id="a223e-143">XElement.DescendantsAndSelf</span></span>|<span data-ttu-id="a223e-144">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="a223e-144">Document order</span></span>|  
|<span data-ttu-id="a223e-145">XNode.Ancestors</span><span class="sxs-lookup"><span data-stu-id="a223e-145">XNode.Ancestors</span></span>|<span data-ttu-id="a223e-146">Pořadí reverzní dokumentů</span><span class="sxs-lookup"><span data-stu-id="a223e-146">Reverse document order</span></span>|  
|<span data-ttu-id="a223e-147">XNode.ElementsAfterSelf</span><span class="sxs-lookup"><span data-stu-id="a223e-147">XNode.ElementsAfterSelf</span></span>|<span data-ttu-id="a223e-148">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="a223e-148">Document order</span></span>|  
|<span data-ttu-id="a223e-149">XNode.ElementsBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="a223e-149">XNode.ElementsBeforeSelf</span></span>|<span data-ttu-id="a223e-150">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="a223e-150">Document order</span></span>|  
|<span data-ttu-id="a223e-151">XNode.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="a223e-151">XNode.NodesAfterSelf</span></span>|<span data-ttu-id="a223e-152">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="a223e-152">Document order</span></span>|  
|<span data-ttu-id="a223e-153">XNode.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="a223e-153">XNode.NodesBeforeSelf</span></span>|<span data-ttu-id="a223e-154">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="a223e-154">Document order</span></span>|  
  
## <a name="positional-predicates"></a><span data-ttu-id="a223e-155">Poziční predikáty.</span><span class="sxs-lookup"><span data-stu-id="a223e-155">Positional Predicates</span></span>  
 <span data-ttu-id="a223e-156">Ve výrazu XPath poziční predikáty se vyjadřují v pořadí dokumentů pro mnoho osy, ale jsou vyjádřeny v pořadí reverzní dokumentů pro reverzní osy, které jsou `preceding`, `preceding-sibling`, `ancestor`, a `ancestor-or-self`.</span><span class="sxs-lookup"><span data-stu-id="a223e-156">Within an XPath expression, positional predicates are expressed in terms of document order for many axes, but are expressed in reverse document order for reverse axes, which are `preceding`, `preceding-sibling`, `ancestor`, and `ancestor-or-self`.</span></span> <span data-ttu-id="a223e-157">Například výraz XPath `preceding-sibling::*[1]` vrátí bezprostředně předcházející na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="a223e-157">For example, the XPath expression `preceding-sibling::*[1]` returns the immediately preceding sibling.</span></span> <span data-ttu-id="a223e-158">To platí i v případě, že sada konečný výsledek se zobrazí v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="a223e-158">This is the case even though the final result set is presented in document order.</span></span>  
  
 <span data-ttu-id="a223e-159">Naopak všechny predikáty poziční v technologii LINQ to XML se vždy vyjadřují v pořadí osy.</span><span class="sxs-lookup"><span data-stu-id="a223e-159">By contrast, all positional predicates in LINQ to XML are always expressed in terms of the order of the axis.</span></span> <span data-ttu-id="a223e-160">Například `anElement.ElementsBeforeSelf().ElementAt(0)` vrátí první podřízený element nadřazeného elementu poslal dotaz, ne okamžité předcházející na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="a223e-160">For example, `anElement.ElementsBeforeSelf().ElementAt(0)` returns the first child element of the parent of the queried element, not the immediate preceding sibling.</span></span> <span data-ttu-id="a223e-161">Další příklad: `anElement.Ancestors().ElementAt(0)` vrátí nadřazeného elementu.</span><span class="sxs-lookup"><span data-stu-id="a223e-161">Another example: `anElement.Ancestors().ElementAt(0)` returns the parent element.</span></span>  
  
 <span data-ttu-id="a223e-162">Pokud byste chtěli najít bezprostředně předcházející prvek v technologii LINQ to XML, měli byste napsat následující výraz:</span><span class="sxs-lookup"><span data-stu-id="a223e-162">If you wanted to find the immediately preceding element in LINQ to XML, you would write the following expression:</span></span>  
  
```csharp
ElementsBeforeSelf().Last()
```
  
```vb
ElementsBeforeSelf().Last()
```
  
## <a name="performance-differences"></a><span data-ttu-id="a223e-163">Rozdíly ve výkonu</span><span class="sxs-lookup"><span data-stu-id="a223e-163">Performance Differences</span></span>  
 <span data-ttu-id="a223e-164">Dotazy XPath, které používají funkce XPath v technologii LINQ to XML nebude provádět, tak LINQ dotazy XML.</span><span class="sxs-lookup"><span data-stu-id="a223e-164">XPath queries that use the XPath functionality in LINQ to XML will not perform as well as LINQ to XML queries.</span></span>  
  
## <a name="comparison-of-composition"></a><span data-ttu-id="a223e-165">Porovnání složení</span><span class="sxs-lookup"><span data-stu-id="a223e-165">Comparison of Composition</span></span>  
 <span data-ttu-id="a223e-166">Složení LINQ to XML dotazu je poněkud paralelní složení výraz XPath, ale velmi odlišné v syntaxi.</span><span class="sxs-lookup"><span data-stu-id="a223e-166">Composition of a LINQ to XML query is somewhat parallel to composition of an XPath expression, although very different in syntax.</span></span>  
  
 <span data-ttu-id="a223e-167">Například, pokud máte v proměnné s názvem elementu `customers`, a vy chcete najít podřízený element s názvem `CompanyName` v rámci všech podřízených elementů s názvem `Customer`, měli byste napsat výraz XPath následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="a223e-167">For example, if you have an element in a variable named `customers`, and you want to find a grandchild element named `CompanyName` under all child elements named `Customer`, you would write an XPath expression as follows:</span></span>  
  
```csharp  
customers.XPathSelectElements("./Customer/CompanyName")
```  
  
```vb
customers.XPathSelectElements("./Customer/CompanyName")
```

 <span data-ttu-id="a223e-168">Je ekvivalentní LINQ to XML dotazu:</span><span class="sxs-lookup"><span data-stu-id="a223e-168">The equivalent LINQ to XML query is:</span></span>  
  
```csharp  
customers.Elements("Customer").Elements("CompanyName")
```  
  
```vb
customers.Elements("Customer").Elements("CompanyName")
```  

 <span data-ttu-id="a223e-169">Jsou podobné parallels pro každý OS XPath.</span><span class="sxs-lookup"><span data-stu-id="a223e-169">There are similar parallels for each of the XPath axes.</span></span>  
  
|<span data-ttu-id="a223e-170">Výraz XPath osy</span><span class="sxs-lookup"><span data-stu-id="a223e-170">XPath axis</span></span>|<span data-ttu-id="a223e-171">Technologie LINQ to XML – osa</span><span class="sxs-lookup"><span data-stu-id="a223e-171">LINQ to XML axis</span></span>|  
|----------------|----------------------|  
|<span data-ttu-id="a223e-172">podřízený (na ose výchozí)</span><span class="sxs-lookup"><span data-stu-id="a223e-172">child (the default axis)</span></span>|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a223e-173">Nadřazené (.)</span><span class="sxs-lookup"><span data-stu-id="a223e-173">Parent (..)</span></span>|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a223e-174">atribut osy (@)</span><span class="sxs-lookup"><span data-stu-id="a223e-174">attribute axis (@)</span></span>|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="a223e-175">or</span><span class="sxs-lookup"><span data-stu-id="a223e-175">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a223e-176">předchůdce osy</span><span class="sxs-lookup"><span data-stu-id="a223e-176">ancestor axis</span></span>|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a223e-177">předchůdce nebo self OS</span><span class="sxs-lookup"><span data-stu-id="a223e-177">ancestor-or-self axis</span></span>|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a223e-178">Následnické osy (/ /)</span><span class="sxs-lookup"><span data-stu-id="a223e-178">descendant axis (//)</span></span>|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="a223e-179">or</span><span class="sxs-lookup"><span data-stu-id="a223e-179">or</span></span><br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a223e-180">descendant-or-self</span><span class="sxs-lookup"><span data-stu-id="a223e-180">descendant-or-self</span></span>|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="a223e-181">or</span><span class="sxs-lookup"><span data-stu-id="a223e-181">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a223e-182">Následující na stejné úrovni</span><span class="sxs-lookup"><span data-stu-id="a223e-182">following-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="a223e-183">or</span><span class="sxs-lookup"><span data-stu-id="a223e-183">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a223e-184">předcházející na stejné úrovni</span><span class="sxs-lookup"><span data-stu-id="a223e-184">preceding-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="a223e-185">or</span><span class="sxs-lookup"><span data-stu-id="a223e-185">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a223e-186">Následující</span><span class="sxs-lookup"><span data-stu-id="a223e-186">following</span></span>|<span data-ttu-id="a223e-187">Žádný přímý ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="a223e-187">No direct equivalent.</span></span>|  
|<span data-ttu-id="a223e-188">předchozí</span><span class="sxs-lookup"><span data-stu-id="a223e-188">preceding</span></span>|<span data-ttu-id="a223e-189">Žádný přímý ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="a223e-189">No direct equivalent.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a223e-190">Viz také</span><span class="sxs-lookup"><span data-stu-id="a223e-190">See Also</span></span>

- [<span data-ttu-id="a223e-191">LINQ to XML pro uživatele jazyka XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="a223e-191">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
