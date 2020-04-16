---
title: Vytvoření první aplikace WPF ve Visual Studiu 2019 – rozhraní .NET Framework
titleSuffix: ''
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
ms.openlocfilehash: facb9ebebd9ce1904886a946277185ac2c2e4bc4
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463927"
---
# <a name="tutorial-create-your-first-wpf-application-in-visual-studio-2019"></a><span data-ttu-id="49aec-102">Kurz: Vytvoření první aplikace WPF v Sadě Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="49aec-102">Tutorial: Create your first WPF application in Visual Studio 2019</span></span>

<span data-ttu-id="49aec-103">Tento článek ukazuje, jak vyvinout desktopovou aplikaci WPF (Windows Presentation Foundation), která obsahuje prvky, které jsou společné pro většinu aplikací WPF: značky Xml (XAML) extensible Application Markup Language (XAML), kód na pozadí, definice aplikací, ovládací prvky, rozložení, datové vazby a styly.</span><span class="sxs-lookup"><span data-stu-id="49aec-103">This article shows you how to develop a Windows Presentation Foundation (WPF) desktop application that includes the elements that are common to most WPF applications: Extensible Application Markup Language (XAML) markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span> <span data-ttu-id="49aec-104">K vývoji aplikace budete používat Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="49aec-104">To develop the application, you'll use Visual Studio.</span></span>

<span data-ttu-id="49aec-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="49aec-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="49aec-106">Vytvořte projekt WPF.</span><span class="sxs-lookup"><span data-stu-id="49aec-106">Create a WPF project.</span></span>
> - <span data-ttu-id="49aec-107">Pomocí XAML navrhnout vzhled uživatelského rozhraní aplikace (UI).</span><span class="sxs-lookup"><span data-stu-id="49aec-107">Use XAML to design the appearance of the application's user interface (UI).</span></span>
> - <span data-ttu-id="49aec-108">Napište kód pro sestavení chování aplikace.</span><span class="sxs-lookup"><span data-stu-id="49aec-108">Write code to build the application's behavior.</span></span>
> - <span data-ttu-id="49aec-109">Vytvořte definici aplikace pro správu aplikace.</span><span class="sxs-lookup"><span data-stu-id="49aec-109">Create an application definition to manage the application.</span></span>
> - <span data-ttu-id="49aec-110">Přidejte ovládací prvky a vytvořte rozložení pro vytvoření uživatelského rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="49aec-110">Add controls and create the layout to compose the application UI.</span></span>
> - <span data-ttu-id="49aec-111">Vytvořte styly pro konzistentní vzhled v celém ui aplikace.</span><span class="sxs-lookup"><span data-stu-id="49aec-111">Create styles for a consistent appearance throughout the application's UI.</span></span>
> - <span data-ttu-id="49aec-112">Svázat ui s daty, a to jak k naplnění ui z dat a zachovat data a ui synchronizovány.</span><span class="sxs-lookup"><span data-stu-id="49aec-112">Bind the UI to data, both to populate the UI from data and to keep the data and UI synchronized.</span></span>

<span data-ttu-id="49aec-113">Na konci kurzu budete mít vytvořenou samostatnou aplikaci systému Windows, která uživatelům umožňuje zobrazit vyúčtování výdajů pro vybrané uživatele.</span><span class="sxs-lookup"><span data-stu-id="49aec-113">By the end of the tutorial, you'll have built a standalone Windows application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="49aec-114">Aplikace se skládá z několika stránek WPF, které jsou hostovány v okně stylu prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="49aec-114">The application is composed of several WPF pages that are hosted in a browser-style window.</span></span>

> [!TIP]
> <span data-ttu-id="49aec-115">Ukázkový kód, který se používá v tomto kurzu je k dispozici pro visual basic a C# v [kurzu WPF ukázkový kód aplikace](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span><span class="sxs-lookup"><span data-stu-id="49aec-115">The sample code that is used in this tutorial is available for both Visual Basic and C# at [Tutorial WPF App Sample Code](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span></span>
>
> <span data-ttu-id="49aec-116">Jazyk kódu ukázkového kódu mezi jazyky C# a Visual Basic můžete přepnout pomocí voliče jazyka v horní části této stránky.</span><span class="sxs-lookup"><span data-stu-id="49aec-116">You can toggle the code language of the sample code between C# and Visual Basic by using the language selector on top of this page.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="49aec-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="49aec-117">Prerequisites</span></span>

