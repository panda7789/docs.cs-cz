---
title: Vytvoření aplikace WPF v aplikaci Visual Studio
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
ms.openlocfilehash: 9d5b5b8a479efd3918dc23616aa331cc07a901ac
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972138"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a><span data-ttu-id="c564a-102">Návod: Moje první desktopová aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="c564a-102">Walkthrough: My first WPF desktop application</span></span>

<span data-ttu-id="c564a-103">V tomto článku se dozvíte, jak vyvíjet desktopovou aplikaci Windows Presentation Foundation (WPF), která obsahuje prvky, které jsou společné pro většinu aplikací WPF: Jazyk Extensible Application Markup Language (XAML) (XAML) značky, kódu na pozadí, definice aplikací, ovládací prvky, rozložení, datové vazby a styly.</span><span class="sxs-lookup"><span data-stu-id="c564a-103">This article shows you how to develop a Windows Presentation Foundation (WPF) desktop application that includes the elements that are common to most WPF applications: Extensible Application Markup Language (XAML) markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span> <span data-ttu-id="c564a-104">K vývoji aplikace použijete Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c564a-104">To develop the application, you'll use Visual Studio.</span></span> 

<span data-ttu-id="c564a-105">Tento návod obsahuje následující kroky:</span><span class="sxs-lookup"><span data-stu-id="c564a-105">This walkthrough includes the following steps:</span></span>

- <span data-ttu-id="c564a-106">Použijte XAML pro návrh vzhledu uživatelského rozhraní (UI) aplikace.</span><span class="sxs-lookup"><span data-stu-id="c564a-106">Use XAML to design the appearance of the application's user interface (UI).</span></span>

- <span data-ttu-id="c564a-107">Napíšete kód pro sestavení chování aplikace.</span><span class="sxs-lookup"><span data-stu-id="c564a-107">Write code to build the application's behavior.</span></span>

- <span data-ttu-id="c564a-108">Vytvořte definici aplikace pro správu aplikace.</span><span class="sxs-lookup"><span data-stu-id="c564a-108">Create an application definition to manage the application.</span></span>

- <span data-ttu-id="c564a-109">Přidejte ovládací prvky a vytvořte rozložení, abyste mohli vytvořit uživatelské rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="c564a-109">Add controls and create the layout to compose the application UI.</span></span>

- <span data-ttu-id="c564a-110">Vytvářejte styly pro konzistentní vzhled v celém uživatelském rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="c564a-110">Create styles for a consistent appearance throughout the application's UI.</span></span>

- <span data-ttu-id="c564a-111">Navažte uživatelské rozhraní na data a naplňte uživatelské rozhraní z dat a Udržujte data a uživatelské rozhraní synchronizované.</span><span class="sxs-lookup"><span data-stu-id="c564a-111">Bind the UI to data, both to populate the UI from data and to keep the data and UI synchronized.</span></span>

<span data-ttu-id="c564a-112">Na konci tohoto návodu budete mít vytvořenou samostatnou aplikaci pro Windows, která uživatelům umožňuje zobrazit sestavy výdajů pro vybrané lidi.</span><span class="sxs-lookup"><span data-stu-id="c564a-112">By the end of the walkthrough, you'll have built a standalone Windows application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="c564a-113">Aplikace se skládá z několika stránek WPF, které jsou hostovány v okně ve stylu prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="c564a-113">The application is composed of several WPF pages that are hosted in a browser-style window.</span></span>

> [!TIP]
> <span data-ttu-id="c564a-114">Vzorový kód, který se používá k sestavení tohoto návodu, je k dispozici pro C# Visual Basic i v [podrobném ukázkovém kódu aplikace WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span><span class="sxs-lookup"><span data-stu-id="c564a-114">The sample code that is used to build this walkthrough is available for both Visual Basic and C# at [Walkthrough WPF App Sample Code](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span></span>
>
> <span data-ttu-id="c564a-115">C# **Pomocí \< rozevíracího seznamu v pravé horní části tohoto článku můžete přepínat jazyk kódu ukázkového kódu mezi a Visual Basic. />**</span><span class="sxs-lookup"><span data-stu-id="c564a-115">You can toggle the code language of the sample code between C# and Visual Basic by using the **\</>** drop-down on the upper right side of this article.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c564a-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c564a-116">Prerequisites</span></span>

