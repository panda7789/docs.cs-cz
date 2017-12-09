---
title: "Návod: Vložení informací o typu ze sestavení sady Microsoft Office v sadě Visual Studio (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 3320e866-01f1-4b7f-8932-049a7b2d2a9b
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 45ec4521da08a9a1f4bdc3b433d3f8d765960526
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-c"></a><span data-ttu-id="aa524-102">Návod: Vložení informací o typu ze sestavení sady Microsoft Office v sadě Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="aa524-102">Walkthrough: Embedding Type Information from Microsoft Office Assemblies in Visual Studio (C#)</span></span>
<span data-ttu-id="aa524-103">Pokud vložit informace typu v aplikaci, která odkazuje na objekty modelu COM, můžete eliminovat potřebu primární spolupracující sestavení (PIA).</span><span class="sxs-lookup"><span data-stu-id="aa524-103">If you embed type information in an application that references COM objects, you can eliminate the need for a primary interop assembly (PIA).</span></span> <span data-ttu-id="aa524-104">Informace o vložených typu navíc umožňuje dosáhnout nezávislost verze pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="aa524-104">Additionally, the embedded type information enables you to achieve version independence for your application.</span></span> <span data-ttu-id="aa524-105">To znamená váš program může být napsán používat typy z více verzí knihovny COM bez nutnosti konkrétní PIA – pro každou verzi.</span><span class="sxs-lookup"><span data-stu-id="aa524-105">That is, your program can be written to use types from multiple versions of a COM library without requiring a specific PIA for each version.</span></span> <span data-ttu-id="aa524-106">Toto je běžný scénář pro aplikace, které používají objekty z knihovny Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="aa524-106">This is a common scenario for applications that use objects from Microsoft Office libraries.</span></span> <span data-ttu-id="aa524-107">Vložení informací o typu umožňuje ve stejném sestavení programu pro práci s různými verzemi nástroje Microsoft Office na různých počítačích bez nutnosti znovu nasaďte program nebo PIA – pro každou verzi systému Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="aa524-107">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers without the need to redeploy either the program or the PIA for each version of Microsoft Office.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a><span data-ttu-id="aa524-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aa524-108">Prerequisites</span></span>  
 <span data-ttu-id="aa524-109">Tento postup vyžaduje následující:</span><span class="sxs-lookup"><span data-stu-id="aa524-109">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="aa524-110">Počítač, na kterém jsou nainstalované sady Visual Studio a aplikaci Microsoft Excel.</span><span class="sxs-lookup"><span data-stu-id="aa524-110">A computer on which Visual Studio and Microsoft Excel are installed.</span></span>  
  
-   <span data-ttu-id="aa524-111">Druhý počítač, na kterém jsou nainstalované rozhraní .NET Framework 4 nebo vyšší a jinou verzi aplikace Excel.</span><span class="sxs-lookup"><span data-stu-id="aa524-111">A second computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
##  <a name="BKMK_createapp"></a><span data-ttu-id="aa524-112">Chcete-li vytvořit aplikaci, která funguje s více verzemi systému Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="aa524-112">To create an application that works with multiple versions of Microsoft Office</span></span>  
  
1.  <span data-ttu-id="aa524-113">Spuštění sady Visual Studio v počítači, na kterém je nainstalována aplikace Excel.</span><span class="sxs-lookup"><span data-stu-id="aa524-113">Start Visual Studio on a computer on which Excel is installed.</span></span>  
  
2.  <span data-ttu-id="aa524-114">Na **soubor** nabídce zvolte **nový**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="aa524-114">On the **File** menu, choose **New**, **Project**.</span></span>  
  
3.  <span data-ttu-id="aa524-115">V **nový projekt** dialogovém **typy projektů** podokně, ujistěte se, že **Windows** je vybrána.</span><span class="sxs-lookup"><span data-stu-id="aa524-115">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="aa524-116">Vyberte **konzolové aplikace** v **šablony** podokně.</span><span class="sxs-lookup"><span data-stu-id="aa524-116">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="aa524-117">V **název** zadejte `CreateExcelWorkbook`a potom zvolte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="aa524-117">In the **Name** box, enter `CreateExcelWorkbook`, and then choose the **OK** button.</span></span> <span data-ttu-id="aa524-118">Vytvoření nového projektu.</span><span class="sxs-lookup"><span data-stu-id="aa524-118">The new project is created.</span></span>  
  
