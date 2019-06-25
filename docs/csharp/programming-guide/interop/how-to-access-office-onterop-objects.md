---
title: 'Postupy: Přístup k objektům Interop sady Office pomocí Vizuálu C# funkce – C# Průvodce programováním'
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
ms.openlocfilehash: 9163bfa98d85a3268e154321d1aa6e55783a50f9
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2019
ms.locfileid: "67347638"
---
# <a name="how-to-access-office-interop-objects-by-using-visual-c-features-c-programming-guide"></a><span data-ttu-id="06535-102">Postupy: Přístup k objektům Interop sady Office pomocí funkcí Visual C# (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="06535-102">How to: Access Office Interop Objects by Using Visual C# Features (C# Programming Guide)</span></span>
<span data-ttu-id="06535-103">Visual C# obsahuje funkce, které usnadňují přístup k objektům rozhraní API Office.</span><span class="sxs-lookup"><span data-stu-id="06535-103">Visual C# has features that simplify access to Office API objects.</span></span> <span data-ttu-id="06535-104">Nové funkce patří pojmenované a nepovinné argumenty, nový typ s názvem `dynamic`a možnost předání argumentů do parametrů odkazu v metodách modelu COM, jako by byly parametry s hodnotou.</span><span class="sxs-lookup"><span data-stu-id="06535-104">The new features include named and optional arguments, a new type called `dynamic`, and the ability to pass arguments to reference parameters in COM methods as if they were value parameters.</span></span>  
  
 <span data-ttu-id="06535-105">V tomto tématu použijete nové funkce napsat kód, který vytvoří a zobrazí list aplikace Microsoft Office Excel.</span><span class="sxs-lookup"><span data-stu-id="06535-105">In this topic you will use the new features to write code that creates and displays a Microsoft Office Excel worksheet.</span></span> <span data-ttu-id="06535-106">Potom napíšete kód pro přidání dokumentu Office Word, který obsahuje ikonu, která je propojený Excelový list.</span><span class="sxs-lookup"><span data-stu-id="06535-106">You will then write code to add an Office Word document that contains an icon that is linked to the Excel worksheet.</span></span>  
  
 <span data-ttu-id="06535-107">K dokončení tohoto návodu, musíte mít aplikaci Microsoft Office Excel 2007 a Microsoft Office Word 2007 nebo novější verze, v počítači nainstalována.</span><span class="sxs-lookup"><span data-stu-id="06535-107">To complete this walkthrough, you must have Microsoft Office Excel 2007 and Microsoft Office Word 2007, or later versions, installed on your computer.</span></span>  
  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-create-a-new-console-application"></a><span data-ttu-id="06535-108">Vytvořte novou konzolovou aplikaci</span><span class="sxs-lookup"><span data-stu-id="06535-108">To create a new console application</span></span>  
  
1. <span data-ttu-id="06535-109">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="06535-109">Start Visual Studio.</span></span>  
  
2. <span data-ttu-id="06535-110">Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.</span><span class="sxs-lookup"><span data-stu-id="06535-110">On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="06535-111">Zobrazí se dialogové okno **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="06535-111">The **New Project** dialog box appears.</span></span>  
  
3. <span data-ttu-id="06535-112">V **nainstalované šablony** podokně rozbalte **Visual C#** a potom klikněte na tlačítko **Windows**.</span><span class="sxs-lookup"><span data-stu-id="06535-112">In the **Installed Templates** pane, expand **Visual C#**, and then click **Windows**.</span></span>  
  
4. <span data-ttu-id="06535-113">Hledat v horní části **nový projekt** dialogové okno že **rozhraní .NET Framework 4** (nebo novější verzi) je vybraná jako Cílová architektura.</span><span class="sxs-lookup"><span data-stu-id="06535-113">Look at the top of the **New Project** dialog box to make sure that **.NET Framework 4** (or later version) is selected as a target framework.</span></span>  
  
5. <span data-ttu-id="06535-114">V **šablony** podokně klikněte na tlačítko **konzolovou aplikaci**.</span><span class="sxs-lookup"><span data-stu-id="06535-114">In the **Templates** pane, click **Console Application**.</span></span>  
  
