---
title: Obor výchozích názvových prostorů v jazyce C#
ms.date: 07/20/2015
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: 7615351f6e5f8b18bd6466a83d54aa65a6c99b50
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253037"
---
# <a name="scope-of-default-namespaces-in-c"></a><span data-ttu-id="b8ab3-102">Rozsah výchozích oborů názvů v C\#</span><span class="sxs-lookup"><span data-stu-id="b8ab3-102">Scope of Default Namespaces in C\#</span></span>
<span data-ttu-id="b8ab3-103">Výchozí obory názvů jako reprezentované ve stromu XML nejsou pro dotazy v oboru.</span><span class="sxs-lookup"><span data-stu-id="b8ab3-103">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="b8ab3-104">Pokud máte XML, který je ve výchozím oboru <xref:System.Xml.Linq.XNamespace> názvů, stále musíte deklarovat proměnnou a zkombinovat ji s místním názvem, abyste vytvořili kvalifikovaný název, který bude použit v dotazu.</span><span class="sxs-lookup"><span data-stu-id="b8ab3-104">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="b8ab3-105">Jedním z nejčastějších problémů při dotazování na stromy XML je, že pokud má strom XML výchozí obor názvů, vývojář někdy zapíše dotaz, jako by xml nebyl v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b8ab3-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="b8ab3-106">První sada příkladů v tomto tématu ukazuje typický způsob, jakým je načten xml ve výchozím oboru názvů, ale je dotazován nesprávně.</span><span class="sxs-lookup"><span data-stu-id="b8ab3-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="b8ab3-107">Druhá sada příkladů zobrazuje potřebné opravy, takže můžete dotazovat XML v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b8ab3-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8ab3-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="b8ab3-108">Example</span></span>  
 <span data-ttu-id="b8ab3-109">Tento příklad ukazuje vytvoření xml v oboru názvů a dotaz, který vrací prázdnou sadu výsledků.</span><span class="sxs-lookup"><span data-stu-id="b8ab3-109">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b8ab3-110">kód</span><span class="sxs-lookup"><span data-stu-id="b8ab3-110">Code</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements("Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
### <a name="comments"></a><span data-ttu-id="b8ab3-111">Komentáře</span><span class="sxs-lookup"><span data-stu-id="b8ab3-111">Comments</span></span>  
 <span data-ttu-id="b8ab3-112">Tento příklad přináší následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="b8ab3-112">This example produces the following result:</span></span>  
  
```output  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="b8ab3-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="b8ab3-113">Example</span></span>  
 <span data-ttu-id="b8ab3-114">Tento příklad ukazuje vytvoření xml v oboru názvů a dotaz, který je kódován správně.</span><span class="sxs-lookup"><span data-stu-id="b8ab3-114">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="b8ab3-115">Na rozdíl od nesprávně kódované příklad výše, správný přístup při použití Jazyka <xref:System.Xml.Linq.XNamespace> C# je deklarovat <xref:System.Xml.Linq.XName> a inicializovat objekt a použít při zadávání objektů.</span><span class="sxs-lookup"><span data-stu-id="b8ab3-115">In contrast to the incorrectly coded example above, the correct approach when using C# is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="b8ab3-116">V tomto případě argument <xref:System.Xml.Linq.XContainer.Elements%2A> metody je <xref:System.Xml.Linq.XName> objekt.</span><span class="sxs-lookup"><span data-stu-id="b8ab3-116">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b8ab3-117">kód</span><span class="sxs-lookup"><span data-stu-id="b8ab3-117">Code</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
### <a name="comments"></a><span data-ttu-id="b8ab3-118">Komentáře</span><span class="sxs-lookup"><span data-stu-id="b8ab3-118">Comments</span></span>  
 <span data-ttu-id="b8ab3-119">Tento příklad přináší následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="b8ab3-119">This example produces the following result:</span></span>  
  
```output  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="b8ab3-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="b8ab3-120">See also</span></span>

- [<span data-ttu-id="b8ab3-121">Obory názvů – přehled (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b8ab3-121">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
