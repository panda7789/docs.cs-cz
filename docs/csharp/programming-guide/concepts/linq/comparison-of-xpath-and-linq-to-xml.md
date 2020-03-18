---
title: Porovnání jazyka XPath a technologie LINQ to XML
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: e9bf192a2075653802f0c5a8b4e44ff0ceacb975
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "66487541"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a><span data-ttu-id="be562-102">Porovnání jazyka XPath a technologie LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="be562-102">Comparison of XPath and LINQ to XML</span></span>
<span data-ttu-id="be562-103">XPath a LINQ na XML nabízejí některé podobné funkce.</span><span class="sxs-lookup"><span data-stu-id="be562-103">XPath and LINQ to XML offer some similar functionality.</span></span> <span data-ttu-id="be562-104">Oba lze použít k dotazování stromu XML, vrácení takové výsledky jako kolekce prvků, kolekce atributů, kolekce uzlů nebo hodnota prvku nebo atributu.</span><span class="sxs-lookup"><span data-stu-id="be562-104">Both can be used to query an XML tree, returning such results as a collection of elements, a collection of attributes, a collection of nodes, or the value of an element or attribute.</span></span> <span data-ttu-id="be562-105">Existují však také určité rozdíly.</span><span class="sxs-lookup"><span data-stu-id="be562-105">However, there are also some differences.</span></span>  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a><span data-ttu-id="be562-106">Rozdíly mezi XPath a LINQ na XML</span><span class="sxs-lookup"><span data-stu-id="be562-106">Differences Between XPath and LINQ to XML</span></span>  
 <span data-ttu-id="be562-107">XPath neumožňuje projekci nových typů.</span><span class="sxs-lookup"><span data-stu-id="be562-107">XPath does not allow projection of new types.</span></span> <span data-ttu-id="be562-108">Může vrátit pouze kolekce uzlů ze stromu, zatímco LINQ do XML může spustit dotaz a promítnout objektový graf nebo strom XML v novém obrazci.</span><span class="sxs-lookup"><span data-stu-id="be562-108">It can only return collections of nodes from the tree, whereas LINQ to XML can execute a query and project an object graph or an XML tree in a new shape.</span></span> <span data-ttu-id="be562-109">Dotazy LINQ na XML zahrnují mnohem více funkcí a jsou mnohem výkonnější než výrazy XPath.</span><span class="sxs-lookup"><span data-stu-id="be562-109">LINQ to XML queries encompass much more functionality and are much more powerful than XPath expressions.</span></span>  
  
 <span data-ttu-id="be562-110">Výrazy XPath existují izolovaně v rámci řetězce.</span><span class="sxs-lookup"><span data-stu-id="be562-110">XPath expressions exist in isolation within a string.</span></span> <span data-ttu-id="be562-111">Kompilátor Jazyka C# nemůže pomoci analyzovat výraz XPath v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="be562-111">The C# compiler cannot help parse the XPath expression at compile time.</span></span> <span data-ttu-id="be562-112">Naproti tomu linq na XML dotazy jsou analyzovány a kompilovány kompilátorem Jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="be562-112">By contrast, LINQ to XML queries are parsed and compiled by the C# compiler.</span></span> <span data-ttu-id="be562-113">Kompilátor je schopen zachytit mnoho chyb dotazu.</span><span class="sxs-lookup"><span data-stu-id="be562-113">The compiler is able to catch many query errors.</span></span>  
  
 <span data-ttu-id="be562-114">Výsledky XPath nejsou silně zadány.</span><span class="sxs-lookup"><span data-stu-id="be562-114">XPath results are not strongly typed.</span></span> <span data-ttu-id="be562-115">V řadě okolností je výsledkem vyhodnocení výrazu XPath objekt a je na vývojáři, aby určil správný typ a podle potřeby přetypoval výsledek.</span><span class="sxs-lookup"><span data-stu-id="be562-115">In a number of circumstances, the result of evaluating an XPath expression is an object, and it is up to the developer to determine the proper type and cast the result as necessary.</span></span> <span data-ttu-id="be562-116">Naproti tomu projekce z linq do dotazu XML jsou silně zadávány.</span><span class="sxs-lookup"><span data-stu-id="be562-116">By contrast, the projections from a LINQ to XML query are strongly typed.</span></span>  
  
