---
title: Vytvoření aplikace WPF v sadě Visual Studio
ms.date: 10/26/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
author: mairaw
ms.author: mairaw
ms.custom: vs-dotnet
ms.openlocfilehash: b7ad8afbad212d5c79c9391bd9f6d1da7ff8fb28
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358182"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a><span data-ttu-id="824cc-102">Návod: Moje první desktopová aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="824cc-102">Walkthrough: My first WPF desktop application</span></span>

<span data-ttu-id="824cc-103">V tomto článku se dozvíte, jak vyvíjet jednoduchou aplikaci Windows Presentation Foundation (WPF), která obsahuje elementy, které jsou společné pro většinu aplikací WPF: Extensible Application Markup Language (XAML) značky, použití modelu code-behind, definice aplikací, ovládací prvky, rozložení, datové vazby a styly.</span><span class="sxs-lookup"><span data-stu-id="824cc-103">This article shows you how to develop a simple Windows Presentation Foundation (WPF) application that includes the elements that are common to most WPF applications: Extensible Application Markup Language (XAML) markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span>

<span data-ttu-id="824cc-104">Tento návod zahrnuje následující kroky:</span><span class="sxs-lookup"><span data-stu-id="824cc-104">This walkthrough includes the following steps:</span></span>

- <span data-ttu-id="824cc-105">Umožňuje navrhnout vzhled uživatelského rozhraní (UI) pro aplikace XAML.</span><span class="sxs-lookup"><span data-stu-id="824cc-105">Use XAML to design the appearance of the application's user interface (UI).</span></span>

- <span data-ttu-id="824cc-106">Napsání kódu pro sestavení chování aplikace.</span><span class="sxs-lookup"><span data-stu-id="824cc-106">Write code to build the application's behavior.</span></span>

- <span data-ttu-id="824cc-107">Vytvořte definici aplikace ke správě aplikace.</span><span class="sxs-lookup"><span data-stu-id="824cc-107">Create an application definition to manage the application.</span></span>

- <span data-ttu-id="824cc-108">Přidání ovládacích prvků a vytvořit rozložení k vytvoření uživatelského rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="824cc-108">Add controls and create the layout to compose the application UI.</span></span>

- <span data-ttu-id="824cc-109">Vytvoření styly pro konzistentní vzhled uživatelského rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="824cc-109">Create styles for a consistent appearance throughout an application's UI.</span></span>

- <span data-ttu-id="824cc-110">Svázat data pro naplnění uživatelského rozhraní z dat i chránit data a synchronizované uživatelské rozhraní uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="824cc-110">Bind the UI to data to both populate the UI from data and keep the data and UI synchronized.</span></span>

<span data-ttu-id="824cc-111">Na konci návodu budete sestavíte samostatnou aplikaci Windows, která umožňuje uživatelům zobrazit vyúčtování pro vybraného uživatele.</span><span class="sxs-lookup"><span data-stu-id="824cc-111">By the end of the walkthrough, you'll have built a standalone Windows application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="824cc-112">Aplikace se skládá z několika stránek WPF, které jsou hostované v okně prohlížeče – vizuální styl.</span><span class="sxs-lookup"><span data-stu-id="824cc-112">The application is composed of several WPF pages that are hosted in a browser-style window.</span></span>

> [!TIP]
> <span data-ttu-id="824cc-113">Ukázkový kód, který se používá k vytvoření tohoto návodu je k dispozici pro Visual Basic a C# na [Úvod do vytváření aplikací WPF](https://go.microsoft.com/fwlink/?LinkID=160008).</span><span class="sxs-lookup"><span data-stu-id="824cc-113">The sample code that is used to build this walkthrough is available for both Visual Basic and C# at [Introduction to Building WPF Applications](https://go.microsoft.com/fwlink/?LinkID=160008).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="824cc-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="824cc-114">Prerequisites</span></span>

