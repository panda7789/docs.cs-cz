---
title: Vytvoření aplikace WPF v sadě Visual Studio
ms.date: 03/20/2019
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
ms.openlocfilehash: 9d0abd18b2242ab21e8a915caac1ff9e3216acd0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617277"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a><span data-ttu-id="bd52c-102">Návod: Moje první desktopová aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="bd52c-102">Walkthrough: My first WPF desktop application</span></span>

<span data-ttu-id="bd52c-103">V tomto článku se dozvíte, jak vyvíjet desktopové aplikace Windows Presentation Foundation (WPF), která obsahuje elementy, které jsou společné pro většinu aplikací WPF: Extensible Application Markup Language (XAML) značky, použití modelu code-behind, definice aplikací, ovládací prvky, rozložení, datové vazby a styly.</span><span class="sxs-lookup"><span data-stu-id="bd52c-103">This article shows you how to develop a Windows Presentation Foundation (WPF) desktop application that includes the elements that are common to most WPF applications: Extensible Application Markup Language (XAML) markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span> <span data-ttu-id="bd52c-104">K vývoji aplikace, používáte sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bd52c-104">To develop the application, you'll use Visual Studio.</span></span> 

<span data-ttu-id="bd52c-105">Tento návod zahrnuje následující kroky:</span><span class="sxs-lookup"><span data-stu-id="bd52c-105">This walkthrough includes the following steps:</span></span>

- <span data-ttu-id="bd52c-106">Umožňuje navrhnout vzhled uživatelského rozhraní (UI) pro aplikace XAML.</span><span class="sxs-lookup"><span data-stu-id="bd52c-106">Use XAML to design the appearance of the application's user interface (UI).</span></span>

- <span data-ttu-id="bd52c-107">Napsání kódu pro sestavení chování aplikace.</span><span class="sxs-lookup"><span data-stu-id="bd52c-107">Write code to build the application's behavior.</span></span>

- <span data-ttu-id="bd52c-108">Vytvořte definici aplikace ke správě aplikace.</span><span class="sxs-lookup"><span data-stu-id="bd52c-108">Create an application definition to manage the application.</span></span>

- <span data-ttu-id="bd52c-109">Přidání ovládacích prvků a vytvořit rozložení k vytvoření uživatelského rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="bd52c-109">Add controls and create the layout to compose the application UI.</span></span>

- <span data-ttu-id="bd52c-110">Vytvoření styly pro konzistentní vzhled uživatelského rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="bd52c-110">Create styles for a consistent appearance throughout the application's UI.</span></span>

- <span data-ttu-id="bd52c-111">Připojení k datům, k naplnění uživatelského rozhraní z dat a vaše data uživatelského rozhraní a synchronizovány uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bd52c-111">Bind the UI to data, both to populate the UI from data and to keep the data and UI synchronized.</span></span>

<span data-ttu-id="bd52c-112">Na konci návodu budete sestavíte samostatnou aplikaci Windows, která umožňuje uživatelům zobrazit vyúčtování pro vybraného uživatele.</span><span class="sxs-lookup"><span data-stu-id="bd52c-112">By the end of the walkthrough, you'll have built a standalone Windows application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="bd52c-113">Aplikace se skládá z několika stránek WPF, které jsou hostované v okně prohlížeče – vizuální styl.</span><span class="sxs-lookup"><span data-stu-id="bd52c-113">The application is composed of several WPF pages that are hosted in a browser-style window.</span></span>

> [!TIP]
> <span data-ttu-id="bd52c-114">Ukázkový kód, který se používá k vytvoření tohoto návodu je k dispozici i v jazyce Visual Basic a C# na [ukázkového kódu aplikace WPF návod](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span><span class="sxs-lookup"><span data-stu-id="bd52c-114">The sample code that is used to build this walkthrough is available for both Visual Basic and C# at [Walkthrough WPF App Sample Code](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span></span>
>
> <span data-ttu-id="bd52c-115">Můžete přepínat na jazyk kódu ukázek kódu mezi C# a Visual Basic pomocí **\< />** rozevíracího seznamu v horní pravé části tohoto článku.</span><span class="sxs-lookup"><span data-stu-id="bd52c-115">You can toggle the code language of the sample code between C# and Visual Basic by using the **\</>** drop-down on the upper right side of this article.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bd52c-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bd52c-116">Prerequisites</span></span>

