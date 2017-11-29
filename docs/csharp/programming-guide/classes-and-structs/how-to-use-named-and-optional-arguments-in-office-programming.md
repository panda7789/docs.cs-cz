---
title: "Postupy: Použití pojmenovaných a nepovinných argumentů v programování pro sadu Office (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
caps.latest.revision: "34"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a453699591397224435fba1e602c305f18e84a11
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a><span data-ttu-id="4cbba-102">Postupy: Použití pojmenovaných a nepovinných argumentů v programování pro sadu Office (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="4cbba-102">How to: Use Named and Optional Arguments in Office Programming (C# Programming Guide)</span></span>
<span data-ttu-id="4cbba-103">Pojmenované argumenty a volitelné argumenty, počínaje [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], zvýšení pohodlí, flexibilitu a čitelnost v C# – programování.</span><span class="sxs-lookup"><span data-stu-id="4cbba-103">Named arguments and optional arguments, introduced in [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], enhance convenience, flexibility, and readability in C# programming.</span></span> <span data-ttu-id="4cbba-104">Kromě toho tyto funkce výrazně usnadnit přístup k rozhraní modelu COM, jako je například Microsoft Office automatizace rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="4cbba-104">In addition, these features greatly facilitate access to COM interfaces such as the Microsoft Office automation APIs.</span></span>  
  
 <span data-ttu-id="4cbba-105">V následujícím příkladu metoda [ConvertToTable](http://go.microsoft.com/fwlink/?LinkId=145378) má šestnáct parametry, které představují vlastností tabulky jako počet sloupců a řádků, formátování, ohraničení, písma a barvy.</span><span class="sxs-lookup"><span data-stu-id="4cbba-105">In the following example, method [ConvertToTable](http://go.microsoft.com/fwlink/?LinkId=145378) has sixteen parameters that represent characteristics of a table, such as number of columns and rows, formatting, borders, fonts, and colors.</span></span> <span data-ttu-id="4cbba-106">Všechny šestnáct parametry jsou volitelné, protože ve většině případů nechcete zadat konkrétní hodnoty pro všechny z nich.</span><span class="sxs-lookup"><span data-stu-id="4cbba-106">All sixteen parameters are optional, because most of the time you do not want to specify particular values for all of them.</span></span> <span data-ttu-id="4cbba-107">Ale bez pojmenované a nepovinné argumenty, hodnotu nebo hodnotu zástupného symbolu je třeba zadat pro jednotlivé parametry.</span><span class="sxs-lookup"><span data-stu-id="4cbba-107">However, without named and optional arguments, a value or a placeholder value has to be provided for each parameter.</span></span> <span data-ttu-id="4cbba-108">Pomocí pojmenovaných a nepovinných argumentů je určit pouze hodnoty parametrů, které jsou požadovány pro svůj projekt.</span><span class="sxs-lookup"><span data-stu-id="4cbba-108">With named and optional arguments, you specify values only for the parameters that are required for your project.</span></span>  
  
 <span data-ttu-id="4cbba-109">Musíte mít aplikaci Microsoft Office Word v počítači nainstalována k provedení těchto postupů.</span><span class="sxs-lookup"><span data-stu-id="4cbba-109">You must have Microsoft Office Word installed on your computer to complete these procedures.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-new-console-application"></a><span data-ttu-id="4cbba-110">Chcete-li vytvořit novou konzolovou aplikaci</span><span class="sxs-lookup"><span data-stu-id="4cbba-110">To create a new console application</span></span>  
  
1.  <span data-ttu-id="4cbba-111">Spuštění sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4cbba-111">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="4cbba-112">Na **soubor** nabídky, přejděte na příkaz **nový**a potom klikněte na **projektu**.</span><span class="sxs-lookup"><span data-stu-id="4cbba-112">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="4cbba-113">V **kategorie šablony** podokně rozbalte **Visual C#**a potom klikněte na **Windows**.</span><span class="sxs-lookup"><span data-stu-id="4cbba-113">In the **Templates Categories** pane, expand **Visual C#**, and then click **Windows**.</span></span>  
  
4.  <span data-ttu-id="4cbba-114">Hledat v horní části **šablony** podokně Ujistěte se, že **rozhraní .NET Framework 4** se zobrazí v **cílové rozhraní** pole.</span><span class="sxs-lookup"><span data-stu-id="4cbba-114">Look in the top of the **Templates** pane to make sure that **.NET Framework 4** appears in the **Target Framework** box.</span></span>  
  
5.  <span data-ttu-id="4cbba-115">V **šablony** podokně klikněte na tlačítko **konzolové aplikace**.</span><span class="sxs-lookup"><span data-stu-id="4cbba-115">In the **Templates** pane, click **Console Application**.</span></span>  
  
6.  <span data-ttu-id="4cbba-116">Zadejte název pro svůj projekt v **název** pole.</span><span class="sxs-lookup"><span data-stu-id="4cbba-116">Type a name for your project in the **Name** field.</span></span>  
  
7.  <span data-ttu-id="4cbba-117">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="4cbba-117">Click **OK**.</span></span>  
  
     <span data-ttu-id="4cbba-118">Nový projekt se zobrazí v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="4cbba-118">The new project appears in **Solution Explorer**.</span></span>  
  
### <a name="to-add-a-reference"></a><span data-ttu-id="4cbba-119">Přidání odkazu</span><span class="sxs-lookup"><span data-stu-id="4cbba-119">To add a reference</span></span>  
  
1.  <span data-ttu-id="4cbba-120">V **Průzkumníku řešení**, klikněte pravým tlačítkem na název vašeho projektu a pak klikněte na tlačítko **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="4cbba-120">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="4cbba-121">**Přidat odkaz na** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="4cbba-121">The **Add Reference** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="4cbba-122">Na **.NET** vyberte **Microsoft.Office.Interop.Word** v **název komponenty** seznamu.</span><span class="sxs-lookup"><span data-stu-id="4cbba-122">On the **.NET** page, select **Microsoft.Office.Interop.Word** in the **Component Name** list.</span></span>  
  
3.  <span data-ttu-id="4cbba-123">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="4cbba-123">Click **OK**.</span></span>  
  
### <a name="to-add-necessary-using-directives"></a><span data-ttu-id="4cbba-124">Chcete-li přidat potřebné pomocí direktiv</span><span class="sxs-lookup"><span data-stu-id="4cbba-124">To add necessary using directives</span></span>  
  
1.  <span data-ttu-id="4cbba-125">V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **Program.cs** souboru a pak klikněte na **kód zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="4cbba-125">In **Solution Explorer**, right-click the **Program.cs** file and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="4cbba-126">Přidejte následující `using` direktivy na začátek souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="4cbba-126">Add the following `using` directives to the top of the code file.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_1.cs)]  
  
### <a name="to-display-text-in-a-word-document"></a><span data-ttu-id="4cbba-127">Zobrazení textu v dokument aplikace Word</span><span class="sxs-lookup"><span data-stu-id="4cbba-127">To display text in a Word document</span></span>  
  
1.  <span data-ttu-id="4cbba-128">V `Program` třídy v souboru Program.cs, přidejte následující metodu pro vytvoření aplikace Word a dokument aplikace Word.</span><span class="sxs-lookup"><span data-stu-id="4cbba-128">In the `Program` class in Program.cs, add the following method to create a Word application and a Word document.</span></span> <span data-ttu-id="4cbba-129">[Přidat](http://go.microsoft.com/fwlink/?LinkId=145381) metoda má čtyři volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="4cbba-129">The [Add](http://go.microsoft.com/fwlink/?LinkId=145381) method has four optional parameters.</span></span> <span data-ttu-id="4cbba-130">Tento příklad používá výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4cbba-130">This example uses their default values.</span></span> <span data-ttu-id="4cbba-131">Proto jsou nezbytné v volání příkazu žádné argumenty.</span><span class="sxs-lookup"><span data-stu-id="4cbba-131">Therefore, no arguments are necessary in the calling statement.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_2.cs)]  
  
2.  <span data-ttu-id="4cbba-132">Přidejte následující kód na konci metody určit, kde k zobrazení textu v dokumentu a jaký text k zobrazení.</span><span class="sxs-lookup"><span data-stu-id="4cbba-132">Add the following code at the end of the method to define where to display text in the document, and what text to display.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_3.cs)]  
  
