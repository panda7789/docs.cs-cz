---
title: "Návod: Ladění vlastních ovládacích prvků Windows Forms během návrhu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- custom controls [Windows Forms], walkthroughs
- visual editors
- debugging [Visual Studio], Windows Forms
- custom controls [Windows Forms], debugging
- designers
- controls [Windows Forms], debugging
- walkthroughs [Windows Forms], debugging
- design-time debugging
ms.assetid: 1fd83ccd-3798-42fc-85a3-6cba99467387
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4dfdc102a5aeb2e3eaccde28a8ce57a1878141e4
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-debugging-custom-windows-forms-controls-at-design-time"></a><span data-ttu-id="44a0c-102">Návod: Ladění vlastních ovládacích prvků Windows Forms během návrhu</span><span class="sxs-lookup"><span data-stu-id="44a0c-102">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>
<span data-ttu-id="44a0c-103">Při vytváření vlastního ovládacího prvku často zjistíte, je nezbytné k ladění její chování v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="44a0c-103">When you create a custom control, you will often find it necessary to debug its design-time behavior.</span></span> <span data-ttu-id="44a0c-104">To platí hlavně vytváříte-li vlastní návrháře pro vaše vlastní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="44a0c-104">This is especially true if you are authoring a custom designer for your custom control.</span></span> <span data-ttu-id="44a0c-105">Podrobnosti najdete v tématu [návod: vytváření funkce systému Windows Forms ovládací prvek, trvá využít nástroje Visual Studio návrhu](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span><span class="sxs-lookup"><span data-stu-id="44a0c-105">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span></span>  
  
 <span data-ttu-id="44a0c-106">Vlastní ovládací prvky pomocí sady Visual Studio, můžete ladit, stejně jako ostatní třídy rozhraní .NET Framework by ladění.</span><span class="sxs-lookup"><span data-stu-id="44a0c-106">You can debug your custom controls using Visual Studio, just as you would debug any other .NET Framework classes.</span></span> <span data-ttu-id="44a0c-107">Rozdíl je, že ladíte samostatnou instanci Visual Studia, která běží kód vlastní ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="44a0c-107">The difference is that you will debug a separate instance of Visual Studio that is running your custom control's code</span></span>  
  
 <span data-ttu-id="44a0c-108">Úkoly v tomto návodu zahrnují:</span><span class="sxs-lookup"><span data-stu-id="44a0c-108">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="44a0c-109">Vytvoření projektu pro hostování vašeho vlastního ovládacího prvku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="44a0c-109">Creating a Windows Forms project to host your custom control</span></span>  
  
-   <span data-ttu-id="44a0c-110">Vytvoření projektu knihovny ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="44a0c-110">Creating a control library project</span></span>  
  
-   <span data-ttu-id="44a0c-111">Přidání vlastnosti do vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="44a0c-111">Adding a property to your custom control</span></span>  
  
-   <span data-ttu-id="44a0c-112">Přidání vlastního ovládacího prvku na formulář hostitele</span><span class="sxs-lookup"><span data-stu-id="44a0c-112">Adding your custom control to the host form</span></span>  
  
-   <span data-ttu-id="44a0c-113">Nastavení projektu pro ladění v době návrhu</span><span class="sxs-lookup"><span data-stu-id="44a0c-113">Setting up the project for design-time debugging</span></span>  
  
-   <span data-ttu-id="44a0c-114">Ladění vlastního ovládacího prvku v době návrhu</span><span class="sxs-lookup"><span data-stu-id="44a0c-114">Debugging your custom control at design time</span></span>  
  
 <span data-ttu-id="44a0c-115">Jakmile budete hotovi, budete mít k pochopení úlohy plánování pro ladění v době návrhu chování vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="44a0c-115">When you are finished, you will have an understanding of the tasks necessary for debugging the design-time behavior of a custom control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44a0c-116">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="44a0c-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="44a0c-117">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="44a0c-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="44a0c-118">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="44a0c-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="44a0c-119">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="44a0c-119">Creating the Project</span></span>  
 <span data-ttu-id="44a0c-120">Prvním krokem je vytvoření projektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="44a0c-120">The first step is to create the application project.</span></span> <span data-ttu-id="44a0c-121">Tento projekt použije k vytvoření aplikace, který je hostitelem vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="44a0c-121">You will use this project to build the application that hosts the custom control.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="44a0c-122">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="44a0c-122">To create the project</span></span>  
  
-   <span data-ttu-id="44a0c-123">Vytvořte projekt aplikace pro systém Windows s názvem "DebuggingExample".</span><span class="sxs-lookup"><span data-stu-id="44a0c-123">Create a Windows Application project called "DebuggingExample".</span></span> <span data-ttu-id="44a0c-124">Podrobnosti najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="44a0c-124">For details, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
## <a name="creating-a-control-library-project"></a><span data-ttu-id="44a0c-125">Vytvoření projektu knihovny ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="44a0c-125">Creating a Control Library Project</span></span>  
 <span data-ttu-id="44a0c-126">Dalším krokem je vytvoření projektu knihovny řízení a nastavení vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="44a0c-126">The next step is to create the control library project and set up the custom control.</span></span>  
  
#### <a name="to-create-the-control-library-project"></a><span data-ttu-id="44a0c-127">Vytvoření projektu knihovny ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="44a0c-127">To create the control library project</span></span>  
  
1.  <span data-ttu-id="44a0c-128">Přidat **knihovny ovládacích prvků Windows** projektu k řešení.</span><span class="sxs-lookup"><span data-stu-id="44a0c-128">Add a **Windows Control Library** project to the solution.</span></span>  
  
2.  <span data-ttu-id="44a0c-129">Přidejte nový **UserControl** položky k DebugControlLibrary projektu.</span><span class="sxs-lookup"><span data-stu-id="44a0c-129">Add a new **UserControl** item to the DebugControlLibrary project.</span></span> <span data-ttu-id="44a0c-130">Podrobnosti najdete v tématu [NIB: postupy: Přidání nové položky projektu](http://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span><span class="sxs-lookup"><span data-stu-id="44a0c-130">For details, see [NIB:How to: Add New Project Items](http://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span></span> <span data-ttu-id="44a0c-131">Zadejte základní název "DebugControl" nové zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="44a0c-131">Give the new source file a base name of "DebugControl".</span></span>  
  
3.  <span data-ttu-id="44a0c-132">Pomocí **Průzkumníku řešení**, odstraňte výchozí řízení projektu odstraněním souboru kódu s základní název "`UserControl1`".</span><span class="sxs-lookup"><span data-stu-id="44a0c-132">Using the **Solution Explorer**, delete the project's default control by deleting the code file with a base name of "`UserControl1`".</span></span> <span data-ttu-id="44a0c-133">Podrobnosti najdete v tématu [NIB: postupy: odebrání, odstranění a vyloučit položky](http://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span><span class="sxs-lookup"><span data-stu-id="44a0c-133">For details, see [NIB:How to: Remove, Delete, and Exclude Items](http://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span></span>  
  
4.  <span data-ttu-id="44a0c-134">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="44a0c-134">Build the solution.</span></span>  
  
## <a name="checkpoint"></a><span data-ttu-id="44a0c-135">Kontrolní bod</span><span class="sxs-lookup"><span data-stu-id="44a0c-135">Checkpoint</span></span>  
 <span data-ttu-id="44a0c-136">V tomto okamžiku bude moci zobrazit vaše vlastní ovládací prvek v **sada nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="44a0c-136">At this point, you will be able to see your custom control in the **Toolbox**.</span></span>  
  
#### <a name="to-check-your-progress"></a><span data-ttu-id="44a0c-137">Chcete-li zkontrolovat průběh</span><span class="sxs-lookup"><span data-stu-id="44a0c-137">To check your progress</span></span>  
  
-   <span data-ttu-id="44a0c-138">Najít novou kartu názvem **DebugControlLibrary součásti** a kliknutím vyberte ho.</span><span class="sxs-lookup"><span data-stu-id="44a0c-138">Find the new tab called **DebugControlLibrary Components** and click to select it.</span></span> <span data-ttu-id="44a0c-139">Když se otevře, zobrazí se vlastní ovládací prvek uveden jako **DebugControl** s výchozí ikonu vedle ní.</span><span class="sxs-lookup"><span data-stu-id="44a0c-139">When it opens, you will see your control listed as **DebugControl** with the default icon beside it.</span></span>  
  
## <a name="adding-a-property-to-your-custom-control"></a><span data-ttu-id="44a0c-140">Přidání vlastnosti do vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="44a0c-140">Adding a Property to Your Custom Control</span></span>  
 <span data-ttu-id="44a0c-141">K prokázání, že vlastní řídicí kód běží v době návrhu, bude přidání vlastnosti a nastavení zarážky v kódu, který implementuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="44a0c-141">To demonstrate that your custom control's code is running at design-time, you will add a property and set a breakpoint in the code that implements the property.</span></span>  
  
#### <a name="to-add-a-property-to-your-custom-control"></a><span data-ttu-id="44a0c-142">Přidání vlastnosti do vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="44a0c-142">To add a property to your custom control</span></span>  
  
1.  <span data-ttu-id="44a0c-143">Otevřete **DebugControl** v **Editor kódu**.</span><span class="sxs-lookup"><span data-stu-id="44a0c-143">Open **DebugControl** in the **Code Editor**.</span></span> <span data-ttu-id="44a0c-144">Přidejte následující kód v definici třídy:</span><span class="sxs-lookup"><span data-stu-id="44a0c-144">Add the following code to the class definition:</span></span>  
  
    ```vb  
    Private demoStringValue As String = Nothing  
    <BrowsableAttribute(true)>  
    Public Property DemoString() As String  
  
        Get  
            Return Me.demoStringValue  
        End Get  
  
        Set(ByVal value As String)  
            Me.demoStringValue = value  
        End Set  
  
    End Property  
    ```  
  
    ```csharp  
    private string demoStringValue = null;  
    [Browsable(true)]  
    public string DemoString  
    {  
        get  
        {  
            return this.demoStringValue;  
        }  
        set  
        {  
            demoStringValue = value;  
        }  
    }  
    ```  
  
2.  <span data-ttu-id="44a0c-145">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="44a0c-145">Build the solution.</span></span>  
  
## <a name="adding-your-custom-control-to-the-host-form"></a><span data-ttu-id="44a0c-146">Přidání vlastního ovládacího prvku na formulář hostitele</span><span class="sxs-lookup"><span data-stu-id="44a0c-146">Adding Your Custom Control to the Host Form</span></span>  
 <span data-ttu-id="44a0c-147">Ladění chování návrhu vlastního ovládacího prvku, umístí instance třídy vlastního ovládacího prvku ve formuláři hostitele.</span><span class="sxs-lookup"><span data-stu-id="44a0c-147">To debug the design-time behavior of your custom control, you will place an instance of the custom control class on a host form.</span></span>  
  
#### <a name="to-add-your-custom-control-to-the-host-form"></a><span data-ttu-id="44a0c-148">Přidání vlastního ovládacího prvku do formuláře hostitele</span><span class="sxs-lookup"><span data-stu-id="44a0c-148">To add your custom control to the host form</span></span>  
  
1.  <span data-ttu-id="44a0c-149">V projektu "DebuggingExample" otevřete Form1 v **Návrhář formulářů Windows**.</span><span class="sxs-lookup"><span data-stu-id="44a0c-149">In the "DebuggingExample" project, open Form1 in the **Windows Forms Designer**.</span></span>  
  
2.  <span data-ttu-id="44a0c-150">V **sada nástrojů**, otevřete **DebugControlLibrary součásti** kartě a přetáhněte ji **DebugControl** instance do formuláře.</span><span class="sxs-lookup"><span data-stu-id="44a0c-150">In the **Toolbox**, open the **DebugControlLibrary Components** tab and drag a **DebugControl** instance onto the form.</span></span>  
  
3.  <span data-ttu-id="44a0c-151">Najít `DemoString` vlastní vlastnost **vlastnosti** okno.</span><span class="sxs-lookup"><span data-stu-id="44a0c-151">Find the `DemoString` custom property in the **Properties** window.</span></span> <span data-ttu-id="44a0c-152">Všimněte si, že stejně jako všechny ostatní vlastnosti můžete změnit jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="44a0c-152">Note that you can change its value as you would any other property.</span></span> <span data-ttu-id="44a0c-153">Všimněte si, že pokud `DemoString` vlastnost je vybraná, řetězec popisu vlastnosti se zobrazí v dolní části **vlastnosti** okno.</span><span class="sxs-lookup"><span data-stu-id="44a0c-153">Also note that when the `DemoString` property is selected, the property's description string appears at the bottom of the **Properties** window.</span></span>  
  
## <a name="setting-up-the-project-for-design-time-debugging"></a><span data-ttu-id="44a0c-154">Nastavení projektu pro ladění v době návrhu</span><span class="sxs-lookup"><span data-stu-id="44a0c-154">Setting Up the Project for Design-Time Debugging</span></span>  
 <span data-ttu-id="44a0c-155">K ladění chování vlastního ovládacího prvku v době návrhu, bude ladění samostatnou instanci Visual Studia, která běží vlastní řídicí kód.</span><span class="sxs-lookup"><span data-stu-id="44a0c-155">To debug your custom control's design-time behavior, you will debug a separate instance of Visual Studio that is running your custom control's code.</span></span>  
  
#### <a name="to-set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="44a0c-156">Nastavení projektu pro ladění v době návrhu</span><span class="sxs-lookup"><span data-stu-id="44a0c-156">To set up the project for design-time debugging</span></span>  
  
1.  <span data-ttu-id="44a0c-157">Klikněte pravým tlačítkem na **DebugControlLibrary** v projektu **Průzkumníku řešení** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="44a0c-157">Right-click on the **DebugControlLibrary** project in the **Solution Explorer** and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="44a0c-158">V **DebugControlLibrary** seznamu vlastností, vyberte **ladění** kartě.</span><span class="sxs-lookup"><span data-stu-id="44a0c-158">In the **DebugControlLibrary** property sheet, select the **Debug** tab.</span></span>  
  
     <span data-ttu-id="44a0c-159">V **spustit akci** vyberte **počáteční vnějšímu programu**.</span><span class="sxs-lookup"><span data-stu-id="44a0c-159">In the **Start Action** section, select **Start external program**.</span></span> <span data-ttu-id="44a0c-160">Bude ladění samostatné instanci sady Visual Studio, proto klikněte na tlačítko se třemi tečkami (![– snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) tlačítko procházení pro Visual Studio IDE.</span><span class="sxs-lookup"><span data-stu-id="44a0c-160">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="44a0c-161">Název spustitelného souboru je **devenv.exe**, a pokud jste nainstalovali do výchozího umístění, je jeho cestu 9.0\Common7\IDE\devenv.exe %programfiles%\Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="44a0c-161">The name of the executable file is **devenv.exe**, and if you installed to the default location, its path is %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe.</span></span>  
  
3.  <span data-ttu-id="44a0c-162">Klikněte na tlačítko **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="44a0c-162">Click **OK** to close the dialog box.</span></span>  
  
4.  <span data-ttu-id="44a0c-163">Klikněte pravým tlačítkem myši **DebugControlLibrary** projektu a vyberte **nastavit jako spouštěný projekt** Chcete-li povolit tuto konfiguraci ladění.</span><span class="sxs-lookup"><span data-stu-id="44a0c-163">Right-click the **DebugControlLibrary** project and select **Set as StartUp Project** to enable this debugging configuration.</span></span>  
  
## <a name="debugging-your-custom-control-at-design-time"></a><span data-ttu-id="44a0c-164">Ladění vlastního ovládacího prvku v době návrhu</span><span class="sxs-lookup"><span data-stu-id="44a0c-164">Debugging Your Custom Control at Design Time</span></span>  
 <span data-ttu-id="44a0c-165">Nyní jste připraveni k ladění vlastního ovládacího prvku při jeho spuštění v režimu návrhu.</span><span class="sxs-lookup"><span data-stu-id="44a0c-165">Now you are ready to debug your custom control as it runs in design mode.</span></span> <span data-ttu-id="44a0c-166">Když spustíte relaci ladění, vytvoří novou instanci sady Visual Studio a použije ho k načtení řešení "DebuggingExample".</span><span class="sxs-lookup"><span data-stu-id="44a0c-166">When you start the debugging session, a new instance of Visual Studio will be created, and you will use it to load the "DebuggingExample" solution.</span></span> <span data-ttu-id="44a0c-167">Když otevřete Form1 v **Návrhář formulářů**, instanci vlastního ovládacího prvku se vytvoří a spustí systémem.</span><span class="sxs-lookup"><span data-stu-id="44a0c-167">When you open Form1 in the **Forms Designer**, an instance of your custom control will be created and will start running.</span></span>  
  
#### <a name="to-debug-your-custom-control-at-design-time"></a><span data-ttu-id="44a0c-168">Chcete-li ladit vlastního ovládacího prvku v době návrhu</span><span class="sxs-lookup"><span data-stu-id="44a0c-168">To debug your custom control at design time</span></span>  
  
1.  <span data-ttu-id="44a0c-169">Otevřete **DebugControl** zdrojový soubor v **Editor kódu** a umístěte zarážku na `Set` přistupujícího `DemoString` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="44a0c-169">Open the **DebugControl** source file in the **Code Editor** and place a breakpoint on the `Set` accessor of the `DemoString` property.</span></span>  
  
2.  <span data-ttu-id="44a0c-170">Stisknutím klávesy F5 spusťte relaci ladění.</span><span class="sxs-lookup"><span data-stu-id="44a0c-170">Press F5 to start the debugging session.</span></span> <span data-ttu-id="44a0c-171">Všimněte si, že je vytvořena nová instance sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="44a0c-171">Note that a new instance of Visual Studio is created.</span></span> <span data-ttu-id="44a0c-172">Možné rozlišit mezi instancemi dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="44a0c-172">You can distinguish between the instances in two ways:</span></span>  
  
    -   <span data-ttu-id="44a0c-173">Ladění instance má slovo **systémem** v jeho záhlaví</span><span class="sxs-lookup"><span data-stu-id="44a0c-173">The debugging instance has the word **Running** in its title bar</span></span>  
  
    -   <span data-ttu-id="44a0c-174">Ladění instance má **spustit** tlačítko na jeho **ladění** zakázáno panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="44a0c-174">The debugging instance has the **Start** button on its **Debug** toolbar disabled</span></span>  
  
     <span data-ttu-id="44a0c-175">Vaší zarážce se nastavuje v ladění instance.</span><span class="sxs-lookup"><span data-stu-id="44a0c-175">Your breakpoint is set in the debugging instance.</span></span>  
  
3.  <span data-ttu-id="44a0c-176">V nové instanci sady Visual Studio otevřete řešení "DebuggingExample".</span><span class="sxs-lookup"><span data-stu-id="44a0c-176">In the new instance of Visual Studio, open the "DebuggingExample" solution.</span></span> <span data-ttu-id="44a0c-177">Budete moci snadno najít řešení výběrem **poslední projekty** z **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="44a0c-177">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="44a0c-178">Soubor řešení "DebuggingExample.sln" se objeví jako naposledy použitých souborů.</span><span class="sxs-lookup"><span data-stu-id="44a0c-178">The "DebuggingExample.sln" solution file will be listed as the most recently used file.</span></span>  
  
4.  <span data-ttu-id="44a0c-179">Otevřete Form1 v **Návrhář formulářů** a vyberte **DebugControl** ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="44a0c-179">Open Form1 in the **Forms Designer** and select the **DebugControl** control.</span></span>  
  
5.  <span data-ttu-id="44a0c-180">Změňte hodnotu `DemoString` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="44a0c-180">Change the value of the `DemoString` property.</span></span> <span data-ttu-id="44a0c-181">Upozorňujeme, že pokud provedete změny, získá fokus ladění instanci sady Visual Studio a spuštění zastaví na vaší zarážce.</span><span class="sxs-lookup"><span data-stu-id="44a0c-181">Note that when you commit the change, the debugging instance of Visual Studio acquires focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="44a0c-182">Můžete krokování prostřednictvím přistupující objekt vlastnosti stejně jako vaše by jakýkoli jiný kód.</span><span class="sxs-lookup"><span data-stu-id="44a0c-182">You can single-step through the property accessor just as your would any other code.</span></span>  
  
6.  <span data-ttu-id="44a0c-183">Když skončíte s vaší relace ladění, můžete ukončit zrušením hostované instanci sady Visual Studio nebo kliknutím **Zastavte ladění** tlačítka na ladění instance.</span><span class="sxs-lookup"><span data-stu-id="44a0c-183">When you are finished with your debugging session, you can exit by dismissing the hosted instance of Visual Studio or by clicking the **Stop Debugging** button in the debugging instance.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="44a0c-184">Další kroky</span><span class="sxs-lookup"><span data-stu-id="44a0c-184">Next Steps</span></span>  
 <span data-ttu-id="44a0c-185">Teď, když ladíte vlastní ovládací prvky v době návrhu existuje mnoho možností pro rozšíření interakci ovládacího prvku s Visual Studio IDE.</span><span class="sxs-lookup"><span data-stu-id="44a0c-185">Now that you can debug your custom controls at design time, there are many possibilities for expanding your control's interaction with the Visual Studio IDE.</span></span>  
  
-   <span data-ttu-id="44a0c-186">Můžete použít <xref:System.ComponentModel.Component.DesignMode%2A> vlastnost <xref:System.ComponentModel.Component> třídu k zápisu kódu, který spustí, pouze v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="44a0c-186">You can use the <xref:System.ComponentModel.Component.DesignMode%2A> property of the <xref:System.ComponentModel.Component> class to write code that will only execute at design time.</span></span> <span data-ttu-id="44a0c-187">Podrobnosti najdete v tématu <xref:System.ComponentModel.Component.DesignMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="44a0c-187">For details, see <xref:System.ComponentModel.Component.DesignMode%2A>.</span></span>  
  
-   <span data-ttu-id="44a0c-188">Několik atributů můžete provést u vlastnosti ovládacího prvku k manipulaci s interakce vlastního ovládacího prvku pomocí návrháře.</span><span class="sxs-lookup"><span data-stu-id="44a0c-188">There are several attributes you can apply to your control's properties to manipulate your custom control's interaction with the designer.</span></span> <span data-ttu-id="44a0c-189">Můžete najít v těchto atributů <xref:System.ComponentModel?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="44a0c-189">You can find these attributes in the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span>  
  
-   <span data-ttu-id="44a0c-190">Můžete napsat vlastní návrháře pro vaše vlastní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="44a0c-190">You can write a custom designer for your custom control.</span></span> <span data-ttu-id="44a0c-191">To vám dává úplnou kontrolu nad prostředí návrhu pomocí extensible návrháře infrastruktury vystavené Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="44a0c-191">This gives you complete control over the design experience using the extensible designer infrastructure exposed by Visual Studio.</span></span> <span data-ttu-id="44a0c-192">Podrobnosti najdete v tématu [návod: vytváření funkce systému Windows Forms ovládací prvek, trvá využít nástroje Visual Studio návrhu](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span><span class="sxs-lookup"><span data-stu-id="44a0c-192">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44a0c-193">Viz také</span><span class="sxs-lookup"><span data-stu-id="44a0c-193">See Also</span></span>  
 [<span data-ttu-id="44a0c-194">Návod: Vytvoření ovládacího prvku Windows Forms, který využívá funkce sady Visual Studio pro dobu návrhu</span><span class="sxs-lookup"><span data-stu-id="44a0c-194">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
 [<span data-ttu-id="44a0c-195">Postupy: přístup ke službám v době návrhu</span><span class="sxs-lookup"><span data-stu-id="44a0c-195">How to: Access Design-Time Services</span></span>](http://msdn.microsoft.com/library/c186c4b6-076c-438d-9ed3-f13da29c8c1f)  
 [<span data-ttu-id="44a0c-196">Postupy: přístup k podpoře návrhu v systému Windows Forms</span><span class="sxs-lookup"><span data-stu-id="44a0c-196">How to: Access Design-Time Support in Windows Forms</span></span>](http://msdn.microsoft.com/library/a84f8579-1f47-41b9-ba37-69030b0aff09)
