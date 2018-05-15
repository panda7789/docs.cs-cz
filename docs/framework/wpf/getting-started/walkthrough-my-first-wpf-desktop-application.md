---
title: Vytvoření aplikace WPF v sadě Visual Studio
ms.date: 04/12/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ceb4d79bb88e41e62f3ee136b6beb3324b3dbd7
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a><span data-ttu-id="70d19-102">Návod: Můj první grafický subsystém WPF aplikace pracovní plochy</span><span class="sxs-lookup"><span data-stu-id="70d19-102">Walkthrough: My first WPF desktop application</span></span>

<span data-ttu-id="70d19-103">V tomto článku se dozvíte, jak vyvíjet jednoduchou aplikaci Windows Presentation Foundation (WPF), která obsahuje prvky, které jsou společné pro většinu grafického subsystému WPF aplikací: kód rozšiřitelné aplikace Markup Language (XAML), kódu, definice aplikace ovládací prvky, rozložení, datové vazby a stylů.</span><span class="sxs-lookup"><span data-stu-id="70d19-103">This article shows you how to develop a simple Windows Presentation Foundation (WPF) application that includes the elements that are common to most WPF applications: Extensible Application Markup Language (XAML) markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span>

<span data-ttu-id="70d19-104">Tento názorný postup obsahuje následující kroky:</span><span class="sxs-lookup"><span data-stu-id="70d19-104">This walkthrough includes the following steps:</span></span>

- <span data-ttu-id="70d19-105">Pomocí XAML můžete navrhnout vzhled aplikace uživatelské rozhraní (UI).</span><span class="sxs-lookup"><span data-stu-id="70d19-105">Use XAML to design the appearance of the application's user interface (UI).</span></span>

- <span data-ttu-id="70d19-106">Napište kód pro sestavení chování aplikace.</span><span class="sxs-lookup"><span data-stu-id="70d19-106">Write code to build the application's behavior.</span></span>

- <span data-ttu-id="70d19-107">Vytvořte definici aplikace ke správě aplikace.</span><span class="sxs-lookup"><span data-stu-id="70d19-107">Create an application definition to manage the application.</span></span>

- <span data-ttu-id="70d19-108">Přidání ovládacích prvků a vytvořte rozložení k vytvoření aplikace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="70d19-108">Add controls and create the layout to compose the application UI.</span></span>

- <span data-ttu-id="70d19-109">Vytvořte styly konzistentní vzhled uživatelského rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="70d19-109">Create styles for a consistent appearance throughout an application's UI.</span></span>

- <span data-ttu-id="70d19-110">Vytvoření vazby uživatelského rozhraní k datům pro naplnění rozhraní z dat i zachovat data a uživatelského rozhraní, které jsou synchronizovány.</span><span class="sxs-lookup"><span data-stu-id="70d19-110">Bind the UI to data to both populate the UI from data and keep the data and UI synchronized.</span></span>

<span data-ttu-id="70d19-111">Na konci průvodce budete mít vytvořené samostatné aplikace Windows, která umožňuje uživatelům zobrazit sestavy výdajů pro vybrané osoby.</span><span class="sxs-lookup"><span data-stu-id="70d19-111">By the end of the walkthrough, you'll have built a standalone Windows application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="70d19-112">Aplikace se skládá z několika grafického subsystému WPF stránek, které jsou hostované v okně prohlížeče stylu.</span><span class="sxs-lookup"><span data-stu-id="70d19-112">The application is composed of several WPF pages that are hosted in a browser-style window.</span></span>

> [!TIP]
> <span data-ttu-id="70d19-113">Ukázkový kód, který je použit k vytvoření tohoto návodu je k dispozici pro Visual Basic a C# na [Úvod do vytváření grafického subsystému WPF aplikací](http://go.microsoft.com/fwlink/?LinkID=160008).</span><span class="sxs-lookup"><span data-stu-id="70d19-113">The sample code that is used to build this walkthrough is available for both Visual Basic and C# at [Introduction to Building WPF Applications](http://go.microsoft.com/fwlink/?LinkID=160008).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="70d19-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="70d19-114">Prerequisites</span></span>

- <span data-ttu-id="70d19-115">Visual Studio 2012 nebo novější</span><span class="sxs-lookup"><span data-stu-id="70d19-115">Visual Studio 2012 or later</span></span>