### <a name="to-run-the-application"></a><span data-ttu-id="4cbba-133">Ke spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="4cbba-133">To run the application</span></span>  
  
1.  <span data-ttu-id="4cbba-134">Přidejte následující příkaz na hlavní.</span><span class="sxs-lookup"><span data-stu-id="4cbba-134">Add the following statement to Main.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_4.cs)]  
  
2.  <span data-ttu-id="4cbba-135">Stisknutím kombinace kláves CTRL + F5 a spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="4cbba-135">Press CTRL+F5 to run the project.</span></span> <span data-ttu-id="4cbba-136">Dokument aplikace Word se zobrazí, který obsahuje zadaný text.</span><span class="sxs-lookup"><span data-stu-id="4cbba-136">A Word document appears that contains the specified text.</span></span>  
  
### <a name="to-change-the-text-to-a-table"></a><span data-ttu-id="4cbba-137">Chcete-li změnit text do tabulky</span><span class="sxs-lookup"><span data-stu-id="4cbba-137">To change the text to a table</span></span>  
  
1.  <span data-ttu-id="4cbba-138">Použití `ConvertToTable` metodu uzavřete text v tabulce.</span><span class="sxs-lookup"><span data-stu-id="4cbba-138">Use the `ConvertToTable` method to enclose the text in a table.</span></span> <span data-ttu-id="4cbba-139">Metoda má šestnáct volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="4cbba-139">The method has sixteen optional parameters.</span></span> <span data-ttu-id="4cbba-140">IntelliSense uzavře volitelné parametry v závorkách, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="4cbba-140">IntelliSense encloses optional parameters in brackets, as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="4cbba-141">![Seznam parametrů pro metodu ConvertToTable. ] (../../../csharp/programming-guide/classes-and-structs/media/convert_tableparameters.png "Convert_TableParameters")</span><span class="sxs-lookup"><span data-stu-id="4cbba-141">![List of parameters for ConvertToTable method.](../../../csharp/programming-guide/classes-and-structs/media/convert_tableparameters.png "Convert_TableParameters")</span></span>  
<span data-ttu-id="4cbba-142">Parametry ConvertToTable</span><span class="sxs-lookup"><span data-stu-id="4cbba-142">ConvertToTable parameters</span></span>  
  
     <span data-ttu-id="4cbba-143">Pojmenované a nepovinné argumenty umožňují zadat hodnoty pro jenom parametry, které chcete změnit.</span><span class="sxs-lookup"><span data-stu-id="4cbba-143">Named and optional arguments enable you to specify values for only the parameters that you want to change.</span></span> <span data-ttu-id="4cbba-144">Přidejte následující kód do konce metoda `DisplayInWord` k vytvoření jednoduché tabulky.</span><span class="sxs-lookup"><span data-stu-id="4cbba-144">Add the following code to the end of method `DisplayInWord` to create a simple table.</span></span> <span data-ttu-id="4cbba-145">Argument určuje, že řetězec čárky v textu v `range` oddělení buňky tabulky.</span><span class="sxs-lookup"><span data-stu-id="4cbba-145">The argument specifies that the commas in the text string in `range` separate the cells of the table.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_5.cs)]  
  
     <span data-ttu-id="4cbba-146">V dřívějších verzích systému C#, volání `ConvertToTable` vyžaduje argument typu odkaz pro všechny parametry, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="4cbba-146">In earlier versions of C#, the call to `ConvertToTable` requires a reference argument for each parameter, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_6.cs)]  
  
