---
title: 'Návod: Vložení informací o typu ze sestavení sady Microsoft Office v sadě Visual Studio (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 26b44286-5066-4ad4-8e6a-c24902be347c
ms.openlocfilehash: bc8f7585964bdd60bac5d5a466f6276fab288c78
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44514511"
---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-visual-basic"></a><span data-ttu-id="f15b7-102">Návod: Vložení informací o typu ze sestavení sady Microsoft Office v sadě Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f15b7-102">Walkthrough: Embedding Type Information from Microsoft Office Assemblies in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="f15b7-103">Je-li vložit informace o typu v aplikaci, která odkazuje na objekty modelu COM, můžete vyloučit potřebu primárního sestavení interop (PIA).</span><span class="sxs-lookup"><span data-stu-id="f15b7-103">If you embed type information in an application that references COM objects, you can eliminate the need for a primary interop assembly (PIA).</span></span> <span data-ttu-id="f15b7-104">Kromě toho informace o typu embedded vám umožní dosáhnout nezávislosti na verzi pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f15b7-104">Additionally, the embedded type information enables you to achieve version independence for your application.</span></span> <span data-ttu-id="f15b7-105">To znamená váš program může zapisovat používat typy z více verzí knihovny COM bez nutnosti zvláštního PIA pro každou verzi.</span><span class="sxs-lookup"><span data-stu-id="f15b7-105">That is, your program can be written to use types from multiple versions of a COM library without requiring a specific PIA for each version.</span></span> <span data-ttu-id="f15b7-106">Toto je běžný scénář pro aplikace, které používají objekty z knihoven Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="f15b7-106">This is a common scenario for applications that use objects from Microsoft Office libraries.</span></span> <span data-ttu-id="f15b7-107">Vložení informací o typu umožňuje jednomu sestavení programu pracovat s různými verzemi sady Microsoft Office na různých počítačích bez nutnosti znovu nasazovat program nebo PIA pro každou verzi sady Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="f15b7-107">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers without the need to redeploy either the program or the PIA for each version of Microsoft Office.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a><span data-ttu-id="f15b7-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f15b7-108">Prerequisites</span></span>  
 <span data-ttu-id="f15b7-109">Tento postup vyžaduje následující:</span><span class="sxs-lookup"><span data-stu-id="f15b7-109">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="f15b7-110">Počítač, na kterém je nainstalováno Visual Studio a Microsoft Excelu.</span><span class="sxs-lookup"><span data-stu-id="f15b7-110">A computer on which Visual Studio and Microsoft Excel are installed.</span></span>  
  
-   <span data-ttu-id="f15b7-111">Druhý počítač, na kterém je nainstalováno rozhraní .NET Framework 4 nebo vyšší a jinou verzi aplikace Excel.</span><span class="sxs-lookup"><span data-stu-id="f15b7-111">A second computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
##  <a name="BKMK_createapp"></a> <span data-ttu-id="f15b7-112">Chcete-li vytvořit aplikaci, která pracuje s více verzemi sady Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="f15b7-112">To create an application that works with multiple versions of Microsoft Office</span></span>  
  
1.  <span data-ttu-id="f15b7-113">Spusťte sadu Visual Studio na počítači, na kterém je nainstalována aplikace Excel.</span><span class="sxs-lookup"><span data-stu-id="f15b7-113">Start Visual Studio on a computer on which Excel is installed.</span></span>  
  
2.  <span data-ttu-id="f15b7-114">Na **souboru** nabídce zvolte **nový**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="f15b7-114">On the **File** menu, choose **New**, **Project**.</span></span>  
  
3.  <span data-ttu-id="f15b7-115">V **nový projekt** v dialogu **typy projektů** podokno, ujistěte se, že **Windows** zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="f15b7-115">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="f15b7-116">Vyberte **konzolovou aplikaci** v **šablony** podokně.</span><span class="sxs-lookup"><span data-stu-id="f15b7-116">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="f15b7-117">V **název** zadejte `CreateExcelWorkbook`a klikněte na tlačítko **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="f15b7-117">In the **Name** box, enter `CreateExcelWorkbook`, and then choose the **OK** button.</span></span> <span data-ttu-id="f15b7-118">Vytvoření nového projektu.</span><span class="sxs-lookup"><span data-stu-id="f15b7-118">The new project is created.</span></span>  
  
