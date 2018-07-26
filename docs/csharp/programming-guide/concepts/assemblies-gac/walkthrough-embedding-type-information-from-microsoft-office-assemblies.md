---
title: 'Návod: Vložení informací o typu ze sestavení sady Microsoft Office v sadě Visual Studio (C#)'
ms.date: 07/20/2015
ms.assetid: 3320e866-01f1-4b7f-8932-049a7b2d2a9b
ms.openlocfilehash: 8e7eb5c797ca87f87950d530112ec64f1327ae0c
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2018
ms.locfileid: "39198494"
---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-c"></a>Návod: Vložení informací o typu ze sestavení sady Microsoft Office v sadě Visual Studio (C#)
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
  
4.  V **Průzkumníka řešení**, otevřete místní nabídku **odkazy** složky a klikněte na tlačítko **přidat odkaz**.  
  
5.  Na **.NET** kartu, zvolte nejnovější verzi `Microsoft.Office.Interop.Excel`. Například **Microsoft.Office.Interop.Excel 14.0.0.0**. Zvolte **OK** tlačítko.  
  
6.  V seznamu odkazů pro **CreateExcelWorkbook** projektu, vyberte odkaz pro `Microsoft.Office.Interop.Excel` , který jste přidali v předchozím kroku. V **vlastnosti** okno, ujistěte se, že `Embed Interop Types` je nastavena na `True`.  
  
    > [!NOTE]
    >  Aplikace vytvořené v tomto názorném postupu se spouští s různými verzemi sady Microsoft Office z důvodu informace o vloženém typu spolupráce. Pokud `Embed Interop Types` je nastavena na `False`, musíte zahrnout PIA pro každou verzi sady Microsoft Office, která bude aplikace spuštěna s.  
  
7.  Otevřít **Program.cs** souboru. Nahraďte kód v souboru následujícím kódem:  
  
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
  
8.  Uložte projekt.  
  
9. Stisknutím kláves CTRL + F5 sestavte a spusťte projekt. Ověřte, zda byl vytvořen sešit aplikace Excel v umístění zadaném v příkladu kódu: C:\SampleFolder\SampleWorkbook.xls.  
  
##  <a name="BKMK_publishapp"></a> K publikování aplikace na počítači, na kterém je nainstalovaná jiná verze systému Microsoft Office  
  
1.  Otevřete projekt vytvořený v rámci tohoto návodu v sadě Visual Studio.  
  
2.  Na **sestavení** nabídce zvolte **publikovat CreateExcelWorkbook**. Postupujte podle kroků v Průvodci publikováním vytvoření instalovatelnou verzi aplikace. Další informace najdete v tématu [Průvodce publikováním (vývoj pro Office v sadě Visual Studio)](https://msdn.microsoft.com/library/bb625071).  
  
3.  Nainstalujte aplikace na počítači, na kterém je nainstalováno rozhraní .NET Framework 4 nebo vyšší a jinou verzi aplikace Excel.  
  
4.  Po dokončení instalace spusťte nainstalovaný program.  
  
5.  Ověřte, zda byl vytvořen sešit aplikace Excel v umístění zadaném ve vzorovém kódu: C:\SampleFolder\SampleWorkbook.xls.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
 [/ Link (možnosti kompilátoru C#)](../../../../csharp/language-reference/compiler-options/link-compiler-option.md)
