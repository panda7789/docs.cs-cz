---
title: Základní třída NativeActivity
ms.date: 03/30/2017
ms.assetid: 254a4c50-425b-426d-a32f-0f7234925bac
ms.openlocfilehash: 604535e39937a75c6d268cf1abbc90dbcd506a16
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989549"
---
# <a name="nativeactivity-base-class"></a><span data-ttu-id="e5719-102">Základní třída NativeActivity</span><span class="sxs-lookup"><span data-stu-id="e5719-102">NativeActivity Base Class</span></span>

<span data-ttu-id="e5719-103"><xref:System.Activities.NativeActivity>je abstraktní třída s chráněným konstruktorem.</span><span class="sxs-lookup"><span data-stu-id="e5719-103"><xref:System.Activities.NativeActivity> is an abstract class with a protected constructor.</span></span> <span data-ttu-id="e5719-104">Podobně <xref:System.Activities.CodeActivity>jako <xref:System.Activities.NativeActivity> , se používá pro psaní <xref:System.Activities.NativeActivity.Execute%2A> imperativního chování implementací metody.</span><span class="sxs-lookup"><span data-stu-id="e5719-104">Like <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> is used for writing imperative behavior by implementing an <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span> <span data-ttu-id="e5719-105">Na rozdíl <xref:System.Activities.CodeActivity>od <xref:System.Activities.NativeActivity> , má přístup ke všem vystaveným funkcím modulu runtime pracovního postupu prostřednictvím <xref:System.Activities.NativeActivityContext> objektu předaného <xref:System.Activities.NativeActivity.Execute%2A> metodě.</span><span class="sxs-lookup"><span data-stu-id="e5719-105">Unlike <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> has access to all of the exposed features of the workflow runtime through the <xref:System.Activities.NativeActivityContext> object passed to the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>

## <a name="using-nativeactivitycontext"></a><span data-ttu-id="e5719-106">Použití NativeActivityContext</span><span class="sxs-lookup"><span data-stu-id="e5719-106">Using NativeActivityContext</span></span>
 <span data-ttu-id="e5719-107">K funkcím modulu runtime pracovního postupu lze v rámci <xref:System.Activities.NativeActivity.Execute%2A> metody přistupovat pomocí členů `context` parametru typu <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="e5719-107">Features of the workflow runtime can be accessed from within the <xref:System.Activities.NativeActivity.Execute%2A> method by using members of the `context` parameter, of type <xref:System.Activities.NativeActivityContext>.</span></span> <span data-ttu-id="e5719-108">K dispozici <xref:System.Activities.NativeActivityContext> jsou tyto funkce:</span><span class="sxs-lookup"><span data-stu-id="e5719-108">The features available through <xref:System.Activities.NativeActivityContext> include the following:</span></span>

- <span data-ttu-id="e5719-109">Získání a nastavení argumentů a proměnných.</span><span class="sxs-lookup"><span data-stu-id="e5719-109">Getting and setting of arguments and variables.</span></span>

- <span data-ttu-id="e5719-110">Plánování podřízených aktivit pomocí<xref:System.Activities.NativeActivityContext.ScheduleActivity%2A></span><span class="sxs-lookup"><span data-stu-id="e5719-110">Scheduling child activities with <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A></span></span>

- <span data-ttu-id="e5719-111">Přerušení provádění aktivity pomocí <xref:System.Activities.NativeActivityContext.Abort%2A>.</span><span class="sxs-lookup"><span data-stu-id="e5719-111">Aborting activity execution using <xref:System.Activities.NativeActivityContext.Abort%2A>.</span></span>

- <span data-ttu-id="e5719-112">Zrušení podřízeného spuštění pomocí <xref:System.Activities.NativeActivityContext.CancelChild%2A> a <xref:System.Activities.NativeActivityContext.CancelChildren%2A>.</span><span class="sxs-lookup"><span data-stu-id="e5719-112">Canceling child execution using <xref:System.Activities.NativeActivityContext.CancelChild%2A> and <xref:System.Activities.NativeActivityContext.CancelChildren%2A>.</span></span>

- <span data-ttu-id="e5719-113">Přístup k záložekm aktivit pomocí takových <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>metod <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>jako, <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>a.</span><span class="sxs-lookup"><span data-stu-id="e5719-113">Access to activity bookmarks using such methods as <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>, and <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>.</span></span>

- <span data-ttu-id="e5719-114">Vlastní funkce sledování pomocí <xref:System.Activities.CodeActivityContext.Track%2A>.</span><span class="sxs-lookup"><span data-stu-id="e5719-114">Custom tracking features using <xref:System.Activities.CodeActivityContext.Track%2A>.</span></span>

- <span data-ttu-id="e5719-115">Přístup k vlastnostem spuštění aktivity a k vlastnostem hodnoty <xref:System.Activities.CodeActivityContext.GetProperty%2A> pomocí <xref:System.Activities.NativeActivityContext.GetValue%2A>a.</span><span class="sxs-lookup"><span data-stu-id="e5719-115">Access to the activity’s execution properties and value properties using <xref:System.Activities.CodeActivityContext.GetProperty%2A> and <xref:System.Activities.NativeActivityContext.GetValue%2A>.</span></span>

