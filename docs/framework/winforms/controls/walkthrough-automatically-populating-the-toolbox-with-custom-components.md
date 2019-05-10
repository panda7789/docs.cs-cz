---
title: 'Návod: Automatické vyplnění sady nástrojů vlastními komponentami'
ms.date: 03/30/2017
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
ms.openlocfilehash: 876de650f9c182c0f82a02d1c5b356faa4f7f118
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211158"
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a><span data-ttu-id="d4166-102">Návod: Automatické vyplnění sady nástrojů vlastními komponentami</span><span class="sxs-lookup"><span data-stu-id="d4166-102">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>

<span data-ttu-id="d4166-103">Pokud vaše komponenty jsou definovány projektu v aktuálně otevřené řešení, se automaticky zobrazí v **nástrojů**, třeba akce.</span><span class="sxs-lookup"><span data-stu-id="d4166-103">If your components are defined by a project in the currently open solution, they will automatically appear in the **Toolbox**, with no action required by you.</span></span> <span data-ttu-id="d4166-104">Můžete také ručně naplnit **nástrojů** pomocí vlastních součástí s použitím [tlačítko panelu nástrojů položky dialogové okno (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100)), ale **nástrojů** bere v úvahu položky ve vašem řešení sestavení výstupy s následujícími charakteristikami:</span><span class="sxs-lookup"><span data-stu-id="d4166-104">You can also manually populate the **Toolbox** with your custom components by using the [Choose Toolbox Items Dialog Box (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100)), but the **Toolbox** takes account of items in your solution's build outputs with all the following characteristics:</span></span>

- <span data-ttu-id="d4166-105">Implementuje <xref:System.ComponentModel.IComponent>;</span><span class="sxs-lookup"><span data-stu-id="d4166-105">Implements <xref:System.ComponentModel.IComponent>;</span></span>

- <span data-ttu-id="d4166-106">Nemá <xref:System.ComponentModel.ToolboxItemAttribute> nastavena na `false`;</span><span class="sxs-lookup"><span data-stu-id="d4166-106">Does not have <xref:System.ComponentModel.ToolboxItemAttribute> set to `false`;</span></span>

- <span data-ttu-id="d4166-107">Nemá <xref:System.ComponentModel.DesignTimeVisibleAttribute> nastavena na `false`.</span><span class="sxs-lookup"><span data-stu-id="d4166-107">Does not have <xref:System.ComponentModel.DesignTimeVisibleAttribute> set to `false`.</span></span>

> [!NOTE]
> <span data-ttu-id="d4166-108">**Nástrojů** nedodržuje odkaz na řetězcích, proto by se nezobrazil položky, které nejsou sestaveny projekt ve vašem řešení.</span><span class="sxs-lookup"><span data-stu-id="d4166-108">The **Toolbox** does not follow reference chains, so it won't display items that are not built by a project in your solution.</span></span>

<span data-ttu-id="d4166-109">Tento návod ukazuje, jak vlastní komponenty se automaticky zobrazí v **nástrojů** po sestavení komponenty.</span><span class="sxs-lookup"><span data-stu-id="d4166-109">This walkthrough demonstrates how a custom component automatically appears in the **Toolbox** once the component is built.</span></span> <span data-ttu-id="d4166-110">Úlohy v tomto návodu zahrnují:</span><span class="sxs-lookup"><span data-stu-id="d4166-110">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="d4166-111">Vytvoření projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d4166-111">Creating a Windows Forms project.</span></span>

- <span data-ttu-id="d4166-112">Vytvoření vlastní komponenty.</span><span class="sxs-lookup"><span data-stu-id="d4166-112">Creating a custom component.</span></span>

- <span data-ttu-id="d4166-113">Vytvoření instance vlastní komponenty.</span><span class="sxs-lookup"><span data-stu-id="d4166-113">Creating an instance of a custom component.</span></span>

- <span data-ttu-id="d4166-114">Uvolnění a opětovné načtení volitelná množina komponent.</span><span class="sxs-lookup"><span data-stu-id="d4166-114">Unloading and reloading a custom component.</span></span>

<span data-ttu-id="d4166-115">Až budete hotovi, uvidíte, že **nástrojů** se vyplní komponentu, kterou jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="d4166-115">When you are finished, you will see that the **Toolbox** is populated with a component that you have created.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="d4166-116">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="d4166-116">Create the project</span></span>

