---
title: Nastavení pozadí panelu pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: 8bdefba433632f7ba02f549a549c52c7aa56c2d7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731916"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a><span data-ttu-id="5e8d9-102">Postupy: nastavení pozadí model Windows Forms panelu pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="5e8d9-102">How to: Set the background of a Windows Forms panel using the Designer</span></span>

<span data-ttu-id="5e8d9-103">Ovládací prvek model Windows Forms <xref:System.Windows.Forms.Panel> může zobrazit barvu pozadí i obrázek pozadí.</span><span class="sxs-lookup"><span data-stu-id="5e8d9-103">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="5e8d9-104">Vlastnost <xref:System.Windows.Forms.Control.BackColor%2A> nastavuje barvu pozadí pro ovládací prvky, které jsou obsaženy na panelu, například popisky a přepínače.</span><span class="sxs-lookup"><span data-stu-id="5e8d9-104">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for controls that are contained in the panel, such as labels and radio buttons.</span></span> <span data-ttu-id="5e8d9-105">Pokud vlastnost <xref:System.Windows.Forms.Control.BackgroundImage%2A> není nastavena, <xref:System.Windows.Forms.Control.BackColor%2A> výběr vyplní celý panel.</span><span class="sxs-lookup"><span data-stu-id="5e8d9-105">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill all of the panel.</span></span> <span data-ttu-id="5e8d9-106">Pokud je nastavena vlastnost <xref:System.Windows.Forms.Control.BackgroundImage%2A>, obrázek se zobrazí za ovládacími prvky, které jsou obsaženy na panelu.</span><span class="sxs-lookup"><span data-stu-id="5e8d9-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the controls that are contained in the panel.</span></span>

<span data-ttu-id="5e8d9-107">Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.Panel>.</span><span class="sxs-lookup"><span data-stu-id="5e8d9-107">The following procedure requires a **Windows Application** project with a form that contains a <xref:System.Windows.Forms.Panel> control.</span></span> <span data-ttu-id="5e8d9-108">Informace o tom, jak nastavit takový projekt v aplikaci Visual Studio, naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [: Add controls to model Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="5e8d9-108">For information about how to set up such a project in Visual Studio, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="set-the-background-in-the-windows-forms-designer"></a><span data-ttu-id="5e8d9-109">Nastavení pozadí v Návrhář formulářů</span><span class="sxs-lookup"><span data-stu-id="5e8d9-109">Set the background in the Windows Forms Designer</span></span>

1. <span data-ttu-id="5e8d9-110">Otevřete projekt v aplikaci Visual Studio a vyberte ovládací prvek <xref:System.Windows.Forms.Panel>.</span><span class="sxs-lookup"><span data-stu-id="5e8d9-110">Open the project in Visual Studio and select the <xref:System.Windows.Forms.Panel> control.</span></span>

2. <span data-ttu-id="5e8d9-111">V okně **vlastnosti** klikněte na tlačítko se šipkou vedle vlastnosti <xref:System.Windows.Forms.Control.BackColor%2A>. zobrazí se okno se třemi kartami.</span><span class="sxs-lookup"><span data-stu-id="5e8d9-111">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackColor%2A> property to display a window with three tabs.</span></span>

3. <span data-ttu-id="5e8d9-112">Vyberte **vlastní** kartu pro zobrazení palety barev.</span><span class="sxs-lookup"><span data-stu-id="5e8d9-112">Select the **Custom** tab to display a palette of colors.</span></span>

4. <span data-ttu-id="5e8d9-113">Vyberte kartu **Web** nebo **systém** , chcete-li zobrazit seznam předdefinovaných názvů pro barvy a pak vyberte barvu.</span><span class="sxs-lookup"><span data-stu-id="5e8d9-113">Select the **Web** or **System** tab to display a list of predefined names for colors, and then select a color.</span></span>

5. <span data-ttu-id="5e8d9-114">V okně **vlastnosti** klikněte na tlačítko se šipkou vedle vlastnosti <xref:System.Windows.Forms.Control.BackgroundImage%2A>.</span><span class="sxs-lookup"><span data-stu-id="5e8d9-114">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span>

6. <span data-ttu-id="5e8d9-115">V dialogovém okně **otevřít** vyberte soubor, který chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="5e8d9-115">In the **Open** dialog box, select the file that you want to display.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e8d9-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5e8d9-116">See also</span></span>

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [<span data-ttu-id="5e8d9-117">Ovládací prvek Panel</span><span class="sxs-lookup"><span data-stu-id="5e8d9-117">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="5e8d9-118">Přehled ovládacího prvku Panel</span><span class="sxs-lookup"><span data-stu-id="5e8d9-118">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="5e8d9-119">Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms Panel pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="5e8d9-119">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>](group-controls-with-wf-panel-control-using-the-designer.md)