4.  <span data-ttu-id="f15b7-119">Otevřete místní nabídku pro projekt CreateExcelWorkbook a pak zvolte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="f15b7-119">Open the shortcut menu for the CreateExcelWorkbook project and then choose **Properties**.</span></span> <span data-ttu-id="f15b7-120">Zvolte **odkazy** kartu. Zvolte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="f15b7-120">Choose the **References** tab. Choose the **Add** button.</span></span>  
  
5.  <span data-ttu-id="f15b7-121">Na **.NET** kartu, zvolte nejnovější verzi `Microsoft.Office.Interop.Excel`.</span><span class="sxs-lookup"><span data-stu-id="f15b7-121">On the **.NET** tab, choose the most recent version of `Microsoft.Office.Interop.Excel`.</span></span> <span data-ttu-id="f15b7-122">Například **Microsoft.Office.Interop.Excel 14.0.0.0**.</span><span class="sxs-lookup"><span data-stu-id="f15b7-122">For example, **Microsoft.Office.Interop.Excel 14.0.0.0**.</span></span> <span data-ttu-id="f15b7-123">Zvolte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="f15b7-123">Choose the **OK** button.</span></span>  
  
6.  <span data-ttu-id="f15b7-124">V seznamu odkazů pro **CreateExcelWorkbook** projektu, vyberte odkaz pro `Microsoft.Office.Interop.Excel` , který jste přidali v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="f15b7-124">In the list of references for the **CreateExcelWorkbook** project, select the reference for `Microsoft.Office.Interop.Excel` that you added in the previous step.</span></span> <span data-ttu-id="f15b7-125">V **vlastnosti** okno, ujistěte se, že `Embed Interop Types` je nastavena na `True`.</span><span class="sxs-lookup"><span data-stu-id="f15b7-125">In the **Properties** window, make sure that the `Embed Interop Types` property is set to `True`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f15b7-126">Aplikace vytvořené v tomto názorném postupu se spouští s různými verzemi sady Microsoft Office z důvodu informace o vloženém typu spolupráce.</span><span class="sxs-lookup"><span data-stu-id="f15b7-126">The application created in this walkthrough runs with different versions of Microsoft Office because of the embedded interop type information.</span></span> <span data-ttu-id="f15b7-127">Pokud `Embed Interop Types` je nastavena na `False`, musíte zahrnout PIA pro každou verzi sady Microsoft Office, která bude aplikace spuštěna s.</span><span class="sxs-lookup"><span data-stu-id="f15b7-127">If the `Embed Interop Types` property is set to `False`, you must include a PIA for each version of Microsoft Office that the application will run with.</span></span>  
  
7.  <span data-ttu-id="f15b7-128">Otevřete soubor Module1.vb.</span><span class="sxs-lookup"><span data-stu-id="f15b7-128">Open the Module1.vb file.</span></span> <span data-ttu-id="f15b7-129">Nahraďte kód v souboru následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="f15b7-129">Replace the code in the file with the following code:</span></span>  
  
    ```vb  
    Imports Excel = Microsoft.Office.Interop.Excel  
  
    Module Module1  
  
        Sub Main()  
            Dim values = {4, 6, 18, 2, 1, 76, 0, 3, 11}  
  
            CreateWorkbook(values, "C:\SampleFolder\SampleWorkbook.xls")  
        End Sub  
  
        Sub CreateWorkbook(ByVal values As Integer(), ByVal filePath As String)  
            Dim excelApp As Excel.Application = Nothing  
            Dim wkbk As Excel.Workbook  
            Dim sheet As Excel.Worksheet  
  
            Try  
                ' Start Excel and create a workbook and worksheet.  
                excelApp = New Excel.Application  
                wkbk = excelApp.Workbooks.Add()  
                sheet = CType(wkbk.Sheets.Add(), Excel.Worksheet)  
                sheet.Name = "Sample Worksheet"  
  
                ' Write a column of values.  
                ' In the For loop, both the row index and array index start at 1.  
                ' Therefore the value of 4 at array index 0 is not included.  
                For i = 1 To values.Length - 1  
                    sheet.Cells(i, 1) = values(i)  
                Next  
  
                ' Suppress any alerts and save the file. Create the directory   
                ' if it does not exist. Overwrite the file if it exists.  
                excelApp.DisplayAlerts = False  
                Dim folderPath = My.Computer.FileSystem.GetParentPath(filePath)  
                If Not My.Computer.FileSystem.DirectoryExists(folderPath) Then  
                    My.Computer.FileSystem.CreateDirectory(folderPath)  
                End If  
                wkbk.SaveAs(filePath)  
        Catch  
  
            Finally  
                sheet = Nothing  
                wkbk = Nothing  
  
                ' Close Excel.  
                excelApp.Quit()  
                excelApp = Nothing  
            End Try  
  
        End Sub  
    End Module  
    ```  
  
