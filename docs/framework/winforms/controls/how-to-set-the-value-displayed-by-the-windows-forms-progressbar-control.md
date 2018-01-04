---
title: "Postupy: Nastavení hodnoty zobrazované ovládacím prvkem Windows Forms ProgressBar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ProgressBar control [Windows Forms], setting value displayed
- progress controls [Windows Forms], setting value displayed
ms.assetid: 0e5010ad-1e9a-4271-895e-5a3d24d37a26
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6ebca02e2084fdb7a76a9a9d711a0b0180f7a7f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a>Postupy: Nastavení hodnoty zobrazované ovládacím prvkem Windows Forms ProgressBar
> [!IMPORTANT]
>  <xref:System.Windows.Forms.ToolStripProgressBar> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.ProgressBar> řízení; však <xref:System.Windows.Forms.ProgressBar> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Nabízí několik různých způsobů k zobrazení dané hodnoty v rámci <xref:System.Windows.Forms.ProgressBar> ovládacího prvku. Jaký přístup zvolíte, bude záviset na na prováděné úloze nebo potíže, které jsou řešení. V následující tabulce jsou uvedeny přístupy, že můžete.  
  
|Přístup|Popis|  
|--------------|-----------------|  
|Nastavte hodnotu <xref:System.Windows.Forms.ProgressBar> řízení přímo.|Tento přístup je užitečný pro úlohy, pokud víte, celkový počet z položky měřená, který bude zahrnut, jako je například čtení záznamy ze zdroje dat. Kromě toho pokud potřebujete nastavit hodnotu jednou nebo dvakrát, to je snadný způsob, jak to provést. Nakonec použijte tento proces, pokud je nutné snížit hodnotu zobrazuje indikátor průběhu.|  
|Zvýšit <xref:System.Windows.Forms.ProgressBar> zobrazit podle pevnou hodnotu.|Tento přístup je užitečné, když jsou zobrazení jednoduché počet mezi minimální a maximální, jako je například uplynulý čas nebo počet souborů, které byly zpracovány mimo známé celkem.|  
|Zvýšit <xref:System.Windows.Forms.ProgressBar> zobrazí hodnotu, která se liší.|Tento přístup je užitečné, když budete muset změnit zobrazená hodnota několikrát v různých objemy. Příklad by zobrazuje množství místa na pevném disku spotřebovávanou při zápisu řady souborů na disk.|  
  
 Nejpřímějším způsobem, nastavte hodnotu zobrazuje indikátor průběhu, je nastavení <xref:System.Windows.Forms.ProgressBar.Value%2A> vlastnost. Tento krok můžete provést v době návrhu nebo za běhu.  
  
### <a name="to-set-the-progressbar-value-directly"></a>Chcete-li nastavit hodnotu ProgressBar přímo  
  
1.  Nastavte <xref:System.Windows.Forms.ProgressBar> ovládacího prvku <xref:System.Windows.Forms.ProgressBar.Minimum%2A> a <xref:System.Windows.Forms.ProgressBar.Maximum%2A> hodnoty.  
  
