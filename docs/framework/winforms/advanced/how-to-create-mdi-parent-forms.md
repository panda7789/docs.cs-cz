---
title: "Postupy: Vytváření nadřazených formulářů MDI"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parent forms
- MDI [Windows Forms], creating forms
ms.assetid: 12c71221-2377-4bb6-b10b-7b4b300fd462
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0147bc0777fdf3168ab0bc36ced0943571187d3c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-mdi-parent-forms"></a><span data-ttu-id="79b84-102">Postupy: Vytváření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="79b84-102">How to: Create MDI Parent Forms</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="79b84-103">Toto téma používá <xref:System.Windows.Forms.MainMenu> ovládací prvek, který byl nahrazen <xref:System.Windows.Forms.MenuStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="79b84-103">This topic uses the <xref:System.Windows.Forms.MainMenu> control, which has been replaced by the <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="79b84-104"><xref:System.Windows.Forms.MainMenu> Řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte.</span><span class="sxs-lookup"><span data-stu-id="79b84-104">The <xref:System.Windows.Forms.MainMenu> control is retained for both backward compatibility and future use, if you choose.</span></span>  <span data-ttu-id="79b84-105">Informace o vytváření MDI nadřazené formuláře pomocí <xref:System.Windows.Forms.MenuStrip>, najdete v části [postupy: vytvoření seznamu okna MDI pomocí MenuStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="79b84-105">For information about creating a MDI parent Form by using a <xref:System.Windows.Forms.MenuStrip>, see [How to: Create an MDI Window List with MenuStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).</span></span>  
  
 <span data-ttu-id="79b84-106">Základ pro aplikace rozhraní více dokumentů (MDI) je nadřazeného formuláře MDI.</span><span class="sxs-lookup"><span data-stu-id="79b84-106">The foundation of a Multiple-Document Interface (MDI) application is the MDI parent form.</span></span> <span data-ttu-id="79b84-107">Toto je formulář, který obsahuje podřízených oken MDI, které jsou dílčí windows, ve kterém uživatel komunikuje aplikace MDI.</span><span class="sxs-lookup"><span data-stu-id="79b84-107">This is the form that contains the MDI child windows, which are the sub-windows wherein the user interacts with the MDI application.</span></span> <span data-ttu-id="79b84-108">Vytvoření formuláře MDI nadřazené je snadné, v Návrháři formulářů a programově.</span><span class="sxs-lookup"><span data-stu-id="79b84-108">Creating an MDI parent form is easy, both in the Windows Forms Designer and programmatically.</span></span>  
  
### <a name="to-create-an-mdi-parent-form-at-design-time"></a><span data-ttu-id="79b84-109">K vytvoření formuláře MDI nadřazené v době návrhu</span><span class="sxs-lookup"><span data-stu-id="79b84-109">To create an MDI parent form at design time</span></span>  
  
1.  <span data-ttu-id="79b84-110">Vytvořte projekt aplikace Windows.</span><span class="sxs-lookup"><span data-stu-id="79b84-110">Create a Windows Application project.</span></span>  
  
2.  <span data-ttu-id="79b84-111">V **vlastnosti** nastavte <xref:System.Windows.Forms.Form.IsMdiContainer%2A> vlastnost **true**.</span><span class="sxs-lookup"><span data-stu-id="79b84-111">In the **Properties** window, set the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to **true**.</span></span>  
  
     <span data-ttu-id="79b84-112">Tento formulář označí jako kontejner MDI pro podřízené windows.</span><span class="sxs-lookup"><span data-stu-id="79b84-112">This designates the form as an MDI container for child windows.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="79b84-113">Při nastavení vlastností ve **vlastnosti** okno, můžete také nastavit `WindowState` vlastnost **Maximized**, pokud chcete, protože je to nejjednodušší provádět k manipulaci s podřízených oken MDI, pokud je nadřazený formulář Maximalizovaný.</span><span class="sxs-lookup"><span data-stu-id="79b84-113">While setting properties in the **Properties** window, you can also set the `WindowState` property to **Maximized**, if you like, as it is easiest to manipulate MDI child windows when the parent form is maximized.</span></span> <span data-ttu-id="79b84-114">Kromě toho Pamatujte, že jsou okraje nadřazeného formuláře MDI vyzvedne, až bude barvu systému (set v Ovládacích panelech systému Windows), místo barvu pozadí nastavíte pomocí <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="79b84-114">Additionally, be aware that the edge of the MDI parent form will pick up the system color (set in the Windows System Control Panel), rather than the back color you set using the <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> property.</span></span>  
  
3.  <span data-ttu-id="79b84-115">Z **sada nástrojů**, přetáhněte ji **MenuStrip** ovládacího prvku do formuláře.</span><span class="sxs-lookup"><span data-stu-id="79b84-115">From the **Toolbox**, drag a **MenuStrip** control to the form.</span></span> <span data-ttu-id="79b84-116">Vytvořit položku nabídky nejvyšší úrovně s **Text** vlastnost nastavena na hodnotu **& souboru** s názvem položky podnabídky **& Nový** a **& Zavřít**.</span><span class="sxs-lookup"><span data-stu-id="79b84-116">Create a top-level menu item with the **Text** property set to **&File** with submenu items called **&New** and **&Close**.</span></span> <span data-ttu-id="79b84-117">Také vytvořit nabídku nejvyšší úrovně položky názvem **& okno**.</span><span class="sxs-lookup"><span data-stu-id="79b84-117">Also create a top-level menu item called **&Window**.</span></span>  
  
     <span data-ttu-id="79b84-118">První nabídky vytvoří a skrytí položek nabídky v době běhu, a druhá nabídka bude sledovat otevřete podřízených oken MDI.</span><span class="sxs-lookup"><span data-stu-id="79b84-118">The first menu will create and hide menu items at run time, and the second menu will keep track of the open MDI child windows.</span></span> <span data-ttu-id="79b84-119">V tomto okamžiku jste vytvořili nadřazeného okna MDI.</span><span class="sxs-lookup"><span data-stu-id="79b84-119">At this point, you have created an MDI parent window.</span></span>  
  
4.  <span data-ttu-id="79b84-120">Stiskněte klávesu **F5** ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="79b84-120">Press **F5** to run the application.</span></span> <span data-ttu-id="79b84-121">Informace o vytváření podřízeného MDI windows, které fungují v rámci nadřazeného formuláře MDI najdete v tématu [postupy: vytváření podřízených formulářů MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md).</span><span class="sxs-lookup"><span data-stu-id="79b84-121">For information about creating MDI child windows that operate within the MDI parent form, see [How to: Create MDI Child Forms](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79b84-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="79b84-122">See Also</span></span>  
 [<span data-ttu-id="79b84-123">Aplikace MDI (Multiple-Document Interface)</span><span class="sxs-lookup"><span data-stu-id="79b84-123">Multiple-Document Interface (MDI) Applications</span></span>](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [<span data-ttu-id="79b84-124">Postupy: Vytváření podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="79b84-124">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="79b84-125">Postupy: Určení podřízeného prvku aktivního MDI</span><span class="sxs-lookup"><span data-stu-id="79b84-125">How to: Determine the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 [<span data-ttu-id="79b84-126">Postupy: Odesílání dat do aktivního podřízeného MDI</span><span class="sxs-lookup"><span data-stu-id="79b84-126">How to: Send Data to the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 [<span data-ttu-id="79b84-127">Postupy: Uspořádání podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="79b84-127">How to: Arrange MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
