---
title: NativeActivity základní třída
ms.date: 03/30/2017
ms.assetid: 254a4c50-425b-426d-a32f-0f7234925bac
ms.openlocfilehash: ca4a497f1e78989f9488507015526214ead6cae7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517264"
---
# <a name="nativeactivity-base-class"></a><span data-ttu-id="efdfc-102">NativeActivity základní třída</span><span class="sxs-lookup"><span data-stu-id="efdfc-102">NativeActivity Base Class</span></span>
<span data-ttu-id="efdfc-103"><xref:System.Activities.NativeActivity> je abstraktní třídy chráněný konstruktor.</span><span class="sxs-lookup"><span data-stu-id="efdfc-103"><xref:System.Activities.NativeActivity> is an abstract class with a protected constructor.</span></span> <span data-ttu-id="efdfc-104">Jako <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> slouží k zápisu imperativní chování implementací <xref:System.Activities.NativeActivity.Execute%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="efdfc-104">Like <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> is used for writing imperative behavior by implementing an <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span> <span data-ttu-id="efdfc-105">Na rozdíl od <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> má přístup ke všem zveřejněné funkce modulu runtime pracovního postupu pomocí <xref:System.Activities.NativeActivityContext> byl předán objekt <xref:System.Activities.NativeActivity.Execute%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="efdfc-105">Unlike <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> has access to all of the exposed features of the workflow runtime through the <xref:System.Activities.NativeActivityContext> object passed to the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>  
  
## <a name="using-nativeactivitycontext"></a><span data-ttu-id="efdfc-106">Pomocí NativeActivityContext</span><span class="sxs-lookup"><span data-stu-id="efdfc-106">Using NativeActivityContext</span></span>  
 <span data-ttu-id="efdfc-107">Funkce modulu runtime pracovního postupu je přístupná prostřednictvím <xref:System.Activities.NativeActivity.Execute%2A> metoda pomocí členy `context` parametr typu <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="efdfc-107">Features of the workflow runtime can be accessed from within the <xref:System.Activities.NativeActivity.Execute%2A> method by using members of the `context` parameter, of type <xref:System.Activities.NativeActivityContext>.</span></span> <span data-ttu-id="efdfc-108">Funkcí dostupných prostřednictvím <xref:System.Activities.NativeActivityContext> patří:</span><span class="sxs-lookup"><span data-stu-id="efdfc-108">The features available through <xref:System.Activities.NativeActivityContext> include the following:</span></span>  
  
-   <span data-ttu-id="efdfc-109">Získání a nastavení proměnných a argumenty.</span><span class="sxs-lookup"><span data-stu-id="efdfc-109">Getting and setting of arguments and variables.</span></span>  
  
-   <span data-ttu-id="efdfc-110">Plánování podřízené aktivity s <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A></span><span class="sxs-lookup"><span data-stu-id="efdfc-110">Scheduling child activities with <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A></span></span>  
  
-   <span data-ttu-id="efdfc-111">Přerušení aktivity provádění pomocí <xref:System.Activities.NativeActivityContext.Abort%2A>.</span><span class="sxs-lookup"><span data-stu-id="efdfc-111">Aborting activity execution using <xref:System.Activities.NativeActivityContext.Abort%2A>.</span></span>  
  
-   <span data-ttu-id="efdfc-112">Ruší podřízené provádění pomocí <xref:System.Activities.NativeActivityContext.CancelChild%2A> a <xref:System.Activities.NativeActivityContext.CancelChildren%2A>.</span><span class="sxs-lookup"><span data-stu-id="efdfc-112">Canceling child execution using <xref:System.Activities.NativeActivityContext.CancelChild%2A> and <xref:System.Activities.NativeActivityContext.CancelChildren%2A>.</span></span>  
  
-   <span data-ttu-id="efdfc-113">Přístup k aktivity záložky pomocí těchto metod jako <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>, a <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>.</span><span class="sxs-lookup"><span data-stu-id="efdfc-113">Access to activity bookmarks using such methods as <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>, and <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>.</span></span>  
  
-   <span data-ttu-id="efdfc-114">Vlastní sledování funkce pomocí <xref:System.Activities.CodeActivityContext.Track%2A>.</span><span class="sxs-lookup"><span data-stu-id="efdfc-114">Custom tracking features using <xref:System.Activities.CodeActivityContext.Track%2A>.</span></span>  
  
-   <span data-ttu-id="efdfc-115">Přístup k provádění vlastnosti a hodnotu vlastnosti pomocí aktivity <xref:System.Activities.CodeActivityContext.GetProperty%2A> a <xref:System.Activities.NativeActivityContext.GetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="efdfc-115">Access to the activity’s execution properties and value properties using <xref:System.Activities.CodeActivityContext.GetProperty%2A> and <xref:System.Activities.NativeActivityContext.GetValue%2A>.</span></span>  
  
-   <span data-ttu-id="efdfc-116">Plánování aktivity akcí a funkcí pomocí <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> a <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.</span><span class="sxs-lookup"><span data-stu-id="efdfc-116">Scheduling activity actions and functions using <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> and <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.</span></span>  
  
