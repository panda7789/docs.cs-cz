---
title: Vytvoření aktivity za běhu s DynamicActivity
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: 0450a56059083f355f3fd71d95c83bf8dd1cf0e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515171"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a><span data-ttu-id="981f3-102">Vytvoření aktivity za běhu s DynamicActivity</span><span class="sxs-lookup"><span data-stu-id="981f3-102">Creating an Activity at Runtime with DynamicActivity</span></span>
<span data-ttu-id="981f3-103"><xref:System.Activities.DynamicActivity> je třída konkrétní, zapečetěné s veřejný konstruktor.</span><span class="sxs-lookup"><span data-stu-id="981f3-103"><xref:System.Activities.DynamicActivity> is a concrete, sealed class with a public constructor.</span></span> <span data-ttu-id="981f3-104"><xref:System.Activities.DynamicActivity> slouží ke kompilaci aktivita funkce za běhu pomocí aktivity modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="981f3-104"><xref:System.Activities.DynamicActivity> can be used to assemble activity functionality at runtime using an activity DOM.</span></span>  
  
## <a name="dynamicactivity-features"></a><span data-ttu-id="981f3-105">Funkce DynamicActivity</span><span class="sxs-lookup"><span data-stu-id="981f3-105">DynamicActivity Features</span></span>  
 <span data-ttu-id="981f3-106"><xref:System.Activities.DynamicActivity> má přístup k vlastnosti provádění, argumentů a proměnné, ale žádný přístup k spuštění služby, jako je například plánování podřízené aktivity nebo sledování.</span><span class="sxs-lookup"><span data-stu-id="981f3-106"><xref:System.Activities.DynamicActivity> has access to execution properties, arguments and variables, but no access to run-time services such as scheduling child activities or tracking.</span></span>  
  
 <span data-ttu-id="981f3-107">Nejvyšší úrovně vlastnosti se dá nastavit pomocí pracovního postupu <xref:System.Activities.Argument> objekty.</span><span class="sxs-lookup"><span data-stu-id="981f3-107">Top-level properties can be set using workflow <xref:System.Activities.Argument> objects.</span></span> <span data-ttu-id="981f3-108">Imperativní kódu se tyto argumenty vytvoří pomocí vlastnosti CLR na nový typ.</span><span class="sxs-lookup"><span data-stu-id="981f3-108">In imperative code, these arguments are created using CLR properties on a new type.</span></span> <span data-ttu-id="981f3-109">V jazyce XAML, jsou deklarovány pomocí `x:Class` a `x:Member` značky.</span><span class="sxs-lookup"><span data-stu-id="981f3-109">In XAML, they are declared using `x:Class` and `x:Member` tags.</span></span>  
  
 <span data-ttu-id="981f3-110">Aktivity, které jsou vytvářeny pomocí <xref:System.Activities.DynamicActivity> rozhraní s použitím návrháře <xref:System.ComponentModel.ICustomTypeDescriptor>.</span><span class="sxs-lookup"><span data-stu-id="981f3-110">Activities constructed using <xref:System.Activities.DynamicActivity> interface with the designer using <xref:System.ComponentModel.ICustomTypeDescriptor>.</span></span> <span data-ttu-id="981f3-111">Aktivity vytvořené v Návrháři můžete načíst pomocí dynamicky <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, jak je znázorněno v následujícím postupu.</span><span class="sxs-lookup"><span data-stu-id="981f3-111">Activities created in the designer can be loaded dynamically using <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, as demonstrated in the following procedure.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a><span data-ttu-id="981f3-112">Chcete-li vytvořit aktivitu v době běhu pomocí imperativní kódu</span><span class="sxs-lookup"><span data-stu-id="981f3-112">To create an activity at runtime using imperative code</span></span>  
  
