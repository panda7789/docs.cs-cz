---
title: 'Postupy: Nastavení pozadí panelu Windows Forms pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: 6927a7118c43ced03623a9764a3ef1e0814c95cb
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211632"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a><span data-ttu-id="8221e-102">Postupy: Nastavení pozadí panelu Windows Forms pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="8221e-102">How to: Set the background of a Windows Forms panel using the Designer</span></span>

<span data-ttu-id="8221e-103">Windows Forms <xref:System.Windows.Forms.Panel> ovládací prvek mohl zobrazit barvu pozadí a obrázek na pozadí.</span><span class="sxs-lookup"><span data-stu-id="8221e-103">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="8221e-104"><xref:System.Windows.Forms.Control.BackColor%2A> Vlastnost nastaví barvu pozadí pro ovládací prvky, které jsou obsaženy v panelu, jako je například popisky a přepínače.</span><span class="sxs-lookup"><span data-stu-id="8221e-104">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for controls that are contained in the panel, such as labels and radio buttons.</span></span> <span data-ttu-id="8221e-105">Pokud <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnost není nastavená, <xref:System.Windows.Forms.Control.BackColor%2A> výběr vyplní všechny panelu.</span><span class="sxs-lookup"><span data-stu-id="8221e-105">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill all of the panel.</span></span> <span data-ttu-id="8221e-106">Pokud <xref:System.Windows.Forms.Control.BackgroundImage%2A> je hodnota nastavena, obrázek se zobrazí za ovládací prvky, které jsou obsaženy v panelu.</span><span class="sxs-lookup"><span data-stu-id="8221e-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the controls that are contained in the panel.</span></span>

<span data-ttu-id="8221e-107">Následující postup vyžaduje, **aplikace Windows** projektu, který obsahuje formulář <xref:System.Windows.Forms.Panel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8221e-107">The following procedure requires a **Windows Application** project with a form that contains a <xref:System.Windows.Forms.Panel> control.</span></span> <span data-ttu-id="8221e-108">Informace o tom, jak nastavit projekt v sadě Visual Studio najdete v tématu [jak: Vytvoření projektu aplikace Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [jak: Přidání ovládacích prvků Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="8221e-108">For information about how to set up such a project in Visual Studio, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="set-the-background-in-the-windows-forms-designer"></a><span data-ttu-id="8221e-109">Nastavení pozadí v Návrháři formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="8221e-109">Set the background in the Windows Forms Designer</span></span>

1. <span data-ttu-id="8221e-110">Otevřete projekt v sadě Visual Studio a vyberte <xref:System.Windows.Forms.Panel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8221e-110">Open the project in Visual Studio and select the <xref:System.Windows.Forms.Panel> control.</span></span>

2. <span data-ttu-id="8221e-111">V **vlastnosti** okna, klikněte na šipku vedle <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost pro zobrazení okna se třemi kartami.</span><span class="sxs-lookup"><span data-stu-id="8221e-111">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackColor%2A> property to display a window with three tabs.</span></span>

3. <span data-ttu-id="8221e-112">Vyberte **vlastní** kartu k zobrazení palety barev.</span><span class="sxs-lookup"><span data-stu-id="8221e-112">Select the **Custom** tab to display a palette of colors.</span></span>

4. <span data-ttu-id="8221e-113">Vyberte **webové** nebo **systému** kartě zobrazíte seznam předdefinovaných názvů pro barvy a pak vyberte barvu.</span><span class="sxs-lookup"><span data-stu-id="8221e-113">Select the **Web** or **System** tab to display a list of predefined names for colors, and then select a color.</span></span>

5. <span data-ttu-id="8221e-114">V **vlastnosti** okna, klikněte na šipku vedle <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8221e-114">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span>

6. <span data-ttu-id="8221e-115">V **otevřít** dialogovém okně vyberte soubor, který chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="8221e-115">In the **Open** dialog box, select the file that you want to display.</span></span>

## <a name="see-also"></a><span data-ttu-id="8221e-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8221e-116">See also</span></span>

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [<span data-ttu-id="8221e-117">Ovládací prvek Panel</span><span class="sxs-lookup"><span data-stu-id="8221e-117">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="8221e-118">Přehled ovládacího prvku Panel</span><span class="sxs-lookup"><span data-stu-id="8221e-118">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="8221e-119">Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms Panel pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="8221e-119">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>](group-controls-with-wf-panel-control-using-the-designer.md)