## <a name="result-ordering"></a><span data-ttu-id="be562-117">Pořadí výsledků</span><span class="sxs-lookup"><span data-stu-id="be562-117">Result Ordering</span></span>  
 <span data-ttu-id="be562-118">Doporučení XPath 1.0 uvádí, že kolekce, která je výsledkem vyhodnocení výrazu XPath je neuspořádané.</span><span class="sxs-lookup"><span data-stu-id="be562-118">The XPath 1.0 Recommendation states that a collection that is the result of evaluating an XPath expression is unordered.</span></span>  
  
 <span data-ttu-id="be562-119">Však při iterace prostřednictvím kolekce vrácené LINQ na XML XPath osy metody, uzly v kolekci jsou vráceny v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="be562-119">However, when iterating through a collection returned by a LINQ to XML XPath axis method, the nodes in the collection are returned in document order.</span></span> <span data-ttu-id="be562-120">To platí i při přístupu k osám XPath, kde jsou predikáty vyjádřeny obráceným pořadím dokumentů, například `preceding` a `preceding-sibling`.</span><span class="sxs-lookup"><span data-stu-id="be562-120">This is the case even when accessing the XPath axes where predicates are expressed in terms of reverse document order, such as `preceding` and `preceding-sibling`.</span></span>  
  
 <span data-ttu-id="be562-121">Naproti tomu většina os LINQ do XML vrací kolekce v pořadí <xref:System.Xml.Linq.XNode.Ancestors%2A> <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>dokumentů, ale dvě z nich a , vrátí kolekce v obráceném pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="be562-121">By contrast, most of the LINQ to XML axes return collections in document order, but two of them, <xref:System.Xml.Linq.XNode.Ancestors%2A> and <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, return collections in reverse document order.</span></span> <span data-ttu-id="be562-122">Následující tabulka obsahuje výčet os a označuje pořadí sběru pro každou z nich:</span><span class="sxs-lookup"><span data-stu-id="be562-122">The following table enumerates the axes, and indicates collection order for each:</span></span>  
  
|<span data-ttu-id="be562-123">LinQ na osu XML</span><span class="sxs-lookup"><span data-stu-id="be562-123">LINQ to XML axis</span></span>|<span data-ttu-id="be562-124">Řazení</span><span class="sxs-lookup"><span data-stu-id="be562-124">Ordering</span></span>|  
|----------------------|--------------|  
|<span data-ttu-id="be562-125">XContainer.DescendantNodes</span><span class="sxs-lookup"><span data-stu-id="be562-125">XContainer.DescendantNodes</span></span>|<span data-ttu-id="be562-126">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="be562-126">Document order</span></span>|  
|<span data-ttu-id="be562-127">XContainer.Descendants</span><span class="sxs-lookup"><span data-stu-id="be562-127">XContainer.Descendants</span></span>|<span data-ttu-id="be562-128">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="be562-128">Document order</span></span>|  
|<span data-ttu-id="be562-129">XKontejner.Elements</span><span class="sxs-lookup"><span data-stu-id="be562-129">XContainer.Elements</span></span>|<span data-ttu-id="be562-130">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="be562-130">Document order</span></span>|  
|<span data-ttu-id="be562-131">XContainer.Uzly</span><span class="sxs-lookup"><span data-stu-id="be562-131">XContainer.Nodes</span></span>|<span data-ttu-id="be562-132">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="be562-132">Document order</span></span>|  
|<span data-ttu-id="be562-133">XContainer.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="be562-133">XContainer.NodesAfterSelf</span></span>|<span data-ttu-id="be562-134">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="be562-134">Document order</span></span>|  
|<span data-ttu-id="be562-135">XContainer.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="be562-135">XContainer.NodesBeforeSelf</span></span>|<span data-ttu-id="be562-136">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="be562-136">Document order</span></span>|  
|<span data-ttu-id="be562-137">XElement.AncestorsAndSelf</span><span class="sxs-lookup"><span data-stu-id="be562-137">XElement.AncestorsAndSelf</span></span>|<span data-ttu-id="be562-138">Obrácené pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="be562-138">Reverse document order</span></span>|  
|<span data-ttu-id="be562-139">XElement.Atributy</span><span class="sxs-lookup"><span data-stu-id="be562-139">XElement.Attributes</span></span>|<span data-ttu-id="be562-140">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="be562-140">Document order</span></span>|  
|<span data-ttu-id="be562-141">XElement.DescendantNodesAndSelf</span><span class="sxs-lookup"><span data-stu-id="be562-141">XElement.DescendantNodesAndSelf</span></span>|<span data-ttu-id="be562-142">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="be562-142">Document order</span></span>|  
|<span data-ttu-id="be562-143">XElement.DescendantsAndSelf</span><span class="sxs-lookup"><span data-stu-id="be562-143">XElement.DescendantsAndSelf</span></span>|<span data-ttu-id="be562-144">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="be562-144">Document order</span></span>|  
|<span data-ttu-id="be562-145">XNode.Předkové</span><span class="sxs-lookup"><span data-stu-id="be562-145">XNode.Ancestors</span></span>|<span data-ttu-id="be562-146">Obrácené pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="be562-146">Reverse document order</span></span>|  
|<span data-ttu-id="be562-147">XNode.ElementsAfterSelf</span><span class="sxs-lookup"><span data-stu-id="be562-147">XNode.ElementsAfterSelf</span></span>|<span data-ttu-id="be562-148">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="be562-148">Document order</span></span>|  
|<span data-ttu-id="be562-149">XNode.ElementsBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="be562-149">XNode.ElementsBeforeSelf</span></span>|<span data-ttu-id="be562-150">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="be562-150">Document order</span></span>|  
|<span data-ttu-id="be562-151">XNode.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="be562-151">XNode.NodesAfterSelf</span></span>|<span data-ttu-id="be562-152">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="be562-152">Document order</span></span>|  
|<span data-ttu-id="be562-153">XNode.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="be562-153">XNode.NodesBeforeSelf</span></span>|<span data-ttu-id="be562-154">Pořadí dokumentů</span><span class="sxs-lookup"><span data-stu-id="be562-154">Document order</span></span>|  
  
