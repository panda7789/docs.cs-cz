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
ms.openlocfilehash: da9a9d40529a1902c58f67d6a8696d8906eb34c9
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040064"
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol-using-the-designer"></a><span data-ttu-id="73085-102">Postupy: Přidávání a odebírání karet pomocí ovládacího prvku Windows Forms TabControl pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="73085-102">How to: Add and Remove Tabs with the Windows Forms TabControl Using the Designer</span></span>
<span data-ttu-id="73085-103">Když umístíte <xref:System.Windows.Forms.TabControl> ovládací prvek do formuláře, ve výchozím nastavení obsahuje dvě karty.</span><span class="sxs-lookup"><span data-stu-id="73085-103">When you place a <xref:System.Windows.Forms.TabControl> control on your form, it contains two tabs by default.</span></span> <span data-ttu-id="73085-104">Můžete přidat nebo odebrat karty pomocí návrháře.</span><span class="sxs-lookup"><span data-stu-id="73085-104">You can add or remove tabs using the designer.</span></span>

 <span data-ttu-id="73085-105">Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje <xref:System.Windows.Forms.TabControl> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="73085-105">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TabControl> control.</span></span> <span data-ttu-id="73085-106">Informace o nastavení takového projektu naleznete v tématu [How to: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms a [postupujte takto: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="73085-106">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-add-or-remove-a-tab-using-the-designer"></a><span data-ttu-id="73085-107">Přidání nebo odebrání karty pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="73085-107">To add or remove a tab using the designer</span></span>

- <span data-ttu-id="73085-108">Na inteligentní značce ovládacího prvku klikněte na **Přidat tabulátor** nebo **odebrat kartu** .</span><span class="sxs-lookup"><span data-stu-id="73085-108">On the control's smart tag, click **Add Tab** or **Remove Tab**</span></span>

     <span data-ttu-id="73085-109">-nebo-</span><span class="sxs-lookup"><span data-stu-id="73085-109">-or-</span></span>

     <span data-ttu-id="73085-110">V okně **vlastnosti** klikněte na tlačítko se **třemi** tečkami![(tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual](./media/visual-studio-ellipsis-button.png) <xref:System.Windows.Forms.TabControl.TabPages%2A> Studio.) vedle vlastnosti otevřete **Editor kolekce TabPage**.</span><span class="sxs-lookup"><span data-stu-id="73085-110">In the **Properties** window, click the **Ellipsis** button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.TabControl.TabPages%2A> property to open the **TabPage Collection Editor**.</span></span> <span data-ttu-id="73085-111">Klikněte na tlačítko **Přidat** nebo **Odebrat** .</span><span class="sxs-lookup"><span data-stu-id="73085-111">Click the **Add** or **Remove** button.</span></span>

## <a name="see-also"></a><span data-ttu-id="73085-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73085-112">See also</span></span>

- [<span data-ttu-id="73085-113">Ovládací prvek TabControl</span><span class="sxs-lookup"><span data-stu-id="73085-113">TabControl Control</span></span>](tabcontrol-control-windows-forms.md)
- [<span data-ttu-id="73085-114">Přehled ovládacího prvku TabControl</span><span class="sxs-lookup"><span data-stu-id="73085-114">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="73085-115">Postupy: Přidání ovládacího prvku na stránku karty</span><span class="sxs-lookup"><span data-stu-id="73085-115">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="73085-116">Postupy: Zakázat stránky karet</span><span class="sxs-lookup"><span data-stu-id="73085-116">How to: Disable Tab Pages</span></span>](how-to-disable-tab-pages.md)
- [<span data-ttu-id="73085-117">Postupy: Změna vzhledu model Windows Forms TabControl</span><span class="sxs-lookup"><span data-stu-id="73085-117">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