2.  <span data-ttu-id="4cbba-147">Stisknutím kombinace kláves CTRL + F5 a spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="4cbba-147">Press CTRL+F5 to run the project.</span></span>  
  
### <a name="to-experiment-with-other-parameters"></a><span data-ttu-id="4cbba-148">A experimentovat s další parametry</span><span class="sxs-lookup"><span data-stu-id="4cbba-148">To experiment with other parameters</span></span>  
  
1.  <span data-ttu-id="4cbba-149">Chcete-li změnit v tabulce tak, aby měl jeden sloupec a tři řádky, nahraďte na posledním řádku `DisplayInWord` s následující příkaz a pak zadejte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="4cbba-149">To change the table so that it has one column and three rows, replace the last line in `DisplayInWord` with the following statement and then type CTRL+F5.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_7.cs)]  
  
2.  <span data-ttu-id="4cbba-150">Pro určení předdefinované formátu pro tabulku, nahraďte na posledním řádku `DisplayInWord` s následující příkaz a pak zadejte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="4cbba-150">To specify a predefined format for the table, replace the last line in `DisplayInWord` with the following statement and then type CTRL+F5.</span></span> <span data-ttu-id="4cbba-151">Formát může být libovolná z [WdTableFormat](http://go.microsoft.com/fwlink/?LinkId=145382) konstanty.</span><span class="sxs-lookup"><span data-stu-id="4cbba-151">The format can be any of the [WdTableFormat](http://go.microsoft.com/fwlink/?LinkId=145382) constants.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_8.cs)]  
  
## <a name="example"></a><span data-ttu-id="4cbba-152">Příklad</span><span class="sxs-lookup"><span data-stu-id="4cbba-152">Example</span></span>  
 <span data-ttu-id="4cbba-153">Následující kód obsahuje kompletní příklad.</span><span class="sxs-lookup"><span data-stu-id="4cbba-153">The following code includes the full example.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_9.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="4cbba-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="4cbba-154">See Also</span></span>  
 [<span data-ttu-id="4cbba-155">Pojmenované a nepovinné argumenty</span><span class="sxs-lookup"><span data-stu-id="4cbba-155">Named and Optional Arguments</span></span>](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)
