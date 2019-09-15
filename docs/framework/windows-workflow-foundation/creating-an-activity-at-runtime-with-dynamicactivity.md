---
title: Vytvoření aktivity za běhu pomocí DynamicActivity
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: de67fdd71f28bc0f4b16017d253682ca2615f854
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989742"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a><span data-ttu-id="8c5da-102">Vytvoření aktivity za běhu pomocí DynamicActivity</span><span class="sxs-lookup"><span data-stu-id="8c5da-102">Creating an Activity at Runtime with DynamicActivity</span></span>
<span data-ttu-id="8c5da-103"><xref:System.Activities.DynamicActivity>je konkrétní zapečetěná třída s veřejným konstruktorem.</span><span class="sxs-lookup"><span data-stu-id="8c5da-103"><xref:System.Activities.DynamicActivity> is a concrete, sealed class with a public constructor.</span></span> <span data-ttu-id="8c5da-104"><xref:System.Activities.DynamicActivity>dá se použít k sestavování funkčnosti aktivity za běhu pomocí modelu DOM aktivity.</span><span class="sxs-lookup"><span data-stu-id="8c5da-104"><xref:System.Activities.DynamicActivity> can be used to assemble activity functionality at runtime using an activity DOM.</span></span>  
  
## <a name="dynamicactivity-features"></a><span data-ttu-id="8c5da-105">Funkce DynamicActivity</span><span class="sxs-lookup"><span data-stu-id="8c5da-105">DynamicActivity Features</span></span>  
 <span data-ttu-id="8c5da-106"><xref:System.Activities.DynamicActivity>má přístup k vlastnostem spuštění, argumentům a proměnným, ale nemá přístup ke službám runtime, jako je plánování podřízených aktivit nebo sledování.</span><span class="sxs-lookup"><span data-stu-id="8c5da-106"><xref:System.Activities.DynamicActivity> has access to execution properties, arguments and variables, but no access to run-time services such as scheduling child activities or tracking.</span></span>  
  
 <span data-ttu-id="8c5da-107">Vlastnosti nejvyšší úrovně lze nastavit pomocí objektů pracovního postupu <xref:System.Activities.Argument> .</span><span class="sxs-lookup"><span data-stu-id="8c5da-107">Top-level properties can be set using workflow <xref:System.Activities.Argument> objects.</span></span> <span data-ttu-id="8c5da-108">V imperativním kódu jsou tyto argumenty vytvořeny pomocí vlastností CLR pro nový typ.</span><span class="sxs-lookup"><span data-stu-id="8c5da-108">In imperative code, these arguments are created using CLR properties on a new type.</span></span> <span data-ttu-id="8c5da-109">V jazyce XAML jsou deklarovány pomocí `x:Class` značek `x:Member` a.</span><span class="sxs-lookup"><span data-stu-id="8c5da-109">In XAML, they are declared using `x:Class` and `x:Member` tags.</span></span>  
  
 <span data-ttu-id="8c5da-110">Aktivity vytvořené pomocí <xref:System.Activities.DynamicActivity> rozhraní s návrhářem pomocí <xref:System.ComponentModel.ICustomTypeDescriptor>.</span><span class="sxs-lookup"><span data-stu-id="8c5da-110">Activities constructed using <xref:System.Activities.DynamicActivity> interface with the designer using <xref:System.ComponentModel.ICustomTypeDescriptor>.</span></span> <span data-ttu-id="8c5da-111">Aktivity vytvořené v Návrháři lze dynamicky načíst pomocí <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, jak je znázorněno v následujícím postupu.</span><span class="sxs-lookup"><span data-stu-id="8c5da-111">Activities created in the designer can be loaded dynamically using <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, as demonstrated in the following procedure.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a><span data-ttu-id="8c5da-112">Vytvoření aktivity za běhu pomocí imperativního kódu</span><span class="sxs-lookup"><span data-stu-id="8c5da-112">To create an activity at runtime using imperative code</span></span>  
  
1. <span data-ttu-id="8c5da-113">OpenVisual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="8c5da-113">OpenVisual Studio 2010.</span></span>  
  
2. <span data-ttu-id="8c5da-114">Vyberte **soubor**, **Nový**, **projekt**.</span><span class="sxs-lookup"><span data-stu-id="8c5da-114">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="8c5da-115">V okně **typy projektů** vyberte **pracovní postup 4,0** v nabídce  **C# vizuál** a vyberte uzel **v2010** .</span><span class="sxs-lookup"><span data-stu-id="8c5da-115">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="8c5da-116">V okně **šablony** vyberte **Konzolová aplikace sekvenčního pracovního postupu** .</span><span class="sxs-lookup"><span data-stu-id="8c5da-116">Select **Sequential Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="8c5da-117">Pojmenujte nový projekt DynamicActivitySample.</span><span class="sxs-lookup"><span data-stu-id="8c5da-117">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="8c5da-118">Klikněte pravým tlačítkem na Workflow1. XAML v projektu HelloActivity a vyberte **Odstranit**.</span><span class="sxs-lookup"><span data-stu-id="8c5da-118">Right-click Workflow1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4. <span data-ttu-id="8c5da-119">Otevřete Program.cs.</span><span class="sxs-lookup"><span data-stu-id="8c5da-119">Open Program.cs.</span></span> <span data-ttu-id="8c5da-120">Do horní části souboru přidejte následující direktivu.</span><span class="sxs-lookup"><span data-stu-id="8c5da-120">Add the following directive to the top of the file.</span></span>  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
5. <span data-ttu-id="8c5da-121">Nahraďte obsah `Main` metody následujícím kódem, který <xref:System.Activities.Statements.Sequence> vytvoří aktivitu, která obsahuje jednu <xref:System.Activities.Statements.WriteLine> aktivitu a přiřadí ji k <xref:System.Activities.DynamicActivity.Implementation%2A> vlastnosti nové dynamické aktivity.</span><span class="sxs-lookup"><span data-stu-id="8c5da-121">Replace the contents of the `Main` method with the following code, which creates a <xref:System.Activities.Statements.Sequence> activity that contains a single <xref:System.Activities.Statements.WriteLine> activity and assigns it to the <xref:System.Activities.DynamicActivity.Implementation%2A> property of a new dynamic activity.</span></span>  
  
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
  