6. <span data-ttu-id="06535-115">Zadejte název pro váš projekt v **název** pole.</span><span class="sxs-lookup"><span data-stu-id="06535-115">Type a name for your project in the **Name** field.</span></span>  
  
7. <span data-ttu-id="06535-116">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="06535-116">Click **OK**.</span></span>  
  
     <span data-ttu-id="06535-117">Nový projekt se zobrazí v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="06535-117">The new project appears in **Solution Explorer**.</span></span>  
  
## <a name="to-add-references"></a><span data-ttu-id="06535-118">Přidání odkazů</span><span class="sxs-lookup"><span data-stu-id="06535-118">To add references</span></span>  
  
1. <span data-ttu-id="06535-119">V **Průzkumníka řešení**, klikněte pravým tlačítkem na název vašeho projektu a pak klikněte na tlačítko **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="06535-119">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="06535-120">**Přidat odkaz** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="06535-120">The **Add Reference** dialog box appears.</span></span>  
  
2. <span data-ttu-id="06535-121">Na **sestavení** stránce **Microsoft.Office.Interop.Word** v **název komponenty** seznamu a pak podržte klávesu CTRL, klíče a vyberte  **Microsoft.Office.Interop.Excel**.</span><span class="sxs-lookup"><span data-stu-id="06535-121">On the **Assemblies**  page, select **Microsoft.Office.Interop.Word** in the **Component Name** list, and then hold down the CTRL key and select **Microsoft.Office.Interop.Excel**.</span></span>  <span data-ttu-id="06535-122">Pokud nevidíte sestavení, budete muset zajistit, jsou nainstalované a zobrazí (viz [jak: Instalace primárních sestavení vzájemné spolupráce Office](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies))</span><span class="sxs-lookup"><span data-stu-id="06535-122">If you do not see the assemblies, you may need to ensure they are installed and displayed (see [How to: Install Office Primary Interop Assemblies](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies))</span></span>  
  
3. <span data-ttu-id="06535-123">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="06535-123">Click **OK**.</span></span>  
  
## <a name="to-add-necessary-using-directives"></a><span data-ttu-id="06535-124">Chcete-li přidat nezbytné direktivy using</span><span class="sxs-lookup"><span data-stu-id="06535-124">To add necessary using directives</span></span>  
  
1. <span data-ttu-id="06535-125">V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **Program.cs** souboru a pak klikněte na tlačítko **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="06535-125">In **Solution Explorer**, right-click the **Program.cs** file and then click **View Code**.</span></span>  
  
2. <span data-ttu-id="06535-126">Přidejte následující `using` direktivy do horní části souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="06535-126">Add the following `using` directives to the top of the code file.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#1)]  
  
## <a name="to-create-a-list-of-bank-accounts"></a><span data-ttu-id="06535-127">Chcete-li vytvořit seznam účtů bank</span><span class="sxs-lookup"><span data-stu-id="06535-127">To create a list of bank accounts</span></span>  
  
1. <span data-ttu-id="06535-128">Vložte následující definice třídy do **Program.cs**v části `Program` třídy.</span><span class="sxs-lookup"><span data-stu-id="06535-128">Paste the following class definition into **Program.cs**, under the `Program` class.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#2)]  
  
2. <span data-ttu-id="06535-129">Přidejte následující kód, který `Main` metodu pro vytvoření `bankAccounts` seznam, který obsahuje dva účty.</span><span class="sxs-lookup"><span data-stu-id="06535-129">Add the following code to the `Main` method to create a `bankAccounts` list that contains two accounts.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#3)]  
  
## <a name="to-declare-a-method-that-exports-account-information-to-excel"></a><span data-ttu-id="06535-130">Chcete-li deklarovat metodu, která se exportuje informace o účtu do Excelu</span><span class="sxs-lookup"><span data-stu-id="06535-130">To declare a method that exports account information to Excel</span></span>  
  
