---
title: Obor výchozích názvových prostorů v jazyce C#
ms.date: 07/20/2015
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: 7615351f6e5f8b18bd6466a83d54aa65a6c99b50
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253037"
---
# <a name="scope-of-default-namespaces-in-c"></a><span data-ttu-id="ed1df-102">Rozsah výchozích oborů názvů v jazyce C\#</span><span class="sxs-lookup"><span data-stu-id="ed1df-102">Scope of Default Namespaces in C\#</span></span>
<span data-ttu-id="ed1df-103">Výchozí obory názvů jako reprezentované ve stromu XML nejsou v oboru pro dotazy.</span><span class="sxs-lookup"><span data-stu-id="ed1df-103">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="ed1df-104">Pokud máte XML, které je ve výchozím oboru názvů, je stále nutné deklarovat <xref:System.Xml.Linq.XNamespace> proměnnou a zkombinovat ji s místním názvem, aby bylo možné použít kvalifikovaný název v dotazu.</span><span class="sxs-lookup"><span data-stu-id="ed1df-104">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="ed1df-105">Jedním z nejběžnějších problémů při dotazování na stromy XML je, že pokud má strom XML výchozí obor názvů, vývojář někdy zapíše dotaz, jako by kód XML nebyl v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ed1df-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="ed1df-106">První sada příkladů v tomto tématu ukazuje typický způsob, jakým je načten XML ve výchozím oboru názvů, ale dotaz je nesprávně zadán.</span><span class="sxs-lookup"><span data-stu-id="ed1df-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="ed1df-107">Druhá sada příkladů ukazuje nezbytné opravy, aby bylo možné dotazovat XML v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ed1df-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed1df-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="ed1df-108">Example</span></span>  
 <span data-ttu-id="ed1df-109">Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který vrací prázdnou sadu výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="ed1df-109">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ed1df-110">Kód</span><span class="sxs-lookup"><span data-stu-id="ed1df-110">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="ed1df-111">Komentáře</span><span class="sxs-lookup"><span data-stu-id="ed1df-111">Comments</span></span>  
 <span data-ttu-id="ed1df-112">Tento příklad vytvoří následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="ed1df-112">This example produces the following result:</span></span>  
  
```output  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="ed1df-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="ed1df-113">Example</span></span>  
 <span data-ttu-id="ed1df-114">Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který je správně kódován.</span><span class="sxs-lookup"><span data-stu-id="ed1df-114">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="ed1df-115">Na rozdíl od nesprávně uvedeného kódovaného příkladu je správný přístup při použití příkazu C# pro deklaraci a inicializaci <xref:System.Xml.Linq.XNamespace> objektu a jeho použití při určení <xref:System.Xml.Linq.XName> objektů.</span><span class="sxs-lookup"><span data-stu-id="ed1df-115">In contrast to the incorrectly coded example above, the correct approach when using C# is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="ed1df-116">V tomto případě argument <xref:System.Xml.Linq.XContainer.Elements%2A> metody <xref:System.Xml.Linq.XName> je objekt.</span><span class="sxs-lookup"><span data-stu-id="ed1df-116">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ed1df-117">Kód</span><span class="sxs-lookup"><span data-stu-id="ed1df-117">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="ed1df-118">Komentáře</span><span class="sxs-lookup"><span data-stu-id="ed1df-118">Comments</span></span>  
 <span data-ttu-id="ed1df-119">Tento příklad vytvoří následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="ed1df-119">This example produces the following result:</span></span>  
  
```output  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="ed1df-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ed1df-120">See also</span></span>

- [<span data-ttu-id="ed1df-121">Přehled oborů názvů (LINQ to XML)C#()</span><span class="sxs-lookup"><span data-stu-id="ed1df-121">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
