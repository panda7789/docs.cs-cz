---
title: Rozsah výchozí obory názvů v jazyce C# 1
ms.date: 07/20/2015
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: 37b10c43071d4f6a9fb2a25d68ab2c100c27dde9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33330093"
---
# <a name="scope-of-default-namespaces-in-c"></a><span data-ttu-id="f02bf-102">Rozsah výchozí obory názvů v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f02bf-102">Scope of Default Namespaces in C#</span></span>
<span data-ttu-id="f02bf-103">Výchozí obory názvů, jak je přestavováno ve stromové struktuře XML nejsou v oboru pro dotazy.</span><span class="sxs-lookup"><span data-stu-id="f02bf-103">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="f02bf-104">Pokud máte XML, který je ve výchozí obor názvů, je stále potřeba deklarovat <xref:System.Xml.Linq.XNamespace> proměnnou a zkombinovat s místní název, aby kvalifikovaný název, který se má použít v dotazu.</span><span class="sxs-lookup"><span data-stu-id="f02bf-104">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="f02bf-105">Jeden z nejběžnějších problémů při dotazování stromy XML je, že pokud stromu XML má výchozí obor názvů, vývojář někdy zapíše dotazu, jako by soubor XML není v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f02bf-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="f02bf-106">První sadu příklady v tomto tématu ukazuje obvyklý způsob, že je načteno kód XML v výchozí obor názvů, ale je dotazován nesprávně.</span><span class="sxs-lookup"><span data-stu-id="f02bf-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="f02bf-107">Druhá sada příklady zobrazit potřebné opravy tak, aby v oboru názvů se můžete dotazovat XML.</span><span class="sxs-lookup"><span data-stu-id="f02bf-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f02bf-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="f02bf-108">Example</span></span>  
 <span data-ttu-id="f02bf-109">Tento příklad ukazuje vytvoření XML v oboru názvů a nastavte dotaz, který vrací prázdný výsledek.</span><span class="sxs-lookup"><span data-stu-id="f02bf-109">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f02bf-110">Kód</span><span class="sxs-lookup"><span data-stu-id="f02bf-110">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="f02bf-111">Komentáře</span><span class="sxs-lookup"><span data-stu-id="f02bf-111">Comments</span></span>  
 <span data-ttu-id="f02bf-112">Tento příklad vytvoří následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="f02bf-112">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="f02bf-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="f02bf-113">Example</span></span>  
 <span data-ttu-id="f02bf-114">Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který je zakódovaný správně.</span><span class="sxs-lookup"><span data-stu-id="f02bf-114">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="f02bf-115">Na rozdíl od nesprávně programové výše uvedeném příkladu správný přístup při použití jazyka C# je deklarovat a inicializovat <xref:System.Xml.Linq.XNamespace> objekt a který můžete použít při zadávání <xref:System.Xml.Linq.XName> objekty.</span><span class="sxs-lookup"><span data-stu-id="f02bf-115">In contrast to the incorrectly coded example above, the correct approach when using C# is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="f02bf-116">V tomto případě argument <xref:System.Xml.Linq.XElement.Elements%2A> je metoda <xref:System.Xml.Linq.XName> objektu.</span><span class="sxs-lookup"><span data-stu-id="f02bf-116">In this case, the argument to the <xref:System.Xml.Linq.XElement.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f02bf-117">Kód</span><span class="sxs-lookup"><span data-stu-id="f02bf-117">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="f02bf-118">Komentáře</span><span class="sxs-lookup"><span data-stu-id="f02bf-118">Comments</span></span>  
 <span data-ttu-id="f02bf-119">Tento příklad vytvoří následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="f02bf-119">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="f02bf-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="f02bf-120">See Also</span></span>  
 [<span data-ttu-id="f02bf-121">Práce s obory názvů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="f02bf-121">Working with XML Namespaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
