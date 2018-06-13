---
title: 'Návod: Vložení informací o typu ze sestavení sady Microsoft Office v sadě Visual Studio (C#)'
ms.date: 07/20/2015
ms.assetid: 3320e866-01f1-4b7f-8932-049a7b2d2a9b
ms.openlocfilehash: 8e7eb5c797ca87f87950d530112ec64f1327ae0c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324522"
---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-c"></a>Návod: Vložení informací o typu ze sestavení sady Microsoft Office v sadě Visual Studio (C#)
Pokud vložit informace typu v aplikaci, která odkazuje na objekty modelu COM, můžete eliminovat potřebu primární spolupracující sestavení (PIA). Informace o vložených typu navíc umožňuje dosáhnout nezávislost verze pro vaši aplikaci. To znamená váš program může být napsán používat typy z více verzí knihovny COM bez nutnosti konkrétní PIA – pro každou verzi. Toto je běžný scénář pro aplikace, které používají objekty z knihovny Microsoft Office. Vložení informací o typu umožňuje ve stejném sestavení programu pro práci s různými verzemi nástroje Microsoft Office na různých počítačích bez nutnosti znovu nasaďte program nebo PIA – pro každou verzi systému Microsoft Office.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 Tento postup vyžaduje následující:  
  
-   Počítač, na kterém jsou nainstalované sady Visual Studio a aplikaci Microsoft Excel.  
  
-   Druhý počítač, na kterém jsou nainstalované rozhraní .NET Framework 4 nebo vyšší a jinou verzi aplikace Excel.  
  
##  <a name="BKMK_createapp"></a> Chcete-li vytvořit aplikaci, která funguje s více verzemi systému Microsoft Office  
  
1.  Spuštění sady Visual Studio v počítači, na kterém je nainstalována aplikace Excel.  
  
2.  Na **soubor** nabídce zvolte **nový**, **projektu**.  
  
3.  V **nový projekt** dialogovém **typy projektů** podokně, ujistěte se, že **Windows** je vybrána. Vyberte **konzolové aplikace** v **šablony** podokně. V **název** zadejte `CreateExcelWorkbook`a potom zvolte **OK** tlačítko. Vytvoření nového projektu.  
  
4.  V **Průzkumníku řešení**, otevřete místní nabídku pro **odkazy** složku a potom zvolte **přidat odkaz na**.  
  
5.  Na **.NET** , zvolte nejnovější verzi `Microsoft.Office.Interop.Excel`. Například **Microsoft.Office.Interop.Excel 14.0.0.0**. Vyberte **OK** tlačítko.  
  
6.  V seznamu odkazů pro **CreateExcelWorkbook** projekt, vyberte odkaz pro `Microsoft.Office.Interop.Excel` kterou jste přidali v předchozím kroku. V **vlastnosti** okna, ujistěte se, že `Embed Interop Types` je nastavena na `True`.  
  
    > [!NOTE]
    >  Z důvodu informace o vložených zprostředkovatele komunikace s objekty typu spuštění aplikace vytvořené v tomto návodu s různými verzemi nástroje Microsoft Office. Pokud `Embed Interop Types` je nastavena na `False`, je nutné zahrnout PIA – pro každou verzi systému Microsoft Office, které aplikace poběží s.  
  
7.  Otevřete **Program.cs** souboru. Nahraďte kód v souboru s následujícím kódem:  
  
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
  
9. Stisknutím klávesy CTRL + F5 sestavit a spustit projekt. Ověřte, že sešit aplikace Excel byl vytvořen v umístění zadaném v ukázkový kód: C:\SampleFolder\SampleWorkbook.xls.  
  
##  <a name="BKMK_publishapp"></a> Publikování aplikace do počítače, na kterém je nainstalovaná jiná verze systému Microsoft Office  
  
1.  Otevřete projekt vytvořené tento návod v sadě Visual Studio.  
  
2.  Na **sestavení** nabídce zvolte **publikování CreateExcelWorkbook**. Postupujte podle kroků v Průvodci publikováním vytvořit instalovatelných verzi aplikace. Další informace najdete v tématu [Průvodci publikováním (vývoj pro Office v sadě Visual Studio)](https://msdn.microsoft.com/library/bb625071).  
  
3.  Nainstalujte aplikaci na počítač, na kterém jsou nainstalované rozhraní .NET Framework 4 nebo vyšší a jinou verzi aplikace Excel.  
  
4.  Po dokončení instalace spusťte nainstalovaný program.  
  
5.  Ověřit, že sešit aplikace Excel byl vytvořen v umístění zadaném v ukázkovém kódu: C:\SampleFolder\SampleWorkbook.xls.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Vložení typů z řízených sestavení v sadě Visual Studio (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
 [/ Link (možnosti kompilátoru C#)](../../../../csharp/language-reference/compiler-options/link-compiler-option.md)
