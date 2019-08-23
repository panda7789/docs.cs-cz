---
title: 'Postupy: Nastavení hodnoty zobrazované ovládacím prvkem Windows Forms ProgressBar'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ProgressBar control [Windows Forms], setting value displayed
- progress controls [Windows Forms], setting value displayed
ms.assetid: 0e5010ad-1e9a-4271-895e-5a3d24d37a26
ms.openlocfilehash: 2e0134206ba3ebdce35f5374cbad575e34483d58
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956081"
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a>Postupy: Nastavení hodnoty zobrazované ovládacím prvkem Windows Forms ProgressBar
> [!IMPORTANT]
> Ovládací prvek nahrazuje a přidává funkce <xref:System.Windows.Forms.ProgressBar> <xref:System.Windows.Forms.ProgressBar> ovládacímu prvku. ovládací prvek je však ponechán pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. <xref:System.Windows.Forms.ToolStripProgressBar>  
  
 .NET Framework poskytuje několik různých způsobů zobrazení dané hodnoty v rámci <xref:System.Windows.Forms.ProgressBar> ovládacího prvku. Jaký přístup zvolíte, bude záviset na úloze nebo na problému, který řešíte. Následující tabulka uvádí přístupy, které můžete zvolit.  
  
|Přístup|Popis|  
|--------------|-----------------|  
|Nastavte hodnotu <xref:System.Windows.Forms.ProgressBar> ovládacího prvku přímo.|Tento přístup je užitečný pro úlohy, u kterých víte, že celkový počet měřených položek, které budou zahrnuty, jako je například čtení záznamů ze zdroje dat. Kromě toho, pokud potřebujete pouze nastavit hodnotu pouze jednou nebo dvakrát, je to jednoduchý způsob, jak to provést. Nakonec tento postup použijte v případě, že potřebujete snížit hodnotu zobrazenou indikátorem průběhu.|  
|<xref:System.Windows.Forms.ProgressBar> Zvětšit zobrazení na pevnou hodnotu.|Tento přístup je užitečný, když zobrazujete jednoduchý počet mezi minimální a maximální, například uplynulý čas nebo počet souborů, které byly zpracovány ze známého celku.|  
|<xref:System.Windows.Forms.ProgressBar> Zvětšit zobrazení o hodnotu, která se liší.|Tento přístup je užitečný v případě, že potřebujete změnit zobrazenou hodnotu v různých částkách. V příkladu se zobrazilo množství místa na pevném disku, které se spotřebovává při zápisu řady souborů na disk.|  
  
 Nejpřímější způsob, jak nastavit hodnotu zobrazenou indikátorem průběhu, je nastavením <xref:System.Windows.Forms.ProgressBar.Value%2A> vlastnosti. To lze provést buď v době návrhu, nebo v době běhu.  
  
### <a name="to-set-the-progressbar-value-directly"></a>Nastavení hodnoty ProgressBar přímo  
  
1. <xref:System.Windows.Forms.ProgressBar> Nastavte ovládacíprvek<xref:System.Windows.Forms.ProgressBar.Maximum%2A>ahodnoty. <xref:System.Windows.Forms.ProgressBar.Minimum%2A>  
  
2. V kódu nastavte <xref:System.Windows.Forms.ProgressBar.Value%2A> vlastnost ovládacího prvku na celočíselnou hodnotu mezi minimální a maximální hodnotou, kterou jste nastavili.  
  
    > [!NOTE]
    > Pokud nastavíte <xref:System.Windows.Forms.ProgressBar.Value%2A> vlastnost mimo hranice zřízené <xref:System.Windows.Forms.ProgressBar.Minimum%2A> vlastnostmi a <xref:System.Windows.Forms.ProgressBar.Maximum%2A> , vyvolá <xref:System.ArgumentException> ovládací prvek výjimku.  
  
     Následující příklad kódu ukazuje, jak nastavit <xref:System.Windows.Forms.ProgressBar> hodnotu přímo. Kód přečte záznamy ze zdroje dat a při každém čtení záznamu dat aktualizuje indikátor průběhu a popisek. Tento příklad vyžaduje <xref:System.Windows.Forms.Label> , aby formulář měl ovládací prvek <xref:System.Windows.Forms.ProgressBar> , ovládací prvek a tabulku dat, která má řádek s názvem `CustomerRow` `FirstName` a `LastName` pole.  
  
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
  
     Pokud zobrazujete průběh, který pokračuje pevným intervalem, můžete nastavit hodnotu a pak zavolat metodu, která zvýší <xref:System.Windows.Forms.ProgressBar> hodnotu ovládacího prvku o tento interval. To je užitečné pro časovače a další scénáře, kdy neměříte průběh jako procento celého celku.  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a>Postup zvýšení hodnoty indikátoru průběhu na pevnou hodnotu  
  
1. <xref:System.Windows.Forms.ProgressBar> Nastavte ovládacíprvek<xref:System.Windows.Forms.ProgressBar.Maximum%2A>ahodnoty. <xref:System.Windows.Forms.ProgressBar.Minimum%2A>  
  
2. Nastavte <xref:System.Windows.Forms.ProgressBar.Step%2A> vlastnost ovládacího prvku na celé číslo představující množství pro zvýšení zobrazené hodnoty indikátoru průběhu.  
  
3. Zavolejte metodu pro změnu hodnoty zobrazené <xref:System.Windows.Forms.ProgressBar.Step%2A> v rámci nastaveného množství ve vlastnosti. <xref:System.Windows.Forms.ProgressBar.PerformStep%2A>  
  
     Následující příklad kódu ukazuje, jak může indikátor průběhu udržovat počet souborů v operaci kopírování.  
  
     V následujícím příkladu jsou jednotlivé soubory čteny do paměti, indikátor průběhu a popisek jsou aktualizovány tak, aby odrážely celkový počet čtených souborů. Tento příklad vyžaduje, aby formulář měl <xref:System.Windows.Forms.Label> ovládací prvek <xref:System.Windows.Forms.ProgressBar> a ovládací prvek.  
  
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
  
     Nakonec můžete zvýšit hodnotu zobrazenou indikátorem průběhu, aby každé zvýšení bylo jedinečné. To je užitečné v případě, že sledujete řadu jedinečných operací, například zápis souborů různých velikostí na pevný disk nebo měření postupu v procentech celého celku.  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a>Postup při zvýšení hodnoty indikátoru průběhu dynamickou hodnotou  
  
1. <xref:System.Windows.Forms.ProgressBar> Nastavte ovládacíprvek<xref:System.Windows.Forms.ProgressBar.Maximum%2A>ahodnoty. <xref:System.Windows.Forms.ProgressBar.Minimum%2A>  
  
2. <xref:System.Windows.Forms.ProgressBar.Increment%2A> Zavolejte metodu pro změnu hodnoty zobrazené podle celého čísla, které zadáte.  
  
     Následující příklad kódu ukazuje, jak může indikátor průběhu vypočítat, kolik místa na disku bylo během operace kopírování použito.  
  
     V následujícím příkladu se při zápisu jednotlivých souborů na pevný disk aktualizuje indikátor průběhu a popisek tak, aby odráželo množství dostupného místa na pevném disku. Tento příklad vyžaduje, aby formulář měl <xref:System.Windows.Forms.Label> ovládací prvek <xref:System.Windows.Forms.ProgressBar> a ovládací prvek.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ProgressBar>
- <xref:System.Windows.Forms.ToolStripProgressBar>
- [Přehled ovládacího prvku ProgressBar](progressbar-control-overview-windows-forms.md)
- [Ovládací prvek ProgressBar](progressbar-control-windows-forms.md)