1. <span data-ttu-id="06535-131">Přidejte následující metodu do `Program` třídy nastavit Excelového listu.</span><span class="sxs-lookup"><span data-stu-id="06535-131">Add the following method to the `Program` class to set up an Excel worksheet.</span></span>  
  
     <span data-ttu-id="06535-132">Metoda <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> je volitelný parametr určující konkrétní šablonu.</span><span class="sxs-lookup"><span data-stu-id="06535-132">Method <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> has an optional parameter for specifying a particular template.</span></span> <span data-ttu-id="06535-133">Volitelné parametry, které jsou nové v C# 4, umožňují argument pro tento parametr vynechat, pokud chcete použít výchozí hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="06535-133">Optional parameters, new in C# 4, enable you to omit the argument for that parameter if you want to use the parameter's default value.</span></span> <span data-ttu-id="06535-134">Protože je v následujícím kódu žádný argument `Add` používá výchozí šablonu a vytvoří nový sešit.</span><span class="sxs-lookup"><span data-stu-id="06535-134">Because no argument is sent in the following code, `Add` uses the default template and creates a new workbook.</span></span> <span data-ttu-id="06535-135">Ekvivalentní příkaz ve starších verzích jazyka C# vyžaduje argument zástupný symbol: `ExcelApp.Workbooks.Add(Type.Missing)`.</span><span class="sxs-lookup"><span data-stu-id="06535-135">The equivalent statement in earlier versions of C# requires a placeholder argument: `ExcelApp.Workbooks.Add(Type.Missing)`.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#4)]  
  
2. <span data-ttu-id="06535-136">Přidejte následující kód na konci `DisplayInExcel`.</span><span class="sxs-lookup"><span data-stu-id="06535-136">Add the following code at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="06535-137">Kód vloží hodnoty do prvních dvou sloupcích prvního řádku listu.</span><span class="sxs-lookup"><span data-stu-id="06535-137">The code inserts values into the first two columns of the first row of the worksheet.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#5)]  
  
3. <span data-ttu-id="06535-138">Přidejte následující kód na konci `DisplayInExcel`.</span><span class="sxs-lookup"><span data-stu-id="06535-138">Add the following code at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="06535-139">`foreach` Smyčky vloží informace ze seznamu účtů do prvních dvou sloupců po sobě jdoucích řádků z listu.</span><span class="sxs-lookup"><span data-stu-id="06535-139">The `foreach` loop puts the information from the list of accounts into the first two columns of successive rows of the worksheet.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#7)]  
  
4. <span data-ttu-id="06535-140">Přidejte následující kód na konci `DisplayInExcel` upravit šířku sloupců podle obsahu.</span><span class="sxs-lookup"><span data-stu-id="06535-140">Add the following code at the end of `DisplayInExcel` to adjust the column widths to fit the content.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#13)]  
  
     <span data-ttu-id="06535-141">Starší verze jazyka C# vyžaduje explicitní přetypování pro tyto operace protože `ExcelApp.Columns[1]` vrátí `Object`, a `AutoFit` je aplikace Excel <xref:Microsoft.Office.Interop.Excel.Range> metody.</span><span class="sxs-lookup"><span data-stu-id="06535-141">Earlier versions of C# require explicit casting for these operations because `ExcelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel <xref:Microsoft.Office.Interop.Excel.Range> method.</span></span> <span data-ttu-id="06535-142">Následující řádky zobrazují přetypování.</span><span class="sxs-lookup"><span data-stu-id="06535-142">The following lines show the casting.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]  
  
     <span data-ttu-id="06535-143">C#4 a novější verze, převede vrácený `Object` k `dynamic` automaticky, pokud je sestavení odkazuje [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) – možnost kompilátoru nebo ekvivalentně, pokud v aplikaci Excel **Embed Interop Types** je nastavena na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="06535-143">C# 4, and later versions, converts the returned `Object` to `dynamic` automatically if the assembly is referenced by the [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) compiler option or, equivalently, if the Excel **Embed Interop Types** property is set to true.</span></span> <span data-ttu-id="06535-144">Hodnota TRUE je výchozí hodnota této vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="06535-144">True is the default value for this property.</span></span>  
  
## <a name="to-run-the-project"></a><span data-ttu-id="06535-145">Spustit projekt</span><span class="sxs-lookup"><span data-stu-id="06535-145">To run the project</span></span>  
  
1. <span data-ttu-id="06535-146">Přidejte následující řádek na konci `Main`.</span><span class="sxs-lookup"><span data-stu-id="06535-146">Add the following line at the end of `Main`.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#8)]  
  
