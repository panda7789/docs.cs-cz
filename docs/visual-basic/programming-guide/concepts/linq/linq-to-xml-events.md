---
title: Události LINQ to XML
ms.date: 07/20/2015
ms.assetid: 34923928-b99c-4004-956e-38f6db25e910
ms.openlocfilehash: d00f6f1b2a14ac73c1bcd4a1f74b9714ca304da3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368813"
---
# <a name="linq-to-xml-events-visual-basic"></a><span data-ttu-id="82811-102">Události LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82811-102">LINQ to XML Events (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="82811-103">události umožňují být upozorňovány při změně stromu XML.</span><span class="sxs-lookup"><span data-stu-id="82811-103">events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="82811-104">Události můžete přidat do instance libovolné <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="82811-104">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="82811-105">Obslužná rutina události poté obdrží události pro úpravy tohoto <xref:System.Xml.Linq.XObject> a kteréhokoli z jeho potomků.</span><span class="sxs-lookup"><span data-stu-id="82811-105">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="82811-106">Například můžete přidat obslužnou rutinu události do kořenového adresáře stromu a zpracovat všechny změny stromu z této obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="82811-106">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="82811-107">Příklady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] událostí naleznete v tématech <xref:System.Xml.Linq.XObject.Changing> a <xref:System.Xml.Linq.XObject.Changed> .</span><span class="sxs-lookup"><span data-stu-id="82811-107">For examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="82811-108">Typy a události</span><span class="sxs-lookup"><span data-stu-id="82811-108">Types and Events</span></span>  
 <span data-ttu-id="82811-109">Při práci s událostmi můžete použít následující typy:</span><span class="sxs-lookup"><span data-stu-id="82811-109">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="82811-110">Typ</span><span class="sxs-lookup"><span data-stu-id="82811-110">Type</span></span>|<span data-ttu-id="82811-111">Description</span><span class="sxs-lookup"><span data-stu-id="82811-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|<span data-ttu-id="82811-112">Určuje typ události při vyvolání události pro <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="82811-112">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<span data-ttu-id="82811-113">Poskytuje data pro <xref:System.Xml.Linq.XObject.Changing> události a <xref:System.Xml.Linq.XObject.Changed> .</span><span class="sxs-lookup"><span data-stu-id="82811-113">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="82811-114">Při úpravě stromu XML jsou vyvolány následující události:</span><span class="sxs-lookup"><span data-stu-id="82811-114">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="82811-115">Událost</span><span class="sxs-lookup"><span data-stu-id="82811-115">Event</span></span>|<span data-ttu-id="82811-116">Description</span><span class="sxs-lookup"><span data-stu-id="82811-116">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|<span data-ttu-id="82811-117">Nastane těsně před tím, než <xref:System.Xml.Linq.XObject> se tato nebo kterákoli z jeho potomků změní.</span><span class="sxs-lookup"><span data-stu-id="82811-117">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<xref:System.Xml.Linq.XObject.Changed>|<span data-ttu-id="82811-118">Vyvolá se v případě, že došlo ke změně <xref:System.Xml.Linq.XObject> nebo některému z jeho potomků.</span><span class="sxs-lookup"><span data-stu-id="82811-118">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="82811-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="82811-119">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="82811-120">Description</span><span class="sxs-lookup"><span data-stu-id="82811-120">Description</span></span>  
 <span data-ttu-id="82811-121">Události jsou užitečné, pokud chcete zachovat některé agregované informace ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="82811-121">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="82811-122">Například můžete chtít zachovat celkovou částku faktury, která je součtem položek řádků faktury.</span><span class="sxs-lookup"><span data-stu-id="82811-122">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="82811-123">V tomto příkladu se používají události pro udržování celkového počtu všech podřízených elementů v rámci komplexního prvku `Items` .</span><span class="sxs-lookup"><span data-stu-id="82811-123">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="82811-124">Kód</span><span class="sxs-lookup"><span data-stu-id="82811-124">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="82811-125">Komentáře</span><span class="sxs-lookup"><span data-stu-id="82811-125">Comments</span></span>  
 <span data-ttu-id="82811-126">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="82811-126">This code produces the following output:</span></span>  
  
```console  
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
  
## <a name="see-also"></a><span data-ttu-id="82811-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="82811-127">See also</span></span>

- [<span data-ttu-id="82811-128">Rozšířené programování LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82811-128">Advanced LINQ to XML Programming (Visual Basic)</span></span>](advanced-linq-to-xml-programming.md)
