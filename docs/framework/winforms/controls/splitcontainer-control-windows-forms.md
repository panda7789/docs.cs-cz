---
title: SplitContainer – ovládací prvek (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- splitter windows
- SplitContainer control [Windows Forms]
ms.assetid: 2e36f17f-5c39-4fb4-bb09-7ce3ef823402
ms.openlocfilehash: d860763e935c88619e3355661038757d00247dfd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963593"
---
# <a name="splitcontainer-control-windows-forms"></a><span data-ttu-id="11877-102">SplitContainer – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="11877-102">SplitContainer Control (Windows Forms)</span></span>
<span data-ttu-id="11877-103">Ovládací prvek `SplitContainer` model Windows Forms lze představit jako složený; jedná se o dva panely oddělené pohyblivým pruhem.</span><span class="sxs-lookup"><span data-stu-id="11877-103">The Windows Forms `SplitContainer` control can be thought of as a composite; it is two panels separated by a movable bar.</span></span> <span data-ttu-id="11877-104">Když je ukazatel myši nad pruhem, ukazatel se změní na obrazec, který ukazuje, že je pruh přesunutý.</span><span class="sxs-lookup"><span data-stu-id="11877-104">When the mouse pointer is over the bar, the pointer changes shape to show that the bar is movable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11877-105">V **sadě nástrojů**tento ovládací prvek nahrazuje <xref:System.Windows.Forms.Splitter> ovládací prvek, který byl v předchozí verzi sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="11877-105">In the **Toolbox**, this control replaces the <xref:System.Windows.Forms.Splitter> control that was there in the previous version of Visual Studio.</span></span> <span data-ttu-id="11877-106">Ovládací prvek je mnohem upřednostňovaný <xref:System.Windows.Forms.Splitter> nad ovládacím prvkem. `SplitContainer`</span><span class="sxs-lookup"><span data-stu-id="11877-106">The `SplitContainer` control is much preferred over the <xref:System.Windows.Forms.Splitter> control.</span></span> <span data-ttu-id="11877-107">Třída je stále zahrnuta v .NET Framework z důvodu kompatibility s existujícími aplikacemi, ale důrazně doporučujeme `SplitContainer` používat ovládací prvek pro nové projekty. <xref:System.Windows.Forms.Splitter></span><span class="sxs-lookup"><span data-stu-id="11877-107">The <xref:System.Windows.Forms.Splitter> class is still included in the .NET Framework for compatibility with existing applications, but we strongly encourage you to use the `SplitContainer` control for new projects.</span></span>  
  
 <span data-ttu-id="11877-108">`SplitContainer` Ovládací prvek umožňuje vytvářet složitá uživatelská rozhraní, často výběr na jednom panelu určuje, které objekty se zobrazí na druhém panelu.</span><span class="sxs-lookup"><span data-stu-id="11877-108">The `SplitContainer` control lets you create complex user interfaces; often, a selection in one panel determines what objects are shown in the other panel.</span></span> <span data-ttu-id="11877-109">Toto uspořádání je velmi efektivní pro zobrazení a informace o procházení.</span><span class="sxs-lookup"><span data-stu-id="11877-109">This arrangement is very effective for displaying and browsing information.</span></span> <span data-ttu-id="11877-110">Když máte dva panely, umožníte si agregovat informace v oblastech a pruh nebo "rozdělovač", aby uživatelé mohli měnit velikost panelů snadno.</span><span class="sxs-lookup"><span data-stu-id="11877-110">Having two panels allow you to aggregate information in areas, and the bar, or "splitter," makes it easy for users to resize the panels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="11877-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="11877-111">In This Section</span></span>  
 [<span data-ttu-id="11877-112">Přehled ovládacího prvku SplitContainer</span><span class="sxs-lookup"><span data-stu-id="11877-112">SplitContainer Control Overview</span></span>](splitcontainer-control-overview-windows-forms.md)  
 <span data-ttu-id="11877-113">`SplitContainer` Zavádí ovládací prvek a popisuje běžně používané vlastnosti, metody a události.</span><span class="sxs-lookup"><span data-stu-id="11877-113">Introduces the `SplitContainer` control and describes the commonly used properties, methods, and events.</span></span>  
  
 [<span data-ttu-id="11877-114">Postupy: Definování chování změny velikosti a umístění v rozděleném okně</span><span class="sxs-lookup"><span data-stu-id="11877-114">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 <span data-ttu-id="11877-115">Popisuje způsob řízení rozdělovače v rámci `SplitContainer` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="11877-115">Describes how to control the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="11877-116">Postupy: Vodorovné rozdělení okna</span><span class="sxs-lookup"><span data-stu-id="11877-116">How to: Split a Window Horizontally</span></span>](how-to-split-a-window-horizontally.md)  
 <span data-ttu-id="11877-117">Popisuje způsob řízení orientace rozdělovače v rámci `SplitContainer` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="11877-117">Describes how to control the orientation of the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="11877-118">Postupy: Vytvoření uživatelského rozhraní s více podokny pomocí model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11877-118">How to: Create a Multipane User Interface with Windows Forms</span></span>](how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 <span data-ttu-id="11877-119">Vytvoří uživatelské rozhraní s více podokny, které se podobá tomu, který se používá v aplikaci Microsoft Outlook.</span><span class="sxs-lookup"><span data-stu-id="11877-119">Creates a multi-pane user interface that is similar to the one used in Microsoft Outlook.</span></span>  
  
 <span data-ttu-id="11877-120">Podívejte [se také na postupy: Rozdělení okna vodorovně pomocí návrháře](how-to-split-a-window-horizontally-using-the-designer.md), [postupy: Postup vytvoření rozhraní ve stylu Průzkumníka Windows ve formuláři Windows Form](how-to-create-a-windows-explorer-style-interface-on-a-windows-form.md): [ Pomocí návrháře](create-a-multipane-user-interface-with-wf-using-the-designer.md)vytvořte uživatelské rozhraní s více podokny pomocí model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="11877-120">Also see [How to: Split a Window Horizontally Using the Designer](how-to-split-a-window-horizontally-using-the-designer.md), [How to: Create a Windows Explorer–Style Interface on a Windows Form](how-to-create-a-windows-explorer-style-interface-on-a-windows-form.md), [How to: Create a Multipane User Interface with Windows Forms Using the Designer](create-a-multipane-user-interface-with-wf-using-the-designer.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="11877-121">Reference</span><span class="sxs-lookup"><span data-stu-id="11877-121">Reference</span></span>  
 <span data-ttu-id="11877-122"><xref:System.Windows.Forms.SplitContainer>Deník</span><span class="sxs-lookup"><span data-stu-id="11877-122"><xref:System.Windows.Forms.SplitContainer> class</span></span>  
 <span data-ttu-id="11877-123">Popisuje tuto třídu a má odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="11877-123">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="11877-124">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="11877-124">Related Sections</span></span>  
 [<span data-ttu-id="11877-125">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="11877-125">Windows Forms Controls</span></span>](index.md)  
 <span data-ttu-id="11877-126">Obsahuje odkazy na témata týkající se ovládacích prvků, které jsou určeny konkrétně pro práci s model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="11877-126">Provides links to topics about the controls designed specifically to work with Windows Forms.</span></span>  
  
 [<span data-ttu-id="11877-127">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11877-127">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="11877-128">Obsahuje úplný seznam model Windows Formsch ovládacích prvků s odkazy na informace o jejich použití.</span><span class="sxs-lookup"><span data-stu-id="11877-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