## <a name="positional-predicates"></a><span data-ttu-id="be562-155">Poziční predikáty</span><span class="sxs-lookup"><span data-stu-id="be562-155">Positional Predicates</span></span>  
 <span data-ttu-id="be562-156">V rámci výrazu XPath jsou poziční predikáty vyjádřeny v pořadí dokumentů pro mnoho os, ale `preceding` `preceding-sibling`jsou `ancestor`vyjádřeny v obráceném pořadí dokumentů pro reverzní osy, které jsou , , , a `ancestor-or-self`.</span><span class="sxs-lookup"><span data-stu-id="be562-156">Within an XPath expression, positional predicates are expressed in terms of document order for many axes, but are expressed in reverse document order for reverse axes, which are `preceding`, `preceding-sibling`, `ancestor`, and `ancestor-or-self`.</span></span> <span data-ttu-id="be562-157">Například výraz `preceding-sibling::*[1]` XPath vrátí bezprostředně předcházející na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="be562-157">For example, the XPath expression `preceding-sibling::*[1]` returns the immediately preceding sibling.</span></span> <span data-ttu-id="be562-158">To je případ i v případě, že konečná sada výsledků je uveden v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="be562-158">This is the case even though the final result set is presented in document order.</span></span>  
  
 <span data-ttu-id="be562-159">Naproti tomu všechny poziční predikáty v LINQ na XML jsou vždy vyjádřeny v pořadí osy.</span><span class="sxs-lookup"><span data-stu-id="be562-159">By contrast, all positional predicates in LINQ to XML are always expressed in terms of the order of the axis.</span></span> <span data-ttu-id="be562-160">Například `anElement.ElementsBeforeSelf().ElementAt(0)` vrátí první podřízený prvek nadřazeného prvku dotazovaného prvku, nikoli bezprostředně předcházející na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="be562-160">For example, `anElement.ElementsBeforeSelf().ElementAt(0)` returns the first child element of the parent of the queried element, not the immediate preceding sibling.</span></span> <span data-ttu-id="be562-161">Jiný příklad: `anElement.Ancestors().ElementAt(0)` vrátí nadřazený prvek.</span><span class="sxs-lookup"><span data-stu-id="be562-161">Another example: `anElement.Ancestors().ElementAt(0)` returns the parent element.</span></span>  
  
 <span data-ttu-id="be562-162">Pokud byste chtěli najít bezprostředně předcházející prvek v LINQ do XML, napsali byste následující výraz:</span><span class="sxs-lookup"><span data-stu-id="be562-162">If you wanted to find the immediately preceding element in LINQ to XML, you would write the following expression:</span></span>  
  
```csharp
ElementsBeforeSelf().Last()
```
  
```vb
ElementsBeforeSelf().Last()
```
  
## <a name="performance-differences"></a><span data-ttu-id="be562-163">Rozdíly ve výkonu</span><span class="sxs-lookup"><span data-stu-id="be562-163">Performance Differences</span></span>  
 <span data-ttu-id="be562-164">Dotazy XPath, které používají funkci XPath v LINQ na XML, nebudou fungovat tak dobře jako linq na dotazy XML.</span><span class="sxs-lookup"><span data-stu-id="be562-164">XPath queries that use the XPath functionality in LINQ to XML will not perform as well as LINQ to XML queries.</span></span>  
  
