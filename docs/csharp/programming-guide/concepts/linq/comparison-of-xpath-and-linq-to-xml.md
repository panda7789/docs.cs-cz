---
title: Porovnání jazyka XPath a technologie LINQ to XML
description: Přečtěte si o podobnostech a rozdílech mezi funkcemi XPath a LINQ to XML v jazyce C#. Pro dotazování stromu XML lze použít obojí.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: e2f34903b20a53dea6e5ff4858d4fadaebd9c37a
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104009"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a><span data-ttu-id="a98aa-104">Porovnání jazyka XPath a technologie LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="a98aa-104">Comparison of XPath and LINQ to XML</span></span>
<span data-ttu-id="a98aa-105">XPath a LINQ to XML nabízejí podobné funkce.</span><span class="sxs-lookup"><span data-stu-id="a98aa-105">XPath and LINQ to XML offer some similar functionality.</span></span> <span data-ttu-id="a98aa-106">Oba lze použít k dotazování stromu XML a vrácení těchto výsledků jako kolekce prvků, kolekce atributů, kolekce uzlů nebo hodnoty elementu nebo atributu.</span><span class="sxs-lookup"><span data-stu-id="a98aa-106">Both can be used to query an XML tree, returning such results as a collection of elements, a collection of attributes, a collection of nodes, or the value of an element or attribute.</span></span> <span data-ttu-id="a98aa-107">Existují však i některé rozdíly.</span><span class="sxs-lookup"><span data-stu-id="a98aa-107">However, there are also some differences.</span></span>  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a><span data-ttu-id="a98aa-108">Rozdíly mezi XPath a LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="a98aa-108">Differences Between XPath and LINQ to XML</span></span>  
 <span data-ttu-id="a98aa-109">XPath nepovoluje projekci nových typů.</span><span class="sxs-lookup"><span data-stu-id="a98aa-109">XPath does not allow projection of new types.</span></span> <span data-ttu-id="a98aa-110">Může vracet pouze kolekce uzlů ze stromu, zatímco LINQ to XML může spustit dotaz a projekt v grafu objektů nebo stromu XML v novém tvaru.</span><span class="sxs-lookup"><span data-stu-id="a98aa-110">It can only return collections of nodes from the tree, whereas LINQ to XML can execute a query and project an object graph or an XML tree in a new shape.</span></span> <span data-ttu-id="a98aa-111">LINQ to XML dotazy zahrnují mnohem více funkcí a jsou mnohem výkonnější než výrazy XPath.</span><span class="sxs-lookup"><span data-stu-id="a98aa-111">LINQ to XML queries encompass much more functionality and are much more powerful than XPath expressions.</span></span>  
  
 <span data-ttu-id="a98aa-112">Výrazy XPath existují v izolaci v rámci řetězce.</span><span class="sxs-lookup"><span data-stu-id="a98aa-112">XPath expressions exist in isolation within a string.</span></span> <span data-ttu-id="a98aa-113">Kompilátor jazyka C# nemůže v době kompilace přispět k analýze výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="a98aa-113">The C# compiler cannot help parse the XPath expression at compile time.</span></span> <span data-ttu-id="a98aa-114">Naopak LINQ to XML dotazy jsou analyzovány a kompilovány kompilátorem jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="a98aa-114">By contrast, LINQ to XML queries are parsed and compiled by the C# compiler.</span></span> <span data-ttu-id="a98aa-115">Kompilátor je schopný zachytit mnoho chyb dotazů.</span><span class="sxs-lookup"><span data-stu-id="a98aa-115">The compiler is able to catch many query errors.</span></span>  
  
 <span data-ttu-id="a98aa-116">Výsledky XPath nejsou silného typu.</span><span class="sxs-lookup"><span data-stu-id="a98aa-116">XPath results are not strongly typed.</span></span> <span data-ttu-id="a98aa-117">V řadě případů je výsledkem vyhodnocení výrazu XPath objekt a je až vývojář, aby určil správný typ a vyhodnotil výsledek podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="a98aa-117">In a number of circumstances, the result of evaluating an XPath expression is an object, and it is up to the developer to determine the proper type and cast the result as necessary.</span></span> <span data-ttu-id="a98aa-118">Naopak projekce z LINQ to XML dotazu jsou silného typu.</span><span class="sxs-lookup"><span data-stu-id="a98aa-118">By contrast, the projections from a LINQ to XML query are strongly typed.</span></span>  
  
