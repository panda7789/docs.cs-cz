---
title: ToolBar – ovládací prvek (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolBar control [Windows Forms]
ms.assetid: 6b40e9ce-6a7a-4784-bfc9-7f1d36b7462e
ms.openlocfilehash: 13a56af0e52897a6fd4e11516fbf4c0b8f6d6b5d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929570"
---
# <a name="toolbar-control-windows-forms"></a><span data-ttu-id="2f23e-102">ToolBar – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="2f23e-102">ToolBar Control (Windows Forms)</span></span>
> [!NOTE]
> <span data-ttu-id="2f23e-103">Ovládací prvek nahrazuje a přidává funkce `ToolBar` `ToolBar` ovládacímu prvku. ovládací prvek je však ponechán pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. <xref:System.Windows.Forms.ToolStrip></span><span class="sxs-lookup"><span data-stu-id="2f23e-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the `ToolBar` control; however, the `ToolBar` control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="2f23e-104">Model Windows Forms `ToolBar` ovládací prvek se používá ve formulářích jako ovládací panel, který zobrazuje řádek rozevíracích nabídek a tlačítek s rastrovými obrázky, které aktivují příkazy.</span><span class="sxs-lookup"><span data-stu-id="2f23e-104">The Windows Forms `ToolBar` control is used on forms as a control bar that displays a row of drop-down menus and bitmapped buttons that activate commands.</span></span> <span data-ttu-id="2f23e-105">Kliknutí na tlačítko na panelu nástrojů je tedy ekvivalentní k výběru příkazu nabídky.</span><span class="sxs-lookup"><span data-stu-id="2f23e-105">Thus, clicking a toolbar button is equivalent to choosing a menu command.</span></span> <span data-ttu-id="2f23e-106">Tlačítka se dají nakonfigurovat tak, aby se zobrazovala jako tlačítka pro vložení, rozevírací nabídky nebo oddělovače.</span><span class="sxs-lookup"><span data-stu-id="2f23e-106">The buttons can be configured to appear and behave as push buttons, drop-down menus, or separators.</span></span> <span data-ttu-id="2f23e-107">Panel nástrojů obvykle obsahuje tlačítka a nabídky, které odpovídají položkám v rámci struktury nabídky aplikace, a poskytuje tak rychlý přístup k nejčastěji používaným funkcím a příkazům aplikace.</span><span class="sxs-lookup"><span data-stu-id="2f23e-107">Typically, a toolbar contains buttons and menus that correspond to items in an application's menu structure, providing quick access to an application's most frequently used functions and commands.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f23e-108">Vlastnost<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> ovládacího prvku přebírá instanci <xref:System.Windows.Forms.ContextMenu>třídy `ToolBar` jako referenci.</span><span class="sxs-lookup"><span data-stu-id="2f23e-108">The `ToolBar` control's <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> property takes an instance of the <xref:System.Windows.Forms.ContextMenu> class as a reference.</span></span> <span data-ttu-id="2f23e-109">Pečlivě zvažte odkaz, který předáte při implementaci tohoto tlačítka na panelech nástrojů ve vaší aplikaci, protože vlastnost akceptuje libovolný objekt, který dědí z <xref:System.Windows.Forms.Menu> třídy.</span><span class="sxs-lookup"><span data-stu-id="2f23e-109">Carefully consider the reference you pass when implementing this sort of button on toolbars in your application, as the property will accept any object that inherits from the <xref:System.Windows.Forms.Menu> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2f23e-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2f23e-110">In This Section</span></span>  
 [<span data-ttu-id="2f23e-111">Přehled ovládacího prvku ToolBar</span><span class="sxs-lookup"><span data-stu-id="2f23e-111">ToolBar Control Overview</span></span>](toolbar-control-overview-windows-forms.md)  
 <span data-ttu-id="2f23e-112">Zavádí obecné koncepce `ToolBar` ovládacího prvku, které vám umožní navrhnout vlastní panely nástrojů, se kterými uživatelé můžou pracovat.</span><span class="sxs-lookup"><span data-stu-id="2f23e-112">Introduces the general concepts of the `ToolBar` control, which allows you to design custom toolbars that your users can work with.</span></span>  
  
 [<span data-ttu-id="2f23e-113">Postupy: Přidání tlačítek do ovládacího prvku ToolBar</span><span class="sxs-lookup"><span data-stu-id="2f23e-113">How to: Add Buttons to a ToolBar Control</span></span>](how-to-add-buttons-to-a-toolbar-control.md)  
 <span data-ttu-id="2f23e-114">Popisuje, jak přidat tlačítka do `ToolBar` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2f23e-114">Describes how to add buttons to a `ToolBar` control.</span></span>  
  
 [<span data-ttu-id="2f23e-115">Postupy: Definování ikony pro tlačítko panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="2f23e-115">How to: Define an Icon for a ToolBar Button</span></span>](how-to-define-an-icon-for-a-toolbar-button.md)  
 <span data-ttu-id="2f23e-116">Popisuje, jak zobrazit ikony v rámci `ToolBar` tlačítek ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2f23e-116">Describes how to display icons within a `ToolBar` control's buttons.</span></span>  
  
 [<span data-ttu-id="2f23e-117">Postupy: Aktivace událostí nabídky pro tlačítka panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="2f23e-117">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)  
 <span data-ttu-id="2f23e-118">Poskytuje pokyny k psaní kódu pro interpretaci, na které tlačítko uživatel klikne v `ToolBar` ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="2f23e-118">Gives directions on writing code to interpret which button the user clicks in a `ToolBar` control.</span></span>  
  
 <span data-ttu-id="2f23e-119">Podívejte [se také na postupy: Definujte ikonu pro tlačítko panelu nástrojů pomocí návrháře](how-to-define-an-icon-for-a-toolbar-button-using-the-designer.md), [jak: Přidejte tlačítka do ovládacího prvku ToolBar pomocí návrháře](how-to-add-buttons-to-a-toolbar-control-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="2f23e-119">Also see [How to: Define an Icon for a ToolBar Button Using the Designer](how-to-define-an-icon-for-a-toolbar-button-using-the-designer.md), [How to: Add Buttons to a ToolBar Control Using the Designer](how-to-add-buttons-to-a-toolbar-control-using-the-designer.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2f23e-120">Reference</span><span class="sxs-lookup"><span data-stu-id="2f23e-120">Reference</span></span>  
 <span data-ttu-id="2f23e-121"><xref:System.Windows.Forms.ToolBar>Deník</span><span class="sxs-lookup"><span data-stu-id="2f23e-121"><xref:System.Windows.Forms.ToolBar> class</span></span>  
 <span data-ttu-id="2f23e-122">Poskytuje referenční informace o třídě a jejích členech.</span><span class="sxs-lookup"><span data-stu-id="2f23e-122">Provides reference information on the class and its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2f23e-123">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="2f23e-123">Related Sections</span></span>  
 [<span data-ttu-id="2f23e-124">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2f23e-124">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="2f23e-125">Obsahuje úplný seznam model Windows Formsch ovládacích prvků s odkazy na informace o jejich použití.</span><span class="sxs-lookup"><span data-stu-id="2f23e-125">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>  
  
 [<span data-ttu-id="2f23e-126">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="2f23e-126">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)  
 <span data-ttu-id="2f23e-127">Popisuje panely nástrojů, které mohou hostovat nabídky, ovládací prvky a uživatelské ovládací prvky v aplikacích model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2f23e-127">Describes toolbars that can host menus, controls, and user controls in Windows Forms applications.</span></span>
