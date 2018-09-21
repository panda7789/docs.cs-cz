---
title: 'Postupy: Vytváření složených ovládacích prvků'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], creating composite controls
- user controls [Windows Forms], creating
- user controls [Windows Forms], inheriting from
- composite controls [Windows Forms], creating
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
ms.openlocfilehash: 7abdeae4d19ceb6425f85e3cdd28f565a03d7ea4
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46537852"
---
# <a name="how-to-author-composite-controls"></a><span data-ttu-id="f4580-102">Postupy: Vytváření složených ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="f4580-102">How to: Author Composite Controls</span></span>
<span data-ttu-id="f4580-103">Složené ovládací prvky mohou být použity v mnoha způsoby.</span><span class="sxs-lookup"><span data-stu-id="f4580-103">Composite controls can be employed in many ways.</span></span> <span data-ttu-id="f4580-104">Můžete vytvářet je v rámci projektu aplikace klasické pracovní plochy Windows a používat pouze u formulářů v projektu.</span><span class="sxs-lookup"><span data-stu-id="f4580-104">You can author them as part of a Windows desktop application project, and use them only on forms in the project.</span></span> <span data-ttu-id="f4580-105">Nebo můžete vytvářet v projektu knihovny ovládací prvků Windows, zkompilujte projekt do sestavení a pomocí ovládacích prvků v jiných projektech.</span><span class="sxs-lookup"><span data-stu-id="f4580-105">Or you can author them in a Windows Control Library project, compile the project into an assembly, and use the controls in other projects.</span></span> <span data-ttu-id="f4580-106">Dokonce je možné zdědit z nich a můžete si je přizpůsobit rychle pro zvláštní účely vizuální dědění.</span><span class="sxs-lookup"><span data-stu-id="f4580-106">You can even inherit from them, and use visual inheritance to customize them quickly for special purposes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4580-107">Pokud chcete vytvořit složeného ovládacího prvku k použití na webové formuláře, naleznete v tématu [vývoj vlastních serverových ovládacích prvků ASP.NET](https://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).</span><span class="sxs-lookup"><span data-stu-id="f4580-107">If you want to author a composite control to use on Web Forms, see [Developing Custom ASP.NET Server Controls](https://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).</span></span>  
>   
>  <span data-ttu-id="f4580-108">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="f4580-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f4580-109">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="f4580-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f4580-110">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="f4580-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-author-a-composite-control"></a><span data-ttu-id="f4580-111">Pro vytvoření složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="f4580-111">To author a composite control</span></span>  
  
1.  <span data-ttu-id="f4580-112">Otevřete novou **aplikace Windows** projekt s názvem `DemoControlHost`.</span><span class="sxs-lookup"><span data-stu-id="f4580-112">Open a new **Windows Application** project called `DemoControlHost`.</span></span>  
  
2.  <span data-ttu-id="f4580-113">Na **projektu** nabídky, klikněte na tlačítko **přidat uživatelský ovládací prvek**.</span><span class="sxs-lookup"><span data-stu-id="f4580-113">On the **Project** menu, click **Add User Control**.</span></span>  
  
3.  <span data-ttu-id="f4580-114">V **přidat novou položku** dialogové okno, poskytují třídy soubor (.vb nebo .cs) název, který chcete mít složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f4580-114">In the **Add New Item** dialog box, give the class file (.vb or .cs file) the name you want the composite control to have.</span></span>  
  
4.  <span data-ttu-id="f4580-115">Vyberte **přidat** tlačítko pro vytvoření souboru třídy složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f4580-115">Select the **Add** button to create the class file for the composite control.</span></span>  
  
5.  <span data-ttu-id="f4580-116">Přidání ovládacích prvků **nástrojů** na povrchu složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f4580-116">Add controls from the **Toolbox** to the composite control surface.</span></span>  
  
6.  <span data-ttu-id="f4580-117">Umístěte kód procedury událostí ke zpracování událostí vyvolaných pomocí složeného ovládacího prvku nebo jeho základní ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="f4580-117">Place code in event procedures, to handle events raised by the composite control or by its constituent controls.</span></span>  
  
7.  <span data-ttu-id="f4580-118">Zavřít Návrhář složeného ovládacího prvku a uložte soubor po zobrazení výzvy.</span><span class="sxs-lookup"><span data-stu-id="f4580-118">Close the designer for the composite control, and save the file when you are prompted.</span></span>  
  
8.  <span data-ttu-id="f4580-119">Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="f4580-119">On the **Build** menu, click **Build Solution**.</span></span>  
  
     <span data-ttu-id="f4580-120">Projekt musí být sestaveny v pořadí pro vlastní ovládací prvky se zobrazí v **nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="f4580-120">The project must be built in order for custom controls to appear in the **Toolbox**.</span></span>  
  
9. <span data-ttu-id="f4580-121">Použití **DemoControlHost** karty **nástrojů** přidat instance ovládacího prvku na `Form1`.</span><span class="sxs-lookup"><span data-stu-id="f4580-121">Use the **DemoControlHost** tab of the **Toolbox** to add instances of your control to `Form1`.</span></span>  
  
### <a name="to-author-a-control-class-library"></a><span data-ttu-id="f4580-122">Chcete-li vytvořit knihovnu tříd ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="f4580-122">To author a control class library</span></span>  
  
