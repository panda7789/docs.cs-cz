---
title: "Postupy: Vytváření složených ovládacích prvků"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UserControl class [Windows Forms], creating composite controls
- user controls [Windows Forms], creating
- user controls [Windows Forms], inheriting from
- composite controls [Windows Forms], creating
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 72c68568f0178956d6154f0b3a070e69b6ff0502
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-author-composite-controls"></a><span data-ttu-id="309a8-102">Postupy: Vytváření složených ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="309a8-102">How to: Author Composite Controls</span></span>
<span data-ttu-id="309a8-103">Složené ovládací prvky mohou být použity v mnoha způsoby.</span><span class="sxs-lookup"><span data-stu-id="309a8-103">Composite controls can be employed in many ways.</span></span> <span data-ttu-id="309a8-104">Můžete je v rámci projektu aplikace pracovní plochy Windows vytvářet a používat pouze ve formulářích v projektu.</span><span class="sxs-lookup"><span data-stu-id="309a8-104">You can author them as part of a Windows desktop application project, and use them only on forms in the project.</span></span> <span data-ttu-id="309a8-105">Nebo můžete vytvořit je v projektu knihovny ovládacích prvků Windows, kompilace projektu do sestavení a pomocí ovládacích prvků v jiném projektu.</span><span class="sxs-lookup"><span data-stu-id="309a8-105">Or you can author them in a Windows Control Library project, compile the project into an assembly, and use the controls in other projects.</span></span> <span data-ttu-id="309a8-106">Můžete dokonce dědit z nich a použít dědičnost vizuálních prvků se přizpůsobit rychle pro zvláštní účely.</span><span class="sxs-lookup"><span data-stu-id="309a8-106">You can even inherit from them, and use visual inheritance to customize them quickly for special purposes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="309a8-107">Pokud chcete vytvořit složeného ovládacího prvku na webové formuláře použít, najdete v článku [vývoj vlastních serverových ovládacích prvků ASP.NET](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).</span><span class="sxs-lookup"><span data-stu-id="309a8-107">If you want to author a composite control to use on Web Forms, see [Developing Custom ASP.NET Server Controls](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).</span></span>  
>   
>  <span data-ttu-id="309a8-108">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="309a8-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="309a8-109">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="309a8-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="309a8-110">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="309a8-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-author-a-composite-control"></a><span data-ttu-id="309a8-111">Pro vytvoření složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="309a8-111">To author a composite control</span></span>  
  
1.  <span data-ttu-id="309a8-112">Otevřete nový **aplikace Windows** projekt s názvem `DemoControlHost`.</span><span class="sxs-lookup"><span data-stu-id="309a8-112">Open a new **Windows Application** project called `DemoControlHost`.</span></span>  
  
2.  <span data-ttu-id="309a8-113">Na **projektu**nabídky, klikněte na tlačítko **přidat uživatelský ovládací prvek**.</span><span class="sxs-lookup"><span data-stu-id="309a8-113">On the **Project**menu, click **Add User Control**.</span></span>  
  
3.  <span data-ttu-id="309a8-114">V **přidat novou položku** dialogové okno, udělte třída název chcete složeného ovládacího prvku tak, aby měl souboru (vb nebo .cs soubor).</span><span class="sxs-lookup"><span data-stu-id="309a8-114">In the **Add New Item** dialog box, give the class file (.vb or .cs file) the name you want the composite control to have.</span></span>  
  
4.  <span data-ttu-id="309a8-115">Klikněte **přidat** tlačítko pro vytvoření souboru třídy složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="309a8-115">Click the **Add** button to create the class file for the composite control.</span></span>  
  
5.  <span data-ttu-id="309a8-116">Přidání ovládacích prvků z **sada nástrojů** na povrchu složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="309a8-116">Add controls from the **Toolbox** to the composite control surface.</span></span>  
  
6.  <span data-ttu-id="309a8-117">V postupech událostí ke zpracování událostí vyvolaných složeného ovládacího prvku, nebo jeho základní ovládací prvky umístěte kód.</span><span class="sxs-lookup"><span data-stu-id="309a8-117">Place code in event procedures, to handle events raised by the composite control or by its constituent controls.</span></span>  
  
7.  <span data-ttu-id="309a8-118">Zavřít návrháře složeného ovládacího prvku a uložte soubor po zobrazení výzvy.</span><span class="sxs-lookup"><span data-stu-id="309a8-118">Close the designer for the composite control, and save the file when you are prompted.</span></span>  
  
8.  <span data-ttu-id="309a8-119">Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="309a8-119">On the **Build** menu, click **Build Solution**.</span></span>  
  
     <span data-ttu-id="309a8-120">Projekt musí být součástí pořadí u vlastních ovládacích prvků, než se objeví na **sada nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="309a8-120">The project must be built in order for custom controls to appear in the **Toolbox**.</span></span>  
  
9. <span data-ttu-id="309a8-121">Použití **DemoControlHost** kartě **sada nástrojů** přidání instancí ovládacího prvku na `Form1`.</span><span class="sxs-lookup"><span data-stu-id="309a8-121">Use the **DemoControlHost** tab of the **Toolbox** to add instances of your control to `Form1`.</span></span>  
  
### <a name="to-author-a-control-class-library"></a><span data-ttu-id="309a8-122">Pro vytvoření knihovny tříd ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="309a8-122">To author a control class library</span></span>  
  