2.  V kódu nastavit ovládacího prvku <xref:System.Windows.Forms.ProgressBar.Value%2A> vlastnost na celočíselnou hodnotu mezi minimální a maximální hodnoty, které jste vytvořili.  
  
    > [!NOTE]
    >  Pokud nastavíte <xref:System.Windows.Forms.ProgressBar.Value%2A> vlastnost mimo hranice vytvořené <xref:System.Windows.Forms.ProgressBar.Minimum%2A> a <xref:System.Windows.Forms.ProgressBar.Maximum%2A> vlastností ovládacího prvku vyvolá <xref:System.ArgumentException> výjimka.  
  
     Následující příklad kódu ukazuje, jak nastavit <xref:System.Windows.Forms.ProgressBar> hodnotu přímo. Kód čte záznamy ze zdroje dat a aktualizuje indikátor průběhu a popisek pokaždé, když záznam dat je pro čtení. Tento příklad vyžaduje, aby svého formuláře <xref:System.Windows.Forms.Label> řízení, <xref:System.Windows.Forms.ProgressBar> řízení a tabulku dat s názvem řádek `CustomerRow` s `FirstName` a `LastName` pole.  
  
    ```vb  
    Public Sub CreateNewRecords()  
       ' Sets the progress bar's Maximum property to  
       ' the total number of records to be created.  
       ProgressBar1.Maximum = 20  
  
       ' Creates a new record in the dataset.  
       ' NOTE: The code below will not compile, it merely  
       ' illustrates how the progress bar would be used.  
       Dim anyRow As CustomerRow = DatasetName.ExistingTable.NewRow  
       anyRow.FirstName = "Stephen"  
       anyRow.LastName = "James"  
       ExistingTable.Rows.Add(anyRow)  
  
       ' Increases the value displayed by the progress bar.  
       ProgressBar1.Value += 1  
       ' Updates the label to show that a record was read.  
       Label1.Text = "Records Read = " & ProgressBar1.Value.ToString()  
    End Sub  
    ```  
  
    ```csharp  
    public void createNewRecords()  
    {  
       // Sets the progress bar's Maximum property to  
       // the total number of records to be created.  
       progressBar1.Maximum = 20;  
  
       // Creates a new record in the dataset.  
       // NOTE: The code below will not compile, it merely  
       // illustrates how the progress bar would be used.  
       CustomerRow anyRow = DatasetName.ExistingTable.NewRow();  
       anyRow.FirstName = "Stephen";  
       anyRow.LastName = "James";  
       ExistingTable.Rows.Add(anyRow);  
  
       // Increases the value displayed by the progress bar.  
       progressBar1.Value += 1;  
       // Updates the label to show that a record was read.  
       label1.Text = "Records Read = " + progressBar1.Value.ToString();  
    }  
    ```  
  
     Pokud jsou zobrazování průběhu, který pokračuje podle pevně zadaném intervalu, můžete nastavit hodnotu a pak volat metodu, která zvyšuje <xref:System.Windows.Forms.ProgressBar> ovládacího prvku hodnoty tohoto intervalu. To je užitečné pro časovače a v dalších scénářích, kde nejsou měření průběh jako procento celku.  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a>Pokud chcete zvýšit indikátoru průběhu pevnou hodnotou  
  
1.  Nastavte <xref:System.Windows.Forms.ProgressBar> ovládacího prvku <xref:System.Windows.Forms.ProgressBar.Minimum%2A> a <xref:System.Windows.Forms.ProgressBar.Maximum%2A> hodnoty.  
  
2.  Nastavte ovládacího prvku <xref:System.Windows.Forms.ProgressBar.Step%2A> vlastnost na celé číslo představující dobu, pokud chcete zvýšit indikátor průběhu zobrazena hodnota.  
  
3.  Volání <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> metoda ke změně hodnoty zobrazené velikostí nastavit <xref:System.Windows.Forms.ProgressBar.Step%2A> vlastnost.  
  
     Následující příklad kódu ukazuje, jak můžete indikátor průběhu udržovat počet souborů v operaci kopírování.  
  
     V následujícím příkladu je každý soubor pro čtení, do paměti, indikátor průběhu a popisek jsou aktualizovány tak, aby odrážela, že celkový počet souborů pro čtení. Tento příklad vyžaduje, aby svého formuláře <xref:System.Windows.Forms.Label> řízení a <xref:System.Windows.Forms.ProgressBar> ovládacího prvku.  
  
    ```vb  
    Public Sub LoadFiles()  
       ' Sets the progress bar's minimum value to a number representing  
       ' no operations complete -- in this case, no files read.  
       ProgressBar1.Minimum = 0  
       ' Sets the progress bar's maximum value to a number representing  
       ' all operations complete -- in this case, all five files read.  
       ProgressBar1.Maximum = 5  
       ' Sets the Step property to amount to increase with each iteration.  
       ' In this case, it will increase by one with every file read.  
       ProgressBar1.Step = 1  
  
       ' Dimensions a counter variable.  
       Dim i As Integer  
       ' Uses a For...Next loop to iterate through the operations to be  
       ' completed. In this case, five files are to be copied into memory,  
       ' so the loop will execute 5 times.  
       For i = 0 To 4  
          ' Insert code to copy a file  
          ProgressBar1.PerformStep()  
          ' Update the label to show that a file was read.  
          Label1.Text = "# of Files Read = " & ProgressBar1.Value.ToString  
       Next i  
    End Sub  
    ```  
  
    ```csharp  
    public void loadFiles()  
    {  
       // Sets the progress bar's minimum value to a number representing  
       // no operations complete -- in this case, no files read.  
       progressBar1.Minimum = 0;  
       // Sets the progress bar's maximum value to a number representing  
       // all operations complete -- in this case, all five files read.  
       progressBar1.Maximum = 5;  
       // Sets the Step property to amount to increase with each iteration.  
       // In this case, it will increase by one with every file read.  
       progressBar1.Step = 1;  
  
       // Uses a for loop to iterate through the operations to be  
       // completed. In this case, five files are to be copied into memory,  
       // so the loop will execute 5 times.  
       for (int i = 0; i <= 4; i++)  
       {  
          // Inserts code to copy a file  
          progressBar1.PerformStep();  
          // Updates the label to show that a file was read.  
          label1.Text = "# of Files Read = " + progressBar1.Value.ToString();  
       }  
    }  
    ```  
  
     Nakonec můžete zvýšit hodnotu tak, aby každý nárůst jedinečný velikost zobrazuje indikátor průběhu. To je užitečné, když jste se udržování přehledu o řady jedinečné operace, jako je zápis souborů různých velikostí pevného disku nebo měření průběh jako procento celku.  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a>Pokud chcete zvýšit indikátoru průběhu dynamické hodnotou  
  
