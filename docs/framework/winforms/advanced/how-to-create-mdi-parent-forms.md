---
title: 'Postupy: Vytváření nadřazených formulářů MDI'
description: Naučte se vytvořit nadřazený formulář MDI programově a pomocí Návrhář formulářů.
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms
- MDI [Windows Forms], creating forms
ms.assetid: 12c71221-2377-4bb6-b10b-7b4b300fd462
ms.openlocfilehash: d387837a565ca247f62828c19f353990b35117c7
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174702"
---
# <a name="how-to-create-mdi-parent-forms"></a><span data-ttu-id="726aa-103">Postupy: Vytváření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="726aa-103">How to: Create MDI Parent Forms</span></span>

> [!IMPORTANT]
> <span data-ttu-id="726aa-104">Toto téma používá <xref:System.Windows.Forms.MainMenu> ovládací prvek, který byl nahrazen <xref:System.Windows.Forms.MenuStrip> ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="726aa-104">This topic uses the <xref:System.Windows.Forms.MainMenu> control, which has been replaced by the <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="726aa-105"><xref:System.Windows.Forms.MainMenu>Ovládací prvek se zachovává pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.</span><span class="sxs-lookup"><span data-stu-id="726aa-105">The <xref:System.Windows.Forms.MainMenu> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="726aa-106">Informace o vytvoření nadřazeného formuláře MDI pomocí a <xref:System.Windows.Forms.MenuStrip> naleznete v tématu [How to: Create a Window MDI list with MenuStrip](../controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="726aa-106">For information about creating a MDI parent Form by using a <xref:System.Windows.Forms.MenuStrip>, see [How to: Create an MDI Window List with MenuStrip](../controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).</span></span>

<span data-ttu-id="726aa-107">Základem aplikace MDI (Multiple Document Interface) je nadřazený formulář MDI.</span><span class="sxs-lookup"><span data-stu-id="726aa-107">The foundation of a Multiple-Document Interface (MDI) application is the MDI parent form.</span></span> <span data-ttu-id="726aa-108">Jedná se o formulář, který obsahuje podřízená okna MDI, což je dílčí systém Windows, podle kterého uživatel pracuje s aplikací MDI.</span><span class="sxs-lookup"><span data-stu-id="726aa-108">This is the form that contains the MDI child windows, which are the sub-windows wherein the user interacts with the MDI application.</span></span> <span data-ttu-id="726aa-109">Vytvoření nadřazeného formuláře MDI je jednoduché v Návrhář formulářů i programově.</span><span class="sxs-lookup"><span data-stu-id="726aa-109">Creating an MDI parent form is easy, both in the Windows Forms Designer and programmatically.</span></span>

## <a name="create-an-mdi-parent-form-at-design-time"></a><span data-ttu-id="726aa-110">Vytvoření nadřazeného formuláře MDI v době návrhu</span><span class="sxs-lookup"><span data-stu-id="726aa-110">Create an MDI parent form at design time</span></span>

1. <span data-ttu-id="726aa-111">Vytvořte projekt aplikace pro Windows v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="726aa-111">Create a Windows Application project in Visual Studio.</span></span>

2. <span data-ttu-id="726aa-112">V okně **vlastnosti** nastavte <xref:System.Windows.Forms.Form.IsMdiContainer%2A> vlastnost na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="726aa-112">In the **Properties** window, set the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to **true**.</span></span>

     <span data-ttu-id="726aa-113">Tato položka označuje formulář jako kontejner MDI pro podřízená okna.</span><span class="sxs-lookup"><span data-stu-id="726aa-113">This designates the form as an MDI container for child windows.</span></span>

    > [!NOTE]
    > <span data-ttu-id="726aa-114">Při nastavování vlastností v okně **vlastnosti** můžete také nastavit `WindowState` vlastnost na **maximalizovat**, pokud chcete, protože je nejjednodušší pracovat s podřízenými okny MDI při maximalizaci nadřazeného formuláře.</span><span class="sxs-lookup"><span data-stu-id="726aa-114">While setting properties in the **Properties** window, you can also set the `WindowState` property to **Maximized**, if you like, as it is easiest to manipulate MDI child windows when the parent form is maximized.</span></span> <span data-ttu-id="726aa-115">Kromě toho mějte na paměti, že hrana nadřazeného formuláře MDI vybere systémovou barvu (nastavenou v ovládacím panelu systém Windows) místo barvy pozadí, kterou jste nastavili pomocí <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="726aa-115">Additionally, be aware that the edge of the MDI parent form will pick up the system color (set in the Windows System Control Panel), rather than the back color you set using the <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> property.</span></span>

3. <span data-ttu-id="726aa-116">Z **panelu nástrojů**přetáhněte ovládací prvek **MenuStrip** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="726aa-116">From the **Toolbox**, drag a **MenuStrip** control to the form.</span></span> <span data-ttu-id="726aa-117">Vytvořte položku nabídky nejvyšší úrovně s vlastností **text** nastavenou na **&soubor** s položkami podnabídky s názvem **&New** a **&Close**.</span><span class="sxs-lookup"><span data-stu-id="726aa-117">Create a top-level menu item with the **Text** property set to **&File** with submenu items called **&New** and **&Close**.</span></span> <span data-ttu-id="726aa-118">Vytvořte také položku nabídky nejvyšší úrovně s názvem **&okno**.</span><span class="sxs-lookup"><span data-stu-id="726aa-118">Also create a top-level menu item called **&Window**.</span></span>

     <span data-ttu-id="726aa-119">První nabídka vytvoří a skryje položky nabídky za běhu a druhá nabídka bude sledovat otevřené podřízené okna MDI.</span><span class="sxs-lookup"><span data-stu-id="726aa-119">The first menu will create and hide menu items at run time, and the second menu will keep track of the open MDI child windows.</span></span> <span data-ttu-id="726aa-120">V tomto okamžiku jste vytvořili nadřazené okno MDI.</span><span class="sxs-lookup"><span data-stu-id="726aa-120">At this point, you have created an MDI parent window.</span></span>

4. <span data-ttu-id="726aa-121">Stisknutím klávesy **F5** spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="726aa-121">Press **F5** to run the application.</span></span> <span data-ttu-id="726aa-122">Informace o vytváření podřízených oken MDI, které pracují v nadřazeném formuláři MDI, naleznete v tématu [How to: Create MDI-podřízené formuláře](how-to-create-mdi-child-forms.md).</span><span class="sxs-lookup"><span data-stu-id="726aa-122">For information about creating MDI child windows that operate within the MDI parent form, see [How to: Create MDI Child Forms](how-to-create-mdi-child-forms.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="726aa-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="726aa-123">See also</span></span>

- [<span data-ttu-id="726aa-124">Aplikace MDI (Multiple-Document Interface)</span><span class="sxs-lookup"><span data-stu-id="726aa-124">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="726aa-125">Postupy: Vytváření podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="726aa-125">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="726aa-126">Postupy: Určení podřízeného prvku aktivního MDI</span><span class="sxs-lookup"><span data-stu-id="726aa-126">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="726aa-127">Postupy: Odesílání dat do aktivního podřízeného MDI</span><span class="sxs-lookup"><span data-stu-id="726aa-127">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="726aa-128">Postupy: Uspořádání podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="726aa-128">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
