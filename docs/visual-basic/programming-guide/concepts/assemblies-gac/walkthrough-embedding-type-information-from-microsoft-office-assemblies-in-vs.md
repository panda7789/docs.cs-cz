---
title: "Návod: Vložení informací o typu ze sestavení sady Microsoft Office v sadě Visual Studio (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26b44286-5066-4ad4-8e6a-c24902be347c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 26e6fee5147e8477c64f7eaf0dc2aeb928c13e15
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-visual-basic"></a><span data-ttu-id="6774c-102">Návod: Vložení informací o typu ze sestavení sady Microsoft Office v sadě Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6774c-102">Walkthrough: Embedding Type Information from Microsoft Office Assemblies in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="6774c-103">Pokud vložit informace typu v aplikaci, která odkazuje na objekty modelu COM, můžete eliminovat potřebu primární spolupracující sestavení (PIA).</span><span class="sxs-lookup"><span data-stu-id="6774c-103">If you embed type information in an application that references COM objects, you can eliminate the need for a primary interop assembly (PIA).</span></span> <span data-ttu-id="6774c-104">Informace o vložených typu navíc umožňuje dosáhnout nezávislost verze pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6774c-104">Additionally, the embedded type information enables you to achieve version independence for your application.</span></span> <span data-ttu-id="6774c-105">To znamená váš program může být napsán používat typy z více verzí knihovny COM bez nutnosti konkrétní PIA – pro každou verzi.</span><span class="sxs-lookup"><span data-stu-id="6774c-105">That is, your program can be written to use types from multiple versions of a COM library without requiring a specific PIA for each version.</span></span> <span data-ttu-id="6774c-106">Toto je běžný scénář pro aplikace, které používají objekty z knihovny Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="6774c-106">This is a common scenario for applications that use objects from Microsoft Office libraries.</span></span> <span data-ttu-id="6774c-107">Vložení informací o typu umožňuje ve stejném sestavení programu pro práci s různými verzemi nástroje Microsoft Office na různých počítačích bez nutnosti znovu nasaďte program nebo PIA – pro každou verzi systému Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="6774c-107">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers without the need to redeploy either the program or the PIA for each version of Microsoft Office.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a><span data-ttu-id="6774c-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6774c-108">Prerequisites</span></span>  
 <span data-ttu-id="6774c-109">Tento postup vyžaduje následující:</span><span class="sxs-lookup"><span data-stu-id="6774c-109">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="6774c-110">Počítač, na kterém jsou nainstalované sady Visual Studio a aplikaci Microsoft Excel.</span><span class="sxs-lookup"><span data-stu-id="6774c-110">A computer on which Visual Studio and Microsoft Excel are installed.</span></span>  
  
-   <span data-ttu-id="6774c-111">Druhý počítač, na kterém jsou nainstalované rozhraní .NET Framework 4 nebo vyšší a jinou verzi aplikace Excel.</span><span class="sxs-lookup"><span data-stu-id="6774c-111">A second computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
##  <a name="BKMK_createapp"></a><span data-ttu-id="6774c-112">Chcete-li vytvořit aplikaci, která funguje s více verzemi systému Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="6774c-112">To create an application that works with multiple versions of Microsoft Office</span></span>  
  
1.  <span data-ttu-id="6774c-113">Spuštění sady Visual Studio v počítači, na kterém je nainstalována aplikace Excel.</span><span class="sxs-lookup"><span data-stu-id="6774c-113">Start Visual Studio on a computer on which Excel is installed.</span></span>  
  
2.  <span data-ttu-id="6774c-114">Na **soubor** nabídce zvolte **nový**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="6774c-114">On the **File** menu, choose **New**, **Project**.</span></span>  
  
3.  <span data-ttu-id="6774c-115">V **nový projekt** dialogovém **typy projektů** podokně, ujistěte se, že **Windows** je vybrána.</span><span class="sxs-lookup"><span data-stu-id="6774c-115">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="6774c-116">Vyberte **konzolové aplikace** v **šablony** podokně.</span><span class="sxs-lookup"><span data-stu-id="6774c-116">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="6774c-117">V **název** zadejte `CreateExcelWorkbook`a potom zvolte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="6774c-117">In the **Name** box, enter `CreateExcelWorkbook`, and then choose the **OK** button.</span></span> <span data-ttu-id="6774c-118">Vytvoření nového projektu.</span><span class="sxs-lookup"><span data-stu-id="6774c-118">The new project is created.</span></span>  
  
4.  <span data-ttu-id="6774c-119">Otevřete místní nabídky projektu CreateExcelWorkbook a zvolte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="6774c-119">Open the shortcut menu for the CreateExcelWorkbook project and then choose **Properties**.</span></span> <span data-ttu-id="6774c-120">Vyberte **odkazy** kartě. Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="6774c-120">Choose the **References** tab. Choose the **Add** button.</span></span>  
  
5.  <span data-ttu-id="6774c-121">Na **.NET** , zvolte nejnovější verzi `Microsoft.Office.Interop.Excel`.</span><span class="sxs-lookup"><span data-stu-id="6774c-121">On the **.NET** tab, choose the most recent version of `Microsoft.Office.Interop.Excel`.</span></span> <span data-ttu-id="6774c-122">Například **Microsoft.Office.Interop.Excel 14.0.0.0**.</span><span class="sxs-lookup"><span data-stu-id="6774c-122">For example, **Microsoft.Office.Interop.Excel 14.0.0.0**.</span></span> <span data-ttu-id="6774c-123">Vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="6774c-123">Choose the **OK** button.</span></span>  
  
