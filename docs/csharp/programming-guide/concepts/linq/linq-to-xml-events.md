---
title: Události LINQ to XML (C#)
ms.date: 07/20/2015
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
ms.openlocfilehash: 6308d81eac830e11b6d58f8e460dfa377663cd21
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46008727"
---
# <a name="linq-to-xml-events-c"></a><span data-ttu-id="741da-102">Události LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="741da-102">LINQ to XML Events (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="741da-103"> události umožňují upozorněni, když je změněna stromu XML.</span><span class="sxs-lookup"><span data-stu-id="741da-103"> events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="741da-104">Události můžete přidat do instance libovolného <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="741da-104">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="741da-105">Obslužná rutina události se pak zobrazí události pro změny, které <xref:System.Xml.Linq.XObject> a všech jejích potomků.</span><span class="sxs-lookup"><span data-stu-id="741da-105">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="741da-106">Můžete například přidat obslužnou rutinu události pro kořen stromu a zpracovat všechny změny do stromové struktury z této obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="741da-106">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="741da-107">Příklady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] události, viz <xref:System.Xml.Linq.XObject.Changing> a <xref:System.Xml.Linq.XObject.Changed>.</span><span class="sxs-lookup"><span data-stu-id="741da-107">For examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="741da-108">Typy a události</span><span class="sxs-lookup"><span data-stu-id="741da-108">Types and Events</span></span>  
 <span data-ttu-id="741da-109">Při práci s událostmi se používají následující typy:</span><span class="sxs-lookup"><span data-stu-id="741da-109">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="741da-110">Typ</span><span class="sxs-lookup"><span data-stu-id="741da-110">Type</span></span>|<span data-ttu-id="741da-111">Popis</span><span class="sxs-lookup"><span data-stu-id="741da-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|<span data-ttu-id="741da-112">Určuje typ události, když událost se vyvolá pro <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="741da-112">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<span data-ttu-id="741da-113">Poskytuje data pro <xref:System.Xml.Linq.XObject.Changing> a <xref:System.Xml.Linq.XObject.Changed> události.</span><span class="sxs-lookup"><span data-stu-id="741da-113">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="741da-114">Při úpravě stromu XML jsou vyvolány následující události:</span><span class="sxs-lookup"><span data-stu-id="741da-114">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="741da-115">Událost</span><span class="sxs-lookup"><span data-stu-id="741da-115">Event</span></span>|<span data-ttu-id="741da-116">Popis</span><span class="sxs-lookup"><span data-stu-id="741da-116">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|<span data-ttu-id="741da-117">Nastane bezprostředně před <xref:System.Xml.Linq.XObject> nebo libovolného z jeho potomků se to změnit.</span><span class="sxs-lookup"><span data-stu-id="741da-117">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<xref:System.Xml.Linq.XObject.Changed>|<span data-ttu-id="741da-118">Vyvolá se při <xref:System.Xml.Linq.XObject> došlo ke změně nebo libovolného z jeho potomků změnily.</span><span class="sxs-lookup"><span data-stu-id="741da-118">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="741da-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="741da-119">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="741da-120">Popis</span><span class="sxs-lookup"><span data-stu-id="741da-120">Description</span></span>  
 <span data-ttu-id="741da-121">Události jsou užitečné, pokud chcete zachovat některé agregované informace ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="741da-121">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="741da-122">Například můžete udržovat celkovou fakturu, který je součtem řádku položek faktury.</span><span class="sxs-lookup"><span data-stu-id="741da-122">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="741da-123">Tento příklad používá události k údržbě celkový součet všech podřízených elementů v rámci komplexních prvků `Items`.</span><span class="sxs-lookup"><span data-stu-id="741da-123">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="741da-124">Kód</span><span class="sxs-lookup"><span data-stu-id="741da-124">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="741da-125">Komentáře</span><span class="sxs-lookup"><span data-stu-id="741da-125">Comments</span></span>  
 <span data-ttu-id="741da-126">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="741da-126">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="741da-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="741da-127">See Also</span></span>

- [<span data-ttu-id="741da-128">Pokročilé technologie LINQ to XML programování (C#)</span><span class="sxs-lookup"><span data-stu-id="741da-128">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
