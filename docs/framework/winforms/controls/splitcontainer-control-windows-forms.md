---
title: "SplitContainer – ovládací prvek (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- splitter windows
- SplitContainer control [Windows Forms]
ms.assetid: 2e36f17f-5c39-4fb4-bb09-7ce3ef823402
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 336243cc4db7039225ba272cac1ba7a3f173f361
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="splitcontainer-control-windows-forms"></a><span data-ttu-id="54824-102">SplitContainer – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="54824-102">SplitContainer Control (Windows Forms)</span></span>
<span data-ttu-id="54824-103">Windows Forms `SplitContainer` řízení lze považovat za složené; je dva panely oddělených mobilní panelu.</span><span class="sxs-lookup"><span data-stu-id="54824-103">The Windows Forms `SplitContainer` control can be thought of as a composite; it is two panels separated by a movable bar.</span></span> <span data-ttu-id="54824-104">Když ukazatel myši nad panelu, změní tvar, který má zobrazit, že je na panelu mobilní.</span><span class="sxs-lookup"><span data-stu-id="54824-104">When the mouse pointer is over the bar, the pointer changes shape to show that the bar is movable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54824-105">V **sada nástrojů**tento řízení nahradí <xref:System.Windows.Forms.Splitter> ovládací prvek, který se někdo u předchozích verzí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="54824-105">In the **Toolbox**, this control replaces the <xref:System.Windows.Forms.Splitter> control that was there in the previous version of Visual Studio.</span></span> <span data-ttu-id="54824-106">`SplitContainer` Ovládací prvek je mnohem upřednostňované přes <xref:System.Windows.Forms.Splitter> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="54824-106">The `SplitContainer` control is much preferred over the <xref:System.Windows.Forms.Splitter> control.</span></span> <span data-ttu-id="54824-107"><xref:System.Windows.Forms.Splitter> Třída je stále zahrnuta v rozhraní .NET Framework pro kompatibilitě se stávajícími aplikacemi, ale důrazně doporučujeme používat `SplitContainer` ovládací prvek pro nové projekty.</span><span class="sxs-lookup"><span data-stu-id="54824-107">The <xref:System.Windows.Forms.Splitter> class is still included in the .NET Framework for compatibility with existing applications, but we strongly encourage you to use the `SplitContainer` control for new projects.</span></span>  
  
 <span data-ttu-id="54824-108">`SplitContainer` Řízení umožňuje vytvořit komplexní uživatelské rozhraní; často výběr jeden panelu určuje, které objekty se zobrazují panelu.</span><span class="sxs-lookup"><span data-stu-id="54824-108">The `SplitContainer` control lets you create complex user interfaces; often, a selection in one panel determines what objects are shown in the other panel.</span></span> <span data-ttu-id="54824-109">Toto uspořádání je velmi efektivní pro zobrazení a procházení informace.</span><span class="sxs-lookup"><span data-stu-id="54824-109">This arrangement is very effective for displaying and browsing information.</span></span> <span data-ttu-id="54824-110">Dva panely umožňují agregační informace v oblastech s panelu nebo "rozdělovače," usnadňuje uživatelům změnit velikost panely.</span><span class="sxs-lookup"><span data-stu-id="54824-110">Having two panels allow you to aggregate information in areas, and the bar, or "splitter," makes it easy for users to resize the panels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="54824-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="54824-111">In This Section</span></span>  
 [<span data-ttu-id="54824-112">Přehled ovládacího prvku SplitContainer</span><span class="sxs-lookup"><span data-stu-id="54824-112">SplitContainer Control Overview</span></span>](../../../../docs/framework/winforms/controls/splitcontainer-control-overview-windows-forms.md)  
 <span data-ttu-id="54824-113">Zavádí `SplitContainer` řízení a popisuje běžně používané vlastnosti, metod a události.</span><span class="sxs-lookup"><span data-stu-id="54824-113">Introduces the `SplitContainer` control and describes the commonly used properties, methods, and events.</span></span>  
  
 [<span data-ttu-id="54824-114">Postupy: definování změny velikosti a polohování v rozděleném okně chování</span><span class="sxs-lookup"><span data-stu-id="54824-114">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](../../../../docs/framework/winforms/controls/how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 <span data-ttu-id="54824-115">Popisuje, jak řídit rozdělovače v rámci `SplitContainer` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="54824-115">Describes how to control the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="54824-116">Postupy: vodorovné rozdělení okna</span><span class="sxs-lookup"><span data-stu-id="54824-116">How to: Split a Window Horizontally</span></span>](../../../../docs/framework/winforms/controls/how-to-split-a-window-horizontally.md)  
 <span data-ttu-id="54824-117">Popisuje, jak řídit orientace Rozdělovače v rámci `SplitContainer` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="54824-117">Describes how to control the orientation of the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="54824-118">Postupy: vytváření více podokny uživatelského rozhraní s Windows Forms</span><span class="sxs-lookup"><span data-stu-id="54824-118">How to: Create a Multipane User Interface with Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 <span data-ttu-id="54824-119">Vytvoří více podokně uživatelské rozhraní, které je podobné použít v aplikaci Microsoft Outlook.</span><span class="sxs-lookup"><span data-stu-id="54824-119">Creates a multi-pane user interface that is similar to the one used in Microsoft Outlook.</span></span>  
  
 <span data-ttu-id="54824-120">Také najdete v části [postupy: rozdělení a okno vodorovně pomocí návrháře](http://msdn.microsoft.com/library/ms233667\(v=vs.110\)), [postup: vytváření rozhraní stylu Průzkumníku Windows ve formuláři Windows](http://msdn.microsoft.com/library/zh2fe5a5\(v=vs.110\)), [postupy: vytváření uživatelského rozhraní s více podokny s Windows Forms pomocí návrháře](http://msdn.microsoft.com/library/ms233661\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="54824-120">Also see [How to: Split a Window Horizontally Using the Designer](http://msdn.microsoft.com/library/ms233667\(v=vs.110\)), [How to: Create a Windows Explorer–Style Interface on a Windows Form](http://msdn.microsoft.com/library/zh2fe5a5\(v=vs.110\)), [How to: Create a Multipane User Interface with Windows Forms Using the Designer](http://msdn.microsoft.com/library/ms233661\(v=vs.110\)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="54824-121">Odkaz</span><span class="sxs-lookup"><span data-stu-id="54824-121">Reference</span></span>  
 <span data-ttu-id="54824-122"><xref:System.Windows.Forms.SplitContainer>– Třída</span><span class="sxs-lookup"><span data-stu-id="54824-122"><xref:System.Windows.Forms.SplitContainer> class</span></span>  
 <span data-ttu-id="54824-123">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="54824-123">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="54824-124">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="54824-124">Related Sections</span></span>  
 [<span data-ttu-id="54824-125">Ovládací prvky Windows Forms</span><span class="sxs-lookup"><span data-stu-id="54824-125">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 <span data-ttu-id="54824-126">Obsahuje odkazy na témata o ovládacích prvcích navrženy speciálně pro práci s Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="54824-126">Provides links to topics about the controls designed specifically to work with Windows Forms.</span></span>  
  
 [<span data-ttu-id="54824-127">Ovládací prvky používané ve formulářích Windows</span><span class="sxs-lookup"><span data-stu-id="54824-127">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="54824-128">Poskytuje úplný seznam Windows Forms – ovládací prvky, odkazy na informace o jejich používání.</span><span class="sxs-lookup"><span data-stu-id="54824-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
