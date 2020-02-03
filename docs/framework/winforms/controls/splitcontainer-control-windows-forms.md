---
title: SplitContainer – ovládací prvek
ms.date: 03/30/2017
helpviewer_keywords:
- splitter windows
- SplitContainer control [Windows Forms]
ms.assetid: 2e36f17f-5c39-4fb4-bb09-7ce3ef823402
ms.openlocfilehash: ac04f60847aa6f77c11637f37b5ec94b6f7ef341
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742901"
---
# <a name="splitcontainer-control-windows-forms"></a><span data-ttu-id="7d884-102">SplitContainer – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="7d884-102">SplitContainer Control (Windows Forms)</span></span>
<span data-ttu-id="7d884-103">Ovládací prvek model Windows Forms `SplitContainer` lze představit jako složený; Jedná se o dva panely oddělené pohyblivým pruhem.</span><span class="sxs-lookup"><span data-stu-id="7d884-103">The Windows Forms `SplitContainer` control can be thought of as a composite; it is two panels separated by a movable bar.</span></span> <span data-ttu-id="7d884-104">Když je ukazatel myši nad pruhem, ukazatel se změní na obrazec, který ukazuje, že je pruh přesunutý.</span><span class="sxs-lookup"><span data-stu-id="7d884-104">When the mouse pointer is over the bar, the pointer changes shape to show that the bar is movable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7d884-105">V **sadě nástrojů**tento ovládací prvek nahrazuje ovládací prvek <xref:System.Windows.Forms.Splitter>, který byl v předchozí verzi sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7d884-105">In the **Toolbox**, this control replaces the <xref:System.Windows.Forms.Splitter> control that was there in the previous version of Visual Studio.</span></span> <span data-ttu-id="7d884-106">Ovládací prvek `SplitContainer` je pro <xref:System.Windows.Forms.Splitter> řízení mnohem upřednostňovaný.</span><span class="sxs-lookup"><span data-stu-id="7d884-106">The `SplitContainer` control is much preferred over the <xref:System.Windows.Forms.Splitter> control.</span></span> <span data-ttu-id="7d884-107">Třída <xref:System.Windows.Forms.Splitter> je stále zahrnuta v .NET Framework kvůli kompatibilitě se stávajícími aplikacemi, ale důrazně doporučujeme používat ovládací prvek `SplitContainer` pro nové projekty.</span><span class="sxs-lookup"><span data-stu-id="7d884-107">The <xref:System.Windows.Forms.Splitter> class is still included in the .NET Framework for compatibility with existing applications, but we strongly encourage you to use the `SplitContainer` control for new projects.</span></span>  
  
 <span data-ttu-id="7d884-108">Ovládací prvek `SplitContainer` umožňuje vytvářet složitá uživatelská rozhraní. často výběr na jednom panelu určuje, které objekty se zobrazí na druhém panelu.</span><span class="sxs-lookup"><span data-stu-id="7d884-108">The `SplitContainer` control lets you create complex user interfaces; often, a selection in one panel determines what objects are shown in the other panel.</span></span> <span data-ttu-id="7d884-109">Toto uspořádání je velmi efektivní pro zobrazení a informace o procházení.</span><span class="sxs-lookup"><span data-stu-id="7d884-109">This arrangement is very effective for displaying and browsing information.</span></span> <span data-ttu-id="7d884-110">Když máte dva panely, umožníte si agregovat informace v oblastech a pruh nebo "rozdělovač", aby uživatelé mohli měnit velikost panelů snadno.</span><span class="sxs-lookup"><span data-stu-id="7d884-110">Having two panels allow you to aggregate information in areas, and the bar, or "splitter," makes it easy for users to resize the panels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7d884-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="7d884-111">In This Section</span></span>  
 [<span data-ttu-id="7d884-112">Přehled ovládacího prvku SplitContainer</span><span class="sxs-lookup"><span data-stu-id="7d884-112">SplitContainer Control Overview</span></span>](splitcontainer-control-overview-windows-forms.md)  
 <span data-ttu-id="7d884-113">Zavádí ovládací prvek `SplitContainer` a popisuje běžně používané vlastnosti, metody a události.</span><span class="sxs-lookup"><span data-stu-id="7d884-113">Introduces the `SplitContainer` control and describes the commonly used properties, methods, and events.</span></span>  
  
 [<span data-ttu-id="7d884-114">Postupy: Definování chování změny velikosti a polohování v rozděleném okně</span><span class="sxs-lookup"><span data-stu-id="7d884-114">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 <span data-ttu-id="7d884-115">Popisuje způsob řízení rozdělovače v rámci ovládacího prvku `SplitContainer`.</span><span class="sxs-lookup"><span data-stu-id="7d884-115">Describes how to control the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="7d884-116">Postupy: Vodorovné rozdělení okna</span><span class="sxs-lookup"><span data-stu-id="7d884-116">How to: Split a Window Horizontally</span></span>](how-to-split-a-window-horizontally.md)  
 <span data-ttu-id="7d884-117">Popisuje způsob řízení orientace rozdělovače v rámci ovládacího prvku `SplitContainer`.</span><span class="sxs-lookup"><span data-stu-id="7d884-117">Describes how to control the orientation of the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="7d884-118">Postupy: Vytváření uživatelského rozhraní s více podokny pomocí Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7d884-118">How to: Create a Multipane User Interface with Windows Forms</span></span>](how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 <span data-ttu-id="7d884-119">Vytvoří uživatelské rozhraní s více podokny, které se podobá tomu, který se používá v aplikaci Microsoft Outlook.</span><span class="sxs-lookup"><span data-stu-id="7d884-119">Creates a multi-pane user interface that is similar to the one used in Microsoft Outlook.</span></span>  
  
 <span data-ttu-id="7d884-120">Viz také [Postupy: rozdělení okna vodorovně pomocí návrháře](how-to-split-a-window-horizontally-using-the-designer.md), [Postupy: vytvoření rozhraní ve stylu Průzkumníka Windows na formuláři Windows](how-to-create-a-windows-explorer-style-interface-on-a-windows-form.md)Forms, [Postupy: vytvoření uživatelského rozhraní s více podokny s model Windows Forms pomocí návrháře](create-a-multipane-user-interface-with-wf-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="7d884-120">Also see [How to: Split a Window Horizontally Using the Designer](how-to-split-a-window-horizontally-using-the-designer.md), [How to: Create a Windows Explorer–Style Interface on a Windows Form](how-to-create-a-windows-explorer-style-interface-on-a-windows-form.md), [How to: Create a Multipane User Interface with Windows Forms Using the Designer](create-a-multipane-user-interface-with-wf-using-the-designer.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7d884-121">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="7d884-121">Reference</span></span>  
 <span data-ttu-id="7d884-122">Třída <xref:System.Windows.Forms.SplitContainer></span><span class="sxs-lookup"><span data-stu-id="7d884-122"><xref:System.Windows.Forms.SplitContainer> class</span></span>  
 <span data-ttu-id="7d884-123">Popisuje tuto třídu a má odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="7d884-123">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7d884-124">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="7d884-124">Related Sections</span></span>  
 [<span data-ttu-id="7d884-125">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="7d884-125">Windows Forms Controls</span></span>](index.md)  
 <span data-ttu-id="7d884-126">Obsahuje odkazy na témata týkající se ovládacích prvků, které jsou určeny konkrétně pro práci s model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7d884-126">Provides links to topics about the controls designed specifically to work with Windows Forms.</span></span>  
  
 [<span data-ttu-id="7d884-127">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7d884-127">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="7d884-128">Obsahuje úplný seznam model Windows Formsch ovládacích prvků s odkazy na informace o jejich použití.</span><span class="sxs-lookup"><span data-stu-id="7d884-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
