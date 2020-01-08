---
title: 'Kurz: Vytvoření první aplikace WPF v aplikaci Visual Studio 2019 – .NET Framework'
ms.date: 09/06/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
ms.topic: tutorial
ms.custom: mvc,vs-dotnet
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7b5f74448ffce448740937c06a476a29c8659879
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75336813"
---
# <a name="tutorial-create-your-first-wpf-application-in-visual-studio-2019"></a><span data-ttu-id="bc48e-102">Kurz: Vytvoření první aplikace WPF v aplikaci Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="bc48e-102">Tutorial: Create your first WPF application in Visual Studio 2019</span></span>

<span data-ttu-id="bc48e-103">V tomto článku se dozvíte, jak vyvíjet desktopovou aplikaci Windows Presentation Foundation (WPF), která zahrnuje prvky společné pro většinu aplikací WPF: značky jazyk Extensible Application Markup Language (XAML) (XAML), kód na pozadí, definice aplikací, ovládací prvky, rozložení, datové vazby a styly.</span><span class="sxs-lookup"><span data-stu-id="bc48e-103">This article shows you how to develop a Windows Presentation Foundation (WPF) desktop application that includes the elements that are common to most WPF applications: Extensible Application Markup Language (XAML) markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span> <span data-ttu-id="bc48e-104">K vývoji aplikace použijete Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bc48e-104">To develop the application, you'll use Visual Studio.</span></span> 

<span data-ttu-id="bc48e-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="bc48e-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="bc48e-106">Vytvořte projekt WPF.</span><span class="sxs-lookup"><span data-stu-id="bc48e-106">Create a WPF project.</span></span>
> - <span data-ttu-id="bc48e-107">Použijte XAML pro návrh vzhledu uživatelského rozhraní (UI) aplikace.</span><span class="sxs-lookup"><span data-stu-id="bc48e-107">Use XAML to design the appearance of the application's user interface (UI).</span></span>
> - <span data-ttu-id="bc48e-108">Napíšete kód pro sestavení chování aplikace.</span><span class="sxs-lookup"><span data-stu-id="bc48e-108">Write code to build the application's behavior.</span></span>
> - <span data-ttu-id="bc48e-109">Vytvořte definici aplikace pro správu aplikace.</span><span class="sxs-lookup"><span data-stu-id="bc48e-109">Create an application definition to manage the application.</span></span>
> - <span data-ttu-id="bc48e-110">Přidejte ovládací prvky a vytvořte rozložení, abyste mohli vytvořit uživatelské rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="bc48e-110">Add controls and create the layout to compose the application UI.</span></span>
> - <span data-ttu-id="bc48e-111">Vytvářejte styly pro konzistentní vzhled v celém uživatelském rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="bc48e-111">Create styles for a consistent appearance throughout the application's UI.</span></span>
> - <span data-ttu-id="bc48e-112">Navažte uživatelské rozhraní na data a naplňte uživatelské rozhraní z dat a Udržujte data a uživatelské rozhraní synchronizované.</span><span class="sxs-lookup"><span data-stu-id="bc48e-112">Bind the UI to data, both to populate the UI from data and to keep the data and UI synchronized.</span></span>

<span data-ttu-id="bc48e-113">Na konci kurzu budete mít vytvořenou samostatnou aplikaci pro Windows, která uživatelům umožňuje zobrazit sestavy výdajů pro vybrané lidi.</span><span class="sxs-lookup"><span data-stu-id="bc48e-113">By the end of the tutorial, you'll have built a standalone Windows application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="bc48e-114">Aplikace se skládá z několika stránek WPF, které jsou hostovány v okně ve stylu prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="bc48e-114">The application is composed of several WPF pages that are hosted in a browser-style window.</span></span>

> [!TIP]
> <span data-ttu-id="bc48e-115">Vzorový kód, který se používá v tomto kurzu, je k dispozici pro C# Visual Basic i v [kurzu pro ukázkový kód aplikace WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span><span class="sxs-lookup"><span data-stu-id="bc48e-115">The sample code that is used in this tutorial is available for both Visual Basic and C# at [Tutorial WPF App Sample Code](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span></span>
>
> <span data-ttu-id="bc48e-116">Můžete přepínat jazyk kódu ukázkového kódu mezi C# a Visual Basic pomocí selektoru jazyka v horní části této stránky.</span><span class="sxs-lookup"><span data-stu-id="bc48e-116">You can toggle the code language of the sample code between C# and Visual Basic by using the language selector on top of this page.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bc48e-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bc48e-117">Prerequisites</span></span>

