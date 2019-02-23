---
title: SplitContainer – ovládací prvek (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- splitter windows
- SplitContainer control [Windows Forms]
ms.assetid: 2e36f17f-5c39-4fb4-bb09-7ce3ef823402
ms.openlocfilehash: 0afc1aba32852406b975cc65ab4d4bff334d3ff7
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745460"
---
# <a name="splitcontainer-control-windows-forms"></a><span data-ttu-id="d3d88-102">SplitContainer – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="d3d88-102">SplitContainer Control (Windows Forms)</span></span>
<span data-ttu-id="d3d88-103">Windows Forms `SplitContainer` ovládací prvek lze považovat za složeného; je dva panely oddělené přesouvatelný panelu.</span><span class="sxs-lookup"><span data-stu-id="d3d88-103">The Windows Forms `SplitContainer` control can be thought of as a composite; it is two panels separated by a movable bar.</span></span> <span data-ttu-id="d3d88-104">Když je ukazatel myši nad panelu, ukazatel se změní tvar, který má zobrazit, že panel je přesouvatelný.</span><span class="sxs-lookup"><span data-stu-id="d3d88-104">When the mouse pointer is over the bar, the pointer changes shape to show that the bar is movable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3d88-105">V **nástrojů**, tento ovládací prvek nahradí <xref:System.Windows.Forms.Splitter> ovládací prvek, který byl existuje v předchozí verzi sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d3d88-105">In the **Toolbox**, this control replaces the <xref:System.Windows.Forms.Splitter> control that was there in the previous version of Visual Studio.</span></span> <span data-ttu-id="d3d88-106">`SplitContainer` Je mnohem upřednostňované nad ovládací prvek <xref:System.Windows.Forms.Splitter> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d3d88-106">The `SplitContainer` control is much preferred over the <xref:System.Windows.Forms.Splitter> control.</span></span> <span data-ttu-id="d3d88-107"><xref:System.Windows.Forms.Splitter> Tříd je zahrnutá v rozhraní .NET Framework z důvodu kompatibility se stávajícími aplikacemi, ale důrazně doporučujeme použít `SplitContainer` ovládací prvek pro nové projekty.</span><span class="sxs-lookup"><span data-stu-id="d3d88-107">The <xref:System.Windows.Forms.Splitter> class is still included in the .NET Framework for compatibility with existing applications, but we strongly encourage you to use the `SplitContainer` control for new projects.</span></span>  
  
 <span data-ttu-id="d3d88-108">`SplitContainer` Řízení umožňuje vytvářet komplexní uživatelské rozhraní; často, výběr v jeden panel Určuje, jaké objekty jsou uvedeny na panelu.</span><span class="sxs-lookup"><span data-stu-id="d3d88-108">The `SplitContainer` control lets you create complex user interfaces; often, a selection in one panel determines what objects are shown in the other panel.</span></span> <span data-ttu-id="d3d88-109">Toto uspořádání se velice efektivní pro zobrazení informací o procházení.</span><span class="sxs-lookup"><span data-stu-id="d3d88-109">This arrangement is very effective for displaying and browsing information.</span></span> <span data-ttu-id="d3d88-110">Dva panely umožňují souhrnné informace v oblastech s panelu, nebo "rozdělovač," usnadňuje uživatelům změnit velikost panelů.</span><span class="sxs-lookup"><span data-stu-id="d3d88-110">Having two panels allow you to aggregate information in areas, and the bar, or "splitter," makes it easy for users to resize the panels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d3d88-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d3d88-111">In This Section</span></span>  
 [<span data-ttu-id="d3d88-112">Přehled ovládacího prvku SplitContainer</span><span class="sxs-lookup"><span data-stu-id="d3d88-112">SplitContainer Control Overview</span></span>](../../../../docs/framework/winforms/controls/splitcontainer-control-overview-windows-forms.md)  
 <span data-ttu-id="d3d88-113">Zavádí `SplitContainer` řídit a popisuje běžně používané vlastnosti, metody a události.</span><span class="sxs-lookup"><span data-stu-id="d3d88-113">Introduces the `SplitContainer` control and describes the commonly used properties, methods, and events.</span></span>  
  
 [<span data-ttu-id="d3d88-114">Postupy: Definování změny velikosti a polohování v rozděleném okně chování</span><span class="sxs-lookup"><span data-stu-id="d3d88-114">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](../../../../docs/framework/winforms/controls/how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 <span data-ttu-id="d3d88-115">Popisuje, jak řídit rozdělovač v rámci `SplitContainer` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d3d88-115">Describes how to control the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="d3d88-116">Postupy: Vodorovné rozdělení okna</span><span class="sxs-lookup"><span data-stu-id="d3d88-116">How to: Split a Window Horizontally</span></span>](../../../../docs/framework/winforms/controls/how-to-split-a-window-horizontally.md)  
 <span data-ttu-id="d3d88-117">Popisuje, jak řídit orientaci ovládacího prvku rozdělovač v rámci `SplitContainer` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d3d88-117">Describes how to control the orientation of the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="d3d88-118">Postupy: Vytvoření více podokny uživatelského rozhraní pomocí Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d3d88-118">How to: Create a Multipane User Interface with Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 <span data-ttu-id="d3d88-119">Vytvoří více podokně uživatelské rozhraní, který je podobný tomu použitému v aplikaci Microsoft Outlook.</span><span class="sxs-lookup"><span data-stu-id="d3d88-119">Creates a multi-pane user interface that is similar to the one used in Microsoft Outlook.</span></span>  
  
 <span data-ttu-id="d3d88-120">Viz také [jak: Rozdělení okna pomocí návrháře vodorovně](how-to-split-a-window-horizontally-using-the-designer.md), [jak: Vytváření rozhraní ve stylu Průzkumníka Windows ve formuláři Windows Forms](how-to-create-a-windows-explorer-style-interface-on-a-windows-form.md), [jak: Vytvoření více podokny uživatelského rozhraní pomocí Windows Forms pomocí návrháře](create-a-multipane-user-interface-with-wf-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="d3d88-120">Also see [How to: Split a Window Horizontally Using the Designer](how-to-split-a-window-horizontally-using-the-designer.md), [How to: Create a Windows Explorer–Style Interface on a Windows Form](how-to-create-a-windows-explorer-style-interface-on-a-windows-form.md), [How to: Create a Multipane User Interface with Windows Forms Using the Designer](create-a-multipane-user-interface-with-wf-using-the-designer.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d3d88-121">Odkaz</span><span class="sxs-lookup"><span data-stu-id="d3d88-121">Reference</span></span>  
 <span data-ttu-id="d3d88-122"><xref:System.Windows.Forms.SplitContainer> Třída</span><span class="sxs-lookup"><span data-stu-id="d3d88-122"><xref:System.Windows.Forms.SplitContainer> class</span></span>  
 <span data-ttu-id="d3d88-123">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="d3d88-123">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d3d88-124">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="d3d88-124">Related Sections</span></span>  
 [<span data-ttu-id="d3d88-125">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="d3d88-125">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 <span data-ttu-id="d3d88-126">Obsahuje odkazy na témata o ovládacích prvcích určený konkrétně pro práci s formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="d3d88-126">Provides links to topics about the controls designed specifically to work with Windows Forms.</span></span>  
  
 [<span data-ttu-id="d3d88-127">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d3d88-127">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="d3d88-128">Obsahuje úplný seznam všech ovládacích prvcích Windows Forms, s odkazy na informace o jejich použití.</span><span class="sxs-lookup"><span data-stu-id="d3d88-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
