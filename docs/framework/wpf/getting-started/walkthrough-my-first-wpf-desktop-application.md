---
title: "Návod: Můj první grafický subsystém WPF aplikace pracovní plochy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
caps.latest.revision: "71"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3667d507f4c35174c1e888c9781b5f74ffd496a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a><span data-ttu-id="a43db-102">Návod: Můj první grafický subsystém WPF aplikace pracovní plochy</span><span class="sxs-lookup"><span data-stu-id="a43db-102">Walkthrough: My first WPF desktop application</span></span>
<span data-ttu-id="a43db-103">Tento názorný postup obsahuje úvod do vývoje [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] aplikace, která obsahuje prvky, které jsou společné pro většinu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace: [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] značek, kódu, definice aplikace, ovládací prvky, rozložení Datová vazba a stylů.</span><span class="sxs-lookup"><span data-stu-id="a43db-103">This walkthrough provides an introduction to the development of a [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] application that includes the elements that are common to most [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications: [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span> 
  
 <span data-ttu-id="a43db-104">Tento postup vás provede vývoj jednoduchou [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace pomocí následujících kroků.</span><span class="sxs-lookup"><span data-stu-id="a43db-104">This walkthrough guides you through the development of a simple [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application using the following steps.</span></span> 
  
-   <span data-ttu-id="a43db-105">Definování [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] návrhu vzhled aplikace [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a43db-105">Defining [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] to design the appearance of the application's [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span> 
  
-   <span data-ttu-id="a43db-106">Psaní kódu k sestavení chování aplikace.</span><span class="sxs-lookup"><span data-stu-id="a43db-106">Writing code to build the application's behavior.</span></span> 
  
-   <span data-ttu-id="a43db-107">Vytvoření definice aplikace ke správě aplikace.</span><span class="sxs-lookup"><span data-stu-id="a43db-107">Creating an application definition to manage the application.</span></span> 
  
-   <span data-ttu-id="a43db-108">Přidání ovládacích prvků a vytváření rozložení k vytvoření aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a43db-108">Adding controls and creating the layout to compose the application [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span></span> 
  
-   <span data-ttu-id="a43db-109">Vytváření stylů pro vytvoření konzistentní vzhled aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a43db-109">Creating styles to create a consistent appearance throughout an application's [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span></span> 
  
-   <span data-ttu-id="a43db-110">Vazba [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] k datům a obě naplnit [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z data a zachovat data a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] synchronizovány.</span><span class="sxs-lookup"><span data-stu-id="a43db-110">Binding the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to data to both populate the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] from data and keep the data and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] synchronized.</span></span> 
  
 <span data-ttu-id="a43db-111">Na konci průvodce, který bude jste vytvořili samostatnou [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] aplikace, která umožňuje uživatelům zobrazit sestavy výdajů pro vybrané osoby.</span><span class="sxs-lookup"><span data-stu-id="a43db-111">By the end of the walkthrough, you will have built a standalone [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="a43db-112">Aplikace se skládá z několika [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] stránek, které jsou hostované v okně prohlížeče stylu.</span><span class="sxs-lookup"><span data-stu-id="a43db-112">The application will be composed of several [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pages that are hosted in a browser-style window.</span></span> 
  
 <span data-ttu-id="a43db-113">Ukázkový kód, který je použit k vytvoření tohoto návodu je dostupná pro [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] a [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] v [Úvod do vytváření grafického subsystému WPF aplikací](http://go.microsoft.com/fwlink/?LinkID=160008).</span><span class="sxs-lookup"><span data-stu-id="a43db-113">The sample code that is used to build this walkthrough is available for both [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] and [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] at  [Introduction to Building WPF Applications](http://go.microsoft.com/fwlink/?LinkID=160008).</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="a43db-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a43db-114">Prerequisites</span></span>  

- [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="a43db-115">nebo novější</span><span class="sxs-lookup"><span data-stu-id="a43db-115"> or later</span></span>

<span data-ttu-id="a43db-116">Další informace o instalaci nejnovější verze sady Visual Studio najdete v tématu [instalaci sady Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="a43db-116">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>
  
## <a name="creating-the-application-project"></a><span data-ttu-id="a43db-117">Vytvoření projektu aplikace</span><span class="sxs-lookup"><span data-stu-id="a43db-117">Creating the application project</span></span>  
 <span data-ttu-id="a43db-118">V této části vytvoříte infrastrukturu aplikace, která zahrnuje definice aplikace, dvě stránky a bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="a43db-118">In this section, you create the application infrastructure, which includes an application definition, two pages, and an image.</span></span> 
  
1. <span data-ttu-id="a43db-119">Vytvořte nový projekt aplikace WPF v jazyce Visual Basic a Visual C# s názvem `ExpenseIt`.</span><span class="sxs-lookup"><span data-stu-id="a43db-119">Create a new WPF Application project in Visual Basic or Visual C# named `ExpenseIt`.</span></span> <span data-ttu-id="a43db-120">Další informace najdete v tématu [postupy: vytvoření nového projektu aplikace WPF](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span><span class="sxs-lookup"><span data-stu-id="a43db-120">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span> 
  
    > [!NOTE]
    >  <span data-ttu-id="a43db-121">Tento návod používá <xref:System.Windows.Controls.DataGrid> ovládací prvek, který je k dispozici v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a43db-121">This walkthrough uses the <xref:System.Windows.Controls.DataGrid> control that is available in the .NET Framework 4.</span></span> <span data-ttu-id="a43db-122">Být jisti, že cílem vašeho projektu je .NET Framework 4 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="a43db-122">Be sure that your project targets the .NET Framework 4 or later.</span></span> <span data-ttu-id="a43db-123">Další informace najdete v tématu[postupy: cílení na verzi rozhraní .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span><span class="sxs-lookup"><span data-stu-id="a43db-123">For more information, see[How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span> 
  
2. <span data-ttu-id="a43db-124">Otevřete Application.xaml (Visual Basic) nebo App.xaml (C#).</span><span class="sxs-lookup"><span data-stu-id="a43db-124">Open Application.xaml (Visual Basic) or App.xaml (C#).</span></span> 
  
     <span data-ttu-id="a43db-125">To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor definuje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace a všechny prostředky aplikace.</span><span class="sxs-lookup"><span data-stu-id="a43db-125">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file defines a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application and any application resources.</span></span> <span data-ttu-id="a43db-126">Tento soubor můžete taky použít k určení [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] která automaticky zobrazí při spuštění aplikace; v tomto případě MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="a43db-126">You also use this file to specify the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] that automatically shows when the application starts; in this case, MainWindow.xaml.</span></span> 
  
     <span data-ttu-id="a43db-127">Vaše [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] by mělo vypadat jako v jazyce Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="a43db-127">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#1_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]  
  
     <span data-ttu-id="a43db-128">Nebo podobně jako v C#:</span><span class="sxs-lookup"><span data-stu-id="a43db-128">Or like this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]  
  
3. <span data-ttu-id="a43db-129">Otevřete MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="a43db-129">Open MainWindow.xaml.</span></span> 
  
     <span data-ttu-id="a43db-130">To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor je hlavním okně aplikace a zobrazí obsah vytvořený v stránky.</span><span class="sxs-lookup"><span data-stu-id="a43db-130">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="a43db-131"><xref:System.Windows.Window> Třídy definuje vlastnosti časového období, například jeho název, velikost nebo ikonu a zpracovává události, například zavření nebo skrytí.</span><span class="sxs-lookup"><span data-stu-id="a43db-131">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span> 
  
4. <span data-ttu-id="a43db-132">Změna <xref:System.Windows.Window> elementu, který chcete <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="a43db-132">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> 
  
     <span data-ttu-id="a43db-133">Tato aplikace bude přejděte na jiný obsah, v závislosti na interakci s uživatelem.</span><span class="sxs-lookup"><span data-stu-id="a43db-133">This application will navigate to different content depending on the user interaction.</span></span> <span data-ttu-id="a43db-134">Proto hlavní <xref:System.Windows.Window> musí změnit tak, aby <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="a43db-134">Therefore, the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="a43db-135"><xref:System.Windows.Navigation.NavigationWindow>dědí všechny vlastnosti <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="a43db-135"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="a43db-136"><xref:System.Windows.Navigation.NavigationWindow> Element v souboru XAML vytvoří instanci <xref:System.Windows.Navigation.NavigationWindow> třídy.</span><span class="sxs-lookup"><span data-stu-id="a43db-136">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="a43db-137">Další informace najdete v tématu [navigační přehled](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a43db-137">For more information, see [Navigation Overview](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span></span> 
  
5. <span data-ttu-id="a43db-138">Změnit na následující vlastnosti <xref:System.Windows.Navigation.NavigationWindow> element:</span><span class="sxs-lookup"><span data-stu-id="a43db-138">Change the following properties on the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>  
  
    -   <span data-ttu-id="a43db-139">Nastavte <xref:System.Windows.Window.Title%2A> vlastnost ExpenseIt "–".</span><span class="sxs-lookup"><span data-stu-id="a43db-139">Set the <xref:System.Windows.Window.Title%2A> property to "ExpenseIt".</span></span> 
  
    -   <span data-ttu-id="a43db-140">Nastavte <xref:System.Windows.FrameworkElement.Width%2A> vlastnost na 500 pixelů.</span><span class="sxs-lookup"><span data-stu-id="a43db-140">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span> 
  
    -   <span data-ttu-id="a43db-141">Nastavte <xref:System.Windows.FrameworkElement.Height%2A> vlastnost 350 pixelů.</span><span class="sxs-lookup"><span data-stu-id="a43db-141">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span> 
  
    -   <span data-ttu-id="a43db-142">Odeberte <xref:System.Windows.Controls.Grid> prvky mezi <xref:System.Windows.Navigation.NavigationWindow> značky.</span><span class="sxs-lookup"><span data-stu-id="a43db-142">Remove the <xref:System.Windows.Controls.Grid> elements between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span> 
  
     <span data-ttu-id="a43db-143">Vaše [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] by mělo vypadat jako v jazyce Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="a43db-143">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#2_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]  
  
     <span data-ttu-id="a43db-144">Nebo podobně jako v C#:</span><span class="sxs-lookup"><span data-stu-id="a43db-144">Or like this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]  
  
6. <span data-ttu-id="a43db-145">Otevřete MainWindow.xaml.vb nebo MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="a43db-145">Open MainWindow.xaml.vb or MainWindow.xaml.cs.</span></span> 
  
     <span data-ttu-id="a43db-146">Tento soubor je soubor kódu, který obsahuje kód pro zpracování události deklarované v MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="a43db-146">This file is a code-behind file that contains code to handle the events declared in MainWindow.xaml.</span></span> <span data-ttu-id="a43db-147">Tento soubor obsahuje konkrétní třídu pro okno definované v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="a43db-147">This file contains a partial class for the window defined in XAML.</span></span> 
  
7. <span data-ttu-id="a43db-148">Pokud používáte C#, změňte `MainWindow` odvozena od třídy <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="a43db-148">If you are using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> 
  
     <span data-ttu-id="a43db-149">V jazyce Visual Basic tomu automaticky dojde při změně okna v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="a43db-149">In Visual Basic, this happens automatically when you change the window in XAML.</span></span> 
  
     <span data-ttu-id="a43db-150">Váš kód by měl vypadat takto.</span><span class="sxs-lookup"><span data-stu-id="a43db-150">Your code should look like this.</span></span> 
  
    [!code-csharp[ExpenseIt#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
    [!code-vb[ExpenseIt#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]  
  
## <a name="adding-files-to-the-application"></a><span data-ttu-id="a43db-151">Přidávání souborů do aplikace</span><span class="sxs-lookup"><span data-stu-id="a43db-151">Adding files to the application</span></span>  
 <span data-ttu-id="a43db-152">V této části přidáte dvě stránky a bitovou kopii do aplikace.</span><span class="sxs-lookup"><span data-stu-id="a43db-152">In this section, you add two pages and an image to the application.</span></span> 
  
1. <span data-ttu-id="a43db-153">Přidat nové stránky (WPF) do projektu s názvem `ExpenseItHome.xaml`.</span><span class="sxs-lookup"><span data-stu-id="a43db-153">Add a new Page (WPF) to the project named `ExpenseItHome.xaml`.</span></span> <span data-ttu-id="a43db-154">Další informace najdete v tématu [postupy: přidání nových položek do projektu WPF](http://msdn.microsoft.com/en-us/17e6b238-fc32-4385-98ef-2f66ca09d9ad).</span><span class="sxs-lookup"><span data-stu-id="a43db-154">For more information, see [How to: Add New Items to a WPF Project](http://msdn.microsoft.com/en-us/17e6b238-fc32-4385-98ef-2f66ca09d9ad).</span></span> 
  
     <span data-ttu-id="a43db-155">Tato stránka je první stránka, která se zobrazí, když je aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="a43db-155">This page is the first page that is displayed when the application is launched.</span></span> <span data-ttu-id="a43db-156">Zobrazí seznam uživatelů, ze kterého může uživatel vybrat uživatele, který bude zobrazit sestavu výdajů pro.</span><span class="sxs-lookup"><span data-stu-id="a43db-156">It will show a list of people from which a user can select a person to show an expense report for.</span></span> 
  
2. <span data-ttu-id="a43db-157">Otevřete ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="a43db-157">Open ExpenseItHome.xaml.</span></span> 
  
3. <span data-ttu-id="a43db-158">Nastavte <xref:System.Windows.Controls.Page.Title%2A> k "ExpenseIt – - domovské".</span><span class="sxs-lookup"><span data-stu-id="a43db-158">Set the <xref:System.Windows.Controls.Page.Title%2A> to "ExpenseIt - Home".</span></span> 
  
     <span data-ttu-id="a43db-159">Vaše [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] by mělo vypadat jako v jazyce Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="a43db-159">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#6_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]  
  
     <span data-ttu-id="a43db-160">Nebo to v jazyce C#:</span><span class="sxs-lookup"><span data-stu-id="a43db-160">Or this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]  
  
4. <span data-ttu-id="a43db-161">Otevřete MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="a43db-161">Open MainWindow.xaml.</span></span> 
  
5. <span data-ttu-id="a43db-162">Nastavte <xref:System.Windows.Navigation.NavigationWindow.Source%2A> vlastnost <xref:System.Windows.Navigation.NavigationWindow> na "ExpenseItHome.xaml".</span><span class="sxs-lookup"><span data-stu-id="a43db-162">Set the <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property on the <xref:System.Windows.Navigation.NavigationWindow> to "ExpenseItHome.xaml".</span></span> 
  
     <span data-ttu-id="a43db-163">Toto nastaví ExpenseItHome.xaml na první stránce otevřelo při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="a43db-163">This sets ExpenseItHome.xaml to be the first page opened when the application starts.</span></span> <span data-ttu-id="a43db-164">Vaše [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] by mělo vypadat jako v jazyce Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="a43db-164">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#7_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]  
  
     <span data-ttu-id="a43db-165">Nebo to v jazyce C#:</span><span class="sxs-lookup"><span data-stu-id="a43db-165">Or this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]  
  
6. <span data-ttu-id="a43db-166">Přidat nové stránky (WPF) do projektu s názvem `ExpenseReportPage.xaml`.</span><span class="sxs-lookup"><span data-stu-id="a43db-166">Add a new Page (WPF) to the project named `ExpenseReportPage.xaml`.</span></span> 
  
     <span data-ttu-id="a43db-167">Tato stránka se zobrazí vyúčtování pro osobě, která je vybrána na ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="a43db-167">This page will show the expense report for the person that is selected on ExpenseItHome.xaml.</span></span> 
  
7. <span data-ttu-id="a43db-168">Otevřete ExpenseReportPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="a43db-168">Open ExpenseReportPage.xaml.</span></span> 
  
8. <span data-ttu-id="a43db-169">Nastavte <xref:System.Windows.Controls.Page.Title%2A> k "ExpenseIt – - zobrazení výdajů".</span><span class="sxs-lookup"><span data-stu-id="a43db-169">Set the <xref:System.Windows.Controls.Page.Title%2A> to "ExpenseIt - View Expense".</span></span> 
  
     <span data-ttu-id="a43db-170">Vaše [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] by mělo vypadat jako v jazyce Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="a43db-170">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#4_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]  
  
     <span data-ttu-id="a43db-171">Nebo to v jazyce C#:</span><span class="sxs-lookup"><span data-stu-id="a43db-171">Or this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]  
  
9. <span data-ttu-id="a43db-172">Otevřete ExpenseItHome.xaml.vb a ExpenseReportPage.xaml.vb, nebo ExpenseItHome.xaml.cs a ExpenseReportPage.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="a43db-172">Open ExpenseItHome.xaml.vb and ExpenseReportPage.xaml.vb, or ExpenseItHome.xaml.cs and ExpenseReportPage.xaml.cs.</span></span> 
  
     <span data-ttu-id="a43db-173">Když vytvoříte nový soubor stránky, Visual Studio automaticky vytvoří souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="a43db-173">When you create a new Page file, Visual Studio automatically creates a code behind file.</span></span> <span data-ttu-id="a43db-174">Tyto soubory kódu zpracování logiky reagovat na vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="a43db-174">These code-behind files handle the logic for responding to user input.</span></span> 
  
     <span data-ttu-id="a43db-175">Váš kód by měl vypadat takto.</span><span class="sxs-lookup"><span data-stu-id="a43db-175">Your code should look like this.</span></span> 
  
    [!code-csharp[ExpenseIt#2_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
    [!code-vb[ExpenseIt#2_5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]  
  
    [!code-csharp[ExpenseIt#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
    [!code-vb[ExpenseIt#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]  
  
10. <span data-ttu-id="a43db-176">Přidejte bitovou kopii s názvem watermark.png do projektu.</span><span class="sxs-lookup"><span data-stu-id="a43db-176">Add an image named watermark.png to the project.</span></span> <span data-ttu-id="a43db-177">Můžete vytvořit vlastní image, nebo zkopírovat soubor z ukázkového kódu.</span><span class="sxs-lookup"><span data-stu-id="a43db-177">You can either create your own image, or copy the file from the sample code.</span></span> <span data-ttu-id="a43db-178">Další informace najdete v tématu [NIB: postupy: Přidání existujících položek do projektu](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span><span class="sxs-lookup"><span data-stu-id="a43db-178">For more information, see [NIB:How to: Add Existing Items to a Project](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span></span> 

## <a name="building-and-running-the-application"></a><span data-ttu-id="a43db-179">Vytváření a spouštění aplikace</span><span class="sxs-lookup"><span data-stu-id="a43db-179">Building and running the application</span></span>  
 <span data-ttu-id="a43db-180">V této části sestavíte a spustíte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a43db-180">In this section, you build and run the application.</span></span> 
  
1. <span data-ttu-id="a43db-181">Sestavte a spusťte aplikaci stisknutím klávesy F5 nebo vyberte **spustit ladění** z **ladění** nabídky.</span><span class="sxs-lookup"><span data-stu-id="a43db-181">Build and run the application by pressing F5 or select **Start Debugging** from the **Debug** menu.</span></span> 
  
     <span data-ttu-id="a43db-182">Následující obrázek znázorňuje aplikace s <xref:System.Windows.Navigation.NavigationWindow> tlačítka.</span><span class="sxs-lookup"><span data-stu-id="a43db-182">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons.</span></span> 
  
     <span data-ttu-id="a43db-183">![Snímek obrazovky ExpenseIt –](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png "GettingStartedFigure1")</span><span class="sxs-lookup"><span data-stu-id="a43db-183">![ExpenseIt sample screen shot](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png "GettingStartedFigure1")</span></span>  
  
2. <span data-ttu-id="a43db-184">Zavřete aplikaci se vraťte do [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a43db-184">Close the application to return to [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span> 
  
## <a name="creating-the-layout"></a><span data-ttu-id="a43db-185">Vytváření rozložení</span><span class="sxs-lookup"><span data-stu-id="a43db-185">Creating the layout</span></span>  
 <span data-ttu-id="a43db-186">Rozložení poskytuje seřazené způsob, jak umístit [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvky a také spravuje velikost a umístění těchto elementů při [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] se změnila velikost.</span><span class="sxs-lookup"><span data-stu-id="a43db-186">Layout provides an ordered way to place [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements, and also manages the size and position of those elements when a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] is resized.</span></span> <span data-ttu-id="a43db-187">Obvykle vytvoříte rozložení s jedním z následujících rozložení ovládacích prvků:</span><span class="sxs-lookup"><span data-stu-id="a43db-187">You typically create a layout with one of the following layout controls:</span></span>  
  
-   <xref:System.Windows.Controls.Canvas>  
  
-   <xref:System.Windows.Controls.DockPanel>  
  
-   <xref:System.Windows.Controls.Grid>  
  
-   <xref:System.Windows.Controls.StackPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
-   <xref:System.Windows.Controls.WrapPanel>  
  
 <span data-ttu-id="a43db-188">Každý z těchto prvků rozložení podporuje zvláštním typem rozložení pro její podřízené elementy.</span><span class="sxs-lookup"><span data-stu-id="a43db-188">Each of these layout controls supports a special type of layout for its child elements.</span></span> <span data-ttu-id="a43db-189">Stránky ExpenseIt – jde změnit, a každé stránce má prvky, které jsou uspořádány vodorovně a svisle u jiných prvků.</span><span class="sxs-lookup"><span data-stu-id="a43db-189">ExpenseIt pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="a43db-190">V důsledku toho <xref:System.Windows.Controls.Grid> je ideální rozložení elementu pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a43db-190">Consequently, the <xref:System.Windows.Controls.Grid> is the ideal layout element for the application.</span></span> 
  
> [!NOTE]
>  <span data-ttu-id="a43db-191">Další informace o <xref:System.Windows.Controls.Panel> elementy, najdete v části [přehled panelů](../../../../docs/framework/wpf/controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a43db-191">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels Overview](../../../../docs/framework/wpf/controls/panels-overview.md).</span></span> <span data-ttu-id="a43db-192">Další informace o rozložení najdete v tématu [rozložení](../../../../docs/framework/wpf/advanced/layout.md).</span><span class="sxs-lookup"><span data-stu-id="a43db-192">For more information about layout, see [Layout](../../../../docs/framework/wpf/advanced/layout.md).</span></span> 
  
 <span data-ttu-id="a43db-193">V části vytvoříte tabulku s jedním sloupcem s tři řádky a okraj 10 pixelů přidáním sloupce a řádku definice, které <xref:System.Windows.Controls.Grid> v ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="a43db-193">In the section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in ExpenseItHome.xaml.</span></span> 
  
1. <span data-ttu-id="a43db-194">Otevřete ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="a43db-194">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="a43db-195">Nastavte <xref:System.Windows.FrameworkElement.Margin%2A> vlastnost <xref:System.Windows.Controls.Grid> element "10,0,10,10", který odpovídá na levé straně, horní, pravé a dolní okraj.</span><span class="sxs-lookup"><span data-stu-id="a43db-195">Set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10" which corresponds to left, top, right and bottom margins.</span></span> 
  
3. <span data-ttu-id="a43db-196">Přidejte následující [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] mezi <xref:System.Windows.Controls.Grid> značek k vytvoření definice řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="a43db-196">Add the following [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions.</span></span> 
  
    [!code-xaml[ExpenseIt#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]  
  
     <span data-ttu-id="a43db-197"><xref:System.Windows.Controls.RowDefinition.Height%2A> Dvou řádků je nastaven na <xref:System.Windows.GridLength.Auto%2A> to znamená, že bude mít velikost řádky založit na obsah v řádcích.</span><span class="sxs-lookup"><span data-stu-id="a43db-197">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A> which means that the rows will be sized base on the content in the rows.</span></span> <span data-ttu-id="a43db-198">Výchozí hodnota <xref:System.Windows.Controls.RowDefinition.Height%2A> je <xref:System.Windows.GridUnitType.Star> nastavení velikosti, což znamená, že řádek bude vyvážené podíl volné místo.</span><span class="sxs-lookup"><span data-stu-id="a43db-198">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row will be a weighted proportion of the available space.</span></span> <span data-ttu-id="a43db-199">Například pokud dva řádky mít výšku "*", budou mít obě výška, který je polovinu dostupné místo.</span><span class="sxs-lookup"><span data-stu-id="a43db-199">For example if two rows each have a height of "*", they will each have a height that is half of the available space.</span></span>  
  
     <span data-ttu-id="a43db-200">Vaše <xref:System.Windows.Controls.Grid> by teď měl vypadat jako následující XAML:</span><span class="sxs-lookup"><span data-stu-id="a43db-200">Your <xref:System.Windows.Controls.Grid> should now look like the following XAML:</span></span>  
  
    [!code-xaml[ExpenseIt#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]  
  
## <a name="adding-controls"></a><span data-ttu-id="a43db-201">Přidání ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="a43db-201">Adding controls</span></span>  
 <span data-ttu-id="a43db-202">V této části se na domovskou stránku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zobrazí seznam lidí, že uživatelé mohou vybírat z zobrazíte vyúčtování pro vybraného uživatele.</span><span class="sxs-lookup"><span data-stu-id="a43db-202">In this section, the home page [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] is updated to show a list of people that users can select from to show the expense report for a selected person.</span></span> <span data-ttu-id="a43db-203">Ovládací prvky jsou objekty uživatelského rozhraní, které umožňují uživatelům interakci s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="a43db-203">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="a43db-204">Další informace najdete v tématu [ovládací prvky](../../../../docs/framework/wpf/controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="a43db-204">For more information, see [Controls](../../../../docs/framework/wpf/controls/index.md).</span></span> 
  
 <span data-ttu-id="a43db-205">K vytvoření tohoto [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], tyto prvky jsou přidány do ExpenseItHome.xaml:</span><span class="sxs-lookup"><span data-stu-id="a43db-205">To create this [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], the following elements are added to ExpenseItHome.xaml:</span></span>  
  
-   <span data-ttu-id="a43db-206"><xref:System.Windows.Controls.ListBox>(pro seznam lidí, kteří).</span><span class="sxs-lookup"><span data-stu-id="a43db-206"><xref:System.Windows.Controls.ListBox> (for the list of people).</span></span> 
  
-   <span data-ttu-id="a43db-207"><xref:System.Windows.Controls.Label>(pro hlavičku seznamu).</span><span class="sxs-lookup"><span data-stu-id="a43db-207"><xref:System.Windows.Controls.Label> (for the list header).</span></span> 
  
-   <span data-ttu-id="a43db-208"><xref:System.Windows.Controls.Button>(Chcete-li kliknutím zobrazíte vyúčtování osoby, který je vybraný v seznamu).</span><span class="sxs-lookup"><span data-stu-id="a43db-208"><xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span> 
  
 <span data-ttu-id="a43db-209">Každý ovládací prvek je umístěn v řádek <xref:System.Windows.Controls.Grid> nastavením <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> přidružená vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a43db-209">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="a43db-210">Další informace o přidružené vlastnosti najdete v tématu [připojen přehled vlastností](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a43db-210">For more information about attached properties, see [Attached Properties Overview](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).</span></span> 
  
1. <span data-ttu-id="a43db-211">Otevřete ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="a43db-211">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="a43db-212">Přidejte následující [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] mezi <xref:System.Windows.Controls.Grid> značky.</span><span class="sxs-lookup"><span data-stu-id="a43db-212">Add the following [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] between the <xref:System.Windows.Controls.Grid> tags.</span></span> 
  
    [!code-xaml[ExpenseIt#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]  
  
3. <span data-ttu-id="a43db-213">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a43db-213">Build and run the application.</span></span> 
  
 <span data-ttu-id="a43db-214">Následující obrázek znázorňuje ovládacích prvků, které jsou vytvořené pomocí XAML v této části.</span><span class="sxs-lookup"><span data-stu-id="a43db-214">The following illustration shows the controls that are created by the XAML in this section.</span></span> 
  
 <span data-ttu-id="a43db-215">![Snímek obrazovky ExpenseIt –](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png "GettingStartedFigure2")</span><span class="sxs-lookup"><span data-stu-id="a43db-215">![ExpenseIt sample screen shot](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png "GettingStartedFigure2")</span></span>  
  
## <a name="adding-an-image-and-a-title"></a><span data-ttu-id="a43db-216">Přidání obrázku a název</span><span class="sxs-lookup"><span data-stu-id="a43db-216">Adding an image and a title</span></span>  
 <span data-ttu-id="a43db-217">V této části se na domovskou stránku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] se aktualizují bitovou kopii a název stránky.</span><span class="sxs-lookup"><span data-stu-id="a43db-217">In this section, the home page [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] is updated with an image and a page title.</span></span> 
  
1. <span data-ttu-id="a43db-218">Otevřete ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="a43db-218">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="a43db-219">Přidejte jiný sloupec pro <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> s pevným <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 pixelů.</span><span class="sxs-lookup"><span data-stu-id="a43db-219">Add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels.</span></span> 
  
    [!code-xaml[ExpenseIt#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]  
  
3. <span data-ttu-id="a43db-220">Přidejte jiný řádek na <xref:System.Windows.Controls.Grid.RowDefinitions%2A>.</span><span class="sxs-lookup"><span data-stu-id="a43db-220">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>.</span></span> 
  
    [!code-xaml[ExpenseIt#11b](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]  
  
4. <span data-ttu-id="a43db-221">Přesunout ovládacích prvků na druhý sloupec nastavením <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> na 1.</span><span class="sxs-lookup"><span data-stu-id="a43db-221">Move the controls to the second column by setting <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> to 1.</span></span> <span data-ttu-id="a43db-222">Každý ovládací prvek dolů řádek, zvýšením <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> o 1.</span><span class="sxs-lookup"><span data-stu-id="a43db-222">Move each control down a row, by increasing the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> by 1.</span></span> 
  
    [!code-xaml[ExpenseIt#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]  
  
5. <span data-ttu-id="a43db-223">Nastavte <xref:System.Windows.Controls.Panel.Background%2A> z <xref:System.Windows.Controls.Grid> být watermark.png soubor bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="a43db-223">Set the <xref:System.Windows.Controls.Panel.Background%2A> of the <xref:System.Windows.Controls.Grid> to be the watermark.png image file.</span></span> 
  
    [!code-xaml[ExpenseIt#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]  
  
6. <span data-ttu-id="a43db-224">Před <xref:System.Windows.Controls.Border>, přidejte <xref:System.Windows.Controls.Label> s obsahem "Zobrazit sestavu výdajů" jako nadpis stránky.</span><span class="sxs-lookup"><span data-stu-id="a43db-224">Before the <xref:System.Windows.Controls.Border>, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report" to be the title of the page.</span></span> 
  
    [!code-xaml[ExpenseIt#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]  
  
7. <span data-ttu-id="a43db-225">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a43db-225">Build and run the application.</span></span> 
  
 <span data-ttu-id="a43db-226">Následující obrázek znázorňuje výsledky v této části.</span><span class="sxs-lookup"><span data-stu-id="a43db-226">The following illustration shows the results of this section.</span></span> 
  
 <span data-ttu-id="a43db-227">![Snímek obrazovky ExpenseIt –](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png "GettingStartedFigure3")</span><span class="sxs-lookup"><span data-stu-id="a43db-227">![ExpenseIt sample screen shot](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png "GettingStartedFigure3")</span></span>  
  
## <a name="adding-code-to-handle-events"></a><span data-ttu-id="a43db-228">Přidání kódu ke zpracování událostí</span><span class="sxs-lookup"><span data-stu-id="a43db-228">Adding code to handle events</span></span>  
  
1. <span data-ttu-id="a43db-229">Otevřete ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="a43db-229">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="a43db-230">Přidat <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužná rutina události <xref:System.Windows.Controls.Button> elementu.</span><span class="sxs-lookup"><span data-stu-id="a43db-230">Add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="a43db-231">Další informace najdete v tématu [postupy: vytvoření jednoduché obslužné rutiny události](http://msdn.microsoft.com/en-us/b1456e07-9dec-4354-99cf-18666b64f480).</span><span class="sxs-lookup"><span data-stu-id="a43db-231">For more information, see [How to: Create a Simple Event Handler](http://msdn.microsoft.com/en-us/b1456e07-9dec-4354-99cf-18666b64f480).</span></span> 
  
    [!code-xaml[ExpenseIt#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]  
  
3. <span data-ttu-id="a43db-232">Otevřete ExpenseItHome.xaml.vb nebo ExpenseItHome.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="a43db-232">Open ExpenseItHome.xaml.vb or ExpenseItHome.xaml.cs.</span></span> 
  
4. <span data-ttu-id="a43db-233">Přidejte následující kód, který <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužné rutiny události, což způsobí, že okno a přejděte k souboru ExpenseReportPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="a43db-233">Add the following code to the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler, which causes the window to navigate to the ExpenseReportPage.xaml file.</span></span> 
  
    [!code-csharp[ExpenseIt#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]  
  
## <a name="creating-the-ui-for-expensereportpage"></a><span data-ttu-id="a43db-234">Vytvoření uživatelského rozhraní pro ExpenseReportPage</span><span class="sxs-lookup"><span data-stu-id="a43db-234">Creating the UI for ExpenseReportPage</span></span>  
 <span data-ttu-id="a43db-235">ExpenseReportPage.xaml zobrazí vyúčtování osoby, která byla vybrána na ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="a43db-235">ExpenseReportPage.xaml displays the expense report for the person that was selected on the ExpenseItHome.xaml.</span></span> <span data-ttu-id="a43db-236">Tato část přidá ovládací prvky a vytvoří [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pro ExpenseReportPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="a43db-236">This section adds controls and creates the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] for ExpenseReportPage.xaml.</span></span> <span data-ttu-id="a43db-237">Tato část také přidá barvy pozadí a výplně na různé [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementy.</span><span class="sxs-lookup"><span data-stu-id="a43db-237">This section also adds background and fill colors to the various [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements.</span></span> 
  
1. <span data-ttu-id="a43db-238">Otevřete ExpenseReportPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="a43db-238">Open ExpenseReportPage.xaml.</span></span> 
  
2. <span data-ttu-id="a43db-239">Přidejte následující XAML mezi <xref:System.Windows.Controls.Grid> značky.</span><span class="sxs-lookup"><span data-stu-id="a43db-239">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags.</span></span> 
  
     <span data-ttu-id="a43db-240">Toto uživatelské rozhraní je podobná na ExpenseItHome.xaml vytvořit, s výjimkou data sestavy se zobrazí v uživatelském rozhraní <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="a43db-240">This UI is similar to the UI created on ExpenseItHome.xaml except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span> 
  
    [!code-xaml[ExpenseIt#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]  
  
3. <span data-ttu-id="a43db-241">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a43db-241">Build and run the application.</span></span> 
  
    > [!NOTE]
    >  <span data-ttu-id="a43db-242">Pokud dojde k chybě <xref:System.Windows.Controls.DataGrid> nebyl nalezen nebo neexistuje, ujistěte se, že cílem vašeho projektu je .NET Framework 4 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="a43db-242">If you get an error that the <xref:System.Windows.Controls.DataGrid> was not found or does not exist, make sure that your project targets the .NET Framework 4 or later.</span></span> <span data-ttu-id="a43db-243">Další informace najdete v tématu [postupy: cílení na verzi rozhraní .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span><span class="sxs-lookup"><span data-stu-id="a43db-243">For more information, see [How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span> 
  
4. <span data-ttu-id="a43db-244">Klikněte **zobrazení** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="a43db-244">Click the **View** button.</span></span> 
  
     <span data-ttu-id="a43db-245">Zobrazí se stránka sestavy výdajů.</span><span class="sxs-lookup"><span data-stu-id="a43db-245">The expense report page appears.</span></span> 
  
 <span data-ttu-id="a43db-246">Následující obrázek ukazuje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementy přidané do ExpenseReportPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="a43db-246">The following illustration shows the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements added to ExpenseReportPage.xaml.</span></span> <span data-ttu-id="a43db-247">Všimněte si, že je povolena back navigační tlačítko.</span><span class="sxs-lookup"><span data-stu-id="a43db-247">Notice that the back navigation button is enabled.</span></span> 
  
 <span data-ttu-id="a43db-248">![Snímek obrazovky ExpenseIt –](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png "GettingStartedFigure4")</span><span class="sxs-lookup"><span data-stu-id="a43db-248">![ExpenseIt sample screen shot](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png "GettingStartedFigure4")</span></span>  
  
## <a name="styling-controls"></a><span data-ttu-id="a43db-249">Ovládací prvky stylů</span><span class="sxs-lookup"><span data-stu-id="a43db-249">Styling controls</span></span>  
 <span data-ttu-id="a43db-250">Vzhled různé prvky může být často stejný pro všechny elementy v stejného typu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a43db-250">The appearance of various elements can often be the same for all elements of the same type in a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span></span> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]<span data-ttu-id="a43db-251">používá styly vzhledy opakovaně použitelné napříč více elementů.</span><span class="sxs-lookup"><span data-stu-id="a43db-251"> uses styles to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="a43db-252">– Opětovné použití stylů umožňuje zjednodušit [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] vytváření a správu.</span><span class="sxs-lookup"><span data-stu-id="a43db-252">The reusability of styles helps to simplify [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] creation and management.</span></span> <span data-ttu-id="a43db-253">Další informace o styly najdete v tématu [stylů a ukázka](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="a43db-253">For more information about styles, see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span> <span data-ttu-id="a43db-254">Tato část nahradí za element atributy, které byly definovány v předchozích krocích se styly.</span><span class="sxs-lookup"><span data-stu-id="a43db-254">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span> 
  
1. <span data-ttu-id="a43db-255">Otevřete Application.xaml nebo App.xaml.</span><span class="sxs-lookup"><span data-stu-id="a43db-255">Open Application.xaml or App.xaml.</span></span> 
  
2. <span data-ttu-id="a43db-256">Přidejte následující XAML mezi <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> značky:</span><span class="sxs-lookup"><span data-stu-id="a43db-256">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>  
  
    [!code-xaml[ExpenseIt#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]  
  
     <span data-ttu-id="a43db-257">To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] přidá následující styly:</span><span class="sxs-lookup"><span data-stu-id="a43db-257">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] adds the following styles:</span></span>  
  
    -  <span data-ttu-id="a43db-258">`headerTextStyle`: Chcete-li formát názvu stránky <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="a43db-258">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span> 
  
    -  <span data-ttu-id="a43db-259">`labelStyle`: K formátování <xref:System.Windows.Controls.Label> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="a43db-259">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span> 
  
    -  <span data-ttu-id="a43db-260">`columnHeaderStyle`: K formátování <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span><span class="sxs-lookup"><span data-stu-id="a43db-260">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span> 
  
    -  <span data-ttu-id="a43db-261">`listHeaderStyle`: K formátování záhlaví seznamu <xref:System.Windows.Controls.Border> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="a43db-261">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span> 
  
    -  <span data-ttu-id="a43db-262">`listHeaderTextStyle`: K formátování záhlaví seznamu <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="a43db-262">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span> 
  
    -  <span data-ttu-id="a43db-263">`buttonStyle`: K formátování <xref:System.Windows.Controls.Button> na ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="a43db-263">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on ExpenseItHome.xaml.</span></span> 
  
     <span data-ttu-id="a43db-264">Všimněte si, že stylů jsou prostředky a podřízené objekty <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> element vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a43db-264">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="a43db-265">V tomto umístění stylů platí pro všechny elementy v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a43db-265">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="a43db-266">Příklad použití prostředků v [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] aplikace, najdete v části [prostředky aplikace použijte](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md).</span><span class="sxs-lookup"><span data-stu-id="a43db-266">For an example of using resources in a [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] application, see [Use Application Resources](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md).</span></span> 
  
3. <span data-ttu-id="a43db-267">Otevřete ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="a43db-267">Open ExpenseItHome.xaml.</span></span> 
  
4. <span data-ttu-id="a43db-268">Nahraďte všechno mezi <xref:System.Windows.Controls.Grid> prvky s následující XAML.</span><span class="sxs-lookup"><span data-stu-id="a43db-268">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML.</span></span> 
  
    [!code-xaml[ExpenseIt#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]  
  
     <span data-ttu-id="a43db-269">Vlastnosti, jako <xref:System.Windows.VerticalAlignment> a <xref:System.Windows.Media.FontFamily> které definují, jak vypadá každý ovládací prvek se odeberou a nahrazuje použití stylů.</span><span class="sxs-lookup"><span data-stu-id="a43db-269">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="a43db-270">Například `headerTextStyle` se použije pro "Zobrazení vyúčtování" <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="a43db-270">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span> 
  
5. <span data-ttu-id="a43db-271">Otevřete ExpenseReportPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="a43db-271">Open ExpenseReportPage.xaml.</span></span> 
  
6. <span data-ttu-id="a43db-272">Nahraďte všechno mezi <xref:System.Windows.Controls.Grid> prvky s následující XAML.</span><span class="sxs-lookup"><span data-stu-id="a43db-272">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML.</span></span> 
  
    [!code-xaml[ExpenseIt#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]  
  
     <span data-ttu-id="a43db-273">Tento postup přidá stylů pro <xref:System.Windows.Controls.Label> a <xref:System.Windows.Controls.Border> elementy.</span><span class="sxs-lookup"><span data-stu-id="a43db-273">This adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span> 
  
7. <span data-ttu-id="a43db-274">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a43db-274">Build and run the application.</span></span> 
  
     <span data-ttu-id="a43db-275">Po přidání [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] v této části aplikace vypadá stejně jako předtím aktualizace se styly.</span><span class="sxs-lookup"><span data-stu-id="a43db-275">After adding the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] in this section, the application looks the same as it did before being updated with styles.</span></span> 
  
## <a name="binding-data-to-a-control"></a><span data-ttu-id="a43db-276">Vazba dat k ovládacímu prvku</span><span class="sxs-lookup"><span data-stu-id="a43db-276">Binding data to a control</span></span>  
 <span data-ttu-id="a43db-277">V této části vytvoříte [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] data, která je vázána na různé ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="a43db-277">In this section, you create the [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] data that is bound to various controls.</span></span> 
  
1. <span data-ttu-id="a43db-278">Otevřete ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="a43db-278">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="a43db-279">Po otevření <xref:System.Windows.Controls.Grid> elementu, přidejte následující XAML pro vytvoření <xref:System.Windows.Data.XmlDataProvider> obsahující data pro každou osobu.</span><span class="sxs-lookup"><span data-stu-id="a43db-279">After the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person.</span></span> 
  
     <span data-ttu-id="a43db-280">Data je vytvořen jako <xref:System.Windows.Controls.Grid> prostředků.</span><span class="sxs-lookup"><span data-stu-id="a43db-280">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="a43db-281">Obvykle to by načíst jako soubor, ale pro zjednodušení je přidat data vložené.</span><span class="sxs-lookup"><span data-stu-id="a43db-281">Normally this would be loaded as a file, but for simplicity the data is added inline.</span></span> 
  
    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xaml[ExpenseIt#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]  
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
3. <span data-ttu-id="a43db-282">V <xref:System.Windows.Controls.Grid> prostředků, přidejte následující <xref:System.Windows.DataTemplate>, který definuje, jak zobrazit data v <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="a43db-282">In the <xref:System.Windows.Controls.Grid> resource, add the following <xref:System.Windows.DataTemplate>, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="a43db-283">Další informace o šablonách dat najdete v tématu [přehled Ukázka dat](../../../../docs/framework/wpf/data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a43db-283">For more information about data templates, see [Data Templating Overview](../../../../docs/framework/wpf/data/data-templating-overview.md).</span></span> 
  
    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xaml[ExpenseIt#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]  
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
4. <span data-ttu-id="a43db-284">Nahradit existující <xref:System.Windows.Controls.ListBox> s následující XAML.</span><span class="sxs-lookup"><span data-stu-id="a43db-284">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML.</span></span> 
  
    [!code-xaml[ExpenseIt#25](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]  
  
     <span data-ttu-id="a43db-285">Tato XAML váže <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost <xref:System.Windows.Controls.ListBox> ke zdroji dat a použije šablona dat jako <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span><span class="sxs-lookup"><span data-stu-id="a43db-285">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span> 
  
## <a name="connecting-data-to-controls"></a><span data-ttu-id="a43db-286">Připojení dat k ovládacím prvkům</span><span class="sxs-lookup"><span data-stu-id="a43db-286">Connecting data to controls</span></span>  
 <span data-ttu-id="a43db-287">V této části můžete psát kód, který načte aktuální položky, který je vybrán v seznamu uživatelů na stránce ExpenseItHome.xaml a předá jeho odkaz na konstruktoru `ExpenseReportPage` během vytváření instancí.</span><span class="sxs-lookup"><span data-stu-id="a43db-287">In this section, you write the code that retrieves the current item that is selected in the list of people on the ExpenseItHome.xaml page, and passes its reference to the constructor of `ExpenseReportPage` during instantiation.</span></span> <span data-ttu-id="a43db-288">`ExpenseReportPage`Nastaví jeho kontext dat s předaný položky, které je ovládací prvky určené ve ExpenseReportPage.xaml vytvoří vazbu k.</span><span class="sxs-lookup"><span data-stu-id="a43db-288">`ExpenseReportPage` sets its data context with the passed item, which is what the controls defined in ExpenseReportPage.xaml will bind to.</span></span> 
  
1. <span data-ttu-id="a43db-289">Otevřete ExpenseReportPage.xaml.vb nebo ExpenseReportPage.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="a43db-289">Open ExpenseReportPage.xaml.vb or ExpenseReportPage.xaml.cs.</span></span> 
  
2. <span data-ttu-id="a43db-290">Přidejte konstruktor, který přebírá objekt, abyste mohli předat data sestavy výdajů vybrané osoby.</span><span class="sxs-lookup"><span data-stu-id="a43db-290">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span> 
  
    [!code-csharp[ExpenseIt#26](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]  
  
3. <span data-ttu-id="a43db-291">Otevřete ExpenseItHome.xaml.vb nebo ExpenseItHome.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="a43db-291">Open ExpenseItHome.xaml.vb or ExpenseItHome.xaml.cs.</span></span> 
  
4. <span data-ttu-id="a43db-292">Změna <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužné rutiny události pro volání konstruktoru new předávání dat sestavy výdajů vybrané osoby.</span><span class="sxs-lookup"><span data-stu-id="a43db-292">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span> 
  
    [!code-csharp[ExpenseIt#27](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]  
  
## <a name="styling-data-with-data-templates"></a><span data-ttu-id="a43db-293">Data stylů se šablonami dat</span><span class="sxs-lookup"><span data-stu-id="a43db-293">Styling data with data templates</span></span>  
 <span data-ttu-id="a43db-294">V této části můžete aktualizovat [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pro každou položku v datech vázaný seznamy pomocí šablon data.</span><span class="sxs-lookup"><span data-stu-id="a43db-294">In this section, you update the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] for each item in the data bound lists by using data templates.</span></span> 
  
1. <span data-ttu-id="a43db-295">Otevřete ExpenseReportPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="a43db-295">Open ExpenseReportPage.xaml.</span></span> 
  
2. <span data-ttu-id="a43db-296">Vytvoření vazby obsah "Název" a "Oddělení" <xref:System.Windows.Controls.Label> vlastnost zdroje elementy, aby příslušná data.</span><span class="sxs-lookup"><span data-stu-id="a43db-296">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="a43db-297">Další informace o vazbě dat najdete v tématu [přehled vazby dat](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a43db-297">For more information about data binding, see [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span> 
  
    [!code-xaml[ExpenseIt#31](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]  
  
3. <span data-ttu-id="a43db-298">Po otevření <xref:System.Windows.Controls.Grid> elementu, přidejte následující data šablon, které definují způsob, jak zobrazit data sestavy výdajů.</span><span class="sxs-lookup"><span data-stu-id="a43db-298">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data.</span></span>  
    [!code-xaml[ExpenseIt#30](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]  
  
4. <span data-ttu-id="a43db-299">Používat šablony pro <xref:System.Windows.Controls.DataGrid> sloupce, které zobrazují nákladů data sestavy.</span><span class="sxs-lookup"><span data-stu-id="a43db-299">Apply the templates to the <xref:System.Windows.Controls.DataGrid> columns that display the expense report data.</span></span> 
  
    [!code-xaml[ExpenseIt#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]  
  
5. <span data-ttu-id="a43db-300">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a43db-300">Build and run the application.</span></span> 
  
6. <span data-ttu-id="a43db-301">Vyberte osoby a klikněte na **zobrazení** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="a43db-301">Select a person and click the **View** button.</span></span> 
  
 <span data-ttu-id="a43db-302">Následující obrázek znázorňuje obě stránky aplikace ExpenseIt – ovládací prvky, rozložení, styly, datové vazby a šablony dat použít.</span><span class="sxs-lookup"><span data-stu-id="a43db-302">The following illustration shows both pages of the ExpenseIt application with controls, layout, styles, data binding, and data templates applied.</span></span> 
  
 <span data-ttu-id="a43db-303">![Snímky obrazovky ukázkové ExpenseIt –](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png "GettingStartedFigure5")</span><span class="sxs-lookup"><span data-stu-id="a43db-303">![ExpenseIt sample screen shots](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png "GettingStartedFigure5")</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="a43db-304">Doporučené postupy</span><span class="sxs-lookup"><span data-stu-id="a43db-304">Best practices</span></span>  
 <span data-ttu-id="a43db-305">Tato ukázka představuje konkrétní funkce WPF a v důsledku toho nedodrží osvědčené postupy pro vývoj aplikací.</span><span class="sxs-lookup"><span data-stu-id="a43db-305">This sample demonstrates a specific feature of WPF and, consequently, does not follow application development best practices.</span></span> <span data-ttu-id="a43db-306">Pro komplexní přehled [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] aplikace vývoj osvědčené postupy, podle potřeby najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="a43db-306">For comprehensive coverage of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] and the [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] application development best practices, see the following topics as appropriate:</span></span>  
  
-   <span data-ttu-id="a43db-307">Usnadnění – [usnadnění – doporučené postupy](../../../../docs/framework/ui-automation/accessibility-best-practices.md)</span><span class="sxs-lookup"><span data-stu-id="a43db-307">Accessibility - [Accessibility Best Practices](../../../../docs/framework/ui-automation/accessibility-best-practices.md)</span></span>  
  
-   <span data-ttu-id="a43db-308">Zabezpečení – [zabezpečení](../../../../docs/framework/wpf/security-wpf.md)</span><span class="sxs-lookup"><span data-stu-id="a43db-308">Security - [Security](../../../../docs/framework/wpf/security-wpf.md)</span></span>  
  
-   <span data-ttu-id="a43db-309">Lokalizace - [WPF globalizace a lokalizace – přehled](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)</span><span class="sxs-lookup"><span data-stu-id="a43db-309">Localization - [WPF Globalization and Localization Overview](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)</span></span>  
  
-   <span data-ttu-id="a43db-310">Výkon – [optimalizace výkonu aplikace WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)</span><span class="sxs-lookup"><span data-stu-id="a43db-310">Performance - [Optimizing WPF Application Performance](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)</span></span>  
  
## <a name="whats-next"></a><span data-ttu-id="a43db-311">Co je další</span><span class="sxs-lookup"><span data-stu-id="a43db-311">What's next</span></span>  
 <span data-ttu-id="a43db-312">Nyní máte několik technik k dispozici pro vytváření [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pomocí [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a43db-312">You now have a number of techniques at your disposal for creating a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] using [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span> <span data-ttu-id="a43db-313">Teď byste měli mít široký přehled o základní stavební bloky vázané na data [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="a43db-313">You should now have a broad understanding of the basic building blocks of a data-bound [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] application.</span></span> <span data-ttu-id="a43db-314">Toto téma je rozhodně není vyčerpávající, ale zpravidla nyní také mít smysl pro některé možnosti, které můžete zjistit, na vlastní nad rámec techniky v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="a43db-314">This topic is by no means exhaustive, but hopefully you also now have a sense of some of the possibilities you might discover on your own beyond the techniques in this topic.</span></span> 
  
 <span data-ttu-id="a43db-315">Další informace o modelech WPF architektura a programování najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="a43db-315">For more information about the WPF architecture and programming models, see the following topics:</span></span>  
  
-   [<span data-ttu-id="a43db-316">Architektura WPF</span><span class="sxs-lookup"><span data-stu-id="a43db-316">WPF Architecture</span></span>](../../../../docs/framework/wpf/advanced/wpf-architecture.md)  
  
-   [<span data-ttu-id="a43db-317">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="a43db-317">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
  
-   [<span data-ttu-id="a43db-318">Přehled vlastností závislosti</span><span class="sxs-lookup"><span data-stu-id="a43db-318">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
  
-   [<span data-ttu-id="a43db-319">Rozložení</span><span class="sxs-lookup"><span data-stu-id="a43db-319">Layout</span></span>](../../../../docs/framework/wpf/advanced/layout.md)  
  
 <span data-ttu-id="a43db-320">Další informace o vytváření aplikací najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="a43db-320">For more information about creating applications, see the following topics:</span></span>  
  
-   [<span data-ttu-id="a43db-321">Vývoj aplikací</span><span class="sxs-lookup"><span data-stu-id="a43db-321">Application Development</span></span>](../../../../docs/framework/wpf/app-development/index.md)  
  
-   [<span data-ttu-id="a43db-322">Ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="a43db-322">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)  
  
-   [<span data-ttu-id="a43db-323">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="a43db-323">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
  
-   [<span data-ttu-id="a43db-324">Grafika a multimédia</span><span class="sxs-lookup"><span data-stu-id="a43db-324">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)  
  
-   [<span data-ttu-id="a43db-325">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="a43db-325">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
  
## <a name="see-also"></a><span data-ttu-id="a43db-326">Viz také</span><span class="sxs-lookup"><span data-stu-id="a43db-326">See also</span></span>  
 [<span data-ttu-id="a43db-327">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="a43db-327">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="a43db-328">Přehled datových šablon</span><span class="sxs-lookup"><span data-stu-id="a43db-328">Data Templating Overview</span></span>](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [<span data-ttu-id="a43db-329">Sestavení aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="a43db-329">Building a WPF Application</span></span>](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [<span data-ttu-id="a43db-330">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="a43db-330">Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/styles-and-templates.md)
