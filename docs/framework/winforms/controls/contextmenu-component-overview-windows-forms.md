---
title: "ContextMenu – přehled komponenty (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ContextMenu
helpviewer_keywords:
- ContextMenu component [Windows Forms], about ContextMenu component
- context menus [Windows Forms], ContextMenu component
- shortcut menus [Windows Forms], ContextMenu component
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b0db67e8da97f380c3bb2eb9aab951628c4b6487
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="contextmenu-component-overview-windows-forms"></a><span data-ttu-id="191fe-102">ContextMenu – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="191fe-102">ContextMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="191fe-103">I když <xref:System.Windows.Forms.MenuStrip> a <xref:System.Windows.Forms.ContextMenuStrip> nahradit a přidání funkce do <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> ovládací prvky předchozí verze, <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> se zachovají pro zpětnou kompatibilitu a budoucí použití, pokud si zvolíte.</span><span class="sxs-lookup"><span data-stu-id="191fe-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="191fe-104">S Windows Forms <xref:System.Windows.Forms.ContextMenu> součásti, můžete poskytnout uživatelům snadno dostupný místní nabídce často používané příkazy, které jsou přidruženy vybraný objekt.</span><span class="sxs-lookup"><span data-stu-id="191fe-104">With the Windows Forms <xref:System.Windows.Forms.ContextMenu> component, you can provide users with an easily accessible shortcut menu of frequently used commands that are associated with the selected object.</span></span> <span data-ttu-id="191fe-105">Položky v místní nabídce jsou často podmnožinou položky z hlavní nabídky, které se zobrazují jinde v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="191fe-105">The items in a shortcut menu are frequently a subset of the items from main menus that appear elsewhere in the application.</span></span> <span data-ttu-id="191fe-106">Místní nabídky moct uživatel přistupovat obvykle kliknutím pravým tlačítkem myši.</span><span class="sxs-lookup"><span data-stu-id="191fe-106">A user can typically access a shortcut menu by right-clicking the mouse.</span></span> <span data-ttu-id="191fe-107">V rozhraní Windows Forms jsou spojeny s ovládacími prvky místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="191fe-107">On Windows Forms, shortcut menus are associated with controls.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="191fe-108">Klíčové vlastnosti</span><span class="sxs-lookup"><span data-stu-id="191fe-108">Key Properties</span></span>  
 <span data-ttu-id="191fe-109">Místní nabídky můžete přidružit s ovládacím prvkem nastavením ovládacího prvku <xref:System.Windows.Forms.Control.ContextMenu%2A> vlastnost, která má <xref:System.Windows.Forms.ContextMenu> součásti.</span><span class="sxs-lookup"><span data-stu-id="191fe-109">You can associate a shortcut menu with a control by setting the control's <xref:System.Windows.Forms.Control.ContextMenu%2A> property to the <xref:System.Windows.Forms.ContextMenu> component.</span></span> <span data-ttu-id="191fe-110">Jeden místní nabídky může být přidružen více ovládacích prvků, ale každý ovládací prvek může mít pouze jeden místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="191fe-110">A single shortcut menu can be associated with multiple controls, but each control can have only one shortcut menu.</span></span>  
  
 <span data-ttu-id="191fe-111">Klíčové vlastnosti <xref:System.Windows.Forms.ContextMenu> součást je <xref:System.Windows.Forms.Menu.MenuItems%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="191fe-111">The key property of the <xref:System.Windows.Forms.ContextMenu> component is the <xref:System.Windows.Forms.Menu.MenuItems%2A> property.</span></span> <span data-ttu-id="191fe-112">Položky nabídky můžete přidat prostřednictvím kódu programu vytvořením <xref:System.Windows.Forms.MenuItem> objekty a jejich přidání <xref:System.Windows.Forms.Menu.MenuItemCollection> z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="191fe-112">You can add menu items by programmatically creating <xref:System.Windows.Forms.MenuItem> objects and adding them to the <xref:System.Windows.Forms.Menu.MenuItemCollection> of the shortcut menu.</span></span> <span data-ttu-id="191fe-113">Protože položky v místní nabídce jsou obvykle čerpají z jiných nabídek, budou nejčastěji přidejte položky do místní nabídky zkopírováním.</span><span class="sxs-lookup"><span data-stu-id="191fe-113">Because the items in a shortcut menu are usually drawn from other menus, you will most frequently add items to a shortcut menu by copying them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="191fe-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="191fe-114">See Also</span></span>  
 <xref:System.Windows.Forms.ContextMenu>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>