1.  <span data-ttu-id="981f3-113">Otevřete[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="981f3-113">Open[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="981f3-114">Vyberte **soubor**, **nové**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="981f3-114">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="981f3-115">Vyberte **Workflow 4.0** pod **Visual C#** v **typy projektů** a vyberte **v2010** uzlu.</span><span class="sxs-lookup"><span data-stu-id="981f3-115">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="981f3-116">Vyberte **sekvenčního pracovního postupu konzolové aplikace** v **šablony** okno.</span><span class="sxs-lookup"><span data-stu-id="981f3-116">Select **Sequential Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="981f3-117">Název nového projektu DynamicActivitySample.</span><span class="sxs-lookup"><span data-stu-id="981f3-117">Name the new project DynamicActivitySample.</span></span>  
  
3.  <span data-ttu-id="981f3-118">Klikněte pravým tlačítkem na Workflow1.xaml v HelloActivity projektu a vyberte **odstranit**.</span><span class="sxs-lookup"><span data-stu-id="981f3-118">Right-click Workflow1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4.  <span data-ttu-id="981f3-119">Otevření souboru Program.cs.</span><span class="sxs-lookup"><span data-stu-id="981f3-119">Open Program.cs.</span></span> <span data-ttu-id="981f3-120">Na začátek souboru přidejte následující direktivy.</span><span class="sxs-lookup"><span data-stu-id="981f3-120">Add the following directive to the top of the file.</span></span>  
  
    ```  
    using System.Collections.Generic;  
    ```  
  
5.  <span data-ttu-id="981f3-121">Nahraďte obsah `Main` metoda následující kód, který vytvoří <xref:System.Activities.Statements.Sequence> aktivity, která obsahuje jeden <xref:System.Activities.Statements.WriteLine> aktivity a přiřadí ji k <xref:System.Activities.DynamicActivity.Implementation%2A> vlastnost nové dynamické aktivity.</span><span class="sxs-lookup"><span data-stu-id="981f3-121">Replace the contents of the `Main` method with the following code, which creates a <xref:System.Activities.Statements.Sequence> activity that contains a single <xref:System.Activities.Statements.WriteLine> activity and assigns it to the <xref:System.Activities.DynamicActivity.Implementation%2A> property of a new dynamic activity.</span></span>  
  
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
  
6.  <span data-ttu-id="981f3-122">Spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="981f3-122">Execute the application.</span></span> <span data-ttu-id="981f3-123">Okno konzoly s textem "Hello, World!"</span><span class="sxs-lookup"><span data-stu-id="981f3-123">A console window with the text "Hello World!"</span></span> <span data-ttu-id="981f3-124">zobrazí.</span><span class="sxs-lookup"><span data-stu-id="981f3-124">displays.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a><span data-ttu-id="981f3-125">Chcete-li vytvořit aktivitu v době běhu pomocí jazyka XAML</span><span class="sxs-lookup"><span data-stu-id="981f3-125">To create an activity at runtime using XAML</span></span>  
  
1.  <span data-ttu-id="981f3-126">Otevřete [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="981f3-126">Open [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="981f3-127">Vyberte **soubor**, **nové**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="981f3-127">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="981f3-128">Vyberte **Workflow 4.0** pod **Visual C#** v **typy projektů** a vyberte **v2010** uzlu.</span><span class="sxs-lookup"><span data-stu-id="981f3-128">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="981f3-129">Vyberte **pracovního postupu konzolové aplikace** v **šablony** okno.</span><span class="sxs-lookup"><span data-stu-id="981f3-129">Select  **Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="981f3-130">Název nového projektu DynamicActivitySample.</span><span class="sxs-lookup"><span data-stu-id="981f3-130">Name the new project DynamicActivitySample.</span></span>  
  
3.  <span data-ttu-id="981f3-131">Otevřete v projektu HelloActivity Workflow1.xaml.</span><span class="sxs-lookup"><span data-stu-id="981f3-131">Open Workflow1.xaml in the HelloActivity project.</span></span> <span data-ttu-id="981f3-132">Klikněte **argumenty** možnost v dolní části návrháře.</span><span class="sxs-lookup"><span data-stu-id="981f3-132">Click the **Arguments** option at the bottom of the designer.</span></span> <span data-ttu-id="981f3-133">Vytvořte novou `In` argument názvem `TextToWrite` typu `String`.</span><span class="sxs-lookup"><span data-stu-id="981f3-133">Create a new `In` argument called `TextToWrite` of type `String`.</span></span>  
  
4.  <span data-ttu-id="981f3-134">Přetáhněte **WriteLine** aktivity z **primitiv** části panelu nástrojů na plochu návrháře.</span><span class="sxs-lookup"><span data-stu-id="981f3-134">Drag a **WriteLine** activity from the **Primitives** section of the toolbox onto the designer surface.</span></span> <span data-ttu-id="981f3-135">Přiřadí hodnotu `TextToWrite` k **Text** vlastnost aktivity.</span><span class="sxs-lookup"><span data-stu-id="981f3-135">Assign the value `TextToWrite` to the **Text** property of the activity.</span></span>  
  
5.  <span data-ttu-id="981f3-136">Otevření souboru Program.cs.</span><span class="sxs-lookup"><span data-stu-id="981f3-136">Open Program.cs.</span></span> <span data-ttu-id="981f3-137">Na začátek souboru přidejte následující direktivy.</span><span class="sxs-lookup"><span data-stu-id="981f3-137">Add the following directive to the top of the file.</span></span>  
  
    ```  
    using System.Activities.XamlIntegration;  
    ```  
  
6.  <span data-ttu-id="981f3-138">Nahraďte obsah `Main` metoda následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="981f3-138">Replace the contents of the `Main` method with the following code.</span></span>  
  
    ```  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7.  <span data-ttu-id="981f3-139">Spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="981f3-139">Execute the application.</span></span> <span data-ttu-id="981f3-140">Okno konzoly s textem "Hello, World!"</span><span class="sxs-lookup"><span data-stu-id="981f3-140">A console window with the text "Hello World!"</span></span> <span data-ttu-id="981f3-141">Zobrazí se.</span><span class="sxs-lookup"><span data-stu-id="981f3-141">appears.</span></span>  
  
8.  <span data-ttu-id="981f3-142">Klikněte pravým tlačítkem na soubor Workflow1.xaml v **Průzkumníku řešení** a vyberte **kód zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="981f3-142">Right-click the Workflow1.xaml file in the **Solution Explorer** and select **View Code**.</span></span> <span data-ttu-id="981f3-143">Všimněte si, že třídy aktivity je vytvořena s `x:Class` a vlastnost je vytvořena s `x:Property`.</span><span class="sxs-lookup"><span data-stu-id="981f3-143">Note that the activity class is created with `x:Class` and the property is created with `x:Property`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="981f3-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="981f3-144">See Also</span></span>  
 [<span data-ttu-id="981f3-145">Vytváření pracovních postupů, aktivit a výrazů pomocí imperativního kódu</span><span class="sxs-lookup"><span data-stu-id="981f3-145">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)  
 [<span data-ttu-id="981f3-146">Vytvoření dynamické aktivity</span><span class="sxs-lookup"><span data-stu-id="981f3-146">DynamicActivity Creation</span></span>](../../../docs/framework/windows-workflow-foundation/samples/dynamicactivity-creation.md)
