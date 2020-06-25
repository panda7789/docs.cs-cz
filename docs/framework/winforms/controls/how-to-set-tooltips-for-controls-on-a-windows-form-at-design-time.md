---
title: 'Postupy: Nastavení ToolTips pro ovládací prvky ve formuláři Windows v době návrhu'
description: Naučte se, jak nastavit popisy tlačítek pro ovládací prvky programově nebo v Návrhář formulářů v sadě Visual Studio.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 15134b38d11de30d0e6a2f998f6ea266affc40d7
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325970"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a><span data-ttu-id="ebf32-103">Postupy: Nastavení popisků pro ovládací prvky ve formuláři Windows v době návrhu</span><span class="sxs-lookup"><span data-stu-id="ebf32-103">How to: Set ToolTips for controls on a Windows Form at design time</span></span>

<span data-ttu-id="ebf32-104">Můžete nastavit <xref:System.Windows.Forms.ToolTip> řetězec v kódu nebo v Návrhář formulářů v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ebf32-104">You can set a <xref:System.Windows.Forms.ToolTip> string in code or in the Windows Forms Designer in Visual Studio.</span></span> <span data-ttu-id="ebf32-105">Další informace o <xref:System.Windows.Forms.ToolTip> komponentě najdete v tématu [Přehled komponent ToolTip](tooltip-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="ebf32-105">For more information about the <xref:System.Windows.Forms.ToolTip> component, see [ToolTip Component Overview](tooltip-component-overview-windows-forms.md).</span></span>

## <a name="set-a-tooltip-programmatically"></a><span data-ttu-id="ebf32-106">Programové nastavení popisu</span><span class="sxs-lookup"><span data-stu-id="ebf32-106">Set a ToolTip programmatically</span></span>

1. <span data-ttu-id="ebf32-107">Přidejte ovládací prvek, který zobrazí popisek.</span><span class="sxs-lookup"><span data-stu-id="ebf32-107">Add the control that will display the ToolTip.</span></span>

2. <span data-ttu-id="ebf32-108">Použijte <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metodu <xref:System.Windows.Forms.ToolTip> komponenty.</span><span class="sxs-lookup"><span data-stu-id="ebf32-108">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>

    ```vb
    ' In this example, Button1 is the control to display the ToolTip.
    ToolTip1.SetToolTip(Button1, "Save changes")
    ```

    ```csharp
    // In this example, button1 is the control to display the ToolTip.
    toolTip1.SetToolTip(button1, "Save changes");
    ```

    ```cpp
    // In this example, button1 is the control to display the ToolTip.
    toolTip1->SetToolTip(button1, "Save changes");
    ```

## <a name="set-a-tooltip-in-the-designer"></a><span data-ttu-id="ebf32-109">Nastavení popisu v Návrháři</span><span class="sxs-lookup"><span data-stu-id="ebf32-109">Set a ToolTip in the designer</span></span>

1. <span data-ttu-id="ebf32-110">V aplikaci Visual Studio přidejte <xref:System.Windows.Forms.ToolTip> komponentu do formuláře.</span><span class="sxs-lookup"><span data-stu-id="ebf32-110">In Visual Studio, add a <xref:System.Windows.Forms.ToolTip> component to the form.</span></span>

2. <span data-ttu-id="ebf32-111">Vyberte ovládací prvek, který zobrazí popisek, nebo jej přidejte do formuláře.</span><span class="sxs-lookup"><span data-stu-id="ebf32-111">Select the control that will display the ToolTip, or add it to the form.</span></span>

3. <span data-ttu-id="ebf32-112">V okně **Vlastnosti nastavte vlastnost** **ToolTip na hodnotu ToolTip1** na příslušný textový řetězec.</span><span class="sxs-lookup"><span data-stu-id="ebf32-112">In the **Properties** window, set the **ToolTip on ToolTip1** value to an appropriate string of text.</span></span>

### <a name="to-remove-a-tooltip-programmatically"></a><span data-ttu-id="ebf32-113">Postup pro odebrání popisku pomocí kódu programu</span><span class="sxs-lookup"><span data-stu-id="ebf32-113">To remove a ToolTip programmatically</span></span>

1. <span data-ttu-id="ebf32-114">Použijte <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metodu <xref:System.Windows.Forms.ToolTip> komponenty.</span><span class="sxs-lookup"><span data-stu-id="ebf32-114">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>

    ```vb
    ' In this example, Button1 is the control displaying the ToolTip.
    ToolTip1.SetToolTip(Button1, Nothing)
    ```

    ```csharp
    // In this example, button1 is the control displaying the ToolTip.
    toolTip1.SetToolTip(button1, null);
    ```

    ```cpp
    // In this example, button1 is the control displaying the ToolTip.
    toolTip1->SetToolTip(button1, NULL);
    ```

## <a name="remove-a-tooltip-in-the-designer"></a><span data-ttu-id="ebf32-115">Odebrání popisu v Návrháři</span><span class="sxs-lookup"><span data-stu-id="ebf32-115">Remove a ToolTip in the designer</span></span>

1. <span data-ttu-id="ebf32-116">V aplikaci Visual Studio vyberte ovládací prvek, který zobrazuje popis tlačítka.</span><span class="sxs-lookup"><span data-stu-id="ebf32-116">In Visual Studio, select the control that is displaying the ToolTip.</span></span>

2. <span data-ttu-id="ebf32-117">V okně **vlastnosti** odstraňte text v **popisku v ToolTip1**.</span><span class="sxs-lookup"><span data-stu-id="ebf32-117">In the **Properties** window, delete the text in the **ToolTip on ToolTip1**.</span></span>

## <a name="see-also"></a><span data-ttu-id="ebf32-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ebf32-118">See also</span></span>

- [<span data-ttu-id="ebf32-119">ToolTip – přehled komponenty</span><span class="sxs-lookup"><span data-stu-id="ebf32-119">ToolTip Component Overview</span></span>](tooltip-component-overview-windows-forms.md)
- [<span data-ttu-id="ebf32-120">Postupy: Změna zpoždění komponenty Windows Forms ToolTip</span><span class="sxs-lookup"><span data-stu-id="ebf32-120">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [<span data-ttu-id="ebf32-121">Komponenta ToolTip</span><span class="sxs-lookup"><span data-stu-id="ebf32-121">ToolTip Component</span></span>](tooltip-component-windows-forms.md)
