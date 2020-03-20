---
title: Nastavení hodnoty zobrazené ovládacím prvkem ProgressBar
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ProgressBar control [Windows Forms], setting value displayed
- progress controls [Windows Forms], setting value displayed
ms.assetid: 0e5010ad-1e9a-4271-895e-5a3d24d37a26
ms.openlocfilehash: d295079a96ca19a4e4c98e113a3f3051c6403182
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141808"
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a>Postupy: Nastavení hodnoty zobrazované ovládacím prvkem Windows Forms ProgressBar
> [!IMPORTANT]
> Ovládací <xref:System.Windows.Forms.ToolStripProgressBar> prvek nahradí a přidá <xref:System.Windows.Forms.ProgressBar> funkce ovládacího prvku; <xref:System.Windows.Forms.ProgressBar> ovládací prvek je však zachován a to jak pro zpětnou kompatibilitu, tak pro budoucí použití, pokud se rozhodnete.  
  
 Rozhraní .NET Framework poskytuje několik různých způsobů, <xref:System.Windows.Forms.ProgressBar> jak zobrazit danou hodnotu v rámci ovládacího prvku. Jaký přístup si vyberete, bude záviset na daném úkolu nebo na problému, který řešíte. V následující tabulce jsou uvedeny přístupy, které si můžete vybrat.  
  
|Přístup|Popis|  
|--------------|-----------------|  
|Nastavte hodnotu <xref:System.Windows.Forms.ProgressBar> ovládacího prvku přímo.|Tento přístup je užitečný pro úkoly, kde znáte součet měřené položky, která bude zapojena, jako je například čtení záznamů ze zdroje dat. Navíc pokud potřebujete nastavit hodnotu pouze jednou nebo dvakrát, je to snadný způsob, jak to udělat. Nakonec použijte tento proces, pokud potřebujete snížit hodnotu zobrazenou indikátorem průběhu.|  
|Zvětšete <xref:System.Windows.Forms.ProgressBar> zobrazení o pevnou hodnotu.|Tento přístup je užitečný, pokud zobrazujete jednoduchý počet mezi minimálním a maximálním, například uplynulý čas nebo počet souborů, které byly zpracovány ze známého součtu.|  
|Zvyšte <xref:System.Windows.Forms.ProgressBar> zobrazení o hodnotu, která se liší.|Tento přístup je užitečný, když potřebujete změnit zobrazenou hodnotu několikrát v různých částkách. Příkladem může být zobrazení množství místa na pevném disku spotřebované při zápisu řady souborů na disk.|  
  
 Nejpřímějším způsobem nastavení hodnoty zobrazené indikátorem průběhu <xref:System.Windows.Forms.ProgressBar.Value%2A> je nastavení vlastnosti. To lze provést buď v době návrhu nebo za běhu.  
  
### <a name="to-set-the-progressbar-value-directly"></a>Nastavení hodnoty ProgressBar přímo  
  
1. Nastavte <xref:System.Windows.Forms.ProgressBar> hodnoty <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ovládacího <xref:System.Windows.Forms.ProgressBar.Maximum%2A> prvku a hodnoty.  
  
2. V kódu nastavte vlastnost <xref:System.Windows.Forms.ProgressBar.Value%2A> ovládacího prvku na celou hodnotu mezi minimální a maximální hodnoty, které jste vytvořili.  
  
    > [!NOTE]
    > Pokud <xref:System.Windows.Forms.ProgressBar.Value%2A> nastavíte vlastnost mimo hranice <xref:System.Windows.Forms.ProgressBar.Minimum%2A> <xref:System.Windows.Forms.ProgressBar.Maximum%2A> stanovené vlastnosti a, <xref:System.ArgumentException> ovládací prvek vyvolá výjimku.  
  
     Následující příklad kódu ukazuje, jak <xref:System.Windows.Forms.ProgressBar> nastavit hodnotu přímo. Kód čte záznamy ze zdroje dat a aktualizuje indikátor průběhu a popisek při každém čtení datového záznamu. Tento příklad vyžaduje, aby <xref:System.Windows.Forms.Label> formulář <xref:System.Windows.Forms.ProgressBar> měl ovládací prvek, ovládací prvek `CustomerRow` `FirstName` a `LastName` tabulku dat s řádekem volaným s a poli.  
  
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
  
     Pokud zobrazujete průběh, který probíhá v pevném intervalu, můžete nastavit <xref:System.Windows.Forms.ProgressBar> hodnotu a potom volat metodu, která zvyšuje hodnotu ovládacího prvku o tento interval. To je užitečné pro časovače a další scénáře, kde neměříte průběh jako procento celku.  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a>Zvýšení indikátoru průběhu o pevnou hodnotu  
  
1. Nastavte <xref:System.Windows.Forms.ProgressBar> hodnoty <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ovládacího <xref:System.Windows.Forms.ProgressBar.Maximum%2A> prvku a hodnoty.  
  
2. Nastavte vlastnost ovládacího <xref:System.Windows.Forms.ProgressBar.Step%2A> prvku na celé číslo představující částku pro zvýšení zobrazené hodnoty indikátoru průběhu.  
  
3. Volání <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> metody změnit hodnotu zobrazenou částkou <xref:System.Windows.Forms.ProgressBar.Step%2A> nastavenou ve vlastnosti.  
  
     Následující příklad kódu ukazuje, jak může indikátor průběhu udržovat počet souborů v operaci kopírování.  
  
     V následujícím příkladu, jak každý soubor je číst do paměti, indikátor průběhu a popisek jsou aktualizovány tak, aby odrážely celkový počet přečtené soubory. Tento příklad vyžaduje, aby <xref:System.Windows.Forms.Label> formulář <xref:System.Windows.Forms.ProgressBar> měl ovládací prvek a ovládací prvek.  
  
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
  
     Nakonec můžete zvýšit hodnotu zobrazenou indikátorem průběhu tak, aby každé zvýšení bylo jedinečnou částkou. To je užitečné, když sledujete řadu jedinečných operací, jako je například zápis souborů různých velikostí na pevný disk nebo měření průběhu jako procento celku.  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a>Zvýšení indikátoru průběhu o dynamickou hodnotu  
  
1. Nastavte <xref:System.Windows.Forms.ProgressBar> hodnoty <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ovládacího <xref:System.Windows.Forms.ProgressBar.Maximum%2A> prvku a hodnoty.  
  
2. Voláním <xref:System.Windows.Forms.ProgressBar.Increment%2A> metody změňte hodnotu zobrazenou zadaným celé číslo.  
  
     Následující příklad kódu ukazuje, jak indikátor průběhu můžete vypočítat, kolik místa na disku bylo využito během operace kopírování.  
  
     V následujícím příkladu, jako každý soubor je zapsán na pevný disk, indikátor průběhu a popisek jsou aktualizovány tak, aby odrážely množství místa na pevném disku k dispozici. Tento příklad vyžaduje, aby <xref:System.Windows.Forms.Label> formulář <xref:System.Windows.Forms.ProgressBar> měl ovládací prvek a ovládací prvek.  
  
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

- <xref:System.Windows.Forms.ProgressBar>
- <xref:System.Windows.Forms.ToolStripProgressBar>
- [ProgressBar – přehled ovládacího prvku](progressbar-control-overview-windows-forms.md)
- [Ovládací prvek ProgressBar](progressbar-control-windows-forms.md)
