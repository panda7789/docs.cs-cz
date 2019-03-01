---
title: 'Postupy: Použití pojmenovaných a nepovinných argumentů v programování pro sadu Office – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
ms.openlocfilehash: af5f2d13365a93e758962daea2b08ea3ae089aeb
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966798"
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a><span data-ttu-id="7d87e-102">Postupy: Použití pojmenovaných a nepovinných argumentů v programování pro Office (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="7d87e-102">How to: Use Named and Optional Arguments in Office Programming (C# Programming Guide)</span></span>
<span data-ttu-id="7d87e-103">Pojmenované argumenty a nepovinné argumenty, počínaje [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], zvyšuje pohodlí, flexibilitu a lepší čitelnost v programování v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="7d87e-103">Named arguments and optional arguments, introduced in [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], enhance convenience, flexibility, and readability in C# programming.</span></span> <span data-ttu-id="7d87e-104">Kromě toho tyto funkce výrazně usnadňují přístup k rozhraní modelu COM, jako je například rozhraní API automatizace Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="7d87e-104">In addition, these features greatly facilitate access to COM interfaces such as the Microsoft Office automation APIs.</span></span>  
  
 <span data-ttu-id="7d87e-105">V následujícím příkladu metoda [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) má šestnáct parametry, které představují vlastnosti tabulky, například počet sloupců a řádků, formátování, ohraničení, písma a barvy.</span><span class="sxs-lookup"><span data-stu-id="7d87e-105">In the following example, method [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) has sixteen parameters that represent characteristics of a table, such as number of columns and rows, formatting, borders, fonts, and colors.</span></span> <span data-ttu-id="7d87e-106">Všechny šestnáct parametry jsou volitelné, protože ve většině případů nechcete zadat konkrétní hodnoty pro všechny z nich.</span><span class="sxs-lookup"><span data-stu-id="7d87e-106">All sixteen parameters are optional, because most of the time you do not want to specify particular values for all of them.</span></span> <span data-ttu-id="7d87e-107">Ale bez pojmenované a nepovinné argumenty, hodnotu nebo hodnotu zástupného symbolu musí být k dispozici pro každý parametr.</span><span class="sxs-lookup"><span data-stu-id="7d87e-107">However, without named and optional arguments, a value or a placeholder value has to be provided for each parameter.</span></span> <span data-ttu-id="7d87e-108">U pojmenovaných a nepovinných argumentů můžete zadat pouze hodnoty parametrů, které jsou požadovány pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="7d87e-108">With named and optional arguments, you specify values only for the parameters that are required for your project.</span></span>  
  
 <span data-ttu-id="7d87e-109">Musíte mít aplikaci Microsoft Office Word nainstalována v počítači pro dokončení těchhle postupů.</span><span class="sxs-lookup"><span data-stu-id="7d87e-109">You must have Microsoft Office Word installed on your computer to complete these procedures.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-new-console-application"></a><span data-ttu-id="7d87e-110">Vytvořte novou konzolovou aplikaci</span><span class="sxs-lookup"><span data-stu-id="7d87e-110">To create a new console application</span></span>  
  
1.  <span data-ttu-id="7d87e-111">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7d87e-111">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="7d87e-112">Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.</span><span class="sxs-lookup"><span data-stu-id="7d87e-112">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="7d87e-113">V **kategorií šablon** podokně rozbalte **Visual C#** a potom klikněte na tlačítko **Windows**.</span><span class="sxs-lookup"><span data-stu-id="7d87e-113">In the **Templates Categories** pane, expand **Visual C#**, and then click **Windows**.</span></span>  
  
4.  <span data-ttu-id="7d87e-114">Hledat v horní části **šablony** podokno a ujistěte se, že **rozhraní .NET Framework 4** se zobrazí v **Cílová architektura** pole.</span><span class="sxs-lookup"><span data-stu-id="7d87e-114">Look in the top of the **Templates** pane to make sure that **.NET Framework 4** appears in the **Target Framework** box.</span></span>  
  
5.  <span data-ttu-id="7d87e-115">V **šablony** podokně klikněte na tlačítko **konzolovou aplikaci**.</span><span class="sxs-lookup"><span data-stu-id="7d87e-115">In the **Templates** pane, click **Console Application**.</span></span>  
  
6.  <span data-ttu-id="7d87e-116">Zadejte název pro váš projekt v **název** pole.</span><span class="sxs-lookup"><span data-stu-id="7d87e-116">Type a name for your project in the **Name** field.</span></span>  
  
7.  <span data-ttu-id="7d87e-117">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="7d87e-117">Click **OK**.</span></span>  
  
     <span data-ttu-id="7d87e-118">Nový projekt se zobrazí v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="7d87e-118">The new project appears in **Solution Explorer**.</span></span>  
  
### <a name="to-add-a-reference"></a><span data-ttu-id="7d87e-119">Přidání odkazu</span><span class="sxs-lookup"><span data-stu-id="7d87e-119">To add a reference</span></span>  
  
1.  <span data-ttu-id="7d87e-120">V **Průzkumníka řešení**, klikněte pravým tlačítkem na název vašeho projektu a pak klikněte na tlačítko **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="7d87e-120">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="7d87e-121">**Přidat odkaz** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="7d87e-121">The **Add Reference** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="7d87e-122">Na **.NET** stránce **Microsoft.Office.Interop.Word** v **název komponenty** seznamu.</span><span class="sxs-lookup"><span data-stu-id="7d87e-122">On the **.NET** page, select **Microsoft.Office.Interop.Word** in the **Component Name** list.</span></span>  
  
3.  <span data-ttu-id="7d87e-123">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="7d87e-123">Click **OK**.</span></span>  
  
### <a name="to-add-necessary-using-directives"></a><span data-ttu-id="7d87e-124">Chcete-li přidat nezbytné direktivy using</span><span class="sxs-lookup"><span data-stu-id="7d87e-124">To add necessary using directives</span></span>  
  
1.  <span data-ttu-id="7d87e-125">V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **Program.cs** souboru a pak klikněte na tlačítko **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="7d87e-125">In **Solution Explorer**, right-click the **Program.cs** file and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="7d87e-126">Přidejte následující `using` direktivy do horní části souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="7d87e-126">Add the following `using` directives to the top of the code file.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#4)]  
  
### <a name="to-display-text-in-a-word-document"></a><span data-ttu-id="7d87e-127">K zobrazení textu v dokumentu aplikace Word</span><span class="sxs-lookup"><span data-stu-id="7d87e-127">To display text in a Word document</span></span>  
  
1.  <span data-ttu-id="7d87e-128">V `Program` třídy v souboru Program.cs, přidejte následující metodu pro vytvoření aplikace Word a Wordový dokument.</span><span class="sxs-lookup"><span data-stu-id="7d87e-128">In the `Program` class in Program.cs, add the following method to create a Word application and a Word document.</span></span> <span data-ttu-id="7d87e-129">[Přidat](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) metoda má čtyři volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="7d87e-129">The [Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) method has four optional parameters.</span></span> <span data-ttu-id="7d87e-130">Tento příklad používá výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7d87e-130">This example uses their default values.</span></span> <span data-ttu-id="7d87e-131">Proto jsou nezbytné v příkazu volání bez argumentů.</span><span class="sxs-lookup"><span data-stu-id="7d87e-131">Therefore, no arguments are necessary in the calling statement.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#6)]  
  
2.  <span data-ttu-id="7d87e-132">Přidejte následující kód na konci metody určit, kde k zobrazení textu v dokumentu a jaký text k zobrazení.</span><span class="sxs-lookup"><span data-stu-id="7d87e-132">Add the following code at the end of the method to define where to display text in the document, and what text to display.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#7)]  
  
### <a name="to-run-the-application"></a><span data-ttu-id="7d87e-133">Ke spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="7d87e-133">To run the application</span></span>  
  
1.  <span data-ttu-id="7d87e-134">Main přidejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="7d87e-134">Add the following statement to Main.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#8)]  
  
2.  <span data-ttu-id="7d87e-135">Stiskněte kombinaci kláves CTRL + F5 ke spuštění projektu.</span><span class="sxs-lookup"><span data-stu-id="7d87e-135">Press CTRL+F5 to run the project.</span></span> <span data-ttu-id="7d87e-136">Zobrazí se Wordový dokument, který obsahuje zadaný text.</span><span class="sxs-lookup"><span data-stu-id="7d87e-136">A Word document appears that contains the specified text.</span></span>  
  
### <a name="to-change-the-text-to-a-table"></a><span data-ttu-id="7d87e-137">Chcete-li změnit text do tabulky</span><span class="sxs-lookup"><span data-stu-id="7d87e-137">To change the text to a table</span></span>  
  
1.  <span data-ttu-id="7d87e-138">Použití `ConvertToTable` metoda k uzavření text v tabulce.</span><span class="sxs-lookup"><span data-stu-id="7d87e-138">Use the `ConvertToTable` method to enclose the text in a table.</span></span> <span data-ttu-id="7d87e-139">Tato metoda má šestnácti volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="7d87e-139">The method has sixteen optional parameters.</span></span> <span data-ttu-id="7d87e-140">Technologie IntelliSense obklopuje volitelné parametry v hranatých závorkách, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="7d87e-140">IntelliSense encloses optional parameters in brackets, as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="7d87e-141">![Seznam parametrů pro metodu ConvertToTable. ](../../../csharp/programming-guide/classes-and-structs/media/convert_tableparameters.png "Convert_TableParameters")</span><span class="sxs-lookup"><span data-stu-id="7d87e-141">![List of parameters for ConvertToTable method.](../../../csharp/programming-guide/classes-and-structs/media/convert_tableparameters.png "Convert_TableParameters")</span></span>  
<span data-ttu-id="7d87e-142">Parametry ConvertToTable</span><span class="sxs-lookup"><span data-stu-id="7d87e-142">ConvertToTable parameters</span></span>  
  
     <span data-ttu-id="7d87e-143">Pojmenované a nepovinné argumenty umožňují zadat hodnoty parametrů, které chcete změnit.</span><span class="sxs-lookup"><span data-stu-id="7d87e-143">Named and optional arguments enable you to specify values for only the parameters that you want to change.</span></span> <span data-ttu-id="7d87e-144">Přidejte následující kód na konec metody `DisplayInWord` k vytvoření jednoduché tabulky.</span><span class="sxs-lookup"><span data-stu-id="7d87e-144">Add the following code to the end of method `DisplayInWord` to create a simple table.</span></span> <span data-ttu-id="7d87e-145">Argument určuje, že čárkami v textu řetězce v `range` oddělení buňky tabulky.</span><span class="sxs-lookup"><span data-stu-id="7d87e-145">The argument specifies that the commas in the text string in `range` separate the cells of the table.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#9)]  
  
     <span data-ttu-id="7d87e-146">V dřívějších verzích jazyka C#, volání `ConvertToTable` vyžaduje argument odkazu pro každého parametru, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="7d87e-146">In earlier versions of C#, the call to `ConvertToTable` requires a reference argument for each parameter, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#14)]  
  
2.  <span data-ttu-id="7d87e-147">Stiskněte kombinaci kláves CTRL + F5 ke spuštění projektu.</span><span class="sxs-lookup"><span data-stu-id="7d87e-147">Press CTRL+F5 to run the project.</span></span>  
  
### <a name="to-experiment-with-other-parameters"></a><span data-ttu-id="7d87e-148">Můžete experimentovat s další parametry</span><span class="sxs-lookup"><span data-stu-id="7d87e-148">To experiment with other parameters</span></span>  
  
1.  <span data-ttu-id="7d87e-149">Chcete-li změnit tabulku tak, aby měl jeden sloupec a třemi řádky, nahraďte na posledním řádku `DisplayInWord` s následující příkaz a zadejte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="7d87e-149">To change the table so that it has one column and three rows, replace the last line in `DisplayInWord` with the following statement and then type CTRL+F5.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#10)]  
  
2.  <span data-ttu-id="7d87e-150">Chcete-li zadat předdefinovaný formát pro tabulku, nahraďte poslední řádek v `DisplayInWord` s následující příkaz a zadejte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="7d87e-150">To specify a predefined format for the table, replace the last line in `DisplayInWord` with the following statement and then type CTRL+F5.</span></span> <span data-ttu-id="7d87e-151">Formát lze rozdělit [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) konstanty.</span><span class="sxs-lookup"><span data-stu-id="7d87e-151">The format can be any of the [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) constants.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#11)]  
  
## <a name="example"></a><span data-ttu-id="7d87e-152">Příklad</span><span class="sxs-lookup"><span data-stu-id="7d87e-152">Example</span></span>  
 <span data-ttu-id="7d87e-153">Následující kód obsahuje úplný příklad.</span><span class="sxs-lookup"><span data-stu-id="7d87e-153">The following code includes the full example.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#12)]  
  
## <a name="see-also"></a><span data-ttu-id="7d87e-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d87e-154">See also</span></span>

- [<span data-ttu-id="7d87e-155">Pojmenované a nepovinné argumenty</span><span class="sxs-lookup"><span data-stu-id="7d87e-155">Named and Optional Arguments</span></span>](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)
