---
title: Změna zpoždění součásti ToolTip
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
ms.openlocfilehash: 8ab0b0760e8c82d752eaada19f14cae57fa63fdc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746585"
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a><span data-ttu-id="47433-102">Postupy: Změna zpoždění součásti Windows Forms ToolTip</span><span class="sxs-lookup"><span data-stu-id="47433-102">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>
<span data-ttu-id="47433-103">Existuje více hodnot zpoždění, které lze nastavit pro komponentu model Windows Forms <xref:System.Windows.Forms.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="47433-103">There are multiple delay values that you can set for a Windows Forms <xref:System.Windows.Forms.ToolTip> component.</span></span> <span data-ttu-id="47433-104">Jednotka měření všech těchto vlastností je milisekund.</span><span class="sxs-lookup"><span data-stu-id="47433-104">The unit of measure for all these properties is milliseconds.</span></span> <span data-ttu-id="47433-105">Vlastnost <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> určuje, jak dlouho musí uživatel ukazovat na přidružený ovládací prvek, aby se zobrazil řetězec s popisem tlačítka.</span><span class="sxs-lookup"><span data-stu-id="47433-105">The <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> property determines how long the user must point at the associated control for the ToolTip string to appear.</span></span> <span data-ttu-id="47433-106">Vlastnost <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> nastaví počet milisekund, které bude trvat, než se při přesunutí ukazatele myši z jednoho ovládacího prvku přidruženého k popisku na jiný ovládací prvek s popisem tlačítka zobrazí v milisekundách.</span><span class="sxs-lookup"><span data-stu-id="47433-106">The <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> property sets the number of milliseconds it takes for subsequent ToolTip strings to appear as the mouse moves from one ToolTip-associated control to another.</span></span> <span data-ttu-id="47433-107">Vlastnost <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> určuje dobu, po kterou je zobrazen řetězec s popisem tlačítka.</span><span class="sxs-lookup"><span data-stu-id="47433-107">The <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> property determines the length of time the ToolTip string is shown.</span></span> <span data-ttu-id="47433-108">Tyto hodnoty můžete nastavit individuálně nebo nastavením hodnoty vlastnosti <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>; Ostatní vlastnosti zpoždění jsou nastaveny na základě hodnoty přiřazené vlastnosti <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>.</span><span class="sxs-lookup"><span data-stu-id="47433-108">You can set these values individually, or by setting the value of the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property; the other delay properties are set based on the value assigned to the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property.</span></span> <span data-ttu-id="47433-109">Pokud je například <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> nastaveno na hodnotu N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> je nastavena na hodnotu N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> je nastavena na hodnotu <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> dělenou pěti (nebo N/5) a <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> je nastavena na hodnotu, která je pětkrát hodnotou <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> vlastnosti (nebo 5N).</span><span class="sxs-lookup"><span data-stu-id="47433-109">For example, when <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> is set to a value N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> is set to N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> is set to the value of <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> divided by five (or N/5), and <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> is set to a value that is five times the value of the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property (or 5N).</span></span>  
  
### <a name="to-set-the-delay"></a><span data-ttu-id="47433-110">Nastavení zpoždění</span><span class="sxs-lookup"><span data-stu-id="47433-110">To set the delay</span></span>  
  
1. <span data-ttu-id="47433-111">Nastavte následující vlastnosti, jak je znázorněno v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="47433-111">Set the following properties as shown in this example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="47433-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="47433-112">See also</span></span>

- [<span data-ttu-id="47433-113">Přehled komponenty ToolTip</span><span class="sxs-lookup"><span data-stu-id="47433-113">ToolTip Component Overview</span></span>](tooltip-component-overview-windows-forms.md)
- [<span data-ttu-id="47433-114">Postupy: Nastavení ToolTips pro ovládací prvky ve formuláři Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="47433-114">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [<span data-ttu-id="47433-115">Komponenta ToolTip</span><span class="sxs-lookup"><span data-stu-id="47433-115">ToolTip Component</span></span>](tooltip-component-windows-forms.md)