2. <span data-ttu-id="06535-147">Stisknutím kláves CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="06535-147">Press CTRL+F5.</span></span>  
  
     <span data-ttu-id="06535-148">Zobrazí se Excelového listu, který obsahuje data z obou účtů.</span><span class="sxs-lookup"><span data-stu-id="06535-148">An Excel worksheet appears that contains the data from the two accounts.</span></span>  
  
## <a name="to-add-a-word-document"></a><span data-ttu-id="06535-149">Chcete-li přidat dokument aplikace Word</span><span class="sxs-lookup"><span data-stu-id="06535-149">To add a Word document</span></span>  
  
1. <span data-ttu-id="06535-150">Pro ilustraci další způsoby C# 4 a novější verze, rozšiřuje programování pro Office, následující kód se otevře aplikace Word a vytvoří ikonu, která odkazuje na Excelový list.</span><span class="sxs-lookup"><span data-stu-id="06535-150">To illustrate additional ways in which C# 4, and later versions, enhances Office programming, the following code opens a Word application and creates an icon that links to the Excel worksheet.</span></span>  
  
     <span data-ttu-id="06535-151">Vložit metodu `CreateIconInWordDoc`, k dispozici dále v tomto kroku do `Program` třídy.</span><span class="sxs-lookup"><span data-stu-id="06535-151">Paste method `CreateIconInWordDoc`, provided later in this step, into the `Program` class.</span></span> <span data-ttu-id="06535-152">`CreateIconInWordDoc` pojmenované a nepovinné argumenty používá ke snížení složitosti volání metody <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> a <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>.</span><span class="sxs-lookup"><span data-stu-id="06535-152">`CreateIconInWordDoc` uses named and optional arguments to reduce the complexity of the method calls to <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> and <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>.</span></span> <span data-ttu-id="06535-153">Tato volání začlenit dvě další nové vlastnosti představené v C# 4, které zjednodušují volání metody COM, které mají odkazovat na parametry.</span><span class="sxs-lookup"><span data-stu-id="06535-153">These calls incorporate two other new features introduced in C# 4 that simplify calls to COM methods that have reference parameters.</span></span> <span data-ttu-id="06535-154">Nejprve můžete poslat argumenty parametrů odkazu jako by byly parametry s hodnotou.</span><span class="sxs-lookup"><span data-stu-id="06535-154">First, you can send arguments to the reference parameters as if they were value parameters.</span></span> <span data-ttu-id="06535-155">To znamená můžete odeslat hodnoty přímo, bez vytváření proměnných pro každý odkaz na parametr.</span><span class="sxs-lookup"><span data-stu-id="06535-155">That is, you can send values directly, without creating a variable for each reference parameter.</span></span> <span data-ttu-id="06535-156">Kompilátor generuje dočasné proměnné pro uložení hodnoty argumentů a zahodí proměnné při návratu z volání.</span><span class="sxs-lookup"><span data-stu-id="06535-156">The compiler generates temporary variables to hold the argument values, and discards the variables when you return from the call.</span></span> <span data-ttu-id="06535-157">Za druhé, můžete vynechat `ref` – klíčové slovo v seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="06535-157">Second, you can omit the `ref` keyword in the argument list.</span></span>  
  
     <span data-ttu-id="06535-158">`Add` Metoda má čtyři parametry odkazu, z nichž všechny jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="06535-158">The `Add` method has four reference parameters, all of which are optional.</span></span> <span data-ttu-id="06535-159">V C# 4.0 a novější verze, pokud chcete použít výchozí hodnoty, můžete vynechat argumenty pro některé nebo všechny parametry.</span><span class="sxs-lookup"><span data-stu-id="06535-159">In C# 4.0 and later versions, you can omit arguments for any or all of the parameters if you want to use their default values.</span></span> <span data-ttu-id="06535-160">V C# 3.0 a starší verze pro každý parametr je třeba zadat argument a argument musí být proměnná, protože parametry jsou parametry odkazů.</span><span class="sxs-lookup"><span data-stu-id="06535-160">In C# 3.0 and earlier versions, an argument must be provided for each parameter, and the argument must be a variable because the parameters are reference parameters.</span></span>  
  
     <span data-ttu-id="06535-161">`PasteSpecial` Metoda vloží obsah schránky.</span><span class="sxs-lookup"><span data-stu-id="06535-161">The `PasteSpecial` method inserts the contents of the Clipboard.</span></span> <span data-ttu-id="06535-162">Metoda má sedm parametrů odkazu, z nichž všechny jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="06535-162">The method has seven reference parameters, all of which are optional.</span></span> <span data-ttu-id="06535-163">Následující kód určuje argumenty pro dva z nich: `Link`, chcete-li vytvořit odkaz na zdroj obsah schránky a `DisplayAsIcon`, aby se zobrazil na odkaz jako ikona.</span><span class="sxs-lookup"><span data-stu-id="06535-163">The following code specifies arguments for two of them: `Link`, to create a link to the source of the Clipboard contents, and `DisplayAsIcon`, to display the link as an icon.</span></span> <span data-ttu-id="06535-164">V C# 4.0 a novější verze, můžete použít pojmenované argumenty pro tyto dvě a ostatní vynechat.</span><span class="sxs-lookup"><span data-stu-id="06535-164">In C# 4.0 and later versions, you can use named arguments for those two and omit the others.</span></span> <span data-ttu-id="06535-165">I když jsou parametry odkazů, není potřeba použít `ref` – klíčové slovo, nebo k vytvoření proměnné k odeslání jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="06535-165">Although these are reference parameters, you do not have to use the `ref` keyword, or to create variables to send in as arguments.</span></span> <span data-ttu-id="06535-166">Hodnoty můžete odeslat přímo.</span><span class="sxs-lookup"><span data-stu-id="06535-166">You can send the values directly.</span></span> <span data-ttu-id="06535-167">V C# 3.0 a starší verze, je nutné zadat argumentů proměnných pro každý odkaz na parametr.</span><span class="sxs-lookup"><span data-stu-id="06535-167">In C# 3.0 and earlier versions, you must supply a variable argument for each reference parameter.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#9)]  
  
     <span data-ttu-id="06535-168">V C# 3.0 a starší verze jazyka následující složitější kód je povinný.</span><span class="sxs-lookup"><span data-stu-id="06535-168">In C# 3.0 and earlier versions of the language, the following more complex code is required.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#10)]  
  
