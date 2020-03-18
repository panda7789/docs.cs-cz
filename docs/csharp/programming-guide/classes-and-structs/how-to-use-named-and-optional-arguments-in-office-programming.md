---
title: Použití pojmenovaných a volitelných argumentů v programovacím programu sady Office – Průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
ms.openlocfilehash: 36b5c8b49404606c8240d24953c3677d5612d30e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714879"
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a><span data-ttu-id="aef2c-102">Použití pojmenovaných a volitelných argumentů v programování sady Office (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="aef2c-102">How to use named and optional arguments in Office programming (C# Programming Guide)</span></span>

<span data-ttu-id="aef2c-103">Pojmenované argumenty a volitelné argumenty, zavedené v jazyce C# 4, zvyšují pohodlí, flexibilitu a čitelnost v programování jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="aef2c-103">Named arguments and optional arguments, introduced in C# 4, enhance convenience, flexibility, and readability in C# programming.</span></span> <span data-ttu-id="aef2c-104">Kromě toho tyto funkce výrazně usnadňují přístup k rozhraním COM, jako jsou rozhraní API automatizace sady Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="aef2c-104">In addition, these features greatly facilitate access to COM interfaces such as the Microsoft Office automation APIs.</span></span>

<span data-ttu-id="aef2c-105">V následujícím příkladu má metoda [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) šestnáct parametrů, které představují charakteristiky tabulky, například počet sloupců a řádků, formátování, ohraničení, písma a barvy.</span><span class="sxs-lookup"><span data-stu-id="aef2c-105">In the following example, method [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) has sixteen parameters that represent characteristics of a table, such as number of columns and rows, formatting, borders, fonts, and colors.</span></span> <span data-ttu-id="aef2c-106">Všech šestnáct parametrů je volitelných, protože většinu času nechcete určit konkrétní hodnoty pro všechny z nich.</span><span class="sxs-lookup"><span data-stu-id="aef2c-106">All sixteen parameters are optional, because most of the time you do not want to specify particular values for all of them.</span></span> <span data-ttu-id="aef2c-107">Bez pojmenovaných a volitelných argumentů však musí být pro každý parametr poskytnuta hodnota nebo zástupná hodnota.</span><span class="sxs-lookup"><span data-stu-id="aef2c-107">However, without named and optional arguments, a value or a placeholder value has to be provided for each parameter.</span></span> <span data-ttu-id="aef2c-108">S pojmenovanými a volitelnými argumenty zadáte hodnoty pouze pro parametry, které jsou požadovány pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="aef2c-108">With named and optional arguments, you specify values only for the parameters that are required for your project.</span></span>

<span data-ttu-id="aef2c-109">K dokončení těchto postupů je třeba mít v počítači nainstalovanou aplikaci Microsoft Office Word.</span><span class="sxs-lookup"><span data-stu-id="aef2c-109">You must have Microsoft Office Word installed on your computer to complete these procedures.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a><span data-ttu-id="aef2c-110">Vytvoření nové konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="aef2c-110">To create a new console application</span></span>

1. <span data-ttu-id="aef2c-111">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aef2c-111">Start Visual Studio.</span></span>

2. <span data-ttu-id="aef2c-112">V nabídce **Soubor** přejděte na **Nový**a potom klepněte na **položku Project**.</span><span class="sxs-lookup"><span data-stu-id="aef2c-112">On the **File** menu, point to **New**, and then click **Project**.</span></span>

3. <span data-ttu-id="aef2c-113">V podokně **Kategorie šablon** rozbalte **položku Visual C#** a klepněte na tlačítko **Windows**.</span><span class="sxs-lookup"><span data-stu-id="aef2c-113">In the **Templates Categories** pane, expand **Visual C#**, and then click **Windows**.</span></span>

4. <span data-ttu-id="aef2c-114">V horní části podokna **Šablony** se ujistěte, že se rozhraní **.NET Framework 4** zobrazí v poli **Cílová architektura.**</span><span class="sxs-lookup"><span data-stu-id="aef2c-114">Look in the top of the **Templates** pane to make sure that **.NET Framework 4** appears in the **Target Framework** box.</span></span>

5. <span data-ttu-id="aef2c-115">V podokně **Šablony** klepněte na položku **Konzolová aplikace**.</span><span class="sxs-lookup"><span data-stu-id="aef2c-115">In the **Templates** pane, click **Console Application**.</span></span>

6. <span data-ttu-id="aef2c-116">Do pole **Název** zadejte název projektu.</span><span class="sxs-lookup"><span data-stu-id="aef2c-116">Type a name for your project in the **Name** field.</span></span>

7. <span data-ttu-id="aef2c-117">Klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="aef2c-117">Click **OK**.</span></span>

     <span data-ttu-id="aef2c-118">Nový projekt se zobrazí v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="aef2c-118">The new project appears in **Solution Explorer**.</span></span>

## <a name="to-add-a-reference"></a><span data-ttu-id="aef2c-119">Přidání odkazu</span><span class="sxs-lookup"><span data-stu-id="aef2c-119">To add a reference</span></span>

1. <span data-ttu-id="aef2c-120">V **Průzkumníku řešení**klikněte pravým tlačítkem myši na název projektu a potom klikněte na **příkaz Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="aef2c-120">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="aef2c-121">Zobrazí se dialogové okno **Přidat odkaz.**</span><span class="sxs-lookup"><span data-stu-id="aef2c-121">The **Add Reference** dialog box appears.</span></span>

2. <span data-ttu-id="aef2c-122">Na stránce **.NET** vyberte v seznamu **Název součásti** **položku Microsoft.Office.Interop.Word.**</span><span class="sxs-lookup"><span data-stu-id="aef2c-122">On the **.NET** page, select **Microsoft.Office.Interop.Word** in the **Component Name** list.</span></span>

3. <span data-ttu-id="aef2c-123">Klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="aef2c-123">Click **OK**.</span></span>

## <a name="to-add-necessary-using-directives"></a><span data-ttu-id="aef2c-124">Chcete-li přidat nezbytné pomocí směrnic</span><span class="sxs-lookup"><span data-stu-id="aef2c-124">To add necessary using directives</span></span>

1. <span data-ttu-id="aef2c-125">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na *soubor Program.cs* a potom klepněte na příkaz Zobrazit **kód**.</span><span class="sxs-lookup"><span data-stu-id="aef2c-125">In **Solution Explorer**, right-click the *Program.cs* file and then click **View Code**.</span></span>

2. <span data-ttu-id="aef2c-126">Do horní `using` části souboru kódu přidejte následující direktivy:</span><span class="sxs-lookup"><span data-stu-id="aef2c-126">Add the following `using` directives to the top of the code file:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#4)]

## <a name="to-display-text-in-a-word-document"></a><span data-ttu-id="aef2c-127">Zobrazení textu ve wordovém dokumentu</span><span class="sxs-lookup"><span data-stu-id="aef2c-127">To display text in a Word document</span></span>

1. <span data-ttu-id="aef2c-128">Do `Program` třídy v *Program.cs*přidejte následující metodu k vytvoření aplikace Word a dokumentu aplikace Word.</span><span class="sxs-lookup"><span data-stu-id="aef2c-128">In the `Program` class in *Program.cs*, add the following method to create a Word application and a Word document.</span></span> <span data-ttu-id="aef2c-129">Metoda [Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) má čtyři volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="aef2c-129">The [Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) method has four optional parameters.</span></span> <span data-ttu-id="aef2c-130">Tento příklad používá jejich výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="aef2c-130">This example uses their default values.</span></span> <span data-ttu-id="aef2c-131">Proto žádné argumenty jsou nezbytné v volání příkazu.</span><span class="sxs-lookup"><span data-stu-id="aef2c-131">Therefore, no arguments are necessary in the calling statement.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#6)]

2. <span data-ttu-id="aef2c-132">Na konec metody přidejte následující kód, který definuje, kde se má v dokumentu zobrazit text a jaký text se má zobrazit:</span><span class="sxs-lookup"><span data-stu-id="aef2c-132">Add the following code at the end of the method to define where to display text in the document, and what text to display:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#7)]

## <a name="to-run-the-application"></a><span data-ttu-id="aef2c-133">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="aef2c-133">To run the application</span></span>

1. <span data-ttu-id="aef2c-134">Do hlavního příkazu přidejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="aef2c-134">Add the following statement to Main:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#8)]

2. <span data-ttu-id="aef2c-135">Spuštění projektu stisknutím <kbd>klávesy CTRL</kbd>+<kbd>F5.</kbd></span><span class="sxs-lookup"><span data-stu-id="aef2c-135">Press <kbd>CTRL</kbd>+<kbd>F5</kbd> to run the project.</span></span> <span data-ttu-id="aef2c-136">Zobrazí se dokument aplikace Word, který obsahuje zadaný text.</span><span class="sxs-lookup"><span data-stu-id="aef2c-136">A Word document appears that contains the specified text.</span></span>

## <a name="to-change-the-text-to-a-table"></a><span data-ttu-id="aef2c-137">Změna textu na tabulku</span><span class="sxs-lookup"><span data-stu-id="aef2c-137">To change the text to a table</span></span>
  
1. <span data-ttu-id="aef2c-138">Pomocí `ConvertToTable` metody uzavřete text do tabulky.</span><span class="sxs-lookup"><span data-stu-id="aef2c-138">Use the `ConvertToTable` method to enclose the text in a table.</span></span> <span data-ttu-id="aef2c-139">Metoda má šestnáct volitelných parametrů.</span><span class="sxs-lookup"><span data-stu-id="aef2c-139">The method has sixteen optional parameters.</span></span> <span data-ttu-id="aef2c-140">Technologie IntelliSense uzavře volitelné parametry do závorek, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="aef2c-140">IntelliSense encloses optional parameters in brackets, as shown in the following illustration.</span></span>

     ![Seznam parametrů pro metodu ConvertToTable](./media/how-to-use-named-and-optional-arguments-in-office-programming/convert-table-parameters.png)

     <span data-ttu-id="aef2c-142">Pojmenované a volitelné argumenty umožňují zadat hodnoty pouze pro parametry, které chcete změnit.</span><span class="sxs-lookup"><span data-stu-id="aef2c-142">Named and optional arguments enable you to specify values for only the parameters that you want to change.</span></span> <span data-ttu-id="aef2c-143">Přidejte následující kód na `DisplayInWord` konec metody a vytvořte jednoduchou tabulku.</span><span class="sxs-lookup"><span data-stu-id="aef2c-143">Add the following code to the end of method `DisplayInWord` to create a simple table.</span></span> <span data-ttu-id="aef2c-144">Argument určuje, že čárky v textovém `range` řetězci v samostatné buňky tabulky.</span><span class="sxs-lookup"><span data-stu-id="aef2c-144">The argument specifies that the commas in the text string in `range` separate the cells of the table.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#9)]

     <span data-ttu-id="aef2c-145">V dřívějších verzích jazyka C# `ConvertToTable` vyžaduje volání pro každý parametr referenční argument, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="aef2c-145">In earlier versions of C#, the call to `ConvertToTable` requires a reference argument for each parameter, as shown in the following code:</span></span>
  
     [!code-csharp[csProgGuideNamedAndOptional#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#14)]

2. <span data-ttu-id="aef2c-146">Spuštění projektu stisknutím <kbd>klávesy CTRL</kbd>+<kbd>F5.</kbd></span><span class="sxs-lookup"><span data-stu-id="aef2c-146">Press <kbd>CTRL</kbd>+<kbd>F5</kbd> to run the project.</span></span>

## <a name="to-experiment-with-other-parameters"></a><span data-ttu-id="aef2c-147">Experimentovat s dalšími parametry</span><span class="sxs-lookup"><span data-stu-id="aef2c-147">To experiment with other parameters</span></span>

1. <span data-ttu-id="aef2c-148">Chcete-li tabulku změnit tak, aby byla mít jeden `DisplayInWord` sloupec a tři řádky, nahraďte poslední řádek v tabulce následujícím příkazem a zadejte <kbd>kombinaci kláves CTRL</kbd>+<kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="aef2c-148">To change the table so that it has one column and three rows, replace the last line in `DisplayInWord` with the following statement and then type <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span>  

     [!code-csharp[csProgGuideNamedAndOptional#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#10)]

2. <span data-ttu-id="aef2c-149">Chcete-li určit předdefinovaný formát tabulky, nahraďte poslední řádek v s `DisplayInWord` následujícím příkazem a zadejte <kbd>kombinaci kláves CTRL</kbd>+<kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="aef2c-149">To specify a predefined format for the table, replace the last line in `DisplayInWord` with the following statement and then type <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span> <span data-ttu-id="aef2c-150">Formát může být libovolná z konstant [WdTableFormat.](<xref:Microsoft.Office.Interop.Word.WdTableFormat>)</span><span class="sxs-lookup"><span data-stu-id="aef2c-150">The format can be any of the [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) constants.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#11)]

## <a name="example"></a><span data-ttu-id="aef2c-151">Příklad</span><span class="sxs-lookup"><span data-stu-id="aef2c-151">Example</span></span>

<span data-ttu-id="aef2c-152">Následující kód obsahuje úplný příklad:</span><span class="sxs-lookup"><span data-stu-id="aef2c-152">The following code includes the full example:</span></span>

 [!code-csharp[csProgGuideNamedAndOptional#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#12)]

## <a name="see-also"></a><span data-ttu-id="aef2c-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="aef2c-153">See also</span></span>

- [<span data-ttu-id="aef2c-154">Pojmenované a nepovinné argumenty</span><span class="sxs-lookup"><span data-stu-id="aef2c-154">Named and Optional Arguments</span></span>](./named-and-optional-arguments.md)
