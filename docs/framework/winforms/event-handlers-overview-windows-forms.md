---
title: Přehled obslužných rutin událostí (Windows Forms)
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
ms.openlocfilehash: cab35250f4fedf0a08dc7198430a668c7428c207
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54567748"
---
# <a name="event-handlers-overview-windows-forms"></a><span data-ttu-id="9fdad-102">Přehled obslužných rutin událostí (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="9fdad-102">Event Handlers Overview (Windows Forms)</span></span>
<span data-ttu-id="9fdad-103">Obslužná rutina události je metoda, která je vázána na událost.</span><span class="sxs-lookup"><span data-stu-id="9fdad-103">An event handler is a method that is bound to an event.</span></span> <span data-ttu-id="9fdad-104">Když se vyvolá událost, je proveden kód v obslužné rutině události.</span><span class="sxs-lookup"><span data-stu-id="9fdad-104">When the event is raised, the code within the event handler is executed.</span></span> <span data-ttu-id="9fdad-105">Každá obslužná rutina události poskytuje dva parametry, které umožňují zpracovat událost správně.</span><span class="sxs-lookup"><span data-stu-id="9fdad-105">Each event handler provides two parameters that allow you to handle the event properly.</span></span> <span data-ttu-id="9fdad-106">Následující příklad ukazuje obslužná rutina události <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Click> událostí.</span><span class="sxs-lookup"><span data-stu-id="9fdad-106">The following example shows an event handler for a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
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
  
 <span data-ttu-id="9fdad-107">První parametr`sender`, poskytuje odkaz na objekt, který vyvolal událost.</span><span class="sxs-lookup"><span data-stu-id="9fdad-107">The first parameter,`sender`, provides a reference to the object that raised the event.</span></span> <span data-ttu-id="9fdad-108">Druhý parametr `e`, v příkladu výše, předá objekt konkrétní událost, která se právě zpracovává.</span><span class="sxs-lookup"><span data-stu-id="9fdad-108">The second parameter, `e`, in the example above, passes an object specific to the event that is being handled.</span></span> <span data-ttu-id="9fdad-109">Pomocí odkazu na vlastnosti objektu (a v některých případech její metody), můžete získat informace, jako je poloha myši pro události myši nebo dat přenášených v událostech a přetažení.</span><span class="sxs-lookup"><span data-stu-id="9fdad-109">By referencing the object's properties (and, sometimes, its methods), you can obtain information such as the location of the mouse for mouse events or data being transferred in drag-and-drop events.</span></span>  
  
 <span data-ttu-id="9fdad-110">Každá událost obvykle vytvoří obslužnou rutinu události s typem objektu na různé události pro druhý parametr.</span><span class="sxs-lookup"><span data-stu-id="9fdad-110">Typically each event produces an event handler with a different event-object type for the second parameter.</span></span> <span data-ttu-id="9fdad-111">Některé obslužné rutiny událostí, třeba kroky týkající <xref:System.Windows.Forms.Control.MouseDown> a <xref:System.Windows.Forms.Control.MouseUp> události, mají stejný typ objektu pro jejich druhý parametr.</span><span class="sxs-lookup"><span data-stu-id="9fdad-111">Some event handlers, such as those for the <xref:System.Windows.Forms.Control.MouseDown> and <xref:System.Windows.Forms.Control.MouseUp> events, have the same object type for their second parameter.</span></span> <span data-ttu-id="9fdad-112">Pro tyto typy událostí, které můžete použít stejný ovladač událostí zpracování obou událostí.</span><span class="sxs-lookup"><span data-stu-id="9fdad-112">For these types of events, you can use the same event handler to handle both events.</span></span>  
  
 <span data-ttu-id="9fdad-113">Stejný ovladač událostí můžete použít také pro zpracování stejné události pro různé ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="9fdad-113">You can also use the same event handler to handle the same event for different controls.</span></span> <span data-ttu-id="9fdad-114">Například, pokud máte skupinu <xref:System.Windows.Forms.RadioButton> ovládací prvky ve formuláři, můžete vytvořit obslužnou rutinu pro jednu událost <xref:System.Windows.Forms.Control.Click> událostí a mít každý ovládací prvek <xref:System.Windows.Forms.Control.Click> událost vázána jedné obslužné rutině událostí.</span><span class="sxs-lookup"><span data-stu-id="9fdad-114">For example, if you have a group of <xref:System.Windows.Forms.RadioButton> controls on a form, you could create a single event handler for the <xref:System.Windows.Forms.Control.Click> event and have each control's <xref:System.Windows.Forms.Control.Click> event bound to the single event handler.</span></span> <span data-ttu-id="9fdad-115">Další informace najdete v tématu [jak: Připojení více událostí jedné obslužné rutině událostí ve Windows Forms](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="9fdad-115">For more information, see [How to: Connect Multiple Events to a Single Event Handler in Windows Forms](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fdad-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9fdad-116">See also</span></span>
- [<span data-ttu-id="9fdad-117">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9fdad-117">Creating Event Handlers in Windows Forms</span></span>](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="9fdad-118">Přehled událostí</span><span class="sxs-lookup"><span data-stu-id="9fdad-118">Events Overview</span></span>](../../../docs/framework/winforms/events-overview-windows-forms.md)