## <a name="result-ordering"></a><span data-ttu-id="a98aa-119">Řazení výsledků</span><span class="sxs-lookup"><span data-stu-id="a98aa-119">Result Ordering</span></span>  
 <span data-ttu-id="a98aa-120">Doporučení XPath 1,0 uvádí, že kolekce, která je výsledkem vyhodnocení výrazu XPath, je neuspořádaná.</span><span class="sxs-lookup"><span data-stu-id="a98aa-120">The XPath 1.0 Recommendation states that a collection that is the result of evaluating an XPath expression is unordered.</span></span>  
  
 <span data-ttu-id="a98aa-121">Při iteraci kolekcí vrácených LINQ to XML metodou osy XPath však budou uzly v kolekci vráceny v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="a98aa-121">However, when iterating through a collection returned by a LINQ to XML XPath axis method, the nodes in the collection are returned in document order.</span></span> <span data-ttu-id="a98aa-122">Jedná se o případ i při přístupu k ose XPath, kde jsou predikáty vyjádřeny na základě objednávky reverzního dokumentu, například `preceding` a `preceding-sibling` .</span><span class="sxs-lookup"><span data-stu-id="a98aa-122">This is the case even when accessing the XPath axes where predicates are expressed in terms of reverse document order, such as `preceding` and `preceding-sibling`.</span></span>  
  
 <span data-ttu-id="a98aa-123">Naopak většina z LINQ to XML osy vrací kolekce v pořadí dokumentů, ale dva z nich <xref:System.Xml.Linq.XNode.Ancestors%2A> <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A> vrací kolekce v obráceném pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="a98aa-123">By contrast, most of the LINQ to XML axes return collections in document order, but two of them, <xref:System.Xml.Linq.XNode.Ancestors%2A> and <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, return collections in reverse document order.</span></span> <span data-ttu-id="a98aa-124">V následující tabulce jsou vyhodnoceny osy a jsou známy pořadí shromažďování dat:</span><span class="sxs-lookup"><span data-stu-id="a98aa-124">The following table enumerates the axes, and indicates collection order for each:</span></span>  
  
|<span data-ttu-id="a98aa-125">LINQ to XML osa</span><span class="sxs-lookup"><span data-stu-id="a98aa-125">LINQ to XML axis</span></span>|<span data-ttu-id="a98aa-126">Řazení</span><span class="sxs-lookup"><span data-stu-id="a98aa-126">Ordering</span></span>|  
|----------------------|--------------|  
|<span data-ttu-id="a98aa-127">XContainer.DescendantNodes</span><span class="sxs-lookup"><span data-stu-id="a98aa-127">XContainer.DescendantNodes</span></span>|<span data-ttu-id="a98aa-128">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="a98aa-128">Document order</span></span>|  
|<span data-ttu-id="a98aa-129">XContainer. Descendants</span><span class="sxs-lookup"><span data-stu-id="a98aa-129">XContainer.Descendants</span></span>|<span data-ttu-id="a98aa-130">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="a98aa-130">Document order</span></span>|  
|<span data-ttu-id="a98aa-131">XContainer. Elements</span><span class="sxs-lookup"><span data-stu-id="a98aa-131">XContainer.Elements</span></span>|<span data-ttu-id="a98aa-132">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="a98aa-132">Document order</span></span>|  
|<span data-ttu-id="a98aa-133">XContainer. Nodes</span><span class="sxs-lookup"><span data-stu-id="a98aa-133">XContainer.Nodes</span></span>|<span data-ttu-id="a98aa-134">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="a98aa-134">Document order</span></span>|  
|<span data-ttu-id="a98aa-135">XContainer.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="a98aa-135">XContainer.NodesAfterSelf</span></span>|<span data-ttu-id="a98aa-136">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="a98aa-136">Document order</span></span>|  
|<span data-ttu-id="a98aa-137">XContainer.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="a98aa-137">XContainer.NodesBeforeSelf</span></span>|<span data-ttu-id="a98aa-138">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="a98aa-138">Document order</span></span>|  
|<span data-ttu-id="a98aa-139">XElement. AncestorsAndSelf</span><span class="sxs-lookup"><span data-stu-id="a98aa-139">XElement.AncestorsAndSelf</span></span>|<span data-ttu-id="a98aa-140">Obrátit objednávku dokumentu</span><span class="sxs-lookup"><span data-stu-id="a98aa-140">Reverse document order</span></span>|  
|<span data-ttu-id="a98aa-141">XElement. Attributes</span><span class="sxs-lookup"><span data-stu-id="a98aa-141">XElement.Attributes</span></span>|<span data-ttu-id="a98aa-142">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="a98aa-142">Document order</span></span>|  
|<span data-ttu-id="a98aa-143">XElement. DescendantNodesAndSelf</span><span class="sxs-lookup"><span data-stu-id="a98aa-143">XElement.DescendantNodesAndSelf</span></span>|<span data-ttu-id="a98aa-144">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="a98aa-144">Document order</span></span>|  
|<span data-ttu-id="a98aa-145">XElement. DescendantsAndSelf</span><span class="sxs-lookup"><span data-stu-id="a98aa-145">XElement.DescendantsAndSelf</span></span>|<span data-ttu-id="a98aa-146">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="a98aa-146">Document order</span></span>|  
|<span data-ttu-id="a98aa-147">XNode. nadřazených prvků</span><span class="sxs-lookup"><span data-stu-id="a98aa-147">XNode.Ancestors</span></span>|<span data-ttu-id="a98aa-148">Obrátit objednávku dokumentu</span><span class="sxs-lookup"><span data-stu-id="a98aa-148">Reverse document order</span></span>|  
|<span data-ttu-id="a98aa-149">XNode.ElementsAfterSelf</span><span class="sxs-lookup"><span data-stu-id="a98aa-149">XNode.ElementsAfterSelf</span></span>|<span data-ttu-id="a98aa-150">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="a98aa-150">Document order</span></span>|  
|<span data-ttu-id="a98aa-151">XNode.ElementsBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="a98aa-151">XNode.ElementsBeforeSelf</span></span>|<span data-ttu-id="a98aa-152">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="a98aa-152">Document order</span></span>|  
|<span data-ttu-id="a98aa-153">XNode.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="a98aa-153">XNode.NodesAfterSelf</span></span>|<span data-ttu-id="a98aa-154">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="a98aa-154">Document order</span></span>|  
|<span data-ttu-id="a98aa-155">XNode.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="a98aa-155">XNode.NodesBeforeSelf</span></span>|<span data-ttu-id="a98aa-156">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="a98aa-156">Document order</span></span>|  
  