- <span data-ttu-id="824cc-115">Visual Studio 2017 nebo novější</span><span class="sxs-lookup"><span data-stu-id="824cc-115">Visual Studio 2017 or later</span></span>

   <span data-ttu-id="824cc-116">Další informace o instalaci nejnovější verze sady Visual Studio najdete v tématu [instalace sady Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="824cc-116">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="824cc-117">Vytvoření projektu aplikace</span><span class="sxs-lookup"><span data-stu-id="824cc-117">Create the application project</span></span>

<span data-ttu-id="824cc-118">Prvním krokem je vytvoření aplikační infrastruktury, který obsahuje definici aplikace, dvě stránky a bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="824cc-118">The first step is to create the application infrastructure, which includes an application definition, two pages, and an image.</span></span>

1. <span data-ttu-id="824cc-119">Vytvoření nového projektu aplikace WPF v jazyce Visual Basic nebo Visual C# s názvem **`ExpenseIt`**:</span><span class="sxs-lookup"><span data-stu-id="824cc-119">Create a new WPF Application project in Visual Basic or Visual C# named **`ExpenseIt`**:</span></span>

   1. <span data-ttu-id="824cc-120">Otevřít Visual Studio a vyberte **souboru** > **nový** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="824cc-120">Open Visual Studio and select **File** > **New** > **Project**.</span></span>

      <span data-ttu-id="824cc-121">**Nový projekt** otevře se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="824cc-121">The **New Project** dialog opens.</span></span>

   2. <span data-ttu-id="824cc-122">V části **nainstalováno** kategorie, rozbalte buď **Visual C#**  nebo **jazyka Visual Basic** uzlu a pak vyberte **Windows Desktop**.</span><span class="sxs-lookup"><span data-stu-id="824cc-122">Under the **Installed** category, expand either the **Visual C#** or **Visual Basic** node, and then select **Windows Desktop**.</span></span>

   3. <span data-ttu-id="824cc-123">Vyberte **aplikace WPF (.NET Framework)** šablony.</span><span class="sxs-lookup"><span data-stu-id="824cc-123">Select the **WPF App (.NET Framework)** template.</span></span> <span data-ttu-id="824cc-124">Zadejte název **`ExpenseIt`** a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="824cc-124">Enter the name **`ExpenseIt`** and then select **OK**.</span></span>

      ![Dialogové okno nového projektu s vybraná aplikace WPF](./media/new-project-dialog.png)

      <span data-ttu-id="824cc-126">Visual Studio vytvoří projekt a otevře se návrhář pro výchozí okno aplikace s názvem **souboru MainWindow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="824cc-126">Visual Studio creates the project and opens the designer for the default application window named **MainWindow.xaml**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="824cc-127">Tento návod používá <xref:System.Windows.Controls.DataGrid> ovládací prvek, který je k dispozici v rozhraní .NET Framework 4 a novější.</span><span class="sxs-lookup"><span data-stu-id="824cc-127">This walkthrough uses the <xref:System.Windows.Controls.DataGrid> control that is available in the .NET Framework 4 and later.</span></span> <span data-ttu-id="824cc-128">Být jisti, že váš projekt cílí na rozhraní .NET Framework 4 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="824cc-128">Be sure that your project targets the .NET Framework 4 or later.</span></span> <span data-ttu-id="824cc-129">Další informace najdete v tématu [jak: Cílení na určitou verzi rozhraní .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span><span class="sxs-lookup"><span data-stu-id="824cc-129">For more information, see [How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span>

2. <span data-ttu-id="824cc-130">Otevřít *Application.xaml* (Visual Basic) nebo *App.xaml* (C#).</span><span class="sxs-lookup"><span data-stu-id="824cc-130">Open *Application.xaml* (Visual Basic) or *App.xaml* (C#).</span></span>

    <span data-ttu-id="824cc-131">Tento soubor XAML definuje aplikace WPF a všechny prostředky, aplikace.</span><span class="sxs-lookup"><span data-stu-id="824cc-131">This XAML file defines a WPF application and any application resources.</span></span> <span data-ttu-id="824cc-132">Tento soubor je využít taky k určení rozhraní, které se automaticky zobrazí při spuštění aplikace; v takovém případě *souboru MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="824cc-132">You also use this file to specify the UI that automatically shows when the application starts; in this case, *MainWindow.xaml*.</span></span>

    <span data-ttu-id="824cc-133">Vaše XAML by měl vypadat takto v jazyce Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="824cc-133">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    <span data-ttu-id="824cc-134">Nebo takto v jazyce C#:</span><span class="sxs-lookup"><span data-stu-id="824cc-134">Or like this in C#:</span></span>

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. <span data-ttu-id="824cc-135">Otevřít *souboru MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="824cc-135">Open *MainWindow.xaml*.</span></span>

    <span data-ttu-id="824cc-136">Tento soubor XAML je hlavní okno aplikace a zobrazí obsah vytvořený na stránkách.</span><span class="sxs-lookup"><span data-stu-id="824cc-136">This XAML file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="824cc-137"><xref:System.Windows.Window> Třídy definuje vlastnosti okna, například jeho název, velikost nebo ikonu a zpracovává události, jako je například zavření nebo skrytí.</span><span class="sxs-lookup"><span data-stu-id="824cc-137">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span>

4. <span data-ttu-id="824cc-138">Změnit <xref:System.Windows.Window> elementu <xref:System.Windows.Navigation.NavigationWindow>, jak je znázorněno v následující XAML:</span><span class="sxs-lookup"><span data-stu-id="824cc-138">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>, as shown in the following XAML:</span></span>

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   <span data-ttu-id="824cc-139">Tato aplikace přejde na jiný obsah v závislosti na vstupu uživatele.</span><span class="sxs-lookup"><span data-stu-id="824cc-139">This app navigates to different content depending on the user input.</span></span> <span data-ttu-id="824cc-140">To je důvod, proč hlavní <xref:System.Windows.Window> musí změnit tak, aby <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="824cc-140">This is why the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="824cc-141"><xref:System.Windows.Navigation.NavigationWindow> zdědí všechny vlastnosti <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="824cc-141"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="824cc-142"><xref:System.Windows.Navigation.NavigationWindow> Vytvoří instanci prvku v souboru XAML <xref:System.Windows.Navigation.NavigationWindow> třídy.</span><span class="sxs-lookup"><span data-stu-id="824cc-142">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="824cc-143">Další informace najdete v tématu [Přehled navigace](../app-development/navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="824cc-143">For more information, see [Navigation overview](../app-development/navigation-overview.md).</span></span>

5. <span data-ttu-id="824cc-144">Změňte následující vlastnosti na <xref:System.Windows.Navigation.NavigationWindow> element:</span><span class="sxs-lookup"><span data-stu-id="824cc-144">Change the following properties on the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>

    - <span data-ttu-id="824cc-145">Nastavte <xref:System.Windows.Window.Title%2A> vlastnost "`ExpenseIt`".</span><span class="sxs-lookup"><span data-stu-id="824cc-145">Set the <xref:System.Windows.Window.Title%2A> property to "`ExpenseIt`".</span></span>

    - <span data-ttu-id="824cc-146">Nastavte <xref:System.Windows.FrameworkElement.Width%2A> vlastnost na šířku 500 pixelů.</span><span class="sxs-lookup"><span data-stu-id="824cc-146">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span>

    - <span data-ttu-id="824cc-147">Nastavte <xref:System.Windows.FrameworkElement.Height%2A> vlastnost na 350 pixelů.</span><span class="sxs-lookup"><span data-stu-id="824cc-147">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span>

    - <span data-ttu-id="824cc-148">Odeberte <xref:System.Windows.Controls.Grid> prvky mezi <xref:System.Windows.Navigation.NavigationWindow> značky.</span><span class="sxs-lookup"><span data-stu-id="824cc-148">Remove the <xref:System.Windows.Controls.Grid> elements between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span>

    <span data-ttu-id="824cc-149">Vaše XAML by měl vypadat takto v jazyce Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="824cc-149">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    <span data-ttu-id="824cc-150">Nebo takto v jazyce C#:</span><span class="sxs-lookup"><span data-stu-id="824cc-150">Or like this in C#:</span></span>

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

6. <span data-ttu-id="824cc-151">Otevřít *soubor MainWindow.xaml.vb* nebo *MainWindow.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="824cc-151">Open *MainWindow.xaml.vb* or *MainWindow.xaml.cs*.</span></span>

    <span data-ttu-id="824cc-152">Tento soubor je soubor kódu na pozadí, který obsahuje kód pro zpracování události deklarované v *souboru MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="824cc-152">This file is a code-behind file that contains code to handle the events declared in *MainWindow.xaml*.</span></span> <span data-ttu-id="824cc-153">Tento soubor obsahuje částečné třídy pro okno definované v XAML.</span><span class="sxs-lookup"><span data-stu-id="824cc-153">This file contains a partial class for the window defined in XAML.</span></span>

7. <span data-ttu-id="824cc-154">Pokud používáte C#, změňte `MainWindow` třídy odvozovat z <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="824cc-154">If you are using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="824cc-155">(V jazyce Visual Basic, tomu automaticky dojde při změně okna v XAML.)</span><span class="sxs-lookup"><span data-stu-id="824cc-155">(In Visual Basic, this happens automatically when you change the window in XAML.)</span></span>

   <span data-ttu-id="824cc-156">Váš kód by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="824cc-156">Your code should look like this:</span></span>

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
   [!code-vb[ExpenseIt#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]

   > [!TIP]
   > <span data-ttu-id="824cc-157">Můžete přepínat na jazyk kódu ukázek kódu mezi C# a Visual Basic v **jazyk** rozevíracího seznamu v horní pravé části tohoto článku.</span><span class="sxs-lookup"><span data-stu-id="824cc-157">You can toggle the code language of the sample code between C# and Visual Basic in the **Language** drop-down on the upper right side of this article.</span></span>

## <a name="add-files-to-the-application"></a><span data-ttu-id="824cc-158">Přidání souborů do aplikace</span><span class="sxs-lookup"><span data-stu-id="824cc-158">Add files to the application</span></span>

<span data-ttu-id="824cc-159">V této části přidáte dvě stránky a obrázku do aplikace.</span><span class="sxs-lookup"><span data-stu-id="824cc-159">In this section, you'll add two pages and an image to the application.</span></span>

1. <span data-ttu-id="824cc-160">Do projektu přidejte novou stránku WPF a pojmenujte ho *`ExpenseItHome.xaml`*:</span><span class="sxs-lookup"><span data-stu-id="824cc-160">Add a new WPF page to the project, and name it *`ExpenseItHome.xaml`*:</span></span>

   1. <span data-ttu-id="824cc-161">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **`ExpenseIt`** uzel projektu a zvolte **přidat** > **stránky**.</span><span class="sxs-lookup"><span data-stu-id="824cc-161">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="824cc-162">V **přidat novou položku** dialogového okna, **stránky (WPF)** šablony je už vybraná.</span><span class="sxs-lookup"><span data-stu-id="824cc-162">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="824cc-163">Zadejte název **`ExpenseItHome`** a pak vyberte **přidat**.</span><span class="sxs-lookup"><span data-stu-id="824cc-163">Enter the name **`ExpenseItHome`**, and then select **Add**.</span></span>

    <span data-ttu-id="824cc-164">Tato stránka je první stránka, která se zobrazí při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="824cc-164">This page is the first page that's displayed when the application is launched.</span></span> <span data-ttu-id="824cc-165">Zobrazí seznam uživatelů vyberte, chcete-li zobrazit sestavy výdajů pro.</span><span class="sxs-lookup"><span data-stu-id="824cc-165">It will show a list of people to select from, to show an expense report for.</span></span>

2. <span data-ttu-id="824cc-166">Otevřít *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="824cc-166">Open *`ExpenseItHome.xaml`*.</span></span>

3. <span data-ttu-id="824cc-167">Nastavte <xref:System.Windows.Controls.Page.Title%2A> na "`ExpenseIt - Home`".</span><span class="sxs-lookup"><span data-stu-id="824cc-167">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - Home`".</span></span>

    <span data-ttu-id="824cc-168">Vaše XAML by měl vypadat takto v jazyce Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="824cc-168">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    <span data-ttu-id="824cc-169">Nebo to v jazyce C#:</span><span class="sxs-lookup"><span data-stu-id="824cc-169">Or this in C#:</span></span>

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

4. <span data-ttu-id="824cc-170">Otevřít *souboru MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="824cc-170">Open *MainWindow.xaml*.</span></span>

5. <span data-ttu-id="824cc-171">Nastavte <xref:System.Windows.Navigation.NavigationWindow.Source%2A> vlastnost <xref:System.Windows.Navigation.NavigationWindow> na "`ExpenseItHome.xaml`".</span><span class="sxs-lookup"><span data-stu-id="824cc-171">Set the <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property on the <xref:System.Windows.Navigation.NavigationWindow> to "`ExpenseItHome.xaml`".</span></span>

    <span data-ttu-id="824cc-172">Tím se nastaví *`ExpenseItHome.xaml`* bude první stránka otevře při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="824cc-172">This sets *`ExpenseItHome.xaml`* to be the first page opened when the application starts.</span></span> <span data-ttu-id="824cc-173">Vaše XAML by měl vypadat takto v jazyce Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="824cc-173">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    <span data-ttu-id="824cc-174">Nebo to v jazyce C#:</span><span class="sxs-lookup"><span data-stu-id="824cc-174">Or this in C#:</span></span>

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > <span data-ttu-id="824cc-175">Můžete také nastavit **zdroj** vlastnost **různé** kategorii **vlastnosti** okna.</span><span class="sxs-lookup"><span data-stu-id="824cc-175">You can also set the **Source** property in the **Miscellaneous** category of the **Properties** window.</span></span>
   >
   > ![Source – vlastnost v okně Vlastnosti](./media/properties-source.png)

6. <span data-ttu-id="824cc-177">Do projektu přidejte další novou stránku WPF a pojmenujte ho *ExpenseReportPage.xaml*::</span><span class="sxs-lookup"><span data-stu-id="824cc-177">Add another new WPF page to the project, and name it *ExpenseReportPage.xaml*::</span></span>

   1. <span data-ttu-id="824cc-178">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **`ExpenseIt`** uzel projektu a zvolte **přidat** > **stránky**.</span><span class="sxs-lookup"><span data-stu-id="824cc-178">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="824cc-179">V **přidat novou položku** dialogového okna, **stránky (WPF)** šablony je už vybraná.</span><span class="sxs-lookup"><span data-stu-id="824cc-179">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="824cc-180">Zadejte název **ExpenseReportPage**a pak vyberte **přidat**.</span><span class="sxs-lookup"><span data-stu-id="824cc-180">Enter the name **ExpenseReportPage**, and then select **Add**.</span></span>

    <span data-ttu-id="824cc-181">Na této stránce se zobrazí vyúčtování pro osoby, která je vybrán na **`ExpenseItHome`** stránky.</span><span class="sxs-lookup"><span data-stu-id="824cc-181">This page will show the expense report for the person that is selected on the **`ExpenseItHome`** page.</span></span>

7. <span data-ttu-id="824cc-182">Otevřít *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="824cc-182">Open *ExpenseReportPage.xaml*.</span></span>

8. <span data-ttu-id="824cc-183">Nastavte <xref:System.Windows.Controls.Page.Title%2A> na "`ExpenseIt - View Expense`".</span><span class="sxs-lookup"><span data-stu-id="824cc-183">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - View Expense`".</span></span>

    <span data-ttu-id="824cc-184">Vaše XAML by měl vypadat takto v jazyce Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="824cc-184">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    <span data-ttu-id="824cc-185">Nebo to v jazyce C#:</span><span class="sxs-lookup"><span data-stu-id="824cc-185">Or this in C#:</span></span>

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

9. <span data-ttu-id="824cc-186">Otevřít *ExpenseItHome.xaml.vb* a *ExpenseReportPage.xaml.vb*, nebo *ExpenseItHome.xaml.cs* a *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="824cc-186">Open *ExpenseItHome.xaml.vb* and *ExpenseReportPage.xaml.vb*, or *ExpenseItHome.xaml.cs* and *ExpenseReportPage.xaml.cs*.</span></span>

    <span data-ttu-id="824cc-187">Když vytvoříte nový soubor stránky, sada Visual Studio automaticky vytvoří *použití modelu code-behind* souboru.</span><span class="sxs-lookup"><span data-stu-id="824cc-187">When you create a new Page file, Visual Studio automatically creates a *code-behind* file.</span></span> <span data-ttu-id="824cc-188">Tyto soubory použití modelu code-behind zpracování logiky reagovat na vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="824cc-188">These code-behind files handle the logic for responding to user input.</span></span>

    <span data-ttu-id="824cc-189">Váš kód by měl vypadat takto pro **`ExpenseItHome`**:</span><span class="sxs-lookup"><span data-stu-id="824cc-189">Your code should look like this for **`ExpenseItHome`**:</span></span>

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    <span data-ttu-id="824cc-190">A takhle pro **ExpenseReportPage**:</span><span class="sxs-lookup"><span data-stu-id="824cc-190">And like this for **ExpenseReportPage**:</span></span>

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

10. <span data-ttu-id="824cc-191">Přidání obrázku s názvem *watermark.png* do projektu.</span><span class="sxs-lookup"><span data-stu-id="824cc-191">Add an image named *watermark.png* to the project.</span></span> <span data-ttu-id="824cc-192">Můžete vytvořit vlastní image, zkopírujte soubor ve vzorku kódu nebo získat [tady](https://github.com/dotnet/docs/blob/master/docs/framework/wpf/getting-started/./media/watermark.png).</span><span class="sxs-lookup"><span data-stu-id="824cc-192">You can create your own image, copy the file from the sample code, or get it [here](https://github.com/dotnet/docs/blob/master/docs/framework/wpf/getting-started/./media/watermark.png).</span></span>

    1. <span data-ttu-id="824cc-193">Klikněte pravým tlačítkem na uzel projektu a vyberte **přidat** > **existující položku**, nebo stiskněte klávesu **Shift**+**Alt** + **A**.</span><span class="sxs-lookup"><span data-stu-id="824cc-193">Right-click on the project node and select **Add** > **Existing Item**, or press **Shift**+**Alt**+**A**.</span></span>

    2. <span data-ttu-id="824cc-194">V **přidat existující položku** dialogové okno, přejděte k souboru bitové kopie, kterou chcete použít a potom vyberte **přidat**.</span><span class="sxs-lookup"><span data-stu-id="824cc-194">In the **Add Existing Item** dialog, browse to the image file you want to use, and then select **Add**.</span></span>

## <a name="build-and-run-the-application"></a><span data-ttu-id="824cc-195">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="824cc-195">Build and run the application</span></span>

1. <span data-ttu-id="824cc-196">Chcete-li sestavit a spustit aplikaci, stiskněte **F5** nebo vyberte **spustit ladění** z **ladění** nabídky.</span><span class="sxs-lookup"><span data-stu-id="824cc-196">To build and run the application, press **F5** or select **Start Debugging** from the **Debug** menu.</span></span>

    <span data-ttu-id="824cc-197">Následující obrázek znázorňuje aplikaci <xref:System.Windows.Navigation.NavigationWindow> tlačítka:</span><span class="sxs-lookup"><span data-stu-id="824cc-197">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons:</span></span>

    ![Snímek obrazovky ExpenseIt – ukázka](./media/gettingstartedfigure1.png)

2. <span data-ttu-id="824cc-199">Ukončete aplikaci se vraťte do sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="824cc-199">Close the application to return to Visual Studio.</span></span>

## <a name="create-the-layout"></a><span data-ttu-id="824cc-200">Vytvořit rozložení</span><span class="sxs-lookup"><span data-stu-id="824cc-200">Create the layout</span></span>

<span data-ttu-id="824cc-201">Rozložení poskytuje seřazený umožňuje umístit prvky uživatelského rozhraní a také spravuje velikost a umístění těchto prvků při změně velikosti uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="824cc-201">Layout provides an ordered way to place UI elements, and also manages the size and position of those elements when a UI is resized.</span></span> <span data-ttu-id="824cc-202">Rozložení se obvykle vytvoříte pomocí jednoho z následujících ovládacích prvků rozložení:</span><span class="sxs-lookup"><span data-stu-id="824cc-202">You typically create a layout with one of the following layout controls:</span></span>

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.DockPanel>
- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.VirtualizingStackPanel>
- <xref:System.Windows.Controls.WrapPanel>

<span data-ttu-id="824cc-203">Každá z těchto ovládacích prvků rozložení podporuje zvláštní druh rozložení pro jeho podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="824cc-203">Each of these layout controls supports a special type of layout for its child elements.</span></span> <span data-ttu-id="824cc-204">`ExpenseIt` změnit velikost stránky, a každá stránka obsahuje prvky, které jsou uspořádány vodorovně a svisle vedle dalších prvků.</span><span class="sxs-lookup"><span data-stu-id="824cc-204">`ExpenseIt` pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="824cc-205">V důsledku toho <xref:System.Windows.Controls.Grid> je prvek ideální rozložení pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="824cc-205">Consequently, the <xref:System.Windows.Controls.Grid> is the ideal layout element for the application.</span></span>

> [!TIP]
> <span data-ttu-id="824cc-206">Další informace o <xref:System.Windows.Controls.Panel> prvky, naleznete v tématu [přehled panelů](../controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="824cc-206">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels overview](../controls/panels-overview.md).</span></span> <span data-ttu-id="824cc-207">Další informace o rozložení najdete v tématu [rozložení](../advanced/layout.md).</span><span class="sxs-lookup"><span data-stu-id="824cc-207">For more information about layout, see [Layout](../advanced/layout.md).</span></span>

<span data-ttu-id="824cc-208">V části vytvoříte tabulku s jedním sloupcem se třemi řádky a 10 pixel okraj přidáním řádků a sloupců definice <xref:System.Windows.Controls.Grid> v *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="824cc-208">In the section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="824cc-209">Otevřít *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="824cc-209">Open *`ExpenseItHome.xaml`*.</span></span>

2. <span data-ttu-id="824cc-210">Nastavte <xref:System.Windows.FrameworkElement.Margin%2A> vlastnost <xref:System.Windows.Controls.Grid> prvku "10,0,10,10", která odpovídá na levé straně, horní, pravé a dolní okraj:</span><span class="sxs-lookup"><span data-stu-id="824cc-210">Set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10", which corresponds to left, top, right and bottom margins:</span></span>

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > <span data-ttu-id="824cc-211">Můžete také nastavit **okraj** hodnoty v **vlastnosti** okně v části **rozložení** kategorie:</span><span class="sxs-lookup"><span data-stu-id="824cc-211">You can also set the **Margin** values in the **Properties** window, under the **Layout** category:</span></span>
   >
   > ![Hodnoty vlastnosti okraj v okně Vlastnosti](./media/properties-margin.png)

3. <span data-ttu-id="824cc-213">Přidejte následující XAML mezi <xref:System.Windows.Controls.Grid> značky vytvářet definice řádků a sloupců:</span><span class="sxs-lookup"><span data-stu-id="824cc-213">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions:</span></span>

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <span data-ttu-id="824cc-214"><xref:System.Windows.Controls.RowDefinition.Height%2A> Dva řádky se nastaví na <xref:System.Windows.GridLength.Auto%2A>, což znamená, že je nastavena velikost řádků na základě obsahu v řádcích.</span><span class="sxs-lookup"><span data-stu-id="824cc-214">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A>, which means that the rows are sized based on the content in the rows.</span></span> <span data-ttu-id="824cc-215">Výchozí hodnota <xref:System.Windows.Controls.RowDefinition.Height%2A> je <xref:System.Windows.GridUnitType.Star> velikosti, což znamená, že vážený poměr volného místa výšku řádku.</span><span class="sxs-lookup"><span data-stu-id="824cc-215">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row height is a weighted proportion of the available space.</span></span> <span data-ttu-id="824cc-216">Například pokud máte dva řádky <xref:System.Windows.Controls.RowDefinition.Height%2A> z "\*", každý z nich výška polovinu dostupné místo.</span><span class="sxs-lookup"><span data-stu-id="824cc-216">For example if two rows each have a <xref:System.Windows.Controls.RowDefinition.Height%2A> of "\*", they each have a height that is half of the available space.</span></span>

    <span data-ttu-id="824cc-217">Vaše <xref:System.Windows.Controls.Grid> by teď měl vypadat podobně jako následující XAML:</span><span class="sxs-lookup"><span data-stu-id="824cc-217">Your <xref:System.Windows.Controls.Grid> should now look like the following XAML:</span></span>

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a><span data-ttu-id="824cc-218">Přidání ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="824cc-218">Add controls</span></span>

<span data-ttu-id="824cc-219">V této části budete aktualizovat na domovské stránce uživatelského rozhraní, zobrazí se seznam lidí, se může uživatel vybrat z zobrazíte vyúčtování pro.</span><span class="sxs-lookup"><span data-stu-id="824cc-219">In this section, you'll update the home page UI to show a list of people that a user can select from to show the expense report for.</span></span> <span data-ttu-id="824cc-220">Ovládací prvky jsou objekty uživatelského rozhraní, které umožňují uživatelům, aby komunikovali s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="824cc-220">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="824cc-221">Další informace najdete v tématu [ovládací prvky](../controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="824cc-221">For more information, see [Controls](../controls/index.md).</span></span>

<span data-ttu-id="824cc-222">K vytvoření tohoto uživatelského rozhraní, přidejte následující prvky, které mají *`ExpenseItHome.xaml`*:</span><span class="sxs-lookup"><span data-stu-id="824cc-222">To create this UI, you'll add the following elements to *`ExpenseItHome.xaml`*:</span></span>

- <span data-ttu-id="824cc-223"><xref:System.Windows.Controls.ListBox> (pro seznam lidí, kteří).</span><span class="sxs-lookup"><span data-stu-id="824cc-223"><xref:System.Windows.Controls.ListBox> (for the list of people).</span></span>
- <span data-ttu-id="824cc-224"><xref:System.Windows.Controls.Label> (pro záhlaví seznamu).</span><span class="sxs-lookup"><span data-stu-id="824cc-224"><xref:System.Windows.Controls.Label> (for the list header).</span></span>
- <span data-ttu-id="824cc-225"><xref:System.Windows.Controls.Button> (Chcete-li kliknutím zobrazíte vyúčtování pro osobu, která je v seznamu vyberete).</span><span class="sxs-lookup"><span data-stu-id="824cc-225"><xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span>

<span data-ttu-id="824cc-226">Každý ovládací prvek nachází v řádku <xref:System.Windows.Controls.Grid> nastavením <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> přidružená vlastnost.</span><span class="sxs-lookup"><span data-stu-id="824cc-226">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="824cc-227">Další informace o přidružené vlastnosti najdete v tématu [přehled připojených vlastností](../advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="824cc-227">For more information about attached properties, see [Attached Properties Overview](../advanced/attached-properties-overview.md).</span></span>

1. <span data-ttu-id="824cc-228">Otevřít *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="824cc-228">Open *`ExpenseItHome.xaml`*.</span></span>

2. <span data-ttu-id="824cc-229">Přidejte následující XAML někde mezi <xref:System.Windows.Controls.Grid> značky:</span><span class="sxs-lookup"><span data-stu-id="824cc-229">Add the following XAML somewhere between the <xref:System.Windows.Controls.Grid> tags:</span></span>

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > <span data-ttu-id="824cc-230">Ovládací prvky můžete vytvořit také z jejich přetažením **nástrojů** okna do okna návrhu a nastavte jejich vlastnosti **vlastnosti** okna.</span><span class="sxs-lookup"><span data-stu-id="824cc-230">You can also create the controls by dragging them from the **Toolbox** window onto the design window, and then setting their properties in the **Properties** window.</span></span>

3. <span data-ttu-id="824cc-231">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="824cc-231">Build and run the application.</span></span>

<span data-ttu-id="824cc-232">Následující obrázek znázorňuje ovládací prvky, že kterou jste právě vytvořili:</span><span class="sxs-lookup"><span data-stu-id="824cc-232">The following illustration shows the controls you just created:</span></span>

![Snímek obrazovky ExpenseIt – ukázka](./media/gettingstartedfigure2.png)

## <a name="add-an-image-and-a-title"></a><span data-ttu-id="824cc-234">Přidat obrázek a název</span><span class="sxs-lookup"><span data-stu-id="824cc-234">Add an image and a title</span></span>

<span data-ttu-id="824cc-235">V této části budete aktualizovat Uživatelském rozhraní domovské stránky s bitovou kopii a název stránky.</span><span class="sxs-lookup"><span data-stu-id="824cc-235">In this section, you'll update the home page UI with an image and a page title.</span></span>

1. <span data-ttu-id="824cc-236">Otevřít *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="824cc-236">Open *`ExpenseItHome.xaml`*.</span></span>

2. <span data-ttu-id="824cc-237">Přidat jiný sloupec <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> s pevnou <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 pixelů:</span><span class="sxs-lookup"><span data-stu-id="824cc-237">Add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels:</span></span>

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]

3. <span data-ttu-id="824cc-238">Přidat další řádek <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, celkem čtyři řádky:</span><span class="sxs-lookup"><span data-stu-id="824cc-238">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, for a total of four rows:</span></span>

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]

4. <span data-ttu-id="824cc-239">Přesuňte ovládací prvky na druhý sloupec tak, že nastavíte <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> vlastnost na hodnotu 1 v každé tři ovládací prvky (hranice ListBox a tlačítko).</span><span class="sxs-lookup"><span data-stu-id="824cc-239">Move the controls to the second column by setting the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property to 1 in each of the three controls (Border, ListBox, and Button).</span></span>

5. <span data-ttu-id="824cc-240">Každý ovládací prvek dolů řádek zvýšením jeho <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> hodnotu o 1.</span><span class="sxs-lookup"><span data-stu-id="824cc-240">Move each control down a row, by incrementing its <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> value by 1.</span></span>

   <span data-ttu-id="824cc-241">XAML pro tři ovládací prvky nyní vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="824cc-241">The XAML for the three controls now looks like this:</span></span>

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

6. <span data-ttu-id="824cc-242">Nastavte <xref:System.Windows.Controls.Panel.Background%2A> z <xref:System.Windows.Controls.Grid> bude *watermark.png* soubor obrázku, přidáním následující XAML někde mezi `<Grid>` a `</Grid>` značky:</span><span class="sxs-lookup"><span data-stu-id="824cc-242">Set the <xref:System.Windows.Controls.Panel.Background%2A> of the <xref:System.Windows.Controls.Grid> to be the *watermark.png* image file, by adding the following XAML somewhere between the `<Grid>` and `</Grid>` tags:</span></span>

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

7. <span data-ttu-id="824cc-243">Před <xref:System.Windows.Controls.Border> prvku, přidejte <xref:System.Windows.Controls.Label> s obsahem "Zobrazení vyúčtování".</span><span class="sxs-lookup"><span data-stu-id="824cc-243">Before the <xref:System.Windows.Controls.Border> element, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report".</span></span> <span data-ttu-id="824cc-244">Toto je název stránky.</span><span class="sxs-lookup"><span data-stu-id="824cc-244">This is the title of the page.</span></span>

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

8. <span data-ttu-id="824cc-245">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="824cc-245">Build and run the application.</span></span>

<span data-ttu-id="824cc-246">Následující obrázek ukazuje výsledky co jste právě přidali:</span><span class="sxs-lookup"><span data-stu-id="824cc-246">The following illustration shows the results of what you just added:</span></span>

![Snímek obrazovky ExpenseIt – ukázka](./media/gettingstartedfigure3.png)

## <a name="add-code-to-handle-events"></a><span data-ttu-id="824cc-248">Přidejte kód pro zpracování událostí</span><span class="sxs-lookup"><span data-stu-id="824cc-248">Add code to handle events</span></span>

1. <span data-ttu-id="824cc-249">Otevřít *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="824cc-249">Open *`ExpenseItHome.xaml`*.</span></span>

2. <span data-ttu-id="824cc-250">Přidat <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužnou rutinu události <xref:System.Windows.Controls.Button> elementu.</span><span class="sxs-lookup"><span data-stu-id="824cc-250">Add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="824cc-251">Další informace najdete v tématu [jak: Vytvořte obslužnou rutinu události jednoduché](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="824cc-251">For more information, see [How to: Create a simple event handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

3. <span data-ttu-id="824cc-252">Otevřít *`ExpenseItHome.xaml.vb`* nebo *`ExpenseItHome.xaml.cs`*.</span><span class="sxs-lookup"><span data-stu-id="824cc-252">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

4. <span data-ttu-id="824cc-253">Přidejte následující kód, který `ExpenseItHome` třídy přidejte tlačítko klikněte na obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="824cc-253">Add the following code to the `ExpenseItHome` class to add a button click event handler.</span></span> <span data-ttu-id="824cc-254">Obslužná rutina události otevře **ExpenseReportPage** stránky.</span><span class="sxs-lookup"><span data-stu-id="824cc-254">The event handler opens the **ExpenseReportPage** page.</span></span>

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a><span data-ttu-id="824cc-255">Vytvoření uživatelského rozhraní pro ExpenseReportPage</span><span class="sxs-lookup"><span data-stu-id="824cc-255">Create the UI for ExpenseReportPage</span></span>

<span data-ttu-id="824cc-256">*ExpenseReportPage.xaml* zobrazí vyúčtování pro osobu, která je vybrán na **`ExpenseItHome`** stránky.</span><span class="sxs-lookup"><span data-stu-id="824cc-256">*ExpenseReportPage.xaml* displays the expense report for the person that's selected on the **`ExpenseItHome`** page.</span></span> <span data-ttu-id="824cc-257">V této části vytvoříte uživatelské rozhraní pro **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="824cc-257">In this section, you'll create the UI for **ExpenseReportPage**.</span></span> <span data-ttu-id="824cc-258">Budete také přidat na pozadí a vyplnit barev pro různé elementy uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="824cc-258">You'll also add background and fill colors to the various UI elements.</span></span>

1. <span data-ttu-id="824cc-259">Otevřít *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="824cc-259">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="824cc-260">Přidejte následující XAML mezi <xref:System.Windows.Controls.Grid> značky:</span><span class="sxs-lookup"><span data-stu-id="824cc-260">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags:</span></span>

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    <span data-ttu-id="824cc-261">Toto uživatelské rozhraní je podobný *`ExpenseItHome.xaml`*, s výjimkou data sestavy se zobrazí v <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="824cc-261">This UI is similar to *`ExpenseItHome.xaml`*, except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span>

3. <span data-ttu-id="824cc-262">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="824cc-262">Build and run the application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="824cc-263">Pokud dojde k chybě <xref:System.Windows.Controls.DataGrid> se nepovedlo najít nebo neexistuje, ujistěte se, že váš projekt cílí na .NET Framework 4 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="824cc-263">If you get an error that the <xref:System.Windows.Controls.DataGrid> was not found or does not exist, make sure that your project targets the .NET Framework 4 or later.</span></span> <span data-ttu-id="824cc-264">Další informace najdete v tématu [jak: Cílení na určitou verzi rozhraní .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span><span class="sxs-lookup"><span data-stu-id="824cc-264">For more information, see [How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span>

4. <span data-ttu-id="824cc-265">Vyberte **zobrazení** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="824cc-265">Select the **View** button.</span></span>

    <span data-ttu-id="824cc-266">Zobrazí se stránka sestavy výdajů.</span><span class="sxs-lookup"><span data-stu-id="824cc-266">The expense report page appears.</span></span> <span data-ttu-id="824cc-267">Všimněte si také, zda je povoleno tlačítko zpětné navigace.</span><span class="sxs-lookup"><span data-stu-id="824cc-267">Also notice that the back navigation button is enabled.</span></span>

<span data-ttu-id="824cc-268">Následující obrázek znázorňuje prvky uživatelského rozhraní, které jsou přidány do *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="824cc-268">The following illustration shows the UI elements added to *ExpenseReportPage.xaml*.</span></span>

![Snímek obrazovky ExpenseIt – ukázka](./media/gettingstartedfigure4.png)

## <a name="style-controls"></a><span data-ttu-id="824cc-270">Ovládací prvky stylu</span><span class="sxs-lookup"><span data-stu-id="824cc-270">Style controls</span></span>

<span data-ttu-id="824cc-271">Vzhled různé prvky je často stejný pro všechny prvky v uživatelském rozhraní stejného typu.</span><span class="sxs-lookup"><span data-stu-id="824cc-271">The appearance of various elements is often the same for all elements of the same type in a UI.</span></span> <span data-ttu-id="824cc-272">Uživatelské rozhraní používá [styly](../controls/styling-and-templating.md) k zajištění vzhled opakovaně použitelné napříč více prvků.</span><span class="sxs-lookup"><span data-stu-id="824cc-272">UI uses [styles](../controls/styling-and-templating.md) to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="824cc-273">Opětovné použití stylů pomáhá zjednodušit XAML vytváření a správu.</span><span class="sxs-lookup"><span data-stu-id="824cc-273">The reusability of styles helps to simplify XAML creation and management.</span></span> <span data-ttu-id="824cc-274">Tato část nahradí atributy na element, definované v předchozích krocích se styly.</span><span class="sxs-lookup"><span data-stu-id="824cc-274">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span>

1. <span data-ttu-id="824cc-275">Otevřít *Application.xaml* nebo *App.xaml*.</span><span class="sxs-lookup"><span data-stu-id="824cc-275">Open *Application.xaml* or *App.xaml*.</span></span>

2. <span data-ttu-id="824cc-276">Přidejte následující XAML mezi <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> značky:</span><span class="sxs-lookup"><span data-stu-id="824cc-276">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    <span data-ttu-id="824cc-277">Tento XAML přidá následující styly:</span><span class="sxs-lookup"><span data-stu-id="824cc-277">This XAML adds the following styles:</span></span>

    - <span data-ttu-id="824cc-278">`headerTextStyle`: Formátování názvu stránky <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="824cc-278">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="824cc-279">`labelStyle`: K formátování <xref:System.Windows.Controls.Label> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="824cc-279">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span>

    - <span data-ttu-id="824cc-280">`columnHeaderStyle`: K formátování <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span><span class="sxs-lookup"><span data-stu-id="824cc-280">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span>

    - <span data-ttu-id="824cc-281">`listHeaderStyle`: K formátování záhlaví seznamu <xref:System.Windows.Controls.Border> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="824cc-281">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span>

    - <span data-ttu-id="824cc-282">`listHeaderTextStyle`: K formátování záhlaví seznamu <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="824cc-282">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="824cc-283">`buttonStyle`: K formátování <xref:System.Windows.Controls.Button> na `ExpenseItHome.xaml`.</span><span class="sxs-lookup"><span data-stu-id="824cc-283">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on `ExpenseItHome.xaml`.</span></span>

    <span data-ttu-id="824cc-284">Všimněte si, že se styly prostředky a podřízené objekty daného <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> element vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="824cc-284">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="824cc-285">V tomto umístění se styly použijí na všechny prvky v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="824cc-285">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="824cc-286">Příklad použití prostředků v aplikaci .NET Framework, naleznete v tématu [využití prostředků aplikace](../advanced/how-to-use-application-resources.md).</span><span class="sxs-lookup"><span data-stu-id="824cc-286">For an example of using resources in a .NET Framework application, see [Use Application Resources](../advanced/how-to-use-application-resources.md).</span></span>

3. <span data-ttu-id="824cc-287">Otevřít *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="824cc-287">Open *`ExpenseItHome.xaml`*.</span></span>

4. <span data-ttu-id="824cc-288">Nahradit vše mezi <xref:System.Windows.Controls.Grid> prvky s následující XAML:</span><span class="sxs-lookup"><span data-stu-id="824cc-288">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    <span data-ttu-id="824cc-289">Vlastnosti, jako <xref:System.Windows.VerticalAlignment> a <xref:System.Windows.Media.FontFamily> , které definují vzhled každého ovládacího prvku odebrán a nahrazen o aplikování stylů.</span><span class="sxs-lookup"><span data-stu-id="824cc-289">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="824cc-290">Například `headerTextStyle` platí pro "Zobrazení vyúčtování" <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="824cc-290">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span>

5. <span data-ttu-id="824cc-291">Otevřít *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="824cc-291">Open *ExpenseReportPage.xaml*.</span></span>

6. <span data-ttu-id="824cc-292">Nahradit vše mezi <xref:System.Windows.Controls.Grid> prvky s následující XAML:</span><span class="sxs-lookup"><span data-stu-id="824cc-292">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    <span data-ttu-id="824cc-293">Tento postup přidá stylů <xref:System.Windows.Controls.Label> a <xref:System.Windows.Controls.Border> elementy.</span><span class="sxs-lookup"><span data-stu-id="824cc-293">This adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span>

## <a name="bind-data-to-a-control"></a><span data-ttu-id="824cc-294">Vytvoření vazby dat k ovládacímu prvku</span><span class="sxs-lookup"><span data-stu-id="824cc-294">Bind data to a control</span></span>

<span data-ttu-id="824cc-295">V této části vytvoříte data XML, který je vázán na různé ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="824cc-295">In this section, you'll create the XML data that is bound to various controls.</span></span>

1. <span data-ttu-id="824cc-296">Otevřít *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="824cc-296">Open *`ExpenseItHome.xaml`*.</span></span>

2. <span data-ttu-id="824cc-297">Po zahájení <xref:System.Windows.Controls.Grid> elementu, přidejte následující XAML vytvořit <xref:System.Windows.Data.XmlDataProvider> , která pro každou osobu, která obsahuje data:</span><span class="sxs-lookup"><span data-stu-id="824cc-297">After the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person:</span></span>

    [!code-xaml[ExpenseIt#21](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]
    [!code-xaml[ExpenseIt#22](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    <span data-ttu-id="824cc-298">Data se vytvoří jako <xref:System.Windows.Controls.Grid> prostředků.</span><span class="sxs-lookup"><span data-stu-id="824cc-298">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="824cc-299">Obvykle to budou načteny jako soubor, ale pro zjednodušení je přidat data vložené.</span><span class="sxs-lookup"><span data-stu-id="824cc-299">Normally this would be loaded as a file, but for simplicity the data is added inline.</span></span>

3. <span data-ttu-id="824cc-300">V rámci `<Grid.Resources>` elementu, přidejte následující <xref:System.Windows.DataTemplate>, který definuje způsob zobrazení dat v <xref:System.Windows.Controls.ListBox>:</span><span class="sxs-lookup"><span data-stu-id="824cc-300">Within the `<Grid.Resources>` element, add the following <xref:System.Windows.DataTemplate>, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>:</span></span>

    [!code-xaml[ExpenseIt#21](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]
    [!code-xaml[ExpenseIt#22](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    <span data-ttu-id="824cc-301">Další informace o šablonách dat, naleznete v tématu [přehled datových šablon](../data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="824cc-301">For more information about data templates, see [Data templating overview](../data/data-templating-overview.md).</span></span>

4. <span data-ttu-id="824cc-302">Nahraďte existující <xref:System.Windows.Controls.ListBox> s následující XAML:</span><span class="sxs-lookup"><span data-stu-id="824cc-302">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    <span data-ttu-id="824cc-303">Tento XAML naváže <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost <xref:System.Windows.Controls.ListBox> ke zdroji dat a použije šablona dat jako <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span><span class="sxs-lookup"><span data-stu-id="824cc-303">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span>

## <a name="connect-data-to-controls"></a><span data-ttu-id="824cc-304">Připojení dat k ovládacím prvkům</span><span class="sxs-lookup"><span data-stu-id="824cc-304">Connect data to controls</span></span>

<span data-ttu-id="824cc-305">V dalším kroku přidáte kód pro načtení název, který je vybrán na **`ExpenseItHome`** stránku a předat konstruktoru **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="824cc-305">Next, you'll add code to retrieve the name that's selected on the **`ExpenseItHome`** page and pass it to the constructor of **ExpenseReportPage**.</span></span> <span data-ttu-id="824cc-306">**ExpenseReportPage** nastaví jeho kontext dat s předaným položka, která se, co ovládací prvky definované v *ExpenseReportPage.xaml* svázat.</span><span class="sxs-lookup"><span data-stu-id="824cc-306">**ExpenseReportPage** sets its data context with the passed item, which is what the controls defined in *ExpenseReportPage.xaml* bind to.</span></span>

1. <span data-ttu-id="824cc-307">Otevřít *ExpenseReportPage.xaml.vb* nebo *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="824cc-307">Open *ExpenseReportPage.xaml.vb* or *ExpenseReportPage.xaml.cs*.</span></span>

2. <span data-ttu-id="824cc-308">Přidáte konstruktor, který přebírá objekt, abyste mohli předat data sestavy výdajů z vybraného uživatele.</span><span class="sxs-lookup"><span data-stu-id="824cc-308">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. <span data-ttu-id="824cc-309">Otevřít *`ExpenseItHome.xaml.vb`* nebo *`ExpenseItHome.xaml.cs`*.</span><span class="sxs-lookup"><span data-stu-id="824cc-309">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

4. <span data-ttu-id="824cc-310">Změnit <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužná rutina události volaná nový konstruktor předávání dat sestavy výdajů z vybraného uživatele.</span><span class="sxs-lookup"><span data-stu-id="824cc-310">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a><span data-ttu-id="824cc-311">Styl dat s využitím šablon dat</span><span class="sxs-lookup"><span data-stu-id="824cc-311">Style data with data templates</span></span>

<span data-ttu-id="824cc-312">V této části budete aktualizovat uživatelské rozhraní pro každou položku v seznamu vázaných na data pomocí šablony.</span><span class="sxs-lookup"><span data-stu-id="824cc-312">In this section, you'll update the UI for each item in the data-bound lists by using data templates.</span></span>

1. <span data-ttu-id="824cc-313">Otevřít *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="824cc-313">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="824cc-314">Vytvoření vazby obsah "Name" a "Oddělení" <xref:System.Windows.Controls.Label> prvků, které se příslušná data source – vlastnost.</span><span class="sxs-lookup"><span data-stu-id="824cc-314">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="824cc-315">Další informace o datové vazbě naleznete v tématu [přehled datových vazeb](../data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="824cc-315">For more information about data binding, see [Data binding overview](../data/data-binding-overview.md).</span></span>

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. <span data-ttu-id="824cc-316">Po zahájení <xref:System.Windows.Controls.Grid> prvku, přidejte následující datové šablony, které definují způsob zobrazení dat sestavy výdajů:</span><span class="sxs-lookup"><span data-stu-id="824cc-316">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data:</span></span>

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. <span data-ttu-id="824cc-317">Nahraďte <xref:System.Windows.Controls.DataGridTextColumn> prvky s <xref:System.Windows.Controls.DataGridTemplateColumn> pod <xref:System.Windows.Controls.DataGrid> elementu a použijte šablony k nim.</span><span class="sxs-lookup"><span data-stu-id="824cc-317">Replace the <xref:System.Windows.Controls.DataGridTextColumn> elements with <xref:System.Windows.Controls.DataGridTemplateColumn> under the <xref:System.Windows.Controls.DataGrid> element and apply the templates to them.</span></span>

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. <span data-ttu-id="824cc-318">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="824cc-318">Build and run the application.</span></span>

6. <span data-ttu-id="824cc-319">Vybrat osobu a pak vyberte **zobrazení** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="824cc-319">Select a person and then select the **View** button.</span></span>

<span data-ttu-id="824cc-320">Následující obrázek ukazuje obě stránky `ExpenseIt` aplikace s ovládacími prvky, rozložení, styly, vazby dat a použitých šablon dat:</span><span class="sxs-lookup"><span data-stu-id="824cc-320">The following illustration shows both pages of the `ExpenseIt` application with controls, layout, styles, data binding, and data templates applied:</span></span>

![Snímky obrazovky ExpenseIt – ukázka](./media/gettingstartedfigure5.png)

> [!NOTE]
> <span data-ttu-id="824cc-322">Tato ukázka předvádí konkrétní funkce WPF a nebude použijte všechny osvědčené postupy pro takové věci, jako je zabezpečení, lokalizace a přístupnost.</span><span class="sxs-lookup"><span data-stu-id="824cc-322">This sample demonstrates a specific feature of WPF and doesn't follow all best practices for things like security, localization, and accessibility.</span></span> <span data-ttu-id="824cc-323">Pro komplexní pokrytí WPF a osvědčené postupy vývoje aplikací rozhraní .NET Framework naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="824cc-323">For comprehensive coverage of WPF and the .NET Framework application development best practices, see the following topics:</span></span>
>
> - [<span data-ttu-id="824cc-324">Usnadnění</span><span class="sxs-lookup"><span data-stu-id="824cc-324">Accessibility</span></span>](../../ui-automation/accessibility-best-practices.md)
>
> - [<span data-ttu-id="824cc-325">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="824cc-325">Security</span></span>](../security-wpf.md)
>
> - [<span data-ttu-id="824cc-326">WPF globalizace a lokalizace</span><span class="sxs-lookup"><span data-stu-id="824cc-326">WPF globalization and localization</span></span>](../advanced/wpf-globalization-and-localization-overview.md)
>
> - [<span data-ttu-id="824cc-327">Výkonu WPF</span><span class="sxs-lookup"><span data-stu-id="824cc-327">WPF performance</span></span>](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a><span data-ttu-id="824cc-328">Další kroky</span><span class="sxs-lookup"><span data-stu-id="824cc-328">Next steps</span></span>

<span data-ttu-id="824cc-329">V tomto návodu jste zjistili několik technik pro vytvoření uživatelského rozhraní pomocí Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="824cc-329">In this walkthrough you learned a number of techniques for creating a UI using Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="824cc-330">Nyní byste měli mít základní znalosti o stavební bloky vázané na data, aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="824cc-330">You should now have a basic understanding of the building blocks of a data-bound, .NET Framework application.</span></span> <span data-ttu-id="824cc-331">Další informace o WPF architekturu a programovací modely naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="824cc-331">For more information about the WPF architecture and programming models, see the following topics:</span></span>

- [<span data-ttu-id="824cc-332">Architektura WPF</span><span class="sxs-lookup"><span data-stu-id="824cc-332">WPF architecture</span></span>](../advanced/wpf-architecture.md)
- [<span data-ttu-id="824cc-333">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="824cc-333">XAML overview (WPF)</span></span>](../advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="824cc-334">Přehled vlastností závislosti</span><span class="sxs-lookup"><span data-stu-id="824cc-334">Dependency properties overview</span></span>](../advanced/dependency-properties-overview.md)
- [<span data-ttu-id="824cc-335">Rozložení</span><span class="sxs-lookup"><span data-stu-id="824cc-335">Layout</span></span>](../advanced/layout.md)

<span data-ttu-id="824cc-336">Další informace o vytváření aplikací naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="824cc-336">For more information about creating applications, see the following topics:</span></span>

- [<span data-ttu-id="824cc-337">Vývoj aplikací</span><span class="sxs-lookup"><span data-stu-id="824cc-337">Application development</span></span>](../app-development/index.md)
- [<span data-ttu-id="824cc-338">Ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="824cc-338">Controls</span></span>](../controls/index.md)
- [<span data-ttu-id="824cc-339">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="824cc-339">Data binding overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="824cc-340">Grafika a multimédia</span><span class="sxs-lookup"><span data-stu-id="824cc-340">Graphics and multimedia</span></span>](../graphics-multimedia/index.md)
- [<span data-ttu-id="824cc-341">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="824cc-341">Documents in WPF</span></span>](../advanced/documents-in-wpf.md)

## <a name="see-also"></a><span data-ttu-id="824cc-342">Viz také:</span><span class="sxs-lookup"><span data-stu-id="824cc-342">See also</span></span>

- [<span data-ttu-id="824cc-343">Přehled panelů</span><span class="sxs-lookup"><span data-stu-id="824cc-343">Panels overview</span></span>](../controls/panels-overview.md)
- [<span data-ttu-id="824cc-344">Přehled datových šablon</span><span class="sxs-lookup"><span data-stu-id="824cc-344">Data templating overview</span></span>](../data/data-templating-overview.md)
- [<span data-ttu-id="824cc-345">Sestavení aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="824cc-345">Build a WPF application</span></span>](../app-development/building-a-wpf-application-wpf.md)
- [<span data-ttu-id="824cc-346">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="824cc-346">Styles and templates</span></span>](../controls/styles-and-templates.md)
