---
title: 'Návod: Automatické vyplnění nástrojů vlastními komponentami'
ms.date: 03/30/2017
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
ms.openlocfilehash: d446ab84cfe135e56483b8b309b696f7f15044fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540043"
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a><span data-ttu-id="455eb-102">Návod: Automatické vyplnění nástrojů vlastními komponentami</span><span class="sxs-lookup"><span data-stu-id="455eb-102">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>
<span data-ttu-id="455eb-103">Pokud vaše komponenty jsou definovány na projekt v aktuálně otevřených řešení, se automaticky zobrazí v **sada nástrojů**, třeba akce.</span><span class="sxs-lookup"><span data-stu-id="455eb-103">If your components are defined by a project in the currently open solution, they will automatically appear in the **Toolbox**, with no action required by you.</span></span> <span data-ttu-id="455eb-104">Můžete také ručně naplnit **sada nástrojů** s vlastních součástí s použitím [zvolte sady nástrojů položek dialogové okno (Visual Studio)](http://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb), ale **sada nástrojů** bere v úvahu položek ve vašem řešení sestavení výstupy s následujícími charakteristikami:</span><span class="sxs-lookup"><span data-stu-id="455eb-104">You can also manually populate the **Toolbox** with your custom components by using the [Choose Toolbox Items Dialog Box (Visual Studio)](http://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb), but the **Toolbox** takes account of items in your solution's build outputs with all the following characteristics:</span></span>  
  
-   <span data-ttu-id="455eb-105">Implementuje <xref:System.ComponentModel.IComponent>;</span><span class="sxs-lookup"><span data-stu-id="455eb-105">Implements <xref:System.ComponentModel.IComponent>;</span></span>  
  
-   <span data-ttu-id="455eb-106">Nemá <xref:System.ComponentModel.ToolboxItemAttribute> nastavena na `false`;</span><span class="sxs-lookup"><span data-stu-id="455eb-106">Does not have <xref:System.ComponentModel.ToolboxItemAttribute> set to `false`;</span></span>  
  
-   <span data-ttu-id="455eb-107">Nemá <xref:System.ComponentModel.DesignTimeVisibleAttribute> nastavena na `false`.</span><span class="sxs-lookup"><span data-stu-id="455eb-107">Does not have <xref:System.ComponentModel.DesignTimeVisibleAttribute> set to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="455eb-108">**Sada nástrojů** nedodrží řetězy odkaz, nebude se zobrazovat položky, které nejsou vytvořené na projekt v řešení.</span><span class="sxs-lookup"><span data-stu-id="455eb-108">The **Toolbox** does not follow reference chains, so it will not display items that are not built by a project in your solution.</span></span>  
  
 <span data-ttu-id="455eb-109">Tento návod ukazuje, jak vlastní součást automaticky zobrazuje v **sada nástrojů** po komponentu.</span><span class="sxs-lookup"><span data-stu-id="455eb-109">This walkthrough demonstrates how a custom component automatically appears in the **Toolbox** once the component is built.</span></span> <span data-ttu-id="455eb-110">Úkoly v tomto návodu zahrnují:</span><span class="sxs-lookup"><span data-stu-id="455eb-110">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="455eb-111">Vytvoření projektu modelu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="455eb-111">Creating a Windows Forms project.</span></span>  
  
-   <span data-ttu-id="455eb-112">Vytvoření vlastní komponenty.</span><span class="sxs-lookup"><span data-stu-id="455eb-112">Creating a custom component.</span></span>  
  
-   <span data-ttu-id="455eb-113">Vytvoření instance vlastní komponenty.</span><span class="sxs-lookup"><span data-stu-id="455eb-113">Creating an instance of a custom component.</span></span>  
  
-   <span data-ttu-id="455eb-114">Uvolnění a načíst vlastní komponenty.</span><span class="sxs-lookup"><span data-stu-id="455eb-114">Unloading and reloading a custom component.</span></span>  
  
 <span data-ttu-id="455eb-115">Jakmile budete hotovi, zobrazí se **sada nástrojů** naplněný součást, kterou jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="455eb-115">When you are finished, you will see that the **Toolbox** is populated with a component that you have created.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="455eb-116">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="455eb-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="455eb-117">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="455eb-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="455eb-118">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="455eb-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="455eb-119">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="455eb-119">Creating the Project</span></span>  
 <span data-ttu-id="455eb-120">Prvním krokem je vytvoření projektu a nastavte formulář.</span><span class="sxs-lookup"><span data-stu-id="455eb-120">The first step is to create the project and to set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="455eb-121">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="455eb-121">To create the project</span></span>  
  
1.  <span data-ttu-id="455eb-122">Vytvořte projekt aplikace pro systém Windows s názvem `ToolboxExample`.</span><span class="sxs-lookup"><span data-stu-id="455eb-122">Create a Windows-based application project called `ToolboxExample`.</span></span>  
  
     <span data-ttu-id="455eb-123">Další informace najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="455eb-123">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="455eb-124">Přidáte novou součást do projektu.</span><span class="sxs-lookup"><span data-stu-id="455eb-124">Add a new component to the project.</span></span> <span data-ttu-id="455eb-125">Volání `DemoComponent`.</span><span class="sxs-lookup"><span data-stu-id="455eb-125">Call it `DemoComponent`.</span></span>  
  
     <span data-ttu-id="455eb-126">Další informace najdete v tématu [NIB: postupy: Přidání nové položky projektu](http://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span><span class="sxs-lookup"><span data-stu-id="455eb-126">For more information, see [NIB:How to: Add New Project Items](http://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span></span>  
  
3.  <span data-ttu-id="455eb-127">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="455eb-127">Build the project.</span></span>  
  
4.  <span data-ttu-id="455eb-128">Z **nástroje** nabídky, klikněte na tlačítko **možnosti** položky.</span><span class="sxs-lookup"><span data-stu-id="455eb-128">From the **Tools** menu, click the **Options** item.</span></span> <span data-ttu-id="455eb-129">Klikněte na tlačítko **Obecné** pod **Návrhář formulářů Windows** položky a ujistěte se, že **AutoToolboxPopulate** je možnost nastavena na **True**.</span><span class="sxs-lookup"><span data-stu-id="455eb-129">Click **General** under the **Windows Forms Designer** item and ensure that the **AutoToolboxPopulate** option is set to **True**.</span></span>  
  
## <a name="creating-an-instance-of-a-custom-component"></a><span data-ttu-id="455eb-130">Vytvoření Instance vlastní komponenty</span><span class="sxs-lookup"><span data-stu-id="455eb-130">Creating an Instance of a Custom Component</span></span>  
 <span data-ttu-id="455eb-131">Dalším krokem je vytvoření instance vlastní součásti na formuláři.</span><span class="sxs-lookup"><span data-stu-id="455eb-131">The next step is to create an instance of the custom component on the form.</span></span> <span data-ttu-id="455eb-132">Protože **sada nástrojů** automaticky účty pro novou součást, to je stejně snadná jako vytváření další komponenta nebo ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="455eb-132">Because the **Toolbox** automatically accounts for the new component, this is as easy as creating any other component or control.</span></span>  
  
#### <a name="to-create-an-instance-of-a-custom-component"></a><span data-ttu-id="455eb-133">K vytvoření instance vlastní komponenty</span><span class="sxs-lookup"><span data-stu-id="455eb-133">To create an instance of a custom component</span></span>  
  
1.  <span data-ttu-id="455eb-134">Otevřít formulář projektu v **Návrhář formulářů**.</span><span class="sxs-lookup"><span data-stu-id="455eb-134">Open the project's form in the **Forms Designer**.</span></span>  
  
2.  <span data-ttu-id="455eb-135">V **sada nástrojů**, klikněte na kartu nové názvem **ToolboxExample součásti**.</span><span class="sxs-lookup"><span data-stu-id="455eb-135">In the **Toolbox**, click the new tab called **ToolboxExample Components**.</span></span>  
  
     <span data-ttu-id="455eb-136">Jakmile kliknete na kartu, zobrazí se **DemoComponent**.</span><span class="sxs-lookup"><span data-stu-id="455eb-136">Once you click the tab, you will see **DemoComponent**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="455eb-137">Z důvodů výkonu komponenty v oblasti automaticky vyplněna **sada nástrojů** nezobrazují vlastní rastrové obrázky a <xref:System.Drawing.ToolboxBitmapAttribute> není podporován.</span><span class="sxs-lookup"><span data-stu-id="455eb-137">For performance reasons, components in the auto-populated area of the **Toolbox** do not display custom bitmaps, and the <xref:System.Drawing.ToolboxBitmapAttribute> is not supported.</span></span> <span data-ttu-id="455eb-138">Zobrazit ikonu pro vlastní součást v **sada nástrojů**, použijte **výběr položek sady nástrojů** dialogové okno načíst příslušné součásti.</span><span class="sxs-lookup"><span data-stu-id="455eb-138">To display an icon for a custom component in the **Toolbox**, use the **Choose Toolbox Items** dialog box to load your component.</span></span>  
  
3.  <span data-ttu-id="455eb-139">Přetáhněte příslušné součásti do formuláře.</span><span class="sxs-lookup"><span data-stu-id="455eb-139">Drag your component onto your form.</span></span>  
  
     <span data-ttu-id="455eb-140">Instance součásti je vytvořen a přidán do **komponent**.</span><span class="sxs-lookup"><span data-stu-id="455eb-140">An instance of the component is created and added to the **Component Tray**.</span></span>  
  
## <a name="unloading-and-reloading-a-custom-component"></a><span data-ttu-id="455eb-141">Uvolnění a načíst vlastní komponenty</span><span class="sxs-lookup"><span data-stu-id="455eb-141">Unloading and Reloading a Custom Component</span></span>  
 <span data-ttu-id="455eb-142">**Sada nástrojů** načíst účet trvá součástí v každém projektu a když na projekt je odpojen, odebere odkazy na součástí projektu.</span><span class="sxs-lookup"><span data-stu-id="455eb-142">The **Toolbox** takes account of the components in each loaded project, and when a project is unloaded, it removes references to the project's components.</span></span>  
  
#### <a name="to-experiment-with-the-effect-on-the-toolbox-of-unloading-and-reloading-components"></a><span data-ttu-id="455eb-143">A experimentovat s vliv na panelu nástrojů uvolnění a opětovném načtení součásti</span><span class="sxs-lookup"><span data-stu-id="455eb-143">To experiment with the effect on the Toolbox of unloading and reloading components</span></span>  
  
1.  <span data-ttu-id="455eb-144">Uvolněte projekt z řešení.</span><span class="sxs-lookup"><span data-stu-id="455eb-144">Unload the project from the solution.</span></span>  
  
     <span data-ttu-id="455eb-145">Další informace o uvolnění projekty najdete v tématu [NIB: postupy: uvolnění a načtěte projekty](http://msdn.microsoft.com/library/abc0155b-8fcb-4ffc-95b6-698518a7100b).</span><span class="sxs-lookup"><span data-stu-id="455eb-145">For more information about unloading projects, see [NIB:How to: Unload and Reload Projects](http://msdn.microsoft.com/library/abc0155b-8fcb-4ffc-95b6-698518a7100b).</span></span> <span data-ttu-id="455eb-146">Pokud se zobrazí výzva k uložení, zvolte **Ano**.</span><span class="sxs-lookup"><span data-stu-id="455eb-146">If you are prompted to save, choose **Yes**.</span></span>  
  
2.  <span data-ttu-id="455eb-147">Přidejte nový **aplikace Windows** projektu k řešení.</span><span class="sxs-lookup"><span data-stu-id="455eb-147">Add a new **Windows Application** project to the solution.</span></span> <span data-ttu-id="455eb-148">Otevřete formulář v **Návrhář**.</span><span class="sxs-lookup"><span data-stu-id="455eb-148">Open the form in the **Designer**.</span></span>  
  
     <span data-ttu-id="455eb-149">**ToolboxExample součásti** karta z předchozí projektu je nyní pryč.</span><span class="sxs-lookup"><span data-stu-id="455eb-149">The **ToolboxExample Components** tab from the previous project is now gone.</span></span>  
  
3.  <span data-ttu-id="455eb-150">Načtěte `ToolboxExample` projektu.</span><span class="sxs-lookup"><span data-stu-id="455eb-150">Reload the `ToolboxExample` project.</span></span>  
  
     <span data-ttu-id="455eb-151">**ToolboxExample součásti** kartě teď se bude zobrazovat.</span><span class="sxs-lookup"><span data-stu-id="455eb-151">The **ToolboxExample Components** tab now reappears.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="455eb-152">Další kroky</span><span class="sxs-lookup"><span data-stu-id="455eb-152">Next Steps</span></span>  
 <span data-ttu-id="455eb-153">Tento návod ukazuje, který **sada nástrojů** bere v úvahu součástí projektu, ale **sada nástrojů** je také účtu trvá ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="455eb-153">This walkthrough demonstrates that the **Toolbox** takes account of a project's components, but the **Toolbox** is also takes account of controls.</span></span> <span data-ttu-id="455eb-154">Experimentujte s vlastní ovládací prvky podle přidávání a odebírání řízení projektů z vašeho řešení.</span><span class="sxs-lookup"><span data-stu-id="455eb-154">Experiment with your own custom controls by adding and removing control projects from your solution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="455eb-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="455eb-155">See Also</span></span>  
 [<span data-ttu-id="455eb-156">Obecné, Návrhář formulářů Windows, dialogové okno Možnosti</span><span class="sxs-lookup"><span data-stu-id="455eb-156">General, Windows Forms Designer, Options Dialog Box</span></span>](http://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834)  
 [<span data-ttu-id="455eb-157">Postupy: manipulace s kartami panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="455eb-157">How to: Manipulate Toolbox Tabs</span></span>](http://msdn.microsoft.com/library/21285050-cadd-455a-b1f5-a2289a89c4db)  
 [<span data-ttu-id="455eb-158">Výběr dialogové okno položek sady nástrojů (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="455eb-158">Choose Toolbox Items Dialog Box (Visual Studio)</span></span>](http://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [<span data-ttu-id="455eb-159">Vkládání ovládacích prvků do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="455eb-159">Putting Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)
