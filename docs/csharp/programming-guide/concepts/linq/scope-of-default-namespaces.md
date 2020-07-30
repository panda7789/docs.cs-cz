---
title: Obor výchozích názvových prostorů v jazyce C#
description: Přečtěte si, jak dotazovat ve výchozích oborech názvů XML v LINQ to XML v jazyce C#. K vytvoření kvalifikovaného názvu pro dotaz použijte proměnnou XNamespace a místní název.
ms.date: 07/20/2015
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: 912e47099f89daa9b80ac58b422d39d598509ac9
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302396"
---
# <a name="scope-of-default-namespaces-in-c"></a><span data-ttu-id="94301-104">Rozsah výchozích oborů názvů v jazyce C\#</span><span class="sxs-lookup"><span data-stu-id="94301-104">Scope of Default Namespaces in C\#</span></span>
<span data-ttu-id="94301-105">Výchozí obory názvů jako reprezentované ve stromu XML nejsou v oboru pro dotazy.</span><span class="sxs-lookup"><span data-stu-id="94301-105">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="94301-106">Pokud máte XML, které je ve výchozím oboru názvů, je stále nutné deklarovat <xref:System.Xml.Linq.XNamespace> proměnnou a zkombinovat ji s místním názvem, aby bylo možné použít kvalifikovaný název v dotazu.</span><span class="sxs-lookup"><span data-stu-id="94301-106">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="94301-107">Jedním z nejběžnějších problémů při dotazování na stromy XML je, že pokud má strom XML výchozí obor názvů, vývojář někdy zapíše dotaz, jako by kód XML nebyl v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="94301-107">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="94301-108">První sada příkladů v tomto tématu ukazuje typický způsob, jakým je načten XML ve výchozím oboru názvů, ale dotaz je nesprávně zadán.</span><span class="sxs-lookup"><span data-stu-id="94301-108">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="94301-109">Druhá sada příkladů ukazuje nezbytné opravy, aby bylo možné dotazovat XML v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="94301-109">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94301-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="94301-110">Example</span></span>  
 <span data-ttu-id="94301-111">Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který vrací prázdnou sadu výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="94301-111">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="94301-112">Kód</span><span class="sxs-lookup"><span data-stu-id="94301-112">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="94301-113">Komentáře</span><span class="sxs-lookup"><span data-stu-id="94301-113">Comments</span></span>  
 <span data-ttu-id="94301-114">Tento příklad vytvoří následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="94301-114">This example produces the following result:</span></span>  
  
```output  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="94301-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="94301-115">Example</span></span>  
 <span data-ttu-id="94301-116">Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který je správně kódován.</span><span class="sxs-lookup"><span data-stu-id="94301-116">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="94301-117">Na rozdíl od nesprávně uvedeného kódovaného příkladu je správný přístup při použití jazyka C# k deklaraci a inicializaci <xref:System.Xml.Linq.XNamespace> objektu a jeho použití při určení <xref:System.Xml.Linq.XName> objektů.</span><span class="sxs-lookup"><span data-stu-id="94301-117">In contrast to the incorrectly coded example above, the correct approach when using C# is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="94301-118">V tomto případě argument <xref:System.Xml.Linq.XContainer.Elements%2A> metody je <xref:System.Xml.Linq.XName> objekt.</span><span class="sxs-lookup"><span data-stu-id="94301-118">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
### <a name="code"></a><span data-ttu-id="94301-119">Kód</span><span class="sxs-lookup"><span data-stu-id="94301-119">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="94301-120">Komentáře</span><span class="sxs-lookup"><span data-stu-id="94301-120">Comments</span></span>  
 <span data-ttu-id="94301-121">Tento příklad vytvoří následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="94301-121">This example produces the following result:</span></span>  
  
```output  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="94301-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94301-122">See also</span></span>

- [<span data-ttu-id="94301-123">Přehled oborů názvů (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="94301-123">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
