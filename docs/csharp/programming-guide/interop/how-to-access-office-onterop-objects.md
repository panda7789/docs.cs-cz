---
title: Přístup k objektům interop sady Office – Průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- optional parameters [C#], Office programming
- named and optional arguments [C#], Office programming
- dynamic [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
- Office programming [C#]
ms.assetid: 041b25c2-3512-4e0f-a4ea-ceb2999e4d5e
ms.openlocfilehash: b5d2da011ec6318c8b07f1eb4d383a4d56488239
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75700832"
---
# <a name="how-to-access-office-interop-objects-c-programming-guide"></a><span data-ttu-id="fdf72-102">Přístup k objektům interop sady Office (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="fdf72-102">How to access Office interop objects (C# Programming Guide)</span></span>

<span data-ttu-id="fdf72-103">C# má funkce, které zjednodušují přístup k objektům rozhraní API sady Office.</span><span class="sxs-lookup"><span data-stu-id="fdf72-103">C# has features that simplify access to Office API objects.</span></span> <span data-ttu-id="fdf72-104">Nové funkce zahrnují pojmenované a volitelné argumenty, nový typ s názvem `dynamic`a schopnost předat argumenty referenčním parametrům v metodách COM, jako by se jednalo o parametry hodnoty.</span><span class="sxs-lookup"><span data-stu-id="fdf72-104">The new features include named and optional arguments, a new type called `dynamic`, and the ability to pass arguments to reference parameters in COM methods as if they were value parameters.</span></span>

<span data-ttu-id="fdf72-105">V tomto tématu budete používat nové funkce k napsání kódu, který vytvoří a zobrazí list aplikace Microsoft Office Excel.</span><span class="sxs-lookup"><span data-stu-id="fdf72-105">In this topic you will use the new features to write code that creates and displays a Microsoft Office Excel worksheet.</span></span> <span data-ttu-id="fdf72-106">Poté napíšete kód pro přidání dokumentu aplikace Office Word, který obsahuje ikonu propojenou s listem aplikace Excel.</span><span class="sxs-lookup"><span data-stu-id="fdf72-106">You will then write code to add an Office Word document that contains an icon that is linked to the Excel worksheet.</span></span>

<span data-ttu-id="fdf72-107">Chcete-li tento návod dokončit, musíte mít v počítači nainstalovanou aplikaci Microsoft Office Excel 2007 a Microsoft Office Word 2007 nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="fdf72-107">To complete this walkthrough, you must have Microsoft Office Excel 2007 and Microsoft Office Word 2007, or later versions, installed on your computer.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a><span data-ttu-id="fdf72-108">Vytvoření nové konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="fdf72-108">To create a new console application</span></span>

1. <span data-ttu-id="fdf72-109">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fdf72-109">Start Visual Studio.</span></span>

2. <span data-ttu-id="fdf72-110">V nabídce **Soubor** přejděte na **Nový**a potom klepněte na **položku Project**.</span><span class="sxs-lookup"><span data-stu-id="fdf72-110">On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="fdf72-111">Zobrazí se dialogové okno **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="fdf72-111">The **New Project** dialog box appears.</span></span>

3. <span data-ttu-id="fdf72-112">V podokně **Nainstalované šablony** rozbalte **položku Visual C#** a klepněte na tlačítko **Windows**.</span><span class="sxs-lookup"><span data-stu-id="fdf72-112">In the **Installed Templates** pane, expand **Visual C#**, and then click **Windows**.</span></span>

4. <span data-ttu-id="fdf72-113">Podívejte se na začátek dialogového okna **Nový projekt** a ujistěte se, že **rozhraní .NET Framework 4** (nebo novější verze) je vybránjako cílová architektura.</span><span class="sxs-lookup"><span data-stu-id="fdf72-113">Look at the top of the **New Project** dialog box to make sure that **.NET Framework 4** (or later version) is selected as a target framework.</span></span>

5. <span data-ttu-id="fdf72-114">V podokně **Šablony** klepněte na položku **Konzolová aplikace**.</span><span class="sxs-lookup"><span data-stu-id="fdf72-114">In the **Templates** pane, click **Console Application**.</span></span>

6. <span data-ttu-id="fdf72-115">Do pole **Název** zadejte název projektu.</span><span class="sxs-lookup"><span data-stu-id="fdf72-115">Type a name for your project in the **Name** field.</span></span>

7. <span data-ttu-id="fdf72-116">Klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="fdf72-116">Click **OK**.</span></span>

     <span data-ttu-id="fdf72-117">Nový projekt se zobrazí v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="fdf72-117">The new project appears in **Solution Explorer**.</span></span>

## <a name="to-add-references"></a><span data-ttu-id="fdf72-118">Přidání odkazů</span><span class="sxs-lookup"><span data-stu-id="fdf72-118">To add references</span></span>

1. <span data-ttu-id="fdf72-119">V **Průzkumníku řešení**klikněte pravým tlačítkem myši na název projektu a potom klikněte na **příkaz Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="fdf72-119">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="fdf72-120">Zobrazí se dialogové okno **Přidat odkaz.**</span><span class="sxs-lookup"><span data-stu-id="fdf72-120">The **Add Reference** dialog box appears.</span></span>

2. <span data-ttu-id="fdf72-121">Na stránce **Sestavení** vyberte v seznamu **Název součásti** položku **Microsoft.Office.Interop.Word** a podržte klávesu CTRL a vyberte **položku Microsoft.Office.Interop.Excel**.</span><span class="sxs-lookup"><span data-stu-id="fdf72-121">On the **Assemblies**  page, select **Microsoft.Office.Interop.Word** in the **Component Name** list, and then hold down the CTRL key and select **Microsoft.Office.Interop.Excel**.</span></span>  <span data-ttu-id="fdf72-122">Pokud sestavy nevidíte, bude pravděpodobně nutné zajistit jejich instalaci a zobrazení.</span><span class="sxs-lookup"><span data-stu-id="fdf72-122">If you do not see the assemblies, you may need to ensure they are installed and displayed.</span></span> <span data-ttu-id="fdf72-123">Postup: [Instalace primárních sestavení mezi opačnou operací sady Office](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies).</span><span class="sxs-lookup"><span data-stu-id="fdf72-123">See [How to: Install Office Primary Interop Assemblies](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies).</span></span>

3. <span data-ttu-id="fdf72-124">Klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="fdf72-124">Click **OK**.</span></span>

## <a name="to-add-necessary-using-directives"></a><span data-ttu-id="fdf72-125">Chcete-li přidat nezbytné pomocí směrnic</span><span class="sxs-lookup"><span data-stu-id="fdf72-125">To add necessary using directives</span></span>

1. <span data-ttu-id="fdf72-126">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na *soubor Program.cs* a potom klepněte na příkaz Zobrazit **kód**.</span><span class="sxs-lookup"><span data-stu-id="fdf72-126">In **Solution Explorer**, right-click the *Program.cs* file and then click **View Code**.</span></span>

2. <span data-ttu-id="fdf72-127">Do horní `using` části souboru kódu přidejte následující direktivy:</span><span class="sxs-lookup"><span data-stu-id="fdf72-127">Add the following `using` directives to the top of the code file:</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#1)]

## <a name="to-create-a-list-of-bank-accounts"></a><span data-ttu-id="fdf72-128">Vytvoření seznamu bankovních účtů</span><span class="sxs-lookup"><span data-stu-id="fdf72-128">To create a list of bank accounts</span></span>

1. <span data-ttu-id="fdf72-129">Vložte následující definici třídy `Program` do **Program.cs**pod třídu.</span><span class="sxs-lookup"><span data-stu-id="fdf72-129">Paste the following class definition into **Program.cs**, under the `Program` class.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#2)]

2. <span data-ttu-id="fdf72-130">Přidejte následující kód `Main` do metody `bankAccounts` a vytvořte seznam, který obsahuje dva účty.</span><span class="sxs-lookup"><span data-stu-id="fdf72-130">Add the following code to the `Main` method to create a `bankAccounts` list that contains two accounts.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#3)]

## <a name="to-declare-a-method-that-exports-account-information-to-excel"></a><span data-ttu-id="fdf72-131">Deklarování metody, která exportuje informace o účtu do aplikace Excel</span><span class="sxs-lookup"><span data-stu-id="fdf72-131">To declare a method that exports account information to Excel</span></span>

1. <span data-ttu-id="fdf72-132">Přidejte do třídy následující metodu `Program` pro nastavení listu aplikace Excel.</span><span class="sxs-lookup"><span data-stu-id="fdf72-132">Add the following method to the `Program` class to set up an Excel worksheet.</span></span>

     <span data-ttu-id="fdf72-133">Metoda <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> má volitelný parametr pro určení konkrétní šablony.</span><span class="sxs-lookup"><span data-stu-id="fdf72-133">Method <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> has an optional parameter for specifying a particular template.</span></span> <span data-ttu-id="fdf72-134">Volitelné parametry, nové v C# 4, umožňují vynechat argument pro tento parametr, pokud chcete použít výchozí hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="fdf72-134">Optional parameters, new in C# 4, enable you to omit the argument for that parameter if you want to use the parameter's default value.</span></span> <span data-ttu-id="fdf72-135">Protože v následujícím kódu není `Add` odeslán žádný argument, použije výchozí šablonu a vytvoří nový sešit.</span><span class="sxs-lookup"><span data-stu-id="fdf72-135">Because no argument is sent in the following code, `Add` uses the default template and creates a new workbook.</span></span> <span data-ttu-id="fdf72-136">Ekvivalentní příkaz v dřívějších verzích jazyka C# `ExcelApp.Workbooks.Add(Type.Missing)`vyžaduje zástupný argument: .</span><span class="sxs-lookup"><span data-stu-id="fdf72-136">The equivalent statement in earlier versions of C# requires a placeholder argument: `ExcelApp.Workbooks.Add(Type.Missing)`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#4)]

2. <span data-ttu-id="fdf72-137">Na konec přidejte následující `DisplayInExcel`kód .</span><span class="sxs-lookup"><span data-stu-id="fdf72-137">Add the following code at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="fdf72-138">Kód vloží hodnoty do prvních dvou sloupců prvního řádku listu.</span><span class="sxs-lookup"><span data-stu-id="fdf72-138">The code inserts values into the first two columns of the first row of the worksheet.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#5)]

3. <span data-ttu-id="fdf72-139">Na konec přidejte následující `DisplayInExcel`kód .</span><span class="sxs-lookup"><span data-stu-id="fdf72-139">Add the following code at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="fdf72-140">Smyčka `foreach` umístí informace ze seznamu účtů do prvních dvou sloupců po sobě jdoucích řádků listu.</span><span class="sxs-lookup"><span data-stu-id="fdf72-140">The `foreach` loop puts the information from the list of accounts into the first two columns of successive rows of the worksheet.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#7)]

4. <span data-ttu-id="fdf72-141">Přidejte následující kód na `DisplayInExcel` konci upravit šířky sloupců, aby odpovídaly obsahu.</span><span class="sxs-lookup"><span data-stu-id="fdf72-141">Add the following code at the end of `DisplayInExcel` to adjust the column widths to fit the content.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#13)]

     <span data-ttu-id="fdf72-142">Dřívější verze jazyka C# vyžadují explicitní `ExcelApp.Columns[1]` přetypování pro tyto `Object`operace, protože vrací , a `AutoFit` je metoda aplikace Excel. <xref:Microsoft.Office.Interop.Excel.Range></span><span class="sxs-lookup"><span data-stu-id="fdf72-142">Earlier versions of C# require explicit casting for these operations because `ExcelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel <xref:Microsoft.Office.Interop.Excel.Range> method.</span></span> <span data-ttu-id="fdf72-143">Následující řádky ukazují odlévání.</span><span class="sxs-lookup"><span data-stu-id="fdf72-143">The following lines show the casting.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

     <span data-ttu-id="fdf72-144">C# 4 a novější verze `Object` převádí vrácené automaticky, `dynamic` pokud je sestavení odkazováno volbou kompilátoru [-link](../../language-reference/compiler-options/link-compiler-option.md) nebo ekvivalentním ekvivalentem, pokud je vlastnost Excel **Embed Interop Types** nastavena na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="fdf72-144">C# 4, and later versions, converts the returned `Object` to `dynamic` automatically if the assembly is referenced by the [-link](../../language-reference/compiler-options/link-compiler-option.md) compiler option or, equivalently, if the Excel **Embed Interop Types** property is set to true.</span></span> <span data-ttu-id="fdf72-145">True je výchozí hodnota pro tuto vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fdf72-145">True is the default value for this property.</span></span>

## <a name="to-run-the-project"></a><span data-ttu-id="fdf72-146">Spuštění projektu</span><span class="sxs-lookup"><span data-stu-id="fdf72-146">To run the project</span></span>

1. <span data-ttu-id="fdf72-147">Na konec položky `Main`přidejte následující řádek .</span><span class="sxs-lookup"><span data-stu-id="fdf72-147">Add the following line at the end of `Main`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#8)]

2. <span data-ttu-id="fdf72-148">Stiskněte kombinaci kláves CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="fdf72-148">Press CTRL+F5.</span></span>

     <span data-ttu-id="fdf72-149">Zobrazí se list aplikace Excel, který obsahuje data z obou účtů.</span><span class="sxs-lookup"><span data-stu-id="fdf72-149">An Excel worksheet appears that contains the data from the two accounts.</span></span>

## <a name="to-add-a-word-document"></a><span data-ttu-id="fdf72-150">Přidání wordové dokumentu</span><span class="sxs-lookup"><span data-stu-id="fdf72-150">To add a Word document</span></span>

1. <span data-ttu-id="fdf72-151">Chcete-li ilustrovat další způsoby, ve kterém C# 4 a novější verze, vylepšuje programování sady Office, následující kód otevře aplikaci Word a vytvoří ikonu, která odkazuje na list aplikace Excel.</span><span class="sxs-lookup"><span data-stu-id="fdf72-151">To illustrate additional ways in which C# 4, and later versions, enhances Office programming, the following code opens a Word application and creates an icon that links to the Excel worksheet.</span></span>

     <span data-ttu-id="fdf72-152">Vložit `CreateIconInWordDoc`metodu , která je k `Program` dispozici dále v tomto kroku, do třídy.</span><span class="sxs-lookup"><span data-stu-id="fdf72-152">Paste method `CreateIconInWordDoc`, provided later in this step, into the `Program` class.</span></span> <span data-ttu-id="fdf72-153">`CreateIconInWordDoc`používá pojmenované a volitelné argumenty ke snížení složitosti volání metody <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> a <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>.</span><span class="sxs-lookup"><span data-stu-id="fdf72-153">`CreateIconInWordDoc` uses named and optional arguments to reduce the complexity of the method calls to <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> and <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>.</span></span> <span data-ttu-id="fdf72-154">Tato volání obsahují dvě další nové funkce zavedené v C# 4, které zjednodušují volání metod COM, které mají referenční parametry.</span><span class="sxs-lookup"><span data-stu-id="fdf72-154">These calls incorporate two other new features introduced in C# 4 that simplify calls to COM methods that have reference parameters.</span></span> <span data-ttu-id="fdf72-155">Nejprve můžete odeslat argumenty do referenčních parametrů, jako by se jednalo o parametry hodnoty.</span><span class="sxs-lookup"><span data-stu-id="fdf72-155">First, you can send arguments to the reference parameters as if they were value parameters.</span></span> <span data-ttu-id="fdf72-156">To znamená, že můžete odesílat hodnoty přímo, bez vytvoření proměnné pro každý referenční parametr.</span><span class="sxs-lookup"><span data-stu-id="fdf72-156">That is, you can send values directly, without creating a variable for each reference parameter.</span></span> <span data-ttu-id="fdf72-157">Kompilátor generuje dočasné proměnné pro uložení hodnot argumentů a zahodí proměnné při návratu z volání.</span><span class="sxs-lookup"><span data-stu-id="fdf72-157">The compiler generates temporary variables to hold the argument values, and discards the variables when you return from the call.</span></span> <span data-ttu-id="fdf72-158">Za druhé můžete vynechat `ref` klíčové slovo v seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="fdf72-158">Second, you can omit the `ref` keyword in the argument list.</span></span>

     <span data-ttu-id="fdf72-159">Metoda `Add` má čtyři referenční parametry, z nichž všechny jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="fdf72-159">The `Add` method has four reference parameters, all of which are optional.</span></span> <span data-ttu-id="fdf72-160">V C# 4.0 a novější verze můžete vynechat argumenty pro některé nebo všechny parametry, pokud chcete použít jejich výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="fdf72-160">In C# 4.0 and later versions, you can omit arguments for any or all of the parameters if you want to use their default values.</span></span> <span data-ttu-id="fdf72-161">V C# 3.0 a starší verze argument musí být k dispozici pro každý parametr a argument musí být proměnná, protože parametry jsou referenční parametry.</span><span class="sxs-lookup"><span data-stu-id="fdf72-161">In C# 3.0 and earlier versions, an argument must be provided for each parameter, and the argument must be a variable because the parameters are reference parameters.</span></span>

     <span data-ttu-id="fdf72-162">Metoda `PasteSpecial` vloží obsah schránky.</span><span class="sxs-lookup"><span data-stu-id="fdf72-162">The `PasteSpecial` method inserts the contents of the Clipboard.</span></span> <span data-ttu-id="fdf72-163">Metoda má sedm referenčních parametrů, z nichž všechny jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="fdf72-163">The method has seven reference parameters, all of which are optional.</span></span> <span data-ttu-id="fdf72-164">Následující kód určuje argumenty pro dva `Link`z nich: , chcete-li vytvořit odkaz `DisplayAsIcon`na zdroj obsahu schránky a , zobrazit odkaz jako ikonu.</span><span class="sxs-lookup"><span data-stu-id="fdf72-164">The following code specifies arguments for two of them: `Link`, to create a link to the source of the Clipboard contents, and `DisplayAsIcon`, to display the link as an icon.</span></span> <span data-ttu-id="fdf72-165">V C# 4.0 a novější verze můžete použít pojmenované argumenty pro tyto dva a vynechat ostatní.</span><span class="sxs-lookup"><span data-stu-id="fdf72-165">In C# 4.0 and later versions, you can use named arguments for those two and omit the others.</span></span> <span data-ttu-id="fdf72-166">Přestože se jedná o referenční parametry, `ref` není třeba použít klíčové slovo nebo vytvořit proměnné pro odeslání jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="fdf72-166">Although these are reference parameters, you do not have to use the `ref` keyword, or to create variables to send in as arguments.</span></span> <span data-ttu-id="fdf72-167">Hodnoty můžete odeslat přímo.</span><span class="sxs-lookup"><span data-stu-id="fdf72-167">You can send the values directly.</span></span> <span data-ttu-id="fdf72-168">V C# 3.0 a staršíverze, musíte zadat argument proměnné pro každý referenční parametr.</span><span class="sxs-lookup"><span data-stu-id="fdf72-168">In C# 3.0 and earlier versions, you must supply a variable argument for each reference parameter.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#9)]

     <span data-ttu-id="fdf72-169">V jazyce C# 3.0 a staršíverze jazyka je vyžadován následující složitější kód.</span><span class="sxs-lookup"><span data-stu-id="fdf72-169">In C# 3.0 and earlier versions of the language, the following more complex code is required.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#10)]

2. <span data-ttu-id="fdf72-170">Na konec příkazu přidejte následující příkaz `Main`.</span><span class="sxs-lookup"><span data-stu-id="fdf72-170">Add the following statement at the end of `Main`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#11)]

3. <span data-ttu-id="fdf72-171">Na konec příkazu přidejte následující příkaz `DisplayInExcel`.</span><span class="sxs-lookup"><span data-stu-id="fdf72-171">Add the following statement at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="fdf72-172">Metoda `Copy` přidá list do schránky.</span><span class="sxs-lookup"><span data-stu-id="fdf72-172">The `Copy` method adds the worksheet to the Clipboard.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#12)]

4. <span data-ttu-id="fdf72-173">Stiskněte kombinaci kláves CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="fdf72-173">Press CTRL+F5.</span></span>

     <span data-ttu-id="fdf72-174">Zobrazí se dokument aplikace Word, který obsahuje ikonu.</span><span class="sxs-lookup"><span data-stu-id="fdf72-174">A Word document appears that contains an icon.</span></span> <span data-ttu-id="fdf72-175">Poklepáním na ikonu přenesete list do popředí.</span><span class="sxs-lookup"><span data-stu-id="fdf72-175">Double-click the icon to bring the worksheet to the foreground.</span></span>

## <a name="to-set-the-embed-interop-types-property"></a><span data-ttu-id="fdf72-176">Nastavení vlastnosti Vložit interop typy</span><span class="sxs-lookup"><span data-stu-id="fdf72-176">To set the Embed Interop Types property</span></span>

1. <span data-ttu-id="fdf72-177">Další vylepšení jsou možná při volání typu COM, který nevyžaduje primární sestavení interop (PIA) za běhu.</span><span class="sxs-lookup"><span data-stu-id="fdf72-177">Additional enhancements are possible when you call a COM type that does not require a primary interop assembly (PIA) at run time.</span></span> <span data-ttu-id="fdf72-178">Odebrání závislosti na PIA má za následek nezávislost verze a snadnější nasazení.</span><span class="sxs-lookup"><span data-stu-id="fdf72-178">Removing the dependency on PIAs results in version independence and easier deployment.</span></span> <span data-ttu-id="fdf72-179">Další informace o výhodách programování bez pia naleznete [v návodu: Vkládání typů ze spravovaných sestavení](../../../standard/assembly/embed-types-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="fdf72-179">For more information about the advantages of programming without PIAs, see [Walkthrough: Embedding Types from Managed Assemblies](../../../standard/assembly/embed-types-visual-studio.md).</span></span>

     <span data-ttu-id="fdf72-180">Programování je navíc jednodušší, protože typy, které jsou požadovány a vráceny metodami COM, mohou být reprezentovány pomocí typu `dynamic` namísto `Object`.</span><span class="sxs-lookup"><span data-stu-id="fdf72-180">In addition, programming is easier because the types that are required and returned by COM methods can be represented by using the type `dynamic` instead of `Object`.</span></span> <span data-ttu-id="fdf72-181">Proměnné, které `dynamic` mají typ nejsou vyhodnoceny až do běhu, což eliminuje potřebu explicitní odlévání.</span><span class="sxs-lookup"><span data-stu-id="fdf72-181">Variables that have type `dynamic` are not evaluated until run time, which eliminates the need for explicit casting.</span></span> <span data-ttu-id="fdf72-182">Další informace naleznete [v tématu Použití dynamického typu](../types/using-type-dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="fdf72-182">For more information, see [Using Type dynamic](../types/using-type-dynamic.md).</span></span>

     <span data-ttu-id="fdf72-183">V C# 4 vkládání informací o typu namísto použití PIA je výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="fdf72-183">In C# 4, embedding type information instead of using PIAs is default behavior.</span></span> <span data-ttu-id="fdf72-184">Z důvodu tohoto výchozího nastavení jsou některé z předchozích příkladů zjednodušeny, protože explicitní přetypování není vyžadováno.</span><span class="sxs-lookup"><span data-stu-id="fdf72-184">Because of that default, several of the previous examples are simplified because explicit casting is not required.</span></span> <span data-ttu-id="fdf72-185">Například prohlášení `worksheet` in `DisplayInExcel` je zapsán `Excel._Worksheet workSheet = excelApp.ActiveSheet` jako `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`spíše než .</span><span class="sxs-lookup"><span data-stu-id="fdf72-185">For example, the declaration of `worksheet` in `DisplayInExcel` is written as `Excel._Worksheet workSheet = excelApp.ActiveSheet` rather than `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`.</span></span> <span data-ttu-id="fdf72-186">Volání `AutoFit` ve stejné metodě by také vyžadovalo explicitní `ExcelApp.Columns[1]` přetypování bez výchozího, protože vrátí metodu `Object`aplikace a `AutoFit` je metodou aplikace Excel.</span><span class="sxs-lookup"><span data-stu-id="fdf72-186">The calls to `AutoFit` in the same method also would require explicit casting without the default, because `ExcelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel  method.</span></span> <span data-ttu-id="fdf72-187">Následující kód ukazuje přetypování.</span><span class="sxs-lookup"><span data-stu-id="fdf72-187">The following code shows the casting.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

2. <span data-ttu-id="fdf72-188">Chcete-li změnit výchozí nastavení a místo vkládání informací o typu použít pia, rozbalte uzel **Odkazy** v **Průzkumníku řešení** a vyberte **položku Microsoft.Office.Interop.Excel** nebo **Microsoft.Office.Interop.Word**.</span><span class="sxs-lookup"><span data-stu-id="fdf72-188">To change the default and use PIAs instead of embedding type information, expand the **References** node in **Solution Explorer** and then select **Microsoft.Office.Interop.Excel** or **Microsoft.Office.Interop.Word**.</span></span>

3. <span data-ttu-id="fdf72-189">Pokud okno **Vlastnosti** nevidíte, stiskněte **klávesu F4**.</span><span class="sxs-lookup"><span data-stu-id="fdf72-189">If you cannot see the **Properties** window, press **F4**.</span></span>

4. <span data-ttu-id="fdf72-190">V seznamu vlastností najdete **typy vložit interop** a změňte jeho hodnotu na **False**.</span><span class="sxs-lookup"><span data-stu-id="fdf72-190">Find **Embed Interop Types** in the list of properties, and change its value to **False**.</span></span> <span data-ttu-id="fdf72-191">Ekvivalentem můžete zkompilovat pomocí možnosti kompilátoru [-reference](../../language-reference/compiler-options/reference-compiler-option.md) namísto [-link](../../language-reference/compiler-options/link-compiler-option.md) na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="fdf72-191">Equivalently, you can compile by using the [-reference](../../language-reference/compiler-options/reference-compiler-option.md) compiler option instead of [-link](../../language-reference/compiler-options/link-compiler-option.md) at a command prompt.</span></span>

## <a name="to-add-additional-formatting-to-the-table"></a><span data-ttu-id="fdf72-192">Přidání dalšího formátování do tabulky</span><span class="sxs-lookup"><span data-stu-id="fdf72-192">To add additional formatting to the table</span></span>

1. <span data-ttu-id="fdf72-193">Nahraďte dvě `AutoFit` `DisplayInExcel` volání v následujícím příkazu.</span><span class="sxs-lookup"><span data-stu-id="fdf72-193">Replace the two calls to `AutoFit` in `DisplayInExcel` with the following statement.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#15)]

     <span data-ttu-id="fdf72-194">Metoda <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> má sedm parametry hodnoty, z nichž všechny jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="fdf72-194">The <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method has seven value parameters, all of which are optional.</span></span> <span data-ttu-id="fdf72-195">Pojmenované a volitelné argumenty umožňují poskytnout argumenty pro žádné, některé nebo všechny z nich.</span><span class="sxs-lookup"><span data-stu-id="fdf72-195">Named and optional arguments enable you to provide arguments for none, some, or all of them.</span></span> <span data-ttu-id="fdf72-196">V předchozím příkazu je zadán argument pouze pro `Format`jeden z parametrů .</span><span class="sxs-lookup"><span data-stu-id="fdf72-196">In the previous statement, an argument is supplied for only one of the parameters, `Format`.</span></span> <span data-ttu-id="fdf72-197">Protože `Format` je první parametr v seznamu parametrů, není třeba zadat název parametru.</span><span class="sxs-lookup"><span data-stu-id="fdf72-197">Because `Format` is the first parameter in the parameter list, you do not have to provide the parameter name.</span></span> <span data-ttu-id="fdf72-198">Příkaz však může být srozumitelnější, pokud je zahrnut název parametru, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="fdf72-198">However, the statement might be easier to understand if the parameter name is included, as is shown in the following code.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#16)]

2. <span data-ttu-id="fdf72-199">Stisknutím kláves CTRL+F5 zobrazíte výsledek.</span><span class="sxs-lookup"><span data-stu-id="fdf72-199">Press CTRL+F5 to see the result.</span></span> <span data-ttu-id="fdf72-200">Ostatní formáty jsou <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> uvedeny ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="fdf72-200">Other formats are listed in the <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> enumeration.</span></span>

3. <span data-ttu-id="fdf72-201">Porovnejte příkaz v kroku 1 s následujícím kódem, který zobrazuje argumenty, které jsou požadovány v C# 3.0 a starších verzích.</span><span class="sxs-lookup"><span data-stu-id="fdf72-201">Compare the statement in step 1 with the following code, which shows the arguments that are required in C# 3.0 and earlier versions.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#17)]

## <a name="example"></a><span data-ttu-id="fdf72-202">Příklad</span><span class="sxs-lookup"><span data-stu-id="fdf72-202">Example</span></span>

<span data-ttu-id="fdf72-203">Následující kód ukazuje úplný příklad.</span><span class="sxs-lookup"><span data-stu-id="fdf72-203">The following code shows the complete example.</span></span>

[!code-csharp[csProgGuideOfficeHowTo#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/walkthrough.cs#18)]

## <a name="see-also"></a><span data-ttu-id="fdf72-204">Viz také</span><span class="sxs-lookup"><span data-stu-id="fdf72-204">See also</span></span>

- <xref:System.Type.Missing?displayProperty=nameWithType>
- [<span data-ttu-id="fdf72-205">Dynamické</span><span class="sxs-lookup"><span data-stu-id="fdf72-205">dynamic</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="fdf72-206">Použití typu dynamic</span><span class="sxs-lookup"><span data-stu-id="fdf72-206">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="fdf72-207">Pojmenované a nepovinné argumenty</span><span class="sxs-lookup"><span data-stu-id="fdf72-207">Named and Optional Arguments</span></span>](../classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="fdf72-208">Použití pojmenovaných a volitelných argumentů v programování sady Office</span><span class="sxs-lookup"><span data-stu-id="fdf72-208">How to use named and optional arguments in Office programming</span></span>](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
