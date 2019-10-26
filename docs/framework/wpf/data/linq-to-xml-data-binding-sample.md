---
title: Příklad datové vazby LINQ to XML
ms.date: 10/22/2019
ms.topic: sample
helpviewer_keywords:
- linq to xml data binding sample
ms.openlocfilehash: aac814e4768a863a93e69e34cd18c941a9b35c89
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920935"
---
# <a name="linq-to-xml-data-binding-sample"></a><span data-ttu-id="8e9bf-102">Ukázka datové vazby LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="8e9bf-102">LINQ to XML data binding sample</span></span>

<span data-ttu-id="8e9bf-103">Tento článek popisuje ukázku příkladu LinqToXmlDataBinding, aplikaci Windows Presentation Foundation (WPF), která váže součásti uživatelského rozhraní k vloženému zdroji dat XML.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-103">This article describes the LinqToXmlDataBinding sample, a Windows Presentation Foundation (WPF) app that binds user interface components to an embedded XML data source.</span></span>

## <a name="overview"></a><span data-ttu-id="8e9bf-104">Přehled</span><span class="sxs-lookup"><span data-stu-id="8e9bf-104">Overview</span></span>

<span data-ttu-id="8e9bf-105">Ukázka příkladu LinqToXmlDataBinding je aplikace Windows Presentation Foundation (WPF), která obsahuje C# zdrojové soubory a XAML.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-105">The LinqToXmlDataBinding sample is a Windows Presentation Foundation (WPF) app that contains C# and XAML source files.</span></span> <span data-ttu-id="8e9bf-106">Vložený dokument XML definuje seznam knih.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-106">An embedded XML document defines a list of books.</span></span> <span data-ttu-id="8e9bf-107">Aplikace umožňuje uživateli zobrazovat, přidávat, odstraňovat a upravovat položky knihy.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-107">The app enables the user to view, add, delete, and edit the book entries.</span></span>

<span data-ttu-id="8e9bf-108">Existují dva primární zdrojové soubory:</span><span class="sxs-lookup"><span data-stu-id="8e9bf-108">There are two primary source files:</span></span>

- <span data-ttu-id="8e9bf-109">[Zdrojový kód L2DBForm. XAML](l2dbform-xaml-source-code.md) obsahuje kód deklarace XAML pro uživatelské rozhraní (UI) hlavního okna.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-109">[L2DBForm.xaml](l2dbform-xaml-source-code.md) contains the XAML declaration code for the user interface (UI) of the main window.</span></span> <span data-ttu-id="8e9bf-110">Obsahuje také oddíl prostředků okna definující poskytovatele dat a vložený dokument XML pro výpisy knih.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-110">It also contains a window resource section that defines a data provider and an embedded XML document for the book listings.</span></span>

- <span data-ttu-id="8e9bf-111">[L2DBForm.XAML.cs](l2dbform-xaml-cs-source-code.md) obsahuje metody inicializace a zpracování událostí přidružené k uživatelskému rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-111">[L2DBForm.xaml.cs](l2dbform-xaml-cs-source-code.md) contains the initialization and event-handling methods associated with the UI.</span></span>

<span data-ttu-id="8e9bf-112">Hlavní okno je rozdělené do následujících čtyř oddílů vertikálního uživatelského rozhraní:</span><span class="sxs-lookup"><span data-stu-id="8e9bf-112">The main window is divided into the following four vertical UI sections:</span></span>

- <span data-ttu-id="8e9bf-113">**XML** zobrazí nezpracovaný zdroj XML se seznamem vložených knih.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-113">**XML** displays the raw XML source of the embedded book listing.</span></span>

- <span data-ttu-id="8e9bf-114">**Seznam knih** zobrazuje položky knihy jako standardní text a umožňuje uživateli vybrat a odstranit jednotlivé položky.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-114">**Book List** displays the book entries as standard text and enables the user to select and delete individual entries.</span></span>

- <span data-ttu-id="8e9bf-115">**Možnost upravit vybranou knihu** umožňuje uživateli upravovat hodnoty spojené s aktuálně vybranou položkou knihy.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-115">**Edit Selected Book** enables the user to edit the values associated with the currently selected book entry.</span></span>

- <span data-ttu-id="8e9bf-116">Možnost **Přidat novou knihu** umožňuje vytvořit novou položku knihy na základě hodnot zadaných uživatelem.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-116">**Add New Book** enables the creation of a new book entry based on values entered by the user.</span></span>

## <a name="run-the-sample"></a><span data-ttu-id="8e9bf-117">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="8e9bf-117">Run the sample</span></span>

<span data-ttu-id="8e9bf-118">V této části se dozvíte, jak vytvořit a sestavit projekt příkladu LinqToXmlDataBinding v aplikaci Visual Studio a jak spustit výslednou aplikaci v příkladu LinqToXmlDataBinding Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="8e9bf-118">This section shows how to create and build the LinqToXmlDataBinding project in Visual Studio, and how to run the resulting LinqToXmlDataBinding Windows Presentation Foundation (WPF) app.</span></span>