4.  <span data-ttu-id="aa524-119">V **Průzkumníku řešení**, otevřete místní nabídku pro **odkazy** složku a potom zvolte **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="aa524-119">In **Solution Explorer**, open the shortcut menu for the **References** folder and then choose **Add Reference**.</span></span>  
  
5.  <span data-ttu-id="aa524-120">Na **.NET** , zvolte nejnovější verzi `Microsoft.Office.Interop.Excel`.</span><span class="sxs-lookup"><span data-stu-id="aa524-120">On the **.NET** tab, choose the most recent version of `Microsoft.Office.Interop.Excel`.</span></span> <span data-ttu-id="aa524-121">Například **Microsoft.Office.Interop.Excel 14.0.0.0**.</span><span class="sxs-lookup"><span data-stu-id="aa524-121">For example, **Microsoft.Office.Interop.Excel 14.0.0.0**.</span></span> <span data-ttu-id="aa524-122">Vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="aa524-122">Choose the **OK** button.</span></span>  
  
6.  <span data-ttu-id="aa524-123">V seznamu odkazů pro **CreateExcelWorkbook** projekt, vyberte odkaz pro `Microsoft.Office.Interop.Excel` kterou jste přidali v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="aa524-123">In the list of references for the **CreateExcelWorkbook** project, select the reference for `Microsoft.Office.Interop.Excel` that you added in the previous step.</span></span> <span data-ttu-id="aa524-124">V **vlastnosti** okna, ujistěte se, že `Embed Interop Types` je nastavena na `True`.</span><span class="sxs-lookup"><span data-stu-id="aa524-124">In the **Properties** window, make sure that the `Embed Interop Types` property is set to `True`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aa524-125">Z důvodu informace o vložených zprostředkovatele komunikace s objekty typu spuštění aplikace vytvořené v tomto návodu s různými verzemi nástroje Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="aa524-125">The application created in this walkthrough runs with different versions of Microsoft Office because of the embedded interop type information.</span></span> <span data-ttu-id="aa524-126">Pokud `Embed Interop Types` je nastavena na `False`, je nutné zahrnout PIA – pro každou verzi systému Microsoft Office, které aplikace poběží s.</span><span class="sxs-lookup"><span data-stu-id="aa524-126">If the `Embed Interop Types` property is set to `False`, you must include a PIA for each version of Microsoft Office that the application will run with.</span></span>  
  
