---
title: Přehled komponenty NotifyIcon
ms.date: 03/30/2017
f1_keywords:
- NotifyIcon
helpviewer_keywords:
- NotifyIcon component [Windows Forms], about NotifyIcon component
- system tray icons [Windows Forms], about system tray icons
- system tray icons [Windows Forms], using in Windows Forms
ms.assetid: 5b9189fa-d4ae-41a6-9b97-eb1f44bb1a69
ms.openlocfilehash: 587bf514db853f1122ed16abc05a195985c5ce8d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742122"
---
# <a name="notifyicon-component-overview-windows-forms"></a><span data-ttu-id="123ba-102">NotifyIcon – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="123ba-102">NotifyIcon Component Overview (Windows Forms)</span></span>

<span data-ttu-id="123ba-103">Komponenta model Windows Forms <xref:System.Windows.Forms.NotifyIcon> se obvykle používá k zobrazení ikon pro procesy, které běží na pozadí, a nezobrazuje uživatelské rozhraní mnohem v čase.</span><span class="sxs-lookup"><span data-stu-id="123ba-103">The Windows Forms <xref:System.Windows.Forms.NotifyIcon> component is typically used to display icons for processes that run in the background and do not show a user interface much of the time.</span></span> <span data-ttu-id="123ba-104">Příkladem může být program antivirové ochrany, ke kterému se dá dostat kliknutím na ikonu v oznamovací oblasti pro stav hlavního panelu.</span><span class="sxs-lookup"><span data-stu-id="123ba-104">An example would be a virus protection program that can be accessed by clicking an icon in the status notification area of the taskbar.</span></span>

## <a name="key-properties-of-notifyicons"></a><span data-ttu-id="123ba-105">Klíčové vlastnosti NotifyIcons</span><span class="sxs-lookup"><span data-stu-id="123ba-105">Key Properties of NotifyIcons</span></span>

<span data-ttu-id="123ba-106">Každá součást <xref:System.Windows.Forms.NotifyIcon> zobrazuje jednu ikonu v oblasti stavu.</span><span class="sxs-lookup"><span data-stu-id="123ba-106">Each <xref:System.Windows.Forms.NotifyIcon> component displays a single icon in the status area.</span></span> <span data-ttu-id="123ba-107">Pokud máte tři procesy na pozadí a chcete pro každou z nich zobrazit ikonu, musíte do formuláře přidat tři součásti <xref:System.Windows.Forms.NotifyIcon>.</span><span class="sxs-lookup"><span data-stu-id="123ba-107">If you have three background processes and wish to display an icon for each, you must add three <xref:System.Windows.Forms.NotifyIcon> components to the form.</span></span> <span data-ttu-id="123ba-108">Klíčové vlastnosti součásti <xref:System.Windows.Forms.NotifyIcon> jsou <xref:System.Windows.Forms.NotifyIcon.Icon%2A> a <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.</span><span class="sxs-lookup"><span data-stu-id="123ba-108">The key properties of the <xref:System.Windows.Forms.NotifyIcon> component are <xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.</span></span> <span data-ttu-id="123ba-109">Vlastnost <xref:System.Windows.Forms.NotifyIcon.Icon%2A> nastaví ikonu, která se zobrazí v oblasti stavu.</span><span class="sxs-lookup"><span data-stu-id="123ba-109">The <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property sets the icon that appears in the status area.</span></span> <span data-ttu-id="123ba-110">Aby se ikona zobrazila, musí být vlastnost <xref:System.Windows.Forms.NotifyIcon.Visible%2A> nastavena na hodnotu `true`.</span><span class="sxs-lookup"><span data-stu-id="123ba-110">In order for the icon to appear, the <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property must be set to `true`.</span></span>

## <a name="notifyicons-options"></a><span data-ttu-id="123ba-111">NotifyIcons možnosti</span><span class="sxs-lookup"><span data-stu-id="123ba-111">NotifyIcons Options</span></span>

<span data-ttu-id="123ba-112">Pomocí <xref:System.Windows.Forms.NotifyIcon> můžete přidružit tipy k bublinám, místní nabídky a popisy tlačítek, které budou uživateli pomáhat.</span><span class="sxs-lookup"><span data-stu-id="123ba-112">You can associate balloon tips, shortcut menus, and ToolTips with a <xref:System.Windows.Forms.NotifyIcon> to assist the user.</span></span>

<span data-ttu-id="123ba-113">Můžete zobrazit tipy v bublinách pro <xref:System.Windows.Forms.NotifyIcon> voláním metody <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> určující časový rozsah, ve kterém chcete zobrazit tip v bublině.</span><span class="sxs-lookup"><span data-stu-id="123ba-113">You can display balloon tips for a <xref:System.Windows.Forms.NotifyIcon> by calling the <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> method specifying the time span you wish the balloon tip to display.</span></span> <span data-ttu-id="123ba-114">Můžete také zadat text, ikonu a název tipu v bublině s <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> a <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="123ba-114">You can also specify the text, icon and title of the balloon tip with the <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> and <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>, respectively.</span></span> <span data-ttu-id="123ba-115">komponenty <xref:System.Windows.Forms.NotifyIcon> mohou mít také přidružené popisy a místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="123ba-115"><xref:System.Windows.Forms.NotifyIcon> components can also have associated ToolTips and shortcut menus.</span></span> <span data-ttu-id="123ba-116">Další informace najdete v tématu [Přehled komponent popisu](tooltip-component-overview-windows-forms.md) a informování [komponent](contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="123ba-116">For more information, see [ToolTip Component Overview](tooltip-component-overview-windows-forms.md) and [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="123ba-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="123ba-117">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- [<span data-ttu-id="123ba-118">Komponenta NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="123ba-118">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
