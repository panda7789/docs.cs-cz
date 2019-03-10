---
title: 'Postupy: Nastavení hodnoty zobrazované v ovládacím prvku Windows Forms ProgressBar'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ProgressBar control [Windows Forms], setting value displayed
- progress controls [Windows Forms], setting value displayed
ms.assetid: 0e5010ad-1e9a-4271-895e-5a3d24d37a26
ms.openlocfilehash: a889d6e5cd40833353c1b294031621b7b289ac4d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715890"
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a>Postupy: Nastavení hodnoty zobrazované v ovládacím prvku Windows Forms ProgressBar
> [!IMPORTANT]
>  <xref:System.Windows.Forms.ToolStripProgressBar> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.ProgressBar> řízení; však <xref:System.Windows.Forms.ProgressBar> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Poskytuje několik různých způsobů, jak zobrazit předané hodnoty v rámci <xref:System.Windows.Forms.ProgressBar> ovládacího prvku. Jaký přístup zvolíte bude záviset na daný úkol nebo problém, který se řešení. Následující tabulka uvádí přístupy, že kterou si zvolíte.  
  
|Přístup|Popis|  
|--------------|-----------------|  
|Nastavte hodnotu <xref:System.Windows.Forms.ProgressBar> řídit přímo.|Tento přístup je užitečný pro úlohy, kdy víte celkový součet měřené položky, která bude zahrnuta, jako je čtení záznamů ze zdroje dat. Kromě toho pokud potřebujete nastavit hodnotu jednou nebo dvakrát, toto je snadný způsob, jak to udělat. Nakonec použijte tento proces, pokud chcete snížit hodnotu zobrazuje indikátor průběhu.|  
|Zvětšit <xref:System.Windows.Forms.ProgressBar> zobrazit pevná hodnota.|Tento přístup je užitečný, pokud zobrazujete jednoduché počtu mezi minimální a maximální, jako je například uplynulého času nebo počet souborů, které byly zpracovány z známé celkem.|  
|Zvětšit <xref:System.Windows.Forms.ProgressBar> zobrazit tak hodnotu, která se liší.|Tento přístup je užitečný, když budete chtít změnit zobrazenou hodnotu několikrát v různých částky. Příklad by se mělo množství místa na pevném disku spotřebovávanou při zápisu řadu souborů na disk.|  
  
 Nejpřímějším způsobem, nastavte hodnotu zobrazuje indikátor průběhu, je nastavení <xref:System.Windows.Forms.ProgressBar.Value%2A> vlastnost. To můžete udělat v době návrhu nebo v době běhu.  
  
### <a name="to-set-the-progressbar-value-directly"></a>K nastavení hodnoty ProgressBar přímo  
  
1.  Nastavte <xref:System.Windows.Forms.ProgressBar> ovládacího prvku <xref:System.Windows.Forms.ProgressBar.Minimum%2A> a <xref:System.Windows.Forms.ProgressBar.Maximum%2A> hodnoty.  
  
2.  V kódu, nastavit u tohoto prvku <xref:System.Windows.Forms.ProgressBar.Value%2A> vlastnost na celočíselnou hodnotu mezi minimální a maximální hodnoty, které jste stanovili.  
  
    > [!NOTE]
    >  Pokud nastavíte <xref:System.Windows.Forms.ProgressBar.Value%2A> vlastnost mimo hranice vytvořené <xref:System.Windows.Forms.ProgressBar.Minimum%2A> a <xref:System.Windows.Forms.ProgressBar.Maximum%2A> vyvolá vlastností, ovládacího prvku <xref:System.ArgumentException> výjimky.  
  
     Následující příklad kódu ukazuje, jak nastavit <xref:System.Windows.Forms.ProgressBar> hodnotu přímo. Kód čte záznamy ze zdroje dat a aktualizuje indikátor průběhu a popisek pokaždé, když je záznam dat pro čtení. Tento příklad vyžaduje, že váš formulář má <xref:System.Windows.Forms.Label> ovládací prvek, <xref:System.Windows.Forms.ProgressBar> ovládacího prvku a tabulku dat s názvem řádek `CustomerRow` s `FirstName` a `LastName` pole.  
  
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
  
     Pokud jsou zobrazení průběhu, který pokračuje v pevně zadaném intervalu, můžete nastavit hodnotu a poté zavolejte metodu, která se zvyšuje <xref:System.Windows.Forms.ProgressBar> hodnotu ovládacího prvku pomocí tohoto intervalu. To je užitečné pro časovačů a další scénáře, ve kterém nejsou měření průběhu jako procenta celku.  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a>Indikátor průběhu zvýšit pevná hodnota  
  
1.  Nastavte <xref:System.Windows.Forms.ProgressBar> ovládacího prvku <xref:System.Windows.Forms.ProgressBar.Minimum%2A> a <xref:System.Windows.Forms.ProgressBar.Maximum%2A> hodnoty.  
  
2.  Nastavit u tohoto prvku <xref:System.Windows.Forms.ProgressBar.Step%2A> vlastnost na celé číslo představující dobu, zvětšete indikátoru průběhu zobrazí hodnotu.  
  
3.  Volání <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> metody, chcete-li změnit hodnoty zobrazené množství v <xref:System.Windows.Forms.ProgressBar.Step%2A> vlastnost.  
  
     Následující příklad kódu ukazuje, jak můžete indikátor průběhu udržovat počet souborů v operaci kopírování.  
  
     V následujícím příkladu se jako každého souboru je načíst do paměti, indikátor průběhu a popisek se aktualizují tak, aby odrážely čtení celkový počet souborů. Tento příklad vyžaduje, že váš formulář má <xref:System.Windows.Forms.Label> ovládacího prvku a <xref:System.Windows.Forms.ProgressBar> ovládacího prvku.  
  
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
  
     Nakonec můžete zvýšit hodnotu tak, aby každý nárůst jedinečný částka zobrazuje indikátor průběhu. To je užitečné, když jste se neudržují přehled o řadě jedinečných operací, jako je například zápis souborů různých velikostí pevného disku nebo měření průběhu jako procenta celku.  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a>Indikátor průběhu zvýšit dynamické hodnoty  
  
1.  Nastavte <xref:System.Windows.Forms.ProgressBar> ovládacího prvku <xref:System.Windows.Forms.ProgressBar.Minimum%2A> a <xref:System.Windows.Forms.ProgressBar.Maximum%2A> hodnoty.  
  
2.  Volání <xref:System.Windows.Forms.ProgressBar.Increment%2A> metoda ke změně hodnoty zobrazí celé číslo, které zadáte.  
  
     Následující příklad kódu ukazuje, jak indikátor průběhu můžete vypočítat, kolik místa na disku se použil během operace kopírování.  
  
     V následujícím příkladu jak každého souboru je zapsána do pevného disku, indikátor průběhu a popisek se aktualizují tak, aby odrážely množství volného místa na pevném disku. Tento příklad vyžaduje, že váš formulář má <xref:System.Windows.Forms.Label> ovládacího prvku a <xref:System.Windows.Forms.ProgressBar> ovládacího prvku.  
  
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
