---
title: 'Postupy: Skrytí ToolStripMenuItems pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
ms.openlocfilehash: 0e1cd7d1868adabd4d3eec9510f6ee567ba3867d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966619"
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="b5cf0-102">Postupy: Skrytí ToolStripMenuItems pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="b5cf0-102">How to: Hide ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="b5cf0-103">Skrytím položek nabídky je způsob, jak řídit uživatelské rozhraní (UI) aplikace a omezit uživatelské příkazy.</span><span class="sxs-lookup"><span data-stu-id="b5cf0-103">Hiding menu items is a way to control the user interface (UI) of your application and restrict user commands.</span></span> <span data-ttu-id="b5cf0-104">Často budete chtít skrýt celou nabídku, pokud nejsou k dispozici všechny položky nabídky, které jsou v ní dostupné.</span><span class="sxs-lookup"><span data-stu-id="b5cf0-104">Often, you will want to hide an entire menu when all of the menu items on it are unavailable.</span></span> <span data-ttu-id="b5cf0-105">To představuje méně odvolání pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="b5cf0-105">This presents fewer distractions for the user.</span></span> <span data-ttu-id="b5cf0-106">Kromě toho můžete chtít skrýt a zakázat položku nabídky nebo nabídky, protože když je skryjete samostatně, nezabráníte uživateli v přístupu k příkazu nabídky pomocí klávesových zkratek.</span><span class="sxs-lookup"><span data-stu-id="b5cf0-106">Furthermore, you might want to both hide and disable the menu or menu item, as hiding alone does not prevent the user from accessing a menu command by using a shortcut key.</span></span> <span data-ttu-id="b5cf0-107">Další informace o zakázání položek nabídky naleznete v tématu [How to: Zakáže ToolStripMenuItems pomocí návrháře](how-to-disable-toolstripmenuitems-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="b5cf0-107">For more information on disabling menu items, see [How to: Disable ToolStripMenuItems Using the Designer](how-to-disable-toolstripmenuitems-using-the-designer.md).</span></span>

## <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a><span data-ttu-id="b5cf0-108">Skrytí nabídky nejvyšší úrovně a jejích položek podnabídky</span><span class="sxs-lookup"><span data-stu-id="b5cf0-108">To hide a top-level menu and its submenu items</span></span>

1. <span data-ttu-id="b5cf0-109">Vyberte položku nabídky nejvyšší úrovně a nastavte její <xref:System.Windows.Forms.ToolStripItem.Visible%2A> vlastnost `false`nebo <xref:System.Windows.Forms.ToolStripItem.Available%2A> .</span><span class="sxs-lookup"><span data-stu-id="b5cf0-109">Select the top-level menu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> or <xref:System.Windows.Forms.ToolStripItem.Available%2A> property to `false`.</span></span>

     <span data-ttu-id="b5cf0-110">Když skryjete položku nabídky nejvyšší úrovně, všechny položky nabídky v této nabídce jsou také skryté.</span><span class="sxs-lookup"><span data-stu-id="b5cf0-110">When you hide the top-level menu item, all menu items within that menu are also hidden.</span></span> <span data-ttu-id="b5cf0-111">Pokud kliknete někam jinam než na <xref:System.Windows.Forms.MenuStrip> nastavení po nastavení <xref:System.Windows.Forms.ToolStripItem.Visible%2A> na `false`, zobrazí se z formuláře celá položka nabídky nejvyšší úrovně a její položky podnabídky, takže se zobrazí efekt spuštění vaší akce.</span><span class="sxs-lookup"><span data-stu-id="b5cf0-111">If you click somewhere other than on the <xref:System.Windows.Forms.MenuStrip> after setting <xref:System.Windows.Forms.ToolStripItem.Visible%2A> to `false`, the entire top-level menu item and its submenu items disappear from your form, thus showing you the run-time effect of your action.</span></span> <span data-ttu-id="b5cf0-112">Chcete-li zobrazit skrytou položku nabídky nejvyšší úrovně v době návrhu, klikněte na <xref:System.Windows.Forms.MenuStrip> položku v **panelu komponenty**, v části **Osnova dokumentu**nebo v horní části mřížky vlastností.</span><span class="sxs-lookup"><span data-stu-id="b5cf0-112">To display the hidden top-level menu item at design time, click on the <xref:System.Windows.Forms.MenuStrip> in the **Component Tray**, in **Document Outline**, or at the top of the property grid.</span></span>

> [!NOTE]
> <span data-ttu-id="b5cf0-113">Celou nabídku s výjimkou podřízených nabídek rozhraní více dokumentů (MDI) ve scénáři sloučení budete skrývat zřídka.</span><span class="sxs-lookup"><span data-stu-id="b5cf0-113">You will rarely hide an entire menu except for multiple document interface (MDI) child menus in a merging scenario.</span></span>

## <a name="to-hide-a-submenu-item"></a><span data-ttu-id="b5cf0-114">Skrytí položky podnabídky</span><span class="sxs-lookup"><span data-stu-id="b5cf0-114">To hide a submenu item</span></span>

1. <span data-ttu-id="b5cf0-115">Vyberte položku podnabídky a nastavte její <xref:System.Windows.Forms.ToolStripItem.Visible%2A> vlastnost na `false`.</span><span class="sxs-lookup"><span data-stu-id="b5cf0-115">Select the submenu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property to `false`.</span></span>

     <span data-ttu-id="b5cf0-116">Když skryjete položku podnabídky, zůstane viditelná ve formuláři v době návrhu, takže ji můžete snadno vybrat pro další práci.</span><span class="sxs-lookup"><span data-stu-id="b5cf0-116">When you hide a submenu item, it remains visible on your form at design time so that you can easily select it for further work.</span></span> <span data-ttu-id="b5cf0-117">Ve skutečnosti bude v době běhu skrytá.</span><span class="sxs-lookup"><span data-stu-id="b5cf0-117">It will actually be hidden at run time.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5cf0-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5cf0-118">See also</span></span>

- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>
- <xref:System.Windows.Forms.ToolStripItem.Available%2A>
- <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>
- [<span data-ttu-id="b5cf0-119">Přehled ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="b5cf0-119">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
- [<span data-ttu-id="b5cf0-120">Postupy: Zakázat ToolStripMenuItems pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="b5cf0-120">How to: Disable ToolStripMenuItems Using the Designer</span></span>](how-to-disable-toolstripmenuitems-using-the-designer.md)
