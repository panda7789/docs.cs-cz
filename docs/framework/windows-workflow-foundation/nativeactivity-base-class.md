---
title: Základní třída NativeActivity
ms.date: 03/30/2017
ms.assetid: 254a4c50-425b-426d-a32f-0f7234925bac
ms.openlocfilehash: d746bb92dab79e7e68075ad003c420e7e37ed683
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637504"
---
# <a name="nativeactivity-base-class"></a><span data-ttu-id="bb71c-102">Základní třída NativeActivity</span><span class="sxs-lookup"><span data-stu-id="bb71c-102">NativeActivity Base Class</span></span>

<span data-ttu-id="bb71c-103"><xref:System.Activities.NativeActivity> je abstraktní třída s konstruktorem chráněné.</span><span class="sxs-lookup"><span data-stu-id="bb71c-103"><xref:System.Activities.NativeActivity> is an abstract class with a protected constructor.</span></span> <span data-ttu-id="bb71c-104">Stejně jako <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> se používá k zápisu imperativní chování implementací <xref:System.Activities.NativeActivity.Execute%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="bb71c-104">Like <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> is used for writing imperative behavior by implementing an <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span> <span data-ttu-id="bb71c-105">Na rozdíl od <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> má přístup ke všem vystavené funkcím modulu runtime pracovního postupu pomocí <xref:System.Activities.NativeActivityContext> předán objekt <xref:System.Activities.NativeActivity.Execute%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="bb71c-105">Unlike <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> has access to all of the exposed features of the workflow runtime through the <xref:System.Activities.NativeActivityContext> object passed to the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>

## <a name="using-nativeactivitycontext"></a><span data-ttu-id="bb71c-106">Pomocí NativeActivityContext</span><span class="sxs-lookup"><span data-stu-id="bb71c-106">Using NativeActivityContext</span></span>
 <span data-ttu-id="bb71c-107">Funkce modulu runtime pracovního postupu je přístupný z v rámci <xref:System.Activities.NativeActivity.Execute%2A> metoda pomocí členy `context` parametr typu <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="bb71c-107">Features of the workflow runtime can be accessed from within the <xref:System.Activities.NativeActivity.Execute%2A> method by using members of the `context` parameter, of type <xref:System.Activities.NativeActivityContext>.</span></span> <span data-ttu-id="bb71c-108">Funkcí dostupných prostřednictvím <xref:System.Activities.NativeActivityContext> patří následující:</span><span class="sxs-lookup"><span data-stu-id="bb71c-108">The features available through <xref:System.Activities.NativeActivityContext> include the following:</span></span>

- <span data-ttu-id="bb71c-109">Získání a nastavení proměnných a argumentů příkazu.</span><span class="sxs-lookup"><span data-stu-id="bb71c-109">Getting and setting of arguments and variables.</span></span>

- <span data-ttu-id="bb71c-110">Plánování podřízené aktivity s <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A></span><span class="sxs-lookup"><span data-stu-id="bb71c-110">Scheduling child activities with <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A></span></span>

- <span data-ttu-id="bb71c-111">Přerušení aktivity spuštění pomocí <xref:System.Activities.NativeActivityContext.Abort%2A>.</span><span class="sxs-lookup"><span data-stu-id="bb71c-111">Aborting activity execution using <xref:System.Activities.NativeActivityContext.Abort%2A>.</span></span>

- <span data-ttu-id="bb71c-112">Zrušení podřízené spuštění pomocí <xref:System.Activities.NativeActivityContext.CancelChild%2A> a <xref:System.Activities.NativeActivityContext.CancelChildren%2A>.</span><span class="sxs-lookup"><span data-stu-id="bb71c-112">Canceling child execution using <xref:System.Activities.NativeActivityContext.CancelChild%2A> and <xref:System.Activities.NativeActivityContext.CancelChildren%2A>.</span></span>

- <span data-ttu-id="bb71c-113">Přístup k záložky aktivity pomocí metod, jako <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>, a <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>.</span><span class="sxs-lookup"><span data-stu-id="bb71c-113">Access to activity bookmarks using such methods as <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>, and <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>.</span></span>

- <span data-ttu-id="bb71c-114">Vlastní sledování funkce pomocí <xref:System.Activities.CodeActivityContext.Track%2A>.</span><span class="sxs-lookup"><span data-stu-id="bb71c-114">Custom tracking features using <xref:System.Activities.CodeActivityContext.Track%2A>.</span></span>

- <span data-ttu-id="bb71c-115">Přístup k provádění vlastnosti a hodnotu vlastnosti pomocí aktivity <xref:System.Activities.CodeActivityContext.GetProperty%2A> a <xref:System.Activities.NativeActivityContext.GetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="bb71c-115">Access to the activity’s execution properties and value properties using <xref:System.Activities.CodeActivityContext.GetProperty%2A> and <xref:System.Activities.NativeActivityContext.GetValue%2A>.</span></span>