1. <span data-ttu-id="d4166-117">V sadě Visual Studio vytvořte projekt aplikace pro systém Windows s názvem `ToolboxExample` (**souboru** > **nový** > **projektu**  >  **Visual C#**  nebo **jazyka Visual Basic** > **klasický desktopový** > **Windows Forms Aplikace**).</span><span class="sxs-lookup"><span data-stu-id="d4166-117">In Visual Studio, create a Windows-based application project called `ToolboxExample` (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="d4166-118">Přidáte novou součást do projektu.</span><span class="sxs-lookup"><span data-stu-id="d4166-118">Add a new component to the project.</span></span> <span data-ttu-id="d4166-119">Pojmenujte ji `DemoComponent`.</span><span class="sxs-lookup"><span data-stu-id="d4166-119">Call it `DemoComponent`.</span></span>

     <span data-ttu-id="d4166-120">Další informace najdete v tématu [jak: Přidání nových položek projektu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d4166-120">For more information, see [How to: Add New Project Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).</span></span>

3. <span data-ttu-id="d4166-121">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="d4166-121">Build the project.</span></span>

4. <span data-ttu-id="d4166-122">Z **nástroje** nabídky, klikněte na tlačítko **možnosti** položky.</span><span class="sxs-lookup"><span data-stu-id="d4166-122">From the **Tools** menu, click the **Options** item.</span></span> <span data-ttu-id="d4166-123">Klikněte na tlačítko **Obecné** pod **Návrháře formulářů Windows** položku a ověřte, že **AutoToolboxPopulate** je možnost nastavená na **True**.</span><span class="sxs-lookup"><span data-stu-id="d4166-123">Click **General** under the **Windows Forms Designer** item and ensure that the **AutoToolboxPopulate** option is set to **True**.</span></span>

## <a name="create-an-instance-of-a-custom-component"></a><span data-ttu-id="d4166-124">Vytvoření instance vlastní komponenty</span><span class="sxs-lookup"><span data-stu-id="d4166-124">Create an instance of a custom component</span></span>

<span data-ttu-id="d4166-125">Dalším krokem je vytvoření instance vlastní komponenty ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="d4166-125">The next step is to create an instance of the custom component on the form.</span></span> <span data-ttu-id="d4166-126">Vzhledem k tomu, **nástrojů** automaticky účty pro novou komponentu, to je stejně jednoduché jako vytvoření jakékoli součást nebo ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="d4166-126">Because the **Toolbox** automatically accounts for the new component, this is as easy as creating any other component or control.</span></span>

1. <span data-ttu-id="d4166-127">Otevřete formulář v projektu v **Návrháře formulářů**.</span><span class="sxs-lookup"><span data-stu-id="d4166-127">Open the project's form in the **Forms Designer**.</span></span>

2. <span data-ttu-id="d4166-128">V **nástrojů**, klikněte na novou kartu **ToolboxExample komponenty**.</span><span class="sxs-lookup"><span data-stu-id="d4166-128">In the **Toolbox**, click the new tab called **ToolboxExample Components**.</span></span>

     <span data-ttu-id="d4166-129">Po kliknutí na kartě, zobrazí se **DemoComponent**.</span><span class="sxs-lookup"><span data-stu-id="d4166-129">Once you click the tab, you will see **DemoComponent**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d4166-130">Z důvodů výkonu komponenty v oblasti vyplní automaticky **nástrojů** vlastních rastrových obrázků, se nezobrazí a <xref:System.Drawing.ToolboxBitmapAttribute> se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="d4166-130">For performance reasons, components in the auto-populated area of the **Toolbox** do not display custom bitmaps, and the <xref:System.Drawing.ToolboxBitmapAttribute> is not supported.</span></span> <span data-ttu-id="d4166-131">Zobrazit ikonu pro vlastní komponenty v **nástrojů**, použijte **zvolit položky nástrojů** dialogové okno načíst vaše komponenta.</span><span class="sxs-lookup"><span data-stu-id="d4166-131">To display an icon for a custom component in the **Toolbox**, use the **Choose Toolbox Items** dialog box to load your component.</span></span>

3. <span data-ttu-id="d4166-132">Přetáhněte komponenty do formuláře.</span><span class="sxs-lookup"><span data-stu-id="d4166-132">Drag your component onto your form.</span></span>

     <span data-ttu-id="d4166-133">Je vytvořen a přidán do instance komponenty **komponent**.</span><span class="sxs-lookup"><span data-stu-id="d4166-133">An instance of the component is created and added to the **Component Tray**.</span></span>

## <a name="unload-and-reload-a-custom-component"></a><span data-ttu-id="d4166-134">Odebrat a znovu načíst vlastní komponenty</span><span class="sxs-lookup"><span data-stu-id="d4166-134">Unload and reload a custom component</span></span>

<span data-ttu-id="d4166-135">**Nástrojů** přihlíží komponent v každém načtení projektu a projekt je uvolněna, odebere odkazy na součásti projektu.</span><span class="sxs-lookup"><span data-stu-id="d4166-135">The **Toolbox** takes account of the components in each loaded project, and when a project is unloaded, it removes references to the project's components.</span></span>

1. <span data-ttu-id="d4166-136">Uvolněte projekt z řešení.</span><span class="sxs-lookup"><span data-stu-id="d4166-136">Unload the project from the solution.</span></span>

     <span data-ttu-id="d4166-137">Další informace o uvolnění projektů, naleznete v tématu [jak: Odebrat a znovu načíst projekty](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/tt479x1t(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d4166-137">For more information about unloading projects, see [How to: Unload and Reload Projects](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/tt479x1t(v=vs.100)).</span></span> <span data-ttu-id="d4166-138">Pokud se zobrazí výzva k uložení, zvolte **Ano**.</span><span class="sxs-lookup"><span data-stu-id="d4166-138">If you are prompted to save, choose **Yes**.</span></span>

2. <span data-ttu-id="d4166-139">Přidat nový **aplikace Windows** projektu do řešení.</span><span class="sxs-lookup"><span data-stu-id="d4166-139">Add a new **Windows Application** project to the solution.</span></span> <span data-ttu-id="d4166-140">Otevřete formulář v nástrojích pro **návrháře**.</span><span class="sxs-lookup"><span data-stu-id="d4166-140">Open the form in the **Designer**.</span></span>

     <span data-ttu-id="d4166-141">**ToolboxExample součásti** kartu z předchozí projektu je teď pryč.</span><span class="sxs-lookup"><span data-stu-id="d4166-141">The **ToolboxExample Components** tab from the previous project is now gone.</span></span>

3. <span data-ttu-id="d4166-142">Znovu načíst `ToolboxExample` projektu.</span><span class="sxs-lookup"><span data-stu-id="d4166-142">Reload the `ToolboxExample` project.</span></span>

     <span data-ttu-id="d4166-143">**ToolboxExample součásti** kartě nyní zobrazí znovu.</span><span class="sxs-lookup"><span data-stu-id="d4166-143">The **ToolboxExample Components** tab now reappears.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d4166-144">Další kroky</span><span class="sxs-lookup"><span data-stu-id="d4166-144">Next steps</span></span>

<span data-ttu-id="d4166-145">Tento návod ukazuje, že **nástrojů** bere v úvahu součástí projektu, ale **nástrojů** je také přihlíží ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="d4166-145">This walkthrough demonstrates that the **Toolbox** takes account of a project's components, but the **Toolbox** is also takes account of controls.</span></span> <span data-ttu-id="d4166-146">Přidáváním a odebíráním ovládací prvek projekty z řešení můžete experimentovat s vlastní ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="d4166-146">Experiment with your own custom controls by adding and removing control projects from your solution.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4166-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d4166-147">See also</span></span>

- <span data-ttu-id="d4166-148">[Obecné, Návrhář formulářů Windows, dialogové okno Možnosti](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d4166-148">[General, Windows Forms Designer, Options Dialog Box](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100))</span></span>
- <span data-ttu-id="d4166-149">[Postupy: Manipulace s karty panelu nástrojů](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/66kwe227(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d4166-149">[How to: Manipulate Toolbox Tabs](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/66kwe227(v=vs.100))</span></span>
- <span data-ttu-id="d4166-150">[Zvolte dialogové okno položky panelu nástrojů (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d4166-150">[Choose Toolbox Items Dialog Box (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))</span></span>
- [<span data-ttu-id="d4166-151">Vkládání ovládacích prvků do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d4166-151">Putting Controls on Windows Forms</span></span>](putting-controls-on-windows-forms.md)
