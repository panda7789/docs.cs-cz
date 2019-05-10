---
title: 'Postupy: Nastavení ToolTips pro ovládací prvky ve formuláři Windows v době návrhu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 0d6725fc1a00826870e6400bffce63a1788e802c
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211688"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a><span data-ttu-id="465b7-102">Postupy: Nastavení ToolTips pro ovládací prvky ve formuláři Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="465b7-102">How to: Set ToolTips for controls on a Windows Form at design time</span></span>

<span data-ttu-id="465b7-103">Můžete nastavit <xref:System.Windows.Forms.ToolTip> řetězec v kódu nebo v Návrháři formulářů Windows v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="465b7-103">You can set a <xref:System.Windows.Forms.ToolTip> string in code or in the Windows Forms Designer in Visual Studio.</span></span> <span data-ttu-id="465b7-104">Další informace o <xref:System.Windows.Forms.ToolTip> komponenty, naleznete v tématu [ToolTip – přehled komponenty](tooltip-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="465b7-104">For more information about the <xref:System.Windows.Forms.ToolTip> component, see [ToolTip Component Overview](tooltip-component-overview-windows-forms.md).</span></span>

## <a name="set-a-tooltip-programmatically"></a><span data-ttu-id="465b7-105">Popis nastavit prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="465b7-105">Set a ToolTip programmatically</span></span>

1. <span data-ttu-id="465b7-106">Přidejte ovládací prvek, který se zobrazí popisek.</span><span class="sxs-lookup"><span data-stu-id="465b7-106">Add the control that will display the ToolTip.</span></span>

2. <span data-ttu-id="465b7-107">Použití <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metodu <xref:System.Windows.Forms.ToolTip> komponenty.</span><span class="sxs-lookup"><span data-stu-id="465b7-107">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>

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

## <a name="set-a-tooltip-in-the-designer"></a><span data-ttu-id="465b7-108">Popis nastavit v Návrháři</span><span class="sxs-lookup"><span data-stu-id="465b7-108">Set a ToolTip in the designer</span></span>

1. <span data-ttu-id="465b7-109">V sadě Visual Studio, přidejte <xref:System.Windows.Forms.ToolTip> komponentu do formuláře.</span><span class="sxs-lookup"><span data-stu-id="465b7-109">In Visual Studio, add a <xref:System.Windows.Forms.ToolTip> component to the form.</span></span>

2. <span data-ttu-id="465b7-110">Vyberte ovládací prvek, který zobrazí popis tlačítka, nebo ho přidejte do formuláře.</span><span class="sxs-lookup"><span data-stu-id="465b7-110">Select the control that will display the ToolTip, or add it to the form.</span></span>

3. <span data-ttu-id="465b7-111">V **vlastnosti** okno, nastaveno **popisu tlačítka ToolTip1** hodnota, která má odpovídající řetězec textu.</span><span class="sxs-lookup"><span data-stu-id="465b7-111">In the **Properties** window, set the **ToolTip on ToolTip1** value to an appropriate string of text.</span></span>

### <a name="to-remove-a-tooltip-programmatically"></a><span data-ttu-id="465b7-112">Chcete-li odebrat popisek prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="465b7-112">To remove a ToolTip programmatically</span></span>

1. <span data-ttu-id="465b7-113">Použití <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metodu <xref:System.Windows.Forms.ToolTip> komponenty.</span><span class="sxs-lookup"><span data-stu-id="465b7-113">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>

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

## <a name="remove-a-tooltip-in-the-designer"></a><span data-ttu-id="465b7-114">Odebrat popisek v Návrháři</span><span class="sxs-lookup"><span data-stu-id="465b7-114">Remove a ToolTip in the designer</span></span>

1. <span data-ttu-id="465b7-115">V sadě Visual Studio vyberte ovládací prvek, který se zobrazuje v popisku.</span><span class="sxs-lookup"><span data-stu-id="465b7-115">In Visual Studio, select the control that is displaying the ToolTip.</span></span>

2. <span data-ttu-id="465b7-116">V **vlastnosti** okna, odstraníte tím stávající text v **popisu tlačítka ToolTip1**.</span><span class="sxs-lookup"><span data-stu-id="465b7-116">In the **Properties** window, delete the text in the **ToolTip on ToolTip1**.</span></span>

## <a name="see-also"></a><span data-ttu-id="465b7-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="465b7-117">See also</span></span>

- [<span data-ttu-id="465b7-118">Přehled komponenty ToolTip</span><span class="sxs-lookup"><span data-stu-id="465b7-118">ToolTip Component Overview</span></span>](tooltip-component-overview-windows-forms.md)
- [<span data-ttu-id="465b7-119">Postupy: Změna zpoždění komponenty Windows Forms ToolTip</span><span class="sxs-lookup"><span data-stu-id="465b7-119">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [<span data-ttu-id="465b7-120">Komponenta ToolTip</span><span class="sxs-lookup"><span data-stu-id="465b7-120">ToolTip Component</span></span>](tooltip-component-windows-forms.md)
