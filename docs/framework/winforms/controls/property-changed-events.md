---
title: "Události změny vlastnosti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- properties [Windows Forms], changes
ms.assetid: 268039ec-5aaa-4d76-b902-acccb036c850
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ad22d77043f00ab0caaa6d8b08b6b0a9eef1fed5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="property-changed-events"></a><span data-ttu-id="0cbdc-102">Události změny vlastnosti</span><span class="sxs-lookup"><span data-stu-id="0cbdc-102">Property-Changed Events</span></span>
<span data-ttu-id="0cbdc-103">Pokud chcete, aby vaše řízení k odesílání oznámení, když vlastnost s názvem *PropertyName* změny, zadejte událost s názvem *PropertyName* `Changed` a metodu s názvem `On` *PropertyName* `Changed` který vyvolává událost.</span><span class="sxs-lookup"><span data-stu-id="0cbdc-103">If you want your control to send notifications when a property named *PropertyName* changes, define an event named *PropertyName*`Changed` and a method named `On`*PropertyName*`Changed` that raises the event.</span></span> <span data-ttu-id="0cbdc-104">Zásady vytváření názvů v rozhraní Windows Forms je připojit slovo *změněno* k názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="0cbdc-104">The naming convention in Windows Forms is to append the word *Changed* to the name of the property.</span></span> <span data-ttu-id="0cbdc-105">Typ delegáta související události pro události změny vlastnosti je <xref:System.EventHandler>, a je datový typ události <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="0cbdc-105">The associated event delegate type for property-changed events is <xref:System.EventHandler>, and the event data type is <xref:System.EventArgs>.</span></span> <span data-ttu-id="0cbdc-106">Základní třída <xref:System.Windows.Forms.Control> definuje mnoho události změny vlastnosti, jako například <xref:System.Windows.Forms.Control.BackColorChanged>, <xref:System.Windows.Forms.Control.BackgroundImageChanged>, <xref:System.Windows.Forms.Control.FontChanged>, <xref:System.Windows.Forms.Control.LocationChanged>a další.</span><span class="sxs-lookup"><span data-stu-id="0cbdc-106">The base class <xref:System.Windows.Forms.Control> defines many property-changed events, such as <xref:System.Windows.Forms.Control.BackColorChanged>, <xref:System.Windows.Forms.Control.BackgroundImageChanged>, <xref:System.Windows.Forms.Control.FontChanged>, <xref:System.Windows.Forms.Control.LocationChanged>, and others.</span></span> <span data-ttu-id="0cbdc-107">Základní informace o událostech, najdete v části [události](../../../../docs/standard/events/index.md) a [události v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="0cbdc-107">For background information about events, see [Events](../../../../docs/standard/events/index.md) and [Events in Windows Forms Controls](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md).</span></span>  
  
 <span data-ttu-id="0cbdc-108">Události změny vlastnosti jsou užitečné, protože umožňují příjemci ovládacího prvku připojit obslužné rutiny událostí, které reagují na změnu.</span><span class="sxs-lookup"><span data-stu-id="0cbdc-108">Property-changed events are useful because they allow consumers of a control to attach event handlers that respond to the change.</span></span> <span data-ttu-id="0cbdc-109">Pokud vaše ovládací prvek musí reagovat na událost změny vlastnosti, která se vyvolá, mají přednost před odpovídající `On` *PropertyName* `Changed` metody místo připojení delegáta k události.</span><span class="sxs-lookup"><span data-stu-id="0cbdc-109">If your control needs to respond to a property-changed event that it raises, override the corresponding `On`*PropertyName*`Changed` method instead of attaching a delegate to the event.</span></span> <span data-ttu-id="0cbdc-110">Ovládací prvek se obvykle odpovídá na událost změny vlastnosti aktualizace jiných vlastností nebo překreslování některé nebo všechny jeho kreslicí plochy.</span><span class="sxs-lookup"><span data-stu-id="0cbdc-110">A control typically responds to a property-changed event by updating other properties or by redrawing some or all of its drawing surface.</span></span>  
  
 <span data-ttu-id="0cbdc-111">Následující příklad ukazuje jak `FlashTrackBar` vlastního ovládacího prvku odpovídá na některé změny vlastnosti události, které dědí z <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="0cbdc-111">The following example shows how the `FlashTrackBar` custom control responds to some of the property-changed events that it inherits from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="0cbdc-112">Kompletní příklad, najdete v části [postupy: vytvoření Windows Forms ovládací prvek, zobrazuje průběh](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span><span class="sxs-lookup"><span data-stu-id="0cbdc-112">For the complete sample, see [How to: Create a Windows Forms Control That Shows Progress](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#2)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="0cbdc-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="0cbdc-113">See Also</span></span>  
 [<span data-ttu-id="0cbdc-114">Události</span><span class="sxs-lookup"><span data-stu-id="0cbdc-114">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="0cbdc-115">Události v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0cbdc-115">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 [<span data-ttu-id="0cbdc-116">Vlastnosti v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0cbdc-116">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
