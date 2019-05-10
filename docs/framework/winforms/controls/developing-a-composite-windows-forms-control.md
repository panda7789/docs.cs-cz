---
title: Vývoj složeného ovládacího prvku Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], composite controls
- composite controls [Windows Forms]
- composite controls [Windows Forms], Windows Forms
- controls [Windows Forms], composite
ms.assetid: d086f2a3-baa3-4e09-b40c-a5bb3cfc51a6
ms.openlocfilehash: 2d6220a95d20cc0ab8ea1cdeb396804dfbcef8a1
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211480"
---
# <a name="develop-a-composite-windows-forms-control"></a><span data-ttu-id="30559-102">Vývoj složeného ovládacího prvku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="30559-102">Develop a composite Windows Forms control</span></span>

<span data-ttu-id="30559-103">Můžete vyvíjet složeného ovládacího prvku Windows Forms kombinací jiných ovládacích prvků Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="30559-103">You can develop a composite Windows Forms control by combining other Windows Forms controls.</span></span> <span data-ttu-id="30559-104">Složené ovládací prvky, které jsou odvozeny z <xref:System.Web.UI.UserControl> se nazývají uživatelské ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="30559-104">Composite controls that derive from <xref:System.Web.UI.UserControl> are called user controls.</span></span> <span data-ttu-id="30559-105">Základní třída <xref:System.Windows.Forms.UserControl>, poskytuje směrování pro podřízené ovládací prvky, čímž zajišťuje, že podřízených ovládacích prvků může získat fokus klávesnice.</span><span class="sxs-lookup"><span data-stu-id="30559-105">The base class, <xref:System.Windows.Forms.UserControl>, provides keyboard routing for the child controls, thus ensuring that child controls can receive focus.</span></span> <span data-ttu-id="30559-106">Příkladem uživatelského ovládacího prvku, naleznete v tématu <xref:System.Windows.Forms.UserControl> ukázku v [jak: Použití atributů v ovládacích prvcích Windows Forms](how-to-apply-attributes-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="30559-106">For an example of a user control, see the <xref:System.Windows.Forms.UserControl> sample in [How to: Apply Attributes in Windows Forms Controls](how-to-apply-attributes-in-windows-forms-controls.md).</span></span>

<span data-ttu-id="30559-107">Návrhář formulářů Windows v sadě Visual Studio poskytuje bohatou podporu návrhu pro vytváření uživatelských ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="30559-107">The Windows Forms designer in Visual Studio provides rich design-time support for authoring user controls.</span></span>

- [<span data-ttu-id="30559-108">Postupy: Zobrazení ovládacího prvku v zvolit položky panelu nástrojů – dialogové okno</span><span class="sxs-lookup"><span data-stu-id="30559-108">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)

- [<span data-ttu-id="30559-109">Návod: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="30559-109">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](serializing-collections-designerserializationvisibilityattribute.md)

- [<span data-ttu-id="30559-110">Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C#</span><span class="sxs-lookup"><span data-stu-id="30559-110">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)

- [<span data-ttu-id="30559-111">Postupy: Poskytnutí rastrového obrázku panelu nástrojů pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="30559-111">How to: Provide a Toolbox Bitmap for a Control</span></span>](how-to-provide-a-toolbox-bitmap-for-a-control.md)

- [<span data-ttu-id="30559-112">Postupy: Dědění z existujících Windows Forms ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="30559-112">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)

- [<span data-ttu-id="30559-113">Návod: Ovládací prvky ladění vlastního Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="30559-113">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)

- [<span data-ttu-id="30559-114">Postupy: Dědit ze třídy Control</span><span class="sxs-lookup"><span data-stu-id="30559-114">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)

- [<span data-ttu-id="30559-115">Postupy: Testování běhového chování UserControl</span><span class="sxs-lookup"><span data-stu-id="30559-115">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)

- [<span data-ttu-id="30559-116">Postupy: Zarovnání ovládacího prvku k okrajům formulářů během návrhu</span><span class="sxs-lookup"><span data-stu-id="30559-116">How to: Align a Control to the Edges of Forms at Design Time</span></span>](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)

- [<span data-ttu-id="30559-117">Postupy: Dědit ze třídy UserControl</span><span class="sxs-lookup"><span data-stu-id="30559-117">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)

- [<span data-ttu-id="30559-118">Postupy: Autor ovládacích prvků Windows Forms</span><span class="sxs-lookup"><span data-stu-id="30559-118">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)

- [<span data-ttu-id="30559-119">Postupy: Vytváření složených ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="30559-119">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)

- [<span data-ttu-id="30559-120">Návod: Vytvoření složeného ovládacího prvku s jazykem Visual Basic</span><span class="sxs-lookup"><span data-stu-id="30559-120">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)

- [<span data-ttu-id="30559-121">Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#</span><span class="sxs-lookup"><span data-stu-id="30559-121">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)

- [<span data-ttu-id="30559-122">Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual Basic</span><span class="sxs-lookup"><span data-stu-id="30559-122">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)

- [<span data-ttu-id="30559-123">Návod: Vytvoření ovládacího prvku Windows Forms, který využívá funkce sady Visual Studio Design-Time</span><span class="sxs-lookup"><span data-stu-id="30559-123">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)

- <span data-ttu-id="30559-124">[Postupy: Vytvoření ovládacího prvku Windows Forms, který využívá funkce návrhu aplikace](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="30559-124">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span></span>

## <a name="see-also"></a><span data-ttu-id="30559-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30559-125">See also</span></span>

- [<span data-ttu-id="30559-126">Postupy: Použití atributů v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="30559-126">How to: Apply Attributes in Windows Forms Controls</span></span>](how-to-apply-attributes-in-windows-forms-controls.md)
- [<span data-ttu-id="30559-127">Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="30559-127">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="30559-128">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="30559-128">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