#### <a name="to-create-a-custom-activity-that-inherits-from-nativeactivity"></a><span data-ttu-id="efdfc-117">Chcete-li vytvořit vlastní aktivitu, která dědí z NativeActivity</span><span class="sxs-lookup"><span data-stu-id="efdfc-117">To create a custom activity that inherits from NativeActivity</span></span>  
  
1.  <span data-ttu-id="efdfc-118">Otevřete[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="efdfc-118">Open[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="efdfc-119">Vyberte **soubor**, **nové**a potom **projektu**.</span><span class="sxs-lookup"><span data-stu-id="efdfc-119">Select **File**, **New**, and then **Project**.</span></span> <span data-ttu-id="efdfc-120">Vyberte **Workflow 4.0** pod **Visual C#** v **typy projektů** a vyberte **v2010** uzlu.</span><span class="sxs-lookup"><span data-stu-id="efdfc-120">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="efdfc-121">Vyberte **knihovna aktivit** v **šablony** okno.</span><span class="sxs-lookup"><span data-stu-id="efdfc-121">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="efdfc-122">Název nového projektu HelloActivity.</span><span class="sxs-lookup"><span data-stu-id="efdfc-122">Name the new project HelloActivity.</span></span>  
  
3.  <span data-ttu-id="efdfc-123">Klikněte pravým tlačítkem na Activity1.xaml v HelloActivity projektu a vyberte **odstranit**.</span><span class="sxs-lookup"><span data-stu-id="efdfc-123">Right-click Activity1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4.  <span data-ttu-id="efdfc-124">Klikněte pravým tlačítkem na projekt HelloActivity a vyberte **přidat**a potom **třída**.</span><span class="sxs-lookup"><span data-stu-id="efdfc-124">Right-click the HelloActivity project and select **Add**, and then **Class**.</span></span> <span data-ttu-id="efdfc-125">Pojmenujte novou třídu HelloActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="efdfc-125">Name the new class HelloActivity.cs.</span></span>  
  
5.  <span data-ttu-id="efdfc-126">V souboru HelloActivity.cs, přidejte následující `using` direktivy.</span><span class="sxs-lookup"><span data-stu-id="efdfc-126">In the HelloActivity.cs file, add the following `using` directives.</span></span>  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.Statements;  
    ```  
  
6.  <span data-ttu-id="efdfc-127">Ujistěte se, nové třídy dědí <xref:System.Activities.NativeActivity> přidáním základní třídu pro deklaraci třídy.</span><span class="sxs-lookup"><span data-stu-id="efdfc-127">Make the new class inherit from <xref:System.Activities.NativeActivity> by adding a base class to the class declaration.</span></span>  
  
    ```csharp  
    class HelloActivity : NativeActivity  
    ```  
  
7.  <span data-ttu-id="efdfc-128">Přidání funkce do třídy přidáním <xref:System.Activities.NativeActivity.Execute%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="efdfc-128">Add functionality to the class by adding an <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>  
  
    ```csharp  
    protected override void Execute(NativeActivityContext context)  
    {  
        Console.WriteLine("Hello World!");  
    }  
    ```  
  
8.  <span data-ttu-id="efdfc-129">Přepsání <xref:System.Activities.NativeActivity.CacheMetadata%2A> metoda a volání odpovídající metodu přidat umožníte modulu runtime pracovního postupu vědět o proměnné vlastní aktivity, argumenty, děti a delegáti.</span><span class="sxs-lookup"><span data-stu-id="efdfc-129">Override the <xref:System.Activities.NativeActivity.CacheMetadata%2A> method and call the appropriate Add method to let the workflow runtime know about the custom activity’s variables, arguments, children, and delegates.</span></span> <span data-ttu-id="efdfc-130">Další informace najdete v článku <xref:System.Activities.NativeActivityMetadata> třídy.</span><span class="sxs-lookup"><span data-stu-id="efdfc-130">For more information see the <xref:System.Activities.NativeActivityMetadata> class.</span></span>  
  
9. <span data-ttu-id="efdfc-131">Použití <xref:System.Activities.NativeActivityContext> objekt, který chcete naplánovat záložky.</span><span class="sxs-lookup"><span data-stu-id="efdfc-131">Use the <xref:System.Activities.NativeActivityContext> object to schedule a bookmark.</span></span> <span data-ttu-id="efdfc-132">V tématu <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> podrobnosti o tom, jak vytvořit, naplánovat a obnovit záložky.</span><span class="sxs-lookup"><span data-stu-id="efdfc-132">See <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> for details on how to create, schedule, and resume a bookmark.</span></span>  
  
    ```  
    protected override void Execute(NativeActivityContext context)  
        {  
            // Create a Bookmark and wait for it to be resumed.  
            context.CreateBookmark(BookmarkName.Get(context),   
                new BookmarkCallback(OnResumeBookmark));  
        }  
    ```