### <a name="create-the-project"></a><span data-ttu-id="8e9bf-119">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="8e9bf-119">Create the project</span></span>

1. <span data-ttu-id="8e9bf-120">Otevřete Visual Studio a vytvořte C# **aplikaci WPF** s názvem **příkladu LinqToXmlDataBinding**.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-120">Open Visual Studio and create a C# **WPF App** named **LinqToXmlDataBinding**.</span></span>

   <span data-ttu-id="8e9bf-121">Projekt by měl cílit na .NET Framework 3,5 (nebo novější).</span><span class="sxs-lookup"><span data-stu-id="8e9bf-121">The project should target the .NET Framework 3.5 (or later).</span></span>

1. <span data-ttu-id="8e9bf-122">Pokud ještě není k dispozici, přidejte odkazy na projekt pro následující sestavení .NET:</span><span class="sxs-lookup"><span data-stu-id="8e9bf-122">If not already present, add project references for the following .NET assemblies:</span></span>

    - <span data-ttu-id="8e9bf-123">System.Data</span><span class="sxs-lookup"><span data-stu-id="8e9bf-123">System.Data</span></span>
    - <span data-ttu-id="8e9bf-124">System. data. DataSetExtensions</span><span class="sxs-lookup"><span data-stu-id="8e9bf-124">System.Data.DataSetExtensions</span></span>
    - <span data-ttu-id="8e9bf-125">System.Xml</span><span class="sxs-lookup"><span data-stu-id="8e9bf-125">System.Xml</span></span>
    - <span data-ttu-id="8e9bf-126">System.Xml</span><span class="sxs-lookup"><span data-stu-id="8e9bf-126">System.Xml</span></span>

1. <span data-ttu-id="8e9bf-127">Sestavte řešení stisknutím **kombinace kláves Ctrl** +**SHIFT** +**B**a pak ho spusťte stisknutím klávesy **F5**.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-127">Build the solution by pressing **Ctrl**+**Shift**+**B**, then run it by pressing **F5**.</span></span>

   <span data-ttu-id="8e9bf-128">Projekt by se měl kompilovat bez chyb a spustit jako obecná aplikace WPF.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-128">The project should compile without errors and run as a generic WPF application.</span></span>

### <a name="add-code"></a><span data-ttu-id="8e9bf-129">Přidat kód</span><span class="sxs-lookup"><span data-stu-id="8e9bf-129">Add code</span></span>

1. <span data-ttu-id="8e9bf-130">V **Průzkumník řešení**přejmenujte zdrojový soubor **Window1. XAML** na **L2XDBForm. XAML**.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-130">In **Solution Explorer**, rename the source file **Window1.xaml** to **L2XDBForm.xaml**.</span></span>

   <span data-ttu-id="8e9bf-131">Závislý zdrojový soubor Window1.xaml.cs se automaticky přejmenuje na L2XDBForm.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-131">The dependent source file Window1.xaml.cs is automatically renamed to L2XDBForm.xaml.cs.</span></span>