## <a name="positional-predicates"></a><span data-ttu-id="a98aa-157">Poziční predikáty</span><span class="sxs-lookup"><span data-stu-id="a98aa-157">Positional Predicates</span></span>  
 <span data-ttu-id="a98aa-158">V rámci výrazu XPath jsou poziční predikáty vyjádřeny v pořadí dokumentů pro mnoho OS, ale jsou vyjádřeny v obráceném pořadí dokumentů pro reverzní osy, které jsou `preceding` , `preceding-sibling` , `ancestor` a `ancestor-or-self` .</span><span class="sxs-lookup"><span data-stu-id="a98aa-158">Within an XPath expression, positional predicates are expressed in terms of document order for many axes, but are expressed in reverse document order for reverse axes, which are `preceding`, `preceding-sibling`, `ancestor`, and `ancestor-or-self`.</span></span> <span data-ttu-id="a98aa-159">Například výraz XPath `preceding-sibling::*[1]` vrátí přímo předchozí položku na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="a98aa-159">For example, the XPath expression `preceding-sibling::*[1]` returns the immediately preceding sibling.</span></span> <span data-ttu-id="a98aa-160">To platí i v případě, že výsledná sada výsledků je prezentována v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="a98aa-160">This is the case even though the final result set is presented in document order.</span></span>  
  
 <span data-ttu-id="a98aa-161">Naopak všechny poziční predikáty v LINQ to XML jsou vždy vyjádřeny v pořadí podle pořadí osy.</span><span class="sxs-lookup"><span data-stu-id="a98aa-161">By contrast, all positional predicates in LINQ to XML are always expressed in terms of the order of the axis.</span></span> <span data-ttu-id="a98aa-162">Například `anElement.ElementsBeforeSelf().ElementAt(0)` vrátí první podřízený prvek nadřazeného elementu s dotazem, nikoli bezprostřední předchozí uzel na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="a98aa-162">For example, `anElement.ElementsBeforeSelf().ElementAt(0)` returns the first child element of the parent of the queried element, not the immediate preceding sibling.</span></span> <span data-ttu-id="a98aa-163">Jiný příklad: `anElement.Ancestors().ElementAt(0)` Vrátí nadřazený element.</span><span class="sxs-lookup"><span data-stu-id="a98aa-163">Another example: `anElement.Ancestors().ElementAt(0)` returns the parent element.</span></span>  
  
 <span data-ttu-id="a98aa-164">Pokud jste chtěli najít bezprostředně předchozí prvek v LINQ to XML, měli byste napsat následující výraz:</span><span class="sxs-lookup"><span data-stu-id="a98aa-164">If you wanted to find the immediately preceding element in LINQ to XML, you would write the following expression:</span></span>  
  
```csharp
ElementsBeforeSelf().Last()
```
  
```vb
ElementsBeforeSelf().Last()
```
  
## <a name="performance-differences"></a><span data-ttu-id="a98aa-165">Rozdíly v výkonu</span><span class="sxs-lookup"><span data-stu-id="a98aa-165">Performance Differences</span></span>  
 <span data-ttu-id="a98aa-166">Dotazy XPath, které používají funkci XPath v LINQ to XML, nebudou provádět ani dotazy LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="a98aa-166">XPath queries that use the XPath functionality in LINQ to XML will not perform as well as LINQ to XML queries.</span></span>  
  
