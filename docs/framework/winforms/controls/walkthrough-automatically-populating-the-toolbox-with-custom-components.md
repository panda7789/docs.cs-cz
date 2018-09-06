---
title: 'Návod: Automatické vyplnění nástrojů vlastními komponentami'
ms.date: 03/30/2017
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
ms.openlocfilehash: 488d51e748ea17b09e61b982db7abadc34f8e311
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44041558"
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a><span data-ttu-id="439d4-102">Návod: Automatické vyplnění nástrojů vlastními komponentami</span><span class="sxs-lookup"><span data-stu-id="439d4-102">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>
<span data-ttu-id="439d4-103">Pokud vaše komponenty jsou definovány projektu v aktuálně otevřené řešení, se automaticky zobrazí v **nástrojů**, třeba akce.</span><span class="sxs-lookup"><span data-stu-id="439d4-103">If your components are defined by a project in the currently open solution, they will automatically appear in the **Toolbox**, with no action required by you.</span></span> <span data-ttu-id="439d4-104">Můžete také ručně naplnit **nástrojů** pomocí vlastních součástí s použitím [tlačítko panelu nástrojů položky dialogové okno (Visual Studio)](https://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb), ale **nástrojů** bere v úvahu položky ve vašem řešení sestavení výstupy s následujícími charakteristikami:</span><span class="sxs-lookup"><span data-stu-id="439d4-104">You can also manually populate the **Toolbox** with your custom components by using the [Choose Toolbox Items Dialog Box (Visual Studio)](https://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb), but the **Toolbox** takes account of items in your solution's build outputs with all the following characteristics:</span></span>  
  
-   <span data-ttu-id="439d4-105">Implementuje <xref:System.ComponentModel.IComponent>;</span><span class="sxs-lookup"><span data-stu-id="439d4-105">Implements <xref:System.ComponentModel.IComponent>;</span></span>  
  
-   <span data-ttu-id="439d4-106">Nemá <xref:System.ComponentModel.ToolboxItemAttribute> nastavena na `false`;</span><span class="sxs-lookup"><span data-stu-id="439d4-106">Does not have <xref:System.ComponentModel.ToolboxItemAttribute> set to `false`;</span></span>  
  
-   <span data-ttu-id="439d4-107">Nemá <xref:System.ComponentModel.DesignTimeVisibleAttribute> nastavena na `false`.</span><span class="sxs-lookup"><span data-stu-id="439d4-107">Does not have <xref:System.ComponentModel.DesignTimeVisibleAttribute> set to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="439d4-108">**Nástrojů** nedodržuje odkaz na řetězcích, proto by se nezobrazil položky, které nejsou sestaveny projekt ve vašem řešení.</span><span class="sxs-lookup"><span data-stu-id="439d4-108">The **Toolbox** does not follow reference chains, so it will not display items that are not built by a project in your solution.</span></span>  
  
 <span data-ttu-id="439d4-109">Tento návod ukazuje, jak vlastní komponenty se automaticky zobrazí v **nástrojů** po sestavení komponenty.</span><span class="sxs-lookup"><span data-stu-id="439d4-109">This walkthrough demonstrates how a custom component automatically appears in the **Toolbox** once the component is built.</span></span> <span data-ttu-id="439d4-110">Úlohy v tomto návodu zahrnují:</span><span class="sxs-lookup"><span data-stu-id="439d4-110">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="439d4-111">Vytvoření projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="439d4-111">Creating a Windows Forms project.</span></span>  
  
-   <span data-ttu-id="439d4-112">Vytvoření vlastní komponenty.</span><span class="sxs-lookup"><span data-stu-id="439d4-112">Creating a custom component.</span></span>  
  
-   <span data-ttu-id="439d4-113">Vytvoření instance vlastní komponenty.</span><span class="sxs-lookup"><span data-stu-id="439d4-113">Creating an instance of a custom component.</span></span>  
  
-   <span data-ttu-id="439d4-114">Uvolnění a opětovné načtení volitelná množina komponent.</span><span class="sxs-lookup"><span data-stu-id="439d4-114">Unloading and reloading a custom component.</span></span>  
  
 <span data-ttu-id="439d4-115">Až budete hotovi, uvidíte, že **nástrojů** se vyplní komponentu, kterou jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="439d4-115">When you are finished, you will see that the **Toolbox** is populated with a component that you have created.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="439d4-116">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="439d4-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="439d4-117">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="439d4-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="439d4-118">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="439d4-118">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="439d4-119">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="439d4-119">Creating the Project</span></span>  
 <span data-ttu-id="439d4-120">Prvním krokem je vytvoření projektu a k nastavení tvaru.</span><span class="sxs-lookup"><span data-stu-id="439d4-120">The first step is to create the project and to set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="439d4-121">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="439d4-121">To create the project</span></span>  
  
1.  <span data-ttu-id="439d4-122">Vytvořte projekt aplikace pro systém Windows s názvem `ToolboxExample` (**souboru** > **nový** > **projektu**  >  **Visual C#** nebo **jazyka Visual Basic** > **klasický desktopový** > **aplikaci Windows Forms**).</span><span class="sxs-lookup"><span data-stu-id="439d4-122">Create a Windows-based application project called `ToolboxExample` (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2.  <span data-ttu-id="439d4-123">Přidáte novou součást do projektu.</span><span class="sxs-lookup"><span data-stu-id="439d4-123">Add a new component to the project.</span></span> <span data-ttu-id="439d4-124">Pojmenujte ji `DemoComponent`.</span><span class="sxs-lookup"><span data-stu-id="439d4-124">Call it `DemoComponent`.</span></span>  
  
     <span data-ttu-id="439d4-125">Další informace najdete v tématu [NIB: postupy: Přidání nové položky projektu](https://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span><span class="sxs-lookup"><span data-stu-id="439d4-125">For more information, see [NIB:How to: Add New Project Items](https://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span></span>  
  
3.  <span data-ttu-id="439d4-126">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="439d4-126">Build the project.</span></span>  
  
4.  <span data-ttu-id="439d4-127">Z **nástroje** nabídky, klikněte na tlačítko **možnosti** položky.</span><span class="sxs-lookup"><span data-stu-id="439d4-127">From the **Tools** menu, click the **Options** item.</span></span> <span data-ttu-id="439d4-128">Klikněte na tlačítko **Obecné** pod **Návrháře formulářů Windows** položku a ověřte, že **AutoToolboxPopulate** je možnost nastavená na **True**.</span><span class="sxs-lookup"><span data-stu-id="439d4-128">Click **General** under the **Windows Forms Designer** item and ensure that the **AutoToolboxPopulate** option is set to **True**.</span></span>  
  
## <a name="creating-an-instance-of-a-custom-component"></a><span data-ttu-id="439d4-129">Vytvoření Instance vlastní komponenty</span><span class="sxs-lookup"><span data-stu-id="439d4-129">Creating an Instance of a Custom Component</span></span>  
 <span data-ttu-id="439d4-130">Dalším krokem je vytvoření instance vlastní komponenty ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="439d4-130">The next step is to create an instance of the custom component on the form.</span></span> <span data-ttu-id="439d4-131">Vzhledem k tomu, **nástrojů** automaticky účty pro novou komponentu, to je stejně jednoduché jako vytvoření jakékoli součást nebo ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="439d4-131">Because the **Toolbox** automatically accounts for the new component, this is as easy as creating any other component or control.</span></span>  
  
#### <a name="to-create-an-instance-of-a-custom-component"></a><span data-ttu-id="439d4-132">K vytvoření instance vlastní komponenty</span><span class="sxs-lookup"><span data-stu-id="439d4-132">To create an instance of a custom component</span></span>  
  
1.  <span data-ttu-id="439d4-133">Otevřete formulář v projektu v **Návrháře formulářů**.</span><span class="sxs-lookup"><span data-stu-id="439d4-133">Open the project's form in the **Forms Designer**.</span></span>  
  
2.  <span data-ttu-id="439d4-134">V **nástrojů**, klikněte na novou kartu **ToolboxExample komponenty**.</span><span class="sxs-lookup"><span data-stu-id="439d4-134">In the **Toolbox**, click the new tab called **ToolboxExample Components**.</span></span>  
  
     <span data-ttu-id="439d4-135">Po kliknutí na kartě, zobrazí se **DemoComponent**.</span><span class="sxs-lookup"><span data-stu-id="439d4-135">Once you click the tab, you will see **DemoComponent**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="439d4-136">Z důvodů výkonu komponenty v oblasti vyplní automaticky **nástrojů** vlastních rastrových obrázků, se nezobrazí a <xref:System.Drawing.ToolboxBitmapAttribute> se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="439d4-136">For performance reasons, components in the auto-populated area of the **Toolbox** do not display custom bitmaps, and the <xref:System.Drawing.ToolboxBitmapAttribute> is not supported.</span></span> <span data-ttu-id="439d4-137">Zobrazit ikonu pro vlastní komponenty v **nástrojů**, použijte **zvolit položky nástrojů** dialogové okno načíst vaše komponenta.</span><span class="sxs-lookup"><span data-stu-id="439d4-137">To display an icon for a custom component in the **Toolbox**, use the **Choose Toolbox Items** dialog box to load your component.</span></span>  
  
3.  <span data-ttu-id="439d4-138">Přetáhněte komponenty do formuláře.</span><span class="sxs-lookup"><span data-stu-id="439d4-138">Drag your component onto your form.</span></span>  
  
     <span data-ttu-id="439d4-139">Je vytvořen a přidán do instance komponenty **komponent**.</span><span class="sxs-lookup"><span data-stu-id="439d4-139">An instance of the component is created and added to the **Component Tray**.</span></span>  
  
## <a name="unloading-and-reloading-a-custom-component"></a><span data-ttu-id="439d4-140">Uvolnění a opětovné načtení volitelná množina komponent</span><span class="sxs-lookup"><span data-stu-id="439d4-140">Unloading and Reloading a Custom Component</span></span>  
 <span data-ttu-id="439d4-141">**Nástrojů** přihlíží komponent v každém načtení projektu a projekt je uvolněna, odebere odkazy na součásti projektu.</span><span class="sxs-lookup"><span data-stu-id="439d4-141">The **Toolbox** takes account of the components in each loaded project, and when a project is unloaded, it removes references to the project's components.</span></span>  
  
#### <a name="to-experiment-with-the-effect-on-the-toolbox-of-unloading-and-reloading-components"></a><span data-ttu-id="439d4-142">Můžete experimentovat s vliv na panelu nástrojů uvolnění a opětovné načítání komponent</span><span class="sxs-lookup"><span data-stu-id="439d4-142">To experiment with the effect on the Toolbox of unloading and reloading components</span></span>  
  
1.  <span data-ttu-id="439d4-143">Uvolněte projekt z řešení.</span><span class="sxs-lookup"><span data-stu-id="439d4-143">Unload the project from the solution.</span></span>  
  
     <span data-ttu-id="439d4-144">Další informace o uvolnění projektů, naleznete v tématu [NIB: postupy: uvolnění a opětovné načtení projekty](https://msdn.microsoft.com/library/abc0155b-8fcb-4ffc-95b6-698518a7100b).</span><span class="sxs-lookup"><span data-stu-id="439d4-144">For more information about unloading projects, see [NIB:How to: Unload and Reload Projects](https://msdn.microsoft.com/library/abc0155b-8fcb-4ffc-95b6-698518a7100b).</span></span> <span data-ttu-id="439d4-145">Pokud se zobrazí výzva k uložení, zvolte **Ano**.</span><span class="sxs-lookup"><span data-stu-id="439d4-145">If you are prompted to save, choose **Yes**.</span></span>  
  
2.  <span data-ttu-id="439d4-146">Přidat nový **aplikace Windows** projektu do řešení.</span><span class="sxs-lookup"><span data-stu-id="439d4-146">Add a new **Windows Application** project to the solution.</span></span> <span data-ttu-id="439d4-147">Otevřete formulář v nástrojích pro **návrháře**.</span><span class="sxs-lookup"><span data-stu-id="439d4-147">Open the form in the **Designer**.</span></span>  
  
     <span data-ttu-id="439d4-148">**ToolboxExample součásti** kartu z předchozí projektu je teď pryč.</span><span class="sxs-lookup"><span data-stu-id="439d4-148">The **ToolboxExample Components** tab from the previous project is now gone.</span></span>  
  
3.  <span data-ttu-id="439d4-149">Znovu načíst `ToolboxExample` projektu.</span><span class="sxs-lookup"><span data-stu-id="439d4-149">Reload the `ToolboxExample` project.</span></span>  
  
     <span data-ttu-id="439d4-150">**ToolboxExample součásti** kartě nyní zobrazí znovu.</span><span class="sxs-lookup"><span data-stu-id="439d4-150">The **ToolboxExample Components** tab now reappears.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="439d4-151">Další kroky</span><span class="sxs-lookup"><span data-stu-id="439d4-151">Next Steps</span></span>  
 <span data-ttu-id="439d4-152">Tento návod ukazuje, že **nástrojů** bere v úvahu součástí projektu, ale **nástrojů** je také přihlíží ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="439d4-152">This walkthrough demonstrates that the **Toolbox** takes account of a project's components, but the **Toolbox** is also takes account of controls.</span></span> <span data-ttu-id="439d4-153">Přidáváním a odebíráním ovládací prvek projekty z řešení můžete experimentovat s vlastní ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="439d4-153">Experiment with your own custom controls by adding and removing control projects from your solution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="439d4-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="439d4-154">See Also</span></span>  
 [<span data-ttu-id="439d4-155">Obecné, Návrhář formulářů Windows, dialogové okno Možnosti</span><span class="sxs-lookup"><span data-stu-id="439d4-155">General, Windows Forms Designer, Options Dialog Box</span></span>](https://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834)  
 [<span data-ttu-id="439d4-156">Postupy: manipulace s karty panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="439d4-156">How to: Manipulate Toolbox Tabs</span></span>](https://msdn.microsoft.com/library/21285050-cadd-455a-b1f5-a2289a89c4db)  
 [<span data-ttu-id="439d4-157">Zvolte dialogové okno položky panelu nástrojů (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="439d4-157">Choose Toolbox Items Dialog Box (Visual Studio)</span></span>](https://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [<span data-ttu-id="439d4-158">Vkládání ovládacích prvků do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="439d4-158">Putting Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)
