---
title: Vytvoření aktivity za běhu pomocí dynamické aktivity
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: 871108fd09e9127b3f9e06174f05a47c7fd7682c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182983"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a><span data-ttu-id="73783-102">Vytvoření aktivity za běhu pomocí dynamické aktivity</span><span class="sxs-lookup"><span data-stu-id="73783-102">Creating an Activity at Runtime with DynamicActivity</span></span>
<span data-ttu-id="73783-103"><xref:System.Activities.DynamicActivity>je betonová, zapečetěná třída s veřejným konstruktérem.</span><span class="sxs-lookup"><span data-stu-id="73783-103"><xref:System.Activities.DynamicActivity> is a concrete, sealed class with a public constructor.</span></span> <span data-ttu-id="73783-104"><xref:System.Activities.DynamicActivity>lze použít k sestavení funkce aktivity za běhu pomocí aktivity DOM.</span><span class="sxs-lookup"><span data-stu-id="73783-104"><xref:System.Activities.DynamicActivity> can be used to assemble activity functionality at runtime using an activity DOM.</span></span>  
  
## <a name="dynamicactivity-features"></a><span data-ttu-id="73783-105">Funkce dynamice aktivity</span><span class="sxs-lookup"><span data-stu-id="73783-105">DynamicActivity Features</span></span>  
 <span data-ttu-id="73783-106"><xref:System.Activities.DynamicActivity>má přístup k vlastnostem spuštění, argumentům a proměnným, ale nemá přístup ke službám za běhu, jako je plánování podřízených aktivit nebo sledování.</span><span class="sxs-lookup"><span data-stu-id="73783-106"><xref:System.Activities.DynamicActivity> has access to execution properties, arguments and variables, but no access to run-time services such as scheduling child activities or tracking.</span></span>  
  
 <span data-ttu-id="73783-107">Vlastnosti nejvyšší úrovně lze <xref:System.Activities.Argument> nastavit pomocí objektů pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="73783-107">Top-level properties can be set using workflow <xref:System.Activities.Argument> objects.</span></span> <span data-ttu-id="73783-108">V imperativním kódu jsou tyto argumenty vytvořeny pomocí vlastností CLR u nového typu.</span><span class="sxs-lookup"><span data-stu-id="73783-108">In imperative code, these arguments are created using CLR properties on a new type.</span></span> <span data-ttu-id="73783-109">V XAML jsou deklarovány pomocí `x:Class` a `x:Member` značky.</span><span class="sxs-lookup"><span data-stu-id="73783-109">In XAML, they are declared using `x:Class` and `x:Member` tags.</span></span>  
  
 <span data-ttu-id="73783-110">Aktivity vytvořené <xref:System.Activities.DynamicActivity> pomocí rozhraní <xref:System.ComponentModel.ICustomTypeDescriptor>s návrhářem pomocí .</span><span class="sxs-lookup"><span data-stu-id="73783-110">Activities constructed using <xref:System.Activities.DynamicActivity> interface with the designer using <xref:System.ComponentModel.ICustomTypeDescriptor>.</span></span> <span data-ttu-id="73783-111">Aktivity vytvořené v návrháři lze <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>načíst dynamicky pomocí , jak je znázorněno v následujícím postupu.</span><span class="sxs-lookup"><span data-stu-id="73783-111">Activities created in the designer can be loaded dynamically using <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, as demonstrated in the following procedure.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a><span data-ttu-id="73783-112">Vytvoření aktivity za běhu pomocí imperativního kódu</span><span class="sxs-lookup"><span data-stu-id="73783-112">To create an activity at runtime using imperative code</span></span>  
  
1. <span data-ttu-id="73783-113">OpenVisual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="73783-113">OpenVisual Studio 2010.</span></span>  
  
2. <span data-ttu-id="73783-114">Vyberte **soubor**, **Nový**, **Projekt**.</span><span class="sxs-lookup"><span data-stu-id="73783-114">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="73783-115">Vyberte **pracovní postup 4.0** v části **Visual C#** v okně **Typy projektů** a vyberte uzel **v2010.**</span><span class="sxs-lookup"><span data-stu-id="73783-115">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="73783-116">V okně Šablony vyberte **Sekvenční konzolová aplikace** **pracovního postupu.**</span><span class="sxs-lookup"><span data-stu-id="73783-116">Select **Sequential Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="73783-117">Pojmenujte nový projekt DynamicActivitySample.</span><span class="sxs-lookup"><span data-stu-id="73783-117">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="73783-118">Klepněte pravým tlačítkem myši na soubor Workflow1.xaml v projektu HelloActivity a vyberte **příkaz Odstranit**.</span><span class="sxs-lookup"><span data-stu-id="73783-118">Right-click Workflow1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4. <span data-ttu-id="73783-119">Otevřete Program.cs.</span><span class="sxs-lookup"><span data-stu-id="73783-119">Open Program.cs.</span></span> <span data-ttu-id="73783-120">Přidejte následující direktivu do horní části souboru.</span><span class="sxs-lookup"><span data-stu-id="73783-120">Add the following directive to the top of the file.</span></span>  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
5. <span data-ttu-id="73783-121">Nahraďte obsah `Main` metody následujícím kódem, <xref:System.Activities.Statements.Sequence> který vytvoří aktivitu, která obsahuje <xref:System.Activities.Statements.WriteLine> <xref:System.Activities.DynamicActivity.Implementation%2A> jednu aktivitu, a přiřadí ji vlastnosti nové dynamické aktivity.</span><span class="sxs-lookup"><span data-stu-id="73783-121">Replace the contents of the `Main` method with the following code, which creates a <xref:System.Activities.Statements.Sequence> activity that contains a single <xref:System.Activities.Statements.WriteLine> activity and assigns it to the <xref:System.Activities.DynamicActivity.Implementation%2A> property of a new dynamic activity.</span></span>  
  
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
  