7.  <span data-ttu-id="aa524-127">Otevřete **Program.cs** souboru.</span><span class="sxs-lookup"><span data-stu-id="aa524-127">Open the **Program.cs** file.</span></span> <span data-ttu-id="aa524-128">Nahraďte kód v souboru s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="aa524-128">Replace the code in the file with the following code:</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.IO;  
    using Excel = Microsoft.Office.Interop.Excel;  
  
    namespace CreateExcelWorkbook  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                int[] values = {4, 6, 18, 2, 1, 76, 0, 3, 11};  
  
                CreateWorkbook(values, @"C:\SampleFolder\SampleWorkbook.xls");  
            }  
  
            static void CreateWorkbook(int[] values, string filePath)  
            {  
                Excel.Application excelApp = null;  
                Excel.Workbook wkbk;  
                Excel.Worksheet sheet;  
  
                try  
                {  
                        // Start Excel and create a workbook and worksheet.  
                        excelApp = new Excel.Application();  
                        wkbk = excelApp.Workbooks.Add();  
                        sheet = wkbk.Sheets.Add() as Excel.Worksheet;  
                        sheet.Name = "Sample Worksheet";  
  
                        // Write a column of values.  
                        // In the For loop, both the row index and array index start at 1.  
                        // Therefore the value of 4 at array index 0 is not included.  
                        for (int i = 1; i < values.Length; i++)  
                        {  
                            sheet.Cells[i, 1] = values[i];  
                        }  
  
                        // Suppress any alerts and save the file. Create the directory   
                        // if it does not exist. Overwrite the file if it exists.  
                        excelApp.DisplayAlerts = false;  
                        string folderPath = Path.GetDirectoryName(filePath);  
                        if (!Directory.Exists(folderPath))  
                        {  
                            Directory.CreateDirectory(folderPath);  
                        }  
                        wkbk.SaveAs(filePath);  
                }  
                catch  
                {  
                }  
                finally  
                {  
                    sheet = null;  
                    wkbk = null;  
  
                    // Close Excel.  
                    excelApp.Quit();  
                    excelApp = null;  
                }  
            }  
        }  
    }  
    ```  
  
8.  <span data-ttu-id="aa524-129">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="aa524-129">Save the project.</span></span>  
  
9. <span data-ttu-id="aa524-130">Stisknutím klávesy CTRL + F5 sestavit a spustit projekt.</span><span class="sxs-lookup"><span data-stu-id="aa524-130">Press CTRL+F5 to build and run the project.</span></span> <span data-ttu-id="aa524-131">Ověřte, že sešit aplikace Excel byl vytvořen v umístění zadaném v ukázkový kód: C:\SampleFolder\SampleWorkbook.xls.</span><span class="sxs-lookup"><span data-stu-id="aa524-131">Verify that an Excel workbook has been created at the location specified in the example code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
##  <a name="BKMK_publishapp"></a><span data-ttu-id="aa524-132">Publikování aplikace do počítače, na kterém je nainstalovaná jiná verze systému Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="aa524-132">To publish the application to a computer on which a different version of Microsoft Office is installed</span></span>  
  
1.  <span data-ttu-id="aa524-133">Otevřete projekt vytvořené tento návod v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aa524-133">Open the project created by this walkthrough in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="aa524-134">Na **sestavení** nabídce zvolte **publikování CreateExcelWorkbook**.</span><span class="sxs-lookup"><span data-stu-id="aa524-134">On the **Build** menu, choose **Publish CreateExcelWorkbook**.</span></span> <span data-ttu-id="aa524-135">Postupujte podle kroků v Průvodci publikováním vytvořit instalovatelných verzi aplikace.</span><span class="sxs-lookup"><span data-stu-id="aa524-135">Follow the steps of the Publish Wizard to create an installable version of the application.</span></span> <span data-ttu-id="aa524-136">Další informace najdete v tématu [Průvodci publikováním (vývoj pro Office v sadě Visual Studio)](https://msdn.microsoft.com/library/bb625071).</span><span class="sxs-lookup"><span data-stu-id="aa524-136">For more information, see [Publish Wizard (Office Development in Visual Studio)](https://msdn.microsoft.com/library/bb625071).</span></span>  
  
3.  <span data-ttu-id="aa524-137">Nainstalujte aplikaci na počítač, na kterém jsou nainstalované rozhraní .NET Framework 4 nebo vyšší a jinou verzi aplikace Excel.</span><span class="sxs-lookup"><span data-stu-id="aa524-137">Install the application on a computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
4.  <span data-ttu-id="aa524-138">Po dokončení instalace spusťte nainstalovaný program.</span><span class="sxs-lookup"><span data-stu-id="aa524-138">When the installation is finished, run the installed program.</span></span>  
  
5.  <span data-ttu-id="aa524-139">Ověřit, že sešit aplikace Excel byl vytvořen v umístění zadaném v ukázkovém kódu: C:\SampleFolder\SampleWorkbook.xls.</span><span class="sxs-lookup"><span data-stu-id="aa524-139">Verify that an Excel workbook has been created at the location specified in the sample code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa524-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="aa524-140">See Also</span></span>  
 [<span data-ttu-id="aa524-141">Návod: Vložení typů z řízených sestavení v sadě Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="aa524-141">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
 [<span data-ttu-id="aa524-142">/ Link (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="aa524-142">/link (C# Compiler Options)</span></span>](../../../../csharp/language-reference/compiler-options/link-compiler-option.md)