6. <span data-ttu-id="8c5da-122">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8c5da-122">Execute the application.</span></span> <span data-ttu-id="8c5da-123">Okno konzoly s textem "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="8c5da-123">A console window with the text "Hello World!"</span></span> <span data-ttu-id="8c5da-124">uvádí.</span><span class="sxs-lookup"><span data-stu-id="8c5da-124">displays.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a><span data-ttu-id="8c5da-125">Vytvoření aktivity za běhu pomocí XAML</span><span class="sxs-lookup"><span data-stu-id="8c5da-125">To create an activity at runtime using XAML</span></span>  
  
1. <span data-ttu-id="8c5da-126">Otevřete Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="8c5da-126">Open Visual Studio 2010.</span></span>  
  
2. <span data-ttu-id="8c5da-127">Vyberte **soubor**, **Nový**, **projekt**.</span><span class="sxs-lookup"><span data-stu-id="8c5da-127">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="8c5da-128">V okně **typy projektů** vyberte **pracovní postup 4,0** v nabídce  **C# vizuál** a vyberte uzel **v2010** .</span><span class="sxs-lookup"><span data-stu-id="8c5da-128">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="8c5da-129">V okně **šablony** vyberte **Konzolová aplikace pracovního postupu** .</span><span class="sxs-lookup"><span data-stu-id="8c5da-129">Select  **Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="8c5da-130">Pojmenujte nový projekt DynamicActivitySample.</span><span class="sxs-lookup"><span data-stu-id="8c5da-130">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="8c5da-131">Otevřete Workflow1. XAML v projektu HelloActivity.</span><span class="sxs-lookup"><span data-stu-id="8c5da-131">Open Workflow1.xaml in the HelloActivity project.</span></span> <span data-ttu-id="8c5da-132">Klikněte na možnost **argumenty** v dolní části návrháře.</span><span class="sxs-lookup"><span data-stu-id="8c5da-132">Click the **Arguments** option at the bottom of the designer.</span></span> <span data-ttu-id="8c5da-133">Vytvořte nový `In` argument nazvaný `TextToWrite` typu `String`.</span><span class="sxs-lookup"><span data-stu-id="8c5da-133">Create a new `In` argument called `TextToWrite` of type `String`.</span></span>  
  
4. <span data-ttu-id="8c5da-134">Přetáhněte aktivitu **WriteLine** z oddílu **primitivních** prvků sady nástrojů na plochu návrháře.</span><span class="sxs-lookup"><span data-stu-id="8c5da-134">Drag a **WriteLine** activity from the **Primitives** section of the toolbox onto the designer surface.</span></span> <span data-ttu-id="8c5da-135">Přiřaďte hodnotu `TextToWrite` k vlastnosti **text** aktivity.</span><span class="sxs-lookup"><span data-stu-id="8c5da-135">Assign the value `TextToWrite` to the **Text** property of the activity.</span></span>  
  
5. <span data-ttu-id="8c5da-136">Otevřete Program.cs.</span><span class="sxs-lookup"><span data-stu-id="8c5da-136">Open Program.cs.</span></span> <span data-ttu-id="8c5da-137">Do horní části souboru přidejte následující direktivu.</span><span class="sxs-lookup"><span data-stu-id="8c5da-137">Add the following directive to the top of the file.</span></span>  
  
    ```csharp  
    using System.Activities.XamlIntegration;  
    ```  
  
6. <span data-ttu-id="8c5da-138">Obsah `Main` metody nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="8c5da-138">Replace the contents of the `Main` method with the following code.</span></span>  
  
    ```csharp  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. <span data-ttu-id="8c5da-139">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8c5da-139">Execute the application.</span></span> <span data-ttu-id="8c5da-140">Okno konzoly s textem "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="8c5da-140">A console window with the text "Hello World!"</span></span> <span data-ttu-id="8c5da-141">uvedeny.</span><span class="sxs-lookup"><span data-stu-id="8c5da-141">appears.</span></span>  
  
8. <span data-ttu-id="8c5da-142">Klikněte pravým tlačítkem na soubor Workflow1. XAML v **Průzkumník řešení** a vyberte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="8c5da-142">Right-click the Workflow1.xaml file in the **Solution Explorer** and select **View Code**.</span></span> <span data-ttu-id="8c5da-143">Všimněte si, že třída Activity je vytvořena `x:Class` s a vlastnost je vytvořena pomocí `x:Property`.</span><span class="sxs-lookup"><span data-stu-id="8c5da-143">Note that the activity class is created with `x:Class` and the property is created with `x:Property`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c5da-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c5da-144">See also</span></span>

- [<span data-ttu-id="8c5da-145">Vytváření pracovních postupů, aktivit a výrazů pomocí imperativního kódu</span><span class="sxs-lookup"><span data-stu-id="8c5da-145">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](authoring-workflows-activities-and-expressions-using-imperative-code.md)