2. <span data-ttu-id="06535-169">Přidejte následující příkaz na konci `Main`.</span><span class="sxs-lookup"><span data-stu-id="06535-169">Add the following statement at the end of `Main`.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#11)]  
  
3. <span data-ttu-id="06535-170">Přidejte následující příkaz na konci `DisplayInExcel`.</span><span class="sxs-lookup"><span data-stu-id="06535-170">Add the following statement at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="06535-171">`Copy` Metoda přidá do listu do schránky.</span><span class="sxs-lookup"><span data-stu-id="06535-171">The `Copy` method adds the worksheet to the Clipboard.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#12)]  
  
4. <span data-ttu-id="06535-172">Stisknutím kláves CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="06535-172">Press CTRL+F5.</span></span>  
  
     <span data-ttu-id="06535-173">Zobrazí se Wordový dokument, který obsahuje ikonu.</span><span class="sxs-lookup"><span data-stu-id="06535-173">A Word document appears that contains an icon.</span></span> <span data-ttu-id="06535-174">Poklepejte na ikonu na listu přenést do popředí.</span><span class="sxs-lookup"><span data-stu-id="06535-174">Double-click the icon to bring the worksheet to the foreground.</span></span>  
  
## <a name="to-set-the-embed-interop-types-property"></a><span data-ttu-id="06535-175">Nastavení vlastnosti vložit typy spolupráce</span><span class="sxs-lookup"><span data-stu-id="06535-175">To set the Embed Interop Types property</span></span>  
  
