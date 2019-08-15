---
title: 'Postupy: Vytváření složených ovládacích prvků'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], creating composite controls
- user controls [Windows Forms], creating
- user controls [Windows Forms], inheriting from
- composite controls [Windows Forms], creating
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
ms.openlocfilehash: 7b0ee8efa62175e2ced2a810ca6dd76e8adc103b
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039885"
---
# <a name="how-to-author-composite-controls"></a><span data-ttu-id="2984f-102">Postupy: Vytváření složených ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="2984f-102">How to: Author Composite Controls</span></span>

<span data-ttu-id="2984f-103">Složené ovládací prvky mohou být zaměstnány mnoha způsoby.</span><span class="sxs-lookup"><span data-stu-id="2984f-103">Composite controls can be employed in many ways.</span></span> <span data-ttu-id="2984f-104">Můžete je vytvořit jako součást projektu desktopové aplikace systému Windows a použít ji pouze pro formuláře v projektu.</span><span class="sxs-lookup"><span data-stu-id="2984f-104">You can author them as part of a Windows desktop application project, and use them only on forms in the project.</span></span> <span data-ttu-id="2984f-105">Nebo je můžete vytvořit v projektu knihovny ovládacích prvků systému Windows, zkompilovat projekt do sestavení a použít ovládací prvky v jiných projektech.</span><span class="sxs-lookup"><span data-stu-id="2984f-105">Or you can author them in a Windows Control Library project, compile the project into an assembly, and use the controls in other projects.</span></span> <span data-ttu-id="2984f-106">Z nich můžete dokonce dědit a použít dědění vizuálu k jejich rychlému přizpůsobení pro zvláštní účely.</span><span class="sxs-lookup"><span data-stu-id="2984f-106">You can even inherit from them and use visual inheritance to customize them quickly for special purposes.</span></span>