- <span data-ttu-id="bc48e-118">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou úlohou **vývoj desktopových aplikací .NET** .</span><span class="sxs-lookup"><span data-stu-id="bc48e-118">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET desktop development** workload installed.</span></span>

   <span data-ttu-id="bc48e-119">Další informace o instalaci nejnovější verze sady Visual Studio najdete v tématu [instalace sady Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="bc48e-119">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="bc48e-120">Vytvoření projektu aplikace</span><span class="sxs-lookup"><span data-stu-id="bc48e-120">Create the application project</span></span>

<span data-ttu-id="bc48e-121">Prvním krokem je vytvoření infrastruktury aplikace, která zahrnuje definici aplikace, dvě stránky a obrázek.</span><span class="sxs-lookup"><span data-stu-id="bc48e-121">The first step is to create the application infrastructure, which includes an application definition, two pages, and an image.</span></span>

1. <span data-ttu-id="bc48e-122">Vytvořte nový projekt aplikace WPF v Visual Basic nebo vizuálu C# s názvem **`ExpenseIt`** :</span><span class="sxs-lookup"><span data-stu-id="bc48e-122">Create a new WPF Application project in Visual Basic or Visual C# named **`ExpenseIt`**:</span></span>

   1. <span data-ttu-id="bc48e-123">Otevřete Visual Studio a **v nabídce Začínáme** vyberte **vytvořit nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="bc48e-123">Open Visual Studio and select **Create a new project** under the **Get started** menu.</span></span>

      <span data-ttu-id="bc48e-124">Otevře se dialogové okno **vytvořit nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="bc48e-124">The **Create a new project** dialog opens.</span></span>

   2. <span data-ttu-id="bc48e-125">V rozevíracím seznamu **jazyk** vyberte možnost **C#** nebo **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="bc48e-125">In the **Language** dropdown, select either **C#** or **Visual Basic**.</span></span>
      
   3. <span data-ttu-id="bc48e-126">Vyberte šablonu **aplikace WPF (.NET Framework)** a pak vyberte **Další**.</span><span class="sxs-lookup"><span data-stu-id="bc48e-126">Select the **WPF App (.NET Framework)** template and then select **Next**.</span></span> 
     
      ![Vytvořit nový projekt – dialogové okno](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)
    
      <span data-ttu-id="bc48e-128">Otevře se dialogové okno **Konfigurovat nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="bc48e-128">The **Configure your new project** dialog opens.</span></span>

   4. <span data-ttu-id="bc48e-129">Zadejte název projektu **`ExpenseIt`** a pak vyberte **vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="bc48e-129">Enter the project name **`ExpenseIt`** and then select **Create**.</span></span>

      ![Dialogové okno Konfigurovat nový projekt](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      <span data-ttu-id="bc48e-131">Visual Studio vytvoří projekt a otevře návrháře pro výchozí okno aplikace s názvem **MainWindow. XAML**.</span><span class="sxs-lookup"><span data-stu-id="bc48e-131">Visual Studio creates the project and opens the designer for the default application window named **MainWindow.xaml**.</span></span>

2. <span data-ttu-id="bc48e-132">Otevřete *Application. XAML* (Visual Basic) nebo *App. XAML* (C#).</span><span class="sxs-lookup"><span data-stu-id="bc48e-132">Open *Application.xaml* (Visual Basic) or *App.xaml* (C#).</span></span>

    <span data-ttu-id="bc48e-133">Tento soubor XAML definuje aplikaci WPF a všechny prostředky aplikace.</span><span class="sxs-lookup"><span data-stu-id="bc48e-133">This XAML file defines a WPF application and any application resources.</span></span> <span data-ttu-id="bc48e-134">Tento soubor můžete také použít k určení uživatelského rozhraní, v tomto případě *MainWindow. XAML*, který se automaticky zobrazí při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="bc48e-134">You also use this file to specify the UI, in this case *MainWindow.xaml*, that automatically shows when the application starts.</span></span>

    <span data-ttu-id="bc48e-135">Váš kód XAML by měl vypadat jako na následujícím Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="bc48e-135">Your XAML should look like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    <span data-ttu-id="bc48e-136">A podobně jako v C#následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="bc48e-136">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. <span data-ttu-id="bc48e-137">Otevřete *MainWindow. XAML*.</span><span class="sxs-lookup"><span data-stu-id="bc48e-137">Open *MainWindow.xaml*.</span></span>

    <span data-ttu-id="bc48e-138">Tento soubor XAML je hlavním oknem vaší aplikace a zobrazuje obsah vytvořený na stránkách.</span><span class="sxs-lookup"><span data-stu-id="bc48e-138">This XAML file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="bc48e-139">Třída <xref:System.Windows.Window> definuje vlastnosti okna, například jeho název, velikost nebo ikonu a zpracovává události, jako je například zavření nebo skrytí.</span><span class="sxs-lookup"><span data-stu-id="bc48e-139">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span>

4. <span data-ttu-id="bc48e-140">Změňte <xref:System.Windows.Window> element na <xref:System.Windows.Navigation.NavigationWindow>, jak je znázorněno v následujícím kódu XAML:</span><span class="sxs-lookup"><span data-stu-id="bc48e-140">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>, as shown in the following XAML:</span></span>

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   <span data-ttu-id="bc48e-141">Tato aplikace přejde na jiný obsah v závislosti na vstupu uživatele.</span><span class="sxs-lookup"><span data-stu-id="bc48e-141">This app navigates to different content depending on the user input.</span></span> <span data-ttu-id="bc48e-142">To je důvod, proč je nutné změnit hlavní <xref:System.Windows.Window> na <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="bc48e-142">This is why the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="bc48e-143"><xref:System.Windows.Navigation.NavigationWindow> dědí všechny vlastnosti <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="bc48e-143"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="bc48e-144">Prvek <xref:System.Windows.Navigation.NavigationWindow> v souboru XAML vytvoří instanci <xref:System.Windows.Navigation.NavigationWindow> třídy.</span><span class="sxs-lookup"><span data-stu-id="bc48e-144">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="bc48e-145">Další informace najdete v tématu [Přehled navigace](../app-development/navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bc48e-145">For more information, see [Navigation overview](../app-development/navigation-overview.md).</span></span>

5. <span data-ttu-id="bc48e-146">Odebere <xref:System.Windows.Controls.Grid> prvky mezi značkami <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="bc48e-146">Remove the <xref:System.Windows.Controls.Grid> elements from between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span>

6. <span data-ttu-id="bc48e-147">Změňte následující vlastnosti v kódu jazyka XAML pro prvek <xref:System.Windows.Navigation.NavigationWindow>:</span><span class="sxs-lookup"><span data-stu-id="bc48e-147">Change the following properties in the XAML code for the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>

    - <span data-ttu-id="bc48e-148">Vlastnost <xref:System.Windows.Window.Title%2A> nastavte na hodnotu "`ExpenseIt`".</span><span class="sxs-lookup"><span data-stu-id="bc48e-148">Set the <xref:System.Windows.Window.Title%2A> property to "`ExpenseIt`".</span></span>

    - <span data-ttu-id="bc48e-149">Nastavte vlastnost <xref:System.Windows.FrameworkElement.Height%2A> na 350 pixelů.</span><span class="sxs-lookup"><span data-stu-id="bc48e-149">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span>

    - <span data-ttu-id="bc48e-150">Nastavte vlastnost <xref:System.Windows.FrameworkElement.Width%2A> na 500 pixelů.</span><span class="sxs-lookup"><span data-stu-id="bc48e-150">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span>

    <span data-ttu-id="bc48e-151">Váš kód XAML by měl vypadat jako u Visual Basic následujících:</span><span class="sxs-lookup"><span data-stu-id="bc48e-151">Your XAML should look like the following for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    <span data-ttu-id="bc48e-152">A podobně jako následující pro C#:</span><span class="sxs-lookup"><span data-stu-id="bc48e-152">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. <span data-ttu-id="bc48e-153">Otevřete *MainWindow. XAML. vb* nebo *MainWindow.XAML.cs*.</span><span class="sxs-lookup"><span data-stu-id="bc48e-153">Open *MainWindow.xaml.vb* or *MainWindow.xaml.cs*.</span></span>

    <span data-ttu-id="bc48e-154">Tento soubor je soubor kódu na pozadí, který obsahuje kód pro zpracování událostí deklarované v souboru *MainWindow. XAML*.</span><span class="sxs-lookup"><span data-stu-id="bc48e-154">This file is a code-behind file that contains code to handle the events declared in *MainWindow.xaml*.</span></span> <span data-ttu-id="bc48e-155">Tento soubor obsahuje částečnou třídu pro okno definované v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="bc48e-155">This file contains a partial class for the window defined in XAML.</span></span>

8. <span data-ttu-id="bc48e-156">Pokud používáte C#, změňte třídu `MainWindow` tak, aby byla odvozena z <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="bc48e-156">If you're using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="bc48e-157">(V Visual Basic k tomu dochází automaticky při změně okna v jazyce XAML.) Váš C# kód by teď měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="bc48e-157">(In Visual Basic, this happens automatically when you change the window in XAML.) Your C# code should now look like this:</span></span>

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a><span data-ttu-id="bc48e-158">Přidat soubory do aplikace</span><span class="sxs-lookup"><span data-stu-id="bc48e-158">Add files to the application</span></span>

<span data-ttu-id="bc48e-159">V této části přidáte do aplikace dvě stránky a image.</span><span class="sxs-lookup"><span data-stu-id="bc48e-159">In this section, you'll add two pages and an image to the application.</span></span>

1. <span data-ttu-id="bc48e-160">Přidejte do projektu novou stránku a pojmenujte ji *`ExpenseItHome.xaml`* :</span><span class="sxs-lookup"><span data-stu-id="bc48e-160">Add a new page to the project, and name it *`ExpenseItHome.xaml`*:</span></span>

   1. <span data-ttu-id="bc48e-161">V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu **`ExpenseIt`** a vyberte možnost **Přidat** > **stránku**.</span><span class="sxs-lookup"><span data-stu-id="bc48e-161">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="bc48e-162">V dialogovém okně **Přidat novou položku** je již vybrána šablona **Stránka (WPF)** .</span><span class="sxs-lookup"><span data-stu-id="bc48e-162">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="bc48e-163">Zadejte název **`ExpenseItHome`** a pak vyberte **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="bc48e-163">Enter the name **`ExpenseItHome`**, and then select **Add**.</span></span>

    <span data-ttu-id="bc48e-164">Tato stránka je první stránkou, která se zobrazí při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="bc48e-164">This page is the first page that's displayed when the application is launched.</span></span> <span data-ttu-id="bc48e-165">Zobrazí se seznam lidí, ze kterých se má vybrat, aby se zobrazila sestava výdajů pro.</span><span class="sxs-lookup"><span data-stu-id="bc48e-165">It will show a list of people to select from, to show an expense report for.</span></span>

1. <span data-ttu-id="bc48e-166">Otevřete *`ExpenseItHome.xaml`* .</span><span class="sxs-lookup"><span data-stu-id="bc48e-166">Open *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="bc48e-167">Nastavte <xref:System.Windows.Controls.Page.Title%2A> na "`ExpenseIt - Home`".</span><span class="sxs-lookup"><span data-stu-id="bc48e-167">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - Home`".</span></span>

1. <span data-ttu-id="bc48e-168">Nastavte `DesignHeight` na 350 pixelů a `DesignWidth` na 500 pixelů.</span><span class="sxs-lookup"><span data-stu-id="bc48e-168">Set the `DesignHeight` to 350 pixels and the `DesignWidth` to 500 pixels.</span></span>

    <span data-ttu-id="bc48e-169">XAML se teď zobrazí jako Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="bc48e-169">The XAML now appears as follows for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    <span data-ttu-id="bc48e-170">A podobně jako následující pro C#:</span><span class="sxs-lookup"><span data-stu-id="bc48e-170">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. <span data-ttu-id="bc48e-171">Otevřete *MainWindow. XAML*.</span><span class="sxs-lookup"><span data-stu-id="bc48e-171">Open *MainWindow.xaml*.</span></span>

1. <span data-ttu-id="bc48e-172">Do prvku <xref:System.Windows.Navigation.NavigationWindow> přidejte vlastnost <xref:System.Windows.Navigation.NavigationWindow.Source%2A> a nastavte ji na "`ExpenseItHome.xaml`".</span><span class="sxs-lookup"><span data-stu-id="bc48e-172">Add a <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property to the <xref:System.Windows.Navigation.NavigationWindow> element and set it to "`ExpenseItHome.xaml`".</span></span>

    <span data-ttu-id="bc48e-173">Tato sada nastaví *`ExpenseItHome.xaml`* jako první stránku otevřenou při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="bc48e-173">This sets *`ExpenseItHome.xaml`* to be the first page opened when the application starts.</span></span> 

    <span data-ttu-id="bc48e-174">Příklad XAML v Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="bc48e-174">Example XAML in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    <span data-ttu-id="bc48e-175">A v jazyce C#:</span><span class="sxs-lookup"><span data-stu-id="bc48e-175">And in C#:</span></span>

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > <span data-ttu-id="bc48e-176">Vlastnost **source** můžete nastavit také v kategorii **různé** v okně **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="bc48e-176">You can also set the **Source** property in the **Miscellaneous** category of the **Properties** window.</span></span>
   >
   > ![Vlastnost source v okno Vlastnosti](./media/properties-source.png)

1. <span data-ttu-id="bc48e-178">Do projektu přidejte další novou stránku WPF a pojmenujte ji *ExpenseReportPage. XAML*::</span><span class="sxs-lookup"><span data-stu-id="bc48e-178">Add another new WPF page to the project, and name it *ExpenseReportPage.xaml*::</span></span>

   1. <span data-ttu-id="bc48e-179">V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu **`ExpenseIt`** a vyberte možnost **Přidat** > **stránku**.</span><span class="sxs-lookup"><span data-stu-id="bc48e-179">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="bc48e-180">V dialogovém okně **Přidat novou položku** vyberte šablonu **Stránka (WPF)** .</span><span class="sxs-lookup"><span data-stu-id="bc48e-180">In the **Add New Item** dialog, select the **Page (WPF)** template.</span></span> <span data-ttu-id="bc48e-181">Zadejte název **ExpenseReportPage**a pak vyberte **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="bc48e-181">Enter the name **ExpenseReportPage**, and then select **Add**.</span></span>

    <span data-ttu-id="bc48e-182">Na této stránce se zobrazí sestava výdajů pro osobu, která je vybrána na stránce **`ExpenseItHome`** .</span><span class="sxs-lookup"><span data-stu-id="bc48e-182">This page will show the expense report for the person that is selected on the **`ExpenseItHome`** page.</span></span>

1. <span data-ttu-id="bc48e-183">Otevřete *ExpenseReportPage. XAML*.</span><span class="sxs-lookup"><span data-stu-id="bc48e-183">Open *ExpenseReportPage.xaml*.</span></span>

1. <span data-ttu-id="bc48e-184">Nastavte <xref:System.Windows.Controls.Page.Title%2A> na "`ExpenseIt - View Expense`".</span><span class="sxs-lookup"><span data-stu-id="bc48e-184">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - View Expense`".</span></span>

1. <span data-ttu-id="bc48e-185">Nastavte `DesignHeight` na 350 pixelů a `DesignWidth` na 500 pixelů.</span><span class="sxs-lookup"><span data-stu-id="bc48e-185">Set the `DesignHeight` to 350 pixels and the `DesignWidth` to 500 pixels.</span></span> 

    <span data-ttu-id="bc48e-186">*ExpenseReportPage. XAML* teď vypadá jako na následujícím Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="bc48e-186">*ExpenseReportPage.xaml* now looks like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    <span data-ttu-id="bc48e-187">A podobně jako v C#následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="bc48e-187">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. <span data-ttu-id="bc48e-188">Otevřete *ExpenseItHome. XAML. vb* a *ExpenseReportPage. XAML. vb*nebo *ExpenseItHome.XAML.cs* a *ExpenseReportPage.XAML.cs*.</span><span class="sxs-lookup"><span data-stu-id="bc48e-188">Open *ExpenseItHome.xaml.vb* and *ExpenseReportPage.xaml.vb*, or *ExpenseItHome.xaml.cs* and *ExpenseReportPage.xaml.cs*.</span></span>

    <span data-ttu-id="bc48e-189">Při vytváření nového stránkovacího souboru aplikace Visual Studio automaticky vytvoří svůj soubor *kódu na pozadí* .</span><span class="sxs-lookup"><span data-stu-id="bc48e-189">When you create a new Page file, Visual Studio automatically creates its *code-behind* file.</span></span> <span data-ttu-id="bc48e-190">Tyto soubory s kódem na pozadí zpracovávají logiku pro reagování na vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="bc48e-190">These code-behind files handle the logic for responding to user input.</span></span>

    <span data-ttu-id="bc48e-191">Váš kód by měl vypadat jako následující pro **`ExpenseItHome`** :</span><span class="sxs-lookup"><span data-stu-id="bc48e-191">Your code should look like the following for **`ExpenseItHome`**:</span></span>

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    <span data-ttu-id="bc48e-192">A podobně jako v případě **ExpenseReportPage**postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="bc48e-192">And like the following for **ExpenseReportPage**:</span></span>

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. <span data-ttu-id="bc48e-193">Přidejte do projektu obrázek s názvem *vodotisk. png* .</span><span class="sxs-lookup"><span data-stu-id="bc48e-193">Add an image named *watermark.png* to the project.</span></span> <span data-ttu-id="bc48e-194">Můžete vytvořit vlastní image, zkopírovat soubor z ukázkového kódu nebo ho získat z úložiště GitHub [Microsoft/WPF-Samples](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png) .</span><span class="sxs-lookup"><span data-stu-id="bc48e-194">You can create your own image, copy the file from the sample code, or get it from the [microsoft/WPF-Samples](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png) GitHub repository.</span></span>

    1. <span data-ttu-id="bc48e-195">Klikněte pravým tlačítkem myši na uzel projektu a vyberte **přidat** > **existující položku**nebo stiskněte **SHIFT**+**ALT**+**A**.</span><span class="sxs-lookup"><span data-stu-id="bc48e-195">Right-click on the project node and select **Add** > **Existing Item**, or press **Shift**+**Alt**+**A**.</span></span>

    2. <span data-ttu-id="bc48e-196">V dialogovém okně **Přidat existující položku** nastavte filtr File buď na **všechny soubory** , nebo na **soubory obrázků**, vyhledejte soubor obrázku, který chcete použít, a pak vyberte **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="bc48e-196">In the **Add Existing Item** dialog, set the file filter to either **All Files** or **Image Files**, browse to the image file you want to use, and then select **Add**.</span></span>

## <a name="build-and-run-the-application"></a><span data-ttu-id="bc48e-197">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="bc48e-197">Build and run the application</span></span>

1. <span data-ttu-id="bc48e-198">Chcete-li sestavit a spustit aplikaci, stiskněte klávesu **F5** nebo vyberte možnost **Spustit ladění** z nabídky **ladění** .</span><span class="sxs-lookup"><span data-stu-id="bc48e-198">To build and run the application, press **F5** or select **Start Debugging** from the **Debug** menu.</span></span>

    <span data-ttu-id="bc48e-199">Následující ilustrace znázorňuje aplikaci s <xref:System.Windows.Navigation.NavigationWindow> tlačítky:</span><span class="sxs-lookup"><span data-stu-id="bc48e-199">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons:</span></span>

    ![Aplikace po sestavení a spuštění.](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. <span data-ttu-id="bc48e-201">Zavřete aplikaci a vraťte se do sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bc48e-201">Close the application to return to Visual Studio.</span></span>

## <a name="create-the-layout"></a><span data-ttu-id="bc48e-202">Vytvoření rozložení</span><span class="sxs-lookup"><span data-stu-id="bc48e-202">Create the layout</span></span>

<span data-ttu-id="bc48e-203">Rozložení poskytuje uspořádaný způsob, jak umístit prvky uživatelského rozhraní a také spravuje velikost a polohu těchto prvků při změně velikosti uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bc48e-203">Layout provides an ordered way to place UI elements, and also manages the size and position of those elements when a UI is resized.</span></span> <span data-ttu-id="bc48e-204">Rozložení obvykle vytvoříte pomocí jednoho z následujících ovládacích prvků rozložení:</span><span class="sxs-lookup"><span data-stu-id="bc48e-204">You typically create a layout with one of the following layout controls:</span></span>

- <span data-ttu-id="bc48e-205"><xref:System.Windows.Controls.Canvas> – definuje oblast, ve které můžete explicitně umístit podřízené prvky pomocí souřadnic, které jsou relativní k oblasti plátna.</span><span class="sxs-lookup"><span data-stu-id="bc48e-205"><xref:System.Windows.Controls.Canvas> - Defines an area within which you can explicitly position child elements by using coordinates that are relative to the Canvas area.</span></span>
- <span data-ttu-id="bc48e-206"><xref:System.Windows.Controls.DockPanel> – definuje oblast, kde můžete uspořádat podřízené elementy buď vodorovně, nebo svisle, vzhledem k sobě navzájem.</span><span class="sxs-lookup"><span data-stu-id="bc48e-206"><xref:System.Windows.Controls.DockPanel> - Defines an area where you can arrange child elements either horizontally or vertically, relative to each other.</span></span>
- <span data-ttu-id="bc48e-207"><xref:System.Windows.Controls.Grid> – definuje flexibilní oblast mřížky, která se skládá ze sloupců a řádků.</span><span class="sxs-lookup"><span data-stu-id="bc48e-207"><xref:System.Windows.Controls.Grid> - Defines a flexible grid area that consists of columns and rows.</span></span>
- <span data-ttu-id="bc48e-208"><xref:System.Windows.Controls.StackPanel> – uspořádá podřízené prvky na jeden řádek, který může být orientovaný vodorovně nebo svisle.</span><span class="sxs-lookup"><span data-stu-id="bc48e-208"><xref:System.Windows.Controls.StackPanel> - Arranges child elements into a single line that can be oriented horizontally or vertically.</span></span>
- <span data-ttu-id="bc48e-209"><xref:System.Windows.Controls.VirtualizingStackPanel> – uspořádá a virtualizuje obsah na jednom řádku, který je orientovaný buď vodorovně, nebo svisle.</span><span class="sxs-lookup"><span data-stu-id="bc48e-209"><xref:System.Windows.Controls.VirtualizingStackPanel> - Arranges and virtualizes content on a single line that is oriented either horizontally or vertically.</span></span>
- <span data-ttu-id="bc48e-210"><xref:System.Windows.Controls.WrapPanel> – umístí podřízené prvky na sekvenční pozici zleva doprava a přeruší obsah na další řádek na okraji obsahujícího pole.</span><span class="sxs-lookup"><span data-stu-id="bc48e-210"><xref:System.Windows.Controls.WrapPanel> - Positions child elements in sequential position from left to right, breaking content to the next line at the edge of the containing box.</span></span> <span data-ttu-id="bc48e-211">Následné řazení probíhá postupně shora dolů nebo zprava doleva v závislosti na hodnotě vlastnosti orientace.</span><span class="sxs-lookup"><span data-stu-id="bc48e-211">Subsequent ordering happens sequentially from top to bottom or from right to left, depending on the value of the Orientation property.</span></span>

<span data-ttu-id="bc48e-212">Každé z těchto ovládacích prvků rozložení podporuje konkrétní typ rozložení pro jeho podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="bc48e-212">Each of these layout controls supports a particular type of layout for its child elements.</span></span> <span data-ttu-id="bc48e-213">můžete změnit velikost `ExpenseIt` stránek a každá stránka obsahuje prvky, které jsou uspořádány vodorovně a svisle vedle ostatních prvků.</span><span class="sxs-lookup"><span data-stu-id="bc48e-213">`ExpenseIt` pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="bc48e-214">V tomto příkladu se <xref:System.Windows.Controls.Grid> používá jako element rozložení pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bc48e-214">In this example, the <xref:System.Windows.Controls.Grid> is used as  layout element for the application.</span></span>

> [!TIP]
> <span data-ttu-id="bc48e-215">Další informace o <xref:System.Windows.Controls.Panel> prvky naleznete v tématu [Přehled panelů](../controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bc48e-215">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels overview](../controls/panels-overview.md).</span></span> <span data-ttu-id="bc48e-216">Další informace o rozložení najdete v tématu [layout](../advanced/layout.md).</span><span class="sxs-lookup"><span data-stu-id="bc48e-216">For more information about layout, see [Layout](../advanced/layout.md).</span></span>

<span data-ttu-id="bc48e-217">V této části vytvoříte tabulku s jedním sloupcem se třemi řádky a okrajem 10 pixelů přidáním definice sloupců a řádků do <xref:System.Windows.Controls.Grid> v *`ExpenseItHome.xaml`* .</span><span class="sxs-lookup"><span data-stu-id="bc48e-217">In this section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="bc48e-218">V *`ExpenseItHome.xaml`* nastavte vlastnost <xref:System.Windows.FrameworkElement.Margin%2A> elementu <xref:System.Windows.Controls.Grid> na hodnotu "10, 0, 10, 10", která odpovídá levému, hornímu, pravému a dolnímu okraji:</span><span class="sxs-lookup"><span data-stu-id="bc48e-218">In *`ExpenseItHome.xaml`*, set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10", which corresponds to left, top, right and bottom margins:</span></span>

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > <span data-ttu-id="bc48e-219">Hodnoty **okrajů** můžete nastavit také v okně **vlastnosti** v kategorii **rozložení** :</span><span class="sxs-lookup"><span data-stu-id="bc48e-219">You can also set the **Margin** values in the **Properties** window, under the **Layout** category:</span></span>
   >
   > ![Hodnoty okrajů v okno Vlastnosti](./media/properties-margin.png)

2. <span data-ttu-id="bc48e-221">Přidejte následující XAML mezi značkami <xref:System.Windows.Controls.Grid> a vytvořte definice řádků a sloupců:</span><span class="sxs-lookup"><span data-stu-id="bc48e-221">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions:</span></span>

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <span data-ttu-id="bc48e-222"><xref:System.Windows.Controls.RowDefinition.Height%2A> dvou řádků je nastavena na hodnotu <xref:System.Windows.GridLength.Auto%2A>, což znamená, že řádky mají velikost na základě obsahu v řádcích.</span><span class="sxs-lookup"><span data-stu-id="bc48e-222">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A>, which means that the rows are sized based on the content in the rows.</span></span> <span data-ttu-id="bc48e-223">Výchozí <xref:System.Windows.Controls.RowDefinition.Height%2A> je <xref:System.Windows.GridUnitType.Star> velikosti, což znamená, že výška řádku je Vážený podíl dostupného místa.</span><span class="sxs-lookup"><span data-stu-id="bc48e-223">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row height is a weighted proportion of the available space.</span></span> <span data-ttu-id="bc48e-224">Pokud například dva řádky mají <xref:System.Windows.Controls.RowDefinition.Height%2A> "\*", každá z nich má výšku, která je polovinu dostupného místa.</span><span class="sxs-lookup"><span data-stu-id="bc48e-224">For example if two rows each have a <xref:System.Windows.Controls.RowDefinition.Height%2A> of "\*", they each have a height that is half of the available space.</span></span>

    <span data-ttu-id="bc48e-225">Váš <xref:System.Windows.Controls.Grid> by teď měl obsahovat následující kód XAML:</span><span class="sxs-lookup"><span data-stu-id="bc48e-225">Your <xref:System.Windows.Controls.Grid> should now contain the following XAML:</span></span>

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a><span data-ttu-id="bc48e-226">Přidat ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="bc48e-226">Add controls</span></span>

<span data-ttu-id="bc48e-227">V této části aktualizujete uživatelské rozhraní domovské stránky tak, aby zobrazovalo seznam lidí, kde vyberete jednu osobu k zobrazení své sestavy výdajů.</span><span class="sxs-lookup"><span data-stu-id="bc48e-227">In this section, you'll update the home page UI to show a list of people, where you select one person to display their expense report.</span></span> <span data-ttu-id="bc48e-228">Ovládací prvky jsou objekty uživatelského rozhraní, které umožňují uživatelům pracovat s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="bc48e-228">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="bc48e-229">Další informace najdete v tématu [ovládací prvky](../controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="bc48e-229">For more information, see [Controls](../controls/index.md).</span></span>

<span data-ttu-id="bc48e-230">Chcete-li vytvořit toto uživatelské rozhraní, přidejte následující prvky pro *`ExpenseItHome.xaml`* :</span><span class="sxs-lookup"><span data-stu-id="bc48e-230">To create this UI, you'll add the following elements to *`ExpenseItHome.xaml`*:</span></span>

- <span data-ttu-id="bc48e-231"><xref:System.Windows.Controls.ListBox> (pro seznam lidí).</span><span class="sxs-lookup"><span data-stu-id="bc48e-231">A <xref:System.Windows.Controls.ListBox> (for the list of people).</span></span>
- <span data-ttu-id="bc48e-232"><xref:System.Windows.Controls.Label> (pro záhlaví seznamu).</span><span class="sxs-lookup"><span data-stu-id="bc48e-232">A <xref:System.Windows.Controls.Label> (for the list header).</span></span>
- <span data-ttu-id="bc48e-233"><xref:System.Windows.Controls.Button> (Kliknutím zobrazíte sestavu výdajů pro osobu, která je vybrána v seznamu).</span><span class="sxs-lookup"><span data-stu-id="bc48e-233">A <xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span>

<span data-ttu-id="bc48e-234">Každý ovládací prvek je umístěn do řádku <xref:System.Windows.Controls.Grid> nastavením vlastnosti <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> připojené.</span><span class="sxs-lookup"><span data-stu-id="bc48e-234">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="bc48e-235">Další informace o připojených vlastnostech najdete v tématu [Přehled připojených vlastností](../advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bc48e-235">For more information about attached properties, see [Attached Properties Overview](../advanced/attached-properties-overview.md).</span></span>

1. <span data-ttu-id="bc48e-236">V *`ExpenseItHome.xaml`* přidejte následující XAML mezi značky <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="bc48e-236">In *`ExpenseItHome.xaml`*, add the following XAML somewhere between the <xref:System.Windows.Controls.Grid> tags:</span></span>

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > <span data-ttu-id="bc48e-237">Ovládací prvky lze také vytvořit přetažením z okna **panelu nástrojů** do okna návrh a následně nastavením jejich vlastností v okně **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="bc48e-237">You can also create the controls by dragging them from the **Toolbox** window onto the design window, and then setting their properties in the **Properties** window.</span></span>

2. <span data-ttu-id="bc48e-238">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bc48e-238">Build and run the application.</span></span>

    <span data-ttu-id="bc48e-239">Následující ilustrace znázorňuje ovládací prvky, které jste vytvořili:</span><span class="sxs-lookup"><span data-stu-id="bc48e-239">The following illustration shows the controls you created:</span></span>

![Ukázka ExpenseIt obrazovky zobrazující seznam názvů](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a><span data-ttu-id="bc48e-241">Přidání obrázku a názvu</span><span class="sxs-lookup"><span data-stu-id="bc48e-241">Add an image and a title</span></span>

<span data-ttu-id="bc48e-242">V této části aktualizujete uživatelské rozhraní domovské stránky s obrázkem a nadpisem stránky.</span><span class="sxs-lookup"><span data-stu-id="bc48e-242">In this section, you'll update the home page UI with an image and a page title.</span></span>

1. <span data-ttu-id="bc48e-243">V *`ExpenseItHome.xaml`* přidejte do <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> další sloupec s pevným <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 pixelů:</span><span class="sxs-lookup"><span data-stu-id="bc48e-243">In *`ExpenseItHome.xaml`*, add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels:</span></span>

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=52-55)]

2. <span data-ttu-id="bc48e-244">Přidat další řádek do <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, celkem čtyři řádky:</span><span class="sxs-lookup"><span data-stu-id="bc48e-244">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, for a total of four rows:</span></span>

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=57-62)]

3. <span data-ttu-id="bc48e-245">Přesuňte ovládací prvky do druhého sloupce nastavením vlastnosti <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> na hodnotu 1 v každém ze tří ovládacích prvků (Border, ListBox a Button).</span><span class="sxs-lookup"><span data-stu-id="bc48e-245">Move the controls to the second column by setting the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property to 1 in each of the three controls (Border, ListBox, and Button).</span></span>

4. <span data-ttu-id="bc48e-246">Přesuňte každý ovládací prvek dolů o jeden řádek posunutím hodnoty <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> o 1 pro každé tři ovládací prvky (ohraničení, seznam a tlačítko) a pro prvek ohraničení.</span><span class="sxs-lookup"><span data-stu-id="bc48e-246">Move each control down a row by incrementing its <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> value by 1 for each of the three controls (Border, ListBox, and Button) and for the Border element.</span></span>

   <span data-ttu-id="bc48e-247">XAML pro tři ovládací prvky nyní vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="bc48e-247">The XAML for the three controls now looks like the following:</span></span>

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. <span data-ttu-id="bc48e-248">Nastavte vlastnost <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> na soubor bitové kopie *. png* přidáním následujícího XAML kamkoli mezi značky `<Grid>` a `</Grid>`:</span><span class="sxs-lookup"><span data-stu-id="bc48e-248">Set the <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> property to the *watermark.png* image file, by adding the following XAML anywhere between the `<Grid>` and `</Grid>` tags:</span></span>

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. <span data-ttu-id="bc48e-249">Před prvkem <xref:System.Windows.Controls.Border> přidejte <xref:System.Windows.Controls.Label> s obsahem zobrazit sestavu výdajů.</span><span class="sxs-lookup"><span data-stu-id="bc48e-249">Before the <xref:System.Windows.Controls.Border> element, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report".</span></span> <span data-ttu-id="bc48e-250">Tento popisek je název stránky.</span><span class="sxs-lookup"><span data-stu-id="bc48e-250">This label is the title of the page.</span></span>

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. <span data-ttu-id="bc48e-251">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bc48e-251">Build and run the application.</span></span>

<span data-ttu-id="bc48e-252">Následující ilustrace znázorňuje výsledky toho, co jste právě přidali:</span><span class="sxs-lookup"><span data-stu-id="bc48e-252">The following illustration shows the results of what you just added:</span></span>

![Ukázka snímku obrazovky ExpenseIt zobrazující nové pozadí obrázku a nadpis stránky](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a><span data-ttu-id="bc48e-254">Přidat kód pro zpracování událostí</span><span class="sxs-lookup"><span data-stu-id="bc48e-254">Add code to handle events</span></span>

1. <span data-ttu-id="bc48e-255">V *`ExpenseItHome.xaml`* přidejte obslužnou rutinu události <xref:System.Windows.Controls.Primitives.ButtonBase.Click> do elementu <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="bc48e-255">In *`ExpenseItHome.xaml`*, add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="bc48e-256">Další informace najdete v tématu [Postup: Vytvoření jednoduché obslužné rutiny události](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="bc48e-256">For more information, see [How to: Create a simple event handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. <span data-ttu-id="bc48e-257">Otevřete *`ExpenseItHome.xaml.vb`* nebo *`ExpenseItHome.xaml.cs`* .</span><span class="sxs-lookup"><span data-stu-id="bc48e-257">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

3. <span data-ttu-id="bc48e-258">Přidejte následující kód do třídy `ExpenseItHome` pro přidání obslužné rutiny události kliknutí na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="bc48e-258">Add the following code to the `ExpenseItHome` class to add a button click event handler.</span></span> <span data-ttu-id="bc48e-259">Obslužná rutina události otevře stránku **ExpenseReportPage** .</span><span class="sxs-lookup"><span data-stu-id="bc48e-259">The event handler opens the **ExpenseReportPage** page.</span></span>

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a><span data-ttu-id="bc48e-260">Vytvoření uživatelského rozhraní pro ExpenseReportPage</span><span class="sxs-lookup"><span data-stu-id="bc48e-260">Create the UI for ExpenseReportPage</span></span>

<span data-ttu-id="bc48e-261">*ExpenseReportPage. XAML* zobrazí sestavu výdajů pro osobu, která je vybrána na stránce **`ExpenseItHome`** .</span><span class="sxs-lookup"><span data-stu-id="bc48e-261">*ExpenseReportPage.xaml* displays the expense report for the person that's selected on the **`ExpenseItHome`** page.</span></span> <span data-ttu-id="bc48e-262">V této části vytvoříte uživatelské rozhraní pro **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="bc48e-262">In this section, you'll create the UI for **ExpenseReportPage**.</span></span> <span data-ttu-id="bc48e-263">Do různých prvků uživatelského rozhraní také přidáte barvy pozadí a výplně.</span><span class="sxs-lookup"><span data-stu-id="bc48e-263">You'll also add background and fill colors to the various UI elements.</span></span>

1. <span data-ttu-id="bc48e-264">Otevřete *ExpenseReportPage. XAML*.</span><span class="sxs-lookup"><span data-stu-id="bc48e-264">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="bc48e-265">Přidejte následující kód XAML mezi značky <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="bc48e-265">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags:</span></span>

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    <span data-ttu-id="bc48e-266">Toto uživatelské rozhraní se podobá *`ExpenseItHome.xaml`* , s výjimkou toho, že se data sestavy zobrazují v <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="bc48e-266">This UI is similar to *`ExpenseItHome.xaml`*, except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span>

3. <span data-ttu-id="bc48e-267">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bc48e-267">Build and run the application.</span></span>

4. <span data-ttu-id="bc48e-268">Vyberte tlačítko **Zobrazit** .</span><span class="sxs-lookup"><span data-stu-id="bc48e-268">Select the **View** button.</span></span>

    <span data-ttu-id="bc48e-269">Zobrazí se stránka Sestava výdajů.</span><span class="sxs-lookup"><span data-stu-id="bc48e-269">The expense report page appears.</span></span> <span data-ttu-id="bc48e-270">Všimněte si také, že je povoleno tlačítko zpět navigace.</span><span class="sxs-lookup"><span data-stu-id="bc48e-270">Also notice that the back navigation button is enabled.</span></span>

<span data-ttu-id="bc48e-271">Následující ilustrace znázorňuje prvky uživatelského rozhraní přidané do souboru *ExpenseReportPage. XAML*.</span><span class="sxs-lookup"><span data-stu-id="bc48e-271">The following illustration shows the UI elements added to *ExpenseReportPage.xaml*.</span></span>

![Ukázka snímku obrazovky ExpenseIt zobrazující uživatelské rozhraní, které jste právě vytvořili pro ExpenseReportPage.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a><span data-ttu-id="bc48e-273">Ovládací prvky stylu</span><span class="sxs-lookup"><span data-stu-id="bc48e-273">Style controls</span></span>

<span data-ttu-id="bc48e-274">Vzhled různých prvků je často stejný pro všechny prvky stejného typu v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bc48e-274">The appearance of various elements is often the same for all elements of the same type in a UI.</span></span> <span data-ttu-id="bc48e-275">Uživatelské rozhraní používá [styly](../controls/styling-and-templating.md) , aby bylo možné vzhledy opakovaně použít napříč více prvky.</span><span class="sxs-lookup"><span data-stu-id="bc48e-275">UI uses [styles](../controls/styling-and-templating.md) to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="bc48e-276">Opětovné použitelnost stylů pomáhá zjednodušit vytváření a správu XAML.</span><span class="sxs-lookup"><span data-stu-id="bc48e-276">The reusability of styles helps to simplify XAML creation and management.</span></span> <span data-ttu-id="bc48e-277">Tato část nahrazuje atributy jednotlivých prvků, které byly definovány v předchozích krocích se styly.</span><span class="sxs-lookup"><span data-stu-id="bc48e-277">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span>

1. <span data-ttu-id="bc48e-278">Otevřete *Application. XAML* nebo *App. XAML*.</span><span class="sxs-lookup"><span data-stu-id="bc48e-278">Open *Application.xaml* or *App.xaml*.</span></span>

2. <span data-ttu-id="bc48e-279">Přidejte následující kód XAML mezi značky <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="bc48e-279">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    <span data-ttu-id="bc48e-280">Tento kód XAML přidá následující styly:</span><span class="sxs-lookup"><span data-stu-id="bc48e-280">This XAML adds the following styles:</span></span>

    - <span data-ttu-id="bc48e-281">`headerTextStyle`: pro naformátování <xref:System.Windows.Controls.Label>nadpisu stránky.</span><span class="sxs-lookup"><span data-stu-id="bc48e-281">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="bc48e-282">`labelStyle`: Chcete-li naformátovat <xref:System.Windows.Controls.Label> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="bc48e-282">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span>

    - <span data-ttu-id="bc48e-283">`columnHeaderStyle`: pro naformátování <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span><span class="sxs-lookup"><span data-stu-id="bc48e-283">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span>

    - <span data-ttu-id="bc48e-284">`listHeaderStyle`: pro formátování <xref:System.Windows.Controls.Border> ovládacích prvků záhlaví seznamu.</span><span class="sxs-lookup"><span data-stu-id="bc48e-284">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span>

    - <span data-ttu-id="bc48e-285">`listHeaderTextStyle`: Chcete-li naformátovat <xref:System.Windows.Controls.Label>záhlaví seznamu.</span><span class="sxs-lookup"><span data-stu-id="bc48e-285">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="bc48e-286">`buttonStyle`: pro naformátování <xref:System.Windows.Controls.Button> na `ExpenseItHome.xaml`.</span><span class="sxs-lookup"><span data-stu-id="bc48e-286">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on `ExpenseItHome.xaml`.</span></span>

    <span data-ttu-id="bc48e-287">Všimněte si, že styly jsou prostředky a podřízené prvky prvku vlastnosti <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bc48e-287">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="bc48e-288">V tomto umístění se styly aplikují na všechny prvky v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bc48e-288">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="bc48e-289">Příklad používání prostředků v aplikaci .NET najdete v tématu [použití prostředků aplikace](../advanced/how-to-use-application-resources.md).</span><span class="sxs-lookup"><span data-stu-id="bc48e-289">For an example of using resources in a .NET app, see [Use Application Resources](../advanced/how-to-use-application-resources.md).</span></span>

3. <span data-ttu-id="bc48e-290">V *`ExpenseItHome.xaml`* nahraďte vše mezi <xref:System.Windows.Controls.Grid> prvky následujícím XAML:</span><span class="sxs-lookup"><span data-stu-id="bc48e-290">In *`ExpenseItHome.xaml`*, replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    <span data-ttu-id="bc48e-291">Vlastnosti, jako <xref:System.Windows.VerticalAlignment> a <xref:System.Windows.Media.FontFamily> definující vzhled jednotlivých ovládacích prvků, jsou odebrány a nahrazeny použitím stylů.</span><span class="sxs-lookup"><span data-stu-id="bc48e-291">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="bc48e-292">`headerTextStyle` se například aplikuje na <xref:System.Windows.Controls.Label>zobrazit sestavu výdajů.</span><span class="sxs-lookup"><span data-stu-id="bc48e-292">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span>

4. <span data-ttu-id="bc48e-293">Otevřete *ExpenseReportPage. XAML*.</span><span class="sxs-lookup"><span data-stu-id="bc48e-293">Open *ExpenseReportPage.xaml*.</span></span>

5. <span data-ttu-id="bc48e-294">Nahraďte vše mezi prvky <xref:System.Windows.Controls.Grid> následujícím XAML:</span><span class="sxs-lookup"><span data-stu-id="bc48e-294">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    <span data-ttu-id="bc48e-295">Tento XAML přidá styly do prvků <xref:System.Windows.Controls.Label> a <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="bc48e-295">This XAML adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span>

6. <span data-ttu-id="bc48e-296">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bc48e-296">Build and run the application.</span></span> <span data-ttu-id="bc48e-297">Vzhled okna je stejný jako dříve.</span><span class="sxs-lookup"><span data-stu-id="bc48e-297">The window appearance is the same as previously.</span></span>

    ![ExpenseIt ukázkový snímek obrazovky se stejným vzhledem jako v poslední části.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. <span data-ttu-id="bc48e-299">Zavřete aplikaci a vraťte se do sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bc48e-299">Close the application to return to Visual Studio.</span></span>

## <a name="bind-data-to-a-control"></a><span data-ttu-id="bc48e-300">Vázání dat k ovládacímu prvku</span><span class="sxs-lookup"><span data-stu-id="bc48e-300">Bind data to a control</span></span>

<span data-ttu-id="bc48e-301">V této části vytvoříte data XML, která jsou svázána s různými ovládacími prvky.</span><span class="sxs-lookup"><span data-stu-id="bc48e-301">In this section, you'll create the XML data that is bound to various controls.</span></span>

1. <span data-ttu-id="bc48e-302">V *`ExpenseItHome.xaml`* po otevření elementu <xref:System.Windows.Controls.Grid> přidejte následující XAML k vytvoření <xref:System.Windows.Data.XmlDataProvider> obsahujícího data pro každou osobu:</span><span class="sxs-lookup"><span data-stu-id="bc48e-302">In *`ExpenseItHome.xaml`*, after the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person:</span></span>

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    <span data-ttu-id="bc48e-303">Data se vytvoří jako prostředek <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="bc48e-303">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="bc48e-304">Obvykle by se tato data načítala jako soubor, ale pro zjednodušení se data přidávají jako vložená.</span><span class="sxs-lookup"><span data-stu-id="bc48e-304">Normally this data would be loaded as a file, but for simplicity the data is added inline.</span></span>

2. <span data-ttu-id="bc48e-305">V rámci prvku `<Grid.Resources>` přidejte následující prvek `<xref:System.Windows.DataTemplate>`, který definuje, jak zobrazit data v <xref:System.Windows.Controls.ListBox>za element `<XmlDataProvider>`:</span><span class="sxs-lookup"><span data-stu-id="bc48e-305">Within the `<Grid.Resources>` element, add the following `<xref:System.Windows.DataTemplate>` element, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>, after the `<XmlDataProvider>` element:</span></span>

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    <span data-ttu-id="bc48e-306">Další informace o datových šablonách najdete v tématu [Přehled šablonování dat](../data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bc48e-306">For more information about data templates, see [Data templating overview](../data/data-templating-overview.md).</span></span>

3. <span data-ttu-id="bc48e-307">Existující <xref:System.Windows.Controls.ListBox> nahraďte následujícím XAML:</span><span class="sxs-lookup"><span data-stu-id="bc48e-307">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    <span data-ttu-id="bc48e-308">Tento kód XAML váže vlastnost <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ListBox> ke zdroji dat a použije šablonu dat jako <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span><span class="sxs-lookup"><span data-stu-id="bc48e-308">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span>

## <a name="connect-data-to-controls"></a><span data-ttu-id="bc48e-309">Připojení dat k ovládacím prvkům</span><span class="sxs-lookup"><span data-stu-id="bc48e-309">Connect data to controls</span></span>

<span data-ttu-id="bc48e-310">Dále přidáte kód, který načte název, který je vybrán na stránce **`ExpenseItHome`** a předáte ho konstruktoru třídy **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="bc48e-310">Next, you'll add code to retrieve the name that's selected on the **`ExpenseItHome`** page and pass it to the constructor of **ExpenseReportPage**.</span></span> <span data-ttu-id="bc48e-311">**ExpenseReportPage** nastaví svůj kontext dat s předanou položkou, která určuje ovládací prvky definované v rámci vazby *ExpenseReportPage. XAML* na.</span><span class="sxs-lookup"><span data-stu-id="bc48e-311">**ExpenseReportPage** sets its data context with the passed item, which is what the controls defined in *ExpenseReportPage.xaml* bind to.</span></span>

1. <span data-ttu-id="bc48e-312">Otevřete *ExpenseReportPage. XAML. vb* nebo *ExpenseReportPage.XAML.cs*.</span><span class="sxs-lookup"><span data-stu-id="bc48e-312">Open *ExpenseReportPage.xaml.vb* or *ExpenseReportPage.xaml.cs*.</span></span>

2. <span data-ttu-id="bc48e-313">Přidejte konstruktor, který převezme objekt, abyste mohli předat data sestavy výdajů vybrané osobě.</span><span class="sxs-lookup"><span data-stu-id="bc48e-313">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. <span data-ttu-id="bc48e-314">Otevřete *`ExpenseItHome.xaml.vb`* nebo *`ExpenseItHome.xaml.cs`* .</span><span class="sxs-lookup"><span data-stu-id="bc48e-314">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

4. <span data-ttu-id="bc48e-315">Změňte obslužnou rutinu události <xref:System.Windows.Controls.Primitives.ButtonBase.Click> pro volání nového konstruktoru, který předává data sestavy výdajů vybrané osobě.</span><span class="sxs-lookup"><span data-stu-id="bc48e-315">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a><span data-ttu-id="bc48e-316">Data stylu pomocí datových šablon</span><span class="sxs-lookup"><span data-stu-id="bc48e-316">Style data with data templates</span></span>

<span data-ttu-id="bc48e-317">V této části aktualizujete uživatelské rozhraní pro každou položku v seznamech vázaných na data pomocí datových šablon.</span><span class="sxs-lookup"><span data-stu-id="bc48e-317">In this section, you'll update the UI for each item in the data-bound lists by using data templates.</span></span>

1. <span data-ttu-id="bc48e-318">Otevřete *ExpenseReportPage. XAML*.</span><span class="sxs-lookup"><span data-stu-id="bc48e-318">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="bc48e-319">Navažte obsah názvu "název" a "oddělení" <xref:System.Windows.Controls.Label> prvky na odpovídající vlastnost zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="bc48e-319">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="bc48e-320">Další informace o datové vazbě najdete v tématu [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bc48e-320">For more information about data binding, see [Data binding overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. <span data-ttu-id="bc48e-321">Po otevření <xref:System.Windows.Controls.Grid> elementu přidejte následující šablony dat, které definují, jak zobrazit data sestavy výdajů:</span><span class="sxs-lookup"><span data-stu-id="bc48e-321">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data:</span></span>

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. <span data-ttu-id="bc48e-322">Nahraďte <xref:System.Windows.Controls.DataGridTextColumn> prvky <xref:System.Windows.Controls.DataGridTemplateColumn> pod elementem <xref:System.Windows.Controls.DataGrid> a použijte je pro šablony.</span><span class="sxs-lookup"><span data-stu-id="bc48e-322">Replace the <xref:System.Windows.Controls.DataGridTextColumn> elements with <xref:System.Windows.Controls.DataGridTemplateColumn> under the <xref:System.Windows.Controls.DataGrid> element and apply the templates to them.</span></span>

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. <span data-ttu-id="bc48e-323">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bc48e-323">Build and run the application.</span></span>

6. <span data-ttu-id="bc48e-324">Vyberte osobu a pak vyberte tlačítko **Zobrazit** .</span><span class="sxs-lookup"><span data-stu-id="bc48e-324">Select a person and then select the **View** button.</span></span>

<span data-ttu-id="bc48e-325">Následující ilustrace znázorňuje obě stránky `ExpenseIt` aplikace s ovládacími prvky, rozložením, styly, datovými vazbami a použitými šablonami dat:</span><span class="sxs-lookup"><span data-stu-id="bc48e-325">The following illustration shows both pages of the `ExpenseIt` application with controls, layout, styles, data binding, and data templates applied:</span></span>

![Obě stránky aplikace zobrazují seznam názvů a sestavu výdajů.](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> <span data-ttu-id="bc48e-327">Tato ukázka demonstruje konkrétní funkci WPF a nedodržuje všechny osvědčené postupy pro věci, jako je zabezpečení, lokalizace a přístupnost.</span><span class="sxs-lookup"><span data-stu-id="bc48e-327">This sample demonstrates a specific feature of WPF and doesn't follow all best practices for things like security, localization, and accessibility.</span></span> <span data-ttu-id="bc48e-328">Pro komplexní pokrytí prostředí WPF a osvědčených postupů vývoje aplikací .NET si přečtěte následující témata:</span><span class="sxs-lookup"><span data-stu-id="bc48e-328">For comprehensive coverage of WPF and the .NET app development best practices, see the following topics:</span></span>
>
> - [<span data-ttu-id="bc48e-329">Usnadnění</span><span class="sxs-lookup"><span data-stu-id="bc48e-329">Accessibility</span></span>](../../ui-automation/accessibility-best-practices.md)
> - [<span data-ttu-id="bc48e-330">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="bc48e-330">Security</span></span>](../security-wpf.md)
> - [<span data-ttu-id="bc48e-331">Globalizace a lokalizace WPF</span><span class="sxs-lookup"><span data-stu-id="bc48e-331">WPF globalization and localization</span></span>](../advanced/wpf-globalization-and-localization-overview.md)
> - [<span data-ttu-id="bc48e-332">Výkon WPF</span><span class="sxs-lookup"><span data-stu-id="bc48e-332">WPF performance</span></span>](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a><span data-ttu-id="bc48e-333">Další kroky</span><span class="sxs-lookup"><span data-stu-id="bc48e-333">Next steps</span></span>

<span data-ttu-id="bc48e-334">V tomto návodu jste se naučili řadou postupů pro vytvoření uživatelského rozhraní pomocí Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="bc48e-334">In this walkthrough you learned a number of techniques for creating a UI using Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="bc48e-335">Nyní byste měli mít základní znalosti stavebních bloků aplikace .NET vázané na data.</span><span class="sxs-lookup"><span data-stu-id="bc48e-335">You should now have a basic understanding of the building blocks of a data-bound .NET app.</span></span> <span data-ttu-id="bc48e-336">Další informace o architektuře a programovacích modelech WPF naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="bc48e-336">For more information about the WPF architecture and programming models, see the following topics:</span></span>

- [<span data-ttu-id="bc48e-337">Architektura WPF</span><span class="sxs-lookup"><span data-stu-id="bc48e-337">WPF architecture</span></span>](../advanced/wpf-architecture.md)
- [<span data-ttu-id="bc48e-338">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="bc48e-338">XAML overview (WPF)</span></span>](../advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="bc48e-339">Přehled vlastností závislosti</span><span class="sxs-lookup"><span data-stu-id="bc48e-339">Dependency properties overview</span></span>](../advanced/dependency-properties-overview.md)
- [<span data-ttu-id="bc48e-340">Rozložení</span><span class="sxs-lookup"><span data-stu-id="bc48e-340">Layout</span></span>](../advanced/layout.md)

<span data-ttu-id="bc48e-341">Další informace o vytváření aplikací naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="bc48e-341">For more information about creating applications, see the following topics:</span></span>

- [<span data-ttu-id="bc48e-342">Vývoj aplikací</span><span class="sxs-lookup"><span data-stu-id="bc48e-342">Application development</span></span>](../app-development/index.md)
- [<span data-ttu-id="bc48e-343">Ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="bc48e-343">Controls</span></span>](../controls/index.md)
- [<span data-ttu-id="bc48e-344">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="bc48e-344">Data binding overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="bc48e-345">Grafika a multimédia</span><span class="sxs-lookup"><span data-stu-id="bc48e-345">Graphics and multimedia</span></span>](../graphics-multimedia/index.md)
- [<span data-ttu-id="bc48e-346">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="bc48e-346">Documents in WPF</span></span>](../advanced/documents-in-wpf.md)

## <a name="see-also"></a><span data-ttu-id="bc48e-347">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bc48e-347">See also</span></span>

- [<span data-ttu-id="bc48e-348">Přehled panelů</span><span class="sxs-lookup"><span data-stu-id="bc48e-348">Panels overview</span></span>](../controls/panels-overview.md)
- [<span data-ttu-id="bc48e-349">Přehled šablonování dat</span><span class="sxs-lookup"><span data-stu-id="bc48e-349">Data templating overview</span></span>](../data/data-templating-overview.md)
- [<span data-ttu-id="bc48e-350">Sestavení aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="bc48e-350">Build a WPF application</span></span>](../app-development/building-a-wpf-application-wpf.md)
- [<span data-ttu-id="bc48e-351">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="bc48e-351">Styles and templates</span></span>](../controls/styles-and-templates.md)
