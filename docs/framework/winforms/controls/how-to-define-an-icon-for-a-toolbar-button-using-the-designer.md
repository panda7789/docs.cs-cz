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
ms.openlocfilehash: 19d0b284238ed662b25627d6077c1ebe6ecc6e86
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59323704"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a><span data-ttu-id="53811-102">Postupy: Definování ikony pro tlačítko ToolBar pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="53811-102">How to: Define an Icon for a ToolBar Button Using the Designer</span></span>
> [!NOTE]
>  <span data-ttu-id="53811-103"><xref:System.Windows.Forms.ToolStrip> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.ToolBar> řízení; však <xref:System.Windows.Forms.ToolBar> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete.</span><span class="sxs-lookup"><span data-stu-id="53811-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="53811-104"><xref:System.Windows.Forms.ToolBar> tlačítka budou moct zobrazit ikony v nich pro snadnou identifikaci uživatelů.</span><span class="sxs-lookup"><span data-stu-id="53811-104"><xref:System.Windows.Forms.ToolBar> buttons are able to display icons within them for easy identification by users.</span></span> <span data-ttu-id="53811-105">Toho můžete dosáhnout přidávání obrázků na <xref:System.Windows.Forms.ImageList> komponenty a přidružíte ho <xref:System.Windows.Forms.ToolBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="53811-105">This is achieved through adding images to the <xref:System.Windows.Forms.ImageList> component and associating it with the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
 <span data-ttu-id="53811-106">Následující postup vyžaduje, **aplikace Windows** projektu s formulář obsahující <xref:System.Windows.Forms.ToolBar> ovládacího prvku a <xref:System.Windows.Forms.ImageList> komponenty.</span><span class="sxs-lookup"><span data-stu-id="53811-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ToolBar> control and an <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="53811-107">Informace o nastavení takový projekt, naleznete v tématu [jak: Vytvoření projektu aplikace Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [jak: Přidání ovládacích prvků Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="53811-107">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53811-108">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="53811-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="53811-109">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="53811-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="53811-110">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="53811-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a><span data-ttu-id="53811-111">Chcete-li nastavit ikonu pro tlačítko panelu nástrojů v době návrhu</span><span class="sxs-lookup"><span data-stu-id="53811-111">To set an icon for a toolbar button at design time</span></span>  
  
1. <span data-ttu-id="53811-112">Přidání obrázků do <xref:System.Windows.Forms.ImageList> komponenty.</span><span class="sxs-lookup"><span data-stu-id="53811-112">Add images to the <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="53811-113">Další informace najdete v tématu [jak: Přidávání a odebírání obrázků ImageList pomocí návrháře](how-to-add-or-remove-imagelist-images-with-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="53811-113">For more information, see [How to: Add or Remove ImageList Images with the Designer](how-to-add-or-remove-imagelist-images-with-the-designer.md).</span></span>  
  
2. <span data-ttu-id="53811-114">Vyberte <xref:System.Windows.Forms.ToolBar> ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="53811-114">Select the <xref:System.Windows.Forms.ToolBar> control on your form.</span></span>  
  
3. <span data-ttu-id="53811-115">V **vlastnosti** okno, nastaveno <xref:System.Windows.Forms.ToolBar> ovládacího prvku <xref:System.Windows.Forms.ToolBar.ImageList%2A> vlastnost <xref:System.Windows.Forms.ImageList> komponenty.</span><span class="sxs-lookup"><span data-stu-id="53811-115">In the **Properties** window, set the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.ImageList%2A> property to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
4. <span data-ttu-id="53811-116">Klikněte na tlačítko <xref:System.Windows.Forms.ToolBar> ovládacího prvku <xref:System.Windows.Forms.ToolBar.Buttons%2A> vlastnost vyberte ho a klikněte na tlačítko se třemi tečkami (![snímek obrazovky VisualStudioEllipsesButton](../media/vbellipsesbutton.png "vbEllipsesButton")) tlačítko Otevřít **Editor kolekce ToolBarButton**.</span><span class="sxs-lookup"><span data-stu-id="53811-116">Click the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.Buttons%2A> property to select it, and click the ellipsis (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **ToolBarButton Collection Editor**.</span></span>  
  
5. <span data-ttu-id="53811-117">Použití **přidat** tlačítko pro přidání tlačítka <xref:System.Windows.Forms.ToolBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="53811-117">Use the **Add** button to add buttons to the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
6. <span data-ttu-id="53811-118">V **vlastnosti** okno, které se zobrazí v podokně na pravé straně **Editor kolekce ToolBarButton**, nastavte <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> vlastnost tlačítko panelu nástrojů na jednu z hodnot v seznamu, který přenesou z imagí, které jste přidali do <xref:System.Windows.Forms.ImageList> komponenty.</span><span class="sxs-lookup"><span data-stu-id="53811-118">In the **Properties** window that appears in the pane on the right side of the **ToolBarButton Collection Editor**, set the <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> property of each toolbar button to one of the values in the list, which is drawn from the images you added to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53811-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53811-119">See also</span></span>

- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="53811-120">Postupy: Aktivační události nabídky pro tlačítka panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="53811-120">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [<span data-ttu-id="53811-121">Ovládací prvek ToolBar</span><span class="sxs-lookup"><span data-stu-id="53811-121">ToolBar Control</span></span>](toolbar-control-windows-forms.md)
- [<span data-ttu-id="53811-122">Komponenta ImageList</span><span class="sxs-lookup"><span data-stu-id="53811-122">ImageList Component</span></span>](imagelist-component-windows-forms.md)