1.  <span data-ttu-id="f4580-123">Otevřete novou **Knihovna ovládacích prvků Windows** projektu.</span><span class="sxs-lookup"><span data-stu-id="f4580-123">Open a new **Windows Control Library** project.</span></span>  
  
     <span data-ttu-id="f4580-124">Ve výchozím nastavení projekt obsahuje složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f4580-124">By default, the project contains a composite control.</span></span>  
  
2.  <span data-ttu-id="f4580-125">Přidání ovládacích prvků a kód, jak je popsáno v předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="f4580-125">Add controls and code as described in the procedure above.</span></span>  
  
3.  <span data-ttu-id="f4580-126">Zvolte ovládací prvek nechcete, aby dědění třídy změnit a nastavit **modifikátory** vlastnosti tohoto ovládacího prvku na **privátní**.</span><span class="sxs-lookup"><span data-stu-id="f4580-126">Choose a control you do not want inheriting classes to change, and set the **Modifiers** property of this control to **Private**.</span></span>  
  
4.  <span data-ttu-id="f4580-127">Sestavení knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="f4580-127">Build the DLL.</span></span>  
  
### <a name="to-inherit-from-a-composite-control-in-a-control-class-library"></a><span data-ttu-id="f4580-128">Chcete-li dědit ze složeného ovládacího prvku v knihovně tříd ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="f4580-128">To inherit from a composite control in a control class library</span></span>  
  
1.  <span data-ttu-id="f4580-129">Na **souboru** nabídky, přejděte k **přidat** a vyberte **nový projekt** přidáte nový **aplikace Windows** projektu do řešení.</span><span class="sxs-lookup"><span data-stu-id="f4580-129">On the **File** menu, point to **Add** and select **New Project** to add a new **Windows Application** project to the solution.</span></span>  
  
2.  <span data-ttu-id="f4580-130">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **odkazy** složku pro nový projekt a zvolte **přidat odkaz** otevřít **přidat odkaz**dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="f4580-130">In **Solution Explorer**, right-click the **References** folder for the new project and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>  
  
3.  <span data-ttu-id="f4580-131">Vyberte **projekty** kartě a dvakrát klikněte na váš projekt knihovny ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="f4580-131">Select the **Projects** tab and double-click your control library project.</span></span>  
  
4.  <span data-ttu-id="f4580-132">Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="f4580-132">On the **Build** menu, click **Build Solution**.</span></span>  
  
5.  <span data-ttu-id="f4580-133">V **Průzkumníka řešení**, klikněte pravým tlačítkem na váš projekt knihovny ovládacích prvků a vyberte **přidat novou položku** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="f4580-133">In **Solution Explorer**, right-click your control library project and select **Add New Item** from the shortcut menu.</span></span>  
  
6.  <span data-ttu-id="f4580-134">Vyberte **zděděné uživatelský ovládací prvek** šablonu z **přidat novou položku** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="f4580-134">Select the **Inherited User Control** template from the **Add New Item** dialog box.</span></span>  
  
7.  <span data-ttu-id="f4580-135">V **výběr dědičnosti** dialogové okno pole, poklepejte na ovládací prvek se má Zdědit z.</span><span class="sxs-lookup"><span data-stu-id="f4580-135">In the **Inheritance Picker** dialog box, double-click the control you want to inherit from.</span></span>  
  
     <span data-ttu-id="f4580-136">Nový ovládací prvek se přidá do vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="f4580-136">A new control is added to your project.</span></span>  
  
8.  <span data-ttu-id="f4580-137">Otevřete vizuálního návrháře pro nový ovládací prvek a přidat další základní ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="f4580-137">Open the visual designer for the new control and add additional constituent controls.</span></span>  
  
     <span data-ttu-id="f4580-138">Můžete zjistit základní ovládací prvky, které byly zděděny ze složeného ovládacího prvku v knihovně DLL, ale můžete změnit vlastnosti ovládacích prvků jehož **modifikátory** vlastnost **veřejné**.</span><span class="sxs-lookup"><span data-stu-id="f4580-138">You can see the constituent controls that were inherited from the composite control in your DLL, and you can alter the properties of controls whose **Modifiers** property is **Public**.</span></span> <span data-ttu-id="f4580-139">Nelze změnit vlastnosti ovládacího prvku jehož **modifikátory** vlastnost **privátní**.</span><span class="sxs-lookup"><span data-stu-id="f4580-139">You cannot change the properties of the control whose **Modifiers** property is **Private**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4580-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4580-140">See Also</span></span>  
 [<span data-ttu-id="f4580-141">Návod: Vytvoření složeného ovládacího prvku pomocí Visual Basicu</span><span class="sxs-lookup"><span data-stu-id="f4580-141">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [<span data-ttu-id="f4580-142">Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#</span><span class="sxs-lookup"><span data-stu-id="f4580-142">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 [<span data-ttu-id="f4580-143">Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual Basicu</span><span class="sxs-lookup"><span data-stu-id="f4580-143">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [<span data-ttu-id="f4580-144">Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C#</span><span class="sxs-lookup"><span data-stu-id="f4580-144">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 [<span data-ttu-id="f4580-145">Doporučení ohledně typu ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="f4580-145">Control Type Recommendations</span></span>](../../../../docs/framework/winforms/controls/control-type-recommendations.md)  
 [<span data-ttu-id="f4580-146">Postupy: Vytváření ovládacích prvků pro Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f4580-146">How to: Author Controls for Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [<span data-ttu-id="f4580-147">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="f4580-147">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