1. <span data-ttu-id="06535-176">Další vylepšení je možné při volání typu COM, který nevyžaduje, aby primární definiční sestavení (PIA) v době běhu.</span><span class="sxs-lookup"><span data-stu-id="06535-176">Additional enhancements are possible when you call a COM type that does not require a primary interop assembly (PIA) at run time.</span></span> <span data-ttu-id="06535-177">Odebráním závislosti na výsledky sestavení PIA v nezávislosti na verzi a nasazení.</span><span class="sxs-lookup"><span data-stu-id="06535-177">Removing the dependency on PIAs results in version independence and easier deployment.</span></span> <span data-ttu-id="06535-178">Další informace o výhodách programování bez PIA, naleznete v tématu [názorný postup: Vložení typů ze spravovaných sestavení](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="06535-178">For more information about the advantages of programming without PIAs, see [Walkthrough: Embedding Types from Managed Assemblies](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).</span></span>  
  
     <span data-ttu-id="06535-179">Programování je navíc jednodušší, protože typy, které vyžadují a vrácené z metody modelu COM lze znázornit pomocí typu `dynamic` místo `Object`.</span><span class="sxs-lookup"><span data-stu-id="06535-179">In addition, programming is easier because the types that are required and returned by COM methods can be represented by using the type `dynamic` instead of `Object`.</span></span> <span data-ttu-id="06535-180">Proměnné, které mají typ `dynamic` není u nich vyhodnoceno až do spuštění, která eliminuje potřebu explicitní přetypování.</span><span class="sxs-lookup"><span data-stu-id="06535-180">Variables that have type `dynamic` are not evaluated until run time, which eliminates the need for explicit casting.</span></span> <span data-ttu-id="06535-181">Další informace najdete v tématu [použití typu dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="06535-181">For more information, see [Using Type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).</span></span>  
  
     <span data-ttu-id="06535-182">V C# 4, vkládání typ informace namísto použití sestavení PIA, je výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="06535-182">In C# 4, embedding type information instead of using PIAs is default behavior.</span></span> <span data-ttu-id="06535-183">Z důvodu tuto výchozí hodnotu některé z předchozích příkladech jsou jednodušší, protože není nutné explicitní přetypování.</span><span class="sxs-lookup"><span data-stu-id="06535-183">Because of that default, several of the previous examples are simplified because explicit casting is not required.</span></span> <span data-ttu-id="06535-184">Například, deklarace `worksheet` v `DisplayInExcel` je zapsán jako `Excel._Worksheet workSheet = excelApp.ActiveSheet` spíše než `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`.</span><span class="sxs-lookup"><span data-stu-id="06535-184">For example, the declaration of `worksheet` in `DisplayInExcel` is written as `Excel._Worksheet workSheet = excelApp.ActiveSheet` rather than `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`.</span></span> <span data-ttu-id="06535-185">Volání `AutoFit` v stejným způsobem také by vyžadovaly explicitní přetypování bez výchozí, protože `ExcelApp.Columns[1]` vrátí `Object`, a `AutoFit` je metoda aplikace Excel.</span><span class="sxs-lookup"><span data-stu-id="06535-185">The calls to `AutoFit` in the same method also would require explicit casting without the default, because `ExcelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel  method.</span></span> <span data-ttu-id="06535-186">Následující kód ukazuje, přetypování.</span><span class="sxs-lookup"><span data-stu-id="06535-186">The following code shows the casting.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]  
  
2. <span data-ttu-id="06535-187">Chcete-li změnit výchozí nastavení a použití sestavení PIA místo vložení informací o typu, rozbalte **odkazy** uzel v **Průzkumníka řešení** a pak vyberte **Microsoft.Office.Interop.Excel** nebo **Microsoft.Office.Interop.Word**.</span><span class="sxs-lookup"><span data-stu-id="06535-187">To change the default and use PIAs instead of embedding type information, expand the **References** node in **Solution Explorer** and then select **Microsoft.Office.Interop.Excel** or **Microsoft.Office.Interop.Word**.</span></span>  
  
3. <span data-ttu-id="06535-188">Pokud nevidíte **vlastnosti** okna, stisknutím klávesy **F4**.</span><span class="sxs-lookup"><span data-stu-id="06535-188">If you cannot see the **Properties** window, press **F4**.</span></span>  
  
4. <span data-ttu-id="06535-189">Najít **Embed Interop Types** v seznamu vlastností a změňte tuto hodnotu na **False**.</span><span class="sxs-lookup"><span data-stu-id="06535-189">Find **Embed Interop Types** in the list of properties, and change its value to **False**.</span></span> <span data-ttu-id="06535-190">Ekvivalentně, můžete zkompilovat pomocí [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) – možnost kompilátoru místo [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="06535-190">Equivalently, you can compile by using the [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) compiler option instead of [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) at a command prompt.</span></span>  
  
## <a name="to-add-additional-formatting-to-the-table"></a><span data-ttu-id="06535-191">Chcete-li přidat další formátování do tabulky</span><span class="sxs-lookup"><span data-stu-id="06535-191">To add additional formatting to the table</span></span>  
  
1. <span data-ttu-id="06535-192">Nahraďte dvě volání na `AutoFit` v `DisplayInExcel` pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="06535-192">Replace the two calls to `AutoFit` in `DisplayInExcel` with the following statement.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#15)]  
  
     <span data-ttu-id="06535-193"><xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> Metoda má sedm parametry s hodnotou, z nichž všechny jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="06535-193">The <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method has seven value parameters, all of which are optional.</span></span> <span data-ttu-id="06535-194">Pojmenované a nepovinné argumenty umožňují zadat argumenty pro none, některé nebo všechny z nich.</span><span class="sxs-lookup"><span data-stu-id="06535-194">Named and optional arguments enable you to provide arguments for none, some, or all of them.</span></span> <span data-ttu-id="06535-195">V předchozí prohlášení, je zadán argument pouze pro jeden z parametrů, `Format`.</span><span class="sxs-lookup"><span data-stu-id="06535-195">In the previous statement, an argument is supplied for only one of the parameters, `Format`.</span></span> <span data-ttu-id="06535-196">Protože `Format` je první parametr v seznamu parametrů, není nutné poskytnout název parametru.</span><span class="sxs-lookup"><span data-stu-id="06535-196">Because `Format` is the first parameter in the parameter list, you do not have to provide the parameter name.</span></span> <span data-ttu-id="06535-197">Příkaz může být však lze snáze pochopit, pokud název parametru je součástí, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="06535-197">However, the statement might be easier to understand if the parameter name is included, as is shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#16)]  
  
2. <span data-ttu-id="06535-198">Stisknutím kláves CTRL + F5 k zobrazení výsledku.</span><span class="sxs-lookup"><span data-stu-id="06535-198">Press CTRL+F5 to see the result.</span></span> <span data-ttu-id="06535-199">Další formáty jsou uvedeny v <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> výčtu.</span><span class="sxs-lookup"><span data-stu-id="06535-199">Other formats are listed in the <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> enumeration.</span></span>  
  
3. <span data-ttu-id="06535-200">Porovnání příkazu v kroku 1 s následujícím kódem, který ukazuje argumenty, které jsou nezbytné C# 3.0 a starší verze.</span><span class="sxs-lookup"><span data-stu-id="06535-200">Compare the statement in step 1 with the following code, which shows the arguments that are required in C# 3.0 and earlier versions.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#17)]  
  
## <a name="example"></a><span data-ttu-id="06535-201">Příklad</span><span class="sxs-lookup"><span data-stu-id="06535-201">Example</span></span>  
 <span data-ttu-id="06535-202">Následující kód ukazuje kompletní příklad.</span><span class="sxs-lookup"><span data-stu-id="06535-202">The following code shows the complete example.</span></span>  
  
 [!code-csharp[csProgGuideOfficeHowTo#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/walkthrough.cs#18)]  
  
## <a name="see-also"></a><span data-ttu-id="06535-203">Viz také:</span><span class="sxs-lookup"><span data-stu-id="06535-203">See also</span></span>

- <xref:System.Type.Missing?displayProperty=nameWithType>
- [<span data-ttu-id="06535-204">dynamic</span><span class="sxs-lookup"><span data-stu-id="06535-204">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)
- [<span data-ttu-id="06535-205">Použití typu dynamic</span><span class="sxs-lookup"><span data-stu-id="06535-205">Using Type dynamic</span></span>](../../../csharp/programming-guide/types/using-type-dynamic.md)
- [<span data-ttu-id="06535-206">Pojmenované a nepovinné argumenty</span><span class="sxs-lookup"><span data-stu-id="06535-206">Named and Optional Arguments</span></span>](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="06535-207">Postupy: Použití pojmenovaných a nepovinných argumentů v programování pro Office</span><span class="sxs-lookup"><span data-stu-id="06535-207">How to: Use Named and Optional Arguments in Office Programming</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
