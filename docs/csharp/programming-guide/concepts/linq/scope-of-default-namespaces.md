---
title: Obor výchozích názvových prostorů v jazyce C# 1
ms.date: 07/20/2015
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: d60f489f616a413e25bf5cd427bd467852a97c7b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379442"
---
# <a name="scope-of-default-namespaces-in-c"></a><span data-ttu-id="5fc36-102">Obor výchozích názvových prostorů v jazyce C\#</span><span class="sxs-lookup"><span data-stu-id="5fc36-102">Scope of Default Namespaces in C\#</span></span>
<span data-ttu-id="5fc36-103">Výchozí obory názvů, jak je ve stromové struktuře XML nejsou v oboru pro dotazy.</span><span class="sxs-lookup"><span data-stu-id="5fc36-103">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="5fc36-104">Pokud budete mít soubor XML, který je ve výchozím oboru názvů, je stále třeba deklarovat <xref:System.Xml.Linq.XNamespace> proměnnou a sloučit s místním názvem vytvořit kvalifikovaný název, který se má použít v dotazu.</span><span class="sxs-lookup"><span data-stu-id="5fc36-104">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="5fc36-105">Jedním z nejběžnějších problémů při dotazování na stromy XML je, že pokud stromu XML má výchozí obor názvů, vývojář někdy zapíše dotaz jakoby nebyly v oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="5fc36-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="5fc36-106">První sada příklady v tomto tématu ukazuje obvyklým způsobem, že je načteno XML ve výchozím oboru názvů, ale je dotazován nesprávně.</span><span class="sxs-lookup"><span data-stu-id="5fc36-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="5fc36-107">Druhá sada příklady ukazují potřebné opravy tak, aby můžete dát dotaz na XML v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5fc36-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fc36-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="5fc36-108">Example</span></span>  
 <span data-ttu-id="5fc36-109">Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který vrací prázdný výsledek sadu.</span><span class="sxs-lookup"><span data-stu-id="5fc36-109">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5fc36-110">Kód</span><span class="sxs-lookup"><span data-stu-id="5fc36-110">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="5fc36-111">Komentáře</span><span class="sxs-lookup"><span data-stu-id="5fc36-111">Comments</span></span>  
 <span data-ttu-id="5fc36-112">Tento příklad vytvoří následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="5fc36-112">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="5fc36-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="5fc36-113">Example</span></span>  
 <span data-ttu-id="5fc36-114">Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který je zakódovaný správně.</span><span class="sxs-lookup"><span data-stu-id="5fc36-114">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="5fc36-115">Na rozdíl od nesprávně programové výše uvedeném příkladu je správný přístup při použití jazyka C# k deklaraci a inicializaci <xref:System.Xml.Linq.XNamespace> objektu a použít je při zadávání <xref:System.Xml.Linq.XName> objekty.</span><span class="sxs-lookup"><span data-stu-id="5fc36-115">In contrast to the incorrectly coded example above, the correct approach when using C# is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="5fc36-116">V tomto případě, že argument <xref:System.Xml.Linq.XContainer.Elements%2A> metoda je <xref:System.Xml.Linq.XName> objektu.</span><span class="sxs-lookup"><span data-stu-id="5fc36-116">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5fc36-117">Kód</span><span class="sxs-lookup"><span data-stu-id="5fc36-117">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="5fc36-118">Komentáře</span><span class="sxs-lookup"><span data-stu-id="5fc36-118">Comments</span></span>  
 <span data-ttu-id="5fc36-119">Tento příklad vytvoří následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="5fc36-119">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="5fc36-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5fc36-120">See also</span></span>

- [<span data-ttu-id="5fc36-121">Práce s názvovými prostory XML (C#)</span><span class="sxs-lookup"><span data-stu-id="5fc36-121">Working with XML Namespaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
