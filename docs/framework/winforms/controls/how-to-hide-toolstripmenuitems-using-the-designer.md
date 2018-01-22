---
title: "Postupy: Skrývání ToolStripMenuItems pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 06a95581e156a7027c8fa0bda6e5fbc4babdb85b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="703f1-102">Postupy: Skrývání ToolStripMenuItems pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="703f1-102">How to: Hide ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="703f1-103">Skrytí položek nabídky je způsob, jak řídit uživatelské rozhraní (UI) vaší aplikace a omezit uživatele příkazy.</span><span class="sxs-lookup"><span data-stu-id="703f1-103">Hiding menu items is a way to control the user interface (UI) of your application and restrict user commands.</span></span> <span data-ttu-id="703f1-104">Často můžete skrýt celou nabídku, když jsou všechny položky nabídky na něm není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="703f1-104">Often, you will want to hide an entire menu when all of the menu items on it are unavailable.</span></span> <span data-ttu-id="703f1-105">To představuje rušeni pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="703f1-105">This presents fewer distractions for the user.</span></span> <span data-ttu-id="703f1-106">Kromě toho můžete chtít skrýt i zakázat nabídka nebo položka nabídky, jak skrytí samostatně nezabrání uživatel přístup k příkazu nabídky pomocí klávesové zkratky.</span><span class="sxs-lookup"><span data-stu-id="703f1-106">Furthermore, you might want to both hide and disable the menu or menu item, as hiding alone does not prevent the user from accessing a menu command by using a shortcut key.</span></span> <span data-ttu-id="703f1-107">Další informace o deaktivace položek nabídky najdete v tématu [postupy: zákaz ToolStripMenuItems pomocí návrháře](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="703f1-107">For more information on disabling menu items, see [How to: Disable ToolStripMenuItems Using the Designer](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="703f1-108">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="703f1-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="703f1-109">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="703f1-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="703f1-110">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="703f1-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a><span data-ttu-id="703f1-111">Chcete-li skrýt nabídek nejvyšší úrovně a jeho dílčí položky</span><span class="sxs-lookup"><span data-stu-id="703f1-111">To hide a top-level menu and its submenu items</span></span>  
  
1.  <span data-ttu-id="703f1-112">Vyberte položku nabídky nejvyšší úrovně a nastavit jeho <xref:System.Windows.Forms.ToolStripItem.Visible%2A> nebo <xref:System.Windows.Forms.ToolStripItem.Available%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="703f1-112">Select the top-level menu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> or <xref:System.Windows.Forms.ToolStripItem.Available%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="703f1-113">Skrytí položek nabídky nejvyšší úrovně, všechny položky nabídky v rámci této nabídky jsou rovněž skryté.</span><span class="sxs-lookup"><span data-stu-id="703f1-113">When you hide the top-level menu item, all menu items within that menu are also hidden.</span></span> <span data-ttu-id="703f1-114">Pokud kliknete na jiném zařízení, než na <xref:System.Windows.Forms.MenuStrip> po nastavení <xref:System.Windows.Forms.ToolStripItem.Visible%2A> k `false`, zmizí ze svého formuláře, což ukazuje spuštění účinku akci celý nabídka nejvyšší úrovně a jeho dílčí položky.</span><span class="sxs-lookup"><span data-stu-id="703f1-114">If you click somewhere other than on the <xref:System.Windows.Forms.MenuStrip> after setting <xref:System.Windows.Forms.ToolStripItem.Visible%2A> to `false`, the entire top-level menu item and its submenu items disappear from your form, thus showing you the run-time effect of your action.</span></span> <span data-ttu-id="703f1-115">Chcete-li zobrazit skrytá nabídka nejvyšší úrovně v době návrhu, klikněte na <xref:System.Windows.Forms.MenuStrip> v **komponent**v **Osnova dokumentu**, nebo v horní části mřížku vlastností.</span><span class="sxs-lookup"><span data-stu-id="703f1-115">To display the hidden top-level menu item at design time, click on the <xref:System.Windows.Forms.MenuStrip> in the **Component Tray**, in **Document Outline**, or at the top of the property grid.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="703f1-116">Občas bude skrýt celou nabídku s výjimkou několika nabídky podřízené ve scénáři slučovat dokumentu rozhraní (MDI).</span><span class="sxs-lookup"><span data-stu-id="703f1-116">You will rarely hide an entire menu except for multiple document interface (MDI) child menus in a merging scenario.</span></span>  
  
### <a name="to-hide-a-submenu-item"></a><span data-ttu-id="703f1-117">Chcete-li skrýt položku podnabídky</span><span class="sxs-lookup"><span data-stu-id="703f1-117">To hide a submenu item</span></span>  
  
1.  <span data-ttu-id="703f1-118">Vyberte položku podnabídky a nastavit jeho <xref:System.Windows.Forms.ToolStripItem.Visible%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="703f1-118">Select the submenu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="703f1-119">Skryjete položku podnabídky, zůstává viditelná ve formuláři v době návrhu tak, aby bylo možné snadno vybrat pro další práci.</span><span class="sxs-lookup"><span data-stu-id="703f1-119">When you hide a submenu item, it remains visible on your form at design time so that you can easily select it for further work.</span></span> <span data-ttu-id="703f1-120">Ve skutečnosti se bude skrytá za běhu.</span><span class="sxs-lookup"><span data-stu-id="703f1-120">It will actually be hidden at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="703f1-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="703f1-121">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripItem.Visible%2A>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>  
 <xref:System.Windows.Forms.ToolStripItem.Available%2A>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>  
 [<span data-ttu-id="703f1-122">Přehled ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="703f1-122">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="703f1-123">Postupy: Zákaz ToolStripMenuItems pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="703f1-123">How to: Disable ToolStripMenuItems Using the Designer</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md)
