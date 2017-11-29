---
title: "Technologie LINQ to XML události (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34923928-b99c-4004-956e-38f6db25e910
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b19d8f19f9feb1d385f9900d76d2a7af8e89bbeb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-xml-events-visual-basic"></a><span data-ttu-id="43d75-102">Technologie LINQ to XML události (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43d75-102">LINQ to XML Events (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="43d75-103">události umožňují být upozorněni, když je změnit strom XML.</span><span class="sxs-lookup"><span data-stu-id="43d75-103"> events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="43d75-104">Události můžete přidat do instance libovolného <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="43d75-104">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="43d75-105">Obslužné rutiny události bude potom přijímat události pro změny, <xref:System.Xml.Linq.XObject> a všechny jeho podřízené položky.</span><span class="sxs-lookup"><span data-stu-id="43d75-105">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="43d75-106">Můžete například přidat obslužné rutiny události ke kořenu stromu a zpracovat všechny změny do stromu z této obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="43d75-106">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="43d75-107">Příklady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] události, viz <xref:System.Xml.Linq.XObject.Changing> a <xref:System.Xml.Linq.XObject.Changed>.</span><span class="sxs-lookup"><span data-stu-id="43d75-107">For examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="43d75-108">Typy a události</span><span class="sxs-lookup"><span data-stu-id="43d75-108">Types and Events</span></span>  
 <span data-ttu-id="43d75-109">Při práci s událostmi se používají následující typy:</span><span class="sxs-lookup"><span data-stu-id="43d75-109">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="43d75-110">Typ</span><span class="sxs-lookup"><span data-stu-id="43d75-110">Type</span></span>|<span data-ttu-id="43d75-111">Popis</span><span class="sxs-lookup"><span data-stu-id="43d75-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|<span data-ttu-id="43d75-112">Určuje typ události, když událost se vyvolá pro <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="43d75-112">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<span data-ttu-id="43d75-113">Poskytuje data pro <xref:System.Xml.Linq.XObject.Changing> a <xref:System.Xml.Linq.XObject.Changed> události.</span><span class="sxs-lookup"><span data-stu-id="43d75-113">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="43d75-114">Při úpravě strom XML, jsou vyvolány následující události:</span><span class="sxs-lookup"><span data-stu-id="43d75-114">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="43d75-115">Událost</span><span class="sxs-lookup"><span data-stu-id="43d75-115">Event</span></span>|<span data-ttu-id="43d75-116">Popis</span><span class="sxs-lookup"><span data-stu-id="43d75-116">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|<span data-ttu-id="43d75-117">Dojde k těsně před <xref:System.Xml.Linq.XObject> nebo některý z jeho následníky se chystáte změnit.</span><span class="sxs-lookup"><span data-stu-id="43d75-117">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<xref:System.Xml.Linq.XObject.Changed>|<span data-ttu-id="43d75-118">Nastane při <xref:System.Xml.Linq.XObject> došlo ke změně nebo některé z jejich potomků změnily.</span><span class="sxs-lookup"><span data-stu-id="43d75-118">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="43d75-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="43d75-119">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="43d75-120">Popis</span><span class="sxs-lookup"><span data-stu-id="43d75-120">Description</span></span>  
 <span data-ttu-id="43d75-121">Události jsou užitečné, pokud chcete zachovat některé agregační informace ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="43d75-121">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="43d75-122">Například můžete udržovat celkovou fakturu představuje součet položek řádku faktury.</span><span class="sxs-lookup"><span data-stu-id="43d75-122">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="43d75-123">Tento příklad používá událostí udržovat celkový počet všech podřízených elementů v části komplexních prvků `Items`.</span><span class="sxs-lookup"><span data-stu-id="43d75-123">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="43d75-124">Kód</span><span class="sxs-lookup"><span data-stu-id="43d75-124">Code</span></span>  
  
```vb  
Module Module1  
    Dim WithEvents items As XElement = Nothing  
    Dim total As XElement = Nothing  
    Dim root As XElement = _  
            <Root>  
                <Total>0</Total>  
                <Items></Items>  
            </Root>  
  
    Private Sub XObjectChanged( _  
            ByVal sender As Object, _  
            ByVal cea As XObjectChangeEventArgs) _  
            Handles items.Changed  
        Select Case cea.ObjectChange  
            Case XObjectChange.Add  
                If sender.GetType() Is GetType(XElement) Then  
                    total.Value = CStr(CInt(total.Value) + _  
                            CInt((DirectCast(sender, XElement)).Value))  
                End If  
                If sender.GetType() Is GetType(XText) Then  
                    total.Value = CStr(CInt(total.Value) + _  
                            CInt((DirectCast(sender, XText)).Value))  
                End If  
            Case XObjectChange.Remove  
                If sender.GetType() Is GetType(XElement) Then  
                    total.Value = CStr(CInt(total.Value) - _  
                            CInt((DirectCast(sender, XElement)).Value))  
                End If  
                If sender.GetType() Is GetType(XText) Then  
                    total.Value = CStr(CInt(total.Value) - _  
                            CInt((DirectCast(sender, XText)).Value))  
                End If  
        End Select  
        Console.WriteLine("Changed {0} {1}", _  
                            sender.GetType().ToString(), _  
                            cea.ObjectChange.ToString())  
    End Sub  
  
    Sub Main()  
        total = root.<Total>(0)  
        items = root.<Items>(0)  
        items.SetElementValue("Item1", 25)  
        items.SetElementValue("Item2", 50)  
        items.SetElementValue("Item2", 75)  
        items.SetElementValue("Item3", 133)  
        items.SetElementValue("Item1", Nothing)  
        items.SetElementValue("Item4", 100)  
        Console.WriteLine("Total:{0}", CInt(total))  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
### <a name="comments"></a><span data-ttu-id="43d75-125">Komentáře</span><span class="sxs-lookup"><span data-stu-id="43d75-125">Comments</span></span>  
 <span data-ttu-id="43d75-126">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="43d75-126">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43d75-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="43d75-127">See Also</span></span>  
 [<span data-ttu-id="43d75-128">Pokročilé technologie LINQ to XML programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43d75-128">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
