---
title: Události změny vlastnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- properties [Windows Forms], changes
ms.assetid: 268039ec-5aaa-4d76-b902-acccb036c850
ms.openlocfilehash: cabfd9e799288a332a0b2f96140f5f1cc328508b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59105765"
---
# <a name="property-changed-events"></a><span data-ttu-id="8cb20-102">Události změny vlastnosti</span><span class="sxs-lookup"><span data-stu-id="8cb20-102">Property-Changed Events</span></span>
<span data-ttu-id="8cb20-103">Pokud chcete, aby ovládací prvek k odesílání oznámení, když vlastnost s názvem *PropertyName* změny, definovat událost s názvem *PropertyName* `Changed` a metodu s názvem `On` *PropertyName* `Changed` , která vyvolává událost.</span><span class="sxs-lookup"><span data-stu-id="8cb20-103">If you want your control to send notifications when a property named *PropertyName* changes, define an event named *PropertyName*`Changed` and a method named `On`*PropertyName*`Changed` that raises the event.</span></span> <span data-ttu-id="8cb20-104">Zásady vytváření názvů v modelu Windows Forms je připojit slovo *změněné* k názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8cb20-104">The naming convention in Windows Forms is to append the word *Changed* to the name of the property.</span></span> <span data-ttu-id="8cb20-105">Typ delegáta přidružené události pro události změny vlastnosti je <xref:System.EventHandler>, a datový typ události je <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="8cb20-105">The associated event delegate type for property-changed events is <xref:System.EventHandler>, and the event data type is <xref:System.EventArgs>.</span></span> <span data-ttu-id="8cb20-106">Základní třída <xref:System.Windows.Forms.Control> definuje mnoho události změny vlastnosti, jako například <xref:System.Windows.Forms.Control.BackColorChanged>, <xref:System.Windows.Forms.Control.BackgroundImageChanged>, <xref:System.Windows.Forms.Control.FontChanged>, <xref:System.Windows.Forms.Control.LocationChanged>a další.</span><span class="sxs-lookup"><span data-stu-id="8cb20-106">The base class <xref:System.Windows.Forms.Control> defines many property-changed events, such as <xref:System.Windows.Forms.Control.BackColorChanged>, <xref:System.Windows.Forms.Control.BackgroundImageChanged>, <xref:System.Windows.Forms.Control.FontChanged>, <xref:System.Windows.Forms.Control.LocationChanged>, and others.</span></span> <span data-ttu-id="8cb20-107">Základní informace o událostech, naleznete v tématu [události](../../../standard/events/index.md) a [události v ovládacích prvcích Windows Forms](events-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="8cb20-107">For background information about events, see [Events](../../../standard/events/index.md) and [Events in Windows Forms Controls](events-in-windows-forms-controls.md).</span></span>  
  
 <span data-ttu-id="8cb20-108">Události změny vlastnosti jsou užitečné, protože umožňují uživatelům ovládací prvek připojte obslužné rutiny událostí, které reagují na změnu.</span><span class="sxs-lookup"><span data-stu-id="8cb20-108">Property-changed events are useful because they allow consumers of a control to attach event handlers that respond to the change.</span></span> <span data-ttu-id="8cb20-109">Pokud váš ovládací prvek reagovat na události změny vlastnosti, která vyvolá, přepište odpovídající `On` *PropertyName* `Changed` metoda místo připojením delegáta k události.</span><span class="sxs-lookup"><span data-stu-id="8cb20-109">If your control needs to respond to a property-changed event that it raises, override the corresponding `On`*PropertyName*`Changed` method instead of attaching a delegate to the event.</span></span> <span data-ttu-id="8cb20-110">Ovládací prvek je obvykle reakce na událost změny vlastnosti, aktualizují se ostatní vlastnosti nebo překreslování některé nebo všechny jeho návrhovém povrchu.</span><span class="sxs-lookup"><span data-stu-id="8cb20-110">A control typically responds to a property-changed event by updating other properties or by redrawing some or all of its drawing surface.</span></span>  
  
 <span data-ttu-id="8cb20-111">Následující příklad ukazuje způsob, jakým `FlashTrackBar` vlastní ovládací prvek reagovat na některé události změny vlastnosti, které dědí z <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="8cb20-111">The following example shows how the `FlashTrackBar` custom control responds to some of the property-changed events that it inherits from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="8cb20-112">Úplnou ukázku najdete v tématu [jak: Vytvoření ovládacího prvku Windows Forms zobrazujícího průběh](how-to-create-a-windows-forms-control-that-shows-progress.md).</span><span class="sxs-lookup"><span data-stu-id="8cb20-112">For the complete sample, see [How to: Create a Windows Forms Control That Shows Progress](how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#2)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="8cb20-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8cb20-113">See also</span></span>

- [<span data-ttu-id="8cb20-114">Události</span><span class="sxs-lookup"><span data-stu-id="8cb20-114">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="8cb20-115">Události v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8cb20-115">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)
- [<span data-ttu-id="8cb20-116">Vlastnosti v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8cb20-116">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