- <span data-ttu-id="c564a-117">Visual Studio 2017 nebo novější (Tento článek používá Visual Studio 2019)</span><span class="sxs-lookup"><span data-stu-id="c564a-117">Visual Studio 2017 or later (this article uses Visual Studio 2019)</span></span>

   <span data-ttu-id="c564a-118">Další informace o instalaci nejnovější verze sady Visual Studio najdete v tématu [instalace sady Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="c564a-118">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="c564a-119">Vytvoření projektu aplikace</span><span class="sxs-lookup"><span data-stu-id="c564a-119">Create the application project</span></span>

<span data-ttu-id="c564a-120">Prvním krokem je vytvoření infrastruktury aplikace, která zahrnuje definici aplikace, dvě stránky a obrázek.</span><span class="sxs-lookup"><span data-stu-id="c564a-120">The first step is to create the application infrastructure, which includes an application definition, two pages, and an image.</span></span>

1. <span data-ttu-id="c564a-121">Vytvoření nového projektu aplikace WPF v Visual Basic nebo vizuálu C# s názvem **`ExpenseIt`** :</span><span class="sxs-lookup"><span data-stu-id="c564a-121">Create a new WPF Application project in Visual Basic or Visual C# named **`ExpenseIt`**:</span></span>

   1. <span data-ttu-id="c564a-122">Otevřete Visual Studio a v nabídce Začínáme vyberte **vytvořit nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="c564a-122">Open Visual Studio and select **Create a new project** under the **Get started** menu.</span></span>

      <span data-ttu-id="c564a-123">Otevře se dialogové okno **vytvořit nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="c564a-123">The **Create a new project** dialog opens.</span></span>

   2. <span data-ttu-id="c564a-124">V rozevíracím seznamu **jazyk** vyberte možnost **C#** nebo **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="c564a-124">In the **Language** dropdown, select either **C#** or **Visual Basic**.</span></span>
      
   3. <span data-ttu-id="c564a-125">Vyberte šablonu **aplikace WPF (.NET Framework)** a pak vyberte **Další**.</span><span class="sxs-lookup"><span data-stu-id="c564a-125">Select the **WPF App (.NET Framework)** template and then select **Next**.</span></span> 
     
      ![Vytvořit nový projekt – dialogové okno](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)
    
      <span data-ttu-id="c564a-127">Otevře se dialogové okno **Konfigurovat nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="c564a-127">The **Configure your new project** dialog opens.</span></span>

   4. <span data-ttu-id="c564a-128">Zadejte název **`ExpenseIt`** projektu a pak vyberte **vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="c564a-128">Enter the project name **`ExpenseIt`** and then select **Create**.</span></span>

      ![Dialogové okno Konfigurovat nový projekt](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      <span data-ttu-id="c564a-130">Visual Studio vytvoří projekt a otevře návrháře pro výchozí okno aplikace s názvem **MainWindow. XAML**.</span><span class="sxs-lookup"><span data-stu-id="c564a-130">Visual Studio creates the project and opens the designer for the default application window named **MainWindow.xaml**.</span></span>

2. <span data-ttu-id="c564a-131">Otevřete *Application. XAML* (Visual Basic) nebo *App. XAML* (C#).</span><span class="sxs-lookup"><span data-stu-id="c564a-131">Open *Application.xaml* (Visual Basic) or *App.xaml* (C#).</span></span>

    <span data-ttu-id="c564a-132">Tento soubor XAML definuje aplikaci WPF a všechny prostředky aplikace.</span><span class="sxs-lookup"><span data-stu-id="c564a-132">This XAML file defines a WPF application and any application resources.</span></span> <span data-ttu-id="c564a-133">Tento soubor můžete také použít k určení uživatelského rozhraní, v tomto případě *MainWindow. XAML*, který se automaticky zobrazí při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="c564a-133">You also use this file to specify the UI, in this case *MainWindow.xaml*, that automatically shows when the application starts.</span></span>

    <span data-ttu-id="c564a-134">Váš kód XAML by měl vypadat jako na následujícím Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="c564a-134">Your XAML should look like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    <span data-ttu-id="c564a-135">A podobně jako v C#následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="c564a-135">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. <span data-ttu-id="c564a-136">Otevřete *MainWindow. XAML*.</span><span class="sxs-lookup"><span data-stu-id="c564a-136">Open *MainWindow.xaml*.</span></span>

    <span data-ttu-id="c564a-137">Tento soubor XAML je hlavním oknem vaší aplikace a zobrazuje obsah vytvořený na stránkách.</span><span class="sxs-lookup"><span data-stu-id="c564a-137">This XAML file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="c564a-138"><xref:System.Windows.Window> Třída definuje vlastnosti okna, například jeho název, velikost nebo ikonu, a zpracovává události, jako je například zavření nebo skrytí.</span><span class="sxs-lookup"><span data-stu-id="c564a-138">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span>

4. <span data-ttu-id="c564a-139"><xref:System.Windows.Window> Změňte element<xref:System.Windows.Navigation.NavigationWindow>na, jak je znázorněno v následujícím kódu XAML:</span><span class="sxs-lookup"><span data-stu-id="c564a-139">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>, as shown in the following XAML:</span></span>

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   <span data-ttu-id="c564a-140">Tato aplikace přejde na jiný obsah v závislosti na vstupu uživatele.</span><span class="sxs-lookup"><span data-stu-id="c564a-140">This app navigates to different content depending on the user input.</span></span> <span data-ttu-id="c564a-141">To je důvod, proč <xref:System.Windows.Window> je hlavní nutné změnit <xref:System.Windows.Navigation.NavigationWindow>na.</span><span class="sxs-lookup"><span data-stu-id="c564a-141">This is why the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="c564a-142"><xref:System.Windows.Navigation.NavigationWindow>dědí všechny vlastnosti <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="c564a-142"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="c564a-143">Prvek v souboru XAML vytvoří instanci <xref:System.Windows.Navigation.NavigationWindow> třídy. <xref:System.Windows.Navigation.NavigationWindow></span><span class="sxs-lookup"><span data-stu-id="c564a-143">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="c564a-144">Další informace najdete v tématu [Přehled navigace](../app-development/navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c564a-144">For more information, see [Navigation overview](../app-development/navigation-overview.md).</span></span>

5. <span data-ttu-id="c564a-145">Odebere prvky z <xref:System.Windows.Navigation.NavigationWindow> značek mezi značkami. <xref:System.Windows.Controls.Grid></span><span class="sxs-lookup"><span data-stu-id="c564a-145">Remove the <xref:System.Windows.Controls.Grid> elements from between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span>

6. <span data-ttu-id="c564a-146">Změňte následující vlastnosti v kódu <xref:System.Windows.Navigation.NavigationWindow> XAML elementu:</span><span class="sxs-lookup"><span data-stu-id="c564a-146">Change the following properties in the XAML code for the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>

    - <span data-ttu-id="c564a-147"><xref:System.Windows.Window.Title%2A> Nastavtevlastnost`ExpenseIt`na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c564a-147">Set the <xref:System.Windows.Window.Title%2A> property to "`ExpenseIt`".</span></span>

    - <span data-ttu-id="c564a-148"><xref:System.Windows.FrameworkElement.Height%2A> Nastavte vlastnost na 350 pixelů.</span><span class="sxs-lookup"><span data-stu-id="c564a-148">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span>

    - <span data-ttu-id="c564a-149"><xref:System.Windows.FrameworkElement.Width%2A> Nastavte vlastnost na 500 pixelů.</span><span class="sxs-lookup"><span data-stu-id="c564a-149">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span>

    <span data-ttu-id="c564a-150">Váš kód XAML by měl vypadat jako u Visual Basic následujících:</span><span class="sxs-lookup"><span data-stu-id="c564a-150">Your XAML should look like the following for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    <span data-ttu-id="c564a-151">A podobně jako následující pro C#:</span><span class="sxs-lookup"><span data-stu-id="c564a-151">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. <span data-ttu-id="c564a-152">Otevřete *MainWindow. XAML. vb* nebo *MainWindow.XAML.cs*.</span><span class="sxs-lookup"><span data-stu-id="c564a-152">Open *MainWindow.xaml.vb* or *MainWindow.xaml.cs*.</span></span>

    <span data-ttu-id="c564a-153">Tento soubor je soubor kódu na pozadí, který obsahuje kód pro zpracování událostí deklarované v souboru *MainWindow. XAML*.</span><span class="sxs-lookup"><span data-stu-id="c564a-153">This file is a code-behind file that contains code to handle the events declared in *MainWindow.xaml*.</span></span> <span data-ttu-id="c564a-154">Tento soubor obsahuje částečnou třídu pro okno definované v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="c564a-154">This file contains a partial class for the window defined in XAML.</span></span>

8. <span data-ttu-id="c564a-155">Pokud používáte C#, změňte `MainWindow` třídu, ze <xref:System.Windows.Navigation.NavigationWindow>které má být odvozena.</span><span class="sxs-lookup"><span data-stu-id="c564a-155">If you're using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="c564a-156">(V Visual Basic k tomu dochází automaticky při změně okna v jazyce XAML.) Váš C# kód by teď měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="c564a-156">(In Visual Basic, this happens automatically when you change the window in XAML.) Your C# code should now look like this:</span></span>

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a><span data-ttu-id="c564a-157">Přidat soubory do aplikace</span><span class="sxs-lookup"><span data-stu-id="c564a-157">Add files to the application</span></span>

<span data-ttu-id="c564a-158">V této části přidáte do aplikace dvě stránky a image.</span><span class="sxs-lookup"><span data-stu-id="c564a-158">In this section, you'll add two pages and an image to the application.</span></span>

1. <span data-ttu-id="c564a-159">Přidejte do projektu novou stránku a pojmenujte ji *`ExpenseItHome.xaml`* :</span><span class="sxs-lookup"><span data-stu-id="c564a-159">Add a new page to the project, and name it *`ExpenseItHome.xaml`*:</span></span>

   1. <span data-ttu-id="c564a-160">V **Průzkumník řešení**klikněte pravým tlačítkem myši **`ExpenseIt`** na uzel projektu a vyberte možnost **Přidat** > **stránku**.</span><span class="sxs-lookup"><span data-stu-id="c564a-160">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="c564a-161">V dialogovém okně **Přidat novou položku** je již vybrána šablona **Stránka (WPF)** .</span><span class="sxs-lookup"><span data-stu-id="c564a-161">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="c564a-162">Zadejte název **`ExpenseItHome`** a pak vyberte **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="c564a-162">Enter the name **`ExpenseItHome`**, and then select **Add**.</span></span>

    <span data-ttu-id="c564a-163">Tato stránka je první stránkou, která se zobrazí při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="c564a-163">This page is the first page that's displayed when the application is launched.</span></span> <span data-ttu-id="c564a-164">Zobrazí se seznam lidí, ze kterých se má vybrat, aby se zobrazila sestava výdajů pro.</span><span class="sxs-lookup"><span data-stu-id="c564a-164">It will show a list of people to select from, to show an expense report for.</span></span>

1. <span data-ttu-id="c564a-165">Otevřete *`ExpenseItHome.xaml`* .</span><span class="sxs-lookup"><span data-stu-id="c564a-165">Open *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="c564a-166"><xref:System.Windows.Controls.Page.Title%2A> Nastavtena`ExpenseIt - Home`.</span><span class="sxs-lookup"><span data-stu-id="c564a-166">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - Home`".</span></span>

1. <span data-ttu-id="c564a-167">Nastavte hodnoty prvku `DesignWidth`ana 300 pixelů. `DesignHeight`</span><span class="sxs-lookup"><span data-stu-id="c564a-167">Set the `DesignHeight` and `DesignWidth` element values to 300 pixels.</span></span>

    <span data-ttu-id="c564a-168">XAML se teď zobrazí jako Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="c564a-168">The XAML now appears as follows for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    <span data-ttu-id="c564a-169">A podobně jako následující pro C#:</span><span class="sxs-lookup"><span data-stu-id="c564a-169">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. <span data-ttu-id="c564a-170">Otevřete *MainWindow. XAML*.</span><span class="sxs-lookup"><span data-stu-id="c564a-170">Open *MainWindow.xaml*.</span></span>

1. <span data-ttu-id="c564a-171">Přidejte k elementu vlastnost a nastavte ji na hodnotu "".`ExpenseItHome.xaml` <xref:System.Windows.Navigation.NavigationWindow.Source%2A> <xref:System.Windows.Navigation.NavigationWindow></span><span class="sxs-lookup"><span data-stu-id="c564a-171">Add a <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property to the <xref:System.Windows.Navigation.NavigationWindow> element and set it to "`ExpenseItHome.xaml`".</span></span>

    <span data-ttu-id="c564a-172">Tato sada *`ExpenseItHome.xaml`* nastaví jako první stránku otevřenou při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="c564a-172">This sets *`ExpenseItHome.xaml`* to be the first page opened when the application starts.</span></span> 

    <span data-ttu-id="c564a-173">Příklad XAML v Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="c564a-173">Example XAML in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    <span data-ttu-id="c564a-174">A v jazyce C#:</span><span class="sxs-lookup"><span data-stu-id="c564a-174">And in C#:</span></span>

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > <span data-ttu-id="c564a-175">Vlastnost **source** můžete nastavit také v kategorii **různé** v okně **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="c564a-175">You can also set the **Source** property in the **Miscellaneous** category of the **Properties** window.</span></span>
   >
   > ![Vlastnost source v okno Vlastnosti](./media/properties-source.png)

1. <span data-ttu-id="c564a-177">Do projektu přidejte další novou stránku WPF a pojmenujte ji *ExpenseReportPage. XAML*::</span><span class="sxs-lookup"><span data-stu-id="c564a-177">Add another new WPF page to the project, and name it *ExpenseReportPage.xaml*::</span></span>

   1. <span data-ttu-id="c564a-178">V **Průzkumník řešení**klikněte pravým tlačítkem myši **`ExpenseIt`** na uzel projektu a vyberte možnost **Přidat** > **stránku**.</span><span class="sxs-lookup"><span data-stu-id="c564a-178">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="c564a-179">V dialogovém okně **Přidat novou položku** vyberte šablonu **Stránka (WPF)** .</span><span class="sxs-lookup"><span data-stu-id="c564a-179">In the **Add New Item** dialog, select the **Page (WPF)** template.</span></span> <span data-ttu-id="c564a-180">Zadejte název **ExpenseReportPage**a pak vyberte **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="c564a-180">Enter the name **ExpenseReportPage**, and then select **Add**.</span></span>

    <span data-ttu-id="c564a-181">Na této stránce se zobrazí sestava výdajů pro osobu, která je vybrána na **`ExpenseItHome`** stránce.</span><span class="sxs-lookup"><span data-stu-id="c564a-181">This page will show the expense report for the person that is selected on the **`ExpenseItHome`** page.</span></span>

1. <span data-ttu-id="c564a-182">Otevřete *ExpenseReportPage. XAML*.</span><span class="sxs-lookup"><span data-stu-id="c564a-182">Open *ExpenseReportPage.xaml*.</span></span>

1. <span data-ttu-id="c564a-183"><xref:System.Windows.Controls.Page.Title%2A> Nastavtena`ExpenseIt - View Expense`.</span><span class="sxs-lookup"><span data-stu-id="c564a-183">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - View Expense`".</span></span>

1. <span data-ttu-id="c564a-184">Nastavte hodnoty prvku `DesignWidth`ana 300 pixelů. `DesignHeight`</span><span class="sxs-lookup"><span data-stu-id="c564a-184">Set the `DesignHeight` and `DesignWidth` element values to 300 pixels.</span></span>

    <span data-ttu-id="c564a-185">*ExpenseReportPage. XAML* teď vypadá jako na následujícím Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="c564a-185">*ExpenseReportPage.xaml* now looks like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    <span data-ttu-id="c564a-186">A podobně jako v C#následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="c564a-186">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. <span data-ttu-id="c564a-187">Otevřete *ExpenseItHome. XAML. vb* a *ExpenseReportPage. XAML. vb*nebo *ExpenseItHome.XAML.cs* a *ExpenseReportPage.XAML.cs*.</span><span class="sxs-lookup"><span data-stu-id="c564a-187">Open *ExpenseItHome.xaml.vb* and *ExpenseReportPage.xaml.vb*, or *ExpenseItHome.xaml.cs* and *ExpenseReportPage.xaml.cs*.</span></span>

    <span data-ttu-id="c564a-188">Při vytváření nového stránkovacího souboru aplikace Visual Studio automaticky vytvoří svůj soubor *kódu na pozadí* .</span><span class="sxs-lookup"><span data-stu-id="c564a-188">When you create a new Page file, Visual Studio automatically creates its *code-behind* file.</span></span> <span data-ttu-id="c564a-189">Tyto soubory s kódem na pozadí zpracovávají logiku pro reagování na vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="c564a-189">These code-behind files handle the logic for responding to user input.</span></span>

    <span data-ttu-id="c564a-190">Váš kód by měl vypadat **`ExpenseItHome`** takto:</span><span class="sxs-lookup"><span data-stu-id="c564a-190">Your code should look like the following for **`ExpenseItHome`**:</span></span>

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    <span data-ttu-id="c564a-191">A podobně jako v případě **ExpenseReportPage**postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="c564a-191">And like the following for **ExpenseReportPage**:</span></span>

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. <span data-ttu-id="c564a-192">Přidejte do projektu obrázek s názvem *vodotisk. png* .</span><span class="sxs-lookup"><span data-stu-id="c564a-192">Add an image named *watermark.png* to the project.</span></span> <span data-ttu-id="c564a-193">Můžete vytvořit vlastní image, zkopírovat soubor z ukázkového kódu nebo ho získat [sem](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png).</span><span class="sxs-lookup"><span data-stu-id="c564a-193">You can create your own image, copy the file from the sample code, or get it [here](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png).</span></span>

    1. <span data-ttu-id="c564a-194">Klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **Přidat** > **existující položku**nebo stiskněte klávesu **SHIFT**+**ALT**+**A**.</span><span class="sxs-lookup"><span data-stu-id="c564a-194">Right-click on the project node and select **Add** > **Existing Item**, or press **Shift**+**Alt**+**A**.</span></span>

    2. <span data-ttu-id="c564a-195">V dialogovém okně **Přidat existující položku** nastavte filtr File buď na **všechny soubory** , nebo na **soubory obrázků**, vyhledejte soubor obrázku, který chcete použít, a pak vyberte **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="c564a-195">In the **Add Existing Item** dialog, set the file filter to either **All Files** or **Image Files**, browse to the image file you want to use, and then select **Add**.</span></span>

## <a name="build-and-run-the-application"></a><span data-ttu-id="c564a-196">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="c564a-196">Build and run the application</span></span>

1. <span data-ttu-id="c564a-197">Chcete-li sestavit a spustit aplikaci, stiskněte klávesu **F5** nebo vyberte možnost **Spustit ladění** z nabídky **ladění** .</span><span class="sxs-lookup"><span data-stu-id="c564a-197">To build and run the application, press **F5** or select **Start Debugging** from the **Debug** menu.</span></span>

    <span data-ttu-id="c564a-198">Následující ilustrace znázorňuje aplikaci s <xref:System.Windows.Navigation.NavigationWindow> tlačítky:</span><span class="sxs-lookup"><span data-stu-id="c564a-198">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons:</span></span>

    ![Aplikace po sestavení a spuštění.](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. <span data-ttu-id="c564a-200">Zavřete aplikaci a vraťte se do sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c564a-200">Close the application to return to Visual Studio.</span></span>

## <a name="create-the-layout"></a><span data-ttu-id="c564a-201">Vytvoření rozložení</span><span class="sxs-lookup"><span data-stu-id="c564a-201">Create the layout</span></span>

<span data-ttu-id="c564a-202">Rozložení poskytuje uspořádaný způsob, jak umístit prvky uživatelského rozhraní a také spravuje velikost a polohu těchto prvků při změně velikosti uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c564a-202">Layout provides an ordered way to place UI elements, and also manages the size and position of those elements when a UI is resized.</span></span> <span data-ttu-id="c564a-203">Rozložení obvykle vytvoříte pomocí jednoho z následujících ovládacích prvků rozložení:</span><span class="sxs-lookup"><span data-stu-id="c564a-203">You typically create a layout with one of the following layout controls:</span></span>

- <span data-ttu-id="c564a-204"><xref:System.Windows.Controls.Canvas>-Definuje oblast, ve které můžete explicitně umístit podřízené prvky pomocí souřadnic, které jsou relativní k oblasti plátna.</span><span class="sxs-lookup"><span data-stu-id="c564a-204"><xref:System.Windows.Controls.Canvas> - Defines an area within which you can explicitly position child elements by using coordinates that are relative to the Canvas area.</span></span>
- <span data-ttu-id="c564a-205"><xref:System.Windows.Controls.DockPanel>– Definuje oblast, kde můžete uspořádat podřízené prvky buď vodorovně, nebo svisle, relativně k sobě navzájem.</span><span class="sxs-lookup"><span data-stu-id="c564a-205"><xref:System.Windows.Controls.DockPanel> - Defines an area where you can arrange child elements either horizontally or vertically, relative to each other.</span></span>
- <span data-ttu-id="c564a-206"><xref:System.Windows.Controls.Grid>– Definuje flexibilní oblast mřížky, která se skládá ze sloupců a řádků.</span><span class="sxs-lookup"><span data-stu-id="c564a-206"><xref:System.Windows.Controls.Grid> - Defines a flexible grid area that consists of columns and rows.</span></span>
- <span data-ttu-id="c564a-207"><xref:System.Windows.Controls.StackPanel>– Uspořádá podřízené prvky na jeden řádek, který může být orientovaný vodorovně nebo svisle.</span><span class="sxs-lookup"><span data-stu-id="c564a-207"><xref:System.Windows.Controls.StackPanel> - Arranges child elements into a single line that can be oriented horizontally or vertically.</span></span>
- <span data-ttu-id="c564a-208"><xref:System.Windows.Controls.VirtualizingStackPanel>– Uspořádá a virtualizuje obsah na jednom řádku, který je orientovaný buď vodorovně, nebo svisle.</span><span class="sxs-lookup"><span data-stu-id="c564a-208"><xref:System.Windows.Controls.VirtualizingStackPanel> - Arranges and virtualizes content on a single line that is oriented either horizontally or vertically.</span></span>
- <span data-ttu-id="c564a-209"><xref:System.Windows.Controls.WrapPanel>-Umístí podřízené elementy v sekvenčním umístění zleva doprava a oddělí obsah na další řádek na okraji obsahujícího pole.</span><span class="sxs-lookup"><span data-stu-id="c564a-209"><xref:System.Windows.Controls.WrapPanel> - Positions child elements in sequential position from left to right, breaking content to the next line at the edge of the containing box.</span></span> <span data-ttu-id="c564a-210">Následné řazení probíhá postupně shora dolů nebo zprava doleva v závislosti na hodnotě vlastnosti orientace.</span><span class="sxs-lookup"><span data-stu-id="c564a-210">Subsequent ordering happens sequentially from top to bottom or from right to left, depending on the value of the Orientation property.</span></span>

<span data-ttu-id="c564a-211">Každé z těchto ovládacích prvků rozložení podporuje konkrétní typ rozložení pro jeho podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="c564a-211">Each of these layout controls supports a particular type of layout for its child elements.</span></span> <span data-ttu-id="c564a-212">`ExpenseIt`lze změnit velikost stránek a každá stránka obsahuje prvky, které jsou uspořádány vodorovně a svisle vedle ostatních prvků.</span><span class="sxs-lookup"><span data-stu-id="c564a-212">`ExpenseIt` pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="c564a-213">V tomto příkladu <xref:System.Windows.Controls.Grid> se používá jako element rozložení pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c564a-213">In this example, the <xref:System.Windows.Controls.Grid> is used as  layout element for the application.</span></span>

> [!TIP]
> <span data-ttu-id="c564a-214">Další informace o <xref:System.Windows.Controls.Panel> prvcích najdete v tématu [Přehled panelů](../controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c564a-214">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels overview](../controls/panels-overview.md).</span></span> <span data-ttu-id="c564a-215">Další informace o rozložení najdete v tématu [layout](../advanced/layout.md).</span><span class="sxs-lookup"><span data-stu-id="c564a-215">For more information about layout, see [Layout](../advanced/layout.md).</span></span>

<span data-ttu-id="c564a-216">V této části vytvoříte tabulku s jedním sloupcem se třemi řádky a okrajem 10 pixelů přidáním definice sloupců a řádků do <xref:System.Windows.Controls.Grid> v. *`ExpenseItHome.xaml`*</span><span class="sxs-lookup"><span data-stu-id="c564a-216">In this section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="c564a-217">V *`ExpenseItHome.xaml`* saděnastavte<xref:System.Windows.Controls.Grid>vlastnostelementu na "10, 0, 10, 10", což odpovídá levému, hornímu a dolnímu okraji: <xref:System.Windows.FrameworkElement.Margin%2A></span><span class="sxs-lookup"><span data-stu-id="c564a-217">In *`ExpenseItHome.xaml`*, set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10", which corresponds to left, top, right and bottom margins:</span></span>

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > <span data-ttu-id="c564a-218">Hodnoty okrajů můžete nastavit také v okně **vlastnosti** v kategorii **rozložení** :</span><span class="sxs-lookup"><span data-stu-id="c564a-218">You can also set the **Margin** values in the **Properties** window, under the **Layout** category:</span></span>
   >
   > ![Hodnoty okrajů v okno Vlastnosti](./media/properties-margin.png)

2. <span data-ttu-id="c564a-220">Přidejte následující XAML mezi <xref:System.Windows.Controls.Grid> značkami k vytvoření definice řádků a sloupců:</span><span class="sxs-lookup"><span data-stu-id="c564a-220">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions:</span></span>

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <span data-ttu-id="c564a-221">U dvou řádků je nastaven na <xref:System.Windows.GridLength.Auto%2A>hodnotu, což znamená, že řádky mají velikost na základě obsahu v řádcích. <xref:System.Windows.Controls.RowDefinition.Height%2A></span><span class="sxs-lookup"><span data-stu-id="c564a-221">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A>, which means that the rows are sized based on the content in the rows.</span></span> <span data-ttu-id="c564a-222">Výchozí hodnota <xref:System.Windows.Controls.RowDefinition.Height%2A> je <xref:System.Windows.GridUnitType.Star> velikost, což znamená, že výška řádku je Vážený podíl dostupného místa.</span><span class="sxs-lookup"><span data-stu-id="c564a-222">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row height is a weighted proportion of the available space.</span></span> <span data-ttu-id="c564a-223">Pokud například dva řádky mají <xref:System.Windows.Controls.RowDefinition.Height%2A> "\*", mají každý z nich výšku, která je polovinu dostupného místa.</span><span class="sxs-lookup"><span data-stu-id="c564a-223">For example if two rows each have a <xref:System.Windows.Controls.RowDefinition.Height%2A> of "\*", they each have a height that is half of the available space.</span></span>

    <span data-ttu-id="c564a-224">Teď <xref:System.Windows.Controls.Grid> by měl obsahovat následující kód XAML:</span><span class="sxs-lookup"><span data-stu-id="c564a-224">Your <xref:System.Windows.Controls.Grid> should now contain the following XAML:</span></span>

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a><span data-ttu-id="c564a-225">Přidat ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="c564a-225">Add controls</span></span>

<span data-ttu-id="c564a-226">V této části aktualizujete uživatelské rozhraní domovské stránky tak, aby zobrazovalo seznam lidí, kde vyberete jednu osobu k zobrazení své sestavy výdajů.</span><span class="sxs-lookup"><span data-stu-id="c564a-226">In this section, you'll update the home page UI to show a list of people, where you select one person to display their expense report.</span></span> <span data-ttu-id="c564a-227">Ovládací prvky jsou objekty uživatelského rozhraní, které umožňují uživatelům pracovat s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="c564a-227">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="c564a-228">Další informace najdete v tématu [ovládací prvky](../controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="c564a-228">For more information, see [Controls](../controls/index.md).</span></span>

<span data-ttu-id="c564a-229">Chcete-li vytvořit toto uživatelské rozhraní, přidejte následující prvky do *`ExpenseItHome.xaml`* :</span><span class="sxs-lookup"><span data-stu-id="c564a-229">To create this UI, you'll add the following elements to *`ExpenseItHome.xaml`*:</span></span>

- <span data-ttu-id="c564a-230">A <xref:System.Windows.Controls.ListBox> (pro seznam lidí).</span><span class="sxs-lookup"><span data-stu-id="c564a-230">A <xref:System.Windows.Controls.ListBox> (for the list of people).</span></span>
- <span data-ttu-id="c564a-231">A <xref:System.Windows.Controls.Label> (pro záhlaví seznamu).</span><span class="sxs-lookup"><span data-stu-id="c564a-231">A <xref:System.Windows.Controls.Label> (for the list header).</span></span>
- <span data-ttu-id="c564a-232">A <xref:System.Windows.Controls.Button> (Kliknutím zobrazíte sestavu výdajů pro osobu, která je vybrána v seznamu).</span><span class="sxs-lookup"><span data-stu-id="c564a-232">A <xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span>

<span data-ttu-id="c564a-233">Každý ovládací prvek je umístěn v řádku <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> nastavení připojené vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c564a-233">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="c564a-234">Další informace o připojených vlastnostech najdete v tématu [Přehled připojených vlastností](../advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c564a-234">For more information about attached properties, see [Attached Properties Overview](../advanced/attached-properties-overview.md).</span></span>

1. <span data-ttu-id="c564a-235">Do *`ExpenseItHome.xaml`* přidejte následující XAML <xref:System.Windows.Controls.Grid> mezi značkami:</span><span class="sxs-lookup"><span data-stu-id="c564a-235">In *`ExpenseItHome.xaml`*, add the following XAML somewhere between the <xref:System.Windows.Controls.Grid> tags:</span></span>

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > <span data-ttu-id="c564a-236">Ovládací prvky lze také vytvořit přetažením z okna **panelu nástrojů** do okna návrh a následně nastavením jejich vlastností v okně **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="c564a-236">You can also create the controls by dragging them from the **Toolbox** window onto the design window, and then setting their properties in the **Properties** window.</span></span>

2. <span data-ttu-id="c564a-237">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c564a-237">Build and run the application.</span></span>

    <span data-ttu-id="c564a-238">Následující ilustrace znázorňuje ovládací prvky, které jste vytvořili:</span><span class="sxs-lookup"><span data-stu-id="c564a-238">The following illustration shows the controls you created:</span></span>

![Ukázka ExpenseIt obrazovky zobrazující seznam názvů](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a><span data-ttu-id="c564a-240">Přidání obrázku a názvu</span><span class="sxs-lookup"><span data-stu-id="c564a-240">Add an image and a title</span></span>

<span data-ttu-id="c564a-241">V této části aktualizujete uživatelské rozhraní domovské stránky s obrázkem a nadpisem stránky.</span><span class="sxs-lookup"><span data-stu-id="c564a-241">In this section, you'll update the home page UI with an image and a page title.</span></span>

1. <span data-ttu-id="c564a-242">Do *`ExpenseItHome.xaml`* přidejte další sloupec <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> s pevným <xref:System.Windows.Controls.ColumnDefinition.Width%2A> počtem 230 pixelů:</span><span class="sxs-lookup"><span data-stu-id="c564a-242">In *`ExpenseItHome.xaml`*, add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels:</span></span>

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=52-55)]

2. <span data-ttu-id="c564a-243">Přidejte další řádek do, <xref:System.Windows.Controls.Grid.RowDefinitions%2A>který bude celkem čtyři řádky:</span><span class="sxs-lookup"><span data-stu-id="c564a-243">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, for a total of four rows:</span></span>

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=57-62)]

3. <span data-ttu-id="c564a-244">Přesuňte ovládací prvky na druhý sloupec nastavením <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> vlastnosti na hodnotu 1 v každém ze tří ovládacích prvků (Border, ListBox a Button).</span><span class="sxs-lookup"><span data-stu-id="c564a-244">Move the controls to the second column by setting the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property to 1 in each of the three controls (Border, ListBox, and Button).</span></span>

4. <span data-ttu-id="c564a-245">Každé tři ovládací prvky (ohraničení, seznam a tlačítko <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> ) a pro prvek ohraničení přesuňte každý prvek dolů o jednu řadu.</span><span class="sxs-lookup"><span data-stu-id="c564a-245">Move each control down a row by incrementing its <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> value by 1 for each of the three controls (Border, ListBox, and Button) and for the Border element.</span></span>

   <span data-ttu-id="c564a-246">XAML pro tři ovládací prvky nyní vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="c564a-246">The XAML for the three controls now looks like the following:</span></span>

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. <span data-ttu-id="c564a-247">Nastavte vlastnost na soubor bitové kopie s *vodotiskem. png* přidáním následujícího `<Grid>` XAML kamkoli mezi značky a `</Grid>`: <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="c564a-247">Set the <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> property to the *watermark.png* image file, by adding the following XAML anywhere between the `<Grid>` and `</Grid>` tags:</span></span>

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. <span data-ttu-id="c564a-248">Před element přidejte a <xref:System.Windows.Controls.Label> pomocí obsahu zobrazit sestavu výdajů. <xref:System.Windows.Controls.Border></span><span class="sxs-lookup"><span data-stu-id="c564a-248">Before the <xref:System.Windows.Controls.Border> element, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report".</span></span> <span data-ttu-id="c564a-249">Tento popisek je název stránky.</span><span class="sxs-lookup"><span data-stu-id="c564a-249">This label is the title of the page.</span></span>

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. <span data-ttu-id="c564a-250">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c564a-250">Build and run the application.</span></span>

<span data-ttu-id="c564a-251">Následující ilustrace znázorňuje výsledky toho, co jste právě přidali:</span><span class="sxs-lookup"><span data-stu-id="c564a-251">The following illustration shows the results of what you just added:</span></span>

![Ukázka snímku obrazovky ExpenseIt zobrazující nové pozadí obrázku a nadpis stránky](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a><span data-ttu-id="c564a-253">Přidat kód pro zpracování událostí</span><span class="sxs-lookup"><span data-stu-id="c564a-253">Add code to handle events</span></span>

1. <span data-ttu-id="c564a-254">V *`ExpenseItHome.xaml`* přidejtek<xref:System.Windows.Controls.Button> elementu obslužnou rutinu události.<xref:System.Windows.Controls.Primitives.ButtonBase.Click></span><span class="sxs-lookup"><span data-stu-id="c564a-254">In *`ExpenseItHome.xaml`*, add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="c564a-255">Další informace najdete v tématu [jak: Vytvořte jednoduchou obslužnou rutinu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100))události.</span><span class="sxs-lookup"><span data-stu-id="c564a-255">For more information, see [How to: Create a simple event handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. <span data-ttu-id="c564a-256">Otevřete *`ExpenseItHome.xaml.vb`* nebo *`ExpenseItHome.xaml.cs`* .</span><span class="sxs-lookup"><span data-stu-id="c564a-256">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

3. <span data-ttu-id="c564a-257">Přidejte následující kód do `ExpenseItHome` třídy pro přidání obslužné rutiny události kliknutí na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c564a-257">Add the following code to the `ExpenseItHome` class to add a button click event handler.</span></span> <span data-ttu-id="c564a-258">Obslužná rutina události otevře stránku **ExpenseReportPage** .</span><span class="sxs-lookup"><span data-stu-id="c564a-258">The event handler opens the **ExpenseReportPage** page.</span></span>

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a><span data-ttu-id="c564a-259">Vytvoření uživatelského rozhraní pro ExpenseReportPage</span><span class="sxs-lookup"><span data-stu-id="c564a-259">Create the UI for ExpenseReportPage</span></span>

<span data-ttu-id="c564a-260">*ExpenseReportPage. XAML* zobrazí sestavu výdajů pro osobu, která je vybrána na **`ExpenseItHome`** stránce.</span><span class="sxs-lookup"><span data-stu-id="c564a-260">*ExpenseReportPage.xaml* displays the expense report for the person that's selected on the **`ExpenseItHome`** page.</span></span> <span data-ttu-id="c564a-261">V této části vytvoříte uživatelské rozhraní pro **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="c564a-261">In this section, you'll create the UI for **ExpenseReportPage**.</span></span> <span data-ttu-id="c564a-262">Do různých prvků uživatelského rozhraní také přidáte barvy pozadí a výplně.</span><span class="sxs-lookup"><span data-stu-id="c564a-262">You'll also add background and fill colors to the various UI elements.</span></span>

1. <span data-ttu-id="c564a-263">Otevřete *ExpenseReportPage. XAML*.</span><span class="sxs-lookup"><span data-stu-id="c564a-263">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="c564a-264">Do <xref:System.Windows.Controls.Grid> značek přidejte následující kód XAML:</span><span class="sxs-lookup"><span data-stu-id="c564a-264">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags:</span></span>

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    <span data-ttu-id="c564a-265">Toto uživatelské rozhraní je podobné *`ExpenseItHome.xaml`* , s výjimkou toho, že se data <xref:System.Windows.Controls.DataGrid>sestavy zobrazují v.</span><span class="sxs-lookup"><span data-stu-id="c564a-265">This UI is similar to *`ExpenseItHome.xaml`*, except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span>

3. <span data-ttu-id="c564a-266">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c564a-266">Build and run the application.</span></span>

4. <span data-ttu-id="c564a-267">Vyberte tlačítko **Zobrazit** .</span><span class="sxs-lookup"><span data-stu-id="c564a-267">Select the **View** button.</span></span>

    <span data-ttu-id="c564a-268">Zobrazí se stránka Sestava výdajů.</span><span class="sxs-lookup"><span data-stu-id="c564a-268">The expense report page appears.</span></span> <span data-ttu-id="c564a-269">Všimněte si také, že je povoleno tlačítko zpět navigace.</span><span class="sxs-lookup"><span data-stu-id="c564a-269">Also notice that the back navigation button is enabled.</span></span>

<span data-ttu-id="c564a-270">Následující ilustrace znázorňuje prvky uživatelského rozhraní přidané do souboru *ExpenseReportPage. XAML*.</span><span class="sxs-lookup"><span data-stu-id="c564a-270">The following illustration shows the UI elements added to *ExpenseReportPage.xaml*.</span></span>

![Ukázka snímku obrazovky ExpenseIt zobrazující uživatelské rozhraní, které jste právě vytvořili pro ExpenseReportPage.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a><span data-ttu-id="c564a-272">Ovládací prvky stylu</span><span class="sxs-lookup"><span data-stu-id="c564a-272">Style controls</span></span>

<span data-ttu-id="c564a-273">Vzhled různých prvků je často stejný pro všechny prvky stejného typu v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c564a-273">The appearance of various elements is often the same for all elements of the same type in a UI.</span></span> <span data-ttu-id="c564a-274">Uživatelské rozhraní používá [styly](../controls/styling-and-templating.md) , aby bylo možné vzhledy opakovaně použít napříč více prvky.</span><span class="sxs-lookup"><span data-stu-id="c564a-274">UI uses [styles](../controls/styling-and-templating.md) to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="c564a-275">Opětovné použitelnost stylů pomáhá zjednodušit vytváření a správu XAML.</span><span class="sxs-lookup"><span data-stu-id="c564a-275">The reusability of styles helps to simplify XAML creation and management.</span></span> <span data-ttu-id="c564a-276">Tato část nahrazuje atributy jednotlivých prvků, které byly definovány v předchozích krocích se styly.</span><span class="sxs-lookup"><span data-stu-id="c564a-276">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span>

1. <span data-ttu-id="c564a-277">Otevřete *Application. XAML* nebo *App. XAML*.</span><span class="sxs-lookup"><span data-stu-id="c564a-277">Open *Application.xaml* or *App.xaml*.</span></span>

2. <span data-ttu-id="c564a-278">Do <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> značek přidejte následující kód XAML:</span><span class="sxs-lookup"><span data-stu-id="c564a-278">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    <span data-ttu-id="c564a-279">Tento kód XAML přidá následující styly:</span><span class="sxs-lookup"><span data-stu-id="c564a-279">This XAML adds the following styles:</span></span>

    - <span data-ttu-id="c564a-280">`headerTextStyle`: Pro naformátování nadpisu <xref:System.Windows.Controls.Label>stránky.</span><span class="sxs-lookup"><span data-stu-id="c564a-280">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="c564a-281">`labelStyle`: Pro formátování <xref:System.Windows.Controls.Label> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="c564a-281">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span>

    - <span data-ttu-id="c564a-282">`columnHeaderStyle`: K naformátování <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span><span class="sxs-lookup"><span data-stu-id="c564a-282">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span>

    - <span data-ttu-id="c564a-283">`listHeaderStyle`: Chcete-li naformátovat ovládací prvky záhlaví <xref:System.Windows.Controls.Border> seznamu.</span><span class="sxs-lookup"><span data-stu-id="c564a-283">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span>

    - <span data-ttu-id="c564a-284">`listHeaderTextStyle`: K naformátování záhlaví <xref:System.Windows.Controls.Label>seznamu.</span><span class="sxs-lookup"><span data-stu-id="c564a-284">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="c564a-285">`buttonStyle`: Pro <xref:System.Windows.Controls.Button> naformátování `ExpenseItHome.xaml`na.</span><span class="sxs-lookup"><span data-stu-id="c564a-285">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on `ExpenseItHome.xaml`.</span></span>

    <span data-ttu-id="c564a-286">Všimněte si, že styly jsou prostředky a podřízené <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> prvky elementu Property.</span><span class="sxs-lookup"><span data-stu-id="c564a-286">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="c564a-287">V tomto umístění se styly aplikují na všechny prvky v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c564a-287">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="c564a-288">Příklad používání prostředků v aplikaci .NET najdete v tématu [použití prostředků aplikace](../advanced/how-to-use-application-resources.md).</span><span class="sxs-lookup"><span data-stu-id="c564a-288">For an example of using resources in a .NET app, see [Use Application Resources](../advanced/how-to-use-application-resources.md).</span></span>

3. <span data-ttu-id="c564a-289">V *`ExpenseItHome.xaml`* , nahraďte vše <xref:System.Windows.Controls.Grid> mezi prvky následujícím XAML:</span><span class="sxs-lookup"><span data-stu-id="c564a-289">In *`ExpenseItHome.xaml`*, replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    <span data-ttu-id="c564a-290">Vlastnosti <xref:System.Windows.VerticalAlignment> , jako jsou a <xref:System.Windows.Media.FontFamily> definující vzhled jednotlivých ovládacích prvků, jsou odebrány a nahrazeny použitím stylů.</span><span class="sxs-lookup"><span data-stu-id="c564a-290">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="c564a-291">Například `headerTextStyle` se použije na <xref:System.Windows.Controls.Label>sestavu zobrazit výdaje.</span><span class="sxs-lookup"><span data-stu-id="c564a-291">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span>

4. <span data-ttu-id="c564a-292">Otevřete *ExpenseReportPage. XAML*.</span><span class="sxs-lookup"><span data-stu-id="c564a-292">Open *ExpenseReportPage.xaml*.</span></span>

5. <span data-ttu-id="c564a-293">Nahraďte vše mezi <xref:System.Windows.Controls.Grid> prvky následujícím XAML:</span><span class="sxs-lookup"><span data-stu-id="c564a-293">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    <span data-ttu-id="c564a-294">Tento XAML přidá styly do <xref:System.Windows.Controls.Label> prvků a. <xref:System.Windows.Controls.Border></span><span class="sxs-lookup"><span data-stu-id="c564a-294">This XAML adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span>

6. <span data-ttu-id="c564a-295">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c564a-295">Build and run the application.</span></span> <span data-ttu-id="c564a-296">Vzhled okna je stejný jako dříve.</span><span class="sxs-lookup"><span data-stu-id="c564a-296">The window appearance is the same as previously.</span></span>

    ![ExpenseIt ukázkový snímek obrazovky se stejným vzhledem jako v poslední části.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. <span data-ttu-id="c564a-298">Zavřete aplikaci a vraťte se do sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c564a-298">Close the application to return to Visual Studio.</span></span>

## <a name="bind-data-to-a-control"></a><span data-ttu-id="c564a-299">Vázání dat k ovládacímu prvku</span><span class="sxs-lookup"><span data-stu-id="c564a-299">Bind data to a control</span></span>

<span data-ttu-id="c564a-300">V této části vytvoříte data XML, která jsou svázána s různými ovládacími prvky.</span><span class="sxs-lookup"><span data-stu-id="c564a-300">In this section, you'll create the XML data that is bound to various controls.</span></span>

1. <span data-ttu-id="c564a-301">V *`ExpenseItHome.xaml`* rámci, po otevření <xref:System.Windows.Controls.Grid> elementu přidejte <xref:System.Windows.Data.XmlDataProvider> následující XAML pro vytvoření obsahující data pro každou osobu:</span><span class="sxs-lookup"><span data-stu-id="c564a-301">In *`ExpenseItHome.xaml`*, after the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person:</span></span>

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    <span data-ttu-id="c564a-302">Data se vytvoří jako <xref:System.Windows.Controls.Grid> prostředek.</span><span class="sxs-lookup"><span data-stu-id="c564a-302">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="c564a-303">Obvykle by se tato data načítala jako soubor, ale pro zjednodušení se data přidávají jako vložená.</span><span class="sxs-lookup"><span data-stu-id="c564a-303">Normally this data would be loaded as a file, but for simplicity the data is added inline.</span></span>

2. <span data-ttu-id="c564a-304">V rámci `<xref:System.Windows.DataTemplate>` <xref:System.Windows.Controls.ListBox>elementu přidejte následující prvek, který definuje, jak zobrazit data `<XmlDataProvider>` v, za prvkem: `<Grid.Resources>`</span><span class="sxs-lookup"><span data-stu-id="c564a-304">Within the `<Grid.Resources>` element, add the following `<xref:System.Windows.DataTemplate>` element, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>, after the `<XmlDataProvider>` element:</span></span>

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    <span data-ttu-id="c564a-305">Další informace o datových šablonách najdete v tématu [Přehled šablonování dat](../data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c564a-305">For more information about data templates, see [Data templating overview](../data/data-templating-overview.md).</span></span>

3. <span data-ttu-id="c564a-306">Nahraďte existující <xref:System.Windows.Controls.ListBox> kód následujícím XAML:</span><span class="sxs-lookup"><span data-stu-id="c564a-306">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    <span data-ttu-id="c564a-307">Tento kód XAML váže <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost <xref:System.Windows.Controls.ListBox> na zdroj dat a použije šablonu dat jako <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span><span class="sxs-lookup"><span data-stu-id="c564a-307">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span>

## <a name="connect-data-to-controls"></a><span data-ttu-id="c564a-308">Připojení dat k ovládacím prvkům</span><span class="sxs-lookup"><span data-stu-id="c564a-308">Connect data to controls</span></span>

<span data-ttu-id="c564a-309">Dále přidáte kód, který načte název, který je vybrán na **`ExpenseItHome`** stránce, a předáte ho konstruktoru třídy **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="c564a-309">Next, you'll add code to retrieve the name that's selected on the **`ExpenseItHome`** page and pass it to the constructor of **ExpenseReportPage**.</span></span> <span data-ttu-id="c564a-310">**ExpenseReportPage** nastaví svůj kontext dat s předanou položkou, která určuje ovládací prvky definované v rámci vazby *ExpenseReportPage. XAML* na.</span><span class="sxs-lookup"><span data-stu-id="c564a-310">**ExpenseReportPage** sets its data context with the passed item, which is what the controls defined in *ExpenseReportPage.xaml* bind to.</span></span>

1. <span data-ttu-id="c564a-311">Otevřete *ExpenseReportPage. XAML. vb* nebo *ExpenseReportPage.XAML.cs*.</span><span class="sxs-lookup"><span data-stu-id="c564a-311">Open *ExpenseReportPage.xaml.vb* or *ExpenseReportPage.xaml.cs*.</span></span>

2. <span data-ttu-id="c564a-312">Přidejte konstruktor, který převezme objekt, abyste mohli předat data sestavy výdajů vybrané osobě.</span><span class="sxs-lookup"><span data-stu-id="c564a-312">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. <span data-ttu-id="c564a-313">Otevřete *`ExpenseItHome.xaml.vb`* nebo *`ExpenseItHome.xaml.cs`* .</span><span class="sxs-lookup"><span data-stu-id="c564a-313">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

4. <span data-ttu-id="c564a-314">Změňte obslužnou rutinu události tak, aby volala nový konstruktor, který předává data sestavy výdajů vybrané osobě. <xref:System.Windows.Controls.Primitives.ButtonBase.Click></span><span class="sxs-lookup"><span data-stu-id="c564a-314">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a><span data-ttu-id="c564a-315">Data stylu pomocí datových šablon</span><span class="sxs-lookup"><span data-stu-id="c564a-315">Style data with data templates</span></span>

<span data-ttu-id="c564a-316">V této části aktualizujete uživatelské rozhraní pro každou položku v seznamech vázaných na data pomocí datových šablon.</span><span class="sxs-lookup"><span data-stu-id="c564a-316">In this section, you'll update the UI for each item in the data-bound lists by using data templates.</span></span>

1. <span data-ttu-id="c564a-317">Otevřete *ExpenseReportPage. XAML*.</span><span class="sxs-lookup"><span data-stu-id="c564a-317">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="c564a-318">Navažte obsah prvků "název" a "oddělení" <xref:System.Windows.Controls.Label> na odpovídající vlastnost zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="c564a-318">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="c564a-319">Další informace o datové vazbě najdete v tématu [Přehled datových vazeb](../data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c564a-319">For more information about data binding, see [Data binding overview](../data/data-binding-overview.md).</span></span>

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. <span data-ttu-id="c564a-320">Po otevření <xref:System.Windows.Controls.Grid> elementu přidejte následující šablony dat, které definují, jak zobrazit data sestavy výdajů:</span><span class="sxs-lookup"><span data-stu-id="c564a-320">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data:</span></span>

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. <span data-ttu-id="c564a-321">Nahraďte<xref:System.Windows.Controls.DataGridTemplateColumn> elementy<xref:System.Windows.Controls.DataGrid> elementem a použijte pro ně šablony. <xref:System.Windows.Controls.DataGridTextColumn></span><span class="sxs-lookup"><span data-stu-id="c564a-321">Replace the <xref:System.Windows.Controls.DataGridTextColumn> elements with <xref:System.Windows.Controls.DataGridTemplateColumn> under the <xref:System.Windows.Controls.DataGrid> element and apply the templates to them.</span></span>

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. <span data-ttu-id="c564a-322">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c564a-322">Build and run the application.</span></span>

6. <span data-ttu-id="c564a-323">Vyberte osobu a pak vyberte tlačítko **Zobrazit** .</span><span class="sxs-lookup"><span data-stu-id="c564a-323">Select a person and then select the **View** button.</span></span>

<span data-ttu-id="c564a-324">Následující ilustrace znázorňuje obě stránky `ExpenseIt` aplikace s ovládacími prvky, rozložením, styly, datovými vazbami a použitými šablonami dat:</span><span class="sxs-lookup"><span data-stu-id="c564a-324">The following illustration shows both pages of the `ExpenseIt` application with controls, layout, styles, data binding, and data templates applied:</span></span>

![Obě stránky aplikace zobrazují seznam názvů a sestavu výdajů.](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> <span data-ttu-id="c564a-326">Tato ukázka demonstruje konkrétní funkci WPF a nedodržuje všechny osvědčené postupy pro věci, jako je zabezpečení, lokalizace a přístupnost.</span><span class="sxs-lookup"><span data-stu-id="c564a-326">This sample demonstrates a specific feature of WPF and doesn't follow all best practices for things like security, localization, and accessibility.</span></span> <span data-ttu-id="c564a-327">Pro komplexní pokrytí prostředí WPF a osvědčených postupů vývoje aplikací .NET si přečtěte následující témata:</span><span class="sxs-lookup"><span data-stu-id="c564a-327">For comprehensive coverage of WPF and the .NET app development best practices, see the following topics:</span></span>
>
> - [<span data-ttu-id="c564a-328">Usnadnění</span><span class="sxs-lookup"><span data-stu-id="c564a-328">Accessibility</span></span>](../../ui-automation/accessibility-best-practices.md)
>
> - [<span data-ttu-id="c564a-329">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c564a-329">Security</span></span>](../security-wpf.md)
>
> - [<span data-ttu-id="c564a-330">Globalizace a lokalizace WPF</span><span class="sxs-lookup"><span data-stu-id="c564a-330">WPF globalization and localization</span></span>](../advanced/wpf-globalization-and-localization-overview.md)
>
> - [<span data-ttu-id="c564a-331">Výkon WPF</span><span class="sxs-lookup"><span data-stu-id="c564a-331">WPF performance</span></span>](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a><span data-ttu-id="c564a-332">Další postup</span><span class="sxs-lookup"><span data-stu-id="c564a-332">Next steps</span></span>

<span data-ttu-id="c564a-333">V tomto návodu jste se naučili řadou postupů pro vytvoření uživatelského rozhraní pomocí Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="c564a-333">In this walkthrough you learned a number of techniques for creating a UI using Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="c564a-334">Nyní byste měli mít základní znalosti stavebních bloků aplikace .NET vázané na data.</span><span class="sxs-lookup"><span data-stu-id="c564a-334">You should now have a basic understanding of the building blocks of a data-bound .NET app.</span></span> <span data-ttu-id="c564a-335">Další informace o architektuře a programovacích modelech WPF naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="c564a-335">For more information about the WPF architecture and programming models, see the following topics:</span></span>

- [<span data-ttu-id="c564a-336">Architektura WPF</span><span class="sxs-lookup"><span data-stu-id="c564a-336">WPF architecture</span></span>](../advanced/wpf-architecture.md)
- [<span data-ttu-id="c564a-337">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="c564a-337">XAML overview (WPF)</span></span>](../advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="c564a-338">Přehled vlastností závislosti</span><span class="sxs-lookup"><span data-stu-id="c564a-338">Dependency properties overview</span></span>](../advanced/dependency-properties-overview.md)
- [<span data-ttu-id="c564a-339">Rozložení</span><span class="sxs-lookup"><span data-stu-id="c564a-339">Layout</span></span>](../advanced/layout.md)

<span data-ttu-id="c564a-340">Další informace o vytváření aplikací naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="c564a-340">For more information about creating applications, see the following topics:</span></span>

- [<span data-ttu-id="c564a-341">Vývoj aplikací</span><span class="sxs-lookup"><span data-stu-id="c564a-341">Application development</span></span>](../app-development/index.md)
- [<span data-ttu-id="c564a-342">Ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="c564a-342">Controls</span></span>](../controls/index.md)
- [<span data-ttu-id="c564a-343">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="c564a-343">Data binding overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="c564a-344">Grafika a multimédia</span><span class="sxs-lookup"><span data-stu-id="c564a-344">Graphics and multimedia</span></span>](../graphics-multimedia/index.md)
- [<span data-ttu-id="c564a-345">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="c564a-345">Documents in WPF</span></span>](../advanced/documents-in-wpf.md)

## <a name="see-also"></a><span data-ttu-id="c564a-346">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c564a-346">See also</span></span>

- [<span data-ttu-id="c564a-347">Přehled panelů</span><span class="sxs-lookup"><span data-stu-id="c564a-347">Panels overview</span></span>](../controls/panels-overview.md)
- [<span data-ttu-id="c564a-348">Přehled šablonování dat</span><span class="sxs-lookup"><span data-stu-id="c564a-348">Data templating overview</span></span>](../data/data-templating-overview.md)
- [<span data-ttu-id="c564a-349">Sestavení aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="c564a-349">Build a WPF application</span></span>](../app-development/building-a-wpf-application-wpf.md)
- [<span data-ttu-id="c564a-350">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="c564a-350">Styles and templates</span></span>](../controls/styles-and-templates.md)