1.  Nastavte <xref:System.Windows.Forms.ProgressBar> ovládacího prvku <xref:System.Windows.Forms.ProgressBar.Minimum%2A> a <xref:System.Windows.Forms.ProgressBar.Maximum%2A> hodnoty.  
  
2.  Volání <xref:System.Windows.Forms.ProgressBar.Increment%2A> metoda ke změně hodnoty zobrazí celé číslo, které zadáte.  
  
     Následující příklad kódu ukazuje, jak indikátor průběhu můžete vypočítat, kolik místa na disku jsou využívány během operace kopírování.  
  
     V následujícím příkladu jako soubory se zapisují na pevný disk, indikátor průběhu a popisek jsou aktualizovány tak, aby odrážela množství místa na pevném disku. Tento příklad vyžaduje, aby svého formuláře <xref:System.Windows.Forms.Label> řízení a <xref:System.Windows.Forms.ProgressBar> ovládacího prvku.  
  
    ```vb  
    Public Sub ReadFiles()  
       ' Sets the progress bar's minimum value to a number   
       ' representing the hard disk space before the files are read in.  
       ' You will most likely have to set this using a system call.  
       ' NOTE: The code below is meant to be an example and  
       ' will not compile.  
       ProgressBar1.Minimum = AvailableDiskSpace()  
       ' Sets the progress bar's maximum value to a number   
       ' representing the total hard disk space.  
       ' You will most likely have to set this using a system call.  
       ' NOTE: The code below is meant to be an example   
       ' and will not compile.  
       ProgressBar1.Maximum = TotalDiskSpace()  
  
       ' Dimension a counter variable.  
       Dim i As Integer  
       ' Uses a For...Next loop to iterate through the operations to be  
       ' completed. In this case, five files are to be written to the disk,  
       ' so it will execute the loop 5 times.  
       For i = 1 To 5  
          ' Insert code to read a file into memory and update file size.  
          ' Increases the progress bar's value based on the size of   
          ' the file currently being written.  
          ProgressBar1.Increment(FileSize)  
          ' Updates the label to show available drive space.  
          Label1.Text = "Current Disk Space Used = " &_   
          ProgressBar1.Value.ToString()  
       Next i  
    End Sub  
    ```  
  
    ```csharp  
    public void readFiles()  
    {  
       // Sets the progress bar's minimum value to a number   
       // representing the hard disk space before the files are read in.  
       // You will most likely have to set this using a system call.  
       // NOTE: The code below is meant to be an example and   
       // will not compile.  
       progressBar1.Minimum = AvailableDiskSpace();  
       // Sets the progress bar's maximum value to a number   
       // representing the total hard disk space.  
       // You will most likely have to set this using a system call.  
       // NOTE: The code below is meant to be an example   
       // and will not compile.  
       progressBar1.Maximum = TotalDiskSpace();  
  
       // Uses a for loop to iterate through the operations to be  
       // completed. In this case, five files are to be written  
       // to the disk, so it will execute the loop 5 times.  
       for (int i = 1; i<= 5; i++)  
       {  
          // Insert code to read a file into memory and update file size.  
          // Increases the progress bar's value based on the size of   
          // the file currently being written.  
          progressBar1.Increment(FileSize);  
          // Updates the label to show available drive space.  
          label1.Text = "Current Disk Space Used = " + progressBar1.Value.ToString();  
       }  
    }  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ProgressBar>  
 <xref:System.Windows.Forms.ToolStripProgressBar>  
 [Přehled ovládacího prvku ProgressBar](../../../../docs/framework/winforms/controls/progressbar-control-overview-windows-forms.md)  
 [Ovládací prvek ProgressBar](../../../../docs/framework/winforms/controls/progressbar-control-windows-forms.md)
