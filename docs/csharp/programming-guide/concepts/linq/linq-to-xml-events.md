---
title: LinQ na xml události (C#)
ms.date: 07/20/2015
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
ms.openlocfilehash: 8e0cb4519dd0fc2bed443d9a62b9a2545d10e161
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253177"
---
# <a name="linq-to-xml-events-c"></a><span data-ttu-id="80c5a-102">LinQ na xml události (C#)</span><span class="sxs-lookup"><span data-stu-id="80c5a-102">LINQ to XML Events (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="80c5a-103">události umožňují upozornění při změně stromu XML.</span><span class="sxs-lookup"><span data-stu-id="80c5a-103">events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="80c5a-104">Události můžete přidat do instance <xref:System.Xml.Linq.XObject>libovolné aplikace .</span><span class="sxs-lookup"><span data-stu-id="80c5a-104">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="80c5a-105">Obslužná rutina události pak <xref:System.Xml.Linq.XObject> obdrží události pro změny, které a všechny jeho potomci.</span><span class="sxs-lookup"><span data-stu-id="80c5a-105">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="80c5a-106">Můžete například přidat obslužnou rutinu události do kořenového adresáře stromu a zpracovat všechny změny stromu z této obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="80c5a-106">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="80c5a-107">Příklady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] událostí naleznete <xref:System.Xml.Linq.XObject.Changing> v <xref:System.Xml.Linq.XObject.Changed>tématu a .</span><span class="sxs-lookup"><span data-stu-id="80c5a-107">For examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="80c5a-108">Typy a události</span><span class="sxs-lookup"><span data-stu-id="80c5a-108">Types and Events</span></span>  
 <span data-ttu-id="80c5a-109">Při práci s událostmi se používají následující typy:</span><span class="sxs-lookup"><span data-stu-id="80c5a-109">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="80c5a-110">Typ</span><span class="sxs-lookup"><span data-stu-id="80c5a-110">Type</span></span>|<span data-ttu-id="80c5a-111">Popis</span><span class="sxs-lookup"><span data-stu-id="80c5a-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|<span data-ttu-id="80c5a-112">Určuje typ události, když je událost <xref:System.Xml.Linq.XObject>vyvolána pro .</span><span class="sxs-lookup"><span data-stu-id="80c5a-112">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<span data-ttu-id="80c5a-113">Poskytuje data <xref:System.Xml.Linq.XObject.Changing> pro <xref:System.Xml.Linq.XObject.Changed> události a.</span><span class="sxs-lookup"><span data-stu-id="80c5a-113">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="80c5a-114">Při úpravě stromu XML jsou vyvolány následující události:</span><span class="sxs-lookup"><span data-stu-id="80c5a-114">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="80c5a-115">Událost</span><span class="sxs-lookup"><span data-stu-id="80c5a-115">Event</span></span>|<span data-ttu-id="80c5a-116">Popis</span><span class="sxs-lookup"><span data-stu-id="80c5a-116">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|<span data-ttu-id="80c5a-117">Vyskytuje se <xref:System.Xml.Linq.XObject> těsně před tím, než se toto nebo některý z jeho potomků změní.</span><span class="sxs-lookup"><span data-stu-id="80c5a-117">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<xref:System.Xml.Linq.XObject.Changed>|<span data-ttu-id="80c5a-118">Vyvolá se <xref:System.Xml.Linq.XObject> při změně nebo změně některého z jeho potomků.</span><span class="sxs-lookup"><span data-stu-id="80c5a-118">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="80c5a-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="80c5a-119">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="80c5a-120">Popis</span><span class="sxs-lookup"><span data-stu-id="80c5a-120">Description</span></span>  
 <span data-ttu-id="80c5a-121">Události jsou užitečné, pokud chcete zachovat některé souhrnné informace ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="80c5a-121">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="80c5a-122">Můžete například chtít udržovat součet faktury, který je součtem řádkových položek faktury.</span><span class="sxs-lookup"><span data-stu-id="80c5a-122">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="80c5a-123">Tento příklad používá události k udržení součtu všech podřízených prvků pod komplexníprvek `Items`.</span><span class="sxs-lookup"><span data-stu-id="80c5a-123">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="80c5a-124">kód</span><span class="sxs-lookup"><span data-stu-id="80c5a-124">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="80c5a-125">Komentáře</span><span class="sxs-lookup"><span data-stu-id="80c5a-125">Comments</span></span>  
 <span data-ttu-id="80c5a-126">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="80c5a-126">This code produces the following output:</span></span>  
  
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
  