6.  <span data-ttu-id="6774c-124">V seznamu odkazů pro **CreateExcelWorkbook** projekt, vyberte odkaz pro `Microsoft.Office.Interop.Excel` kterou jste přidali v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="6774c-124">In the list of references for the **CreateExcelWorkbook** project, select the reference for `Microsoft.Office.Interop.Excel` that you added in the previous step.</span></span> <span data-ttu-id="6774c-125">V **vlastnosti** okna, ujistěte se, že `Embed Interop Types` je nastavena na `True`.</span><span class="sxs-lookup"><span data-stu-id="6774c-125">In the **Properties** window, make sure that the `Embed Interop Types` property is set to `True`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6774c-126">Z důvodu informace o vložených zprostředkovatele komunikace s objekty typu spuštění aplikace vytvořené v tomto návodu s různými verzemi nástroje Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="6774c-126">The application created in this walkthrough runs with different versions of Microsoft Office because of the embedded interop type information.</span></span> <span data-ttu-id="6774c-127">Pokud `Embed Interop Types` je nastavena na `False`, je nutné zahrnout PIA – pro každou verzi systému Microsoft Office, které aplikace poběží s.</span><span class="sxs-lookup"><span data-stu-id="6774c-127">If the `Embed Interop Types` property is set to `False`, you must include a PIA for each version of Microsoft Office that the application will run with.</span></span>  
  
7.  <span data-ttu-id="6774c-128">Otevřete soubor Module1.vb.</span><span class="sxs-lookup"><span data-stu-id="6774c-128">Open the Module1.vb file.</span></span> <span data-ttu-id="6774c-129">Nahraďte kód v souboru s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="6774c-129">Replace the code in the file with the following code:</span></span>  
  
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
  
8.  <span data-ttu-id="6774c-130">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="6774c-130">Save the project.</span></span>  
  
9. <span data-ttu-id="6774c-131">Stisknutím klávesy CTRL + F5 sestavit a spustit projekt.</span><span class="sxs-lookup"><span data-stu-id="6774c-131">Press CTRL+F5 to build and run the project.</span></span> <span data-ttu-id="6774c-132">Ověřte, že sešit aplikace Excel byl vytvořen v umístění zadaném v ukázkový kód: C:\SampleFolder\SampleWorkbook.xls.</span><span class="sxs-lookup"><span data-stu-id="6774c-132">Verify that an Excel workbook has been created at the location specified in the example code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
##  <a name="BKMK_publishapp"></a><span data-ttu-id="6774c-133">Publikování aplikace do počítače, na kterém je nainstalovaná jiná verze systému Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="6774c-133">To publish the application to a computer on which a different version of Microsoft Office is installed</span></span>  
  
1.  <span data-ttu-id="6774c-134">Otevřete projekt vytvořené tento návod v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6774c-134">Open the project created by this walkthrough in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="6774c-135">Na **sestavení** nabídce zvolte **publikování CreateExcelWorkbook**.</span><span class="sxs-lookup"><span data-stu-id="6774c-135">On the **Build** menu, choose **Publish CreateExcelWorkbook**.</span></span> <span data-ttu-id="6774c-136">Postupujte podle kroků v Průvodci publikováním vytvořit instalovatelných verzi aplikace.</span><span class="sxs-lookup"><span data-stu-id="6774c-136">Follow the steps of the Publish Wizard to create an installable version of the application.</span></span> <span data-ttu-id="6774c-137">Další informace najdete v tématu [Průvodci publikováním (vývoj pro Office v sadě Visual Studio)](https://msdn.microsoft.com/library/bb625071).</span><span class="sxs-lookup"><span data-stu-id="6774c-137">For more information, see [Publish Wizard (Office Development in Visual Studio)](https://msdn.microsoft.com/library/bb625071).</span></span>  
  
3.  <span data-ttu-id="6774c-138">Nainstalujte aplikaci na počítač, na kterém jsou nainstalované rozhraní .NET Framework 4 nebo vyšší a jinou verzi aplikace Excel.</span><span class="sxs-lookup"><span data-stu-id="6774c-138">Install the application on a computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
4.  <span data-ttu-id="6774c-139">Po dokončení instalace spusťte nainstalovaný program.</span><span class="sxs-lookup"><span data-stu-id="6774c-139">When the installation is finished, run the installed program.</span></span>  
  
5.  <span data-ttu-id="6774c-140">Ověřit, že sešit aplikace Excel byl vytvořen v umístění zadaném v ukázkovém kódu: C:\SampleFolder\SampleWorkbook.xls.</span><span class="sxs-lookup"><span data-stu-id="6774c-140">Verify that an Excel workbook has been created at the location specified in the sample code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6774c-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="6774c-141">See Also</span></span>  
 [<span data-ttu-id="6774c-142">Návod: Vložení typů z řízených sestavení v sadě Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6774c-142">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)  
 [<span data-ttu-id="6774c-143">/ Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6774c-143">/link (Visual Basic)</span></span>](../../../../visual-basic/reference/command-line-compiler/link.md)
