---
title: Vytvoření aktivity za běhu pomocí DynamicActivity
description: DynamicActivity je konkrétní zapečetěná třída s veřejným konstruktorem. Použijte třídu k sestavení funkcí aktivity za běhu pomocí modelu DOM aktivity.
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: 17ee14be7df4801018c7afd2e91f1fb07c34e8e1
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421537"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a><span data-ttu-id="5f9f8-104">Vytvoření aktivity za běhu pomocí DynamicActivity</span><span class="sxs-lookup"><span data-stu-id="5f9f8-104">Creating an Activity at Runtime with DynamicActivity</span></span>
<span data-ttu-id="5f9f8-105"><xref:System.Activities.DynamicActivity>je konkrétní zapečetěná třída s veřejným konstruktorem.</span><span class="sxs-lookup"><span data-stu-id="5f9f8-105"><xref:System.Activities.DynamicActivity> is a concrete, sealed class with a public constructor.</span></span> <span data-ttu-id="5f9f8-106"><xref:System.Activities.DynamicActivity>dá se použít k sestavování funkčnosti aktivity za běhu pomocí modelu DOM aktivity.</span><span class="sxs-lookup"><span data-stu-id="5f9f8-106"><xref:System.Activities.DynamicActivity> can be used to assemble activity functionality at runtime using an activity DOM.</span></span>  
  
## <a name="dynamicactivity-features"></a><span data-ttu-id="5f9f8-107">Funkce DynamicActivity</span><span class="sxs-lookup"><span data-stu-id="5f9f8-107">DynamicActivity Features</span></span>  
 <span data-ttu-id="5f9f8-108"><xref:System.Activities.DynamicActivity>má přístup k vlastnostem spuštění, argumentům a proměnným, ale nemá přístup ke službám runtime, jako je plánování podřízených aktivit nebo sledování.</span><span class="sxs-lookup"><span data-stu-id="5f9f8-108"><xref:System.Activities.DynamicActivity> has access to execution properties, arguments and variables, but no access to run-time services such as scheduling child activities or tracking.</span></span>  
  
 <span data-ttu-id="5f9f8-109">Vlastnosti nejvyšší úrovně lze nastavit pomocí objektů pracovního postupu <xref:System.Activities.Argument> .</span><span class="sxs-lookup"><span data-stu-id="5f9f8-109">Top-level properties can be set using workflow <xref:System.Activities.Argument> objects.</span></span> <span data-ttu-id="5f9f8-110">V imperativním kódu jsou tyto argumenty vytvořeny pomocí vlastností CLR pro nový typ.</span><span class="sxs-lookup"><span data-stu-id="5f9f8-110">In imperative code, these arguments are created using CLR properties on a new type.</span></span> <span data-ttu-id="5f9f8-111">V jazyce XAML jsou deklarovány pomocí `x:Class` `x:Member` značek a.</span><span class="sxs-lookup"><span data-stu-id="5f9f8-111">In XAML, they are declared using `x:Class` and `x:Member` tags.</span></span>  
  
 <span data-ttu-id="5f9f8-112">Aktivity vytvořené pomocí <xref:System.Activities.DynamicActivity> rozhraní s návrhářem pomocí <xref:System.ComponentModel.ICustomTypeDescriptor> .</span><span class="sxs-lookup"><span data-stu-id="5f9f8-112">Activities constructed using <xref:System.Activities.DynamicActivity> interface with the designer using <xref:System.ComponentModel.ICustomTypeDescriptor>.</span></span> <span data-ttu-id="5f9f8-113">Aktivity vytvořené v Návrháři lze dynamicky načíst pomocí <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> , jak je znázorněno v následujícím postupu.</span><span class="sxs-lookup"><span data-stu-id="5f9f8-113">Activities created in the designer can be loaded dynamically using <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, as demonstrated in the following procedure.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a><span data-ttu-id="5f9f8-114">Vytvoření aktivity za běhu pomocí imperativního kódu</span><span class="sxs-lookup"><span data-stu-id="5f9f8-114">To create an activity at runtime using imperative code</span></span>  
  
