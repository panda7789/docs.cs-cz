---
title: ToolBar – ovládací prvek
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolBar control [Windows Forms]
ms.assetid: 6b40e9ce-6a7a-4784-bfc9-7f1d36b7462e
ms.openlocfilehash: 027c96bb49e9446244e4b08ba93c551ef043b3c0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735464"
---
# <a name="toolbar-control-windows-forms"></a><span data-ttu-id="1dfae-102">ToolBar – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="1dfae-102">ToolBar Control (Windows Forms)</span></span>
> [!NOTE]
> <span data-ttu-id="1dfae-103">Ovládací prvek <xref:System.Windows.Forms.ToolStrip> nahrazuje a přidává funkce do ovládacího prvku `ToolBar`; Nicméně ovládací prvek `ToolBar` se zachovává pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.</span><span class="sxs-lookup"><span data-stu-id="1dfae-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the `ToolBar` control; however, the `ToolBar` control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="1dfae-104">Ovládací prvek model Windows Forms `ToolBar` se ve formulářích používá jako ovládací panel, který zobrazuje řádek rozevíracích nabídek a tlačítek s rastrovými obrázky, které aktivují příkazy.</span><span class="sxs-lookup"><span data-stu-id="1dfae-104">The Windows Forms `ToolBar` control is used on forms as a control bar that displays a row of drop-down menus and bitmapped buttons that activate commands.</span></span> <span data-ttu-id="1dfae-105">Kliknutí na tlačítko na panelu nástrojů je tedy ekvivalentní k výběru příkazu nabídky.</span><span class="sxs-lookup"><span data-stu-id="1dfae-105">Thus, clicking a toolbar button is equivalent to choosing a menu command.</span></span> <span data-ttu-id="1dfae-106">Tlačítka se dají nakonfigurovat tak, aby se zobrazovala jako tlačítka pro vložení, rozevírací nabídky nebo oddělovače.</span><span class="sxs-lookup"><span data-stu-id="1dfae-106">The buttons can be configured to appear and behave as push buttons, drop-down menus, or separators.</span></span> <span data-ttu-id="1dfae-107">Panel nástrojů obvykle obsahuje tlačítka a nabídky, které odpovídají položkám v rámci struktury nabídky aplikace, a poskytuje tak rychlý přístup k nejčastěji používaným funkcím a příkazům aplikace.</span><span class="sxs-lookup"><span data-stu-id="1dfae-107">Typically, a toolbar contains buttons and menus that correspond to items in an application's menu structure, providing quick access to an application's most frequently used functions and commands.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1dfae-108">Vlastnost <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> ovládacího prvku `ToolBar` přebírá instanci třídy <xref:System.Windows.Forms.ContextMenu> jako referenci.</span><span class="sxs-lookup"><span data-stu-id="1dfae-108">The `ToolBar` control's <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> property takes an instance of the <xref:System.Windows.Forms.ContextMenu> class as a reference.</span></span> <span data-ttu-id="1dfae-109">Pečlivě zvažte odkaz, který předáte při implementaci tohoto tlačítka na panelech nástrojů ve vaší aplikaci, protože vlastnost akceptuje libovolný objekt, který dědí z třídy <xref:System.Windows.Forms.Menu>.</span><span class="sxs-lookup"><span data-stu-id="1dfae-109">Carefully consider the reference you pass when implementing this sort of button on toolbars in your application, as the property will accept any object that inherits from the <xref:System.Windows.Forms.Menu> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1dfae-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="1dfae-110">In This Section</span></span>  
 [<span data-ttu-id="1dfae-111">Přehled ovládacího prvku ToolBar</span><span class="sxs-lookup"><span data-stu-id="1dfae-111">ToolBar Control Overview</span></span>](toolbar-control-overview-windows-forms.md)  
 <span data-ttu-id="1dfae-112">Zavádí obecné koncepce ovládacího prvku `ToolBar`, který umožňuje navrhovat vlastní panely nástrojů, se kterými můžou uživatelé pracovat.</span><span class="sxs-lookup"><span data-stu-id="1dfae-112">Introduces the general concepts of the `ToolBar` control, which allows you to design custom toolbars that your users can work with.</span></span>  
  
 [<span data-ttu-id="1dfae-113">Postupy: Přidání tlačítek do ovládacího prvku ToolBar</span><span class="sxs-lookup"><span data-stu-id="1dfae-113">How to: Add Buttons to a ToolBar Control</span></span>](how-to-add-buttons-to-a-toolbar-control.md)  
 <span data-ttu-id="1dfae-114">Popisuje, jak přidat tlačítka do ovládacího prvku `ToolBar`.</span><span class="sxs-lookup"><span data-stu-id="1dfae-114">Describes how to add buttons to a `ToolBar` control.</span></span>  
  
 [<span data-ttu-id="1dfae-115">Postupy: Definování ikony pro tlačítko ToolBar</span><span class="sxs-lookup"><span data-stu-id="1dfae-115">How to: Define an Icon for a ToolBar Button</span></span>](how-to-define-an-icon-for-a-toolbar-button.md)  
 <span data-ttu-id="1dfae-116">Popisuje, jak zobrazit ikony v rámci tlačítek ovládacího prvku `ToolBar`.</span><span class="sxs-lookup"><span data-stu-id="1dfae-116">Describes how to display icons within a `ToolBar` control's buttons.</span></span>  
  
 [<span data-ttu-id="1dfae-117">Postupy: Spouštění událostí nabídky pro tlačítka panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="1dfae-117">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)  
 <span data-ttu-id="1dfae-118">Poskytuje pokyny k psaní kódu pro interpretaci, které tlačítko uživatel klikne v ovládacím prvku `ToolBar`.</span><span class="sxs-lookup"><span data-stu-id="1dfae-118">Gives directions on writing code to interpret which button the user clicks in a `ToolBar` control.</span></span>  
  
 <span data-ttu-id="1dfae-119">Viz také [Postupy: definování ikony pro tlačítko panelu nástrojů pomocí návrháře](how-to-define-an-icon-for-a-toolbar-button-using-the-designer.md), [Postupy: Přidání tlačítek do ovládacího prvku panelu nástrojů pomocí návrháře](how-to-add-buttons-to-a-toolbar-control-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="1dfae-119">Also see [How to: Define an Icon for a ToolBar Button Using the Designer](how-to-define-an-icon-for-a-toolbar-button-using-the-designer.md), [How to: Add Buttons to a ToolBar Control Using the Designer](how-to-add-buttons-to-a-toolbar-control-using-the-designer.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1dfae-120">Odkaz</span><span class="sxs-lookup"><span data-stu-id="1dfae-120">Reference</span></span>  
 <span data-ttu-id="1dfae-121"><xref:System.Windows.Forms.ToolBar> – třída</span><span class="sxs-lookup"><span data-stu-id="1dfae-121"><xref:System.Windows.Forms.ToolBar> class</span></span>  
 <span data-ttu-id="1dfae-122">Poskytuje referenční informace o třídě a jejích členech.</span><span class="sxs-lookup"><span data-stu-id="1dfae-122">Provides reference information on the class and its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1dfae-123">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="1dfae-123">Related Sections</span></span>  
 [<span data-ttu-id="1dfae-124">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1dfae-124">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="1dfae-125">Obsahuje úplný seznam model Windows Formsch ovládacích prvků s odkazy na informace o jejich použití.</span><span class="sxs-lookup"><span data-stu-id="1dfae-125">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>  
  
 [<span data-ttu-id="1dfae-126">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="1dfae-126">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)  
 <span data-ttu-id="1dfae-127">Popisuje panely nástrojů, které mohou hostovat nabídky, ovládací prvky a uživatelské ovládací prvky v aplikacích model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1dfae-127">Describes toolbars that can host menus, controls, and user controls in Windows Forms applications.</span></span>
