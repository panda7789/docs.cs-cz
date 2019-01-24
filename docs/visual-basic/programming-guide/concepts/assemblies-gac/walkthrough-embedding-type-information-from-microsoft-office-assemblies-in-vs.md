---
title: 'Průvodce: Vložení informací o typu ze sestavení sady Microsoft Office v sadě Visual Studio (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 26b44286-5066-4ad4-8e6a-c24902be347c
ms.openlocfilehash: e5b94c190a77f6877c9a3d37f310aa527083a26a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722774"
---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-visual-basic"></a>Průvodce: Vložení informací o typu ze sestavení sady Microsoft Office v sadě Visual Studio (Visual Basic)
Je-li vložit informace o typu v aplikaci, která odkazuje na objekty modelu COM, můžete vyloučit potřebu primárního sestavení interop (PIA). Kromě toho informace o typu embedded vám umožní dosáhnout nezávislosti na verzi pro vaši aplikaci. To znamená váš program může zapisovat používat typy z více verzí knihovny COM bez nutnosti zvláštního PIA pro každou verzi. Toto je běžný scénář pro aplikace, které používají objekty z knihoven Microsoft Office. Vložení informací o typu umožňuje jednomu sestavení programu pracovat s různými verzemi sady Microsoft Office na různých počítačích bez nutnosti znovu nasazovat program nebo PIA pro každou verzi sady Microsoft Office.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 Tento postup vyžaduje následující:  
  
-   Počítač, na kterém je nainstalováno Visual Studio a Microsoft Excelu.  
  
-   Druhý počítač, na kterém je nainstalováno rozhraní .NET Framework 4 nebo vyšší a jinou verzi aplikace Excel.  
  
##  <a name="BKMK_createapp"></a> Chcete-li vytvořit aplikaci, která pracuje s více verzemi sady Microsoft Office  
  
1.  Spusťte sadu Visual Studio na počítači, na kterém je nainstalována aplikace Excel.  
  
2.  Na **souboru** nabídce zvolte **nový**, **projektu**.  
  
3.  V **nový projekt** v dialogu **typy projektů** podokno, ujistěte se, že **Windows** zaškrtnuto. Vyberte **konzolovou aplikaci** v **šablony** podokně. V **název** zadejte `CreateExcelWorkbook`a klikněte na tlačítko **OK** tlačítko. Vytvoření nového projektu.  
  
4.  Otevřete místní nabídku pro projekt CreateExcelWorkbook a pak zvolte **vlastnosti**. Zvolte **odkazy** kartu. Zvolte **přidat** tlačítko.  
  
5.  Na **.NET** kartu, zvolte nejnovější verzi `Microsoft.Office.Interop.Excel`. Například **Microsoft.Office.Interop.Excel 14.0.0.0**. Zvolte **OK** tlačítko.  
  
6.  V seznamu odkazů pro **CreateExcelWorkbook** projektu, vyberte odkaz pro `Microsoft.Office.Interop.Excel` , který jste přidali v předchozím kroku. V **vlastnosti** okno, ujistěte se, že `Embed Interop Types` je nastavena na `True`.  
  
    > [!NOTE]
    >  Aplikace vytvořené v tomto názorném postupu se spouští s různými verzemi sady Microsoft Office z důvodu informace o vloženém typu spolupráce. Pokud `Embed Interop Types` je nastavena na `False`, musíte zahrnout PIA pro každou verzi sady Microsoft Office, která bude aplikace spuštěna s.  
  
7.  Otevřete soubor Module1.vb. Nahraďte kód v souboru následujícím kódem:  
  
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
  
9. Stisknutím kláves CTRL + F5 sestavte a spusťte projekt. Ověřte, zda byl vytvořen sešit aplikace Excel v umístění zadaném v příkladu kódu: C:\SampleFolder\SampleWorkbook.xls.  
  
##  <a name="BKMK_publishapp"></a> K publikování aplikace na počítači, na kterém je nainstalovaná jiná verze systému Microsoft Office  
  
1.  Otevřete projekt vytvořený v rámci tohoto návodu v sadě Visual Studio.  
  
2.  Na **sestavení** nabídce zvolte **publikovat CreateExcelWorkbook**. Postupujte podle kroků v Průvodci publikováním vytvoření instalovatelnou verzi aplikace. Další informace najdete v tématu [Průvodce publikováním (vývoj pro Office v sadě Visual Studio)](/visualstudio/vsto/publish-wizard-office-development-in-visual-studio).  
  
3.  Nainstalujte aplikace na počítači, na kterém je nainstalováno rozhraní .NET Framework 4 nebo vyšší a jinou verzi aplikace Excel.  
  
4.  Po dokončení instalace spusťte nainstalovaný program.  
  
5.  Ověřte, zda byl vytvořen sešit aplikace Excel v umístění zadaném ve vzorovém kódu: C:\SampleFolder\SampleWorkbook.xls.  
  
## <a name="see-also"></a>Viz také:

- [Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [/ Link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md)