1. <span data-ttu-id="8e9bf-132">Nahraďte zdrojový kód, který se nachází v souboru **L2XDBForm. XAML** , pomocí [zdrojového kódu zdrojový kód L2DBForm. XAML](l2dbform-xaml-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="8e9bf-132">Replace the source code found in the file **L2XDBForm.xaml** with the [L2DBForm.xaml source code](l2dbform-xaml-source-code.md).</span></span> <span data-ttu-id="8e9bf-133">Pro práci s tímto souborem použijte zobrazení zdroje XAML.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-133">Use the XAML source view to work with this file.</span></span>

1. <span data-ttu-id="8e9bf-134">Podobně nahraďte zdroj v **L2XDBForm.XAML.cs** [zdrojovým kódem L2DBForm.XAML.cs](l2dbform-xaml-cs-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="8e9bf-134">Similarly, replace the source in **L2XDBForm.xaml.cs** with the [L2DBForm.xaml.cs source code](l2dbform-xaml-cs-source-code.md).</span></span>

1. <span data-ttu-id="8e9bf-135">V souboru **App. XAML**nahraďte všechny výskyty řetězce **Window1. XAML** pomocí **L2XDBForm. XAML**.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-135">In the file **App.xaml**, replace all occurrences of the string **Window1.xaml** with **L2XDBForm.xaml**.</span></span>

1. <span data-ttu-id="8e9bf-136">Sestavte řešení stisknutím **kombinace kláves Ctrl** +**SHIFT** +**B**.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-136">Build the solution by pressing **Ctrl**+**Shift**+**B**.</span></span>

### <a name="run-the-app"></a><span data-ttu-id="8e9bf-137">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="8e9bf-137">Run the app</span></span>

<span data-ttu-id="8e9bf-138">Aplikace příkladu LinqToXmlDataBinding umožňuje uživateli zobrazit a manipulovat se seznamem knih, které jsou uloženy jako vložený prvek XML.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-138">The LinqToXmlDataBinding app enables the user to view and manipulate a list of books that's stored as an embedded XML element.</span></span> <span data-ttu-id="8e9bf-139">Spusťte aplikaci stisknutím klávesy **F5** (Spustit ladění) nebo **kombinací kláves CTRL**+**F5** (spustit bez ladění).</span><span class="sxs-lookup"><span data-stu-id="8e9bf-139">Run the app by pressing **F5** (Start Debugging) or **Ctrl**+**F5** (Start Without Debugging).</span></span>

<span data-ttu-id="8e9bf-140">Zobrazí se okno programu s názvem **datová vazba WPF pomocí LINQ to XML** .</span><span class="sxs-lookup"><span data-stu-id="8e9bf-140">A program window with the title **WPF Data Binding using LINQ to XML** appears.</span></span>

<span data-ttu-id="8e9bf-141">V horní části uživatelského rozhraní se zobrazuje nezpracovaný **soubor XML** , který představuje seznam knih.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-141">The top section of the UI displays the raw **XML** that represents the book list.</span></span> <span data-ttu-id="8e9bf-142">Zobrazuje se pomocí ovládacího prvku WPF <xref:System.Windows.Controls.TextBlock>, který neumožňuje interakci přes myš ani klávesnici.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-142">It is displayed using a WPF <xref:System.Windows.Controls.TextBlock> control, which does not enable interaction through the mouse or keyboard.</span></span>

<span data-ttu-id="8e9bf-143">Druhá svislá sekce, označená jako **seznam knihy**, zobrazuje knihy jako seznam seřazený jako prostý text.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-143">The second vertical section, labeled **Book List**, displays the books as a plain text ordered list.</span></span> <span data-ttu-id="8e9bf-144">Používá ovládací prvek <xref:System.Windows.Controls.ListBox>, který umožňuje výběr i přes myš nebo klávesnici.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-144">It uses a <xref:System.Windows.Controls.ListBox> control that enables selection though the mouse or keyboard.</span></span>

### <a name="add-and-delete-books"></a><span data-ttu-id="8e9bf-145">Přidávání a odstraňování knih</span><span class="sxs-lookup"><span data-stu-id="8e9bf-145">Add and delete books</span></span>

<span data-ttu-id="8e9bf-146">Pokud chcete do seznamu přidat novou knihu, zadejte hodnoty do pole **ID** a **hodnota** <xref:System.Windows.Controls.TextBox> ovládací prvky v poslední části, **přidejte novou knihu**a pak vyberte **Přidat knihu**.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-146">To add a new book to the list, enter values into the **ID** and **Value** <xref:System.Windows.Controls.TextBox> controls in the last section, **Add New Book**, and then select **Add Book**.</span></span> <span data-ttu-id="8e9bf-147">Kniha se připojí k seznamu v knize i ve výpisech XML.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-147">The book is appended to the list in both the book and XML listings.</span></span> <span data-ttu-id="8e9bf-148">Tento program neověřuje vstupní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-148">This program does not validate input values.</span></span>

<span data-ttu-id="8e9bf-149">Pokud chcete odstranit existující knihu ze seznamu, vyberte ji v části **seznam knih** a pak vyberte **Odebrat vybranou knihu**.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-149">To delete an existing book from the list, select it in the **Book List** section, and then select **Remove Selected Book**.</span></span> <span data-ttu-id="8e9bf-150">Položka knihy se odebere z knihy i z nezpracovaného zdrojového seznamu XML.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-150">The book entry is removed from both the book and the raw XML source listings.</span></span>

### <a name="edit-a-book-entry"></a><span data-ttu-id="8e9bf-151">Úprava položky knihy</span><span class="sxs-lookup"><span data-stu-id="8e9bf-151">Edit a book entry</span></span>

1. <span data-ttu-id="8e9bf-152">V části seznamu druhých **knih** vyberte položku kniha.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-152">Select the book entry in the second **Book List** section.</span></span>

   <span data-ttu-id="8e9bf-153">Aktuální hodnoty se zobrazí v oddílu **Upravit vybranou knihu** .</span><span class="sxs-lookup"><span data-stu-id="8e9bf-153">Its current values are displayed in the **Edit Selected Book** section.</span></span>

1. <span data-ttu-id="8e9bf-154">Upravte hodnoty pomocí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-154">Edit the values using the keyboard.</span></span> <span data-ttu-id="8e9bf-155">Jakmile <xref:System.Windows.Controls.TextBox> ovládací prvek ztratí fokus, změny se automaticky rozšíří do seznamů zdrojů a knih XML.</span><span class="sxs-lookup"><span data-stu-id="8e9bf-155">As soon as either <xref:System.Windows.Controls.TextBox> control loses focus, changes are automatically propagated to the XML source and book listings.</span></span>
