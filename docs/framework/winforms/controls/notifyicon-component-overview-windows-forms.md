---
title: NotifyIcon – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- NotifyIcon
helpviewer_keywords:
- NotifyIcon component [Windows Forms], about NotifyIcon component
- system tray icons [Windows Forms], about system tray icons
- system tray icons [Windows Forms], using in Windows Forms
ms.assetid: 5b9189fa-d4ae-41a6-9b97-eb1f44bb1a69
ms.openlocfilehash: 430d869265b9add34c6de617a178aa27af6218f3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707622"
---
# <a name="notifyicon-component-overview-windows-forms"></a><span data-ttu-id="062ae-102">NotifyIcon – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="062ae-102">NotifyIcon Component Overview (Windows Forms)</span></span>

<span data-ttu-id="062ae-103">Windows Forms <xref:System.Windows.Forms.NotifyIcon> komponenty se obvykle používá k zobrazení ikon pro procesy, které běží na pozadí a nezobrazovat uživateli rozhraní většinu času.</span><span class="sxs-lookup"><span data-stu-id="062ae-103">The Windows Forms <xref:System.Windows.Forms.NotifyIcon> component is typically used to display icons for processes that run in the background and do not show a user interface much of the time.</span></span> <span data-ttu-id="062ae-104">Příkladem může být program antivirové ochrany, který je přístupný kliknutím na ikonu v oznamovací oblasti na hlavním panelu Stav.</span><span class="sxs-lookup"><span data-stu-id="062ae-104">An example would be a virus protection program that can be accessed by clicking an icon in the status notification area of the taskbar.</span></span>

## <a name="key-properties-of-notifyicons"></a><span data-ttu-id="062ae-105">Klíčové vlastnosti NotifyIcons</span><span class="sxs-lookup"><span data-stu-id="062ae-105">Key Properties of NotifyIcons</span></span>

<span data-ttu-id="062ae-106">Každý <xref:System.Windows.Forms.NotifyIcon> komponenty zobrazí jedna ikona v oblasti stavu.</span><span class="sxs-lookup"><span data-stu-id="062ae-106">Each <xref:System.Windows.Forms.NotifyIcon> component displays a single icon in the status area.</span></span> <span data-ttu-id="062ae-107">Pokud budete mít tři procesy na pozadí a chcete zobrazit ikonu pro každou, je třeba přidat tři <xref:System.Windows.Forms.NotifyIcon> komponenty do formuláře.</span><span class="sxs-lookup"><span data-stu-id="062ae-107">If you have three background processes and wish to display an icon for each, you must add three <xref:System.Windows.Forms.NotifyIcon> components to the form.</span></span> <span data-ttu-id="062ae-108">Klíčové vlastnosti <xref:System.Windows.Forms.NotifyIcon> komponenty jsou <xref:System.Windows.Forms.NotifyIcon.Icon%2A> a <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.</span><span class="sxs-lookup"><span data-stu-id="062ae-108">The key properties of the <xref:System.Windows.Forms.NotifyIcon> component are <xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.</span></span> <span data-ttu-id="062ae-109"><xref:System.Windows.Forms.NotifyIcon.Icon%2A> Vlastnost nastaví na ikonu, která se zobrazí v oblasti stavu.</span><span class="sxs-lookup"><span data-stu-id="062ae-109">The <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property sets the icon that appears in the status area.</span></span> <span data-ttu-id="062ae-110">Aby se na ikonu se zobrazí <xref:System.Windows.Forms.NotifyIcon.Visible%2A> musí být vlastnost nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="062ae-110">In order for the icon to appear, the <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property must be set to `true`.</span></span>

## <a name="notifyicons-options"></a><span data-ttu-id="062ae-111">Možnosti NotifyIcons</span><span class="sxs-lookup"><span data-stu-id="062ae-111">NotifyIcons Options</span></span>

<span data-ttu-id="062ae-112">Můžete přidružit tipy, místní nabídky a popisy tlačítek s <xref:System.Windows.Forms.NotifyIcon> pomáhat uživatele.</span><span class="sxs-lookup"><span data-stu-id="062ae-112">You can associate balloon tips, shortcut menus, and ToolTips with a <xref:System.Windows.Forms.NotifyIcon> to assist the user.</span></span>

<span data-ttu-id="062ae-113">Můžete zobrazit tipy pro <xref:System.Windows.Forms.NotifyIcon> voláním <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> metoda určující časový interval, které chcete zobrazení tipu v bublině zobrazíte.</span><span class="sxs-lookup"><span data-stu-id="062ae-113">You can display balloon tips for a <xref:System.Windows.Forms.NotifyIcon> by calling the <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> method specifying the time span you wish the balloon tip to display.</span></span> <span data-ttu-id="062ae-114">Můžete také zadat text, ikona a záhlaví zobrazení tipu v bublině s <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> a <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="062ae-114">You can also specify the text, icon and title of the balloon tip with the <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> and <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>, respectively.</span></span> <span data-ttu-id="062ae-115"><xref:System.Windows.Forms.NotifyIcon> součásti můžete mít také související popisy tlačítek a místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="062ae-115"><xref:System.Windows.Forms.NotifyIcon> components can also have associated ToolTips and shortcut menus.</span></span> <span data-ttu-id="062ae-116">Další informace najdete v tématu [ToolTip – přehled komponenty](tooltip-component-overview-windows-forms.md) a [ContextMenu – přehled komponenty](contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="062ae-116">For more information, see [ToolTip Component Overview](tooltip-component-overview-windows-forms.md) and [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="062ae-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="062ae-117">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- [<span data-ttu-id="062ae-118">Komponenta NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="062ae-118">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)