- <span data-ttu-id="bb71c-116">Plánování aktivit akcí a funkcí pomocí <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> a <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.</span><span class="sxs-lookup"><span data-stu-id="bb71c-116">Scheduling activity actions and functions using <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> and <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.</span></span>

### <a name="to-create-a-custom-activity-that-inherits-from-nativeactivity"></a><span data-ttu-id="bb71c-117">Chcete-li vytvořit vlastní aktivitu, která dědí z nativeactivity načte jako</span><span class="sxs-lookup"><span data-stu-id="bb71c-117">To create a custom activity that inherits from NativeActivity</span></span>

1. <span data-ttu-id="bb71c-118">OpenVisual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="bb71c-118">OpenVisual Studio 2010.</span></span>

2. <span data-ttu-id="bb71c-119">Vyberte **souboru**, **nové**a potom **projektu**.</span><span class="sxs-lookup"><span data-stu-id="bb71c-119">Select **File**, **New**, and then **Project**.</span></span> <span data-ttu-id="bb71c-120">Vyberte **Workflow 4.0** pod **Visual C#** v **typy projektů** okna a vyberte **v2010** uzlu.</span><span class="sxs-lookup"><span data-stu-id="bb71c-120">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="bb71c-121">Vyberte **knihovny aktivit** v **šablony** okna.</span><span class="sxs-lookup"><span data-stu-id="bb71c-121">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="bb71c-122">Název nového projektu HelloActivity.</span><span class="sxs-lookup"><span data-stu-id="bb71c-122">Name the new project HelloActivity.</span></span>

3. <span data-ttu-id="bb71c-123">Klikněte pravým tlačítkem na Activity1.xaml HelloActivity projektu a vyberte **odstranit**.</span><span class="sxs-lookup"><span data-stu-id="bb71c-123">Right-click Activity1.xaml in the HelloActivity project and select **Delete**.</span></span>

4. <span data-ttu-id="bb71c-124">Klikněte pravým tlačítkem na projekt HelloActivity a vyberte **přidat**a potom **třídy**.</span><span class="sxs-lookup"><span data-stu-id="bb71c-124">Right-click the HelloActivity project and select **Add**, and then **Class**.</span></span> <span data-ttu-id="bb71c-125">Pojmenujte novou třídu HelloActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="bb71c-125">Name the new class HelloActivity.cs.</span></span>

5. <span data-ttu-id="bb71c-126">V souboru HelloActivity.cs, přidejte následující `using` direktivy.</span><span class="sxs-lookup"><span data-stu-id="bb71c-126">In the HelloActivity.cs file, add the following `using` directives.</span></span>

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6. <span data-ttu-id="bb71c-127">Ujistěte se, nová třída dědila z <xref:System.Activities.NativeActivity> přidáním základní třídu pro deklaraci třídy.</span><span class="sxs-lookup"><span data-stu-id="bb71c-127">Make the new class inherit from <xref:System.Activities.NativeActivity> by adding a base class to the class declaration.</span></span>

    ```csharp
    class HelloActivity : NativeActivity
    ```

7. <span data-ttu-id="bb71c-128">Přidání funkce do třídy tak, že přidáte <xref:System.Activities.NativeActivity.Execute%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="bb71c-128">Add functionality to the class by adding an <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>

    ```csharp
    protected override void Execute(NativeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8. <span data-ttu-id="bb71c-129">Přepsat <xref:System.Activities.NativeActivity.CacheMetadata%2A> metoda a volání odpovídající metody Add umožní modulu runtime pracovního postupu vědět o proměnné, argumenty, podřízené položky a delegáti vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="bb71c-129">Override the <xref:System.Activities.NativeActivity.CacheMetadata%2A> method and call the appropriate Add method to let the workflow runtime know about the custom activity’s variables, arguments, children, and delegates.</span></span> <span data-ttu-id="bb71c-130">Další informace najdete v článku <xref:System.Activities.NativeActivityMetadata> třídy.</span><span class="sxs-lookup"><span data-stu-id="bb71c-130">For more information see the <xref:System.Activities.NativeActivityMetadata> class.</span></span>

9. <span data-ttu-id="bb71c-131">Použití <xref:System.Activities.NativeActivityContext> objekt naplánování záložku.</span><span class="sxs-lookup"><span data-stu-id="bb71c-131">Use the <xref:System.Activities.NativeActivityContext> object to schedule a bookmark.</span></span> <span data-ttu-id="bb71c-132">Zobrazit <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> podrobnosti o tom, jak vytvořit, naplánovat a obnovení záložku.</span><span class="sxs-lookup"><span data-stu-id="bb71c-132">See <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> for details on how to create, schedule, and resume a bookmark.</span></span>

    ```
    protected override void Execute(NativeActivityContext context)
        {
            // Create a Bookmark and wait for it to be resumed.
            context.CreateBookmark(BookmarkName.Get(context),
                new BookmarkCallback(OnResumeBookmark));
        }
    ```