1.  <span data-ttu-id="309a8-123">Otevřete nový **knihovny ovládacích prvků Windows** projektu.</span><span class="sxs-lookup"><span data-stu-id="309a8-123">Open a new **Windows Control Library** project.</span></span>  
  
     <span data-ttu-id="309a8-124">Ve výchozím nastavení obsahuje projektu složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="309a8-124">By default, the project contains a composite control.</span></span>  
  
2.  <span data-ttu-id="309a8-125">Přidejte ovládacími prvky a kódem, jak je popsáno v předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="309a8-125">Add controls and code as described in the procedure above.</span></span>  
  
3.  <span data-ttu-id="309a8-126">Vyberte ovládací prvek nechcete dědění třídy změnit, a nastavte **modifikátory** vlastnosti tohoto ovládacího prvku na **privátní**.</span><span class="sxs-lookup"><span data-stu-id="309a8-126">Choose a control you do not want inheriting classes to change, and set the **Modifiers** property of this control to **Private**.</span></span>  
  
4.  <span data-ttu-id="309a8-127">Vytvořte knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="309a8-127">Build the DLL.</span></span>  
  
### <a name="to-inherit-from-a-composite-control-in-a-control-class-library"></a><span data-ttu-id="309a8-128">Dědění z složeného ovládacího prvku v knihovnu tříd ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="309a8-128">To inherit from a composite control in a control class library</span></span>  
  
1.  <span data-ttu-id="309a8-129">Na **souboru** nabídky, přejděte na příkaz **přidat** a vyberte **nový projekt** přidat nový **aplikace pro systém Windows** projektu k řešení.</span><span class="sxs-lookup"><span data-stu-id="309a8-129">On the **File** menu, point to **Add** and select **New Project** to add a new **Windows Application** project to the solution.</span></span>  
  
2.  <span data-ttu-id="309a8-130">V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **odkazy** složku pro nové projektu a zvolte **přidat odkaz na** otevřete **přidat odkaz na**dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="309a8-130">In **Solution Explorer**, right-click the **References** folder for the new project and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>  
  
3.  <span data-ttu-id="309a8-131">Vyberte **projekty** kartě a dvakrát klikněte na projekt knihovny ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="309a8-131">Select the **Projects** tab and double-click your control library project.</span></span>  
  
4.  <span data-ttu-id="309a8-132">Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="309a8-132">On the **Build** menu, click **Build Solution**.</span></span>  
  
5.  <span data-ttu-id="309a8-133">V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt knihovny ovládací prvek a vyberte **přidat novou položku** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="309a8-133">In **Solution Explorer**, right-click your control library project and select **Add New Item** from the shortcut menu.</span></span>  
  
6.  <span data-ttu-id="309a8-134">Vyberte **zděděná uživatelský ovládací prvek** šablony z **přidat novou položku** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="309a8-134">Select the **Inherited User Control** template from the **Add New Item** dialog box.</span></span>  
  
7.  <span data-ttu-id="309a8-135">V **výběr dědičnosti** dialogové okno pole, dvakrát klikněte na chcete použít dědění z ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="309a8-135">In the **Inheritance Picker** dialog box, double-click the control you want to inherit from.</span></span>  
  
     <span data-ttu-id="309a8-136">Nový ovládací prvek se přidá do projektu.</span><span class="sxs-lookup"><span data-stu-id="309a8-136">A new control is added to your project.</span></span>  
  
8.  <span data-ttu-id="309a8-137">Otevřete vizuálního návrháře pro nový ovládací prvek a přidat další základních ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="309a8-137">Open the visual designer for the new control and add additional constituent controls.</span></span>  
  
     <span data-ttu-id="309a8-138">Zobrazí se základní ovládací prvky, které byly zděděno z složeného ovládacího prvku v knihovně DLL a upravíte vlastnosti ovládacích prvků jejichž **modifikátory** vlastnost je **veřejné**.</span><span class="sxs-lookup"><span data-stu-id="309a8-138">You can see the constituent controls that were inherited from the composite control in your DLL, and you can alter the properties of controls whose **Modifiers** property is **Public**.</span></span> <span data-ttu-id="309a8-139">Nelze změnit vlastnosti ovládacího prvku jehož **modifikátory** vlastnost je **privátní**.</span><span class="sxs-lookup"><span data-stu-id="309a8-139">You cannot change the properties of the control whose **Modifiers** property is **Private**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="309a8-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="309a8-140">See Also</span></span>  
 [<span data-ttu-id="309a8-141">Návod: Vytvoření složeného ovládacího prvku pomocí Visual Basic</span><span class="sxs-lookup"><span data-stu-id="309a8-141">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [<span data-ttu-id="309a8-142">Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#</span><span class="sxs-lookup"><span data-stu-id="309a8-142">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 [<span data-ttu-id="309a8-143">Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual Basic</span><span class="sxs-lookup"><span data-stu-id="309a8-143">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [<span data-ttu-id="309a8-144">Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C#</span><span class="sxs-lookup"><span data-stu-id="309a8-144">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 [<span data-ttu-id="309a8-145">Doporučení ohledně typu ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="309a8-145">Control Type Recommendations</span></span>](../../../../docs/framework/winforms/controls/control-type-recommendations.md)  
 [<span data-ttu-id="309a8-146">Postupy: vytváření ovládacích prvků pro Windows Forms</span><span class="sxs-lookup"><span data-stu-id="309a8-146">How to: Author Controls for Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [<span data-ttu-id="309a8-147">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="309a8-147">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
