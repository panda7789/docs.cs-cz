---
title: ToolBar – ovládací prvek (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolBar control [Windows Forms]
ms.assetid: 6b40e9ce-6a7a-4784-bfc9-7f1d36b7462e
ms.openlocfilehash: 8162dfc898f7965d65de918d2a5b1f7afbfdf9b2
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863280"
---
# <a name="toolbar-control-windows-forms"></a><span data-ttu-id="5a464-102">ToolBar – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="5a464-102">ToolBar Control (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="5a464-103"><xref:System.Windows.Forms.ToolStrip> Ovládací prvek nahradí a přidá funkce, které `ToolBar` řízení; však `ToolBar` ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete.</span><span class="sxs-lookup"><span data-stu-id="5a464-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the `ToolBar` control; however, the `ToolBar` control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="5a464-104">Windows Forms `ToolBar` ovládací prvek se používá ve formulářích jako ovládací panel, který zobrazuje řádek z rozevírací nabídky a tlačítek s rastrovými obrázky, které aktivovat příkazy.</span><span class="sxs-lookup"><span data-stu-id="5a464-104">The Windows Forms `ToolBar` control is used on forms as a control bar that displays a row of drop-down menus and bitmapped buttons that activate commands.</span></span> <span data-ttu-id="5a464-105">Kliknutím na tlačítko panelu nástrojů je tedy ekvivalentem možnosti vybrání příkazu nabídky.</span><span class="sxs-lookup"><span data-stu-id="5a464-105">Thus, clicking a toolbar button is equivalent to choosing a menu command.</span></span> <span data-ttu-id="5a464-106">Tlačítka lze nastavit na a chovají se jako tlačítek, rozevíracích nabídek nebo oddělovače.</span><span class="sxs-lookup"><span data-stu-id="5a464-106">The buttons can be configured to appear and behave as push buttons, drop-down menus, or separators.</span></span> <span data-ttu-id="5a464-107">Obvykle obsahuje panel nástrojů tlačítka a nabídky, které odpovídají položky nabídky struktury aplikace poskytuje rychlý přístup k aplikačním nejčastěji používané funkce a příkazy.</span><span class="sxs-lookup"><span data-stu-id="5a464-107">Typically, a toolbar contains buttons and menus that correspond to items in an application's menu structure, providing quick access to an application's most frequently used functions and commands.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a464-108">`ToolBar` Ovládacího prvku <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> vlastnost přebírá instanci <xref:System.Windows.Forms.ContextMenu> třídu jako odkaz.</span><span class="sxs-lookup"><span data-stu-id="5a464-108">The `ToolBar` control's <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> property takes an instance of the <xref:System.Windows.Forms.ContextMenu> class as a reference.</span></span> <span data-ttu-id="5a464-109">Pečlivě zvažte, předáte při implementaci tohoto druhu tlačítko na panely nástrojů v aplikaci jako vlastnost přijme některý objekt, který dědí z odkazu <xref:System.Windows.Forms.Menu> třídy.</span><span class="sxs-lookup"><span data-stu-id="5a464-109">Carefully consider the reference you pass when implementing this sort of button on toolbars in your application, as the property will accept any object that inherits from the <xref:System.Windows.Forms.Menu> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5a464-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="5a464-110">In This Section</span></span>  
 [<span data-ttu-id="5a464-111">Přehled ovládacího prvku ToolBar</span><span class="sxs-lookup"><span data-stu-id="5a464-111">ToolBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolbar-control-overview-windows-forms.md)  
 <span data-ttu-id="5a464-112">Představuje obecné koncepty `ToolBar` ovládací prvek, který vám umožní navrhnout vlastní panely nástrojů, které vaši uživatelé můžou pracovat s.</span><span class="sxs-lookup"><span data-stu-id="5a464-112">Introduces the general concepts of the `ToolBar` control, which allows you to design custom toolbars that your users can work with.</span></span>  
  
 [<span data-ttu-id="5a464-113">Postupy: Přidání tlačítek do ovládacího prvku ToolBar</span><span class="sxs-lookup"><span data-stu-id="5a464-113">How to: Add Buttons to a ToolBar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)  
 <span data-ttu-id="5a464-114">Popisuje postup přidání tlačítek `ToolBar` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5a464-114">Describes how to add buttons to a `ToolBar` control.</span></span>  
  
 [<span data-ttu-id="5a464-115">Postupy: Definování ikony pro tlačítko ToolBar</span><span class="sxs-lookup"><span data-stu-id="5a464-115">How to: Define an Icon for a ToolBar Button</span></span>](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 <span data-ttu-id="5a464-116">Popisuje, jak zobrazit ikony v rámci `ToolBar` ovládacího prvku tlačítka.</span><span class="sxs-lookup"><span data-stu-id="5a464-116">Describes how to display icons within a `ToolBar` control's buttons.</span></span>  
  
 [<span data-ttu-id="5a464-117">Postupy: Spouštění událostí nabídky pro tlačítka panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="5a464-117">How to: Trigger Menu Events for Toolbar Buttons</span></span>](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 <span data-ttu-id="5a464-118">Poskytuje pokyny s psaním kódu pro interpretaci, které uživatel tlačítko klikne do oblasti `ToolBar` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5a464-118">Gives directions on writing code to interpret which button the user clicks in a `ToolBar` control.</span></span>  
  
 <span data-ttu-id="5a464-119">Také naleznete v tématu [postupy: definování ikony pro panelu nástrojů tlačítko pomocí návrháře](how-to-define-an-icon-for-a-toolbar-button-using-the-designer.md), [postupy: Přidání tlačítka na panelu nástrojů ovládacího prvku pomocí návrháře](how-to-add-buttons-to-a-toolbar-control-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="5a464-119">Also see [How to: Define an Icon for a ToolBar Button Using the Designer](how-to-define-an-icon-for-a-toolbar-button-using-the-designer.md), [How to: Add Buttons to a ToolBar Control Using the Designer](how-to-add-buttons-to-a-toolbar-control-using-the-designer.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5a464-120">Odkaz</span><span class="sxs-lookup"><span data-stu-id="5a464-120">Reference</span></span>  
 <span data-ttu-id="5a464-121"><xref:System.Windows.Forms.ToolBar> Třída</span><span class="sxs-lookup"><span data-stu-id="5a464-121"><xref:System.Windows.Forms.ToolBar> class</span></span>  
 <span data-ttu-id="5a464-122">Poskytuje referenční informace o třídě a její členy.</span><span class="sxs-lookup"><span data-stu-id="5a464-122">Provides reference information on the class and its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5a464-123">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="5a464-123">Related Sections</span></span>  
 [<span data-ttu-id="5a464-124">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5a464-124">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="5a464-125">Obsahuje úplný seznam všech ovládacích prvcích Windows Forms, s odkazy na informace o jejich použití.</span><span class="sxs-lookup"><span data-stu-id="5a464-125">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>  
  
 [<span data-ttu-id="5a464-126">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="5a464-126">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 <span data-ttu-id="5a464-127">Popisuje panely nástrojů, které můžete hostovat nabídek, ovládacích prvků a uživatelských ovládacích prvků v aplikacích Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5a464-127">Describes toolbars that can host menus, controls, and user controls in Windows Forms applications.</span></span>
