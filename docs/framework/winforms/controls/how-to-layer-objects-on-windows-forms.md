---
title: 'Postupy: Vrstvení objektů ve formulářích Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, layering
- controls [Windows Forms], layering
- z order
- controls [Windows Forms], positioning
- z-order
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
ms.openlocfilehash: d67d9b204c316dce5f3818496d791ed4c1b352f2
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45589453"
---
# <a name="how-to-layer-objects-on-windows-forms"></a><span data-ttu-id="609a7-102">Postupy: Vrstvení objektů ve formulářích Windows</span><span class="sxs-lookup"><span data-stu-id="609a7-102">How to: Layer Objects on Windows Forms</span></span>
<span data-ttu-id="609a7-103">Při vytváření složitých uživatelského rozhraní nebo pracovat s více formulář dokumentu (MDI interface), budete často vrstvy ovládací prvky a podřízené formuláře, chcete-li vytvořit složitější uživatelská rozhraní (UI).</span><span class="sxs-lookup"><span data-stu-id="609a7-103">When you create a complex user interface, or work with a multiple document interface (MDI) form, you will often want to layer both controls and child forms to create more complex user interfaces (UI).</span></span> <span data-ttu-id="609a7-104">Přesunout a mějte přehled o ovládací prvky a windows v rámci skupiny, manipulaci s jejich pořadí vykreslování.</span><span class="sxs-lookup"><span data-stu-id="609a7-104">To move and keep track of controls and windows within the context of a group, you manipulate their z-order.</span></span> <span data-ttu-id="609a7-105">*Pořadí vykreslování* je vizuální rozvržení ovládací prvky ve formuláři podél osy z formuláře (hloubku).</span><span class="sxs-lookup"><span data-stu-id="609a7-105">*Z-order* is the visual layering of controls on a form along the form's z-axis (depth).</span></span> <span data-ttu-id="609a7-106">V horní části pořadí vykreslování okna se překrývá všech ostatních oken.</span><span class="sxs-lookup"><span data-stu-id="609a7-106">The window at the top of the z-order overlaps all other windows.</span></span> <span data-ttu-id="609a7-107">Všechny ostatní okna překrývat okno v dolní části pořadí vykreslování.</span><span class="sxs-lookup"><span data-stu-id="609a7-107">All other windows overlap the window at the bottom of the z-order.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="609a7-108">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="609a7-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="609a7-109">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="609a7-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="609a7-110">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="609a7-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-layer-controls-at-design-time"></a><span data-ttu-id="609a7-111">K ovládacím prvkům vrstvy v době návrhu</span><span class="sxs-lookup"><span data-stu-id="609a7-111">To layer controls at design time</span></span>  
  
1.  <span data-ttu-id="609a7-112">Vyberte ovládací prvek, který chcete vrstvy.</span><span class="sxs-lookup"><span data-stu-id="609a7-112">Select a control that you want to layer.</span></span>  
  
2.  <span data-ttu-id="609a7-113">Na **formátu** nabídky, přejděte k **pořadí**a potom klikněte na tlačítko **přenést dopředu** nebo **odeslat zpět**.</span><span class="sxs-lookup"><span data-stu-id="609a7-113">On the **Format** menu, point to **Order**, and then click **Bring To Front** or **Send To Back**.</span></span>  
  
### <a name="to-layer-controls-programmatically"></a><span data-ttu-id="609a7-114">Ovládací prvky vrstvy prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="609a7-114">To layer controls programmatically</span></span>  
  
-   <span data-ttu-id="609a7-115">Použití <xref:System.Windows.Forms.Control.BringToFront%2A> a <xref:System.Windows.Forms.Control.SendToBack%2A> metody pro manipulaci s pořadí vykreslování ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="609a7-115">Use the <xref:System.Windows.Forms.Control.BringToFront%2A> and <xref:System.Windows.Forms.Control.SendToBack%2A> methods to manipulate the z-order of the controls.</span></span>  
  
     <span data-ttu-id="609a7-116">Například pokud <xref:System.Windows.Forms.TextBox> ovládacího prvku, `txtFirstName`, je pod jiného ovládacího prvku a chcete mít v horní části, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="609a7-116">For example, if a <xref:System.Windows.Forms.TextBox> control, `txtFirstName`, is underneath another control and you want to have it on top, use the following code:</span></span>  
  
    ```vb  
    txtFirstName.BringToFront()  
    ```  
  
    ```csharp  
    txtFirstName.BringToFront();  
    ```  
  
    ```cpp  
    txtFirstName->BringToFront();  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="609a7-117">Podporuje formuláře Windows *používání kontejnerů ovládacích prvků*.</span><span class="sxs-lookup"><span data-stu-id="609a7-117">Windows Forms supports *control containment*.</span></span> <span data-ttu-id="609a7-118">Používání kontejnerů ovládacích prvků zahrnuje umístění celé řady kontrolních mechanismů v rámci nadřazeného ovládacího prvku, třeba počet <xref:System.Windows.Forms.RadioButton> ovládací prvky v rámci <xref:System.Windows.Forms.GroupBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="609a7-118">Control containment involves placing a number of controls within a containing control, such as a number of <xref:System.Windows.Forms.RadioButton> controls within a <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="609a7-119">Potom můžete vrstvy ovládací prvky v rámci nadřazeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="609a7-119">You can then layer the controls within the containing control.</span></span> <span data-ttu-id="609a7-120">Přesunutí skupinový rámeček přesune ovládací prvky, protože se nacházejí uvnitř.</span><span class="sxs-lookup"><span data-stu-id="609a7-120">Moving the group box moves the controls as well, because they are contained inside it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="609a7-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="609a7-121">See Also</span></span>  
 [<span data-ttu-id="609a7-122">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="609a7-122">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="609a7-123">Uspořádávání ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="609a7-123">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="609a7-124">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="609a7-124">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="609a7-125">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="609a7-125">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="609a7-126">Ovládací prvky Windows Forms podle funkce</span><span class="sxs-lookup"><span data-stu-id="609a7-126">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