- <span data-ttu-id="49aec-118">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou **úlohou pro vývoj desktopů .NET.**</span><span class="sxs-lookup"><span data-stu-id="49aec-118">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET desktop development** workload installed.</span></span>

   <span data-ttu-id="49aec-119">Další informace o instalaci nejnovější verze sady Visual Studio naleznete v [tématu Instalace sady Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="49aec-119">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="49aec-120">Vytvoření projektu aplikace</span><span class="sxs-lookup"><span data-stu-id="49aec-120">Create the application project</span></span>

<span data-ttu-id="49aec-121">Prvním krokem je vytvoření aplikační infrastruktury, která zahrnuje definici aplikace, dvě stránky a bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="49aec-121">The first step is to create the application infrastructure, which includes an application definition, two pages, and an image.</span></span>

1. <span data-ttu-id="49aec-122">Vytvořte nový projekt aplikace WPF v jazyce Visual Basic nebo Visual C# s názvem **`ExpenseIt`**:</span><span class="sxs-lookup"><span data-stu-id="49aec-122">Create a new WPF Application project in Visual Basic or Visual C# named **`ExpenseIt`**:</span></span>

   1. <span data-ttu-id="49aec-123">V nabídce **Začínáme** otevřete Visual Studio a vyberte **Vytvořit nový projekt.**</span><span class="sxs-lookup"><span data-stu-id="49aec-123">Open Visual Studio and select **Create a new project** under the **Get started** menu.</span></span>

      <span data-ttu-id="49aec-124">Otevře se dialogové okno **Vytvořit nový projekt.**</span><span class="sxs-lookup"><span data-stu-id="49aec-124">The **Create a new project** dialog opens.</span></span>

   2. <span data-ttu-id="49aec-125">V rozevíracím **souboru Jazyk** vyberte **c#** nebo **visual basic**.</span><span class="sxs-lookup"><span data-stu-id="49aec-125">In the **Language** dropdown, select either **C#** or **Visual Basic**.</span></span>

   3. <span data-ttu-id="49aec-126">Vyberte šablonu **aplikace WPF (.NET Framework)** a pak vyberte **Další**.</span><span class="sxs-lookup"><span data-stu-id="49aec-126">Select the **WPF App (.NET Framework)** template and then select **Next**.</span></span>

      ![Vytvořit dialogové okno vytvořit nový projekt](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)

      <span data-ttu-id="49aec-128">Otevře se dialogové okno **Konfigurovat nový projekt.**</span><span class="sxs-lookup"><span data-stu-id="49aec-128">The **Configure your new project** dialog opens.</span></span>

   4. <span data-ttu-id="49aec-129">Zadejte název **`ExpenseIt`** projektu a pak vyberte **Vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="49aec-129">Enter the project name **`ExpenseIt`** and then select **Create**.</span></span>

      ![Konfigurace dialogového okna nového projektu](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      <span data-ttu-id="49aec-131">Visual Studio vytvoří projekt a otevře návrháře pro výchozí okno aplikace s názvem **MainWindow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="49aec-131">Visual Studio creates the project and opens the designer for the default application window named **MainWindow.xaml**.</span></span>

2. <span data-ttu-id="49aec-132">Otevřete *soubor Application.xaml* (Visual Basic) nebo *Soubor App.xaml* (C#).</span><span class="sxs-lookup"><span data-stu-id="49aec-132">Open *Application.xaml* (Visual Basic) or *App.xaml* (C#).</span></span>

    <span data-ttu-id="49aec-133">Tento soubor XAML definuje aplikaci WPF a všechny prostředky aplikace.</span><span class="sxs-lookup"><span data-stu-id="49aec-133">This XAML file defines a WPF application and any application resources.</span></span> <span data-ttu-id="49aec-134">Tento soubor můžete také použít k určení uživatelského uživatelského okna, v tomto případě *MainWindow.xaml*, který se automaticky zobrazí při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="49aec-134">You also use this file to specify the UI, in this case *MainWindow.xaml*, that automatically shows when the application starts.</span></span>

    <span data-ttu-id="49aec-135">XAML by měl vypadat takto v jazyce Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="49aec-135">Your XAML should look like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    <span data-ttu-id="49aec-136">A stejně jako následující v C#:</span><span class="sxs-lookup"><span data-stu-id="49aec-136">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. <span data-ttu-id="49aec-137">Otevřete *soubor MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="49aec-137">Open *MainWindow.xaml*.</span></span>

    <span data-ttu-id="49aec-138">Tento soubor XAML je hlavním oknem vaší aplikace a zobrazuje obsah vytvořený na stránkách.</span><span class="sxs-lookup"><span data-stu-id="49aec-138">This XAML file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="49aec-139">Třída <xref:System.Windows.Window> definuje vlastnosti okna, jako je jeho název, velikost nebo ikona, a zpracovává události, jako je například zavření nebo skrytí.</span><span class="sxs-lookup"><span data-stu-id="49aec-139">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span>

4. <span data-ttu-id="49aec-140">Změňte <xref:System.Windows.Window> prvek <xref:System.Windows.Navigation.NavigationWindow>na , jak je znázorněno v následujícím xaml:</span><span class="sxs-lookup"><span data-stu-id="49aec-140">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>, as shown in the following XAML:</span></span>

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   <span data-ttu-id="49aec-141">Tato aplikace přejde na jiný obsah v závislosti na vstupu uživatele.</span><span class="sxs-lookup"><span data-stu-id="49aec-141">This app navigates to different content depending on the user input.</span></span> <span data-ttu-id="49aec-142">To je důvod, proč hlavní <xref:System.Windows.Window> <xref:System.Windows.Navigation.NavigationWindow>je třeba změnit na .</span><span class="sxs-lookup"><span data-stu-id="49aec-142">This is why the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="49aec-143"><xref:System.Windows.Navigation.NavigationWindow>dědí všechny vlastnosti . <xref:System.Windows.Window></span><span class="sxs-lookup"><span data-stu-id="49aec-143"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="49aec-144">Prvek <xref:System.Windows.Navigation.NavigationWindow> v souboru XAML vytvoří <xref:System.Windows.Navigation.NavigationWindow> instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="49aec-144">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="49aec-145">Další informace naleznete v tématu [Navigační přehled](../app-development/navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="49aec-145">For more information, see [Navigation overview](../app-development/navigation-overview.md).</span></span>

5. <span data-ttu-id="49aec-146">Odstraňte <xref:System.Windows.Controls.Grid> prvky <xref:System.Windows.Navigation.NavigationWindow> mezi značkami.</span><span class="sxs-lookup"><span data-stu-id="49aec-146">Remove the <xref:System.Windows.Controls.Grid> elements from between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span>

6. <span data-ttu-id="49aec-147">Změňte následující vlastnosti v kódu <xref:System.Windows.Navigation.NavigationWindow> XAML pro prvek:</span><span class="sxs-lookup"><span data-stu-id="49aec-147">Change the following properties in the XAML code for the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>

    - <span data-ttu-id="49aec-148">Nastavte <xref:System.Windows.Window.Title%2A> vlastnost na`ExpenseIt`" ".</span><span class="sxs-lookup"><span data-stu-id="49aec-148">Set the <xref:System.Windows.Window.Title%2A> property to "`ExpenseIt`".</span></span>

    - <span data-ttu-id="49aec-149">Nastavte <xref:System.Windows.FrameworkElement.Height%2A> vlastnost na 350 pixelů.</span><span class="sxs-lookup"><span data-stu-id="49aec-149">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span>

    - <span data-ttu-id="49aec-150">Nastavte <xref:System.Windows.FrameworkElement.Width%2A> vlastnost na 500 pixelů.</span><span class="sxs-lookup"><span data-stu-id="49aec-150">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span>

    <span data-ttu-id="49aec-151">XAML by měl vypadat takto pro Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="49aec-151">Your XAML should look like the following for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    <span data-ttu-id="49aec-152">A stejně jako následující pro C#:</span><span class="sxs-lookup"><span data-stu-id="49aec-152">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. <span data-ttu-id="49aec-153">Otevřete *soubor MainWindow.xaml.vb* nebo *MainWindow.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="49aec-153">Open *MainWindow.xaml.vb* or *MainWindow.xaml.cs*.</span></span>

    <span data-ttu-id="49aec-154">Tento soubor je soubor s kódem na pozadí, který obsahuje kód pro zpracování událostí deklarovaných v *MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="49aec-154">This file is a code-behind file that contains code to handle the events declared in *MainWindow.xaml*.</span></span> <span data-ttu-id="49aec-155">Tento soubor obsahuje částečnou třídu pro okno definované v XAML.</span><span class="sxs-lookup"><span data-stu-id="49aec-155">This file contains a partial class for the window defined in XAML.</span></span>

8. <span data-ttu-id="49aec-156">Pokud používáte C#, změňte třídu, `MainWindow` která má být odvozena od <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="49aec-156">If you're using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="49aec-157">(V jazyce Visual Basic k tomu dojde automaticky při změně okna v XAML.) Kód jazyka C# by nyní měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="49aec-157">(In Visual Basic, this happens automatically when you change the window in XAML.) Your C# code should now look like this:</span></span>

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a><span data-ttu-id="49aec-158">Přidání souborů do aplikace</span><span class="sxs-lookup"><span data-stu-id="49aec-158">Add files to the application</span></span>

<span data-ttu-id="49aec-159">V této části přidáte do aplikace dvě stránky a obrázek.</span><span class="sxs-lookup"><span data-stu-id="49aec-159">In this section, you'll add two pages and an image to the application.</span></span>

1. <span data-ttu-id="49aec-160">Přidejte do projektu novou stránku *`ExpenseItHome.xaml`* a pojmenujte ji :</span><span class="sxs-lookup"><span data-stu-id="49aec-160">Add a new page to the project, and name it *`ExpenseItHome.xaml`*:</span></span>

   1. <span data-ttu-id="49aec-161">V **Průzkumníku řešení**klikněte **`ExpenseIt`** pravým tlačítkem myši na uzel projektu a zvolte **Přidat** > **stránku**.</span><span class="sxs-lookup"><span data-stu-id="49aec-161">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="49aec-162">V dialogovém okně **Přidat novou položku** je šablona **Stránka (WPF)** již vybraná.</span><span class="sxs-lookup"><span data-stu-id="49aec-162">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="49aec-163">Zadejte **`ExpenseItHome`** název a pak vyberte **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="49aec-163">Enter the name **`ExpenseItHome`**, and then select **Add**.</span></span>

    <span data-ttu-id="49aec-164">Tato stránka je první stránka, která se zobrazí při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="49aec-164">This page is the first page that's displayed when the application is launched.</span></span> <span data-ttu-id="49aec-165">Zobrazí se seznam osob, ze kterých je třeba vybrat, pro které se zobrazí vyúčtování výdajů.</span><span class="sxs-lookup"><span data-stu-id="49aec-165">It will show a list of people to select from, to show an expense report for.</span></span>

1. <span data-ttu-id="49aec-166">Otevřít *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="49aec-166">Open *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="49aec-167">Nastavte <xref:System.Windows.Controls.Page.Title%2A> na`ExpenseIt - Home`" ".</span><span class="sxs-lookup"><span data-stu-id="49aec-167">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - Home`".</span></span>

1. <span data-ttu-id="49aec-168">Nastavte `DesignHeight` 350 pixelů a `DesignWidth` 500 pixelů.</span><span class="sxs-lookup"><span data-stu-id="49aec-168">Set the `DesignHeight` to 350 pixels and the `DesignWidth` to 500 pixels.</span></span>

    <span data-ttu-id="49aec-169">XAML se nyní zobrazí takto pro visual basic:</span><span class="sxs-lookup"><span data-stu-id="49aec-169">The XAML now appears as follows for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    <span data-ttu-id="49aec-170">A stejně jako následující pro C#:</span><span class="sxs-lookup"><span data-stu-id="49aec-170">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. <span data-ttu-id="49aec-171">Otevřete *soubor MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="49aec-171">Open *MainWindow.xaml*.</span></span>

1. <span data-ttu-id="49aec-172">Přidejte <xref:System.Windows.Navigation.NavigationWindow.Source%2A> vlastnost <xref:System.Windows.Navigation.NavigationWindow> do prvku a`ExpenseItHome.xaml`nastavte ji na " ".</span><span class="sxs-lookup"><span data-stu-id="49aec-172">Add a <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property to the <xref:System.Windows.Navigation.NavigationWindow> element and set it to "`ExpenseItHome.xaml`".</span></span>

    <span data-ttu-id="49aec-173">To *`ExpenseItHome.xaml`* nastaví první stránku otevřenou při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="49aec-173">This sets *`ExpenseItHome.xaml`* to be the first page opened when the application starts.</span></span>

    <span data-ttu-id="49aec-174">Příklad XAML v jazyce Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="49aec-174">Example XAML in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    <span data-ttu-id="49aec-175">A v C#:</span><span class="sxs-lookup"><span data-stu-id="49aec-175">And in C#:</span></span>

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > <span data-ttu-id="49aec-176">Můžete také nastavit **Source** vlastnost v různé **kategorie** okna **Vlastnosti.**</span><span class="sxs-lookup"><span data-stu-id="49aec-176">You can also set the **Source** property in the **Miscellaneous** category of the **Properties** window.</span></span>
   >
   > ![Zdrojová vlastnost v okně Vlastnosti](./media/properties-source.png)

1. <span data-ttu-id="49aec-178">Přidejte do projektu další novou stránku WPF a pojmenujte ji *ExpenseReportPage.xaml*::</span><span class="sxs-lookup"><span data-stu-id="49aec-178">Add another new WPF page to the project, and name it *ExpenseReportPage.xaml*::</span></span>

   1. <span data-ttu-id="49aec-179">V **Průzkumníku řešení**klikněte **`ExpenseIt`** pravým tlačítkem myši na uzel projektu a zvolte **Přidat** > **stránku**.</span><span class="sxs-lookup"><span data-stu-id="49aec-179">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="49aec-180">V dialogovém okně **Přidat novou položku** vyberte šablonu **Stránky (WPF).**</span><span class="sxs-lookup"><span data-stu-id="49aec-180">In the **Add New Item** dialog, select the **Page (WPF)** template.</span></span> <span data-ttu-id="49aec-181">Zadejte název **ExpenseReportPage**a pak vyberte **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="49aec-181">Enter the name **ExpenseReportPage**, and then select **Add**.</span></span>

    <span data-ttu-id="49aec-182">Na této stránce se zobrazí vyúčtování výdajů **`ExpenseItHome`** pro osobu, která je na stránce vybrána.</span><span class="sxs-lookup"><span data-stu-id="49aec-182">This page will show the expense report for the person that is selected on the **`ExpenseItHome`** page.</span></span>

1. <span data-ttu-id="49aec-183">Otevřete *soubor ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="49aec-183">Open *ExpenseReportPage.xaml*.</span></span>

1. <span data-ttu-id="49aec-184">Nastavte <xref:System.Windows.Controls.Page.Title%2A> na`ExpenseIt - View Expense`" ".</span><span class="sxs-lookup"><span data-stu-id="49aec-184">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - View Expense`".</span></span>

1. <span data-ttu-id="49aec-185">Nastavte `DesignHeight` 350 pixelů a `DesignWidth` 500 pixelů.</span><span class="sxs-lookup"><span data-stu-id="49aec-185">Set the `DesignHeight` to 350 pixels and the `DesignWidth` to 500 pixels.</span></span>

    <span data-ttu-id="49aec-186">*ExpenseReportPage.xaml* teď vypadá takto v jazyce Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="49aec-186">*ExpenseReportPage.xaml* now looks like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    <span data-ttu-id="49aec-187">A stejně jako následující v C#:</span><span class="sxs-lookup"><span data-stu-id="49aec-187">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. <span data-ttu-id="49aec-188">Otevřete *stránku ExpenseItHome.xaml.vb* a *ExpenseReportPage.xaml.vb*nebo *ExpenseItHome.xaml.cs* a *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="49aec-188">Open *ExpenseItHome.xaml.vb* and *ExpenseReportPage.xaml.vb*, or *ExpenseItHome.xaml.cs* and *ExpenseReportPage.xaml.cs*.</span></span>

    <span data-ttu-id="49aec-189">Když vytvoříte nový soubor Stránky, Visual Studio automaticky vytvoří jeho soubor *s kódem na pozadí.*</span><span class="sxs-lookup"><span data-stu-id="49aec-189">When you create a new Page file, Visual Studio automatically creates its *code-behind* file.</span></span> <span data-ttu-id="49aec-190">Tyto soubory s kódem na pozadí zpracovávají logiku pro reakci na vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="49aec-190">These code-behind files handle the logic for responding to user input.</span></span>

    <span data-ttu-id="49aec-191">Váš kód by měl **`ExpenseItHome`** vypadat takto pro :</span><span class="sxs-lookup"><span data-stu-id="49aec-191">Your code should look like the following for **`ExpenseItHome`**:</span></span>

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    <span data-ttu-id="49aec-192">A stejně jako následující pro **ExpenseReportPage**:</span><span class="sxs-lookup"><span data-stu-id="49aec-192">And like the following for **ExpenseReportPage**:</span></span>

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. <span data-ttu-id="49aec-193">Přidejte do projektu obrázek s názvem *vodoznak.png.*</span><span class="sxs-lookup"><span data-stu-id="49aec-193">Add an image named *watermark.png* to the project.</span></span> <span data-ttu-id="49aec-194">Můžete vytvořit vlastní bitovou kopii, zkopírovat soubor z ukázkového kódu nebo jej získat z úložiště [GitHub microsoft/WPF-Samples.](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png)</span><span class="sxs-lookup"><span data-stu-id="49aec-194">You can create your own image, copy the file from the sample code, or get it from the [microsoft/WPF-Samples](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png) GitHub repository.</span></span>

    1. <span data-ttu-id="49aec-195">Klikněte pravým tlačítkem myši na uzel projektu a vyberte **Přidat** > **existující položku**nebo stiskněte **Shift**+**Alt**+**A**.</span><span class="sxs-lookup"><span data-stu-id="49aec-195">Right-click on the project node and select **Add** > **Existing Item**, or press **Shift**+**Alt**+**A**.</span></span>

    2. <span data-ttu-id="49aec-196">V dialogovém okně **Přidat existující položku** nastavte filtr souborů na **všechny soubory** nebo **obrazové soubory**, vyhledejte soubor obrazu, který chcete použít, a pak vyberte **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="49aec-196">In the **Add Existing Item** dialog, set the file filter to either **All Files** or **Image Files**, browse to the image file you want to use, and then select **Add**.</span></span>

## <a name="build-and-run-the-application"></a><span data-ttu-id="49aec-197">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="49aec-197">Build and run the application</span></span>

1. <span data-ttu-id="49aec-198">Chcete-li vytvořit a spustit aplikaci, stiskněte **klávesu F5** nebo v yberte **Spustit ladění** z nabídky **Ladění.**</span><span class="sxs-lookup"><span data-stu-id="49aec-198">To build and run the application, press **F5** or select **Start Debugging** from the **Debug** menu.</span></span>

    <span data-ttu-id="49aec-199">Následující obrázek znázorňuje <xref:System.Windows.Navigation.NavigationWindow> aplikaci s tlačítky:</span><span class="sxs-lookup"><span data-stu-id="49aec-199">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons:</span></span>

    ![Aplikace po sestavení a spuštění.](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. <span data-ttu-id="49aec-201">Zavřete aplikaci a vraťte se do sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="49aec-201">Close the application to return to Visual Studio.</span></span>

## <a name="create-the-layout"></a><span data-ttu-id="49aec-202">Vytvoření rozložení</span><span class="sxs-lookup"><span data-stu-id="49aec-202">Create the layout</span></span>

<span data-ttu-id="49aec-203">Rozložení poskytuje seřazený způsob umístění prvků uživatelského rozhraní a také spravuje velikost a umístění těchto prvků při změně velikosti uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="49aec-203">Layout provides an ordered way to place UI elements, and also manages the size and position of those elements when a UI is resized.</span></span> <span data-ttu-id="49aec-204">Obvykle vytvoříte rozložení s jedním z následujících ovládacích prvků rozložení:</span><span class="sxs-lookup"><span data-stu-id="49aec-204">You typically create a layout with one of the following layout controls:</span></span>

- <span data-ttu-id="49aec-205"><xref:System.Windows.Controls.Canvas>- Definuje oblast, ve které můžete explicitně umístit podřízené prvky pomocí souřadnic, které jsou vzhledem k oblasti Plátno.</span><span class="sxs-lookup"><span data-stu-id="49aec-205"><xref:System.Windows.Controls.Canvas> - Defines an area within which you can explicitly position child elements by using coordinates that are relative to the Canvas area.</span></span>
- <span data-ttu-id="49aec-206"><xref:System.Windows.Controls.DockPanel>- Definuje oblast, kde můžete uspořádat podřízené prvky buď vodorovně nebo svisle, vzhledem k sobě navzájem.</span><span class="sxs-lookup"><span data-stu-id="49aec-206"><xref:System.Windows.Controls.DockPanel> - Defines an area where you can arrange child elements either horizontally or vertically, relative to each other.</span></span>
- <span data-ttu-id="49aec-207"><xref:System.Windows.Controls.Grid>- Definuje flexibilní oblast mřížky, která se skládá ze sloupců a řádků.</span><span class="sxs-lookup"><span data-stu-id="49aec-207"><xref:System.Windows.Controls.Grid> - Defines a flexible grid area that consists of columns and rows.</span></span>
- <span data-ttu-id="49aec-208"><xref:System.Windows.Controls.StackPanel>- Uspořádá podřízené prvky do jedné čáry, která může být orientována vodorovně nebo svisle.</span><span class="sxs-lookup"><span data-stu-id="49aec-208"><xref:System.Windows.Controls.StackPanel> - Arranges child elements into a single line that can be oriented horizontally or vertically.</span></span>
- <span data-ttu-id="49aec-209"><xref:System.Windows.Controls.VirtualizingStackPanel>- Uspořádá a virtualizuje obsah na jednom řádku, který je orientován vodorovně nebo svisle.</span><span class="sxs-lookup"><span data-stu-id="49aec-209"><xref:System.Windows.Controls.VirtualizingStackPanel> - Arranges and virtualizes content on a single line that is oriented either horizontally or vertically.</span></span>
- <span data-ttu-id="49aec-210"><xref:System.Windows.Controls.WrapPanel>- Umístí podřízené prvky v sekvenční poloze zleva doprava, čímž přeruší obsah na další řádek na okraji obsahující krabice.</span><span class="sxs-lookup"><span data-stu-id="49aec-210"><xref:System.Windows.Controls.WrapPanel> - Positions child elements in sequential position from left to right, breaking content to the next line at the edge of the containing box.</span></span> <span data-ttu-id="49aec-211">Následné řazení probíhá postupně shora dolů nebo zprava doleva, v závislosti na hodnotě Orientation vlastnost.</span><span class="sxs-lookup"><span data-stu-id="49aec-211">Subsequent ordering happens sequentially from top to bottom or from right to left, depending on the value of the Orientation property.</span></span>

<span data-ttu-id="49aec-212">Každý z těchto ovládacích prvků rozložení podporuje určitý typ rozložení pro jeho podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="49aec-212">Each of these layout controls supports a particular type of layout for its child elements.</span></span> <span data-ttu-id="49aec-213">`ExpenseIt`stránky lze velikost a každá stránka obsahuje prvky, které jsou uspořádány vodorovně a svisle vedle jiných prvků.</span><span class="sxs-lookup"><span data-stu-id="49aec-213">`ExpenseIt` pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="49aec-214">V tomto příkladu <xref:System.Windows.Controls.Grid> se používá jako prvek rozložení pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="49aec-214">In this example, the <xref:System.Windows.Controls.Grid> is used as  layout element for the application.</span></span>

> [!TIP]
> <span data-ttu-id="49aec-215">Další informace <xref:System.Windows.Controls.Panel> o prvcích naleznete v [tématu Přehled panelů](../controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="49aec-215">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels overview](../controls/panels-overview.md).</span></span> <span data-ttu-id="49aec-216">Další informace o rozložení naleznete v [tématu Layout](../advanced/layout.md).</span><span class="sxs-lookup"><span data-stu-id="49aec-216">For more information about layout, see [Layout](../advanced/layout.md).</span></span>

<span data-ttu-id="49aec-217">V této části vytvoříte tabulku s jedním sloupcem se třemi řádky a okrajem <xref:System.Windows.Controls.Grid> 10 pixelů přidáním definic sloupců a řádků do v *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="49aec-217">In this section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="49aec-218">V *`ExpenseItHome.xaml`* <xref:System.Windows.FrameworkElement.Margin%2A> nastavíte vlastnost <xref:System.Windows.Controls.Grid> prvku na "10,0,10,10", což odpovídá levému, hornímu, pravému a dolnímu okraji:</span><span class="sxs-lookup"><span data-stu-id="49aec-218">In *`ExpenseItHome.xaml`*, set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10", which corresponds to left, top, right and bottom margins:</span></span>

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > <span data-ttu-id="49aec-219">Hodnoty **okraje** můžete také nastavit v okně **Vlastnosti** v kategorii **Rozložení:**</span><span class="sxs-lookup"><span data-stu-id="49aec-219">You can also set the **Margin** values in the **Properties** window, under the **Layout** category:</span></span>
   >
   > ![Hodnoty okrajů v okně Vlastnosti](./media/properties-margin.png)

2. <span data-ttu-id="49aec-221">Chcete-li vytvořit definice <xref:System.Windows.Controls.Grid> řádků a sloupců, přidejte mezi značky xaml následující:</span><span class="sxs-lookup"><span data-stu-id="49aec-221">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions:</span></span>

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <span data-ttu-id="49aec-222">Dva <xref:System.Windows.Controls.RowDefinition.Height%2A> řádky je nastavena na <xref:System.Windows.GridLength.Auto%2A>, což znamená, že řádky jsou velikosti na základě obsahu v řádcích.</span><span class="sxs-lookup"><span data-stu-id="49aec-222">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A>, which means that the rows are sized based on the content in the rows.</span></span> <span data-ttu-id="49aec-223">Výchozí <xref:System.Windows.Controls.RowDefinition.Height%2A> hodnota <xref:System.Windows.GridUnitType.Star> je velikost, což znamená, že výška řádku je vážený majem k dispozici.</span><span class="sxs-lookup"><span data-stu-id="49aec-223">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row height is a weighted proportion of the available space.</span></span> <span data-ttu-id="49aec-224">Například pokud dva řádky <xref:System.Windows.Controls.RowDefinition.Height%2A> každý z "\*", každý z nich má výšku, která je polovina dostupného místa.</span><span class="sxs-lookup"><span data-stu-id="49aec-224">For example if two rows each have a <xref:System.Windows.Controls.RowDefinition.Height%2A> of "\*", they each have a height that is half of the available space.</span></span>

    <span data-ttu-id="49aec-225">Nyní <xref:System.Windows.Controls.Grid> byste měli obsahovat následující XAML:</span><span class="sxs-lookup"><span data-stu-id="49aec-225">Your <xref:System.Windows.Controls.Grid> should now contain the following XAML:</span></span>

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a><span data-ttu-id="49aec-226">Přidání ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="49aec-226">Add controls</span></span>

<span data-ttu-id="49aec-227">V této části aktualizujete ui domovské stránky tak, aby zobrazovalo seznam lidí, kde vyberete jednu osobu, která zobrazí vyúčtování výdajů.</span><span class="sxs-lookup"><span data-stu-id="49aec-227">In this section, you'll update the home page UI to show a list of people, where you select one person to display their expense report.</span></span> <span data-ttu-id="49aec-228">Ovládací prvky jsou objekty uživatelského rozhraní, které umožňují uživatelům pracovat s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="49aec-228">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="49aec-229">Další informace naleznete v [tématu Controls](../controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="49aec-229">For more information, see [Controls](../controls/index.md).</span></span>

<span data-ttu-id="49aec-230">Chcete-li vytvořit toto uživatelské rozhraní, *`ExpenseItHome.xaml`* přidáte do aplikace :</span><span class="sxs-lookup"><span data-stu-id="49aec-230">To create this UI, you'll add the following elements to *`ExpenseItHome.xaml`*:</span></span>

- <span data-ttu-id="49aec-231">A <xref:System.Windows.Controls.ListBox> (pro seznam lidí).</span><span class="sxs-lookup"><span data-stu-id="49aec-231">A <xref:System.Windows.Controls.ListBox> (for the list of people).</span></span>
- <span data-ttu-id="49aec-232">A <xref:System.Windows.Controls.Label> (pro záhlaví seznamu).</span><span class="sxs-lookup"><span data-stu-id="49aec-232">A <xref:System.Windows.Controls.Label> (for the list header).</span></span>
- <span data-ttu-id="49aec-233">A <xref:System.Windows.Controls.Button> (kliknutím zobrazíte vyúčtování výdajů pro osobu, která je vybrána v seznamu).</span><span class="sxs-lookup"><span data-stu-id="49aec-233">A <xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span>

<span data-ttu-id="49aec-234">Každý ovládací prvek je umístěn <xref:System.Windows.Controls.Grid> v <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> řádku nastavením připojené vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="49aec-234">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="49aec-235">Další informace o připojených vlastnostech naleznete v tématu [Přehled připojených vlastností](../advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="49aec-235">For more information about attached properties, see [Attached Properties Overview](../advanced/attached-properties-overview.md).</span></span>

1. <span data-ttu-id="49aec-236">V *`ExpenseItHome.xaml`* aplikace přidejte mezi značky <xref:System.Windows.Controls.Grid> přibližně následující xaml:</span><span class="sxs-lookup"><span data-stu-id="49aec-236">In *`ExpenseItHome.xaml`*, add the following XAML somewhere between the <xref:System.Windows.Controls.Grid> tags:</span></span>

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > <span data-ttu-id="49aec-237">Ovládací prvky můžete také vytvořit přetažením z okna **panelu nástrojů** do okna návrhu a potom nastavením jejich vlastností v okně **Vlastnosti.**</span><span class="sxs-lookup"><span data-stu-id="49aec-237">You can also create the controls by dragging them from the **Toolbox** window onto the design window, and then setting their properties in the **Properties** window.</span></span>

2. <span data-ttu-id="49aec-238">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="49aec-238">Build and run the application.</span></span>

    <span data-ttu-id="49aec-239">Následující obrázek znázorňuje ovládací prvky, které jste vytvořili:</span><span class="sxs-lookup"><span data-stu-id="49aec-239">The following illustration shows the controls you created:</span></span>

![ExpenseIt ukázkový snímek obrazovky se seznamem jmen](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a><span data-ttu-id="49aec-241">Přidání obrázku a názvu</span><span class="sxs-lookup"><span data-stu-id="49aec-241">Add an image and a title</span></span>

<span data-ttu-id="49aec-242">V této části aktualizujete hlavní nastavení domovské stránky pomocí obrázku a názvu stránky.</span><span class="sxs-lookup"><span data-stu-id="49aec-242">In this section, you'll update the home page UI with an image and a page title.</span></span>

1. <span data-ttu-id="49aec-243">V *`ExpenseItHome.xaml`*, přidejte <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> další sloupec <xref:System.Windows.Controls.ColumnDefinition.Width%2A> s pevnou 230 pixelů:</span><span class="sxs-lookup"><span data-stu-id="49aec-243">In *`ExpenseItHome.xaml`*, add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels:</span></span>

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=2#NewColumn)]

2. <span data-ttu-id="49aec-244">Přidejte další <xref:System.Windows.Controls.Grid.RowDefinitions%2A>řádek do , pro celkem čtyři řádky:</span><span class="sxs-lookup"><span data-stu-id="49aec-244">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, for a total of four rows:</span></span>

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=2#NewRows)]

3. <span data-ttu-id="49aec-245">Přesuňte ovládací prvky do <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> druhého sloupce nastavením vlastnosti na 1 v každém ze tří ovládacích prvků (Border, ListBox a Button).</span><span class="sxs-lookup"><span data-stu-id="49aec-245">Move the controls to the second column by setting the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property to 1 in each of the three controls (Border, ListBox, and Button).</span></span>

4. <span data-ttu-id="49aec-246">Přesuňte každý ovládací prvek dolů řádek <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> zvýšením jeho hodnotu o 1 pro každý ze tří ovládacích prvků (Border, ListBox a Button) a border element.</span><span class="sxs-lookup"><span data-stu-id="49aec-246">Move each control down a row by incrementing its <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> value by 1 for each of the three controls (Border, ListBox, and Button) and for the Border element.</span></span>

   <span data-ttu-id="49aec-247">XAML pro tři ovládací prvky nyní vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="49aec-247">The XAML for the three controls now looks like the following:</span></span>

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. <span data-ttu-id="49aec-248">Nastavte <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> vlastnost na obrazový soubor *vodoznak.png* přidáním následujícího XAML kdekoli mezi `<Grid>` `</Grid>` a tagy:</span><span class="sxs-lookup"><span data-stu-id="49aec-248">Set the <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> property to the *watermark.png* image file, by adding the following XAML anywhere between the `<Grid>` and `</Grid>` tags:</span></span>

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. <span data-ttu-id="49aec-249">Před <xref:System.Windows.Controls.Border> prvek přidejte <xref:System.Windows.Controls.Label> a s obsahem "Zobrazit vyúčtování výdajů".</span><span class="sxs-lookup"><span data-stu-id="49aec-249">Before the <xref:System.Windows.Controls.Border> element, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report".</span></span> <span data-ttu-id="49aec-250">Tento popisek je název stránky.</span><span class="sxs-lookup"><span data-stu-id="49aec-250">This label is the title of the page.</span></span>

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. <span data-ttu-id="49aec-251">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="49aec-251">Build and run the application.</span></span>

<span data-ttu-id="49aec-252">Následující obrázek znázorňuje výsledky toho, co jste právě přidali:</span><span class="sxs-lookup"><span data-stu-id="49aec-252">The following illustration shows the results of what you just added:</span></span>

![ExpenseIt ukázkový snímek obrazovky s novým pozadím obrázku a názvem stránky](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a><span data-ttu-id="49aec-254">Přidání kódu pro zpracování událostí</span><span class="sxs-lookup"><span data-stu-id="49aec-254">Add code to handle events</span></span>

1. <span data-ttu-id="49aec-255">V *`ExpenseItHome.xaml`* souboru <xref:System.Windows.Controls.Primitives.ButtonBase.Click> přidejte <xref:System.Windows.Controls.Button> do prvku obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="49aec-255">In *`ExpenseItHome.xaml`*, add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="49aec-256">Další informace naleznete v [tématu Postup: Vytvoření jednoduché obslužné rutiny události](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="49aec-256">For more information, see [How to: Create a simple event handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. <span data-ttu-id="49aec-257">Otevřít *`ExpenseItHome.xaml.vb`* *`ExpenseItHome.xaml.cs`* nebo .</span><span class="sxs-lookup"><span data-stu-id="49aec-257">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

3. <span data-ttu-id="49aec-258">Přidejte do třídy následující kód a `ExpenseItHome` přidejte obslužnou rutinu události kliknutí na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="49aec-258">Add the following code to the `ExpenseItHome` class to add a button click event handler.</span></span> <span data-ttu-id="49aec-259">Obslužná rutina události otevře stránku **ExpenseReportPage.**</span><span class="sxs-lookup"><span data-stu-id="49aec-259">The event handler opens the **ExpenseReportPage** page.</span></span>

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a><span data-ttu-id="49aec-260">Vytvoření ui pro ExpenseReportPage</span><span class="sxs-lookup"><span data-stu-id="49aec-260">Create the UI for ExpenseReportPage</span></span>

<span data-ttu-id="49aec-261">*ExpenseReportPage.xaml* zobrazí vyúčtování výdajů pro osobu, **`ExpenseItHome`** která je vybrána na stránce.</span><span class="sxs-lookup"><span data-stu-id="49aec-261">*ExpenseReportPage.xaml* displays the expense report for the person that's selected on the **`ExpenseItHome`** page.</span></span> <span data-ttu-id="49aec-262">V této části vytvoříte ui pro **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="49aec-262">In this section, you'll create the UI for **ExpenseReportPage**.</span></span> <span data-ttu-id="49aec-263">Do různých prvků uživatelského rozhraní také přidáte barvy pozadí a výplně.</span><span class="sxs-lookup"><span data-stu-id="49aec-263">You'll also add background and fill colors to the various UI elements.</span></span>

1. <span data-ttu-id="49aec-264">Otevřete *soubor ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="49aec-264">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="49aec-265">Mezi značky <xref:System.Windows.Controls.Grid> přidejte následující xaml:</span><span class="sxs-lookup"><span data-stu-id="49aec-265">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags:</span></span>

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    <span data-ttu-id="49aec-266">Toto ui *`ExpenseItHome.xaml`* je podobné , s výjimkou <xref:System.Windows.Controls.DataGrid>data sestavy je zobrazena v .</span><span class="sxs-lookup"><span data-stu-id="49aec-266">This UI is similar to *`ExpenseItHome.xaml`*, except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span>

3. <span data-ttu-id="49aec-267">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="49aec-267">Build and run the application.</span></span>

4. <span data-ttu-id="49aec-268">Vyberte tlačítko **Zobrazit.**</span><span class="sxs-lookup"><span data-stu-id="49aec-268">Select the **View** button.</span></span>

    <span data-ttu-id="49aec-269">Zobrazí se stránka vyúčtování výdajů.</span><span class="sxs-lookup"><span data-stu-id="49aec-269">The expense report page appears.</span></span> <span data-ttu-id="49aec-270">Všimněte si také, že je povoleno navigační tlačítko Zpět.</span><span class="sxs-lookup"><span data-stu-id="49aec-270">Also notice that the back navigation button is enabled.</span></span>

<span data-ttu-id="49aec-271">Následující obrázek znázorňuje prvky uživatelského rozhraní přidané do *souboru ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="49aec-271">The following illustration shows the UI elements added to *ExpenseReportPage.xaml*.</span></span>

![Ukázkový snímek obrazovky zobrazující právě vytvořené rozhraní pro expensereportpage.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a><span data-ttu-id="49aec-273">Ovládací prvky stylu</span><span class="sxs-lookup"><span data-stu-id="49aec-273">Style controls</span></span>

<span data-ttu-id="49aec-274">Vzhled různých prvků je často stejný pro všechny prvky stejného typu v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="49aec-274">The appearance of various elements is often the same for all elements of the same type in a UI.</span></span> <span data-ttu-id="49aec-275">Uživatelské rozhraní používá [styly](../controls/styling-and-templating.md) k opakovanému použití vzhledu ve více prvcích.</span><span class="sxs-lookup"><span data-stu-id="49aec-275">UI uses [styles](../controls/styling-and-templating.md) to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="49aec-276">Opětovná použitelnost stylů pomáhá zjednodušit vytváření a správu XAML.</span><span class="sxs-lookup"><span data-stu-id="49aec-276">The reusability of styles helps to simplify XAML creation and management.</span></span> <span data-ttu-id="49aec-277">Tato část nahrazuje atributy za prvek, které byly definovány v předchozích krocích, styly.</span><span class="sxs-lookup"><span data-stu-id="49aec-277">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span>

1. <span data-ttu-id="49aec-278">Otevřete *soubor Application.xaml* nebo *App.xaml*.</span><span class="sxs-lookup"><span data-stu-id="49aec-278">Open *Application.xaml* or *App.xaml*.</span></span>

2. <span data-ttu-id="49aec-279">Mezi značky <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> přidejte následující xaml:</span><span class="sxs-lookup"><span data-stu-id="49aec-279">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    <span data-ttu-id="49aec-280">Tento XAML přidává následující styly:</span><span class="sxs-lookup"><span data-stu-id="49aec-280">This XAML adds the following styles:</span></span>

    - <span data-ttu-id="49aec-281">`headerTextStyle`: Formátování názvu <xref:System.Windows.Controls.Label>stránky .</span><span class="sxs-lookup"><span data-stu-id="49aec-281">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="49aec-282">`labelStyle`: Formátování <xref:System.Windows.Controls.Label> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="49aec-282">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span>

    - <span data-ttu-id="49aec-283">`columnHeaderStyle`: Formátování <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span><span class="sxs-lookup"><span data-stu-id="49aec-283">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span>

    - <span data-ttu-id="49aec-284">`listHeaderStyle`: Formátování ovládacích <xref:System.Windows.Controls.Border> prvků záhlaví seznamu.</span><span class="sxs-lookup"><span data-stu-id="49aec-284">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span>

    - <span data-ttu-id="49aec-285">`listHeaderTextStyle`: Formátování záhlaví <xref:System.Windows.Controls.Label>seznamu .</span><span class="sxs-lookup"><span data-stu-id="49aec-285">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="49aec-286">`buttonStyle`: Formátování <xref:System.Windows.Controls.Button> zapnuté `ExpenseItHome.xaml`funkce .</span><span class="sxs-lookup"><span data-stu-id="49aec-286">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on `ExpenseItHome.xaml`.</span></span>

    <span data-ttu-id="49aec-287">Všimněte si, že styly <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> jsou prostředky a podřízené prvku vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="49aec-287">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="49aec-288">V tomto umístění jsou styly použity na všechny prvky v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="49aec-288">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="49aec-289">Příklad použití prostředků v aplikaci .NET najdete v tématu [Použití prostředků aplikace](../advanced/how-to-use-application-resources.md).</span><span class="sxs-lookup"><span data-stu-id="49aec-289">For an example of using resources in a .NET app, see [Use Application Resources](../advanced/how-to-use-application-resources.md).</span></span>

3. <span data-ttu-id="49aec-290">V *`ExpenseItHome.xaml`*, nahradit <xref:System.Windows.Controls.Grid> vše mezi prvky s následujícími XAML:</span><span class="sxs-lookup"><span data-stu-id="49aec-290">In *`ExpenseItHome.xaml`*, replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    <span data-ttu-id="49aec-291">Vlastnosti, <xref:System.Windows.VerticalAlignment> jako <xref:System.Windows.Media.FontFamily> je například a které definují vzhled každého ovládacího prvku, jsou odebrány a nahrazeny použitím stylů.</span><span class="sxs-lookup"><span data-stu-id="49aec-291">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="49aec-292">Například `headerTextStyle` je použita na "Zobrazit <xref:System.Windows.Controls.Label>vyúčtování výdajů" .</span><span class="sxs-lookup"><span data-stu-id="49aec-292">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span>

4. <span data-ttu-id="49aec-293">Otevřete *soubor ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="49aec-293">Open *ExpenseReportPage.xaml*.</span></span>

5. <span data-ttu-id="49aec-294">Nahraďte <xref:System.Windows.Controls.Grid> vše mezi prvky následujícím XAML:</span><span class="sxs-lookup"><span data-stu-id="49aec-294">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    <span data-ttu-id="49aec-295">Tento XAML přidává <xref:System.Windows.Controls.Label> styly a <xref:System.Windows.Controls.Border> prvky.</span><span class="sxs-lookup"><span data-stu-id="49aec-295">This XAML adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span>

6. <span data-ttu-id="49aec-296">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="49aec-296">Build and run the application.</span></span> <span data-ttu-id="49aec-297">Vzhled okna je stejný jako dříve.</span><span class="sxs-lookup"><span data-stu-id="49aec-297">The window appearance is the same as previously.</span></span>

    ![ExpenseIt ukázkový snímek obrazovky se stejným vzhledem jako v poslední části.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. <span data-ttu-id="49aec-299">Zavřete aplikaci a vraťte se do sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="49aec-299">Close the application to return to Visual Studio.</span></span>

## <a name="bind-data-to-a-control"></a><span data-ttu-id="49aec-300">Vazba dat s ovládacím prvkem</span><span class="sxs-lookup"><span data-stu-id="49aec-300">Bind data to a control</span></span>

<span data-ttu-id="49aec-301">V této části vytvoříte data XML, která jsou vázána na různé ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="49aec-301">In this section, you'll create the XML data that is bound to various controls.</span></span>

1. <span data-ttu-id="49aec-302">V *`ExpenseItHome.xaml`* aplikaci <xref:System.Windows.Controls.Grid> za otevření elementu přidejte následující <xref:System.Windows.Data.XmlDataProvider> xaml a vytvořte tak, že obsahuje data pro každou osobu:</span><span class="sxs-lookup"><span data-stu-id="49aec-302">In *`ExpenseItHome.xaml`*, after the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person:</span></span>

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    <span data-ttu-id="49aec-303">Data jsou vytvořena <xref:System.Windows.Controls.Grid> jako prostředek.</span><span class="sxs-lookup"><span data-stu-id="49aec-303">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="49aec-304">Za normálních okolností by tato data byla načtena jako soubor, ale pro jednoduchost jsou data přidána vložena.</span><span class="sxs-lookup"><span data-stu-id="49aec-304">Normally this data would be loaded as a file, but for simplicity the data is added inline.</span></span>

2. <span data-ttu-id="49aec-305">V `<Grid.Resources>` rámci prvku přidejte následující `<xref:System.Windows.DataTemplate>` prvek, který definuje, <xref:System.Windows.Controls.ListBox>jak zobrazit `<XmlDataProvider>` data v , za element:</span><span class="sxs-lookup"><span data-stu-id="49aec-305">Within the `<Grid.Resources>` element, add the following `<xref:System.Windows.DataTemplate>` element, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>, after the `<XmlDataProvider>` element:</span></span>

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    <span data-ttu-id="49aec-306">Další informace o šablonách dat naleznete v [tématu Přehled šablon dat](../data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="49aec-306">For more information about data templates, see [Data templating overview](../data/data-templating-overview.md).</span></span>

3. <span data-ttu-id="49aec-307">Nahraďte <xref:System.Windows.Controls.ListBox> existující pomocí následujícího XAML:</span><span class="sxs-lookup"><span data-stu-id="49aec-307">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    <span data-ttu-id="49aec-308">Tento XAML váže <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnosti <xref:System.Windows.Controls.ListBox> zdroje dat a použije šablonu <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>dat jako .</span><span class="sxs-lookup"><span data-stu-id="49aec-308">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span>

## <a name="connect-data-to-controls"></a><span data-ttu-id="49aec-309">Připojení dat k ovládacím prvkům</span><span class="sxs-lookup"><span data-stu-id="49aec-309">Connect data to controls</span></span>

<span data-ttu-id="49aec-310">Dále přidáte kód k načtení názvu, který je **`ExpenseItHome`** vybrán na stránce a předat jej konstruktoru **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="49aec-310">Next, you'll add code to retrieve the name that's selected on the **`ExpenseItHome`** page and pass it to the constructor of **ExpenseReportPage**.</span></span> <span data-ttu-id="49aec-311">**ExpenseReportPage** nastaví svůj kontext dat s předanou položkou, což je to, co ovládací prvky definované v *ExpenseReportPage.xaml* vázat.</span><span class="sxs-lookup"><span data-stu-id="49aec-311">**ExpenseReportPage** sets its data context with the passed item, which is what the controls defined in *ExpenseReportPage.xaml* bind to.</span></span>

1. <span data-ttu-id="49aec-312">Otevřete *soubor ExpenseReportPage.xaml.vb* nebo *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="49aec-312">Open *ExpenseReportPage.xaml.vb* or *ExpenseReportPage.xaml.cs*.</span></span>

2. <span data-ttu-id="49aec-313">Přidejte konstruktor, který převezme objekt, takže můžete předat data vyúčtování výdajů vybrané osoby.</span><span class="sxs-lookup"><span data-stu-id="49aec-313">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. <span data-ttu-id="49aec-314">Otevřít *`ExpenseItHome.xaml.vb`* *`ExpenseItHome.xaml.cs`* nebo .</span><span class="sxs-lookup"><span data-stu-id="49aec-314">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

4. <span data-ttu-id="49aec-315">Změňte <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužnou rutinu události tak, aby volala nového konstruktoru, který předává data vyúčtování výdajů vybrané osoby.</span><span class="sxs-lookup"><span data-stu-id="49aec-315">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a><span data-ttu-id="49aec-316">Data stylu se šablonami dat</span><span class="sxs-lookup"><span data-stu-id="49aec-316">Style data with data templates</span></span>

<span data-ttu-id="49aec-317">V této části aktualizujete uživatelské tlačítko pro každou položku v seznamech vázaných na data pomocí šablon dat.</span><span class="sxs-lookup"><span data-stu-id="49aec-317">In this section, you'll update the UI for each item in the data-bound lists by using data templates.</span></span>

1. <span data-ttu-id="49aec-318">Otevřete *soubor ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="49aec-318">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="49aec-319">Svázat obsah "Název" a "Oddělení" <xref:System.Windows.Controls.Label> prvky příslušné vlastnosti zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="49aec-319">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="49aec-320">Další informace o datové vazbě naleznete v [tématu Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="49aec-320">For more information about data binding, see [Data binding overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. <span data-ttu-id="49aec-321">Za otevírací <xref:System.Windows.Controls.Grid> prvek přidejte následující šablony dat, které definují, jak zobrazit data vyúčtování výdajů:</span><span class="sxs-lookup"><span data-stu-id="49aec-321">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data:</span></span>

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. <span data-ttu-id="49aec-322">Nahraďte <xref:System.Windows.Controls.DataGridTemplateColumn> prvky <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Controls.DataGridTextColumn> pod elementem a aplikujte na ně šablony.</span><span class="sxs-lookup"><span data-stu-id="49aec-322">Replace the <xref:System.Windows.Controls.DataGridTextColumn> elements with <xref:System.Windows.Controls.DataGridTemplateColumn> under the <xref:System.Windows.Controls.DataGrid> element and apply the templates to them.</span></span>

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. <span data-ttu-id="49aec-323">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="49aec-323">Build and run the application.</span></span>

6. <span data-ttu-id="49aec-324">Vyberte osobu a pak vyberte tlačítko **Zobrazit.**</span><span class="sxs-lookup"><span data-stu-id="49aec-324">Select a person and then select the **View** button.</span></span>

<span data-ttu-id="49aec-325">Následující obrázek znázorňuje `ExpenseIt` obě stránky aplikace s použitými ovládacími prvky, rozložením, styly, datovou vazbou a šablonami dat:</span><span class="sxs-lookup"><span data-stu-id="49aec-325">The following illustration shows both pages of the `ExpenseIt` application with controls, layout, styles, data binding, and data templates applied:</span></span>

![Obě stránky aplikace zobrazující seznam jmen a vyúčtování výdajů.](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> <span data-ttu-id="49aec-327">Tato ukázka ukazuje konkrétní funkci WPF a nedodržuje všechny osvědčené postupy pro věci, jako je zabezpečení, lokalizace a usnadnění přístupu.</span><span class="sxs-lookup"><span data-stu-id="49aec-327">This sample demonstrates a specific feature of WPF and doesn't follow all best practices for things like security, localization, and accessibility.</span></span> <span data-ttu-id="49aec-328">Komplexní pokrytí WPF a osvědčených postupů pro vývoj aplikací .NET najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="49aec-328">For comprehensive coverage of WPF and the .NET app development best practices, see the following topics:</span></span>
>
> - [<span data-ttu-id="49aec-329">Usnadnění</span><span class="sxs-lookup"><span data-stu-id="49aec-329">Accessibility</span></span>](../../ui-automation/accessibility-best-practices.md)
> - [<span data-ttu-id="49aec-330">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="49aec-330">Security</span></span>](../security-wpf.md)
> - [<span data-ttu-id="49aec-331">WPF globalizace a lokalizace</span><span class="sxs-lookup"><span data-stu-id="49aec-331">WPF globalization and localization</span></span>](../advanced/wpf-globalization-and-localization-overview.md)
> - [<span data-ttu-id="49aec-332">WPF výkon</span><span class="sxs-lookup"><span data-stu-id="49aec-332">WPF performance</span></span>](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a><span data-ttu-id="49aec-333">Další kroky</span><span class="sxs-lookup"><span data-stu-id="49aec-333">Next steps</span></span>

<span data-ttu-id="49aec-334">V tomto návodu jste se naučili řadu technik pro vytvoření ui pomocí Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="49aec-334">In this walkthrough you learned a number of techniques for creating a UI using Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="49aec-335">Nyní byste měli mít základní znalosti o stavebních blocích aplikace .NET vázané na data.</span><span class="sxs-lookup"><span data-stu-id="49aec-335">You should now have a basic understanding of the building blocks of a data-bound .NET app.</span></span> <span data-ttu-id="49aec-336">Další informace o architektuře WPF a programovacích modelech naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="49aec-336">For more information about the WPF architecture and programming models, see the following topics:</span></span>

- [<span data-ttu-id="49aec-337">Architektura WPF</span><span class="sxs-lookup"><span data-stu-id="49aec-337">WPF architecture</span></span>](../advanced/wpf-architecture.md)
- [<span data-ttu-id="49aec-338">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="49aec-338">XAML overview (WPF)</span></span>](../advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="49aec-339">Přehled vlastností závislostí</span><span class="sxs-lookup"><span data-stu-id="49aec-339">Dependency properties overview</span></span>](../advanced/dependency-properties-overview.md)
- [<span data-ttu-id="49aec-340">Rozložení</span><span class="sxs-lookup"><span data-stu-id="49aec-340">Layout</span></span>](../advanced/layout.md)

<span data-ttu-id="49aec-341">Další informace o vytváření aplikací naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="49aec-341">For more information about creating applications, see the following topics:</span></span>

- [<span data-ttu-id="49aec-342">Vývoj aplikací</span><span class="sxs-lookup"><span data-stu-id="49aec-342">Application development</span></span>](../app-development/index.md)
- [<span data-ttu-id="49aec-343">Ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="49aec-343">Controls</span></span>](../controls/index.md)
- [<span data-ttu-id="49aec-344">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="49aec-344">Data binding overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="49aec-345">Grafika a multimédia</span><span class="sxs-lookup"><span data-stu-id="49aec-345">Graphics and multimedia</span></span>](../graphics-multimedia/index.md)
- [<span data-ttu-id="49aec-346">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="49aec-346">Documents in WPF</span></span>](../advanced/documents-in-wpf.md)

## <a name="see-also"></a><span data-ttu-id="49aec-347">Viz také</span><span class="sxs-lookup"><span data-stu-id="49aec-347">See also</span></span>

- [<span data-ttu-id="49aec-348">Panely – přehled</span><span class="sxs-lookup"><span data-stu-id="49aec-348">Panels overview</span></span>](../controls/panels-overview.md)
- [<span data-ttu-id="49aec-349">Přehled šablon ování dat</span><span class="sxs-lookup"><span data-stu-id="49aec-349">Data templating overview</span></span>](../data/data-templating-overview.md)
- [<span data-ttu-id="49aec-350">Vytvoření aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="49aec-350">Build a WPF application</span></span>](../app-development/building-a-wpf-application-wpf.md)
- [<span data-ttu-id="49aec-351">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="49aec-351">Styles and templates</span></span>](../controls/styles-and-templates.md)
