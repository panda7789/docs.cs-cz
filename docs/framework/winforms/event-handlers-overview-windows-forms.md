---
title: Přehled obslužných rutin událostí
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handling [Windows Forms], Windows Forms
- event handlers [Windows Forms], about event handlers
ms.assetid: 228112e1-1711-42ee-8ffa-ff3555bffe66
ms.openlocfilehash: 10ba458197973ede35849a86fec35003f139b8d2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743493"
---
# <a name="event-handlers-overview-windows-forms"></a><span data-ttu-id="97055-102">Přehled obslužných rutin událostí (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="97055-102">Event Handlers Overview (Windows Forms)</span></span>
<span data-ttu-id="97055-103">Obslužná rutina události je metoda, která je svázána s událostí.</span><span class="sxs-lookup"><span data-stu-id="97055-103">An event handler is a method that is bound to an event.</span></span> <span data-ttu-id="97055-104">Při vyvolání události je proveden kód v rámci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="97055-104">When the event is raised, the code within the event handler is executed.</span></span> <span data-ttu-id="97055-105">Každá obslužná rutina události poskytuje dva parametry, které umožňují správné zpracování události.</span><span class="sxs-lookup"><span data-stu-id="97055-105">Each event handler provides two parameters that allow you to handle the event properly.</span></span> <span data-ttu-id="97055-106">Následující příklad ukazuje obslužnou rutinu události pro událost <xref:System.Windows.Forms.Control.Click> ovládacího prvku <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="97055-106">The following example shows an event handler for a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
```vb  
Private Sub button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles button1.Click  
  
End Sub  
```  
  
```csharp  
private void button1_Click(object sender, System.EventArgs e)   
{  
  
}  
```  
  
```cpp  
private:  
  void button1_Click(System::Object ^ sender,  
    System::EventArgs ^ e)  
  {  
  
  }  
```  
  
 <span data-ttu-id="97055-107">První parametr,`sender`, poskytuje odkaz na objekt, který vyvolal událost.</span><span class="sxs-lookup"><span data-stu-id="97055-107">The first parameter,`sender`, provides a reference to the object that raised the event.</span></span> <span data-ttu-id="97055-108">Druhý parametr `e`, v příkladu výše, předává objekt specifický pro událost, která je zpracovávána.</span><span class="sxs-lookup"><span data-stu-id="97055-108">The second parameter, `e`, in the example above, passes an object specific to the event that is being handled.</span></span> <span data-ttu-id="97055-109">Odkazem na vlastnosti objektu (a někdy na jeho metody) můžete získat informace, jako je například umístění myši pro události myši nebo přenášená data v událostech přetažení.</span><span class="sxs-lookup"><span data-stu-id="97055-109">By referencing the object's properties (and, sometimes, its methods), you can obtain information such as the location of the mouse for mouse events or data being transferred in drag-and-drop events.</span></span>  
  
 <span data-ttu-id="97055-110">Každá událost obvykle vytváří obslužnou rutinu události s jiným typem objektu Event pro druhý parametr.</span><span class="sxs-lookup"><span data-stu-id="97055-110">Typically each event produces an event handler with a different event-object type for the second parameter.</span></span> <span data-ttu-id="97055-111">Některé obslužné rutiny událostí, jako jsou například pro události <xref:System.Windows.Forms.Control.MouseDown> a <xref:System.Windows.Forms.Control.MouseUp>, mají stejný typ objektu pro svůj druhý parametr.</span><span class="sxs-lookup"><span data-stu-id="97055-111">Some event handlers, such as those for the <xref:System.Windows.Forms.Control.MouseDown> and <xref:System.Windows.Forms.Control.MouseUp> events, have the same object type for their second parameter.</span></span> <span data-ttu-id="97055-112">Pro tyto typy událostí můžete použít stejnou obslužnou rutinu události pro zpracování obou událostí.</span><span class="sxs-lookup"><span data-stu-id="97055-112">For these types of events, you can use the same event handler to handle both events.</span></span>  
  
 <span data-ttu-id="97055-113">Můžete také použít stejnou obslužnou rutinu události pro zpracování stejné události pro různé ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="97055-113">You can also use the same event handler to handle the same event for different controls.</span></span> <span data-ttu-id="97055-114">Například pokud máte ve formuláři skupinu <xref:System.Windows.Forms.RadioButton> ovládací prvky, můžete vytvořit jedinou obslužnou rutinu události pro událost <xref:System.Windows.Forms.Control.Click> a nechat událost <xref:System.Windows.Forms.Control.Click> každého ovládacího prvku svázat s jednou obslužnou rutinou události.</span><span class="sxs-lookup"><span data-stu-id="97055-114">For example, if you have a group of <xref:System.Windows.Forms.RadioButton> controls on a form, you could create a single event handler for the <xref:System.Windows.Forms.Control.Click> event and have each control's <xref:System.Windows.Forms.Control.Click> event bound to the single event handler.</span></span> <span data-ttu-id="97055-115">Další informace najdete v tématu [Postup: připojení více událostí k jedné obslužné rutině události v model Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="97055-115">For more information, see [How to: Connect Multiple Events to a Single Event Handler in Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97055-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="97055-116">See also</span></span>

- [<span data-ttu-id="97055-117">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="97055-117">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="97055-118">Přehled událostí</span><span class="sxs-lookup"><span data-stu-id="97055-118">Events Overview</span></span>](events-overview-windows-forms.md)