## <a name="comparison-of-composition"></a><span data-ttu-id="be562-165">Porovnání složení</span><span class="sxs-lookup"><span data-stu-id="be562-165">Comparison of Composition</span></span>  
 <span data-ttu-id="be562-166">Složení dotazu LINQ na XML je poněkud paralelní se složením výrazu XPath, i když se velmi liší syntaxí.</span><span class="sxs-lookup"><span data-stu-id="be562-166">Composition of a LINQ to XML query is somewhat parallel to composition of an XPath expression, although very different in syntax.</span></span>  
  
 <span data-ttu-id="be562-167">Například pokud máte prvek v proměnné `customers`s názvem , a chcete `CompanyName` najít prvek vnouče s názvem pod všechny podřízené prvky s názvem `Customer`, byste napsat výraz XPath takto:</span><span class="sxs-lookup"><span data-stu-id="be562-167">For example, if you have an element in a variable named `customers`, and you want to find a grandchild element named `CompanyName` under all child elements named `Customer`, you would write an XPath expression as follows:</span></span>  
  
```csharp  
customers.XPathSelectElements("./Customer/CompanyName")
```  
  
```vb
customers.XPathSelectElements("./Customer/CompanyName")
```

 <span data-ttu-id="be562-168">Ekvivalentní linq dotazu XML je:</span><span class="sxs-lookup"><span data-stu-id="be562-168">The equivalent LINQ to XML query is:</span></span>  
  
```csharp  
customers.Elements("Customer").Elements("CompanyName")
```  
  
```vb
customers.Elements("Customer").Elements("CompanyName")
```  

 <span data-ttu-id="be562-169">Existují podobné paralely pro každou z os XPath.</span><span class="sxs-lookup"><span data-stu-id="be562-169">There are similar parallels for each of the XPath axes.</span></span>  
  
|<span data-ttu-id="be562-170">Osa XPath</span><span class="sxs-lookup"><span data-stu-id="be562-170">XPath axis</span></span>|<span data-ttu-id="be562-171">LinQ na osu XML</span><span class="sxs-lookup"><span data-stu-id="be562-171">LINQ to XML axis</span></span>|  
|----------------|----------------------|  
|<span data-ttu-id="be562-172">podřízená (výchozí osa)</span><span class="sxs-lookup"><span data-stu-id="be562-172">child (the default axis)</span></span>|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="be562-173">Rodič (..)od rodičů (..)</span><span class="sxs-lookup"><span data-stu-id="be562-173">Parent (..)</span></span>|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="be562-174">osa atributu (@)</span><span class="sxs-lookup"><span data-stu-id="be562-174">attribute axis (@)</span></span>|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="be562-175">– nebo –</span><span class="sxs-lookup"><span data-stu-id="be562-175">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="be562-176">předek osa</span><span class="sxs-lookup"><span data-stu-id="be562-176">ancestor axis</span></span>|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="be562-177">předek-nebo-vlastní osa</span><span class="sxs-lookup"><span data-stu-id="be562-177">ancestor-or-self axis</span></span>|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="be562-178">následná osa (//)</span><span class="sxs-lookup"><span data-stu-id="be562-178">descendant axis (//)</span></span>|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="be562-179">– nebo –</span><span class="sxs-lookup"><span data-stu-id="be562-179">or</span></span><br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="be562-180">potomek-nebo-já</span><span class="sxs-lookup"><span data-stu-id="be562-180">descendant-or-self</span></span>|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="be562-181">– nebo –</span><span class="sxs-lookup"><span data-stu-id="be562-181">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="be562-182">následující-sourozenec</span><span class="sxs-lookup"><span data-stu-id="be562-182">following-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="be562-183">– nebo –</span><span class="sxs-lookup"><span data-stu-id="be562-183">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="be562-184">předchozí-sourozenec</span><span class="sxs-lookup"><span data-stu-id="be562-184">preceding-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="be562-185">– nebo –</span><span class="sxs-lookup"><span data-stu-id="be562-185">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="be562-186">Následující</span><span class="sxs-lookup"><span data-stu-id="be562-186">following</span></span>|<span data-ttu-id="be562-187">Žádný přímý ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="be562-187">No direct equivalent.</span></span>|  
|<span data-ttu-id="be562-188">Předchozí</span><span class="sxs-lookup"><span data-stu-id="be562-188">preceding</span></span>|<span data-ttu-id="be562-189">Žádný přímý ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="be562-189">No direct equivalent.</span></span>|  
  