1. <span data-ttu-id="5f9f8-115">OpenVisual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="5f9f8-115">OpenVisual Studio 2010.</span></span>  
  
2. <span data-ttu-id="5f9f8-116">Vyberte **soubor**, **Nový**, **projekt**.</span><span class="sxs-lookup"><span data-stu-id="5f9f8-116">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="5f9f8-117">V okně **typy projektů** vyberte **pracovní postup 4,0** v jazyce **Visual C#** a vyberte uzel **v2010** .</span><span class="sxs-lookup"><span data-stu-id="5f9f8-117">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="5f9f8-118">V okně **šablony** vyberte **Konzolová aplikace sekvenčního pracovního postupu** .</span><span class="sxs-lookup"><span data-stu-id="5f9f8-118">Select **Sequential Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="5f9f8-119">Pojmenujte nový projekt DynamicActivitySample.</span><span class="sxs-lookup"><span data-stu-id="5f9f8-119">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="5f9f8-120">Klikněte pravým tlačítkem na Workflow1. XAML v projektu HelloActivity a vyberte **Odstranit**.</span><span class="sxs-lookup"><span data-stu-id="5f9f8-120">Right-click Workflow1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4. <span data-ttu-id="5f9f8-121">Otevřete Program.cs.</span><span class="sxs-lookup"><span data-stu-id="5f9f8-121">Open Program.cs.</span></span> <span data-ttu-id="5f9f8-122">Do horní části souboru přidejte následující direktivu.</span><span class="sxs-lookup"><span data-stu-id="5f9f8-122">Add the following directive to the top of the file.</span></span>  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
5. <span data-ttu-id="5f9f8-123">Nahraďte obsah `Main` metody následujícím kódem, který vytvoří <xref:System.Activities.Statements.Sequence> aktivitu, která obsahuje jednu <xref:System.Activities.Statements.WriteLine> aktivitu a přiřadí ji k <xref:System.Activities.DynamicActivity.Implementation%2A> Vlastnosti nové dynamické aktivity.</span><span class="sxs-lookup"><span data-stu-id="5f9f8-123">Replace the contents of the `Main` method with the following code, which creates a <xref:System.Activities.Statements.Sequence> activity that contains a single <xref:System.Activities.Statements.WriteLine> activity and assigns it to the <xref:System.Activities.DynamicActivity.Implementation%2A> property of a new dynamic activity.</span></span>  
  
    ```csharp  
    //Define the input argument for the activity  
    var textOut = new InArgument<string>();  
    //Create the activity, property, and implementation  
                Activity dynamicWorkflow = new DynamicActivity()  
                {  
                    Properties =
                    {  
                        new DynamicActivityProperty  
                        {  
                            Name = "Text",  
                            Type = typeof(InArgument<String>),  
                            Value = textOut  
                        }  
                    },  
                    Implementation = () => new Sequence()  
                    {  
                        Activities =
                        {  
                            new WriteLine()  
                            {  
                                Text = new InArgument<string>(env => textOut.Get(env))  
                            }  
                        }  
                    }  
                };  
    //Execute the activity with a parameter dictionary  
                WorkflowInvoker.Invoke(dynamicWorkflow, new Dictionary<string, object> { { "Text", "Hello World!" } });  
                Console.ReadLine();  
    ```  
  
6. <span data-ttu-id="5f9f8-124">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5f9f8-124">Execute the application.</span></span> <span data-ttu-id="5f9f8-125">Okno konzoly s textem "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="5f9f8-125">A console window with the text "Hello World!"</span></span> <span data-ttu-id="5f9f8-126">uvádí.</span><span class="sxs-lookup"><span data-stu-id="5f9f8-126">displays.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a><span data-ttu-id="5f9f8-127">Vytvoření aktivity za běhu pomocí XAML</span><span class="sxs-lookup"><span data-stu-id="5f9f8-127">To create an activity at runtime using XAML</span></span>  
  
1. <span data-ttu-id="5f9f8-128">Otevřete Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="5f9f8-128">Open Visual Studio 2010.</span></span>  
  
