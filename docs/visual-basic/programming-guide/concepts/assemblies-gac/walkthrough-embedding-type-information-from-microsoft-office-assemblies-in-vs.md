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
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-visual-basic"></a>Návod: Vložení informací o typu ze sestavení sady Microsoft Office v sadě Visual Studio (Visual Basic)
Pokud vložit informace typu v aplikaci, která odkazuje na objekty modelu COM, můžete eliminovat potřebu primární spolupracující sestavení (PIA). Informace o vložených typu navíc umožňuje dosáhnout nezávislost verze pro vaši aplikaci. To znamená váš program může být napsán používat typy z více verzí knihovny COM bez nutnosti konkrétní PIA – pro každou verzi. Toto je běžný scénář pro aplikace, které používají objekty z knihovny Microsoft Office. Vložení informací o typu umožňuje ve stejném sestavení programu pro práci s různými verzemi nástroje Microsoft Office na různých počítačích bez nutnosti znovu nasaďte program nebo PIA – pro každou verzi systému Microsoft Office.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 Tento postup vyžaduje následující:  
  
-   Počítač, na kterém jsou nainstalované sady Visual Studio a aplikaci Microsoft Excel.  
  
-   Druhý počítač, na kterém jsou nainstalované rozhraní .NET Framework 4 nebo vyšší a jinou verzi aplikace Excel.  
  
##  <a name="BKMK_createapp"></a>Chcete-li vytvořit aplikaci, která funguje s více verzemi systému Microsoft Office  
  
1.  Spuštění sady Visual Studio v počítači, na kterém je nainstalována aplikace Excel.  
  
2.  Na **soubor** nabídce zvolte **nový**, **projektu**.  
  
3.  V **nový projekt** dialogovém **typy projektů** podokně, ujistěte se, že **Windows** je vybrána. Vyberte **konzolové aplikace** v **šablony** podokně. V **název** zadejte `CreateExcelWorkbook`a potom zvolte **OK** tlačítko. Vytvoření nového projektu.  
  
4.  Otevřete místní nabídky projektu CreateExcelWorkbook a zvolte **vlastnosti**. Vyberte **odkazy** kartě. Vyberte **přidat** tlačítko.  
  
5.  Na **.NET** , zvolte nejnovější verzi `Microsoft.Office.Interop.Excel`. Například **Microsoft.Office.Interop.Excel 14.0.0.0**. Vyberte **OK** tlačítko.  
  
6.  V seznamu odkazů pro **CreateExcelWorkbook** projekt, vyberte odkaz pro `Microsoft.Office.Interop.Excel` kterou jste přidali v předchozím kroku. V **vlastnosti** okna, ujistěte se, že `Embed Interop Types` je nastavena na `True`.  
  
    > [!NOTE]
    >  Z důvodu informace o vložených zprostředkovatele komunikace s objekty typu spuštění aplikace vytvořené v tomto návodu s různými verzemi nástroje Microsoft Office. Pokud `Embed Interop Types` je nastavena na `False`, je nutné zahrnout PIA – pro každou verzi systému Microsoft Office, které aplikace poběží s.  
  
7.  Otevřete soubor Module1.vb. Nahraďte kód v souboru s následujícím kódem:  
  
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
  
8.  Uložte projekt.  
  
9. Stisknutím klávesy CTRL + F5 sestavit a spustit projekt. Ověřte, že sešit aplikace Excel byl vytvořen v umístění zadaném v ukázkový kód: C:\SampleFolder\SampleWorkbook.xls.  
  
##  <a name="BKMK_publishapp"></a>Publikování aplikace do počítače, na kterém je nainstalovaná jiná verze systému Microsoft Office  
  
1.  Otevřete projekt vytvořené tento návod v sadě Visual Studio.  
  
2.  Na **sestavení** nabídce zvolte **publikování CreateExcelWorkbook**. Postupujte podle kroků v Průvodci publikováním vytvořit instalovatelných verzi aplikace. Další informace najdete v tématu [Průvodci publikováním (vývoj pro Office v sadě Visual Studio)](https://msdn.microsoft.com/library/bb625071).  
  
3.  Nainstalujte aplikaci na počítač, na kterém jsou nainstalované rozhraní .NET Framework 4 nebo vyšší a jinou verzi aplikace Excel.  
  
4.  Po dokončení instalace spusťte nainstalovaný program.  
  
5.  Ověřit, že sešit aplikace Excel byl vytvořen v umístění zadaném v ukázkovém kódu: C:\SampleFolder\SampleWorkbook.xls.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Vložení typů z řízených sestavení v sadě Visual Studio (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)  
 [/ Link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md)
