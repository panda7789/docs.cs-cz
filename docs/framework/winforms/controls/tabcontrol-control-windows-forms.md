---
title: TabControl – ovládací prvek (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- TabControl control [Windows Forms]
- tab controls
- tab controls [Windows Forms], creating
- multipage dialog boxes
- dialog boxes [Windows Forms], creating multipage
- property pages [Windows Forms], creating
- tab dialog boxes
ms.assetid: 915091af-93ac-4d3d-8283-738dd2d21ea7
ms.openlocfilehash: 91a9930a3678e08fc0e46335f1eb95330bd171a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536758"
---
# <a name="tabcontrol-control-windows-forms"></a><span data-ttu-id="1a4de-102">TabControl – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="1a4de-102">TabControl Control (Windows Forms)</span></span>
<span data-ttu-id="1a4de-103">Windows Forms `TabControl` zobrazí několik karet, jako je rozdělení Poznámkový blok nebo popisků v sadě složek v souboru CAB podání.</span><span class="sxs-lookup"><span data-stu-id="1a4de-103">The Windows Forms `TabControl` displays multiple tabs, like dividers in a notebook or labels in a set of folders in a filing cabinet.</span></span> <span data-ttu-id="1a4de-104">Karty může obsahovat obrázky a jiných ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="1a4de-104">The tabs can contain pictures and other controls.</span></span> <span data-ttu-id="1a4de-105">Použití `TabControl` k vytvoření stránky vlastností.</span><span class="sxs-lookup"><span data-stu-id="1a4de-105">Use the `TabControl` to create property pages.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1a4de-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="1a4de-106">In This Section</span></span>  
 [<span data-ttu-id="1a4de-107">Přehled ovládacího prvku TabControl</span><span class="sxs-lookup"><span data-stu-id="1a4de-107">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 <span data-ttu-id="1a4de-108">Vysvětluje, co je tento ovládací prvek a jeho klíčové funkce a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1a4de-108">Explains what this control is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="1a4de-109">Postupy: Přidání ovládacího prvku na kartu</span><span class="sxs-lookup"><span data-stu-id="1a4de-109">How to: Add a Control to a Tab Page</span></span>](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 <span data-ttu-id="1a4de-110">Poskytuje pokyny pro zobrazení ovládacích prvků na kartě stránkách.</span><span class="sxs-lookup"><span data-stu-id="1a4de-110">Gives directions for displaying controls on tab pages.</span></span>  
  
 [<span data-ttu-id="1a4de-111">Postupy: Přidání a odebrání karet pomocí ovládacího prvku Windows Forms TabControl</span><span class="sxs-lookup"><span data-stu-id="1a4de-111">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)  
 <span data-ttu-id="1a4de-112">Poskytuje pokyny pro přidávání a odebírání karet v Návrháři nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="1a4de-112">Gives directions for adding and removing tabs in the designer or in code.</span></span>  
  
 [<span data-ttu-id="1a4de-113">Postupy: Změna vzhledu Windows Forms TabControl</span><span class="sxs-lookup"><span data-stu-id="1a4de-113">How to: Change the Appearance of the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)  
 <span data-ttu-id="1a4de-114">Poskytuje pokyny pro úpravu vlastností, které ovlivňují vzhled jednotlivé karty.</span><span class="sxs-lookup"><span data-stu-id="1a4de-114">Gives directions for adjusting properties that affect the appearance of individual tabs.</span></span>  
  
 [<span data-ttu-id="1a4de-115">Postupy: Zákaz karet</span><span class="sxs-lookup"><span data-stu-id="1a4de-115">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 <span data-ttu-id="1a4de-116">Vysvětluje, jak omezit přístup do stránky karty, případně založená na přihlašovací údaje uživatele.</span><span class="sxs-lookup"><span data-stu-id="1a4de-116">Explains how to restrict access to a tab page, possibly based on user credentials.</span></span>  
  
 <span data-ttu-id="1a4de-117">Viz také [postupy: Přidání a odebrání karty s Windows Forms TabControl pomocí návrháře](http://msdn.microsoft.com/library/ms233654\(v=vs.110\)), [postupy: Přidání ovládacího prvku na kartě stránky pomocí návrháře](http://msdn.microsoft.com/library/ms233668\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="1a4de-117">Also see [How to: Add and Remove Tabs with the Windows Forms TabControl Using the Designer](http://msdn.microsoft.com/library/ms233654\(v=vs.110\)), [How to: Add a Control to a Tab Page Using the Designer](http://msdn.microsoft.com/library/ms233668\(v=vs.110\))</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1a4de-118">Odkaz</span><span class="sxs-lookup"><span data-stu-id="1a4de-118">Reference</span></span>  
 <span data-ttu-id="1a4de-119"><xref:System.Windows.Forms.TabControl> – Třída</span><span class="sxs-lookup"><span data-stu-id="1a4de-119"><xref:System.Windows.Forms.TabControl> class</span></span>  
 <span data-ttu-id="1a4de-120">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="1a4de-120">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1a4de-121">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="1a4de-121">Related Sections</span></span>  
 [<span data-ttu-id="1a4de-122">Dialogová okna ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1a4de-122">Dialog Boxes in Windows Forms</span></span>](../../../../docs/framework/winforms/dialog-boxes-in-windows-forms.md)  
 <span data-ttu-id="1a4de-123">Poskytuje seznam úloh pro dialogová okna, které často zobrazení karet.</span><span class="sxs-lookup"><span data-stu-id="1a4de-123">Provides a list of tasks for dialog boxes, which often display tabs.</span></span>  
  
 [<span data-ttu-id="1a4de-124">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1a4de-124">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="1a4de-125">Poskytuje úplný seznam Windows Forms – ovládací prvky, odkazy na informace o jejich používání.</span><span class="sxs-lookup"><span data-stu-id="1a4de-125">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
