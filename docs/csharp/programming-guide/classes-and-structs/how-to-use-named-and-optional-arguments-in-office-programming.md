---
title: Použití pojmenovaných a nepovinných argumentů v programování pro systém Office – Průvodce programováním v C#
description: Naučte se používat pojmenované argumenty a volitelné argumenty pro usnadnění přístupu k rozhraním COM, jako jsou systém Microsoft Office rozhraní API pro automatizaci.
ms.date: 07/20/2015
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
ms.openlocfilehash: 7e24331d37e8fdbe2bc66a2d9f73a5f6a7242af9
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864342"
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a><span data-ttu-id="399cb-103">Použití pojmenovaných a nepovinných argumentů v programování pro systém Office (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="399cb-103">How to use named and optional arguments in Office programming (C# Programming Guide)</span></span>

<span data-ttu-id="399cb-104">Pojmenované argumenty a nepovinné argumenty, představené v C# 4, vylepšují pohodlí, flexibilitu a čitelnost v programování v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="399cb-104">Named arguments and optional arguments, introduced in C# 4, enhance convenience, flexibility, and readability in C# programming.</span></span> <span data-ttu-id="399cb-105">Kromě toho tyto funkce významně usnadňují přístup k rozhraním COM, jako jsou systém Microsoft Office rozhraní API pro automatizaci.</span><span class="sxs-lookup"><span data-stu-id="399cb-105">In addition, these features greatly facilitate access to COM interfaces such as the Microsoft Office automation APIs.</span></span>

<span data-ttu-id="399cb-106">V následujícím příkladu má metoda [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) šestnáct parametrů, které reprezentují vlastnosti tabulky, jako je počet sloupců a řádků, formátování, ohraničení, písma a barvy.</span><span class="sxs-lookup"><span data-stu-id="399cb-106">In the following example, method [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) has sixteen parameters that represent characteristics of a table, such as number of columns and rows, formatting, borders, fonts, and colors.</span></span> <span data-ttu-id="399cb-107">Všechny šestnácté parametry jsou volitelné, protože většina času neumožňuje zadat konkrétní hodnoty pro všechny.</span><span class="sxs-lookup"><span data-stu-id="399cb-107">All sixteen parameters are optional, because most of the time you do not want to specify particular values for all of them.</span></span> <span data-ttu-id="399cb-108">Bez pojmenovaných a nepovinných argumentů však musí být pro každý parametr zadána hodnota nebo zástupný symbol.</span><span class="sxs-lookup"><span data-stu-id="399cb-108">However, without named and optional arguments, a value or a placeholder value has to be provided for each parameter.</span></span> <span data-ttu-id="399cb-109">U pojmenovaných a nepovinných argumentů zadáte hodnoty pouze pro parametry, které jsou požadovány pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="399cb-109">With named and optional arguments, you specify values only for the parameters that are required for your project.</span></span>

<span data-ttu-id="399cb-110">Aby bylo možné dokončit tyto postupy, je nutné, aby byl v počítači nainstalován systém Microsoft Office Word.</span><span class="sxs-lookup"><span data-stu-id="399cb-110">You must have Microsoft Office Word installed on your computer to complete these procedures.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a><span data-ttu-id="399cb-111">Vytvoření nové konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="399cb-111">To create a new console application</span></span>

1. <span data-ttu-id="399cb-112">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="399cb-112">Start Visual Studio.</span></span>

2. <span data-ttu-id="399cb-113">V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**.</span><span class="sxs-lookup"><span data-stu-id="399cb-113">On the **File** menu, point to **New**, and then click **Project**.</span></span>

3. <span data-ttu-id="399cb-114">V podokně **Kategorie šablon** rozbalte položku **Visual C#** a potom klikněte na možnost **Windows**.</span><span class="sxs-lookup"><span data-stu-id="399cb-114">In the **Templates Categories** pane, expand **Visual C#**, and then click **Windows**.</span></span>

4. <span data-ttu-id="399cb-115">Podívejte se v horní části podokna **šablony** , abyste se ujistili, že se v poli **cílová architektura** zobrazí **.NET Framework 4** .</span><span class="sxs-lookup"><span data-stu-id="399cb-115">Look in the top of the **Templates** pane to make sure that **.NET Framework 4** appears in the **Target Framework** box.</span></span>

5. <span data-ttu-id="399cb-116">V podokně **šablony** klikněte na **Konzolová aplikace**.</span><span class="sxs-lookup"><span data-stu-id="399cb-116">In the **Templates** pane, click **Console Application**.</span></span>

6. <span data-ttu-id="399cb-117">Do pole **název** zadejte název projektu.</span><span class="sxs-lookup"><span data-stu-id="399cb-117">Type a name for your project in the **Name** field.</span></span>

7. <span data-ttu-id="399cb-118">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="399cb-118">Click **OK**.</span></span>

     <span data-ttu-id="399cb-119">Nový projekt se zobrazí v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="399cb-119">The new project appears in **Solution Explorer**.</span></span>

## <a name="to-add-a-reference"></a><span data-ttu-id="399cb-120">Přidání odkazu</span><span class="sxs-lookup"><span data-stu-id="399cb-120">To add a reference</span></span>

1. <span data-ttu-id="399cb-121">V **Průzkumník řešení**klikněte pravým tlačítkem myši na název projektu a pak klikněte na **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="399cb-121">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="399cb-122">Zobrazí se dialogové okno **Přidat odkaz** .</span><span class="sxs-lookup"><span data-stu-id="399cb-122">The **Add Reference** dialog box appears.</span></span>

2. <span data-ttu-id="399cb-123">Na stránce **.NET** vyberte v seznamu **název součásti** možnost **Microsoft. Office. Interop. Word** .</span><span class="sxs-lookup"><span data-stu-id="399cb-123">On the **.NET** page, select **Microsoft.Office.Interop.Word** in the **Component Name** list.</span></span>

3. <span data-ttu-id="399cb-124">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="399cb-124">Click **OK**.</span></span>

## <a name="to-add-necessary-using-directives"></a><span data-ttu-id="399cb-125">Přidání nezbytných direktiv using</span><span class="sxs-lookup"><span data-stu-id="399cb-125">To add necessary using directives</span></span>

1. <span data-ttu-id="399cb-126">V **Průzkumník řešení**klikněte pravým tlačítkem na soubor *program.cs* a pak klikněte na **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="399cb-126">In **Solution Explorer**, right-click the *Program.cs* file and then click **View Code**.</span></span>

2. <span data-ttu-id="399cb-127">`using`Do horní části souboru kódu přidejte následující direktivy:</span><span class="sxs-lookup"><span data-stu-id="399cb-127">Add the following `using` directives to the top of the code file:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#4)]

## <a name="to-display-text-in-a-word-document"></a><span data-ttu-id="399cb-128">Zobrazení textu v dokumentu aplikace Word</span><span class="sxs-lookup"><span data-stu-id="399cb-128">To display text in a Word document</span></span>

1. <span data-ttu-id="399cb-129">Do `Program` třídy v *program.cs*přidejte následující metodu pro vytvoření aplikace Word a wordového dokumentu.</span><span class="sxs-lookup"><span data-stu-id="399cb-129">In the `Program` class in *Program.cs*, add the following method to create a Word application and a Word document.</span></span> <span data-ttu-id="399cb-130">Metoda [Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) má čtyři volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="399cb-130">The [Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) method has four optional parameters.</span></span> <span data-ttu-id="399cb-131">V tomto příkladu se používají výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="399cb-131">This example uses their default values.</span></span> <span data-ttu-id="399cb-132">Proto nejsou v příkazu call nutné žádné argumenty.</span><span class="sxs-lookup"><span data-stu-id="399cb-132">Therefore, no arguments are necessary in the calling statement.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#6)]

2. <span data-ttu-id="399cb-133">Na konec metody přidejte následující kód, který definuje, kde se má v dokumentu zobrazovat text, a zobrazený text:</span><span class="sxs-lookup"><span data-stu-id="399cb-133">Add the following code at the end of the method to define where to display text in the document, and what text to display:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#7)]

## <a name="to-run-the-application"></a><span data-ttu-id="399cb-134">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="399cb-134">To run the application</span></span>

1. <span data-ttu-id="399cb-135">Přidejte následující příkaz do Main:</span><span class="sxs-lookup"><span data-stu-id="399cb-135">Add the following statement to Main:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#8)]

2. <span data-ttu-id="399cb-136">Stisknutím klávesy <kbd>CTRL</kbd> + <kbd>F5</kbd> spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="399cb-136">Press <kbd>CTRL</kbd>+<kbd>F5</kbd> to run the project.</span></span> <span data-ttu-id="399cb-137">Zobrazí se dokument aplikace Word obsahující zadaný text.</span><span class="sxs-lookup"><span data-stu-id="399cb-137">A Word document appears that contains the specified text.</span></span>

## <a name="to-change-the-text-to-a-table"></a><span data-ttu-id="399cb-138">Změna textu na tabulku</span><span class="sxs-lookup"><span data-stu-id="399cb-138">To change the text to a table</span></span>
  
1. <span data-ttu-id="399cb-139">`ConvertToTable`K uzavření textu v tabulce použijte metodu.</span><span class="sxs-lookup"><span data-stu-id="399cb-139">Use the `ConvertToTable` method to enclose the text in a table.</span></span> <span data-ttu-id="399cb-140">Metoda má 16 nepovinných parametrů.</span><span class="sxs-lookup"><span data-stu-id="399cb-140">The method has sixteen optional parameters.</span></span> <span data-ttu-id="399cb-141">IntelliSense vloží volitelné parametry do závorek, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="399cb-141">IntelliSense encloses optional parameters in brackets, as shown in the following illustration.</span></span>

     ![Seznam parametrů pro metodu ConvertToTable](./media/how-to-use-named-and-optional-arguments-in-office-programming/convert-table-parameters.png)

     <span data-ttu-id="399cb-143">Pojmenované a volitelné argumenty umožňují zadat hodnoty pouze pro parametry, které chcete změnit.</span><span class="sxs-lookup"><span data-stu-id="399cb-143">Named and optional arguments enable you to specify values for only the parameters that you want to change.</span></span> <span data-ttu-id="399cb-144">Přidejte následující kód na konec metody `DisplayInWord` pro vytvoření jednoduché tabulky.</span><span class="sxs-lookup"><span data-stu-id="399cb-144">Add the following code to the end of method `DisplayInWord` to create a simple table.</span></span> <span data-ttu-id="399cb-145">Argument určuje, že čárky v textovém řetězci jsou `range` oddělené buňkami v tabulce.</span><span class="sxs-lookup"><span data-stu-id="399cb-145">The argument specifies that the commas in the text string in `range` separate the cells of the table.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#9)]

     <span data-ttu-id="399cb-146">V dřívějších verzích jazyka C# volání `ConvertToTable` vyžaduje pro každý parametr odkazový argument, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="399cb-146">In earlier versions of C#, the call to `ConvertToTable` requires a reference argument for each parameter, as shown in the following code:</span></span>
  
     [!code-csharp[csProgGuideNamedAndOptional#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#14)]

2. <span data-ttu-id="399cb-147">Stisknutím klávesy <kbd>CTRL</kbd> + <kbd>F5</kbd> spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="399cb-147">Press <kbd>CTRL</kbd>+<kbd>F5</kbd> to run the project.</span></span>

## <a name="to-experiment-with-other-parameters"></a><span data-ttu-id="399cb-148">Experimentování s jinými parametry</span><span class="sxs-lookup"><span data-stu-id="399cb-148">To experiment with other parameters</span></span>

1. <span data-ttu-id="399cb-149">Chcete-li změnit tabulku tak, aby měla jeden sloupec a tři řádky, nahraďte poslední řádek v `DisplayInWord` následujícím příkazem a zadejte <kbd>klávesu CTRL</kbd> + <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="399cb-149">To change the table so that it has one column and three rows, replace the last line in `DisplayInWord` with the following statement and then type <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span>  

     [!code-csharp[csProgGuideNamedAndOptional#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#10)]

2. <span data-ttu-id="399cb-150">Chcete-li pro tabulku zadat předdefinovaný formát, nahraďte poslední řádek příkazem `DisplayInWord` následujícím příkazem a zadejte <kbd>klávesu CTRL</kbd> + <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="399cb-150">To specify a predefined format for the table, replace the last line in `DisplayInWord` with the following statement and then type <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span> <span data-ttu-id="399cb-151">Formát může být libovolná konstanta [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) .</span><span class="sxs-lookup"><span data-stu-id="399cb-151">The format can be any of the [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) constants.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#11)]

## <a name="example"></a><span data-ttu-id="399cb-152">Příklad</span><span class="sxs-lookup"><span data-stu-id="399cb-152">Example</span></span>

<span data-ttu-id="399cb-153">Následující kód obsahuje úplný příklad:</span><span class="sxs-lookup"><span data-stu-id="399cb-153">The following code includes the full example:</span></span>

 [!code-csharp[csProgGuideNamedAndOptional#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#12)]

## <a name="see-also"></a><span data-ttu-id="399cb-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="399cb-154">See also</span></span>

- [<span data-ttu-id="399cb-155">Pojmenované a nepovinné argumenty</span><span class="sxs-lookup"><span data-stu-id="399cb-155">Named and Optional Arguments</span></span>](./named-and-optional-arguments.md)
