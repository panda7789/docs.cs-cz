---
title: 'Postupy: Změna zpoždění komponenty Windows Forms ToolTip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolTip component [Windows Forms], delay values
- tooltips [Windows Forms], delay values
- examples [Windows Forms], tooltips
ms.assetid: 08979ba7-dd84-477b-ab17-8d06e759be99
ms.openlocfilehash: cf257cccd272c16c3d7c3d403456265444fc8ac8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781235"
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a><span data-ttu-id="f6c1c-102">Postupy: Změna zpoždění komponenty Windows Forms ToolTip</span><span class="sxs-lookup"><span data-stu-id="f6c1c-102">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>
<span data-ttu-id="f6c1c-103">Existuje více hodnot zpoždění, které můžete nastavit pro Windows Forms <xref:System.Windows.Forms.ToolTip> komponenty.</span><span class="sxs-lookup"><span data-stu-id="f6c1c-103">There are multiple delay values that you can set for a Windows Forms <xref:System.Windows.Forms.ToolTip> component.</span></span> <span data-ttu-id="f6c1c-104">Jednotka měření pro všechny tyto vlastnosti je milisekund.</span><span class="sxs-lookup"><span data-stu-id="f6c1c-104">The unit of measure for all these properties is milliseconds.</span></span> <span data-ttu-id="f6c1c-105"><xref:System.Windows.Forms.ToolTip.InitialDelay%2A> Vlastnost určuje, jak dlouho musí odkazovat uživatele na přidružený ovládací prvek pro řetězec popisku se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="f6c1c-105">The <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> property determines how long the user must point at the associated control for the ToolTip string to appear.</span></span> <span data-ttu-id="f6c1c-106"><xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> Vlastnost nastaví dobu v milisekundách, která je potřebná pro následující řetězce popis se zobrazí jako ukazatel myši přesune z jednoho ovládacího prvku ToolTip přidružené do jiného.</span><span class="sxs-lookup"><span data-stu-id="f6c1c-106">The <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> property sets the number of milliseconds it takes for subsequent ToolTip strings to appear as the mouse moves from one ToolTip-associated control to another.</span></span> <span data-ttu-id="f6c1c-107"><xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> Vlastnost určuje dobu řetězec popisku se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="f6c1c-107">The <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> property determines the length of time the ToolTip string is shown.</span></span> <span data-ttu-id="f6c1c-108">Tyto hodnoty můžete nastavit samostatně, nebo tak, že nastavíte hodnotu <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> vlastnost; zpoždění, které jsou nastaveny vlastnosti závislosti na hodnotě přiřazené k <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f6c1c-108">You can set these values individually, or by setting the value of the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property; the other delay properties are set based on the value assigned to the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property.</span></span> <span data-ttu-id="f6c1c-109">Například, když <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> je nastavena na hodnotu N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> je nastavena na N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> je nastavena na hodnotu <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> rozdělené podle pět (nebo N/5), a <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> je nastavena na hodnotu, která je pětkrát hodnotu <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> vlastnosti (nebo 5N).</span><span class="sxs-lookup"><span data-stu-id="f6c1c-109">For example, when <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> is set to a value N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> is set to N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> is set to the value of <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> divided by five (or N/5), and <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> is set to a value that is five times the value of the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property (or 5N).</span></span>  
  
### <a name="to-set-the-delay"></a><span data-ttu-id="f6c1c-110">Chcete-li nastavit zpoždění</span><span class="sxs-lookup"><span data-stu-id="f6c1c-110">To set the delay</span></span>  
  
1. <span data-ttu-id="f6c1c-111">Jak je znázorněno v tomto příkladu, nastavte následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f6c1c-111">Set the following properties as shown in this example.</span></span>  
  
    ```vb  
    ToolTip1.InitialDelay = 500  
    ToolTip1.ReshowDelay = 100  
    ToolTip1.AutoPopDelay = 5000  
    ```  
  
    ```csharp  
    ToolTip1.InitialDelay = 500;  
    ToolTip1.ReshowDelay = 100;  
    ToolTip1.AutoPopDelay = 5000;  
    ```  
  
    ```cpp  
    toolTip1->InitialDelay = 500;  
    toolTip1->ReshowDelay = 100;  
    toolTip1->AutoPopDelay = 5000;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f6c1c-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f6c1c-112">See also</span></span>

- [<span data-ttu-id="f6c1c-113">Přehled komponenty ToolTip</span><span class="sxs-lookup"><span data-stu-id="f6c1c-113">ToolTip Component Overview</span></span>](tooltip-component-overview-windows-forms.md)
- [<span data-ttu-id="f6c1c-114">Postupy: Nastavení ToolTips pro ovládací prvky ve formuláři Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="f6c1c-114">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [<span data-ttu-id="f6c1c-115">Komponenta ToolTip</span><span class="sxs-lookup"><span data-stu-id="f6c1c-115">ToolTip Component</span></span>](tooltip-component-windows-forms.md)
