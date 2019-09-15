---
title: 'Postupy: Přístup k objektům Interop Office pomocí C# vizuálních C# funkcí – Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- optional parameters [C#], Office programming
- named and optional arguments [C#], Office programming
- dynamic [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
- Office programming [C#]
ms.assetid: 041b25c2-3512-4e0f-a4ea-ceb2999e4d5e
ms.openlocfilehash: 8e99402752b3fafb486735d56d66737f03ceec30
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972088"
---
# <a name="how-to-access-office-interop-objects-by-using-visual-c-features-c-programming-guide"></a><span data-ttu-id="f8a55-102">Postupy: Přístup k objektům Interop sady Office pomocí funkcí Visual C# (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="f8a55-102">How to: Access Office Interop Objects by Using Visual C# Features (C# Programming Guide)</span></span>

<span data-ttu-id="f8a55-103">Vizuál C# obsahuje funkce, které zjednodušují přístup k OBJEKTŮM rozhraní API Office.</span><span class="sxs-lookup"><span data-stu-id="f8a55-103">Visual C# has features that simplify access to Office API objects.</span></span> <span data-ttu-id="f8a55-104">Nové funkce zahrnují pojmenované a nepovinné argumenty, nový typ s názvem `dynamic`a možnost předat argumenty odkazovým parametrům v metodách modelu COM, jako kdyby byly parametry hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f8a55-104">The new features include named and optional arguments, a new type called `dynamic`, and the ability to pass arguments to reference parameters in COM methods as if they were value parameters.</span></span>

<span data-ttu-id="f8a55-105">V tomto tématu použijete nové funkce k psaní kódu, který vytvoří a zobrazí systém Microsoft Office excelový list.</span><span class="sxs-lookup"><span data-stu-id="f8a55-105">In this topic you will use the new features to write code that creates and displays a Microsoft Office Excel worksheet.</span></span> <span data-ttu-id="f8a55-106">Potom napíšete kód pro přidání dokumentu aplikace Office Word, který obsahuje ikonu, která je propojena s listem aplikace Excel.</span><span class="sxs-lookup"><span data-stu-id="f8a55-106">You will then write code to add an Office Word document that contains an icon that is linked to the Excel worksheet.</span></span>

<span data-ttu-id="f8a55-107">K dokončení tohoto Názorného postupu musíte mít v počítači nainstalovanou systém Microsoft Office Excel 2007 a systém Microsoft Office Word 2007 nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="f8a55-107">To complete this walkthrough, you must have Microsoft Office Excel 2007 and Microsoft Office Word 2007, or later versions, installed on your computer.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a><span data-ttu-id="f8a55-108">Vytvoření nové konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="f8a55-108">To create a new console application</span></span>

1. <span data-ttu-id="f8a55-109">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f8a55-109">Start Visual Studio.</span></span>

2. <span data-ttu-id="f8a55-110">V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**.</span><span class="sxs-lookup"><span data-stu-id="f8a55-110">On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="f8a55-111">Zobrazí se dialogové okno **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="f8a55-111">The **New Project** dialog box appears.</span></span>

3. <span data-ttu-id="f8a55-112">V podokně **Nainstalované šablony** rozbalte **vizuál C#** a pak klikněte na **Windows**.</span><span class="sxs-lookup"><span data-stu-id="f8a55-112">In the **Installed Templates** pane, expand **Visual C#**, and then click **Windows**.</span></span>

4. <span data-ttu-id="f8a55-113">Podívejte se v horní části dialogového okna **Nový projekt** , abyste se ujistili, že je jako cílová architektura vybraná **.NET Framework 4** (nebo novější verze).</span><span class="sxs-lookup"><span data-stu-id="f8a55-113">Look at the top of the **New Project** dialog box to make sure that **.NET Framework 4** (or later version) is selected as a target framework.</span></span>

5. <span data-ttu-id="f8a55-114">V podokně **šablony** klikněte na **Konzolová aplikace**.</span><span class="sxs-lookup"><span data-stu-id="f8a55-114">In the **Templates** pane, click **Console Application**.</span></span>

6. <span data-ttu-id="f8a55-115">Do pole **název** zadejte název projektu.</span><span class="sxs-lookup"><span data-stu-id="f8a55-115">Type a name for your project in the **Name** field.</span></span>

7. <span data-ttu-id="f8a55-116">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="f8a55-116">Click **OK**.</span></span>

     <span data-ttu-id="f8a55-117">Nový projekt se zobrazí v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="f8a55-117">The new project appears in **Solution Explorer**.</span></span>

## <a name="to-add-references"></a><span data-ttu-id="f8a55-118">Přidání odkazů</span><span class="sxs-lookup"><span data-stu-id="f8a55-118">To add references</span></span>

1. <span data-ttu-id="f8a55-119">V **Průzkumník řešení**klikněte pravým tlačítkem myši na název projektu a pak klikněte na **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="f8a55-119">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="f8a55-120">Zobrazí se dialogové okno **Přidat odkaz** .</span><span class="sxs-lookup"><span data-stu-id="f8a55-120">The **Add Reference** dialog box appears.</span></span>

2. <span data-ttu-id="f8a55-121">Na stránce **sestavení** vyberte v seznamu **název součásti** možnost **Microsoft. Office. Interop. Word** a pak stiskněte klávesu CTRL a vyberte **Microsoft. Office. Interop. Excel**.</span><span class="sxs-lookup"><span data-stu-id="f8a55-121">On the **Assemblies**  page, select **Microsoft.Office.Interop.Word** in the **Component Name** list, and then hold down the CTRL key and select **Microsoft.Office.Interop.Excel**.</span></span>  <span data-ttu-id="f8a55-122">Pokud nevidíte sestavení, možná budete muset zajistit, aby se nainstalovaly a zobrazovaly (viz [postup: Nainstalovat primární spolupracující sestavení](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies)pro Office</span><span class="sxs-lookup"><span data-stu-id="f8a55-122">If you do not see the assemblies, you may need to ensure they are installed and displayed (see [How to: Install Office Primary Interop Assemblies](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies))</span></span>

3. <span data-ttu-id="f8a55-123">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="f8a55-123">Click **OK**.</span></span>

## <a name="to-add-necessary-using-directives"></a><span data-ttu-id="f8a55-124">Přidání nezbytných direktiv using</span><span class="sxs-lookup"><span data-stu-id="f8a55-124">To add necessary using directives</span></span>

1. <span data-ttu-id="f8a55-125">V **Průzkumník řešení**klikněte pravým tlačítkem na soubor **program.cs** a pak klikněte na **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="f8a55-125">In **Solution Explorer**, right-click the **Program.cs** file and then click **View Code**.</span></span>

2. <span data-ttu-id="f8a55-126">Do horní části `using` souboru kódu přidejte následující direktivy.</span><span class="sxs-lookup"><span data-stu-id="f8a55-126">Add the following `using` directives to the top of the code file.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#1)]

## <a name="to-create-a-list-of-bank-accounts"></a><span data-ttu-id="f8a55-127">Vytvoření seznamu bankovních účtů</span><span class="sxs-lookup"><span data-stu-id="f8a55-127">To create a list of bank accounts</span></span>

1. <span data-ttu-id="f8a55-128">Vložte následující definici třídy do **program.cs**v rámci `Program` třídy.</span><span class="sxs-lookup"><span data-stu-id="f8a55-128">Paste the following class definition into **Program.cs**, under the `Program` class.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#2)]

2. <span data-ttu-id="f8a55-129">Přidejte následující kód do `Main` metody k `bankAccounts` vytvoření seznamu, který obsahuje dva účty.</span><span class="sxs-lookup"><span data-stu-id="f8a55-129">Add the following code to the `Main` method to create a `bankAccounts` list that contains two accounts.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#3)]

## <a name="to-declare-a-method-that-exports-account-information-to-excel"></a><span data-ttu-id="f8a55-130">Deklarace metody, která exportuje informace o účtu do Excelu</span><span class="sxs-lookup"><span data-stu-id="f8a55-130">To declare a method that exports account information to Excel</span></span>

1. <span data-ttu-id="f8a55-131">Přidejte následující metodu do `Program` třídy pro nastavení listu aplikace Excel.</span><span class="sxs-lookup"><span data-stu-id="f8a55-131">Add the following method to the `Program` class to set up an Excel worksheet.</span></span>

     <span data-ttu-id="f8a55-132">Metoda <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> má volitelný parametr pro určení konkrétní šablony.</span><span class="sxs-lookup"><span data-stu-id="f8a55-132">Method <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> has an optional parameter for specifying a particular template.</span></span> <span data-ttu-id="f8a55-133">Volitelné parametry, novinka C# ve 4, umožňují vynechat argument pro tento parametr, pokud chcete použít výchozí hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="f8a55-133">Optional parameters, new in C# 4, enable you to omit the argument for that parameter if you want to use the parameter's default value.</span></span> <span data-ttu-id="f8a55-134">Vzhledem k tomu, že žádný argument není odesílán v `Add` následujícím kódu, používá výchozí šablonu a vytvoří nový sešit.</span><span class="sxs-lookup"><span data-stu-id="f8a55-134">Because no argument is sent in the following code, `Add` uses the default template and creates a new workbook.</span></span> <span data-ttu-id="f8a55-135">Ekvivalent příkazu v dřívějších verzích nástroje C# vyžaduje zástupný argument:. `ExcelApp.Workbooks.Add(Type.Missing)`</span><span class="sxs-lookup"><span data-stu-id="f8a55-135">The equivalent statement in earlier versions of C# requires a placeholder argument: `ExcelApp.Workbooks.Add(Type.Missing)`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#4)]

2. <span data-ttu-id="f8a55-136">Přidejte následující kód na konec `DisplayInExcel`.</span><span class="sxs-lookup"><span data-stu-id="f8a55-136">Add the following code at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="f8a55-137">Kód vloží hodnoty do prvních dvou sloupců prvního řádku listu.</span><span class="sxs-lookup"><span data-stu-id="f8a55-137">The code inserts values into the first two columns of the first row of the worksheet.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#5)]

3. <span data-ttu-id="f8a55-138">Přidejte následující kód na konec `DisplayInExcel`.</span><span class="sxs-lookup"><span data-stu-id="f8a55-138">Add the following code at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="f8a55-139">`foreach` Smyčka vloží informace ze seznamu účtů do prvního dvou sloupců po sobě jdoucích řádků listu.</span><span class="sxs-lookup"><span data-stu-id="f8a55-139">The `foreach` loop puts the information from the list of accounts into the first two columns of successive rows of the worksheet.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#7)]

4. <span data-ttu-id="f8a55-140">Přidejte následující kód na konec `DisplayInExcel` a upravte šířku sloupce tak, aby odpovídaly obsahu.</span><span class="sxs-lookup"><span data-stu-id="f8a55-140">Add the following code at the end of `DisplayInExcel` to adjust the column widths to fit the content.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#13)]

     <span data-ttu-id="f8a55-141">Starší verze nástroje C# vyžadují explicitní přetypování pro tyto operace `ExcelApp.Columns[1]` `Object`, protože vrací a `AutoFit` je metoda aplikace <xref:Microsoft.Office.Interop.Excel.Range> Excel.</span><span class="sxs-lookup"><span data-stu-id="f8a55-141">Earlier versions of C# require explicit casting for these operations because `ExcelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel <xref:Microsoft.Office.Interop.Excel.Range> method.</span></span> <span data-ttu-id="f8a55-142">Následující řádky ukazují přetypování.</span><span class="sxs-lookup"><span data-stu-id="f8a55-142">The following lines show the casting.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

     <span data-ttu-id="f8a55-143">C#4 a novější verze, převádí `Object` vrácené na `dynamic` automatické, pokud je sestavení odkazováno pomocí možnosti kompilátoru [/Link](../../language-reference/compiler-options/link-compiler-option.md) nebo, ekvivalentní, pokud je vlastnost Excel **Embed Interop Types** nastavená na true.</span><span class="sxs-lookup"><span data-stu-id="f8a55-143">C# 4, and later versions, converts the returned `Object` to `dynamic` automatically if the assembly is referenced by the [/link](../../language-reference/compiler-options/link-compiler-option.md) compiler option or, equivalently, if the Excel **Embed Interop Types** property is set to true.</span></span> <span data-ttu-id="f8a55-144">Hodnota true je výchozí hodnota pro tuto vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f8a55-144">True is the default value for this property.</span></span>

## <a name="to-run-the-project"></a><span data-ttu-id="f8a55-145">Spuštění projektu</span><span class="sxs-lookup"><span data-stu-id="f8a55-145">To run the project</span></span>

1. <span data-ttu-id="f8a55-146">Přidejte následující řádek na konci `Main`.</span><span class="sxs-lookup"><span data-stu-id="f8a55-146">Add the following line at the end of `Main`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#8)]

2. <span data-ttu-id="f8a55-147">Stisknutím kláves CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="f8a55-147">Press CTRL+F5.</span></span>

     <span data-ttu-id="f8a55-148">Zobrazí se excelový list obsahující data ze dvou účtů.</span><span class="sxs-lookup"><span data-stu-id="f8a55-148">An Excel worksheet appears that contains the data from the two accounts.</span></span>

## <a name="to-add-a-word-document"></a><span data-ttu-id="f8a55-149">Přidání dokumentu aplikace Word</span><span class="sxs-lookup"><span data-stu-id="f8a55-149">To add a Word document</span></span>

1. <span data-ttu-id="f8a55-150">Pro ilustraci dalších způsobů, ve C# kterých 4 a novější verze vylepšuje programování pro Office, následující kód otevře aplikaci Word a vytvoří ikonu, která odkazuje na excelový list.</span><span class="sxs-lookup"><span data-stu-id="f8a55-150">To illustrate additional ways in which C# 4, and later versions, enhances Office programming, the following code opens a Word application and creates an icon that links to the Excel worksheet.</span></span>

     <span data-ttu-id="f8a55-151">Metoda `CreateIconInWordDoc`vložení, která `Program` je v tomto kroku k dispozici, do třídy.</span><span class="sxs-lookup"><span data-stu-id="f8a55-151">Paste method `CreateIconInWordDoc`, provided later in this step, into the `Program` class.</span></span> <span data-ttu-id="f8a55-152">`CreateIconInWordDoc`používá pojmenované a volitelné argumenty ke snížení složitosti volání metody do <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> a. <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A></span><span class="sxs-lookup"><span data-stu-id="f8a55-152">`CreateIconInWordDoc` uses named and optional arguments to reduce the complexity of the method calls to <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> and <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>.</span></span> <span data-ttu-id="f8a55-153">Tato volání zahrnují dvě další nové funkce, které C# byly představeny v 4, které zjednodušují volání metod modelu COM, které mají referenční parametry.</span><span class="sxs-lookup"><span data-stu-id="f8a55-153">These calls incorporate two other new features introduced in C# 4 that simplify calls to COM methods that have reference parameters.</span></span> <span data-ttu-id="f8a55-154">Nejprve můžete odeslat argumenty parametrům reference, jako by to byly parametry hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f8a55-154">First, you can send arguments to the reference parameters as if they were value parameters.</span></span> <span data-ttu-id="f8a55-155">To znamená, že můžete odesílat hodnoty přímo, bez vytváření proměnné pro každý parametr odkazu.</span><span class="sxs-lookup"><span data-stu-id="f8a55-155">That is, you can send values directly, without creating a variable for each reference parameter.</span></span> <span data-ttu-id="f8a55-156">Kompilátor generuje dočasné proměnné pro uchovávání hodnot argumentů a zahodí proměnné při návratu ze volání.</span><span class="sxs-lookup"><span data-stu-id="f8a55-156">The compiler generates temporary variables to hold the argument values, and discards the variables when you return from the call.</span></span> <span data-ttu-id="f8a55-157">Za druhé můžete `ref` klíčové slovo vynechat v seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="f8a55-157">Second, you can omit the `ref` keyword in the argument list.</span></span>

     <span data-ttu-id="f8a55-158">`Add` Metoda má čtyři referenční parametry, z nichž všechny jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="f8a55-158">The `Add` method has four reference parameters, all of which are optional.</span></span> <span data-ttu-id="f8a55-159">V C# 4,0 a novějších verzích můžete vynechat argumenty pro všechny nebo všechny parametry, pokud chcete použít výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f8a55-159">In C# 4.0 and later versions, you can omit arguments for any or all of the parameters if you want to use their default values.</span></span> <span data-ttu-id="f8a55-160">V C# 3,0 a starších verzích musí být pro každý parametr k dispozici argument a argument musí být proměnná, protože parametry jsou referenční parametry.</span><span class="sxs-lookup"><span data-stu-id="f8a55-160">In C# 3.0 and earlier versions, an argument must be provided for each parameter, and the argument must be a variable because the parameters are reference parameters.</span></span>

     <span data-ttu-id="f8a55-161">`PasteSpecial` Metoda vloží obsah schránky.</span><span class="sxs-lookup"><span data-stu-id="f8a55-161">The `PasteSpecial` method inserts the contents of the Clipboard.</span></span> <span data-ttu-id="f8a55-162">Metoda má sedm referenčních parametrů, z nichž všechny jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="f8a55-162">The method has seven reference parameters, all of which are optional.</span></span> <span data-ttu-id="f8a55-163">Následující kód Určuje argumenty pro dva z nich: `Link`, chcete-li vytvořit odkaz na zdroj obsahu schránky a `DisplayAsIcon`zobrazit odkaz jako ikonu.</span><span class="sxs-lookup"><span data-stu-id="f8a55-163">The following code specifies arguments for two of them: `Link`, to create a link to the source of the Clipboard contents, and `DisplayAsIcon`, to display the link as an icon.</span></span> <span data-ttu-id="f8a55-164">V C# 4,0 a novějších verzích můžete použít pojmenované argumenty pro tyto dva a vynechat ostatní.</span><span class="sxs-lookup"><span data-stu-id="f8a55-164">In C# 4.0 and later versions, you can use named arguments for those two and omit the others.</span></span> <span data-ttu-id="f8a55-165">I když se jedná o `ref` parametry odkazu, nemusíte používat klíčové slovo nebo k vytvoření proměnných pro odeslání jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="f8a55-165">Although these are reference parameters, you do not have to use the `ref` keyword, or to create variables to send in as arguments.</span></span> <span data-ttu-id="f8a55-166">Hodnoty můžete přímo odeslat.</span><span class="sxs-lookup"><span data-stu-id="f8a55-166">You can send the values directly.</span></span> <span data-ttu-id="f8a55-167">V C# 3,0 a starších verzích je nutné pro každý parametr odkazu vyplnit argument proměnné.</span><span class="sxs-lookup"><span data-stu-id="f8a55-167">In C# 3.0 and earlier versions, you must supply a variable argument for each reference parameter.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#9)]

     <span data-ttu-id="f8a55-168">V C# 3,0 a starších verzích jazyka je vyžadován následující složitější kód.</span><span class="sxs-lookup"><span data-stu-id="f8a55-168">In C# 3.0 and earlier versions of the language, the following more complex code is required.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#10)]

2. <span data-ttu-id="f8a55-169">Přidejte následující příkaz na konci `Main`.</span><span class="sxs-lookup"><span data-stu-id="f8a55-169">Add the following statement at the end of `Main`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#11)]

3. <span data-ttu-id="f8a55-170">Přidejte následující příkaz na konci `DisplayInExcel`.</span><span class="sxs-lookup"><span data-stu-id="f8a55-170">Add the following statement at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="f8a55-171">`Copy` Metoda přidá list do schránky.</span><span class="sxs-lookup"><span data-stu-id="f8a55-171">The `Copy` method adds the worksheet to the Clipboard.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#12)]

4. <span data-ttu-id="f8a55-172">Stisknutím kláves CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="f8a55-172">Press CTRL+F5.</span></span>

     <span data-ttu-id="f8a55-173">Zobrazí se dokument aplikace Word obsahující ikonu.</span><span class="sxs-lookup"><span data-stu-id="f8a55-173">A Word document appears that contains an icon.</span></span> <span data-ttu-id="f8a55-174">Dvojitým kliknutím na ikonu přeneste list do popředí.</span><span class="sxs-lookup"><span data-stu-id="f8a55-174">Double-click the icon to bring the worksheet to the foreground.</span></span>

## <a name="to-set-the-embed-interop-types-property"></a><span data-ttu-id="f8a55-175">Nastavení vlastnosti Embed Interop Types</span><span class="sxs-lookup"><span data-stu-id="f8a55-175">To set the Embed Interop Types property</span></span>

1. <span data-ttu-id="f8a55-176">Další vylepšení jsou možná při volání typu modelu COM, který nevyžaduje primární definiční sestavení (PIA) v době běhu.</span><span class="sxs-lookup"><span data-stu-id="f8a55-176">Additional enhancements are possible when you call a COM type that does not require a primary interop assembly (PIA) at run time.</span></span> <span data-ttu-id="f8a55-177">Výsledkem odebrání závislosti na PIA je nezávislost verzí a snazší nasazení.</span><span class="sxs-lookup"><span data-stu-id="f8a55-177">Removing the dependency on PIAs results in version independence and easier deployment.</span></span> <span data-ttu-id="f8a55-178">Další informace o výhodách programování bez PIA najdete v tématu [Názorný postup: Vložení typů ze spravovaných sestavení](../../../standard/assembly/embed-types-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="f8a55-178">For more information about the advantages of programming without PIAs, see [Walkthrough: Embedding Types from Managed Assemblies](../../../standard/assembly/embed-types-visual-studio.md).</span></span>

     <span data-ttu-id="f8a55-179">Kromě toho programování je snazší, protože typy, které jsou požadovány a vraceny metodou com, lze reprezentovat pomocí typu `dynamic` `Object`namísto.</span><span class="sxs-lookup"><span data-stu-id="f8a55-179">In addition, programming is easier because the types that are required and returned by COM methods can be represented by using the type `dynamic` instead of `Object`.</span></span> <span data-ttu-id="f8a55-180">Proměnné, které mají `dynamic` typ, nejsou vyhodnocovány až do doby běhu, což eliminuje nutnost explicitního přetypování.</span><span class="sxs-lookup"><span data-stu-id="f8a55-180">Variables that have type `dynamic` are not evaluated until run time, which eliminates the need for explicit casting.</span></span> <span data-ttu-id="f8a55-181">Další informace naleznete v tématu [použití typu Dynamic](../types/using-type-dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="f8a55-181">For more information, see [Using Type dynamic](../types/using-type-dynamic.md).</span></span>

     <span data-ttu-id="f8a55-182">Ve C# 4 je vkládání informací o typu namísto použití PIA nastaveno jako výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="f8a55-182">In C# 4, embedding type information instead of using PIAs is default behavior.</span></span> <span data-ttu-id="f8a55-183">Z důvodu tohoto výchozího nastavení je několik z předchozích příkladů zjednodušeno, protože explicitní přetypování není vyžadováno.</span><span class="sxs-lookup"><span data-stu-id="f8a55-183">Because of that default, several of the previous examples are simplified because explicit casting is not required.</span></span> <span data-ttu-id="f8a55-184">Například deklarace `worksheet` v `DisplayInExcel` je zapsána jako `Excel._Worksheet workSheet = excelApp.ActiveSheet` spíše než `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`.</span><span class="sxs-lookup"><span data-stu-id="f8a55-184">For example, the declaration of `worksheet` in `DisplayInExcel` is written as `Excel._Worksheet workSheet = excelApp.ActiveSheet` rather than `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`.</span></span> <span data-ttu-id="f8a55-185">Volání `AutoFit` ve stejné metodě by také vyžadovala explicitní přetypování bez výchozí hodnoty, protože `ExcelApp.Columns[1]` vrací `Object`a `AutoFit` je metoda aplikace Excel.</span><span class="sxs-lookup"><span data-stu-id="f8a55-185">The calls to `AutoFit` in the same method also would require explicit casting without the default, because `ExcelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel  method.</span></span> <span data-ttu-id="f8a55-186">Následující kód ukazuje přetypování.</span><span class="sxs-lookup"><span data-stu-id="f8a55-186">The following code shows the casting.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

2. <span data-ttu-id="f8a55-187">Chcete-li změnit výchozí nastavení a použít PIA namísto vložení informací o typu, rozbalte uzel **odkazy** v **Průzkumník řešení** a pak vyberte **Microsoft. Office. Interop. Excel** nebo **Microsoft. Office. Interop. Word**.</span><span class="sxs-lookup"><span data-stu-id="f8a55-187">To change the default and use PIAs instead of embedding type information, expand the **References** node in **Solution Explorer** and then select **Microsoft.Office.Interop.Excel** or **Microsoft.Office.Interop.Word**.</span></span>

3. <span data-ttu-id="f8a55-188">Pokud se okno **vlastnosti** nezobrazí, stiskněte **F4**.</span><span class="sxs-lookup"><span data-stu-id="f8a55-188">If you cannot see the **Properties** window, press **F4**.</span></span>

4. <span data-ttu-id="f8a55-189">Vyhledejte **typy spolupráce pro vložení** v seznamu vlastností a změňte její hodnotu na **false**.</span><span class="sxs-lookup"><span data-stu-id="f8a55-189">Find **Embed Interop Types** in the list of properties, and change its value to **False**.</span></span> <span data-ttu-id="f8a55-190">Ekvivalentně lze kompilovat pomocí možnosti kompilátoru [/reference](../../language-reference/compiler-options/reference-compiler-option.md) namísto rozhraní [/Link](../../language-reference/compiler-options/link-compiler-option.md) v příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="f8a55-190">Equivalently, you can compile by using the [/reference](../../language-reference/compiler-options/reference-compiler-option.md) compiler option instead of [/link](../../language-reference/compiler-options/link-compiler-option.md) at a command prompt.</span></span>

## <a name="to-add-additional-formatting-to-the-table"></a><span data-ttu-id="f8a55-191">Přidání dalšího formátování do tabulky</span><span class="sxs-lookup"><span data-stu-id="f8a55-191">To add additional formatting to the table</span></span>

1. <span data-ttu-id="f8a55-192">Nahraďte dvě volání do `AutoFit` v `DisplayInExcel` pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="f8a55-192">Replace the two calls to `AutoFit` in `DisplayInExcel` with the following statement.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#15)]

     <span data-ttu-id="f8a55-193"><xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> Metoda má sedm parametrů hodnot, z nichž všechny jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="f8a55-193">The <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method has seven value parameters, all of which are optional.</span></span> <span data-ttu-id="f8a55-194">Pojmenované a volitelné argumenty umožňují zadat argumenty pro žádné, některé nebo všechny.</span><span class="sxs-lookup"><span data-stu-id="f8a55-194">Named and optional arguments enable you to provide arguments for none, some, or all of them.</span></span> <span data-ttu-id="f8a55-195">V předchozím příkazu je argument zadán pouze pro jeden z parametrů, `Format`.</span><span class="sxs-lookup"><span data-stu-id="f8a55-195">In the previous statement, an argument is supplied for only one of the parameters, `Format`.</span></span> <span data-ttu-id="f8a55-196">Protože `Format` je prvním parametrem v seznamu parametrů, nemusíte zadávat název parametru.</span><span class="sxs-lookup"><span data-stu-id="f8a55-196">Because `Format` is the first parameter in the parameter list, you do not have to provide the parameter name.</span></span> <span data-ttu-id="f8a55-197">Příkaz však může být snazší pochopit, zda je název parametru zahrnut, jak je uvedeno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="f8a55-197">However, the statement might be easier to understand if the parameter name is included, as is shown in the following code.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#16)]

2. <span data-ttu-id="f8a55-198">Výsledek zobrazíte stisknutím kombinace kláves CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="f8a55-198">Press CTRL+F5 to see the result.</span></span> <span data-ttu-id="f8a55-199">Další formáty jsou uvedeny ve <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> výčtu.</span><span class="sxs-lookup"><span data-stu-id="f8a55-199">Other formats are listed in the <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> enumeration.</span></span>

3. <span data-ttu-id="f8a55-200">Porovnejte příkaz v kroku 1 s následujícím kódem, který ukazuje argumenty vyžadované v C# 3,0 a dřívějších verzích.</span><span class="sxs-lookup"><span data-stu-id="f8a55-200">Compare the statement in step 1 with the following code, which shows the arguments that are required in C# 3.0 and earlier versions.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#17)]

## <a name="example"></a><span data-ttu-id="f8a55-201">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8a55-201">Example</span></span>

<span data-ttu-id="f8a55-202">Následující kód ukazuje kompletní příklad.</span><span class="sxs-lookup"><span data-stu-id="f8a55-202">The following code shows the complete example.</span></span>

[!code-csharp[csProgGuideOfficeHowTo#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/walkthrough.cs#18)]

## <a name="see-also"></a><span data-ttu-id="f8a55-203">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8a55-203">See also</span></span>

- <xref:System.Type.Missing?displayProperty=nameWithType>
- [<span data-ttu-id="f8a55-204">dynamic</span><span class="sxs-lookup"><span data-stu-id="f8a55-204">dynamic</span></span>](../../language-reference/keywords/dynamic.md)
- [<span data-ttu-id="f8a55-205">Použití typu dynamic</span><span class="sxs-lookup"><span data-stu-id="f8a55-205">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="f8a55-206">Pojmenované a nepovinné argumenty</span><span class="sxs-lookup"><span data-stu-id="f8a55-206">Named and Optional Arguments</span></span>](../classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="f8a55-207">Postupy: Použití pojmenovaných a nepovinných argumentů v programování pro Office</span><span class="sxs-lookup"><span data-stu-id="f8a55-207">How to: Use Named and Optional Arguments in Office Programming</span></span>](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
