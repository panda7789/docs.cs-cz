---
title: 'Postupy: Přidávání a odebírání karet pomocí ovládacího prvku Windows Forms TabControl pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- tabs [Windows Forms], removing from pages
- TabPage control
- TabPage control [Windows Forms], adding and removing tabs
- tabs [Windows Forms], adding to pages
- tab pages
ms.assetid: 480633db-413a-45d2-9c8f-0427cc13adbe
ms.openlocfilehash: 23fe9fa2b8405a6ebe66e8f0cee1d81d45f2395b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219756"
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol-using-the-designer"></a><span data-ttu-id="ec5ce-102">Postupy: Přidávání a odebírání karet pomocí ovládacího prvku Windows Forms TabControl pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="ec5ce-102">How to: Add and Remove Tabs with the Windows Forms TabControl Using the Designer</span></span>
<span data-ttu-id="ec5ce-103">Když umístíte <xref:System.Windows.Forms.TabControl> ovládací prvek na formuláři, obsahuje dvě karty ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="ec5ce-103">When you place a <xref:System.Windows.Forms.TabControl> control on your form, it contains two tabs by default.</span></span> <span data-ttu-id="ec5ce-104">Můžete přidat nebo odebrat karty pomocí návrháře.</span><span class="sxs-lookup"><span data-stu-id="ec5ce-104">You can add or remove tabs using the designer.</span></span>  
  
 <span data-ttu-id="ec5ce-105">Následující postup vyžaduje, **aplikace Windows** projektu s formulář obsahující <xref:System.Windows.Forms.TabControl> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ec5ce-105">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TabControl> control.</span></span> <span data-ttu-id="ec5ce-106">Informace o nastavení takový projekt, naleznete v tématu [jak: Vytvoření projektu aplikace Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [jak: Přidání ovládacích prvků Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="ec5ce-106">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ec5ce-107">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="ec5ce-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="ec5ce-108">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="ec5ce-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="ec5ce-109">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="ec5ce-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-or-remove-a-tab-using-the-designer"></a><span data-ttu-id="ec5ce-110">Chcete-li přidat nebo odebrat kartu pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="ec5ce-110">To add or remove a tab using the designer</span></span>  
  
-   <span data-ttu-id="ec5ce-111">Na inteligentní značky ovládacího prvku, klikněte na tlačítko **přidat kartu** nebo **odebrat kartu**</span><span class="sxs-lookup"><span data-stu-id="ec5ce-111">On the control's smart tag, click **Add Tab** or **Remove Tab**</span></span>  
  
     <span data-ttu-id="ec5ce-112">-nebo-</span><span class="sxs-lookup"><span data-stu-id="ec5ce-112">-or-</span></span>  
  
     <span data-ttu-id="ec5ce-113">V **vlastnosti** okna, klikněte na tlačítko **tlačítko se třemi tečkami** tlačítko (![snímek obrazovky VisualStudioEllipsesButton](../media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.TabControl.TabPages%2A> vlastnosti otevřít **TabPage – Editor kolekce**.</span><span class="sxs-lookup"><span data-stu-id="ec5ce-113">In the **Properties** window, click the **Ellipsis** button (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.TabControl.TabPages%2A> property to open the **TabPage Collection Editor**.</span></span> <span data-ttu-id="ec5ce-114">Klikněte na tlačítko **přidat** nebo **odebrat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="ec5ce-114">Click the **Add** or **Remove** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec5ce-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec5ce-115">See also</span></span>

- [<span data-ttu-id="ec5ce-116">TabControl – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="ec5ce-116">TabControl Control</span></span>](tabcontrol-control-windows-forms.md)
- [<span data-ttu-id="ec5ce-117">Přehled ovládacího prvku TabControl</span><span class="sxs-lookup"><span data-stu-id="ec5ce-117">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="ec5ce-118">Postupy: Přidání ovládacího prvku na kartu</span><span class="sxs-lookup"><span data-stu-id="ec5ce-118">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="ec5ce-119">Postupy: Zakázání karet</span><span class="sxs-lookup"><span data-stu-id="ec5ce-119">How to: Disable Tab Pages</span></span>](how-to-disable-tab-pages.md)
- [<span data-ttu-id="ec5ce-120">Postupy: Změna vzhledu ovládacího prvku Windows Forms TabControl</span><span class="sxs-lookup"><span data-stu-id="ec5ce-120">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