<span data-ttu-id="70d19-116">Další informace o instalaci nejnovější verze sady Visual Studio najdete v tématu [instalaci sady Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="70d19-116">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="70d19-117">Vytvořte projekt aplikace</span><span class="sxs-lookup"><span data-stu-id="70d19-117">Create the application project</span></span>

<span data-ttu-id="70d19-118">Prvním krokem je vytvoření infrastrukturu aplikace, která zahrnuje definice aplikace, dvě stránky a bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="70d19-118">The first step is to create the application infrastructure, which includes an application definition, two pages, and an image.</span></span>

1. <span data-ttu-id="70d19-119">Vytvořte nový projekt aplikace WPF v jazyce Visual Basic a Visual C# s názvem **ExpenseIt –**:</span><span class="sxs-lookup"><span data-stu-id="70d19-119">Create a new WPF Application project in Visual Basic or Visual C# named **ExpenseIt**:</span></span>

   1. <span data-ttu-id="70d19-120">Otevřete Visual Studio a vyberte **soubor** > **nový** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="70d19-120">Open Visual Studio and select **File** > **New** > **Project**.</span></span>

      <span data-ttu-id="70d19-121">**Nový projekt** otevře se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="70d19-121">The **New Project** dialog opens.</span></span>

   2. <span data-ttu-id="70d19-122">V části **nainstalovaná** kategorie, rozbalte **Visual C#** nebo **jazyka Visual Basic** uzel a potom vyberte **Windows Classic Desktop**.</span><span class="sxs-lookup"><span data-stu-id="70d19-122">Under the **Installed** category, expand either the **Visual C#** or **Visual Basic** node, and then select **Windows Classic Desktop**.</span></span>

   3. <span data-ttu-id="70d19-123">Vyberte **aplikace WPF (rozhraní .NET Framework)** šablony.</span><span class="sxs-lookup"><span data-stu-id="70d19-123">Select the **WPF App (.NET Framework)** template.</span></span> <span data-ttu-id="70d19-124">Zadejte název **ExpenseIt –** a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="70d19-124">Enter the name **ExpenseIt** and then select **OK**.</span></span>

      ![Dialogové okno Nový projekt s vybrané aplikaci WPF](media/new-project-dialog.png)

      <span data-ttu-id="70d19-126">Visual Studio vytvoří projekt a otevře designer pro výchozím okně aplikace s názvem **MainWindow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="70d19-126">Visual Studio creates the project and opens the designer for the default application window named **MainWindow.xaml**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="70d19-127">Tento návod používá <xref:System.Windows.Controls.DataGrid> ovládací prvek, který je k dispozici v rozhraní .NET Framework 4 a novější.</span><span class="sxs-lookup"><span data-stu-id="70d19-127">This walkthrough uses the <xref:System.Windows.Controls.DataGrid> control that is available in the .NET Framework 4 and later.</span></span> <span data-ttu-id="70d19-128">Být jisti, že cílem vašeho projektu je .NET Framework 4 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="70d19-128">Be sure that your project targets the .NET Framework 4 or later.</span></span> <span data-ttu-id="70d19-129">Další informace najdete v tématu [postupy: cílení na verzi rozhraní .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span><span class="sxs-lookup"><span data-stu-id="70d19-129">For more information, see [How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span>

2. <span data-ttu-id="70d19-130">Otevřete *Application.xaml* (Visual Basic) nebo *App.xaml* (C#).</span><span class="sxs-lookup"><span data-stu-id="70d19-130">Open *Application.xaml* (Visual Basic) or *App.xaml* (C#).</span></span>

    <span data-ttu-id="70d19-131">Tento soubor XAML definuje aplikace WPF a všechny prostředky aplikace.</span><span class="sxs-lookup"><span data-stu-id="70d19-131">This XAML file defines a WPF application and any application resources.</span></span> <span data-ttu-id="70d19-132">Tento soubor můžete taky použít k určení rozhraní, které se automaticky zobrazí při spuštění aplikace; v takovém případě *MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="70d19-132">You also use this file to specify the UI that automatically shows when the application starts; in this case, *MainWindow.xaml*.</span></span>

    <span data-ttu-id="70d19-133">Vaše XAML by měl vypadat přibližně takto v jazyce Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="70d19-133">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#1_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    <span data-ttu-id="70d19-134">Nebo podobně jako v C#:</span><span class="sxs-lookup"><span data-stu-id="70d19-134">Or like this in C#:</span></span>

    [!code-xaml[ExpenseIt#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. <span data-ttu-id="70d19-135">Otevřete *MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="70d19-135">Open *MainWindow.xaml*.</span></span>

    <span data-ttu-id="70d19-136">Tento soubor XAML hlavní okno vaší aplikace a zobrazí obsah vytvořený v stránky.</span><span class="sxs-lookup"><span data-stu-id="70d19-136">This XAML file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="70d19-137"><xref:System.Windows.Window> Třídy definuje vlastnosti časového období, například jeho název, velikost nebo ikonu a zpracovává události, například zavření nebo skrytí.</span><span class="sxs-lookup"><span data-stu-id="70d19-137">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span>

4. <span data-ttu-id="70d19-138">Změna <xref:System.Windows.Window> elementu, který chcete <xref:System.Windows.Navigation.NavigationWindow>, jak je znázorněno v následujícím XAML:</span><span class="sxs-lookup"><span data-stu-id="70d19-138">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>, as shown in the following XAML:</span></span>

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   <span data-ttu-id="70d19-139">Tato aplikace přejde na jiný obsah, v závislosti na vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="70d19-139">This app navigates to different content depending on the user input.</span></span> <span data-ttu-id="70d19-140">To je důvod, proč hlavní <xref:System.Windows.Window> musí změnit tak, aby <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="70d19-140">This is why the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="70d19-141"><xref:System.Windows.Navigation.NavigationWindow> dědí všechny vlastnosti <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="70d19-141"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="70d19-142"><xref:System.Windows.Navigation.NavigationWindow> Element v souboru XAML vytvoří instanci <xref:System.Windows.Navigation.NavigationWindow> třídy.</span><span class="sxs-lookup"><span data-stu-id="70d19-142">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="70d19-143">Další informace najdete v tématu [navigační přehled](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="70d19-143">For more information, see [Navigation overview](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span></span>

5. <span data-ttu-id="70d19-144">Změnit na následující vlastnosti <xref:System.Windows.Navigation.NavigationWindow> element:</span><span class="sxs-lookup"><span data-stu-id="70d19-144">Change the following properties on the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>

    - <span data-ttu-id="70d19-145">Nastavte <xref:System.Windows.Window.Title%2A> vlastnost ExpenseIt "–".</span><span class="sxs-lookup"><span data-stu-id="70d19-145">Set the <xref:System.Windows.Window.Title%2A> property to "ExpenseIt".</span></span>

    - <span data-ttu-id="70d19-146">Nastavte <xref:System.Windows.FrameworkElement.Width%2A> vlastnost na 500 pixelů.</span><span class="sxs-lookup"><span data-stu-id="70d19-146">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span>

    - <span data-ttu-id="70d19-147">Nastavte <xref:System.Windows.FrameworkElement.Height%2A> vlastnost 350 pixelů.</span><span class="sxs-lookup"><span data-stu-id="70d19-147">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span>

    - <span data-ttu-id="70d19-148">Odeberte <xref:System.Windows.Controls.Grid> prvky mezi <xref:System.Windows.Navigation.NavigationWindow> značky.</span><span class="sxs-lookup"><span data-stu-id="70d19-148">Remove the <xref:System.Windows.Controls.Grid> elements between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span>

    <span data-ttu-id="70d19-149">Vaše XAML by měl vypadat přibližně takto v jazyce Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="70d19-149">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#2_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    <span data-ttu-id="70d19-150">Nebo podobně jako v C#:</span><span class="sxs-lookup"><span data-stu-id="70d19-150">Or like this in C#:</span></span>

    [!code-xaml[ExpenseIt#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

6. <span data-ttu-id="70d19-151">Otevřete *MainWindow.xaml.vb* nebo *MainWindow.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="70d19-151">Open *MainWindow.xaml.vb* or *MainWindow.xaml.cs*.</span></span>

    <span data-ttu-id="70d19-152">Tento soubor je soubor kódu, který obsahuje kód pro zpracování události deklarované v *MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="70d19-152">This file is a code-behind file that contains code to handle the events declared in *MainWindow.xaml*.</span></span> <span data-ttu-id="70d19-153">Tento soubor obsahuje konkrétní třídu pro okno definované v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="70d19-153">This file contains a partial class for the window defined in XAML.</span></span>

7. <span data-ttu-id="70d19-154">Pokud používáte C#, změňte `MainWindow` odvozena od třídy <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="70d19-154">If you are using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="70d19-155">(V jazyce Visual Basic tomu automaticky dojde při změně okna v jazyce XAML.)</span><span class="sxs-lookup"><span data-stu-id="70d19-155">(In Visual Basic, this happens automatically when you change the window in XAML.)</span></span>

   <span data-ttu-id="70d19-156">Váš kód by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="70d19-156">Your code should look like this:</span></span>

   [!code-csharp[ExpenseIt#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
   [!code-vb[ExpenseIt#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]

   > [!TIP]
   > <span data-ttu-id="70d19-157">Můžete přepínat jazyk kódu ukázkový kód mezi C# a Visual Basic v **jazyk** rozevíracího seznamu v pravé horní části tohoto článku.</span><span class="sxs-lookup"><span data-stu-id="70d19-157">You can toggle the code language of the sample code between C# and Visual Basic in the **Language** drop-down on the upper right side of this article.</span></span>

## <a name="add-files-to-the-application"></a><span data-ttu-id="70d19-158">Přidání souborů do aplikace</span><span class="sxs-lookup"><span data-stu-id="70d19-158">Add files to the application</span></span>

<span data-ttu-id="70d19-159">V této části přidáte dvě stránky a bitovou kopii do aplikace.</span><span class="sxs-lookup"><span data-stu-id="70d19-159">In this section, you'll add two pages and an image to the application.</span></span>

1. <span data-ttu-id="70d19-160">Do projektu přidejte novou stránku WPF a pojmenujte ji *ExpenseItHome.xaml*:</span><span class="sxs-lookup"><span data-stu-id="70d19-160">Add a new WPF page to the project, and name it *ExpenseItHome.xaml*:</span></span>

   1. <span data-ttu-id="70d19-161">V **Průzkumníku řešení**, klikněte pravým tlačítkem na **ExpenseIt –** uzel projektu a zvolte **přidat** > **stránky**.</span><span class="sxs-lookup"><span data-stu-id="70d19-161">In **Solution Explorer**, right-click on the **ExpenseIt** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="70d19-162">V **přidat novou položku** dialogové okno, **stránky (WPF)** šablony je již vybrána.</span><span class="sxs-lookup"><span data-stu-id="70d19-162">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="70d19-163">Zadejte název **ExpenseItHome**a potom vyberte **přidat**.</span><span class="sxs-lookup"><span data-stu-id="70d19-163">Enter the name **ExpenseItHome**, and then select **Add**.</span></span>

    <span data-ttu-id="70d19-164">Tato stránka je první stránka, která se zobrazí, když je aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="70d19-164">This page is the first page that's displayed when the application is launched.</span></span> <span data-ttu-id="70d19-165">Zobrazí seznam uživatelů a vyberte, chcete-li zobrazit sestavu výdajů pro.</span><span class="sxs-lookup"><span data-stu-id="70d19-165">It will show a list of people to select from, to show an expense report for.</span></span>

2. <span data-ttu-id="70d19-166">Otevřete *ExpenseItHome.xaml*.</span><span class="sxs-lookup"><span data-stu-id="70d19-166">Open *ExpenseItHome.xaml*.</span></span>

3. <span data-ttu-id="70d19-167">Nastavte <xref:System.Windows.Controls.Page.Title%2A> k "ExpenseIt – - domovské".</span><span class="sxs-lookup"><span data-stu-id="70d19-167">Set the <xref:System.Windows.Controls.Page.Title%2A> to "ExpenseIt - Home".</span></span>

    <span data-ttu-id="70d19-168">Vaše XAML by měl vypadat přibližně takto v jazyce Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="70d19-168">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#6_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    <span data-ttu-id="70d19-169">Nebo to v jazyce C#:</span><span class="sxs-lookup"><span data-stu-id="70d19-169">Or this in C#:</span></span>

    [!code-xaml[ExpenseIt#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

4. <span data-ttu-id="70d19-170">Otevřete *MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="70d19-170">Open *MainWindow.xaml*.</span></span>

5. <span data-ttu-id="70d19-171">Nastavte <xref:System.Windows.Navigation.NavigationWindow.Source%2A> vlastnost <xref:System.Windows.Navigation.NavigationWindow> na "ExpenseItHome.xaml".</span><span class="sxs-lookup"><span data-stu-id="70d19-171">Set the <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property on the <xref:System.Windows.Navigation.NavigationWindow> to "ExpenseItHome.xaml".</span></span>

    <span data-ttu-id="70d19-172">Nastaví tato *ExpenseItHome.xaml* na první stránce otevřelo při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="70d19-172">This sets *ExpenseItHome.xaml* to be the first page opened when the application starts.</span></span> <span data-ttu-id="70d19-173">Vaše XAML by měl vypadat přibližně takto v jazyce Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="70d19-173">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#7_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    <span data-ttu-id="70d19-174">Nebo to v jazyce C#:</span><span class="sxs-lookup"><span data-stu-id="70d19-174">Or this in C#:</span></span>

    [!code-xaml[ExpenseIt#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > <span data-ttu-id="70d19-175">Můžete také nastavit **zdroj** vlastnost **různé** kategorii **vlastnosti** okno.</span><span class="sxs-lookup"><span data-stu-id="70d19-175">You can also set the **Source** property in the **Miscellaneous** category of the **Properties** window.</span></span>
   >
   > ![Zdrojová vlastnost ve vlastnosti – okno](media/properties-source.png)

6. <span data-ttu-id="70d19-177">Do projektu přidejte další novou stránku grafického subsystému WPF a pojmenujte ji *ExpenseReportPage.xaml*::</span><span class="sxs-lookup"><span data-stu-id="70d19-177">Add another new WPF page to the project, and name it *ExpenseReportPage.xaml*::</span></span>

   1. <span data-ttu-id="70d19-178">V **Průzkumníku řešení**, klikněte pravým tlačítkem na **ExpenseIt –** uzel projektu a zvolte **přidat** > **stránky**.</span><span class="sxs-lookup"><span data-stu-id="70d19-178">In **Solution Explorer**, right-click on the **ExpenseIt** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="70d19-179">V **přidat novou položku** dialogové okno, **stránky (WPF)** šablony je již vybrána.</span><span class="sxs-lookup"><span data-stu-id="70d19-179">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="70d19-180">Zadejte název **ExpenseReportPage**a potom vyberte **přidat**.</span><span class="sxs-lookup"><span data-stu-id="70d19-180">Enter the name **ExpenseReportPage**, and then select **Add**.</span></span>

    <span data-ttu-id="70d19-181">Tato stránka se zobrazí vyúčtování pro osobě, která je vybrána na **ExpenseItHome** stránky.</span><span class="sxs-lookup"><span data-stu-id="70d19-181">This page will show the expense report for the person that is selected on the **ExpenseItHome** page.</span></span>

7. <span data-ttu-id="70d19-182">Otevřete *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="70d19-182">Open *ExpenseReportPage.xaml*.</span></span>

8. <span data-ttu-id="70d19-183">Nastavte <xref:System.Windows.Controls.Page.Title%2A> k "ExpenseIt – - zobrazení výdajů".</span><span class="sxs-lookup"><span data-stu-id="70d19-183">Set the <xref:System.Windows.Controls.Page.Title%2A> to "ExpenseIt - View Expense".</span></span>

    <span data-ttu-id="70d19-184">Vaše XAML by měl vypadat přibližně takto v jazyce Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="70d19-184">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#4_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    <span data-ttu-id="70d19-185">Nebo to v jazyce C#:</span><span class="sxs-lookup"><span data-stu-id="70d19-185">Or this in C#:</span></span>

    [!code-xaml[ExpenseIt#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

9. <span data-ttu-id="70d19-186">Otevřete *ExpenseItHome.xaml.vb* a *ExpenseReportPage.xaml.vb*, nebo *ExpenseItHome.xaml.cs* a *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="70d19-186">Open *ExpenseItHome.xaml.vb* and *ExpenseReportPage.xaml.vb*, or *ExpenseItHome.xaml.cs* and *ExpenseReportPage.xaml.cs*.</span></span>

    <span data-ttu-id="70d19-187">Když vytvoříte nový soubor stránky, Visual Studio automaticky vytvoří *kódu* souboru.</span><span class="sxs-lookup"><span data-stu-id="70d19-187">When you create a new Page file, Visual Studio automatically creates a *code-behind* file.</span></span> <span data-ttu-id="70d19-188">Tyto soubory kódu zpracování logiky reagovat na vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="70d19-188">These code-behind files handle the logic for responding to user input.</span></span>

    <span data-ttu-id="70d19-189">Váš kód by měl vypadat takto pro **ExpenseItHome**:</span><span class="sxs-lookup"><span data-stu-id="70d19-189">Your code should look like this for **ExpenseItHome**:</span></span>

    [!code-csharp[ExpenseIt#2_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
    [!code-vb[ExpenseIt#2_5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    <span data-ttu-id="70d19-190">A takto pro **ExpenseReportPage**:</span><span class="sxs-lookup"><span data-stu-id="70d19-190">And like this for **ExpenseReportPage**:</span></span>

    [!code-csharp[ExpenseIt#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
    [!code-vb[ExpenseIt#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

10. <span data-ttu-id="70d19-191">Přidání image s názvem *watermark.png* do projektu.</span><span class="sxs-lookup"><span data-stu-id="70d19-191">Add an image named *watermark.png* to the project.</span></span> <span data-ttu-id="70d19-192">Můžete vytvořit vlastní image, zkopírujte soubor z ukázkového kódu nebo jim [zde](https://github.com/dotnet/docs/blob/master/docs/framework/wpf/getting-started/media/watermark.png).</span><span class="sxs-lookup"><span data-stu-id="70d19-192">You can create your own image, copy the file from the sample code, or get it [here](https://github.com/dotnet/docs/blob/master/docs/framework/wpf/getting-started/media/watermark.png).</span></span>

   1. <span data-ttu-id="70d19-193">Klikněte pravým tlačítkem na uzel projektu a vyberte **přidat** > **existující položka**, nebo stiskněte klávesu **Shift**+**Alt** + **A**.</span><span class="sxs-lookup"><span data-stu-id="70d19-193">Right-click on the project node and select **Add** > **Existing Item**, or press **Shift**+**Alt**+**A**.</span></span>

   2. <span data-ttu-id="70d19-194">V **přidat existující položku** dialogové okno, přejděte k souboru bitové kopie, kterou chcete použít a potom vyberte **přidat**.</span><span class="sxs-lookup"><span data-stu-id="70d19-194">In the **Add Existing Item** dialog, browse to the image file you want to use, and then select **Add**.</span></span>

## <a name="build-and-run-the-application"></a><span data-ttu-id="70d19-195">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="70d19-195">Build and run the application</span></span>

1. <span data-ttu-id="70d19-196">Sestavení a spuštění aplikace, stiskněte klávesu **F5** nebo vyberte **spustit ladění** z **ladění** nabídky.</span><span class="sxs-lookup"><span data-stu-id="70d19-196">To build and run the application, press **F5** or select **Start Debugging** from the **Debug** menu.</span></span>

    <span data-ttu-id="70d19-197">Následující obrázek znázorňuje aplikace s <xref:System.Windows.Navigation.NavigationWindow> tlačítka:</span><span class="sxs-lookup"><span data-stu-id="70d19-197">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons:</span></span>

    ![Snímek obrazovky ExpenseIt – ukázka](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png)

2. <span data-ttu-id="70d19-199">Zavřete aplikaci se vraťte do sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="70d19-199">Close the application to return to Visual Studio.</span></span>

## <a name="create-the-layout"></a><span data-ttu-id="70d19-200">Vytvoření rozložení</span><span class="sxs-lookup"><span data-stu-id="70d19-200">Create the layout</span></span>

<span data-ttu-id="70d19-201">Rozložení poskytuje seřazené způsob, jak umístit prvky uživatelského rozhraní a také spravuje velikost a umístění těchto elementů při změně velikosti uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="70d19-201">Layout provides an ordered way to place UI elements, and also manages the size and position of those elements when a UI is resized.</span></span> <span data-ttu-id="70d19-202">Obvykle vytvoříte rozložení s jedním z následujících rozložení ovládacích prvků:</span><span class="sxs-lookup"><span data-stu-id="70d19-202">You typically create a layout with one of the following layout controls:</span></span>

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.DockPanel>
- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.VirtualizingStackPanel>
- <xref:System.Windows.Controls.WrapPanel>

<span data-ttu-id="70d19-203">Každý z těchto prvků rozložení podporuje zvláštním typem rozložení pro její podřízené elementy.</span><span class="sxs-lookup"><span data-stu-id="70d19-203">Each of these layout controls supports a special type of layout for its child elements.</span></span> <span data-ttu-id="70d19-204">Stránky ExpenseIt – jde změnit, a každé stránce má prvky, které jsou uspořádány vodorovně a svisle u jiných prvků.</span><span class="sxs-lookup"><span data-stu-id="70d19-204">ExpenseIt pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="70d19-205">V důsledku toho <xref:System.Windows.Controls.Grid> je ideální rozložení elementu pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="70d19-205">Consequently, the <xref:System.Windows.Controls.Grid> is the ideal layout element for the application.</span></span>

> [!TIP]
> <span data-ttu-id="70d19-206">Další informace o <xref:System.Windows.Controls.Panel> elementy, najdete v části [přehled panelů](../../../../docs/framework/wpf/controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="70d19-206">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels overview](../../../../docs/framework/wpf/controls/panels-overview.md).</span></span> <span data-ttu-id="70d19-207">Další informace o rozložení najdete v tématu [rozložení](../../../../docs/framework/wpf/advanced/layout.md).</span><span class="sxs-lookup"><span data-stu-id="70d19-207">For more information about layout, see [Layout](../../../../docs/framework/wpf/advanced/layout.md).</span></span>

<span data-ttu-id="70d19-208">V části vytvoříte tabulku s jedním sloupcem s tři řádky a okraj 10 pixelů přidáním sloupce a řádku definice, které <xref:System.Windows.Controls.Grid> v *ExpenseItHome.xaml*.</span><span class="sxs-lookup"><span data-stu-id="70d19-208">In the section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in *ExpenseItHome.xaml*.</span></span>

1. <span data-ttu-id="70d19-209">Otevřete *ExpenseItHome.xaml*.</span><span class="sxs-lookup"><span data-stu-id="70d19-209">Open *ExpenseItHome.xaml*.</span></span>

2. <span data-ttu-id="70d19-210">Nastavte <xref:System.Windows.FrameworkElement.Margin%2A> vlastnost <xref:System.Windows.Controls.Grid> element "10,0,10,10", který odpovídá na levé straně, horní, pravé a dolní okraj:</span><span class="sxs-lookup"><span data-stu-id="70d19-210">Set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10", which corresponds to left, top, right and bottom margins:</span></span>

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > <span data-ttu-id="70d19-211">Můžete také nastavit **okraj** hodnoty ve **vlastnosti** okno, v části **rozložení** kategorie:</span><span class="sxs-lookup"><span data-stu-id="70d19-211">You can also set the **Margin** values in the **Properties** window, under the **Layout** category:</span></span>
   >
   > ![Okraj hodnoty vlastnosti – okno](media/properties-margin.png)

3. <span data-ttu-id="70d19-213">Přidejte následující XAML mezi <xref:System.Windows.Controls.Grid> značek k vytvoření definice řádků a sloupců:</span><span class="sxs-lookup"><span data-stu-id="70d19-213">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions:</span></span>

    [!code-xaml[ExpenseIt#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <span data-ttu-id="70d19-214"><xref:System.Windows.Controls.RowDefinition.Height%2A> Dvou řádků je nastaven na <xref:System.Windows.GridLength.Auto%2A>, což znamená, že se velikost řádky založit na obsah v řádcích.</span><span class="sxs-lookup"><span data-stu-id="70d19-214">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A>, which means that the rows are sized base on the content in the rows.</span></span> <span data-ttu-id="70d19-215">Výchozí hodnota <xref:System.Windows.Controls.RowDefinition.Height%2A> je <xref:System.Windows.GridUnitType.Star> nastavení velikosti, což znamená, že výška řádku je vyvážené podíl volné místo.</span><span class="sxs-lookup"><span data-stu-id="70d19-215">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row height is a weighted proportion of the available space.</span></span> <span data-ttu-id="70d19-216">Například pokud mají dva řádky <xref:System.Windows.Controls.RowDefinition.Height%2A> z "\*", každá má výška, který je polovinu dostupné místo.</span><span class="sxs-lookup"><span data-stu-id="70d19-216">For example if two rows each have a <xref:System.Windows.Controls.RowDefinition.Height%2A> of "\*", they each have a height that is half of the available space.</span></span>

    <span data-ttu-id="70d19-217">Vaše <xref:System.Windows.Controls.Grid> by teď měl vypadat jako následující XAML:</span><span class="sxs-lookup"><span data-stu-id="70d19-217">Your <xref:System.Windows.Controls.Grid> should now look like the following XAML:</span></span>

    [!code-xaml[ExpenseIt#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a><span data-ttu-id="70d19-218">Přidání ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="70d19-218">Add controls</span></span>

<span data-ttu-id="70d19-219">V této části aktualizujete domovské stránce uživatelského rozhraní, zobrazí se seznam osob, které může uživatel vybrat z zobrazíte vyúčtování pro.</span><span class="sxs-lookup"><span data-stu-id="70d19-219">In this section, you'll update the home page UI to show a list of people that a user can select from to show the expense report for.</span></span> <span data-ttu-id="70d19-220">Ovládací prvky jsou objekty uživatelského rozhraní, které umožňují uživatelům interakci s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="70d19-220">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="70d19-221">Další informace najdete v tématu [ovládací prvky](../../../../docs/framework/wpf/controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="70d19-221">For more information, see [Controls](../../../../docs/framework/wpf/controls/index.md).</span></span>

<span data-ttu-id="70d19-222">Pokud chcete vytvořit toto uživatelské rozhraní, přidáte následující elementy pro *ExpenseItHome.xaml*:</span><span class="sxs-lookup"><span data-stu-id="70d19-222">To create this UI, you'll add the following elements to *ExpenseItHome.xaml*:</span></span>

- <span data-ttu-id="70d19-223"><xref:System.Windows.Controls.ListBox> (pro seznam lidí, kteří).</span><span class="sxs-lookup"><span data-stu-id="70d19-223"><xref:System.Windows.Controls.ListBox> (for the list of people).</span></span>
- <span data-ttu-id="70d19-224"><xref:System.Windows.Controls.Label> (pro hlavičku seznamu).</span><span class="sxs-lookup"><span data-stu-id="70d19-224"><xref:System.Windows.Controls.Label> (for the list header).</span></span>
- <span data-ttu-id="70d19-225"><xref:System.Windows.Controls.Button> (Chcete-li kliknutím zobrazíte vyúčtování osoby, který je vybraný v seznamu).</span><span class="sxs-lookup"><span data-stu-id="70d19-225"><xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span>

<span data-ttu-id="70d19-226">Každý ovládací prvek je umístěn v řádek <xref:System.Windows.Controls.Grid> nastavením <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> přidružená vlastnost.</span><span class="sxs-lookup"><span data-stu-id="70d19-226">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="70d19-227">Další informace o přidružené vlastnosti najdete v tématu [připojen přehled vlastností](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="70d19-227">For more information about attached properties, see [Attached Properties Overview](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).</span></span>

1. <span data-ttu-id="70d19-228">Otevřete *ExpenseItHome.xaml*.</span><span class="sxs-lookup"><span data-stu-id="70d19-228">Open *ExpenseItHome.xaml*.</span></span>

2. <span data-ttu-id="70d19-229">Přidejte následující XAML někde mezi <xref:System.Windows.Controls.Grid> značky:</span><span class="sxs-lookup"><span data-stu-id="70d19-229">Add the following XAML somewhere between the <xref:System.Windows.Controls.Grid> tags:</span></span>

   [!code-xaml[ExpenseIt#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > <span data-ttu-id="70d19-230">Můžete také vytvořit ovládací prvky je přetáhnete z **sada nástrojů** okna do okna návrhu a pak nastavování jejich vlastností **vlastnosti** okno.</span><span class="sxs-lookup"><span data-stu-id="70d19-230">You can also create the controls by dragging them from the **Toolbox** window onto the design window, and then setting their properties in the **Properties** window.</span></span>

3. <span data-ttu-id="70d19-231">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="70d19-231">Build and run the application.</span></span>

<span data-ttu-id="70d19-232">Následující obrázek znázorňuje ovládací prvky, že kterou jste právě vytvořili:</span><span class="sxs-lookup"><span data-stu-id="70d19-232">The following illustration shows the controls you just created:</span></span>

![Snímek obrazovky ExpenseIt – ukázka](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png)

## <a name="add-an-image-and-a-title"></a><span data-ttu-id="70d19-234">Přidejte bitovou kopii a název</span><span class="sxs-lookup"><span data-stu-id="70d19-234">Add an image and a title</span></span>

<span data-ttu-id="70d19-235">V této části aktualizujete uživatelském rozhraní domovské stránky s bitovou kopii a název stránky.</span><span class="sxs-lookup"><span data-stu-id="70d19-235">In this section, you'll update the home page UI with an image and a page title.</span></span>

1. <span data-ttu-id="70d19-236">Otevřete *ExpenseItHome.xaml*.</span><span class="sxs-lookup"><span data-stu-id="70d19-236">Open *ExpenseItHome.xaml*.</span></span>

2. <span data-ttu-id="70d19-237">Přidejte jiný sloupec pro <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> s pevným <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 pixelů:</span><span class="sxs-lookup"><span data-stu-id="70d19-237">Add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels:</span></span>

    [!code-xaml[ExpenseIt#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]

3. <span data-ttu-id="70d19-238">Přidat další řádek, abyste <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, celkem čtyři řádky:</span><span class="sxs-lookup"><span data-stu-id="70d19-238">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, for a total of four rows:</span></span>

    [!code-xaml[ExpenseIt#11b](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]

4. <span data-ttu-id="70d19-239">Přesunout ovládacích prvků na druhý sloupec nastavením <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> vlastnost na hodnotu 1 v každé tři ovládacích prvků (ohraničení, ListBox a tlačítko).</span><span class="sxs-lookup"><span data-stu-id="70d19-239">Move the controls to the second column by setting the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property to 1 in each of the three controls (Border, ListBox, and Button).</span></span>

5. <span data-ttu-id="70d19-240">Přesunout dolů řádek, každý ovládací prvek zvyšování jeho <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> hodnoty 1.</span><span class="sxs-lookup"><span data-stu-id="70d19-240">Move each control down a row, by incrementing its <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> value by 1.</span></span>

   <span data-ttu-id="70d19-241">XAML pro ovládací prvky, tři nyní vypadat třeba takto:</span><span class="sxs-lookup"><span data-stu-id="70d19-241">The XAML for the three controls now looks like this:</span></span>

    [!code-xaml[ExpenseIt#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

6. <span data-ttu-id="70d19-242">Nastavte <xref:System.Windows.Controls.Panel.Background%2A> z <xref:System.Windows.Controls.Grid> jako *watermark.png* soubor obrázku, přidáním následující XAML někde mezi `<Grid>` a `<\/Grid>` značky:</span><span class="sxs-lookup"><span data-stu-id="70d19-242">Set the <xref:System.Windows.Controls.Panel.Background%2A> of the <xref:System.Windows.Controls.Grid> to be the *watermark.png* image file, by adding the following XAML somewhere between the `<Grid>` and `<\/Grid>` tags:</span></span>

    [!code-xaml[ExpenseIt#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

7. <span data-ttu-id="70d19-243">Před <xref:System.Windows.Controls.Border> elementu, přidejte <xref:System.Windows.Controls.Label> s obsahem "Zobrazení vyúčtování".</span><span class="sxs-lookup"><span data-stu-id="70d19-243">Before the <xref:System.Windows.Controls.Border> element, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report".</span></span> <span data-ttu-id="70d19-244">Toto je název stránky.</span><span class="sxs-lookup"><span data-stu-id="70d19-244">This is the title of the page.</span></span>

    [!code-xaml[ExpenseIt#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

8. <span data-ttu-id="70d19-245">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="70d19-245">Build and run the application.</span></span>

<span data-ttu-id="70d19-246">Následující obrázek znázorňuje, co jste právě přidali výsledky:</span><span class="sxs-lookup"><span data-stu-id="70d19-246">The following illustration shows the results of what you just added:</span></span>

![Snímek obrazovky ExpenseIt – ukázka](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png)

## <a name="add-code-to-handle-events"></a><span data-ttu-id="70d19-248">Přidat kód pro zpracování událostí</span><span class="sxs-lookup"><span data-stu-id="70d19-248">Add code to handle events</span></span>

1. <span data-ttu-id="70d19-249">Otevřete *ExpenseItHome.xaml*.</span><span class="sxs-lookup"><span data-stu-id="70d19-249">Open *ExpenseItHome.xaml*.</span></span>

2. <span data-ttu-id="70d19-250">Přidat <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužná rutina události <xref:System.Windows.Controls.Button> elementu.</span><span class="sxs-lookup"><span data-stu-id="70d19-250">Add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="70d19-251">Další informace najdete v tématu [postupy: vytvoření jednoduché události obslužná rutina](http://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480).</span><span class="sxs-lookup"><span data-stu-id="70d19-251">For more information, see [How to: Create a simple event handler](http://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480).</span></span>

    [!code-xaml[ExpenseIt#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

3. <span data-ttu-id="70d19-252">Otevřete *ExpenseItHome.xaml.vb* nebo *ExpenseItHome.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="70d19-252">Open *ExpenseItHome.xaml.vb* or *ExpenseItHome.xaml.cs*.</span></span>

4. <span data-ttu-id="70d19-253">Přidejte následující kód, který `ExpenseItHome` třída pro přidání tlačítka klikněte na obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="70d19-253">Add the following code to the `ExpenseItHome` class to add a button click event handler.</span></span> <span data-ttu-id="70d19-254">Obslužné rutiny události otevře **ExpenseReportPage** stránky.</span><span class="sxs-lookup"><span data-stu-id="70d19-254">The event handler opens the **ExpenseReportPage** page.</span></span>

    [!code-csharp[ExpenseIt#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a><span data-ttu-id="70d19-255">Vytvoření uživatelského rozhraní pro ExpenseReportPage</span><span class="sxs-lookup"><span data-stu-id="70d19-255">Create the UI for ExpenseReportPage</span></span>

<span data-ttu-id="70d19-256">*ExpenseReportPage.xaml* zobrazí vyúčtování pro osobě, která je vybrána na **ExpenseItHome** stránky.</span><span class="sxs-lookup"><span data-stu-id="70d19-256">*ExpenseReportPage.xaml* displays the expense report for the person that's selected on the **ExpenseItHome** page.</span></span> <span data-ttu-id="70d19-257">V této části budete ovládací prvky a vytvoření uživatelského rozhraní pro **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="70d19-257">In this section, you'll controls and create the UI for **ExpenseReportPage**.</span></span> <span data-ttu-id="70d19-258">Budete také přidat pozadí a barvy k různým elementům uživatelského rozhraní výplně.</span><span class="sxs-lookup"><span data-stu-id="70d19-258">You'll also add background and fill colors to the various UI elements.</span></span>

1. <span data-ttu-id="70d19-259">Otevřete *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="70d19-259">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="70d19-260">Přidejte následující XAML mezi <xref:System.Windows.Controls.Grid> značky:</span><span class="sxs-lookup"><span data-stu-id="70d19-260">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags:</span></span>

    [!code-xaml[ExpenseIt#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    <span data-ttu-id="70d19-261">Toto uživatelské rozhraní je podobná *ExpenseItHome.xaml*, s výjimkou v se zobrazí data sestavy <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="70d19-261">This UI is similar to *ExpenseItHome.xaml*, except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span>

3. <span data-ttu-id="70d19-262">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="70d19-262">Build and run the application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="70d19-263">Pokud dojde k chybě <xref:System.Windows.Controls.DataGrid> nebyl nalezen nebo neexistuje, ujistěte se, že cílem vašeho projektu je .NET Framework 4 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="70d19-263">If you get an error that the <xref:System.Windows.Controls.DataGrid> was not found or does not exist, make sure that your project targets the .NET Framework 4 or later.</span></span> <span data-ttu-id="70d19-264">Další informace najdete v tématu [postupy: cílení na verzi rozhraní .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span><span class="sxs-lookup"><span data-stu-id="70d19-264">For more information, see [How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span>

4. <span data-ttu-id="70d19-265">Vyberte **zobrazení** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="70d19-265">Select the **View** button.</span></span>

    <span data-ttu-id="70d19-266">Zobrazí se stránka sestavy výdajů.</span><span class="sxs-lookup"><span data-stu-id="70d19-266">The expense report page appears.</span></span> <span data-ttu-id="70d19-267">Všimněte si také, zda je povoleno back navigační tlačítko.</span><span class="sxs-lookup"><span data-stu-id="70d19-267">Also notice that the back navigation button is enabled.</span></span>

<span data-ttu-id="70d19-268">Následující obrázek znázorňuje prvky uživatelského rozhraní, které jsou přidány do *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="70d19-268">The following illustration shows the UI elements added to *ExpenseReportPage.xaml*.</span></span>

![Snímek obrazovky ExpenseIt – ukázka](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png)

## <a name="style-controls"></a><span data-ttu-id="70d19-270">Ovládací prvky stylu</span><span class="sxs-lookup"><span data-stu-id="70d19-270">Style controls</span></span>

<span data-ttu-id="70d19-271">Vzhled různé prvky mezi sebou, je často stejný pro všechny elementy stejného typu v uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="70d19-271">The appearance of various elements is often the same for all elements of the same type in a UI.</span></span> <span data-ttu-id="70d19-272">Uživatelské rozhraní používá [styly](../../../../docs/framework/wpf/controls/styling-and-templating.md) aby vzhledy opakovaně použitelné napříč více elementů.</span><span class="sxs-lookup"><span data-stu-id="70d19-272">UI uses [styles](../../../../docs/framework/wpf/controls/styling-and-templating.md) to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="70d19-273">– Opětovné použití stylů pomáhá zjednodušit XAML vytváření a správu.</span><span class="sxs-lookup"><span data-stu-id="70d19-273">The reusability of styles helps to simplify XAML creation and management.</span></span> <span data-ttu-id="70d19-274">Tato část nahradí za element atributy, které byly definovány v předchozích krocích se styly.</span><span class="sxs-lookup"><span data-stu-id="70d19-274">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span>

1. <span data-ttu-id="70d19-275">Otevřete *Application.xaml* nebo *App.xaml*.</span><span class="sxs-lookup"><span data-stu-id="70d19-275">Open *Application.xaml* or *App.xaml*.</span></span>

2. <span data-ttu-id="70d19-276">Přidejte následující XAML mezi <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> značky:</span><span class="sxs-lookup"><span data-stu-id="70d19-276">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>

    [!code-xaml[ExpenseIt#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    <span data-ttu-id="70d19-277">Tato XAML přidá následující styly:</span><span class="sxs-lookup"><span data-stu-id="70d19-277">This XAML adds the following styles:</span></span>

    - <span data-ttu-id="70d19-278">`headerTextStyle`: Chcete-li formát názvu stránky <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="70d19-278">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="70d19-279">`labelStyle`: K formátování <xref:System.Windows.Controls.Label> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="70d19-279">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span>

    - <span data-ttu-id="70d19-280">`columnHeaderStyle`: K formátování <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span><span class="sxs-lookup"><span data-stu-id="70d19-280">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span>

    - <span data-ttu-id="70d19-281">`listHeaderStyle`: K formátování záhlaví seznamu <xref:System.Windows.Controls.Border> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="70d19-281">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span>

    - <span data-ttu-id="70d19-282">`listHeaderTextStyle`: K formátování záhlaví seznamu <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="70d19-282">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="70d19-283">`buttonStyle`: K formátování <xref:System.Windows.Controls.Button> na ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="70d19-283">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on ExpenseItHome.xaml.</span></span>

    <span data-ttu-id="70d19-284">Všimněte si, že stylů jsou prostředky a podřízené objekty <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> element vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="70d19-284">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="70d19-285">V tomto umístění stylů platí pro všechny elementy v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="70d19-285">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="70d19-286">Příklad používání prostředků ve aplikace rozhraní .NET Framework, naleznete v části [prostředky aplikace použijte](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md).</span><span class="sxs-lookup"><span data-stu-id="70d19-286">For an example of using resources in a .NET Framework application, see [Use Application Resources](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md).</span></span>

3. <span data-ttu-id="70d19-287">Otevřete *ExpenseItHome.xaml*.</span><span class="sxs-lookup"><span data-stu-id="70d19-287">Open *ExpenseItHome.xaml*.</span></span>

4. <span data-ttu-id="70d19-288">Nahraďte všechno mezi <xref:System.Windows.Controls.Grid> prvky s následující XAML:</span><span class="sxs-lookup"><span data-stu-id="70d19-288">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    <span data-ttu-id="70d19-289">Vlastnosti, jako <xref:System.Windows.VerticalAlignment> a <xref:System.Windows.Media.FontFamily> které definují, jak vypadá každý ovládací prvek se odeberou a nahrazuje použití stylů.</span><span class="sxs-lookup"><span data-stu-id="70d19-289">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="70d19-290">Například `headerTextStyle` se použije pro "Zobrazení vyúčtování" <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="70d19-290">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span>

5. <span data-ttu-id="70d19-291">Otevřete *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="70d19-291">Open *ExpenseReportPage.xaml*.</span></span>

6. <span data-ttu-id="70d19-292">Nahraďte všechno mezi <xref:System.Windows.Controls.Grid> prvky s následující XAML:</span><span class="sxs-lookup"><span data-stu-id="70d19-292">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    <span data-ttu-id="70d19-293">Tento postup přidá stylů pro <xref:System.Windows.Controls.Label> a <xref:System.Windows.Controls.Border> elementy.</span><span class="sxs-lookup"><span data-stu-id="70d19-293">This adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span>

## <a name="bind-data-to-a-control"></a><span data-ttu-id="70d19-294">Vázání dat k ovládacímu prvku</span><span class="sxs-lookup"><span data-stu-id="70d19-294">Bind data to a control</span></span>

<span data-ttu-id="70d19-295">V této části vytvoříte data XML, který je vázaný na různé ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="70d19-295">In this section, you'll create the XML data that is bound to various controls.</span></span>

1. <span data-ttu-id="70d19-296">Otevřete *ExpenseItHome.xaml*.</span><span class="sxs-lookup"><span data-stu-id="70d19-296">Open *ExpenseItHome.xaml*.</span></span>

2. <span data-ttu-id="70d19-297">Po otevření <xref:System.Windows.Controls.Grid> elementu, přidejte následující XAML pro vytvoření <xref:System.Windows.Data.XmlDataProvider> obsahující data pro každou osobu:</span><span class="sxs-lookup"><span data-stu-id="70d19-297">After the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person:</span></span>

    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    <span data-ttu-id="70d19-298">Data je vytvořen jako <xref:System.Windows.Controls.Grid> prostředků.</span><span class="sxs-lookup"><span data-stu-id="70d19-298">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="70d19-299">Obvykle to by načíst jako soubor, ale pro zjednodušení je přidat data vložené.</span><span class="sxs-lookup"><span data-stu-id="70d19-299">Normally this would be loaded as a file, but for simplicity the data is added inline.</span></span>

3. <span data-ttu-id="70d19-300">V rámci `<Grid.Resources>` elementu, přidejte následující <xref:System.Windows.DataTemplate>, který definuje, jak zobrazit data v <xref:System.Windows.Controls.ListBox>:</span><span class="sxs-lookup"><span data-stu-id="70d19-300">Within the `<Grid.Resources>` element, add the following <xref:System.Windows.DataTemplate>, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>:</span></span>

    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    <span data-ttu-id="70d19-301">Další informace o šablonách dat najdete v tématu [přehled Ukázka dat](../../../../docs/framework/wpf/data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="70d19-301">For more information about data templates, see [Data templating overview](../../../../docs/framework/wpf/data/data-templating-overview.md).</span></span>

4. <span data-ttu-id="70d19-302">Nahradit existující <xref:System.Windows.Controls.ListBox> s následující XAML:</span><span class="sxs-lookup"><span data-stu-id="70d19-302">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#25](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    <span data-ttu-id="70d19-303">Tato XAML váže <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost <xref:System.Windows.Controls.ListBox> ke zdroji dat a použije šablona dat jako <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span><span class="sxs-lookup"><span data-stu-id="70d19-303">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span>

## <a name="connect-data-to-controls"></a><span data-ttu-id="70d19-304">Připojení dat k ovládacím prvkům</span><span class="sxs-lookup"><span data-stu-id="70d19-304">Connect data to controls</span></span>

<span data-ttu-id="70d19-305">Dále přidáte kód načíst název, který je vybrán na **ExpenseItHome** stránky a předejte ji do konstruktoru **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="70d19-305">Next, you'll add code to retrieve the name that's selected on the **ExpenseItHome** page and pass it to the constructor of **ExpenseReportPage**.</span></span> <span data-ttu-id="70d19-306">**ExpenseReportPage** nastaví jeho kontext dat s předaný položky, které je co ovládací prvky určené ve *ExpenseReportPage.xaml* vytvořit vazbu.</span><span class="sxs-lookup"><span data-stu-id="70d19-306">**ExpenseReportPage** sets its data context with the passed item, which is what the controls defined in *ExpenseReportPage.xaml* bind to.</span></span>

1. <span data-ttu-id="70d19-307">Otevřete *ExpenseReportPage.xaml.vb* nebo *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="70d19-307">Open *ExpenseReportPage.xaml.vb* or *ExpenseReportPage.xaml.cs*.</span></span>

2. <span data-ttu-id="70d19-308">Přidejte konstruktor, který přebírá objekt, abyste mohli předat data sestavy výdajů vybrané osoby.</span><span class="sxs-lookup"><span data-stu-id="70d19-308">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#26](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. <span data-ttu-id="70d19-309">Otevřete *ExpenseItHome.xaml.vb* nebo *ExpenseItHome.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="70d19-309">Open *ExpenseItHome.xaml.vb* or *ExpenseItHome.xaml.cs*.</span></span>

4. <span data-ttu-id="70d19-310">Změna <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužné rutiny události pro volání konstruktoru new předávání dat sestavy výdajů vybrané osoby.</span><span class="sxs-lookup"><span data-stu-id="70d19-310">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#27](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a><span data-ttu-id="70d19-311">Styl dat pomocí šablony dat</span><span class="sxs-lookup"><span data-stu-id="70d19-311">Style data with data templates</span></span>

<span data-ttu-id="70d19-312">V této části aktualizujete uživatelského rozhraní pro každou položku v seznamech vázané na data pomocí šablon data.</span><span class="sxs-lookup"><span data-stu-id="70d19-312">In this section, you'll update the UI for each item in the data-bound lists by using data templates.</span></span>

1. <span data-ttu-id="70d19-313">Otevřete *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="70d19-313">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="70d19-314">Vytvoření vazby obsah "Název" a "Oddělení" <xref:System.Windows.Controls.Label> vlastnost zdroje elementy, aby příslušná data.</span><span class="sxs-lookup"><span data-stu-id="70d19-314">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="70d19-315">Další informace o vazbě dat najdete v tématu [přehled vazby dat](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="70d19-315">For more information about data binding, see [Data binding overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>

    [!code-xaml[ExpenseIt#31](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. <span data-ttu-id="70d19-316">Po otevření <xref:System.Windows.Controls.Grid> elementu, přidejte následující data šablon, které definují způsob, jak zobrazit data sestavy výdajů:</span><span class="sxs-lookup"><span data-stu-id="70d19-316">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data:</span></span>

    [!code-xaml[ExpenseIt#30](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. <span data-ttu-id="70d19-317">Používat šablony pro <xref:System.Windows.Controls.DataGrid> sloupce, které zobrazují nákladů data sestavy.</span><span class="sxs-lookup"><span data-stu-id="70d19-317">Apply the templates to the <xref:System.Windows.Controls.DataGrid> columns that display the expense report data.</span></span>

    [!code-xaml[ExpenseIt#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. <span data-ttu-id="70d19-318">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="70d19-318">Build and run the application.</span></span>

6. <span data-ttu-id="70d19-319">Vyberte osoby a pak vyberte **zobrazení** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="70d19-319">Select a person and then select the **View** button.</span></span>

<span data-ttu-id="70d19-320">Následující obrázek znázorňuje obě stránky ExpenseIt – aplikace s ovládací prvky, rozložení, styly, vazby dat a dat šablony použít:</span><span class="sxs-lookup"><span data-stu-id="70d19-320">The following illustration shows both pages of the ExpenseIt application with controls, layout, styles, data binding, and data templates applied:</span></span>

![Snímky obrazovky ExpenseIt – ukázka](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png)

> [!NOTE]
> <span data-ttu-id="70d19-322">Tato ukázka ukazuje konkrétní funkce WPF a nemá použijte všechny osvědčené postupy pro takové věci, jako zabezpečení, lokalizace a usnadnění přístupu.</span><span class="sxs-lookup"><span data-stu-id="70d19-322">This sample demonstrates a specific feature of WPF and doesn't follow all best practices for things like security, localization, and accessibility.</span></span> <span data-ttu-id="70d19-323">Úplný přehled WPF a osvědčené postupy vývoj aplikací rozhraní .NET Framework najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="70d19-323">For comprehensive coverage of WPF and the .NET Framework application development best practices, see the following topics:</span></span>
>
> - [<span data-ttu-id="70d19-324">Usnadnění</span><span class="sxs-lookup"><span data-stu-id="70d19-324">Accessibility</span></span>](../../../../docs/framework/ui-automation/accessibility-best-practices.md)
>
> - [<span data-ttu-id="70d19-325">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="70d19-325">Security</span></span>](../../../../docs/framework/wpf/security-wpf.md)
>
> - [<span data-ttu-id="70d19-326">WPF globalizace a lokalizace</span><span class="sxs-lookup"><span data-stu-id="70d19-326">WPF globalization and localization</span></span>](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)
>
> - [<span data-ttu-id="70d19-327">Výkon WPF</span><span class="sxs-lookup"><span data-stu-id="70d19-327">WPF performance</span></span>](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a><span data-ttu-id="70d19-328">Další kroky</span><span class="sxs-lookup"><span data-stu-id="70d19-328">Next steps</span></span>

<span data-ttu-id="70d19-329">V tomto návodu jste se dozvěděli počet techniky pro vytvoření uživatelského rozhraní pomocí Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="70d19-329">In this walkthrough you learned a number of techniques for creating a UI using Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="70d19-330">Teď byste měli mít základní znalosti o stavební bloky vázané na data, aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="70d19-330">You should now have a basic understanding of the building blocks of a data-bound, .NET Framework application.</span></span> <span data-ttu-id="70d19-331">Další informace o modelech WPF architektura a programování najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="70d19-331">For more information about the WPF architecture and programming models, see the following topics:</span></span>

- [<span data-ttu-id="70d19-332">Architektura WPF</span><span class="sxs-lookup"><span data-stu-id="70d19-332">WPF architecture</span></span>](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
- [<span data-ttu-id="70d19-333">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="70d19-333">XAML overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="70d19-334">Přehled vlastností závislostí</span><span class="sxs-lookup"><span data-stu-id="70d19-334">Dependency properties overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
- [<span data-ttu-id="70d19-335">Rozložení</span><span class="sxs-lookup"><span data-stu-id="70d19-335">Layout</span></span>](../../../../docs/framework/wpf/advanced/layout.md)

<span data-ttu-id="70d19-336">Další informace o vytváření aplikací najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="70d19-336">For more information about creating applications, see the following topics:</span></span>

- [<span data-ttu-id="70d19-337">Vývoj aplikací</span><span class="sxs-lookup"><span data-stu-id="70d19-337">Application development</span></span>](../../../../docs/framework/wpf/app-development/index.md)
- [<span data-ttu-id="70d19-338">Ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="70d19-338">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)
- [<span data-ttu-id="70d19-339">Přehled vazba dat</span><span class="sxs-lookup"><span data-stu-id="70d19-339">Data binding overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [<span data-ttu-id="70d19-340">Grafika a multimédia</span><span class="sxs-lookup"><span data-stu-id="70d19-340">Graphics and multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)
- [<span data-ttu-id="70d19-341">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="70d19-341">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)

## <a name="see-also"></a><span data-ttu-id="70d19-342">Viz také</span><span class="sxs-lookup"><span data-stu-id="70d19-342">See also</span></span>

- [<span data-ttu-id="70d19-343">Přehled panelů</span><span class="sxs-lookup"><span data-stu-id="70d19-343">Panels overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
- [<span data-ttu-id="70d19-344">Ukázka dat – přehled</span><span class="sxs-lookup"><span data-stu-id="70d19-344">Data templating overview</span></span>](../../../../docs/framework/wpf/data/data-templating-overview.md)
- [<span data-ttu-id="70d19-345">Vytvoření aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="70d19-345">Build a WPF application</span></span>](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)
- [<span data-ttu-id="70d19-346">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="70d19-346">Styles and templates</span></span>](../../../../docs/framework/wpf/controls/styles-and-templates.md)