6. <span data-ttu-id="73783-122">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="73783-122">Execute the application.</span></span> <span data-ttu-id="73783-123">Okno konzoly s textem "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="73783-123">A console window with the text "Hello World!"</span></span> <span data-ttu-id="73783-124">Zobrazí.</span><span class="sxs-lookup"><span data-stu-id="73783-124">displays.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a><span data-ttu-id="73783-125">Vytvoření aktivity za běhu pomocí xaml</span><span class="sxs-lookup"><span data-stu-id="73783-125">To create an activity at runtime using XAML</span></span>  
  
1. <span data-ttu-id="73783-126">Otevřete Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="73783-126">Open Visual Studio 2010.</span></span>  
  
2. <span data-ttu-id="73783-127">Vyberte **soubor**, **Nový**, **Projekt**.</span><span class="sxs-lookup"><span data-stu-id="73783-127">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="73783-128">Vyberte **pracovní postup 4.0** v části **Visual C#** v okně **Typy projektů** a vyberte uzel **v2010.**</span><span class="sxs-lookup"><span data-stu-id="73783-128">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="73783-129">V okně **Šablony** vyberte **Konzolová aplikace pracovního postupu.**</span><span class="sxs-lookup"><span data-stu-id="73783-129">Select  **Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="73783-130">Pojmenujte nový projekt DynamicActivitySample.</span><span class="sxs-lookup"><span data-stu-id="73783-130">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="73783-131">Otevřete soubor Workflow1.xaml v projektu HelloActivity.</span><span class="sxs-lookup"><span data-stu-id="73783-131">Open Workflow1.xaml in the HelloActivity project.</span></span> <span data-ttu-id="73783-132">Klikněte na možnost **Argumenty** v dolní části návrháře.</span><span class="sxs-lookup"><span data-stu-id="73783-132">Click the **Arguments** option at the bottom of the designer.</span></span> <span data-ttu-id="73783-133">Vytvořte `In` nový `TextToWrite` argument `String`nazvaný typu .</span><span class="sxs-lookup"><span data-stu-id="73783-133">Create a new `In` argument called `TextToWrite` of type `String`.</span></span>  
  
4. <span data-ttu-id="73783-134">Přetáhněte aktivitu **WriteLine** z části **Primitiv** v panelu nástrojů na povrch návrháře.</span><span class="sxs-lookup"><span data-stu-id="73783-134">Drag a **WriteLine** activity from the **Primitives** section of the toolbox onto the designer surface.</span></span> <span data-ttu-id="73783-135">Přiřaďte hodnotu `TextToWrite` vlastnosti **Text** aktivity.</span><span class="sxs-lookup"><span data-stu-id="73783-135">Assign the value `TextToWrite` to the **Text** property of the activity.</span></span>  
  
5. <span data-ttu-id="73783-136">Otevřete Program.cs.</span><span class="sxs-lookup"><span data-stu-id="73783-136">Open Program.cs.</span></span> <span data-ttu-id="73783-137">Přidejte následující direktivu do horní části souboru.</span><span class="sxs-lookup"><span data-stu-id="73783-137">Add the following directive to the top of the file.</span></span>  
  
    ```csharp  
    using System.Activities.XamlIntegration;  
    ```  
  
6. <span data-ttu-id="73783-138">Obsah metody `Main` nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="73783-138">Replace the contents of the `Main` method with the following code.</span></span>  
  
    ```csharp  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. <span data-ttu-id="73783-139">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="73783-139">Execute the application.</span></span> <span data-ttu-id="73783-140">Okno konzoly s textem "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="73783-140">A console window with the text "Hello World!"</span></span> <span data-ttu-id="73783-141">Zobrazí.</span><span class="sxs-lookup"><span data-stu-id="73783-141">appears.</span></span>  
  
8. <span data-ttu-id="73783-142">Klepněte pravým tlačítkem myši na soubor Workflow1.xaml v **Průzkumníku řešení** a vyberte **příkaz Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="73783-142">Right-click the Workflow1.xaml file in the **Solution Explorer** and select **View Code**.</span></span> <span data-ttu-id="73783-143">Všimněte si, že `x:Class` třída aktivity je `x:Property`vytvořena s a vlastnost je vytvořena pomocí .</span><span class="sxs-lookup"><span data-stu-id="73783-143">Note that the activity class is created with `x:Class` and the property is created with `x:Property`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73783-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="73783-144">See also</span></span>

- [<span data-ttu-id="73783-145">Vytváření pracovních postupů, aktivit a výrazů pomocí imperativního kódu</span><span class="sxs-lookup"><span data-stu-id="73783-145">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](authoring-workflows-activities-and-expressions-using-imperative-code.md)
