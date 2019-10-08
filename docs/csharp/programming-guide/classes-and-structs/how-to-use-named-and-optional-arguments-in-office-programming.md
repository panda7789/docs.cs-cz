---
title: 'Postupy: použití pojmenovaných a nepovinných argumentů v C# programování pro systém Office – Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
ms.openlocfilehash: 90b60a6410ffbe7f9802b01bf3303b6e842a1424
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002786"
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a><span data-ttu-id="ce12e-102">Postupy: Použití pojmenovaných a nepovinných argumentů v programování pro sadu Office (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="ce12e-102">How to: Use Named and Optional Arguments in Office Programming (C# Programming Guide)</span></span>

<span data-ttu-id="ce12e-103">Pojmenované argumenty a volitelné argumenty, představené C# ve 4, zvyšují pohodlí, flexibilitu a čitelnost při C# programování.</span><span class="sxs-lookup"><span data-stu-id="ce12e-103">Named arguments and optional arguments, introduced in C# 4, enhance convenience, flexibility, and readability in C# programming.</span></span> <span data-ttu-id="ce12e-104">Kromě toho tyto funkce významně usnadňují přístup k rozhraním COM, jako jsou systém Microsoft Office rozhraní API pro automatizaci.</span><span class="sxs-lookup"><span data-stu-id="ce12e-104">In addition, these features greatly facilitate access to COM interfaces such as the Microsoft Office automation APIs.</span></span>

<span data-ttu-id="ce12e-105">V následujícím příkladu má metoda [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) šestnáct parametrů, které reprezentují vlastnosti tabulky, jako je počet sloupců a řádků, formátování, ohraničení, písma a barvy.</span><span class="sxs-lookup"><span data-stu-id="ce12e-105">In the following example, method [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) has sixteen parameters that represent characteristics of a table, such as number of columns and rows, formatting, borders, fonts, and colors.</span></span> <span data-ttu-id="ce12e-106">Všechny šestnácté parametry jsou volitelné, protože většina času neumožňuje zadat konkrétní hodnoty pro všechny.</span><span class="sxs-lookup"><span data-stu-id="ce12e-106">All sixteen parameters are optional, because most of the time you do not want to specify particular values for all of them.</span></span> <span data-ttu-id="ce12e-107">Bez pojmenovaných a nepovinných argumentů však musí být pro každý parametr zadána hodnota nebo zástupný symbol.</span><span class="sxs-lookup"><span data-stu-id="ce12e-107">However, without named and optional arguments, a value or a placeholder value has to be provided for each parameter.</span></span> <span data-ttu-id="ce12e-108">U pojmenovaných a nepovinných argumentů zadáte hodnoty pouze pro parametry, které jsou požadovány pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="ce12e-108">With named and optional arguments, you specify values only for the parameters that are required for your project.</span></span>

<span data-ttu-id="ce12e-109">Aby bylo možné dokončit tyto postupy, je nutné, aby byl v počítači nainstalován systém Microsoft Office Word.</span><span class="sxs-lookup"><span data-stu-id="ce12e-109">You must have Microsoft Office Word installed on your computer to complete these procedures.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a><span data-ttu-id="ce12e-110">Vytvoření nové konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="ce12e-110">To create a new console application</span></span>

1. <span data-ttu-id="ce12e-111">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ce12e-111">Start Visual Studio.</span></span>

2. <span data-ttu-id="ce12e-112">V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**.</span><span class="sxs-lookup"><span data-stu-id="ce12e-112">On the **File** menu, point to **New**, and then click **Project**.</span></span>

3. <span data-ttu-id="ce12e-113">V podokně **Kategorie šablon** rozbalte položku **vizuál C#** a potom klikněte na možnost **Windows**.</span><span class="sxs-lookup"><span data-stu-id="ce12e-113">In the **Templates Categories** pane, expand **Visual C#**, and then click **Windows**.</span></span>

4. <span data-ttu-id="ce12e-114">Podívejte se v horní části podokna **šablony** , abyste se ujistili, že se v poli **cílová architektura** zobrazí **.NET Framework 4** .</span><span class="sxs-lookup"><span data-stu-id="ce12e-114">Look in the top of the **Templates** pane to make sure that **.NET Framework 4** appears in the **Target Framework** box.</span></span>

5. <span data-ttu-id="ce12e-115">V podokně **šablony** klikněte na **Konzolová aplikace**.</span><span class="sxs-lookup"><span data-stu-id="ce12e-115">In the **Templates** pane, click **Console Application**.</span></span>

6. <span data-ttu-id="ce12e-116">Do pole **název** zadejte název projektu.</span><span class="sxs-lookup"><span data-stu-id="ce12e-116">Type a name for your project in the **Name** field.</span></span>

7. <span data-ttu-id="ce12e-117">Klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="ce12e-117">Click **OK**.</span></span>

     <span data-ttu-id="ce12e-118">Nový projekt se zobrazí v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="ce12e-118">The new project appears in **Solution Explorer**.</span></span>

## <a name="to-add-a-reference"></a><span data-ttu-id="ce12e-119">Přidání odkazu</span><span class="sxs-lookup"><span data-stu-id="ce12e-119">To add a reference</span></span>

1. <span data-ttu-id="ce12e-120">V **Průzkumník řešení**klikněte pravým tlačítkem myši na název projektu a pak klikněte na **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="ce12e-120">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="ce12e-121">Zobrazí se dialogové okno **Přidat odkaz** .</span><span class="sxs-lookup"><span data-stu-id="ce12e-121">The **Add Reference** dialog box appears.</span></span>

2. <span data-ttu-id="ce12e-122">Na stránce **.NET** vyberte v seznamu **název součásti** možnost **Microsoft. Office. Interop. Word** .</span><span class="sxs-lookup"><span data-stu-id="ce12e-122">On the **.NET** page, select **Microsoft.Office.Interop.Word** in the **Component Name** list.</span></span>

3. <span data-ttu-id="ce12e-123">Klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="ce12e-123">Click **OK**.</span></span>

## <a name="to-add-necessary-using-directives"></a><span data-ttu-id="ce12e-124">Přidání nezbytných direktiv using</span><span class="sxs-lookup"><span data-stu-id="ce12e-124">To add necessary using directives</span></span>

1. <span data-ttu-id="ce12e-125">V **Průzkumník řešení**klikněte pravým tlačítkem na soubor *program.cs* a pak klikněte na **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="ce12e-125">In **Solution Explorer**, right-click the *Program.cs* file and then click **View Code**.</span></span>

2. <span data-ttu-id="ce12e-126">Přidejte následující direktivy `using` do horní části souboru kódu:</span><span class="sxs-lookup"><span data-stu-id="ce12e-126">Add the following `using` directives to the top of the code file:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#4)]

## <a name="to-display-text-in-a-word-document"></a><span data-ttu-id="ce12e-127">Zobrazení textu v dokumentu aplikace Word</span><span class="sxs-lookup"><span data-stu-id="ce12e-127">To display text in a Word document</span></span>

1. <span data-ttu-id="ce12e-128">Do třídy `Program` v *program.cs*přidejte následující metodu pro vytvoření aplikace Word a wordového dokumentu.</span><span class="sxs-lookup"><span data-stu-id="ce12e-128">In the `Program` class in *Program.cs*, add the following method to create a Word application and a Word document.</span></span> <span data-ttu-id="ce12e-129">Metoda [Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) má čtyři volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="ce12e-129">The [Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) method has four optional parameters.</span></span> <span data-ttu-id="ce12e-130">V tomto příkladu se používají výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ce12e-130">This example uses their default values.</span></span> <span data-ttu-id="ce12e-131">Proto nejsou v příkazu call nutné žádné argumenty.</span><span class="sxs-lookup"><span data-stu-id="ce12e-131">Therefore, no arguments are necessary in the calling statement.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#6)]

2. <span data-ttu-id="ce12e-132">Na konec metody přidejte následující kód, který definuje, kde se má v dokumentu zobrazovat text, a zobrazený text:</span><span class="sxs-lookup"><span data-stu-id="ce12e-132">Add the following code at the end of the method to define where to display text in the document, and what text to display:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#7)]

## <a name="to-run-the-application"></a><span data-ttu-id="ce12e-133">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="ce12e-133">To run the application</span></span>

1. <span data-ttu-id="ce12e-134">Přidejte následující příkaz do Main:</span><span class="sxs-lookup"><span data-stu-id="ce12e-134">Add the following statement to Main:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#8)]

2. <span data-ttu-id="ce12e-135">Stisknutím <kbd>kombinace kláves CTRL</kbd>+<kbd>F5</kbd> spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="ce12e-135">Press <kbd>CTRL</kbd>+<kbd>F5</kbd> to run the project.</span></span> <span data-ttu-id="ce12e-136">Zobrazí se dokument aplikace Word obsahující zadaný text.</span><span class="sxs-lookup"><span data-stu-id="ce12e-136">A Word document appears that contains the specified text.</span></span>

## <a name="to-change-the-text-to-a-table"></a><span data-ttu-id="ce12e-137">Změna textu na tabulku</span><span class="sxs-lookup"><span data-stu-id="ce12e-137">To change the text to a table</span></span>
  
1. <span data-ttu-id="ce12e-138">K uzavření textu v tabulce použijte metodu `ConvertToTable`.</span><span class="sxs-lookup"><span data-stu-id="ce12e-138">Use the `ConvertToTable` method to enclose the text in a table.</span></span> <span data-ttu-id="ce12e-139">Metoda má 16 nepovinných parametrů.</span><span class="sxs-lookup"><span data-stu-id="ce12e-139">The method has sixteen optional parameters.</span></span> <span data-ttu-id="ce12e-140">IntelliSense vloží volitelné parametry do závorek, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="ce12e-140">IntelliSense encloses optional parameters in brackets, as shown in the following illustration.</span></span>

     ![Seznam parametrů pro metodu ConvertToTable](./media/how-to-use-named-and-optional-arguments-in-office-programming/convert-table-parameters.png)

     <span data-ttu-id="ce12e-142">Pojmenované a volitelné argumenty umožňují zadat hodnoty pouze pro parametry, které chcete změnit.</span><span class="sxs-lookup"><span data-stu-id="ce12e-142">Named and optional arguments enable you to specify values for only the parameters that you want to change.</span></span> <span data-ttu-id="ce12e-143">Přidejte následující kód na konec metody `DisplayInWord` pro vytvoření jednoduché tabulky.</span><span class="sxs-lookup"><span data-stu-id="ce12e-143">Add the following code to the end of method `DisplayInWord` to create a simple table.</span></span> <span data-ttu-id="ce12e-144">Argument určuje, že čárky v textovém řetězci v `range` oddělují buňky tabulky.</span><span class="sxs-lookup"><span data-stu-id="ce12e-144">The argument specifies that the commas in the text string in `range` separate the cells of the table.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#9)]

     <span data-ttu-id="ce12e-145">V dřívějších verzích C#nástroje volání `ConvertToTable` vyžaduje argument odkazu pro každý parametr, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="ce12e-145">In earlier versions of C#, the call to `ConvertToTable` requires a reference argument for each parameter, as shown in the following code:</span></span>
  
     [!code-csharp[csProgGuideNamedAndOptional#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#14)]

2. <span data-ttu-id="ce12e-146">Stisknutím <kbd>kombinace kláves CTRL</kbd>+<kbd>F5</kbd> spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="ce12e-146">Press <kbd>CTRL</kbd>+<kbd>F5</kbd> to run the project.</span></span>

## <a name="to-experiment-with-other-parameters"></a><span data-ttu-id="ce12e-147">Experimentování s jinými parametry</span><span class="sxs-lookup"><span data-stu-id="ce12e-147">To experiment with other parameters</span></span>

1. <span data-ttu-id="ce12e-148">Chcete-li změnit tabulku tak, aby měla jeden sloupec a tři řádky, nahraďte poslední řádek v `DisplayInWord` následujícím příkazem a zadejte <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="ce12e-148">To change the table so that it has one column and three rows, replace the last line in `DisplayInWord` with the following statement and then type <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span>  

     [!code-csharp[csProgGuideNamedAndOptional#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#10)]

2. <span data-ttu-id="ce12e-149">Chcete-li zadat předdefinovaný formát tabulky, nahraďte poslední řádek v `DisplayInWord` následujícím příkazem a potom zadejte <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="ce12e-149">To specify a predefined format for the table, replace the last line in `DisplayInWord` with the following statement and then type <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span> <span data-ttu-id="ce12e-150">Formát může být libovolná konstanta [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) .</span><span class="sxs-lookup"><span data-stu-id="ce12e-150">The format can be any of the [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) constants.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#11)]

## <a name="example"></a><span data-ttu-id="ce12e-151">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce12e-151">Example</span></span>

<span data-ttu-id="ce12e-152">Následující kód obsahuje úplný příklad:</span><span class="sxs-lookup"><span data-stu-id="ce12e-152">The following code includes the full example:</span></span>

 [!code-csharp[csProgGuideNamedAndOptional#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#12)]

## <a name="see-also"></a><span data-ttu-id="ce12e-153">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ce12e-153">See also</span></span>

- [<span data-ttu-id="ce12e-154">Pojmenované a nepovinné argumenty</span><span class="sxs-lookup"><span data-stu-id="ce12e-154">Named and Optional Arguments</span></span>](./named-and-optional-arguments.md)