2. <span data-ttu-id="5f9f8-129">Vyberte **soubor**, **Nový**, **projekt**.</span><span class="sxs-lookup"><span data-stu-id="5f9f8-129">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="5f9f8-130">V okně **typy projektů** vyberte **pracovní postup 4,0** v jazyce **Visual C#** a vyberte uzel **v2010** .</span><span class="sxs-lookup"><span data-stu-id="5f9f8-130">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="5f9f8-131">V okně **šablony** vyberte **Konzolová aplikace pracovního postupu** .</span><span class="sxs-lookup"><span data-stu-id="5f9f8-131">Select  **Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="5f9f8-132">Pojmenujte nový projekt DynamicActivitySample.</span><span class="sxs-lookup"><span data-stu-id="5f9f8-132">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="5f9f8-133">Otevřete Workflow1. XAML v projektu HelloActivity.</span><span class="sxs-lookup"><span data-stu-id="5f9f8-133">Open Workflow1.xaml in the HelloActivity project.</span></span> <span data-ttu-id="5f9f8-134">Klikněte na možnost **argumenty** v dolní části návrháře.</span><span class="sxs-lookup"><span data-stu-id="5f9f8-134">Click the **Arguments** option at the bottom of the designer.</span></span> <span data-ttu-id="5f9f8-135">Vytvořte nový `In` argument nazvaný `TextToWrite` typu `String` .</span><span class="sxs-lookup"><span data-stu-id="5f9f8-135">Create a new `In` argument called `TextToWrite` of type `String`.</span></span>  
  
4. <span data-ttu-id="5f9f8-136">Přetáhněte aktivitu **WriteLine** z oddílu **primitivních** prvků sady nástrojů na plochu návrháře.</span><span class="sxs-lookup"><span data-stu-id="5f9f8-136">Drag a **WriteLine** activity from the **Primitives** section of the toolbox onto the designer surface.</span></span> <span data-ttu-id="5f9f8-137">Přiřaďte hodnotu `TextToWrite` k vlastnosti **text** aktivity.</span><span class="sxs-lookup"><span data-stu-id="5f9f8-137">Assign the value `TextToWrite` to the **Text** property of the activity.</span></span>  
  
5. <span data-ttu-id="5f9f8-138">Otevřete Program.cs.</span><span class="sxs-lookup"><span data-stu-id="5f9f8-138">Open Program.cs.</span></span> <span data-ttu-id="5f9f8-139">Do horní části souboru přidejte následující direktivu.</span><span class="sxs-lookup"><span data-stu-id="5f9f8-139">Add the following directive to the top of the file.</span></span>  
  
    ```csharp  
    using System.Activities.XamlIntegration;  
    ```  
  
6. <span data-ttu-id="5f9f8-140">Obsah metody `Main` nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="5f9f8-140">Replace the contents of the `Main` method with the following code.</span></span>  
  
    ```csharp  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. <span data-ttu-id="5f9f8-141">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5f9f8-141">Execute the application.</span></span> <span data-ttu-id="5f9f8-142">Okno konzoly s textem "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="5f9f8-142">A console window with the text "Hello World!"</span></span> <span data-ttu-id="5f9f8-143">uvedeny.</span><span class="sxs-lookup"><span data-stu-id="5f9f8-143">appears.</span></span>  
  
8. <span data-ttu-id="5f9f8-144">Klikněte pravým tlačítkem na soubor Workflow1. XAML v **Průzkumník řešení** a vyberte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="5f9f8-144">Right-click the Workflow1.xaml file in the **Solution Explorer** and select **View Code**.</span></span> <span data-ttu-id="5f9f8-145">Všimněte si, že třída Activity je vytvořena s `x:Class` a vlastnost je vytvořena pomocí `x:Property` .</span><span class="sxs-lookup"><span data-stu-id="5f9f8-145">Note that the activity class is created with `x:Class` and the property is created with `x:Property`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f9f8-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="5f9f8-146">See also</span></span>

- [<span data-ttu-id="5f9f8-147">Vytváření pracovních postupů, aktivit a výrazů pomocí imperativního kódu</span><span class="sxs-lookup"><span data-stu-id="5f9f8-147">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](authoring-workflows-activities-and-expressions-using-imperative-code.md)
