---
title: 'Postupy: Definování ikony pro tlačítko ToolBar pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- buttons [Windows Forms], images
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
ms.openlocfilehash: 49e93f12bebbf409e6b3a06634556b9103c85f44
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666208"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a><span data-ttu-id="4f62f-102">Postupy: Definování ikony pro tlačítko ToolBar pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="4f62f-102">How to: Define an Icon for a ToolBar Button Using the Designer</span></span>

> [!NOTE]
> <span data-ttu-id="4f62f-103">Ovládací prvek nahrazuje a přidává funkce <xref:System.Windows.Forms.ToolBar> <xref:System.Windows.Forms.ToolBar> ovládacímu prvku. ovládací prvek je však ponechán pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. <xref:System.Windows.Forms.ToolStrip></span><span class="sxs-lookup"><span data-stu-id="4f62f-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>

<span data-ttu-id="4f62f-104"><xref:System.Windows.Forms.ToolBar>tlačítka jsou schopna zobrazit ikony, aby je uživatelé mohli snadno identifikovat.</span><span class="sxs-lookup"><span data-stu-id="4f62f-104"><xref:System.Windows.Forms.ToolBar> buttons are able to display icons within them for easy identification by users.</span></span> <span data-ttu-id="4f62f-105">Toho lze dosáhnout přidáním obrázků do <xref:System.Windows.Forms.ImageList> komponenty a jejich <xref:System.Windows.Forms.ToolBar> přidružením k ovládacímu prvku.</span><span class="sxs-lookup"><span data-stu-id="4f62f-105">This is achieved through adding images to the <xref:System.Windows.Forms.ImageList> component and associating it with the <xref:System.Windows.Forms.ToolBar> control.</span></span>

<span data-ttu-id="4f62f-106">Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje <xref:System.Windows.Forms.ToolBar> ovládací prvek a <xref:System.Windows.Forms.ImageList> komponentu.</span><span class="sxs-lookup"><span data-stu-id="4f62f-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ToolBar> control and an <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="4f62f-107">Informace o nastavení takového projektu naleznete v tématu [How to: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms a [postupujte takto: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="4f62f-107">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a><span data-ttu-id="4f62f-108">Nastavení ikony pro tlačítko panelu nástrojů v době návrhu</span><span class="sxs-lookup"><span data-stu-id="4f62f-108">To set an icon for a toolbar button at design time</span></span>

1. <span data-ttu-id="4f62f-109">Přidejte obrázky do <xref:System.Windows.Forms.ImageList> komponenty.</span><span class="sxs-lookup"><span data-stu-id="4f62f-109">Add images to the <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="4f62f-110">Další informace najdete v tématu [jak: Přidejte nebo odeberte obrázky ImageList pomocí návrháře](how-to-add-or-remove-imagelist-images-with-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="4f62f-110">For more information, see [How to: Add or Remove ImageList Images with the Designer](how-to-add-or-remove-imagelist-images-with-the-designer.md).</span></span>

2. <span data-ttu-id="4f62f-111"><xref:System.Windows.Forms.ToolBar> Vyberte ovládací prvek ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="4f62f-111">Select the <xref:System.Windows.Forms.ToolBar> control on your form.</span></span>

3. <span data-ttu-id="4f62f-112">V okně **vlastnosti** nastavte <xref:System.Windows.Forms.ToolBar> <xref:System.Windows.Forms.ToolBar.ImageList%2A> vlastnost ovládacího prvku na <xref:System.Windows.Forms.ImageList> součást.</span><span class="sxs-lookup"><span data-stu-id="4f62f-112">In the **Properties** window, set the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.ImageList%2A> property to the <xref:System.Windows.Forms.ImageList> component.</span></span>

4. <span data-ttu-id="4f62f-113"><xref:System.Windows.Forms.ToolBar.Buttons%2A> ![](./media/visual-studio-ellipsis-button.png)Kliknutím na vlastnost ovládacíhoprvkujivyberteakliknutímnatlačítkosetřemitečkami(...)voknoVlastnostisadyVisualStudio.)otevřeteEditorkolekceToolBarButton.<xref:System.Windows.Forms.ToolBar></span><span class="sxs-lookup"><span data-stu-id="4f62f-113">Click the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.Buttons%2A> property to select it, and click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button to open the **ToolBarButton Collection Editor**.</span></span>

5. <span data-ttu-id="4f62f-114">K přidání tlačítek do <xref:System.Windows.Forms.ToolBar> ovládacího prvku použijte tlačítko Přidat.</span><span class="sxs-lookup"><span data-stu-id="4f62f-114">Use the **Add** button to add buttons to the <xref:System.Windows.Forms.ToolBar> control.</span></span>

6. <span data-ttu-id="4f62f-115">V okně **vlastnosti** , které se zobrazí v podokně na pravé straně **editoru kolekce ToolBarButton** <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> , nastavte vlastnost každého tlačítka panelu nástrojů na jednu z hodnot v seznamu, která je vykreslena z obrázků přidaných do <xref:System.Windows.Forms.ImageList> součást.</span><span class="sxs-lookup"><span data-stu-id="4f62f-115">In the **Properties** window that appears in the pane on the right side of the **ToolBarButton Collection Editor**, set the <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> property of each toolbar button to one of the values in the list, which is drawn from the images you added to the <xref:System.Windows.Forms.ImageList> component.</span></span>

## <a name="see-also"></a><span data-ttu-id="4f62f-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f62f-116">See also</span></span>

- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="4f62f-117">Postupy: Aktivace událostí nabídky pro tlačítka panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="4f62f-117">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [<span data-ttu-id="4f62f-118">Ovládací prvek ToolBar</span><span class="sxs-lookup"><span data-stu-id="4f62f-118">ToolBar Control</span></span>](toolbar-control-windows-forms.md)
- [<span data-ttu-id="4f62f-119">Komponenta ImageList</span><span class="sxs-lookup"><span data-stu-id="4f62f-119">ImageList Component</span></span>](imagelist-component-windows-forms.md)