## <a name="comparison-of-composition"></a><span data-ttu-id="a98aa-167">Porovnání složení</span><span class="sxs-lookup"><span data-stu-id="a98aa-167">Comparison of Composition</span></span>  
 <span data-ttu-id="a98aa-168">Složení LINQ to XMLho dotazu je trochu paralelní na složení výrazu XPath, i když je v syntaxi velmi odlišné.</span><span class="sxs-lookup"><span data-stu-id="a98aa-168">Composition of a LINQ to XML query is somewhat parallel to composition of an XPath expression, although very different in syntax.</span></span>  
  
 <span data-ttu-id="a98aa-169">Například pokud máte prvek v proměnné s názvem `customers` a chcete najít podřízený element s názvem `CompanyName` v rámci všech podřízených elementů s názvem `Customer` , měli byste napsat výraz XPath následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="a98aa-169">For example, if you have an element in a variable named `customers`, and you want to find a grandchild element named `CompanyName` under all child elements named `Customer`, you would write an XPath expression as follows:</span></span>  
  
```csharp  
customers.XPathSelectElements("./Customer/CompanyName")
```  
  
```vb
customers.XPathSelectElements("./Customer/CompanyName")
```

 <span data-ttu-id="a98aa-170">Ekvivalentní LINQ to XML dotaz:</span><span class="sxs-lookup"><span data-stu-id="a98aa-170">The equivalent LINQ to XML query is:</span></span>  
  
```csharp  
customers.Elements("Customer").Elements("CompanyName")
```  
  
```vb
customers.Elements("Customer").Elements("CompanyName")
```  

 <span data-ttu-id="a98aa-171">Pro každou osu XPath existují podobné paralelismuy.</span><span class="sxs-lookup"><span data-stu-id="a98aa-171">There are similar parallels for each of the XPath axes.</span></span>  
  
|<span data-ttu-id="a98aa-172">Osa XPath</span><span class="sxs-lookup"><span data-stu-id="a98aa-172">XPath axis</span></span>|<span data-ttu-id="a98aa-173">LINQ to XML osa</span><span class="sxs-lookup"><span data-stu-id="a98aa-173">LINQ to XML axis</span></span>|  
|----------------|----------------------|  
|<span data-ttu-id="a98aa-174">podřízená (výchozí osa)</span><span class="sxs-lookup"><span data-stu-id="a98aa-174">child (the default axis)</span></span>|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a98aa-175">Nadřazený objekt (..)</span><span class="sxs-lookup"><span data-stu-id="a98aa-175">Parent (..)</span></span>|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a98aa-176">osa atributu (@)</span><span class="sxs-lookup"><span data-stu-id="a98aa-176">attribute axis (@)</span></span>|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="a98aa-177">nebo</span><span class="sxs-lookup"><span data-stu-id="a98aa-177">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a98aa-178">Nadřazená osa</span><span class="sxs-lookup"><span data-stu-id="a98aa-178">ancestor axis</span></span>|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a98aa-179">nadřazený nebo samoobslužná osa</span><span class="sxs-lookup"><span data-stu-id="a98aa-179">ancestor-or-self axis</span></span>|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a98aa-180">osa následníka (//)</span><span class="sxs-lookup"><span data-stu-id="a98aa-180">descendant axis (//)</span></span>|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="a98aa-181">nebo</span><span class="sxs-lookup"><span data-stu-id="a98aa-181">or</span></span><br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a98aa-182">následník – nebo – samotný</span><span class="sxs-lookup"><span data-stu-id="a98aa-182">descendant-or-self</span></span>|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="a98aa-183">nebo</span><span class="sxs-lookup"><span data-stu-id="a98aa-183">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a98aa-184">po stejné úrovni</span><span class="sxs-lookup"><span data-stu-id="a98aa-184">following-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="a98aa-185">nebo</span><span class="sxs-lookup"><span data-stu-id="a98aa-185">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a98aa-186">předchozí uzel na stejné úrovni</span><span class="sxs-lookup"><span data-stu-id="a98aa-186">preceding-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="a98aa-187">nebo</span><span class="sxs-lookup"><span data-stu-id="a98aa-187">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a98aa-188">důsledku</span><span class="sxs-lookup"><span data-stu-id="a98aa-188">following</span></span>|<span data-ttu-id="a98aa-189">Žádný přímý ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="a98aa-189">No direct equivalent.</span></span>|  
|<span data-ttu-id="a98aa-190">cházel</span><span class="sxs-lookup"><span data-stu-id="a98aa-190">preceding</span></span>|<span data-ttu-id="a98aa-191">Žádný přímý ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="a98aa-191">No direct equivalent.</span></span>|  
  