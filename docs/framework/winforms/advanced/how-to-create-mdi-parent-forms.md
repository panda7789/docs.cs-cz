---
title: 'Postupy: Vytváření nadřazených formulářů MDI'
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms
- MDI [Windows Forms], creating forms
ms.assetid: 12c71221-2377-4bb6-b10b-7b4b300fd462
ms.openlocfilehash: 2aa4261d6354f744f000f36a87e70a39f5c004ea
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211374"
---
# <a name="how-to-create-mdi-parent-forms"></a><span data-ttu-id="26d02-102">Postupy: Vytváření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="26d02-102">How to: Create MDI Parent Forms</span></span>

> [!IMPORTANT]
> <span data-ttu-id="26d02-103">Toto téma používá <xref:System.Windows.Forms.MainMenu> ovládací prvek, který byl nahrazen <xref:System.Windows.Forms.MenuStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="26d02-103">This topic uses the <xref:System.Windows.Forms.MainMenu> control, which has been replaced by the <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="26d02-104"><xref:System.Windows.Forms.MainMenu> Ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete.</span><span class="sxs-lookup"><span data-stu-id="26d02-104">The <xref:System.Windows.Forms.MainMenu> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="26d02-105">Informace o vytváření MDI nadřazený formulář s využitím <xref:System.Windows.Forms.MenuStrip>, naleznete v tématu [jak: Vytvoření seznamu okna MDI pomocí MenuStrip](../controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="26d02-105">For information about creating a MDI parent Form by using a <xref:System.Windows.Forms.MenuStrip>, see [How to: Create an MDI Window List with MenuStrip](../controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).</span></span>

<span data-ttu-id="26d02-106">Základ pro aplikace rozhraní více dokumentů (MDI) je nadřazený formulář MDI.</span><span class="sxs-lookup"><span data-stu-id="26d02-106">The foundation of a Multiple-Document Interface (MDI) application is the MDI parent form.</span></span> <span data-ttu-id="26d02-107">Toto je formulář, který obsahuje podřízených oken MDI, které jsou dílčí windows, ve kterém uživatel pracuje v aplikaci MDI.</span><span class="sxs-lookup"><span data-stu-id="26d02-107">This is the form that contains the MDI child windows, which are the sub-windows wherein the user interacts with the MDI application.</span></span> <span data-ttu-id="26d02-108">Vytvoření nadřazený formulář MDI je jednoduché, v Návrháři formulářů Windows a prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="26d02-108">Creating an MDI parent form is easy, both in the Windows Forms Designer and programmatically.</span></span>

## <a name="create-an-mdi-parent-form-at-design-time"></a><span data-ttu-id="26d02-109">Vytvořit nadřazený formulář MDI v době návrhu</span><span class="sxs-lookup"><span data-stu-id="26d02-109">Create an MDI parent form at design time</span></span>

1. <span data-ttu-id="26d02-110">Vytvoření projektu aplikace Windows v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="26d02-110">Create a Windows Application project in Visual Studio.</span></span>

2. <span data-ttu-id="26d02-111">V **vlastnosti** okno, nastaveno <xref:System.Windows.Forms.Form.IsMdiContainer%2A> vlastnost **true**.</span><span class="sxs-lookup"><span data-stu-id="26d02-111">In the **Properties** window, set the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to **true**.</span></span>

     <span data-ttu-id="26d02-112">Ta určuje formuláře jako kontejnerem MDI pro podřízená okna.</span><span class="sxs-lookup"><span data-stu-id="26d02-112">This designates the form as an MDI container for child windows.</span></span>

    > [!NOTE]
    > <span data-ttu-id="26d02-113">Při nastavování vlastností **vlastnosti** okna, můžete také nastavit `WindowState` vlastnost **Maximized**, pokud chcete, můžete, protože je nejjednodušší k manipulaci s podřízených oken MDI, pokud je nadřazený formulář maximalizované.</span><span class="sxs-lookup"><span data-stu-id="26d02-113">While setting properties in the **Properties** window, you can also set the `WindowState` property to **Maximized**, if you like, as it is easiest to manipulate MDI child windows when the parent form is maximized.</span></span> <span data-ttu-id="26d02-114">Kromě toho mějte na paměti, že okraj nadřazený formulář MDI vyzvedne, až bude systémovou barvou (nastavení v Ovládacích panelech systému Windows), nikoli barva pozadí nastavíte pomocí <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="26d02-114">Additionally, be aware that the edge of the MDI parent form will pick up the system color (set in the Windows System Control Panel), rather than the back color you set using the <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> property.</span></span>

3. <span data-ttu-id="26d02-115">Z **nástrojů**, přetáhněte **MenuStrip** ovládacího prvku na formuláři.</span><span class="sxs-lookup"><span data-stu-id="26d02-115">From the **Toolbox**, drag a **MenuStrip** control to the form.</span></span> <span data-ttu-id="26d02-116">Vytvoření položky nabídek nejvyšší úrovně s **Text** vlastnost nastavena na hodnotu **& soubor** s názvem položky podnabídky **& Nový** a **Zavřít**.</span><span class="sxs-lookup"><span data-stu-id="26d02-116">Create a top-level menu item with the **Text** property set to **&File** with submenu items called **&New** and **&Close**.</span></span> <span data-ttu-id="26d02-117">Také vytvořit nabídek nejvyšší úrovně položky volá **& okno**.</span><span class="sxs-lookup"><span data-stu-id="26d02-117">Also create a top-level menu item called **&Window**.</span></span>

     <span data-ttu-id="26d02-118">Vytvoří a skrytí položek nabídky v době běhu nabídce první a druhé nabídky bude sledovat, otevřete podřízených oken MDI.</span><span class="sxs-lookup"><span data-stu-id="26d02-118">The first menu will create and hide menu items at run time, and the second menu will keep track of the open MDI child windows.</span></span> <span data-ttu-id="26d02-119">V tomto okamžiku jste vytvořili nadřazeného okna MDI.</span><span class="sxs-lookup"><span data-stu-id="26d02-119">At this point, you have created an MDI parent window.</span></span>

4. <span data-ttu-id="26d02-120">Stisknutím klávesy **F5** ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="26d02-120">Press **F5** to run the application.</span></span> <span data-ttu-id="26d02-121">Informace o vytváření podřízeného MDI windows, které působí v rámci nadřazený formulář MDI, naleznete v tématu [jak: Vytváření podřízených formulářů MDI](how-to-create-mdi-child-forms.md).</span><span class="sxs-lookup"><span data-stu-id="26d02-121">For information about creating MDI child windows that operate within the MDI parent form, see [How to: Create MDI Child Forms](how-to-create-mdi-child-forms.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="26d02-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="26d02-122">See also</span></span>

- [<span data-ttu-id="26d02-123">Aplikace MDI (Multiple-Document Interface)</span><span class="sxs-lookup"><span data-stu-id="26d02-123">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="26d02-124">Postupy: Vytváření podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="26d02-124">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="26d02-125">Postupy: Určení podřízeného prvku aktivního MDI</span><span class="sxs-lookup"><span data-stu-id="26d02-125">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="26d02-126">Postupy: Odesílání dat do aktivního podřízeného MDI</span><span class="sxs-lookup"><span data-stu-id="26d02-126">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="26d02-127">Postupy: Uspořádání podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="26d02-127">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