- <span data-ttu-id="e5719-116">Plánování akcí a funkcí aktivity pomocí <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> a <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.</span><span class="sxs-lookup"><span data-stu-id="e5719-116">Scheduling activity actions and functions using <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> and <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.</span></span>

### <a name="to-create-a-custom-activity-that-inherits-from-nativeactivity"></a><span data-ttu-id="e5719-117">Vytvoření vlastní aktivity, která dědí z NativeActivity</span><span class="sxs-lookup"><span data-stu-id="e5719-117">To create a custom activity that inherits from NativeActivity</span></span>

1. <span data-ttu-id="e5719-118">OpenVisual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="e5719-118">OpenVisual Studio 2010.</span></span>

2. <span data-ttu-id="e5719-119">Vyberte **soubor**, **Nový**a pak **projekt**.</span><span class="sxs-lookup"><span data-stu-id="e5719-119">Select **File**, **New**, and then **Project**.</span></span> <span data-ttu-id="e5719-120">V okně **typy projektů** vyberte **pracovní postup 4,0** v nabídce  **C# vizuál** a vyberte uzel **v2010** .</span><span class="sxs-lookup"><span data-stu-id="e5719-120">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="e5719-121">V okně **šablony** vyberte **Knihovna aktivit** .</span><span class="sxs-lookup"><span data-stu-id="e5719-121">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="e5719-122">Pojmenujte nový projekt HelloActivity.</span><span class="sxs-lookup"><span data-stu-id="e5719-122">Name the new project HelloActivity.</span></span>

3. <span data-ttu-id="e5719-123">Klikněte pravým tlačítkem na Activity1. XAML v projektu HelloActivity a vyberte **Odstranit**.</span><span class="sxs-lookup"><span data-stu-id="e5719-123">Right-click Activity1.xaml in the HelloActivity project and select **Delete**.</span></span>

4. <span data-ttu-id="e5719-124">Klikněte pravým tlačítkem myši na projekt HelloActivity a vyberte možnost **Přidat**a **Třída**.</span><span class="sxs-lookup"><span data-stu-id="e5719-124">Right-click the HelloActivity project and select **Add**, and then **Class**.</span></span> <span data-ttu-id="e5719-125">Pojmenujte novou třídu HelloActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="e5719-125">Name the new class HelloActivity.cs.</span></span>

5. <span data-ttu-id="e5719-126">Do souboru HelloActivity.cs přidejte následující `using` direktivy.</span><span class="sxs-lookup"><span data-stu-id="e5719-126">In the HelloActivity.cs file, add the following `using` directives.</span></span>

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6. <span data-ttu-id="e5719-127">Nastavit novou třídu jako dědění <xref:System.Activities.NativeActivity> přidáním základní třídy do deklarace třídy.</span><span class="sxs-lookup"><span data-stu-id="e5719-127">Make the new class inherit from <xref:System.Activities.NativeActivity> by adding a base class to the class declaration.</span></span>

    ```csharp
    class HelloActivity : NativeActivity
    ```

7. <span data-ttu-id="e5719-128">Přidejte do třídy <xref:System.Activities.NativeActivity.Execute%2A> funkce přidáním metody.</span><span class="sxs-lookup"><span data-stu-id="e5719-128">Add functionality to the class by adding an <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>

    ```csharp
    protected override void Execute(NativeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8. <span data-ttu-id="e5719-129">Přepište <xref:System.Activities.NativeActivity.CacheMetadata%2A> metodu a zavolejte příslušnou metodu Add, aby modul runtime pracovního postupu mohl získat informace o proměnných, argumentech, podřízených a delegátech vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="e5719-129">Override the <xref:System.Activities.NativeActivity.CacheMetadata%2A> method and call the appropriate Add method to let the workflow runtime know about the custom activity’s variables, arguments, children, and delegates.</span></span> <span data-ttu-id="e5719-130">Další informace najdete v tématu <xref:System.Activities.NativeActivityMetadata> třída.</span><span class="sxs-lookup"><span data-stu-id="e5719-130">For more information see the <xref:System.Activities.NativeActivityMetadata> class.</span></span>

9. <span data-ttu-id="e5719-131">K naplánování záložky použijte objekt.<xref:System.Activities.NativeActivityContext></span><span class="sxs-lookup"><span data-stu-id="e5719-131">Use the <xref:System.Activities.NativeActivityContext> object to schedule a bookmark.</span></span> <span data-ttu-id="e5719-132">Podrobnosti <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> o tom, jak vytvořit, naplánovat a obnovit záložku, najdete v tématu.</span><span class="sxs-lookup"><span data-stu-id="e5719-132">See <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> for details on how to create, schedule, and resume a bookmark.</span></span>

    ```csharp
    protected override void Execute(NativeActivityContext context)
        {
            // Create a Bookmark and wait for it to be resumed.
            context.CreateBookmark(BookmarkName.Get(context),
                new BookmarkCallback(OnResumeBookmark));
        }
    ```