8.  <span data-ttu-id="f15b7-130">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="f15b7-130">Save the project.</span></span>  
  
9. <span data-ttu-id="f15b7-131">Stisknutím kláves CTRL + F5 sestavte a spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="f15b7-131">Press CTRL+F5 to build and run the project.</span></span> <span data-ttu-id="f15b7-132">Ověřte, zda byl vytvořen sešit aplikace Excel v umístění zadaném v příkladu kódu: C:\SampleFolder\SampleWorkbook.xls.</span><span class="sxs-lookup"><span data-stu-id="f15b7-132">Verify that an Excel workbook has been created at the location specified in the example code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
##  <a name="BKMK_publishapp"></a> <span data-ttu-id="f15b7-133">K publikování aplikace na počítači, na kterém je nainstalovaná jiná verze systému Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="f15b7-133">To publish the application to a computer on which a different version of Microsoft Office is installed</span></span>  
  
1.  <span data-ttu-id="f15b7-134">Otevřete projekt vytvořený v rámci tohoto návodu v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f15b7-134">Open the project created by this walkthrough in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="f15b7-135">Na **sestavení** nabídce zvolte **publikovat CreateExcelWorkbook**.</span><span class="sxs-lookup"><span data-stu-id="f15b7-135">On the **Build** menu, choose **Publish CreateExcelWorkbook**.</span></span> <span data-ttu-id="f15b7-136">Postupujte podle kroků v Průvodci publikováním vytvoření instalovatelnou verzi aplikace.</span><span class="sxs-lookup"><span data-stu-id="f15b7-136">Follow the steps of the Publish Wizard to create an installable version of the application.</span></span> <span data-ttu-id="f15b7-137">Další informace najdete v tématu [Průvodce publikováním (vývoj pro Office v sadě Visual Studio)](/visualstudio/vsto/publish-wizard-office-development-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="f15b7-137">For more information, see [Publish Wizard (Office Development in Visual Studio)](/visualstudio/vsto/publish-wizard-office-development-in-visual-studio).</span></span>  
  
3.  <span data-ttu-id="f15b7-138">Nainstalujte aplikace na počítači, na kterém je nainstalováno rozhraní .NET Framework 4 nebo vyšší a jinou verzi aplikace Excel.</span><span class="sxs-lookup"><span data-stu-id="f15b7-138">Install the application on a computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
4.  <span data-ttu-id="f15b7-139">Po dokončení instalace spusťte nainstalovaný program.</span><span class="sxs-lookup"><span data-stu-id="f15b7-139">When the installation is finished, run the installed program.</span></span>  
  
5.  <span data-ttu-id="f15b7-140">Ověřte, zda byl vytvořen sešit aplikace Excel v umístění zadaném ve vzorovém kódu: C:\SampleFolder\SampleWorkbook.xls.</span><span class="sxs-lookup"><span data-stu-id="f15b7-140">Verify that an Excel workbook has been created at the location specified in the sample code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f15b7-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f15b7-141">See also</span></span>

- [<span data-ttu-id="f15b7-142">Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f15b7-142">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)  
- [<span data-ttu-id="f15b7-143">/ Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f15b7-143">/link (Visual Basic)</span></span>](../../../../visual-basic/reference/command-line-compiler/link.md)
