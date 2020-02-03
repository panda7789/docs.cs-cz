---
title: TabControl – ovládací prvek
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
ms.openlocfilehash: c4f310629342e5302021bbc7dc5f92d473377397
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742814"
---
# <a name="tabcontrol-control-windows-forms"></a><span data-ttu-id="e2693-102">TabControl – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="e2693-102">TabControl Control (Windows Forms)</span></span>
<span data-ttu-id="e2693-103">`TabControl` model Windows Forms zobrazí více karet, jako jsou například oddělovače v poznámkovém bloku nebo štítky v sadě složek v kartotéce.</span><span class="sxs-lookup"><span data-stu-id="e2693-103">The Windows Forms `TabControl` displays multiple tabs, like dividers in a notebook or labels in a set of folders in a filing cabinet.</span></span> <span data-ttu-id="e2693-104">Karty mohou obsahovat obrázky a další ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="e2693-104">The tabs can contain pictures and other controls.</span></span> <span data-ttu-id="e2693-105">Stránky vlastností můžete vytvořit pomocí `TabControl`.</span><span class="sxs-lookup"><span data-stu-id="e2693-105">Use the `TabControl` to create property pages.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e2693-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="e2693-106">In This Section</span></span>  
 [<span data-ttu-id="e2693-107">Přehled ovládacího prvku TabControl</span><span class="sxs-lookup"><span data-stu-id="e2693-107">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)  
 <span data-ttu-id="e2693-108">Vysvětluje, co je tento ovládací prvek a jeho klíčové funkce a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e2693-108">Explains what this control is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="e2693-109">Postupy: Přidání ovládacího prvku na kartu</span><span class="sxs-lookup"><span data-stu-id="e2693-109">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)  
 <span data-ttu-id="e2693-110">Poskytuje pokyny pro zobrazení ovládacích prvků na stránkách karet.</span><span class="sxs-lookup"><span data-stu-id="e2693-110">Gives directions for displaying controls on tab pages.</span></span>  
  
 [<span data-ttu-id="e2693-111">Postupy: Přidání a odebrání karet pomocí ovládacího prvku Windows Forms TabControl</span><span class="sxs-lookup"><span data-stu-id="e2693-111">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)  
 <span data-ttu-id="e2693-112">Poskytuje pokyny pro přidání a odebrání karet v Návrháři nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="e2693-112">Gives directions for adding and removing tabs in the designer or in code.</span></span>  
  
 [<span data-ttu-id="e2693-113">Postupy: Změna vzhledu Windows Forms TabControl</span><span class="sxs-lookup"><span data-stu-id="e2693-113">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)  
 <span data-ttu-id="e2693-114">Poskytuje pokyny pro úpravu vlastností, které ovlivňují vzhled jednotlivých karet.</span><span class="sxs-lookup"><span data-stu-id="e2693-114">Gives directions for adjusting properties that affect the appearance of individual tabs.</span></span>  
  
 [<span data-ttu-id="e2693-115">Postupy: Zákaz karet</span><span class="sxs-lookup"><span data-stu-id="e2693-115">How to: Disable Tab Pages</span></span>](how-to-disable-tab-pages.md)  
 <span data-ttu-id="e2693-116">Vysvětluje, jak omezit přístup na stránku karet, případně na základě přihlašovacích údajů uživatele.</span><span class="sxs-lookup"><span data-stu-id="e2693-116">Explains how to restrict access to a tab page, possibly based on user credentials.</span></span>  
  
 <span data-ttu-id="e2693-117">Viz také [Postupy: Přidání a odebrání karet pomocí model Windows Forms TabControl pomocí návrháře](add-and-remove-tabs-with-wf-tabcontrol-using-the-designer.md), [Postupy: Přidání ovládacího prvku na stránku karty pomocí návrháře](how-to-add-a-control-to-a-tab-page-using-the-designer.md)</span><span class="sxs-lookup"><span data-stu-id="e2693-117">Also see [How to: Add and Remove Tabs with the Windows Forms TabControl Using the Designer](add-and-remove-tabs-with-wf-tabcontrol-using-the-designer.md), [How to: Add a Control to a Tab Page Using the Designer](how-to-add-a-control-to-a-tab-page-using-the-designer.md)</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e2693-118">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="e2693-118">Reference</span></span>  
 <span data-ttu-id="e2693-119">Třída <xref:System.Windows.Forms.TabControl></span><span class="sxs-lookup"><span data-stu-id="e2693-119"><xref:System.Windows.Forms.TabControl> class</span></span>  
 <span data-ttu-id="e2693-120">Popisuje tuto třídu a má odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="e2693-120">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e2693-121">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="e2693-121">Related Sections</span></span>  
 [<span data-ttu-id="e2693-122">Dialogová okna ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e2693-122">Dialog Boxes in Windows Forms</span></span>](../dialog-boxes-in-windows-forms.md)  
 <span data-ttu-id="e2693-123">Poskytuje seznam úloh pro dialogová okna, která často zobrazují karty.</span><span class="sxs-lookup"><span data-stu-id="e2693-123">Provides a list of tasks for dialog boxes, which often display tabs.</span></span>  
  
 [<span data-ttu-id="e2693-124">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e2693-124">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="e2693-125">Obsahuje úplný seznam model Windows Formsch ovládacích prvků s odkazy na informace o jejich použití.</span><span class="sxs-lookup"><span data-stu-id="e2693-125">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
