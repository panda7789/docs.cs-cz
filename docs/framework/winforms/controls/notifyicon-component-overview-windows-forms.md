---
title: "NotifyIcon – přehled komponenty (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: NotifyIcon
helpviewer_keywords:
- NotifyIcon component [Windows Forms], about NotifyIcon component
- system tray icons [Windows Forms], about system tray icons
- system tray icons [Windows Forms], using in Windows Forms
ms.assetid: 5b9189fa-d4ae-41a6-9b97-eb1f44bb1a69
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d951d45232437026cc41d8e40284207ea1c64ab9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="notifyicon-component-overview-windows-forms"></a><span data-ttu-id="ebcbf-102">NotifyIcon – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="ebcbf-102">NotifyIcon Component Overview (Windows Forms)</span></span>
<span data-ttu-id="ebcbf-103">Windows Forms <xref:System.Windows.Forms.NotifyIcon> součást se obvykle používá pro zobrazení ikon pro procesy, které běží na pozadí a nezobrazovat uživateli rozhraní většinu času.</span><span class="sxs-lookup"><span data-stu-id="ebcbf-103">The Windows Forms <xref:System.Windows.Forms.NotifyIcon> component is typically used to display icons for processes that run in the background and do not show a user interface much of the time.</span></span> <span data-ttu-id="ebcbf-104">Příkladem může být antivirový program, můžete dostat kliknutím na ikonu v oznamovací oblasti stav na hlavním panelu.</span><span class="sxs-lookup"><span data-stu-id="ebcbf-104">An example would be a virus protection program that can be accessed by clicking an icon in the status notification area of the taskbar.</span></span>  
  
## <a name="key-properties-of-notifyicons"></a><span data-ttu-id="ebcbf-105">Klíčové vlastnosti NotifyIcons</span><span class="sxs-lookup"><span data-stu-id="ebcbf-105">Key Properties of NotifyIcons</span></span>  
 <span data-ttu-id="ebcbf-106">Každý <xref:System.Windows.Forms.NotifyIcon> součást zobrazí jeden ikonu na stavovém řádku.</span><span class="sxs-lookup"><span data-stu-id="ebcbf-106">Each <xref:System.Windows.Forms.NotifyIcon> component displays a single icon in the status area.</span></span> <span data-ttu-id="ebcbf-107">Pokud máte tři procesy na pozadí a chcete zobrazit ikony pro každou, je třeba přidat tři <xref:System.Windows.Forms.NotifyIcon> komponenty do formuláře.</span><span class="sxs-lookup"><span data-stu-id="ebcbf-107">If you have three background processes and wish to display an icon for each, you must add three <xref:System.Windows.Forms.NotifyIcon> components to the form.</span></span> <span data-ttu-id="ebcbf-108">Klíčové vlastnosti <xref:System.Windows.Forms.NotifyIcon> jsou součástí <xref:System.Windows.Forms.NotifyIcon.Icon%2A> a <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.</span><span class="sxs-lookup"><span data-stu-id="ebcbf-108">The key properties of the <xref:System.Windows.Forms.NotifyIcon> component are <xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.</span></span> <span data-ttu-id="ebcbf-109"><xref:System.Windows.Forms.NotifyIcon.Icon%2A> Vlastnost nastaví na ikonu, který se zobrazí v oblasti stavu.</span><span class="sxs-lookup"><span data-stu-id="ebcbf-109">The <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property sets the icon that appears in the status area.</span></span> <span data-ttu-id="ebcbf-110">Aby se na ikonu se zobrazí <xref:System.Windows.Forms.NotifyIcon.Visible%2A> musí být nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="ebcbf-110">In order for the icon to appear, the <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property must be set to `true`.</span></span>  
  
 <span data-ttu-id="ebcbf-111">Pokud používáte [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], máte přístup k rozsáhlé knihovně standardní bitové kopie, které můžete použít s <xref:System.Windows.Forms.NotifyIcon> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ebcbf-111">If you are using [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], you have access to a large library of standard images that you can use with the <xref:System.Windows.Forms.NotifyIcon> control.</span></span>  
  
## <a name="notifyicons-options"></a><span data-ttu-id="ebcbf-112">Možnosti NotifyIcons</span><span class="sxs-lookup"><span data-stu-id="ebcbf-112">NotifyIcons Options</span></span>  
 <span data-ttu-id="ebcbf-113">Můžete přidružit tipech, místní nabídky a popisy tlačítek s <xref:System.Windows.Forms.NotifyIcon> pomůže uživatele.</span><span class="sxs-lookup"><span data-stu-id="ebcbf-113">You can associate balloon tips, shortcut menus, and ToolTips with a <xref:System.Windows.Forms.NotifyIcon> to assist the user.</span></span>  
  
 <span data-ttu-id="ebcbf-114">Můžete zobrazit tipy pro <xref:System.Windows.Forms.NotifyIcon> voláním <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> metoda zadat časový interval, které chcete bublinách tip pro zobrazení.</span><span class="sxs-lookup"><span data-stu-id="ebcbf-114">You can display balloon tips for a <xref:System.Windows.Forms.NotifyIcon> by calling the <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> method specifying the time span you wish the balloon tip to display.</span></span> <span data-ttu-id="ebcbf-115">Můžete také zadat text, ikona a název tipu bublinách s <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> a <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ebcbf-115">You can also specify the text, icon and title of the balloon tip with the <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> and <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>, respectively.</span></span> <span data-ttu-id="ebcbf-116"><xref:System.Windows.Forms.NotifyIcon>součásti může mít také přidružené popisy tlačítek a místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="ebcbf-116"><xref:System.Windows.Forms.NotifyIcon> components can also have associated ToolTips and shortcut menus.</span></span> <span data-ttu-id="ebcbf-117">Další informace najdete v tématu [ToolTip – přehled komponenty](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md) a [ContextMenu – přehled komponenty](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="ebcbf-117">For more information, see [ToolTip Component Overview](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md) and [ContextMenu Component Overview](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebcbf-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ebcbf-118">See Also</span></span>  
 <xref:System.Windows.Forms.NotifyIcon>  
 [<span data-ttu-id="ebcbf-119">NotifyIcon – komponenta</span><span class="sxs-lookup"><span data-stu-id="ebcbf-119">NotifyIcon Component</span></span>](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)