> [!NOTE]
> <span data-ttu-id="2984f-107">Chcete-li vytvořit složený ovládací prvek pro použití ve webových formulářích, přečtěte si téma [vývoj vlastních ovládacích prvků ASP.NET serveru](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="2984f-107">If you want to author a composite control to use on Web Forms, see [Developing Custom ASP.NET Server Controls](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span></span>

## <a name="to-author-a-composite-control"></a><span data-ttu-id="2984f-108">Vytváření složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="2984f-108">To author a composite control</span></span>

1. <span data-ttu-id="2984f-109">V aplikaci Visual Studio vytvořte nový projekt **aplikace systému Windows** s `DemoControlHost`názvem.</span><span class="sxs-lookup"><span data-stu-id="2984f-109">In Visual Studio, create a new **Windows Application** project called `DemoControlHost`.</span></span>

2. <span data-ttu-id="2984f-110">V nabídce **projekt** klikněte na příkaz **Přidat uživatelský ovládací prvek**.</span><span class="sxs-lookup"><span data-stu-id="2984f-110">On the **Project** menu, click **Add User Control**.</span></span>

3. <span data-ttu-id="2984f-111">V dialogovém okně **Přidat novou položku** poskytněte souboru třídy (soubor. vb nebo. cs) název, který má složený ovládací prvek mít.</span><span class="sxs-lookup"><span data-stu-id="2984f-111">In the **Add New Item** dialog box, give the class file (.vb or .cs file) the name you want the composite control to have.</span></span>

4. <span data-ttu-id="2984f-112">Vyberte tlačítko **Přidat** , chcete-li vytvořit soubor třídy pro složený ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="2984f-112">Select the **Add** button to create the class file for the composite control.</span></span>

5. <span data-ttu-id="2984f-113">Přidejte ovládací prvky ze **sady nástrojů** do složené plochy ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2984f-113">Add controls from the **Toolbox** to the composite control surface.</span></span>

6. <span data-ttu-id="2984f-114">Umístěte kód do procedur událostí pro zpracování událostí vyvolaných složeným ovládacím prvkem nebo ovládacími prvky prvku.</span><span class="sxs-lookup"><span data-stu-id="2984f-114">Place code in event procedures, to handle events raised by the composite control or by its constituent controls.</span></span>

7. <span data-ttu-id="2984f-115">Zavřete návrháře složeného ovládacího prvku a uložte soubor po zobrazení výzvy.</span><span class="sxs-lookup"><span data-stu-id="2984f-115">Close the designer for the composite control, and save the file when you are prompted.</span></span>

8. <span data-ttu-id="2984f-116">Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="2984f-116">On the **Build** menu, click **Build Solution**.</span></span>

     <span data-ttu-id="2984f-117">Aby se v **sadě nástrojů**zobrazovaly vlastní ovládací prvky, musí být projekt sestaven.</span><span class="sxs-lookup"><span data-stu-id="2984f-117">The project must be built in order for custom controls to appear in the **Toolbox**.</span></span>

9. <span data-ttu-id="2984f-118">Použijte kartu **DemoControlHost** sady **nástrojů** k přidání instancí ovládacího prvku do `Form1`.</span><span class="sxs-lookup"><span data-stu-id="2984f-118">Use the **DemoControlHost** tab of the **Toolbox** to add instances of your control to `Form1`.</span></span>

## <a name="to-author-a-control-class-library"></a><span data-ttu-id="2984f-119">Chcete-li vytvořit knihovnu tříd ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="2984f-119">To author a control class library</span></span>

1. <span data-ttu-id="2984f-120">Otevřete nový projekt **knihovny ovládacích prvků systému Windows** .</span><span class="sxs-lookup"><span data-stu-id="2984f-120">Open a new **Windows Control Library** project.</span></span>

     <span data-ttu-id="2984f-121">Ve výchozím nastavení projekt obsahuje složený ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="2984f-121">By default, the project contains a composite control.</span></span>

2. <span data-ttu-id="2984f-122">Přidejte ovládací prvky a kód, jak je popsáno výše v postupu.</span><span class="sxs-lookup"><span data-stu-id="2984f-122">Add controls and code as described in the procedure above.</span></span>

3. <span data-ttu-id="2984f-123">Vyberte ovládací prvek, který nechcete dědit třídy, a nastavte vlastnost modifikátory tohoto ovládacího prvku na hodnotu **Private**.</span><span class="sxs-lookup"><span data-stu-id="2984f-123">Choose a control you do not want inheriting classes to change, and set the **Modifiers** property of this control to **Private**.</span></span>

4. <span data-ttu-id="2984f-124">Sestavení knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="2984f-124">Build the DLL.</span></span>

## <a name="to-inherit-from-a-composite-control-in-a-control-class-library"></a><span data-ttu-id="2984f-125">Dědění ze složeného ovládacího prvku v knihovně tříd ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="2984f-125">To inherit from a composite control in a control class library</span></span>

1. <span data-ttu-id="2984f-126">V nabídce **soubor** přejděte na příkaz **Přidat** a vyberte **Nový projekt** a přidejte do řešení nový projekt **aplikace pro Windows** .</span><span class="sxs-lookup"><span data-stu-id="2984f-126">On the **File** menu, point to **Add** and select **New Project** to add a new **Windows Application** project to the solution.</span></span>

2. <span data-ttu-id="2984f-127">V **Průzkumník řešení**klikněte pravým tlačítkem myši na složku **odkazy** pro nový projekt a vyberte možnost **Přidat odkaz** . tím otevřete dialogové okno **Přidat odkaz** .</span><span class="sxs-lookup"><span data-stu-id="2984f-127">In **Solution Explorer**, right-click the **References** folder for the new project and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

3. <span data-ttu-id="2984f-128">Vyberte kartu **projekty** a dvakrát klikněte na projekt knihovny ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="2984f-128">Select the **Projects** tab and double-click your control library project.</span></span>

4. <span data-ttu-id="2984f-129">Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="2984f-129">On the **Build** menu, click **Build Solution**.</span></span>

5. <span data-ttu-id="2984f-130">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt knihovny ovládacích prvků a v místní nabídce vyberte možnost **Přidat novou položku** .</span><span class="sxs-lookup"><span data-stu-id="2984f-130">In **Solution Explorer**, right-click your control library project and select **Add New Item** from the shortcut menu.</span></span>

6. <span data-ttu-id="2984f-131">Vyberte šablonu **zděděného uživatelského ovládacího prvku** z dialogového okna **Přidat novou položku** .</span><span class="sxs-lookup"><span data-stu-id="2984f-131">Select the **Inherited User Control** template from the **Add New Item** dialog box.</span></span>

7. <span data-ttu-id="2984f-132">V dialogovém okně **Výběr dědičnosti** dvakrát klikněte na ovládací prvek, ze kterého chcete dědit.</span><span class="sxs-lookup"><span data-stu-id="2984f-132">In the **Inheritance Picker** dialog box, double-click the control you want to inherit from.</span></span>

     <span data-ttu-id="2984f-133">Do projektu se přidá nový ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="2984f-133">A new control is added to your project.</span></span>

8. <span data-ttu-id="2984f-134">Otevřete vizuálního návrháře pro nový ovládací prvek a přidejte další ovládací prvky prvku.</span><span class="sxs-lookup"><span data-stu-id="2984f-134">Open the visual designer for the new control and add additional constituent controls.</span></span>

     <span data-ttu-id="2984f-135">Můžete vidět ovládací prvky prvku, které byly zděděny ze složeného ovládacího prvku v knihovně DLL, a můžete změnit vlastnosti ovládacích prvků, jejichž Modifikátory vlastnost je **Veřejná**.</span><span class="sxs-lookup"><span data-stu-id="2984f-135">You can see the constituent controls that were inherited from the composite control in your DLL, and you can alter the properties of controls whose **Modifiers** property is **Public**.</span></span> <span data-ttu-id="2984f-136">Nemůžete změnit vlastnosti ovládacího prvku, jehož vlastnost modifikátory je **soukromá**.</span><span class="sxs-lookup"><span data-stu-id="2984f-136">You cannot change the properties of the control whose **Modifiers** property is **Private**.</span></span>

## <a name="see-also"></a><span data-ttu-id="2984f-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2984f-137">See also</span></span>

- [<span data-ttu-id="2984f-138">Návod: Vytváření složeného ovládacího prvku pomocí Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2984f-138">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [<span data-ttu-id="2984f-139">Návod: Vytváření složeného ovládacího prvku pomocí vizuáluC#</span><span class="sxs-lookup"><span data-stu-id="2984f-139">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [<span data-ttu-id="2984f-140">Návod: Dědění z ovládacího prvku model Windows Forms s Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2984f-140">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)
- [<span data-ttu-id="2984f-141">Návod: Dědění z ovládacího prvku model Windows Forms pomocí vizuáluC#</span><span class="sxs-lookup"><span data-stu-id="2984f-141">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
- [<span data-ttu-id="2984f-142">Doporučení ohledně typu ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="2984f-142">Control Type Recommendations</span></span>](control-type-recommendations.md)
- [<span data-ttu-id="2984f-143">Postupy: Vytváření ovládacích prvků pro model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2984f-143">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="2984f-144">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="2984f-144">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
