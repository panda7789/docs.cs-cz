---
title: Události v ovládacích prvcích
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: c60713917b9c84aa7fad50fb1c81fc9252149ad6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745750"
---
# <a name="events-in-windows-forms-controls"></a><span data-ttu-id="b8714-102">Události v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b8714-102">Events in Windows Forms Controls</span></span>
<span data-ttu-id="b8714-103">Ovládací prvek model Windows Forms dědí více než 60 událostí od <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b8714-103">A Windows Forms control inherits more than sixty events from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b8714-104">Mezi ně patří událost <xref:System.Windows.Forms.Control.Paint>, což způsobí, že se ovládací prvek vykreslí, události související se zobrazením okna, jako jsou události <xref:System.Windows.Forms.Control.Resize> a <xref:System.Windows.Forms.Control.Layout>, a událostmi myši nízké úrovně a událostí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="b8714-104">These include the <xref:System.Windows.Forms.Control.Paint> event, which causes a control to be drawn, events related to displaying a window, such as the <xref:System.Windows.Forms.Control.Resize> and <xref:System.Windows.Forms.Control.Layout> events, and low-level mouse and keyboard events.</span></span> <span data-ttu-id="b8714-105">Některé události nízké úrovně jsou syntetizované <xref:System.Windows.Forms.Control> se sémantickými událostmi, jako jsou <xref:System.Windows.Forms.Control.Click> a <xref:System.Windows.Forms.Control.DoubleClick>.</span><span class="sxs-lookup"><span data-stu-id="b8714-105">Some low-level events are synthesized by <xref:System.Windows.Forms.Control> into semantic events such as <xref:System.Windows.Forms.Control.Click> and <xref:System.Windows.Forms.Control.DoubleClick>.</span></span> <span data-ttu-id="b8714-106">Podrobnosti o zděděných událostech najdete v tématu <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="b8714-106">For details about inherited events, see <xref:System.Windows.Forms.Control>.</span></span>  
  
 <span data-ttu-id="b8714-107">Pokud váš vlastní ovládací prvek potřebuje přepsat zděděné funkce události, přepište zděděnou metodu `On`*EventName* namísto připojení delegáta.</span><span class="sxs-lookup"><span data-stu-id="b8714-107">If your custom control needs to override inherited event functionality, override the inherited `On`*EventName* method instead of attaching a delegate.</span></span> <span data-ttu-id="b8714-108">Pokud nejste obeznámeni s modelem událostí v .NET Framework, přečtěte si téma [vyvolání událostí ze součásti](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="b8714-108">If you are not familiar with the event model in the .NET Framework, see [Raising Events from a Component](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8714-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8714-109">See also</span></span>

- [<span data-ttu-id="b8714-110">Přepsání metody OnPaint</span><span class="sxs-lookup"><span data-stu-id="b8714-110">Overriding the OnPaint Method</span></span>](overriding-the-onpaint-method.md)
- [<span data-ttu-id="b8714-111">Zpracování uživatelského vstupu</span><span class="sxs-lookup"><span data-stu-id="b8714-111">Handling User Input</span></span>](handling-user-input.md)
- [<span data-ttu-id="b8714-112">Definování události</span><span class="sxs-lookup"><span data-stu-id="b8714-112">Defining an Event</span></span>](defining-an-event-in-windows-forms-controls.md)
- [<span data-ttu-id="b8714-113">Události</span><span class="sxs-lookup"><span data-stu-id="b8714-113">Events</span></span>](../../../standard/events/index.md)
