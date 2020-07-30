---
title: Události LINQ to XML (C#)
description: Přidejte LINQ to XML události v C# do instance libovolné XObject. Obslužná rutina události přijímá události při změně stromu XML pro tento XObject.
ms.date: 07/20/2015
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
ms.openlocfilehash: 576b0a5d0472bddd66e01d3bef8f3affa1c9458b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165423"
---
# <a name="linq-to-xml-events-c"></a><span data-ttu-id="96ffc-104">Události LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="96ffc-104">LINQ to XML Events (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="96ffc-105">události umožňují být upozorňovány při změně stromu XML.</span><span class="sxs-lookup"><span data-stu-id="96ffc-105">events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="96ffc-106">Události můžete přidat do instance libovolné <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="96ffc-106">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="96ffc-107">Obslužná rutina události poté obdrží události pro úpravy tohoto <xref:System.Xml.Linq.XObject> a kteréhokoli z jeho potomků.</span><span class="sxs-lookup"><span data-stu-id="96ffc-107">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="96ffc-108">Například můžete přidat obslužnou rutinu události do kořenového adresáře stromu a zpracovat všechny změny stromu z této obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="96ffc-108">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="96ffc-109">Příklady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] událostí naleznete v tématech <xref:System.Xml.Linq.XObject.Changing> a <xref:System.Xml.Linq.XObject.Changed> .</span><span class="sxs-lookup"><span data-stu-id="96ffc-109">For examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="96ffc-110">Typy a události</span><span class="sxs-lookup"><span data-stu-id="96ffc-110">Types and Events</span></span>  
 <span data-ttu-id="96ffc-111">Při práci s událostmi můžete použít následující typy:</span><span class="sxs-lookup"><span data-stu-id="96ffc-111">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="96ffc-112">Typ</span><span class="sxs-lookup"><span data-stu-id="96ffc-112">Type</span></span>|<span data-ttu-id="96ffc-113">Popis</span><span class="sxs-lookup"><span data-stu-id="96ffc-113">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|<span data-ttu-id="96ffc-114">Určuje typ události při vyvolání události pro <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="96ffc-114">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<span data-ttu-id="96ffc-115">Poskytuje data pro <xref:System.Xml.Linq.XObject.Changing> události a <xref:System.Xml.Linq.XObject.Changed> .</span><span class="sxs-lookup"><span data-stu-id="96ffc-115">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="96ffc-116">Při úpravě stromu XML jsou vyvolány následující události:</span><span class="sxs-lookup"><span data-stu-id="96ffc-116">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="96ffc-117">Událost</span><span class="sxs-lookup"><span data-stu-id="96ffc-117">Event</span></span>|<span data-ttu-id="96ffc-118">Popis</span><span class="sxs-lookup"><span data-stu-id="96ffc-118">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|<span data-ttu-id="96ffc-119">Nastane těsně před tím, než <xref:System.Xml.Linq.XObject> se tato nebo kterákoli z jeho potomků změní.</span><span class="sxs-lookup"><span data-stu-id="96ffc-119">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<xref:System.Xml.Linq.XObject.Changed>|<span data-ttu-id="96ffc-120">Vyvolá se v případě, že došlo ke změně <xref:System.Xml.Linq.XObject> nebo některému z jeho potomků.</span><span class="sxs-lookup"><span data-stu-id="96ffc-120">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="96ffc-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="96ffc-121">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="96ffc-122">Popis</span><span class="sxs-lookup"><span data-stu-id="96ffc-122">Description</span></span>  
 <span data-ttu-id="96ffc-123">Události jsou užitečné, pokud chcete zachovat některé agregované informace ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="96ffc-123">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="96ffc-124">Například můžete chtít zachovat celkovou částku faktury, která je součtem položek řádků faktury.</span><span class="sxs-lookup"><span data-stu-id="96ffc-124">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="96ffc-125">V tomto příkladu se používají události pro udržování celkového počtu všech podřízených elementů v rámci komplexního prvku `Items` .</span><span class="sxs-lookup"><span data-stu-id="96ffc-125">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="96ffc-126">Kód</span><span class="sxs-lookup"><span data-stu-id="96ffc-126">Code</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Total", "0"),  
    new XElement("Items")  
);  
XElement total = root.Element("Total");  
XElement items = root.Element("Items");  
items.Changed += (object sender, XObjectChangeEventArgs cea) =>  
{  
    switch (cea.ObjectChange)  
    {  
        case XObjectChange.Add:  
            if (sender is XElement)  
                total.Value = ((int)total + (int)(XElement)sender).ToString();  
            if (sender is XText)  
                total.Value = ((int)total + (int)((XText)sender).Parent).ToString();  
            break;  
        case XObjectChange.Remove:  
            if (sender is XElement)  
                total.Value = ((int)total - (int)(XElement)sender).ToString();  
            if (sender is XText)  
                total.Value = ((int)total - Int32.Parse(((XText)sender).Value)).ToString();  
            break;  
    }  
    Console.WriteLine("Changed {0} {1}",  
      sender.GetType().ToString(), cea.ObjectChange.ToString());  
};  
items.SetElementValue("Item1", 25);  
items.SetElementValue("Item2", 50);  
items.SetElementValue("Item2", 75);  
items.SetElementValue("Item3", 133);  
items.SetElementValue("Item1", null);  
items.SetElementValue("Item4", 100);  
Console.WriteLine("Total:{0}", (int)total);  
Console.WriteLine(root);  
```  
  
### <a name="comments"></a><span data-ttu-id="96ffc-127">Komentáře</span><span class="sxs-lookup"><span data-stu-id="96ffc-127">Comments</span></span>  
 <span data-ttu-id="96ffc-128">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="96ffc-128">This code produces the following output:</span></span>  
  
```output  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XText Remove  
Changed System.Xml.Linq.XText Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Remove  
Changed System.Xml.Linq.XElement Add  
Total:308  
<Root>  
  <Total>308</Total>  
  <Items>  
    <Item2>75</Item2>  
    <Item3>133</Item3>  
    <Item4>100</Item4>  
  </Items>  
</Root>  
```  
  