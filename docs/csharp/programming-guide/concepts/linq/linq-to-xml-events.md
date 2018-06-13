---
title: Technologie LINQ to XML událostí (C#)
ms.date: 07/20/2015
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
ms.openlocfilehash: 3dd4eaa0261ae7d878e188572d260b34b64fc031
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322390"
---
# <a name="linq-to-xml-events-c"></a><span data-ttu-id="61b1f-102">Technologie LINQ to XML událostí (C#)</span><span class="sxs-lookup"><span data-stu-id="61b1f-102">LINQ to XML Events (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="61b1f-103"> události umožňují být upozorněni, když je změnit strom XML.</span><span class="sxs-lookup"><span data-stu-id="61b1f-103"> events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="61b1f-104">Události můžete přidat do instance libovolného <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="61b1f-104">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="61b1f-105">Obslužné rutiny události bude potom přijímat události pro změny, <xref:System.Xml.Linq.XObject> a všechny jeho podřízené položky.</span><span class="sxs-lookup"><span data-stu-id="61b1f-105">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="61b1f-106">Můžete například přidat obslužné rutiny události ke kořenu stromu a zpracovat všechny změny do stromu z této obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="61b1f-106">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="61b1f-107">Příklady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] události, viz <xref:System.Xml.Linq.XObject.Changing> a <xref:System.Xml.Linq.XObject.Changed>.</span><span class="sxs-lookup"><span data-stu-id="61b1f-107">For examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="61b1f-108">Typy a události</span><span class="sxs-lookup"><span data-stu-id="61b1f-108">Types and Events</span></span>  
 <span data-ttu-id="61b1f-109">Při práci s událostmi se používají následující typy:</span><span class="sxs-lookup"><span data-stu-id="61b1f-109">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="61b1f-110">Typ</span><span class="sxs-lookup"><span data-stu-id="61b1f-110">Type</span></span>|<span data-ttu-id="61b1f-111">Popis</span><span class="sxs-lookup"><span data-stu-id="61b1f-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|<span data-ttu-id="61b1f-112">Určuje typ události, když událost se vyvolá pro <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="61b1f-112">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<span data-ttu-id="61b1f-113">Poskytuje data pro <xref:System.Xml.Linq.XObject.Changing> a <xref:System.Xml.Linq.XObject.Changed> události.</span><span class="sxs-lookup"><span data-stu-id="61b1f-113">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="61b1f-114">Při úpravě strom XML, jsou vyvolány následující události:</span><span class="sxs-lookup"><span data-stu-id="61b1f-114">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="61b1f-115">Událost</span><span class="sxs-lookup"><span data-stu-id="61b1f-115">Event</span></span>|<span data-ttu-id="61b1f-116">Popis</span><span class="sxs-lookup"><span data-stu-id="61b1f-116">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|<span data-ttu-id="61b1f-117">Dojde k těsně před <xref:System.Xml.Linq.XObject> nebo některý z jeho následníky se chystáte změnit.</span><span class="sxs-lookup"><span data-stu-id="61b1f-117">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<xref:System.Xml.Linq.XObject.Changed>|<span data-ttu-id="61b1f-118">Nastane při <xref:System.Xml.Linq.XObject> došlo ke změně nebo některé z jejich potomků změnily.</span><span class="sxs-lookup"><span data-stu-id="61b1f-118">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="61b1f-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="61b1f-119">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="61b1f-120">Popis</span><span class="sxs-lookup"><span data-stu-id="61b1f-120">Description</span></span>  
 <span data-ttu-id="61b1f-121">Události jsou užitečné, pokud chcete zachovat některé agregační informace ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="61b1f-121">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="61b1f-122">Například můžete udržovat celkovou fakturu představuje součet položek řádku faktury.</span><span class="sxs-lookup"><span data-stu-id="61b1f-122">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="61b1f-123">Tento příklad používá událostí udržovat celkový počet všech podřízených elementů v části komplexních prvků `Items`.</span><span class="sxs-lookup"><span data-stu-id="61b1f-123">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="61b1f-124">Kód</span><span class="sxs-lookup"><span data-stu-id="61b1f-124">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="61b1f-125">Komentáře</span><span class="sxs-lookup"><span data-stu-id="61b1f-125">Comments</span></span>  
 <span data-ttu-id="61b1f-126">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="61b1f-126">This code produces the following output:</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="61b1f-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="61b1f-127">See Also</span></span>  
 [<span data-ttu-id="61b1f-128">Pokročilé technologie LINQ to XML programování (C#)</span><span class="sxs-lookup"><span data-stu-id="61b1f-128">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