- <span data-ttu-id="bd52c-117">Visual Studio 2017 nebo novější</span><span class="sxs-lookup"><span data-stu-id="bd52c-117">Visual Studio 2017 or later</span></span>

   <span data-ttu-id="bd52c-118">Další informace o instalaci nejnovější verze sady Visual Studio najdete v tématu [instalace sady Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="bd52c-118">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span> <span data-ttu-id="bd52c-119">Tento článek používá Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="bd52c-119">This article uses Visual Studio 2019.</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="bd52c-120">Vytvoření projektu aplikace</span><span class="sxs-lookup"><span data-stu-id="bd52c-120">Create the application project</span></span>

<span data-ttu-id="bd52c-121">Prvním krokem je vytvoření aplikační infrastruktury, který obsahuje definici aplikace, dvě stránky a bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="bd52c-121">The first step is to create the application infrastructure, which includes an application definition, two pages, and an image.</span></span>

1. <span data-ttu-id="bd52c-122">Vytvoření nového projektu aplikace WPF v jazyce Visual Basic nebo Visual C# s názvem **`ExpenseIt`**:</span><span class="sxs-lookup"><span data-stu-id="bd52c-122">Create a new WPF Application project in Visual Basic or Visual C# named **`ExpenseIt`**:</span></span>

   1. <span data-ttu-id="bd52c-123">Otevřít Visual Studio a vyberte **souboru** > **nový** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="bd52c-123">Open Visual Studio and select **File** > **New** > **Project**.</span></span>

      <span data-ttu-id="bd52c-124">**Vytvořte nový projekt** otevře se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="bd52c-124">The **Create a new project** dialog opens.</span></span>

      ![Vytvořit dialogové okno nového projektu](./media/gettingstartedfigure0a.png)

   2. <span data-ttu-id="bd52c-126">V **jazyk** rozevírací seznam, vyberte buď **C#** nebo **jazyka Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="bd52c-126">In the **Language** dropdown, select either **C#** or **Visual Basic**.</span></span>

   3. <span data-ttu-id="bd52c-127">Vyberte **aplikace WPF (.NET Framework)** šablonu a pak vyberte **Další**.</span><span class="sxs-lookup"><span data-stu-id="bd52c-127">Select the **WPF App (.NET Framework)** template and then select **Next**.</span></span> 
    
   4. <span data-ttu-id="bd52c-128">Vyberte **vytvořte nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="bd52c-128">Select **Create a new project**.</span></span>

      <span data-ttu-id="bd52c-129">**Konfigurovat nový projekt** otevře se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="bd52c-129">The **Configure a new project** dialog opens.</span></span>

      ![Konfigurace dialogové okno nového projektu](./media/gettingstartedfigure0c.png)

   5. <span data-ttu-id="bd52c-131">Zadejte název projektu **`ExpenseIt`** a pak vyberte **vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="bd52c-131">Enter the project name **`ExpenseIt`** and then select **Create**.</span></span>

      <span data-ttu-id="bd52c-132">Visual Studio vytvoří projekt a otevře se návrhář pro výchozí okno aplikace s názvem **souboru MainWindow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="bd52c-132">Visual Studio creates the project and opens the designer for the default application window named **MainWindow.xaml**.</span></span>

2. <span data-ttu-id="bd52c-133">Otevřít *Application.xaml* (Visual Basic) nebo *App.xaml* (C#).</span><span class="sxs-lookup"><span data-stu-id="bd52c-133">Open *Application.xaml* (Visual Basic) or *App.xaml* (C#).</span></span>

    <span data-ttu-id="bd52c-134">Tento soubor XAML definuje aplikace WPF a všechny prostředky, aplikace.</span><span class="sxs-lookup"><span data-stu-id="bd52c-134">This XAML file defines a WPF application and any application resources.</span></span> <span data-ttu-id="bd52c-135">Tento soubor k zadání uživatelského rozhraní, v tomto případě použijete také *souboru MainWindow.xaml*, která automaticky zobrazí při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="bd52c-135">You also use this file to specify the UI, in this case *MainWindow.xaml*, that automatically shows when the application starts.</span></span>

    <span data-ttu-id="bd52c-136">Vaše XAML by měl vypadat nějak takto v jazyce Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="bd52c-136">Your XAML should look like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    <span data-ttu-id="bd52c-137">A stejně jako v následující C#:</span><span class="sxs-lookup"><span data-stu-id="bd52c-137">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. <span data-ttu-id="bd52c-138">Otevřít *souboru MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="bd52c-138">Open *MainWindow.xaml*.</span></span>

    <span data-ttu-id="bd52c-139">Tento soubor XAML je hlavní okno aplikace a zobrazí obsah vytvořený na stránkách.</span><span class="sxs-lookup"><span data-stu-id="bd52c-139">This XAML file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="bd52c-140"><xref:System.Windows.Window> Třídy definuje vlastnosti okna, například jeho název, velikost nebo ikonu a zpracovává události, jako je například zavření nebo skrytí.</span><span class="sxs-lookup"><span data-stu-id="bd52c-140">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span>

4. <span data-ttu-id="bd52c-141">Změnit <xref:System.Windows.Window> elementu <xref:System.Windows.Navigation.NavigationWindow>, jak je znázorněno v následující XAML:</span><span class="sxs-lookup"><span data-stu-id="bd52c-141">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>, as shown in the following XAML:</span></span>

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   <span data-ttu-id="bd52c-142">Tato aplikace přejde na jiný obsah v závislosti na vstupu uživatele.</span><span class="sxs-lookup"><span data-stu-id="bd52c-142">This app navigates to different content depending on the user input.</span></span> <span data-ttu-id="bd52c-143">To je důvod, proč hlavní <xref:System.Windows.Window> musí změnit tak, aby <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="bd52c-143">This is why the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="bd52c-144"><xref:System.Windows.Navigation.NavigationWindow> zdědí všechny vlastnosti <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="bd52c-144"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="bd52c-145"><xref:System.Windows.Navigation.NavigationWindow> Vytvoří instanci prvku v souboru XAML <xref:System.Windows.Navigation.NavigationWindow> třídy.</span><span class="sxs-lookup"><span data-stu-id="bd52c-145">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="bd52c-146">Další informace najdete v tématu [Přehled navigace](../app-development/navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bd52c-146">For more information, see [Navigation overview](../app-development/navigation-overview.md).</span></span>

5. <span data-ttu-id="bd52c-147">Odeberte <xref:System.Windows.Controls.Grid> prvky z mezi <xref:System.Windows.Navigation.NavigationWindow> značky.</span><span class="sxs-lookup"><span data-stu-id="bd52c-147">Remove the <xref:System.Windows.Controls.Grid> elements from between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span>

6. <span data-ttu-id="bd52c-148">Změňte následující vlastnosti v kódu XAML <xref:System.Windows.Navigation.NavigationWindow> element:</span><span class="sxs-lookup"><span data-stu-id="bd52c-148">Change the following properties in the XAML code for the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>

    - <span data-ttu-id="bd52c-149">Nastavte <xref:System.Windows.Window.Title%2A> vlastnost "`ExpenseIt`".</span><span class="sxs-lookup"><span data-stu-id="bd52c-149">Set the <xref:System.Windows.Window.Title%2A> property to "`ExpenseIt`".</span></span>

    - <span data-ttu-id="bd52c-150">Nastavte <xref:System.Windows.FrameworkElement.Height%2A> vlastnost na 350 pixelů.</span><span class="sxs-lookup"><span data-stu-id="bd52c-150">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span>

    - <span data-ttu-id="bd52c-151">Nastavte <xref:System.Windows.FrameworkElement.Width%2A> vlastnost na šířku 500 pixelů.</span><span class="sxs-lookup"><span data-stu-id="bd52c-151">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span>

    <span data-ttu-id="bd52c-152">Vaše XAML by měl vypadat nějak takto v jazyce Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="bd52c-152">Your XAML should look like the following for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    <span data-ttu-id="bd52c-153">A podobně jako následující C#:</span><span class="sxs-lookup"><span data-stu-id="bd52c-153">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. <span data-ttu-id="bd52c-154">Otevřít *soubor MainWindow.xaml.vb* nebo *MainWindow.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="bd52c-154">Open *MainWindow.xaml.vb* or *MainWindow.xaml.cs*.</span></span>

    <span data-ttu-id="bd52c-155">Tento soubor je soubor kódu na pozadí, který obsahuje kód pro zpracování události deklarované v *souboru MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="bd52c-155">This file is a code-behind file that contains code to handle the events declared in *MainWindow.xaml*.</span></span> <span data-ttu-id="bd52c-156">Tento soubor obsahuje částečné třídy pro okno definované v XAML.</span><span class="sxs-lookup"><span data-stu-id="bd52c-156">This file contains a partial class for the window defined in XAML.</span></span>

8. <span data-ttu-id="bd52c-157">Pokud používáte C#, změnit `MainWindow` třídy odvozovat z <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="bd52c-157">If you're using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="bd52c-158">(V jazyce Visual Basic, tomu automaticky dojde při změně okna v XAML.) Vaše C# kódu by teď měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="bd52c-158">(In Visual Basic, this happens automatically when you change the window in XAML.) Your C# code should now look like this:</span></span>

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a><span data-ttu-id="bd52c-159">Přidání souborů do aplikace</span><span class="sxs-lookup"><span data-stu-id="bd52c-159">Add files to the application</span></span>

<span data-ttu-id="bd52c-160">V této části přidáte dvě stránky a obrázku do aplikace.</span><span class="sxs-lookup"><span data-stu-id="bd52c-160">In this section, you'll add two pages and an image to the application.</span></span>

1. <span data-ttu-id="bd52c-161">Přidejte novou stránku do projektu a pojmenujte ho *`ExpenseItHome.xaml`*:</span><span class="sxs-lookup"><span data-stu-id="bd52c-161">Add a new page to the project, and name it *`ExpenseItHome.xaml`*:</span></span>

   1. <span data-ttu-id="bd52c-162">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **`ExpenseIt`** uzel projektu a zvolte **přidat** > **stránky**.</span><span class="sxs-lookup"><span data-stu-id="bd52c-162">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="bd52c-163">V **přidat novou položku** dialogového okna, **stránky (WPF)** šablony je už vybraná.</span><span class="sxs-lookup"><span data-stu-id="bd52c-163">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="bd52c-164">Zadejte název **`ExpenseItHome`** a pak vyberte **přidat**.</span><span class="sxs-lookup"><span data-stu-id="bd52c-164">Enter the name **`ExpenseItHome`**, and then select **Add**.</span></span>

    <span data-ttu-id="bd52c-165">Tato stránka je první stránka, která se zobrazí při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="bd52c-165">This page is the first page that's displayed when the application is launched.</span></span> <span data-ttu-id="bd52c-166">Zobrazí seznam uživatelů vyberte, chcete-li zobrazit sestavy výdajů pro.</span><span class="sxs-lookup"><span data-stu-id="bd52c-166">It will show a list of people to select from, to show an expense report for.</span></span>

1. <span data-ttu-id="bd52c-167">Otevřít *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="bd52c-167">Open *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="bd52c-168">Nastavte <xref:System.Windows.Controls.Page.Title%2A> na "`ExpenseIt - Home`".</span><span class="sxs-lookup"><span data-stu-id="bd52c-168">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - Home`".</span></span>

1. <span data-ttu-id="bd52c-169">Nastavte `DesignHeight` a `DesignWidth` hodnoty prvku na 300 pixelů.</span><span class="sxs-lookup"><span data-stu-id="bd52c-169">Set the `DesignHeight` and `DesignWidth` element values to 300 pixels.</span></span>

    <span data-ttu-id="bd52c-170">XAML se teď zobrazí následujícím způsobem v jazyce Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="bd52c-170">The XAML now appears as follows for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    <span data-ttu-id="bd52c-171">A podobně jako následující C#:</span><span class="sxs-lookup"><span data-stu-id="bd52c-171">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. <span data-ttu-id="bd52c-172">Otevřít *souboru MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="bd52c-172">Open *MainWindow.xaml*.</span></span>

1. <span data-ttu-id="bd52c-173">Přidat <xref:System.Windows.Navigation.NavigationWindow.Source%2A> vlastnost <xref:System.Windows.Navigation.NavigationWindow> elementu a nastavte ho na "`ExpenseItHome.xaml`".</span><span class="sxs-lookup"><span data-stu-id="bd52c-173">Add a <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property to the <xref:System.Windows.Navigation.NavigationWindow> element and set it to "`ExpenseItHome.xaml`".</span></span>

    <span data-ttu-id="bd52c-174">Tím se nastaví *`ExpenseItHome.xaml`* bude první stránka otevře při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="bd52c-174">This sets *`ExpenseItHome.xaml`* to be the first page opened when the application starts.</span></span> 

    <span data-ttu-id="bd52c-175">Příklad XAML v jazyce Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="bd52c-175">Example XAML in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    <span data-ttu-id="bd52c-176">A v jazyce C#:</span><span class="sxs-lookup"><span data-stu-id="bd52c-176">And in C#:</span></span>

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > <span data-ttu-id="bd52c-177">Můžete také nastavit **zdroj** vlastnost **různé** kategorii **vlastnosti** okna.</span><span class="sxs-lookup"><span data-stu-id="bd52c-177">You can also set the **Source** property in the **Miscellaneous** category of the **Properties** window.</span></span>
   >
   > ![Source – vlastnost v okně Vlastnosti](./media/properties-source.png)

1. <span data-ttu-id="bd52c-179">Do projektu přidejte další novou stránku WPF a pojmenujte ho *ExpenseReportPage.xaml*::</span><span class="sxs-lookup"><span data-stu-id="bd52c-179">Add another new WPF page to the project, and name it *ExpenseReportPage.xaml*::</span></span>

   1. <span data-ttu-id="bd52c-180">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **`ExpenseIt`** uzel projektu a zvolte **přidat** > **stránky**.</span><span class="sxs-lookup"><span data-stu-id="bd52c-180">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="bd52c-181">V **přidat novou položku** dialogového okna, vyberte **stránky (WPF)** šablony.</span><span class="sxs-lookup"><span data-stu-id="bd52c-181">In the **Add New Item** dialog, select the **Page (WPF)** template.</span></span> <span data-ttu-id="bd52c-182">Zadejte název **ExpenseReportPage**a pak vyberte **přidat**.</span><span class="sxs-lookup"><span data-stu-id="bd52c-182">Enter the name **ExpenseReportPage**, and then select **Add**.</span></span>

    <span data-ttu-id="bd52c-183">Na této stránce se zobrazí vyúčtování pro osoby, která je vybrán na **`ExpenseItHome`** stránky.</span><span class="sxs-lookup"><span data-stu-id="bd52c-183">This page will show the expense report for the person that is selected on the **`ExpenseItHome`** page.</span></span>

1. <span data-ttu-id="bd52c-184">Otevřít *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="bd52c-184">Open *ExpenseReportPage.xaml*.</span></span>

1. <span data-ttu-id="bd52c-185">Nastavte <xref:System.Windows.Controls.Page.Title%2A> na "`ExpenseIt - View Expense`".</span><span class="sxs-lookup"><span data-stu-id="bd52c-185">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - View Expense`".</span></span>

1. <span data-ttu-id="bd52c-186">Nastavte `DesignHeight` a `DesignWidth` hodnoty prvku na 300 pixelů.</span><span class="sxs-lookup"><span data-stu-id="bd52c-186">Set the `DesignHeight` and `DesignWidth` element values to 300 pixels.</span></span>

    <span data-ttu-id="bd52c-187">*ExpenseReportPage.xaml* teď vypadá podobně jako následující v jazyce Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="bd52c-187">*ExpenseReportPage.xaml* now looks like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    <span data-ttu-id="bd52c-188">A stejně jako v následující C#:</span><span class="sxs-lookup"><span data-stu-id="bd52c-188">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. <span data-ttu-id="bd52c-189">Otevřít *ExpenseItHome.xaml.vb* a *ExpenseReportPage.xaml.vb*, nebo *ExpenseItHome.xaml.cs* a *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="bd52c-189">Open *ExpenseItHome.xaml.vb* and *ExpenseReportPage.xaml.vb*, or *ExpenseItHome.xaml.cs* and *ExpenseReportPage.xaml.cs*.</span></span>

    <span data-ttu-id="bd52c-190">Když vytvoříte nový soubor stránky, sada Visual Studio automaticky vytvoří jeho *použití modelu code-behind* souboru.</span><span class="sxs-lookup"><span data-stu-id="bd52c-190">When you create a new Page file, Visual Studio automatically creates its *code-behind* file.</span></span> <span data-ttu-id="bd52c-191">Tyto soubory použití modelu code-behind zpracování logiky reagovat na vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="bd52c-191">These code-behind files handle the logic for responding to user input.</span></span>

    <span data-ttu-id="bd52c-192">Váš kód by měl vypadat jako následující **`ExpenseItHome`**:</span><span class="sxs-lookup"><span data-stu-id="bd52c-192">Your code should look like the following for **`ExpenseItHome`**:</span></span>

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    <span data-ttu-id="bd52c-193">A podobně jako následující **ExpenseReportPage**:</span><span class="sxs-lookup"><span data-stu-id="bd52c-193">And like the following for **ExpenseReportPage**:</span></span>

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. <span data-ttu-id="bd52c-194">Přidání obrázku s názvem *watermark.png* do projektu.</span><span class="sxs-lookup"><span data-stu-id="bd52c-194">Add an image named *watermark.png* to the project.</span></span> <span data-ttu-id="bd52c-195">Můžete vytvořit vlastní image, zkopírujte soubor ve vzorku kódu nebo získat [tady](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span><span class="sxs-lookup"><span data-stu-id="bd52c-195">You can create your own image, copy the file from the sample code, or get it [here](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span></span>

    1. <span data-ttu-id="bd52c-196">Klikněte pravým tlačítkem na uzel projektu a vyberte **přidat** > **existující položku**, nebo stiskněte klávesu **Shift**+**Alt** + **A**.</span><span class="sxs-lookup"><span data-stu-id="bd52c-196">Right-click on the project node and select **Add** > **Existing Item**, or press **Shift**+**Alt**+**A**.</span></span>

    2. <span data-ttu-id="bd52c-197">V **přidat existující položku** dialogové okno, nastavte filtr souboru buď **všechny soubory** nebo **soubory bitových kopií**, přejděte k souboru bitové kopie, kterou chcete použít a potom vyberte **přidat** .</span><span class="sxs-lookup"><span data-stu-id="bd52c-197">In the **Add Existing Item** dialog, set the file filter to either **All Files** or **Image Files**, browse to the image file you want to use, and then select **Add**.</span></span>

## <a name="build-and-run-the-application"></a><span data-ttu-id="bd52c-198">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="bd52c-198">Build and run the application</span></span>

1. <span data-ttu-id="bd52c-199">Chcete-li sestavit a spustit aplikaci, stiskněte **F5** nebo vyberte **spustit ladění** z **ladění** nabídky.</span><span class="sxs-lookup"><span data-stu-id="bd52c-199">To build and run the application, press **F5** or select **Start Debugging** from the **Debug** menu.</span></span>

    <span data-ttu-id="bd52c-200">Následující obrázek znázorňuje aplikaci <xref:System.Windows.Navigation.NavigationWindow> tlačítka:</span><span class="sxs-lookup"><span data-stu-id="bd52c-200">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons:</span></span>

    ![Snímek obrazovky ExpenseIt – ukázka](./media/gettingstartedfigure1.png)

2. <span data-ttu-id="bd52c-202">Ukončete aplikaci se vraťte do sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bd52c-202">Close the application to return to Visual Studio.</span></span>

## <a name="create-the-layout"></a><span data-ttu-id="bd52c-203">Vytvořit rozložení</span><span class="sxs-lookup"><span data-stu-id="bd52c-203">Create the layout</span></span>

<span data-ttu-id="bd52c-204">Rozložení poskytuje seřazený umožňuje umístit prvky uživatelského rozhraní a také spravuje velikost a umístění těchto prvků při změně velikosti uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bd52c-204">Layout provides an ordered way to place UI elements, and also manages the size and position of those elements when a UI is resized.</span></span> <span data-ttu-id="bd52c-205">Rozložení se obvykle vytvoříte pomocí jednoho z následujících ovládacích prvků rozložení:</span><span class="sxs-lookup"><span data-stu-id="bd52c-205">You typically create a layout with one of the following layout controls:</span></span>

- <span data-ttu-id="bd52c-206"><xref:System.Windows.Controls.Canvas> -Vymezuje oblast, ve kterém můžete explicitně umísťovat podřízené prvky použitím souřadnic, které jsou relativní k oblasti plátna.</span><span class="sxs-lookup"><span data-stu-id="bd52c-206"><xref:System.Windows.Controls.Canvas> - Defines an area within which you can explicitly position child elements by using coordinates that are relative to the Canvas area.</span></span>
- <span data-ttu-id="bd52c-207"><xref:System.Windows.Controls.DockPanel> -Vymezuje oblast, ve kterém můžete uspořádat podřízené elementy vodorovně nebo svisle, relativně vůči sobě navzájem.</span><span class="sxs-lookup"><span data-stu-id="bd52c-207"><xref:System.Windows.Controls.DockPanel> - Defines an area where you can arrange child elements either horizontally or vertically, relative to each other.</span></span>
- <span data-ttu-id="bd52c-208"><xref:System.Windows.Controls.Grid> -Definuje flexibilní oblast mřížky, která se skládá ze sloupců a řádků.</span><span class="sxs-lookup"><span data-stu-id="bd52c-208"><xref:System.Windows.Controls.Grid> - Defines a flexible grid area that consists of columns and rows.</span></span>
- <span data-ttu-id="bd52c-209"><xref:System.Windows.Controls.StackPanel> -Uspořádává podřízené prvky do jednoho řádku, který může být orientovaný vodorovně nebo svisle.</span><span class="sxs-lookup"><span data-stu-id="bd52c-209"><xref:System.Windows.Controls.StackPanel> - Arranges child elements into a single line that can be oriented horizontally or vertically.</span></span>
- <span data-ttu-id="bd52c-210"><xref:System.Windows.Controls.VirtualizingStackPanel> -Uspořádá a Virtualizuje obsah na jednom řádku, který je orientovaný buď vodorovně nebo svisle.</span><span class="sxs-lookup"><span data-stu-id="bd52c-210"><xref:System.Windows.Controls.VirtualizingStackPanel> - Arranges and virtualizes content on a single line that is oriented either horizontally or vertically.</span></span>
- <span data-ttu-id="bd52c-211"><xref:System.Windows.Controls.WrapPanel> -Umísťuje podřízené prvky do sekvenční Pozice zleva doprava, zásadní obsahu na další řádek na okraji obsahujícího pole.</span><span class="sxs-lookup"><span data-stu-id="bd52c-211"><xref:System.Windows.Controls.WrapPanel> - Positions child elements in sequential position from left to right, breaking content to the next line at the edge of the containing box.</span></span> <span data-ttu-id="bd52c-212">Následné řazení se děje sekvenčně shora dolů nebo zprava doleva v závislosti na hodnotě vlastnosti Orientation.</span><span class="sxs-lookup"><span data-stu-id="bd52c-212">Subsequent ordering happens sequentially from top to bottom or from right to left, depending on the value of the Orientation property.</span></span>

<span data-ttu-id="bd52c-213">Každá z těchto ovládacích prvků rozložení podporuje konkrétního typu rozložení pro jeho podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="bd52c-213">Each of these layout controls supports a particular type of layout for its child elements.</span></span> <span data-ttu-id="bd52c-214">`ExpenseIt` změnit velikost stránky, a každá stránka obsahuje prvky, které jsou uspořádány vodorovně a svisle vedle dalších prvků.</span><span class="sxs-lookup"><span data-stu-id="bd52c-214">`ExpenseIt` pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="bd52c-215">V tomto příkladu <xref:System.Windows.Controls.Grid> slouží jako prvek rozložení pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bd52c-215">In this example, the <xref:System.Windows.Controls.Grid> is used as  layout element for the application.</span></span>

> [!TIP]
> <span data-ttu-id="bd52c-216">Další informace o <xref:System.Windows.Controls.Panel> prvky, naleznete v tématu [přehled panelů](../controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bd52c-216">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels overview](../controls/panels-overview.md).</span></span> <span data-ttu-id="bd52c-217">Další informace o rozložení najdete v tématu [rozložení](../advanced/layout.md).</span><span class="sxs-lookup"><span data-stu-id="bd52c-217">For more information about layout, see [Layout](../advanced/layout.md).</span></span>

<span data-ttu-id="bd52c-218">V této části vytvoříte tabulku s jedním sloupcem se třemi řádky a 10 pixel okraj přidáním řádků a sloupců definice <xref:System.Windows.Controls.Grid> v *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="bd52c-218">In this section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="bd52c-219">V *`ExpenseItHome.xaml`*, nastavte <xref:System.Windows.FrameworkElement.Margin%2A> vlastnost <xref:System.Windows.Controls.Grid> prvku "10,0,10,10", která odpovídá na levé straně, horní, pravé a dolní okraj:</span><span class="sxs-lookup"><span data-stu-id="bd52c-219">In *`ExpenseItHome.xaml`*, set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10", which corresponds to left, top, right and bottom margins:</span></span>

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > <span data-ttu-id="bd52c-220">Můžete také nastavit **okraj** hodnoty v **vlastnosti** okně v části **rozložení** kategorie:</span><span class="sxs-lookup"><span data-stu-id="bd52c-220">You can also set the **Margin** values in the **Properties** window, under the **Layout** category:</span></span>
   >
   > ![Hodnoty vlastnosti okraj v okně Vlastnosti](./media/properties-margin.png)

2. <span data-ttu-id="bd52c-222">Přidejte následující XAML mezi <xref:System.Windows.Controls.Grid> značky vytvářet definice řádků a sloupců:</span><span class="sxs-lookup"><span data-stu-id="bd52c-222">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions:</span></span>

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <span data-ttu-id="bd52c-223"><xref:System.Windows.Controls.RowDefinition.Height%2A> Dva řádky se nastaví na <xref:System.Windows.GridLength.Auto%2A>, což znamená, že je nastavena velikost řádků na základě obsahu v řádcích.</span><span class="sxs-lookup"><span data-stu-id="bd52c-223">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A>, which means that the rows are sized based on the content in the rows.</span></span> <span data-ttu-id="bd52c-224">Výchozí hodnota <xref:System.Windows.Controls.RowDefinition.Height%2A> je <xref:System.Windows.GridUnitType.Star> velikosti, což znamená, že vážený poměr volného místa výšku řádku.</span><span class="sxs-lookup"><span data-stu-id="bd52c-224">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row height is a weighted proportion of the available space.</span></span> <span data-ttu-id="bd52c-225">Například pokud máte dva řádky <xref:System.Windows.Controls.RowDefinition.Height%2A> z "\*", každý z nich výška polovinu dostupné místo.</span><span class="sxs-lookup"><span data-stu-id="bd52c-225">For example if two rows each have a <xref:System.Windows.Controls.RowDefinition.Height%2A> of "\*", they each have a height that is half of the available space.</span></span>

    <span data-ttu-id="bd52c-226">Vaše <xref:System.Windows.Controls.Grid> by měl nyní obsahovat následující XAML:</span><span class="sxs-lookup"><span data-stu-id="bd52c-226">Your <xref:System.Windows.Controls.Grid> should now contain the following XAML:</span></span>

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a><span data-ttu-id="bd52c-227">Přidání ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="bd52c-227">Add controls</span></span>

<span data-ttu-id="bd52c-228">V této části budete aktualizovat na domovské stránce uživatelského rozhraní, zobrazí se seznam lidí, kde vyberete jedna osoba zobrazíte jejich vyúčtování.</span><span class="sxs-lookup"><span data-stu-id="bd52c-228">In this section, you'll update the home page UI to show a list of people, where you select one person to display their expense report.</span></span> <span data-ttu-id="bd52c-229">Ovládací prvky jsou objekty uživatelského rozhraní, které umožňují uživatelům, aby komunikovali s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="bd52c-229">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="bd52c-230">Další informace najdete v tématu [ovládací prvky](../controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="bd52c-230">For more information, see [Controls](../controls/index.md).</span></span>

<span data-ttu-id="bd52c-231">K vytvoření tohoto uživatelského rozhraní, přidejte následující prvky, které mají *`ExpenseItHome.xaml`*:</span><span class="sxs-lookup"><span data-stu-id="bd52c-231">To create this UI, you'll add the following elements to *`ExpenseItHome.xaml`*:</span></span>

- <span data-ttu-id="bd52c-232">A <xref:System.Windows.Controls.ListBox> (pro seznam lidí, kteří).</span><span class="sxs-lookup"><span data-stu-id="bd52c-232">A <xref:System.Windows.Controls.ListBox> (for the list of people).</span></span>
- <span data-ttu-id="bd52c-233">A <xref:System.Windows.Controls.Label> (pro hlavičku seznamu).</span><span class="sxs-lookup"><span data-stu-id="bd52c-233">A <xref:System.Windows.Controls.Label> (for the list header).</span></span>
- <span data-ttu-id="bd52c-234">A <xref:System.Windows.Controls.Button> (Chcete-li kliknutím zobrazíte vyúčtování pro osobu, která je v seznamu vyberete).</span><span class="sxs-lookup"><span data-stu-id="bd52c-234">A <xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span>

<span data-ttu-id="bd52c-235">Každý ovládací prvek nachází v řádku <xref:System.Windows.Controls.Grid> nastavením <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> přidružená vlastnost.</span><span class="sxs-lookup"><span data-stu-id="bd52c-235">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="bd52c-236">Další informace o přidružené vlastnosti najdete v tématu [přehled připojených vlastností](../advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bd52c-236">For more information about attached properties, see [Attached Properties Overview](../advanced/attached-properties-overview.md).</span></span>

1. <span data-ttu-id="bd52c-237">V *`ExpenseItHome.xaml`*, přidejte následující XAML někde mezi <xref:System.Windows.Controls.Grid> značky:</span><span class="sxs-lookup"><span data-stu-id="bd52c-237">In *`ExpenseItHome.xaml`*, add the following XAML somewhere between the <xref:System.Windows.Controls.Grid> tags:</span></span>

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > <span data-ttu-id="bd52c-238">Ovládací prvky můžete vytvořit také z jejich přetažením **nástrojů** okna do okna návrhu a nastavte jejich vlastnosti **vlastnosti** okna.</span><span class="sxs-lookup"><span data-stu-id="bd52c-238">You can also create the controls by dragging them from the **Toolbox** window onto the design window, and then setting their properties in the **Properties** window.</span></span>

2. <span data-ttu-id="bd52c-239">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bd52c-239">Build and run the application.</span></span>

    <span data-ttu-id="bd52c-240">Následující obrázek znázorňuje ovládací prvky, že kterou jste vytvořili:</span><span class="sxs-lookup"><span data-stu-id="bd52c-240">The following illustration shows the controls you created:</span></span>

    ![Snímek obrazovky ExpenseIt – ukázka](./media/gettingstartedfigure2.png)

3. <span data-ttu-id="bd52c-242">Ukončete aplikaci se vraťte do sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bd52c-242">Close the application to return to Visual Studio.</span></span>

## <a name="add-an-image-and-a-title"></a><span data-ttu-id="bd52c-243">Přidat obrázek a název</span><span class="sxs-lookup"><span data-stu-id="bd52c-243">Add an image and a title</span></span>

<span data-ttu-id="bd52c-244">V této části budete aktualizovat Uživatelském rozhraní domovské stránky s bitovou kopii a název stránky.</span><span class="sxs-lookup"><span data-stu-id="bd52c-244">In this section, you'll update the home page UI with an image and a page title.</span></span>

1. <span data-ttu-id="bd52c-245">V *`ExpenseItHome.xaml`*, přidejte jiný sloupec <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> s pevnou <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 pixelů:</span><span class="sxs-lookup"><span data-stu-id="bd52c-245">In *`ExpenseItHome.xaml`*, add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels:</span></span>

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=52-55)]

2. <span data-ttu-id="bd52c-246">Přidat další řádek <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, celkem čtyři řádky:</span><span class="sxs-lookup"><span data-stu-id="bd52c-246">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, for a total of four rows:</span></span>

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=57-62)]

3. <span data-ttu-id="bd52c-247">Přesuňte ovládací prvky na druhý sloupec tak, že nastavíte <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> vlastnost na hodnotu 1 v každé tři ovládací prvky (hranice ListBox a tlačítko).</span><span class="sxs-lookup"><span data-stu-id="bd52c-247">Move the controls to the second column by setting the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property to 1 in each of the three controls (Border, ListBox, and Button).</span></span>

4. <span data-ttu-id="bd52c-248">Každý ovládací prvek dolů řádek zvýšením jeho <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> hodnotu 1 pro všechny tři ovládací prvky (hranice ListBox a tlačítko) a ohraničení prvku.</span><span class="sxs-lookup"><span data-stu-id="bd52c-248">Move each control down a row by incrementing its <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> value by 1 for each of the three controls (Border, ListBox, and Button) and for the Border element.</span></span>

   <span data-ttu-id="bd52c-249">XAML pro tři ovládací prvky nyní vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="bd52c-249">The XAML for the three controls now looks like the following:</span></span>

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. <span data-ttu-id="bd52c-250">Nastavte <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> vlastnost *watermark.png* soubor obrázku, přidáním následující XAML kdekoli mezi `<Grid>` a `</Grid>` značky:</span><span class="sxs-lookup"><span data-stu-id="bd52c-250">Set the <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> property to the *watermark.png* image file, by adding the following XAML anywhere between the `<Grid>` and `</Grid>` tags:</span></span>

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. <span data-ttu-id="bd52c-251">Před <xref:System.Windows.Controls.Border> prvku, přidejte <xref:System.Windows.Controls.Label> s obsahem "Zobrazení vyúčtování".</span><span class="sxs-lookup"><span data-stu-id="bd52c-251">Before the <xref:System.Windows.Controls.Border> element, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report".</span></span> <span data-ttu-id="bd52c-252">Tento popisek je název stránky.</span><span class="sxs-lookup"><span data-stu-id="bd52c-252">This label is the title of the page.</span></span>

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. <span data-ttu-id="bd52c-253">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bd52c-253">Build and run the application.</span></span>

<span data-ttu-id="bd52c-254">Následující obrázek ukazuje výsledky co jste právě přidali:</span><span class="sxs-lookup"><span data-stu-id="bd52c-254">The following illustration shows the results of what you just added:</span></span>

![Snímek obrazovky ExpenseIt – ukázka](./media/gettingstartedfigure3.png)

## <a name="add-code-to-handle-events"></a><span data-ttu-id="bd52c-256">Přidejte kód pro zpracování událostí</span><span class="sxs-lookup"><span data-stu-id="bd52c-256">Add code to handle events</span></span>

1. <span data-ttu-id="bd52c-257">V *`ExpenseItHome.xaml`*, přidejte <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužnou rutinu události <xref:System.Windows.Controls.Button> elementu.</span><span class="sxs-lookup"><span data-stu-id="bd52c-257">In *`ExpenseItHome.xaml`*, add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="bd52c-258">Další informace najdete v tématu [jak: Vytvořte obslužnou rutinu události jednoduché](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="bd52c-258">For more information, see [How to: Create a simple event handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. <span data-ttu-id="bd52c-259">Otevřít *`ExpenseItHome.xaml.vb`* nebo *`ExpenseItHome.xaml.cs`*.</span><span class="sxs-lookup"><span data-stu-id="bd52c-259">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

3. <span data-ttu-id="bd52c-260">Přidejte následující kód, který `ExpenseItHome` třídy přidejte tlačítko klikněte na obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="bd52c-260">Add the following code to the `ExpenseItHome` class to add a button click event handler.</span></span> <span data-ttu-id="bd52c-261">Obslužná rutina události otevře **ExpenseReportPage** stránky.</span><span class="sxs-lookup"><span data-stu-id="bd52c-261">The event handler opens the **ExpenseReportPage** page.</span></span>

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a><span data-ttu-id="bd52c-262">Vytvoření uživatelského rozhraní pro ExpenseReportPage</span><span class="sxs-lookup"><span data-stu-id="bd52c-262">Create the UI for ExpenseReportPage</span></span>

<span data-ttu-id="bd52c-263">*ExpenseReportPage.xaml* zobrazí vyúčtování pro osobu, která je vybrán na **`ExpenseItHome`** stránky.</span><span class="sxs-lookup"><span data-stu-id="bd52c-263">*ExpenseReportPage.xaml* displays the expense report for the person that's selected on the **`ExpenseItHome`** page.</span></span> <span data-ttu-id="bd52c-264">V této části vytvoříte uživatelské rozhraní pro **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="bd52c-264">In this section, you'll create the UI for **ExpenseReportPage**.</span></span> <span data-ttu-id="bd52c-265">Budete také přidat na pozadí a vyplnit barev pro různé elementy uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bd52c-265">You'll also add background and fill colors to the various UI elements.</span></span>

1. <span data-ttu-id="bd52c-266">Otevřít *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="bd52c-266">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="bd52c-267">Přidejte následující XAML mezi <xref:System.Windows.Controls.Grid> značky:</span><span class="sxs-lookup"><span data-stu-id="bd52c-267">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags:</span></span>

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    <span data-ttu-id="bd52c-268">Toto uživatelské rozhraní je podobný *`ExpenseItHome.xaml`*, s výjimkou data sestavy se zobrazí v <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="bd52c-268">This UI is similar to *`ExpenseItHome.xaml`*, except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span>

3. <span data-ttu-id="bd52c-269">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bd52c-269">Build and run the application.</span></span>

4. <span data-ttu-id="bd52c-270">Vyberte **zobrazení** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="bd52c-270">Select the **View** button.</span></span>

    <span data-ttu-id="bd52c-271">Zobrazí se stránka sestavy výdajů.</span><span class="sxs-lookup"><span data-stu-id="bd52c-271">The expense report page appears.</span></span> <span data-ttu-id="bd52c-272">Všimněte si také, zda je povoleno tlačítko zpětné navigace.</span><span class="sxs-lookup"><span data-stu-id="bd52c-272">Also notice that the back navigation button is enabled.</span></span>

<span data-ttu-id="bd52c-273">Následující obrázek znázorňuje prvky uživatelského rozhraní, které jsou přidány do *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="bd52c-273">The following illustration shows the UI elements added to *ExpenseReportPage.xaml*.</span></span>

![Snímek obrazovky ExpenseIt – ukázka](./media/gettingstartedfigure4.png)

## <a name="style-controls"></a><span data-ttu-id="bd52c-275">Ovládací prvky stylu</span><span class="sxs-lookup"><span data-stu-id="bd52c-275">Style controls</span></span>

<span data-ttu-id="bd52c-276">Vzhled různé prvky je často stejný pro všechny prvky v uživatelském rozhraní stejného typu.</span><span class="sxs-lookup"><span data-stu-id="bd52c-276">The appearance of various elements is often the same for all elements of the same type in a UI.</span></span> <span data-ttu-id="bd52c-277">Uživatelské rozhraní používá [styly](../controls/styling-and-templating.md) k zajištění vzhled opakovaně použitelné napříč více prvků.</span><span class="sxs-lookup"><span data-stu-id="bd52c-277">UI uses [styles](../controls/styling-and-templating.md) to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="bd52c-278">Opětovné použití stylů pomáhá zjednodušit XAML vytváření a správu.</span><span class="sxs-lookup"><span data-stu-id="bd52c-278">The reusability of styles helps to simplify XAML creation and management.</span></span> <span data-ttu-id="bd52c-279">Tato část nahradí atributy na element, definované v předchozích krocích se styly.</span><span class="sxs-lookup"><span data-stu-id="bd52c-279">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span>

1. <span data-ttu-id="bd52c-280">Otevřít *Application.xaml* nebo *App.xaml*.</span><span class="sxs-lookup"><span data-stu-id="bd52c-280">Open *Application.xaml* or *App.xaml*.</span></span>

2. <span data-ttu-id="bd52c-281">Přidejte následující XAML mezi <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> značky:</span><span class="sxs-lookup"><span data-stu-id="bd52c-281">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    <span data-ttu-id="bd52c-282">Tento XAML přidá následující styly:</span><span class="sxs-lookup"><span data-stu-id="bd52c-282">This XAML adds the following styles:</span></span>

    - <span data-ttu-id="bd52c-283">`headerTextStyle`: Formátování názvu stránky <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="bd52c-283">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="bd52c-284">`labelStyle`: K formátování <xref:System.Windows.Controls.Label> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="bd52c-284">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span>

    - <span data-ttu-id="bd52c-285">`columnHeaderStyle`: K formátování <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span><span class="sxs-lookup"><span data-stu-id="bd52c-285">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span>

    - <span data-ttu-id="bd52c-286">`listHeaderStyle`: K formátování záhlaví seznamu <xref:System.Windows.Controls.Border> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="bd52c-286">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span>

    - <span data-ttu-id="bd52c-287">`listHeaderTextStyle`: K formátování záhlaví seznamu <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="bd52c-287">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="bd52c-288">`buttonStyle`: K formátování <xref:System.Windows.Controls.Button> na `ExpenseItHome.xaml`.</span><span class="sxs-lookup"><span data-stu-id="bd52c-288">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on `ExpenseItHome.xaml`.</span></span>

    <span data-ttu-id="bd52c-289">Všimněte si, že se styly prostředky a podřízené objekty daného <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> element vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="bd52c-289">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="bd52c-290">V tomto umístění se styly použijí na všechny prvky v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bd52c-290">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="bd52c-291">Příklad použití prostředků v aplikaci .NET, naleznete v tématu [využití prostředků aplikace](../advanced/how-to-use-application-resources.md).</span><span class="sxs-lookup"><span data-stu-id="bd52c-291">For an example of using resources in a .NET app, see [Use Application Resources](../advanced/how-to-use-application-resources.md).</span></span>

3. <span data-ttu-id="bd52c-292">V *`ExpenseItHome.xaml`*, nahradit všechno mezi <xref:System.Windows.Controls.Grid> prvky s následující XAML:</span><span class="sxs-lookup"><span data-stu-id="bd52c-292">In *`ExpenseItHome.xaml`*, replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    <span data-ttu-id="bd52c-293">Vlastnosti, jako <xref:System.Windows.VerticalAlignment> a <xref:System.Windows.Media.FontFamily> , které definují vzhled každého ovládacího prvku odebrán a nahrazen o aplikování stylů.</span><span class="sxs-lookup"><span data-stu-id="bd52c-293">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="bd52c-294">Například `headerTextStyle` platí pro "Zobrazení vyúčtování" <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="bd52c-294">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span>

4. <span data-ttu-id="bd52c-295">Otevřít *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="bd52c-295">Open *ExpenseReportPage.xaml*.</span></span>

5. <span data-ttu-id="bd52c-296">Nahradit vše mezi <xref:System.Windows.Controls.Grid> prvky s následující XAML:</span><span class="sxs-lookup"><span data-stu-id="bd52c-296">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    <span data-ttu-id="bd52c-297">Styly přidá tento XAML <xref:System.Windows.Controls.Label> a <xref:System.Windows.Controls.Border> elementy.</span><span class="sxs-lookup"><span data-stu-id="bd52c-297">This XAML adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span>

6. <span data-ttu-id="bd52c-298">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bd52c-298">Build and run the application.</span></span> <span data-ttu-id="bd52c-299">Vzhled okno je stejný jako dříve.</span><span class="sxs-lookup"><span data-stu-id="bd52c-299">The window appearance is the same as previously.</span></span>

    ![Snímek obrazovky ExpenseIt – ukázka](./media/gettingstartedfigure4.png)

7. <span data-ttu-id="bd52c-301">Ukončete aplikaci se vraťte do sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bd52c-301">Close the application to return to Visual Studio.</span></span>

## <a name="bind-data-to-a-control"></a><span data-ttu-id="bd52c-302">Vytvoření vazby dat k ovládacímu prvku</span><span class="sxs-lookup"><span data-stu-id="bd52c-302">Bind data to a control</span></span>

<span data-ttu-id="bd52c-303">V této části vytvoříte data XML, který je vázán na různé ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="bd52c-303">In this section, you'll create the XML data that is bound to various controls.</span></span>

1. <span data-ttu-id="bd52c-304">V *`ExpenseItHome.xaml`*, po zahájení <xref:System.Windows.Controls.Grid> elementu, přidejte následující XAML vytvořit <xref:System.Windows.Data.XmlDataProvider> , která pro každou osobu, která obsahuje data:</span><span class="sxs-lookup"><span data-stu-id="bd52c-304">In *`ExpenseItHome.xaml`*, after the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person:</span></span>

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    <span data-ttu-id="bd52c-305">Data se vytvoří jako <xref:System.Windows.Controls.Grid> prostředků.</span><span class="sxs-lookup"><span data-stu-id="bd52c-305">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="bd52c-306">Normálně by tato data načíst jako soubor, ale pro zjednodušení se přidat data vložené.</span><span class="sxs-lookup"><span data-stu-id="bd52c-306">Normally this data would be loaded as a file, but for simplicity the data is added inline.</span></span>

2. <span data-ttu-id="bd52c-307">V rámci `<Grid.Resources>` element, přidejte následující `<xref:System.Windows.DataTemplate>` element, který určuje způsob zobrazení dat v <xref:System.Windows.Controls.ListBox>, poté, co `<XmlDataProvider>` element:</span><span class="sxs-lookup"><span data-stu-id="bd52c-307">Within the `<Grid.Resources>` element, add the following `<xref:System.Windows.DataTemplate>` element, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>, after the `<XmlDataProvider>` element:</span></span>

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    <span data-ttu-id="bd52c-308">Další informace o šablonách dat, naleznete v tématu [přehled datových šablon](../data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bd52c-308">For more information about data templates, see [Data templating overview](../data/data-templating-overview.md).</span></span>

3. <span data-ttu-id="bd52c-309">Nahraďte existující <xref:System.Windows.Controls.ListBox> s následující XAML:</span><span class="sxs-lookup"><span data-stu-id="bd52c-309">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    <span data-ttu-id="bd52c-310">Tento XAML naváže <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost <xref:System.Windows.Controls.ListBox> ke zdroji dat a použije šablona dat jako <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span><span class="sxs-lookup"><span data-stu-id="bd52c-310">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span>

## <a name="connect-data-to-controls"></a><span data-ttu-id="bd52c-311">Připojení dat k ovládacím prvkům</span><span class="sxs-lookup"><span data-stu-id="bd52c-311">Connect data to controls</span></span>

<span data-ttu-id="bd52c-312">V dalším kroku přidáte kód pro načtení název, který je vybrán na **`ExpenseItHome`** stránku a předat konstruktoru **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="bd52c-312">Next, you'll add code to retrieve the name that's selected on the **`ExpenseItHome`** page and pass it to the constructor of **ExpenseReportPage**.</span></span> <span data-ttu-id="bd52c-313">**ExpenseReportPage** nastaví jeho kontext dat s předaným položka, která se, co ovládací prvky definované v *ExpenseReportPage.xaml* svázat.</span><span class="sxs-lookup"><span data-stu-id="bd52c-313">**ExpenseReportPage** sets its data context with the passed item, which is what the controls defined in *ExpenseReportPage.xaml* bind to.</span></span>

1. <span data-ttu-id="bd52c-314">Otevřít *ExpenseReportPage.xaml.vb* nebo *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="bd52c-314">Open *ExpenseReportPage.xaml.vb* or *ExpenseReportPage.xaml.cs*.</span></span>

2. <span data-ttu-id="bd52c-315">Přidáte konstruktor, který přebírá objekt, abyste mohli předat data sestavy výdajů z vybraného uživatele.</span><span class="sxs-lookup"><span data-stu-id="bd52c-315">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. <span data-ttu-id="bd52c-316">Otevřít *`ExpenseItHome.xaml.vb`* nebo *`ExpenseItHome.xaml.cs`*.</span><span class="sxs-lookup"><span data-stu-id="bd52c-316">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

4. <span data-ttu-id="bd52c-317">Změnit <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužná rutina události volaná nový konstruktor předávání dat sestavy výdajů z vybraného uživatele.</span><span class="sxs-lookup"><span data-stu-id="bd52c-317">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a><span data-ttu-id="bd52c-318">Styl dat s využitím šablon dat</span><span class="sxs-lookup"><span data-stu-id="bd52c-318">Style data with data templates</span></span>

<span data-ttu-id="bd52c-319">V této části budete aktualizovat uživatelské rozhraní pro každou položku v seznamu vázaných na data pomocí šablony.</span><span class="sxs-lookup"><span data-stu-id="bd52c-319">In this section, you'll update the UI for each item in the data-bound lists by using data templates.</span></span>

1. <span data-ttu-id="bd52c-320">Otevřít *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="bd52c-320">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="bd52c-321">Vytvoření vazby obsah "Name" a "Oddělení" <xref:System.Windows.Controls.Label> prvků, které se příslušná data source – vlastnost.</span><span class="sxs-lookup"><span data-stu-id="bd52c-321">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="bd52c-322">Další informace o datové vazbě naleznete v tématu [přehled datových vazeb](../data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bd52c-322">For more information about data binding, see [Data binding overview](../data/data-binding-overview.md).</span></span>

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. <span data-ttu-id="bd52c-323">Po zahájení <xref:System.Windows.Controls.Grid> prvku, přidejte následující datové šablony, které definují způsob zobrazení dat sestavy výdajů:</span><span class="sxs-lookup"><span data-stu-id="bd52c-323">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data:</span></span>

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. <span data-ttu-id="bd52c-324">Nahraďte <xref:System.Windows.Controls.DataGridTextColumn> prvky s <xref:System.Windows.Controls.DataGridTemplateColumn> pod <xref:System.Windows.Controls.DataGrid> elementu a použijte šablony k nim.</span><span class="sxs-lookup"><span data-stu-id="bd52c-324">Replace the <xref:System.Windows.Controls.DataGridTextColumn> elements with <xref:System.Windows.Controls.DataGridTemplateColumn> under the <xref:System.Windows.Controls.DataGrid> element and apply the templates to them.</span></span>

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. <span data-ttu-id="bd52c-325">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bd52c-325">Build and run the application.</span></span>

6. <span data-ttu-id="bd52c-326">Vybrat osobu a pak vyberte **zobrazení** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="bd52c-326">Select a person and then select the **View** button.</span></span>

<span data-ttu-id="bd52c-327">Následující obrázek ukazuje obě stránky `ExpenseIt` aplikace s ovládacími prvky, rozložení, styly, vazby dat a použitých šablon dat:</span><span class="sxs-lookup"><span data-stu-id="bd52c-327">The following illustration shows both pages of the `ExpenseIt` application with controls, layout, styles, data binding, and data templates applied:</span></span>

![Snímky obrazovky ExpenseIt – ukázka](./media/gettingstartedfigure5.png)

> [!NOTE]
> <span data-ttu-id="bd52c-329">Tato ukázka předvádí konkrétní funkce WPF a nebude použijte všechny osvědčené postupy pro takové věci, jako je zabezpečení, lokalizace a přístupnost.</span><span class="sxs-lookup"><span data-stu-id="bd52c-329">This sample demonstrates a specific feature of WPF and doesn't follow all best practices for things like security, localization, and accessibility.</span></span> <span data-ttu-id="bd52c-330">Komplexní pokrytí WPF a osvědčené postupy vývoje aplikací .NET najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="bd52c-330">For comprehensive coverage of WPF and the .NET app development best practices, see the following topics:</span></span>
>
> - [<span data-ttu-id="bd52c-331">Usnadnění</span><span class="sxs-lookup"><span data-stu-id="bd52c-331">Accessibility</span></span>](../../ui-automation/accessibility-best-practices.md)
>
> - [<span data-ttu-id="bd52c-332">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="bd52c-332">Security</span></span>](../security-wpf.md)
>
> - [<span data-ttu-id="bd52c-333">WPF globalizace a lokalizace</span><span class="sxs-lookup"><span data-stu-id="bd52c-333">WPF globalization and localization</span></span>](../advanced/wpf-globalization-and-localization-overview.md)
>
> - [<span data-ttu-id="bd52c-334">Výkonu WPF</span><span class="sxs-lookup"><span data-stu-id="bd52c-334">WPF performance</span></span>](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a><span data-ttu-id="bd52c-335">Další kroky</span><span class="sxs-lookup"><span data-stu-id="bd52c-335">Next steps</span></span>

<span data-ttu-id="bd52c-336">V tomto návodu jste zjistili několik technik pro vytvoření uživatelského rozhraní pomocí Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="bd52c-336">In this walkthrough you learned a number of techniques for creating a UI using Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="bd52c-337">Nyní byste měli mít základní znalosti o stavební kameny nástroje aplikace .NET vázané na data.</span><span class="sxs-lookup"><span data-stu-id="bd52c-337">You should now have a basic understanding of the building blocks of a data-bound .NET app.</span></span> <span data-ttu-id="bd52c-338">Další informace o WPF architekturu a programovací modely naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="bd52c-338">For more information about the WPF architecture and programming models, see the following topics:</span></span>

- [<span data-ttu-id="bd52c-339">Architektura WPF</span><span class="sxs-lookup"><span data-stu-id="bd52c-339">WPF architecture</span></span>](../advanced/wpf-architecture.md)
- [<span data-ttu-id="bd52c-340">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="bd52c-340">XAML overview (WPF)</span></span>](../advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="bd52c-341">Přehled vlastností závislosti</span><span class="sxs-lookup"><span data-stu-id="bd52c-341">Dependency properties overview</span></span>](../advanced/dependency-properties-overview.md)
- [<span data-ttu-id="bd52c-342">Rozložení</span><span class="sxs-lookup"><span data-stu-id="bd52c-342">Layout</span></span>](../advanced/layout.md)

<span data-ttu-id="bd52c-343">Další informace o vytváření aplikací naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="bd52c-343">For more information about creating applications, see the following topics:</span></span>

- [<span data-ttu-id="bd52c-344">Vývoj aplikací</span><span class="sxs-lookup"><span data-stu-id="bd52c-344">Application development</span></span>](../app-development/index.md)
- [<span data-ttu-id="bd52c-345">Ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="bd52c-345">Controls</span></span>](../controls/index.md)
- [<span data-ttu-id="bd52c-346">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="bd52c-346">Data binding overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="bd52c-347">Grafika a multimédia</span><span class="sxs-lookup"><span data-stu-id="bd52c-347">Graphics and multimedia</span></span>](../graphics-multimedia/index.md)
- [<span data-ttu-id="bd52c-348">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="bd52c-348">Documents in WPF</span></span>](../advanced/documents-in-wpf.md)

## <a name="see-also"></a><span data-ttu-id="bd52c-349">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bd52c-349">See also</span></span>

- [<span data-ttu-id="bd52c-350">Přehled panelů</span><span class="sxs-lookup"><span data-stu-id="bd52c-350">Panels overview</span></span>](../controls/panels-overview.md)
- [<span data-ttu-id="bd52c-351">Přehled datových šablon</span><span class="sxs-lookup"><span data-stu-id="bd52c-351">Data templating overview</span></span>](../data/data-templating-overview.md)
- [<span data-ttu-id="bd52c-352">Sestavení aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="bd52c-352">Build a WPF application</span></span>](../app-development/building-a-wpf-application-wpf.md)
- [<span data-ttu-id="bd52c-353">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="bd52c-353">Styles and templates</span></span>](../controls/styles-and-templates.md)
