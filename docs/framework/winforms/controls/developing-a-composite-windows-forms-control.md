---
title: Vývoj složeného ovládacího prvku Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], composite controls
- composite controls [Windows Forms]
- composite controls [Windows Forms], Windows Forms
- controls [Windows Forms], composite
ms.assetid: d086f2a3-baa3-4e09-b40c-a5bb3cfc51a6
ms.openlocfilehash: 9ccbf3de3f5c65b99a06c29ffce4c96896d11fae
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015959"
---
# <a name="develop-a-composite-windows-forms-control"></a><span data-ttu-id="f6cbd-102">Vývoj složeného ovládacího prvku model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f6cbd-102">Develop a composite Windows Forms control</span></span>

<span data-ttu-id="f6cbd-103">Složený ovládací prvek model Windows Forms lze vyvinout kombinací dalších ovládacích prvků model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f6cbd-103">You can develop a composite Windows Forms control by combining other Windows Forms controls.</span></span> <span data-ttu-id="f6cbd-104">Složené ovládací prvky, které <xref:System.Web.UI.UserControl> jsou odvozeny z, se nazývají uživatelské ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="f6cbd-104">Composite controls that derive from <xref:System.Web.UI.UserControl> are called user controls.</span></span> <span data-ttu-id="f6cbd-105">Základní třída <xref:System.Windows.Forms.UserControl>, poskytuje směrování klávesnice pro podřízené ovládací prvky, čímž zajišťuje, aby podřízené ovládací prvky mohly získat fokus.</span><span class="sxs-lookup"><span data-stu-id="f6cbd-105">The base class, <xref:System.Windows.Forms.UserControl>, provides keyboard routing for the child controls, thus ensuring that child controls can receive focus.</span></span> <span data-ttu-id="f6cbd-106">Příklad uživatelského ovládacího prvku naleznete v <xref:System.Windows.Forms.UserControl> ukázce v [tématu How to: Použití atributů v ovládacích prvcích](how-to-apply-attributes-in-windows-forms-controls.md)model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f6cbd-106">For an example of a user control, see the <xref:System.Windows.Forms.UserControl> sample in [How to: Apply Attributes in Windows Forms Controls](how-to-apply-attributes-in-windows-forms-controls.md).</span></span>

<span data-ttu-id="f6cbd-107">Návrhář model Windows Forms v aplikaci Visual Studio poskytuje bohatou podporu při návrhu pro vytváření uživatelských ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="f6cbd-107">The Windows Forms designer in Visual Studio provides rich design-time support for authoring user controls.</span></span>

- [<span data-ttu-id="f6cbd-108">Postupy: Zobrazení ovládacího prvku v dialogovém okně zvolit položky sady nástrojů</span><span class="sxs-lookup"><span data-stu-id="f6cbd-108">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)

- [<span data-ttu-id="f6cbd-109">Návod: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="f6cbd-109">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](serializing-collections-designerserializationvisibilityattribute.md)

- [<span data-ttu-id="f6cbd-110">Návod: Dědění z ovládacího prvku model Windows Forms pomocí vizuáluC#</span><span class="sxs-lookup"><span data-stu-id="f6cbd-110">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)

- [<span data-ttu-id="f6cbd-111">Postupy: Poskytnutí rastrového obrázku panelu nástrojů pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="f6cbd-111">How to: Provide a Toolbox Bitmap for a Control</span></span>](how-to-provide-a-toolbox-bitmap-for-a-control.md)

- [<span data-ttu-id="f6cbd-112">Postupy: Zdědit z existujících ovládacích prvků model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f6cbd-112">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)

- [<span data-ttu-id="f6cbd-113">Návod: Ladění vlastních ovládacích prvků model Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="f6cbd-113">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)

- [<span data-ttu-id="f6cbd-114">Postupy: Zdědit z třídy ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="f6cbd-114">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)

- [<span data-ttu-id="f6cbd-115">Postupy: Testování chování prvku UserControl v době běhu</span><span class="sxs-lookup"><span data-stu-id="f6cbd-115">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)

- [<span data-ttu-id="f6cbd-116">Postupy: Zarovnání ovládacího prvku na okraje formulářů v době návrhu</span><span class="sxs-lookup"><span data-stu-id="f6cbd-116">How to: Align a Control to the Edges of Forms at Design Time</span></span>](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)

- [<span data-ttu-id="f6cbd-117">Postupy: Zdědit z třídy UserControl</span><span class="sxs-lookup"><span data-stu-id="f6cbd-117">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)

- [<span data-ttu-id="f6cbd-118">Postupy: Vytváření ovládacích prvků pro model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f6cbd-118">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)

- [<span data-ttu-id="f6cbd-119">Postupy: Vytváření složených ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="f6cbd-119">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)

- [<span data-ttu-id="f6cbd-120">Návod: Vytváření složeného ovládacího prvku pomocí vizuáluC#</span><span class="sxs-lookup"><span data-stu-id="f6cbd-120">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)

- [<span data-ttu-id="f6cbd-121">Návod: Vytvoření ovládacího prvku model Windows Forms, který využívá výhod funkcí nástroje Visual Studio pro dobu návrhu</span><span class="sxs-lookup"><span data-stu-id="f6cbd-121">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)

- <span data-ttu-id="f6cbd-122">[Postupy: Vytvoření model Windows Formsho ovládacího prvku, který bude využívat funkce pro dobu návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="f6cbd-122">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span></span>

## <a name="see-also"></a><span data-ttu-id="f6cbd-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f6cbd-123">See also</span></span>

- [<span data-ttu-id="f6cbd-124">Postupy: Použití atributů v ovládacích prvcích model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f6cbd-124">How to: Apply Attributes in Windows Forms Controls</span></span>](how-to-apply-attributes-in-windows-forms-controls.md)
- [<span data-ttu-id="f6cbd-125">Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f6cbd-125">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="f6cbd-126">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="f6cbd-126">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
