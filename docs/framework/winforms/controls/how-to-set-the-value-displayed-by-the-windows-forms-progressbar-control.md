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
ms.openlocfilehash: 292a70658e37839897b39d4d58fdf98903d2d963
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196876"
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a><span data-ttu-id="d2904-102">Postupy: Nastavení hodnoty zobrazované ovládacím prvkem Windows Forms ProgressBar</span><span class="sxs-lookup"><span data-stu-id="d2904-102">How to: Set the Value Displayed by the Windows Forms ProgressBar Control</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="d2904-103"><xref:System.Windows.Forms.ToolStripProgressBar> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.ProgressBar> řízení; však <xref:System.Windows.Forms.ProgressBar> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete.</span><span class="sxs-lookup"><span data-stu-id="d2904-103">The <xref:System.Windows.Forms.ToolStripProgressBar> control replaces and adds functionality to the <xref:System.Windows.Forms.ProgressBar> control; however, the <xref:System.Windows.Forms.ProgressBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="d2904-104">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Poskytuje několik různých způsobů, jak zobrazit předané hodnoty v rámci <xref:System.Windows.Forms.ProgressBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d2904-104">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] gives you several different ways to display a given value within the <xref:System.Windows.Forms.ProgressBar> control.</span></span> <span data-ttu-id="d2904-105">Jaký přístup zvolíte bude záviset na daný úkol nebo problém, který se řešení.</span><span class="sxs-lookup"><span data-stu-id="d2904-105">Which approach you choose will depend on the task at hand or the problem you are solving.</span></span> <span data-ttu-id="d2904-106">Následující tabulka uvádí přístupy, že kterou si zvolíte.</span><span class="sxs-lookup"><span data-stu-id="d2904-106">The following table shows the approaches you can choose.</span></span>  
  
|<span data-ttu-id="d2904-107">Přístup</span><span class="sxs-lookup"><span data-stu-id="d2904-107">Approach</span></span>|<span data-ttu-id="d2904-108">Popis</span><span class="sxs-lookup"><span data-stu-id="d2904-108">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="d2904-109">Nastavte hodnotu <xref:System.Windows.Forms.ProgressBar> řídit přímo.</span><span class="sxs-lookup"><span data-stu-id="d2904-109">Set the value of the <xref:System.Windows.Forms.ProgressBar> control directly.</span></span>|<span data-ttu-id="d2904-110">Tento přístup je užitečný pro úlohy, kdy víte celkový součet měřené položky, která bude zahrnuta, jako je čtení záznamů ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="d2904-110">This approach is useful for tasks where you know the total of the item measured that will be involved, such as reading records from a data source.</span></span> <span data-ttu-id="d2904-111">Kromě toho pokud potřebujete nastavit hodnotu jednou nebo dvakrát, toto je snadný způsob, jak to udělat.</span><span class="sxs-lookup"><span data-stu-id="d2904-111">Additionally, if you only need to set the value once or twice, this is an easy way to do it.</span></span> <span data-ttu-id="d2904-112">Nakonec použijte tento proces, pokud chcete snížit hodnotu zobrazuje indikátor průběhu.</span><span class="sxs-lookup"><span data-stu-id="d2904-112">Finally, use this process if you need to decrease the value displayed by the progress bar.</span></span>|  
|<span data-ttu-id="d2904-113">Zvětšit <xref:System.Windows.Forms.ProgressBar> zobrazit pevná hodnota.</span><span class="sxs-lookup"><span data-stu-id="d2904-113">Increase the <xref:System.Windows.Forms.ProgressBar> display by a fixed value.</span></span>|<span data-ttu-id="d2904-114">Tento přístup je užitečný, pokud zobrazujete jednoduché počtu mezi minimální a maximální, jako je například uplynulého času nebo počet souborů, které byly zpracovány z známé celkem.</span><span class="sxs-lookup"><span data-stu-id="d2904-114">This approach is useful when you are displaying a simple count between the minimum and maximum, such as elapsed time or the number of files that have been processed out of a known total.</span></span>|  
|<span data-ttu-id="d2904-115">Zvětšit <xref:System.Windows.Forms.ProgressBar> zobrazit tak hodnotu, která se liší.</span><span class="sxs-lookup"><span data-stu-id="d2904-115">Increase the <xref:System.Windows.Forms.ProgressBar> display by a value that varies.</span></span>|<span data-ttu-id="d2904-116">Tento přístup je užitečný, když budete chtít změnit zobrazenou hodnotu několikrát v různých částky.</span><span class="sxs-lookup"><span data-stu-id="d2904-116">This approach is useful when you need to change the displayed value a number of times in different amounts.</span></span> <span data-ttu-id="d2904-117">Příklad by se mělo množství místa na pevném disku spotřebovávanou při zápisu řadu souborů na disk.</span><span class="sxs-lookup"><span data-stu-id="d2904-117">An example would be showing the amount of hard-disk space being consumed while writing a series of files to the disk.</span></span>|  
  
 <span data-ttu-id="d2904-118">Nejpřímějším způsobem, nastavte hodnotu zobrazuje indikátor průběhu, je nastavení <xref:System.Windows.Forms.ProgressBar.Value%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d2904-118">The most direct way to set the value displayed by a progress bar is by setting the <xref:System.Windows.Forms.ProgressBar.Value%2A> property.</span></span> <span data-ttu-id="d2904-119">To můžete udělat v době návrhu nebo v době běhu.</span><span class="sxs-lookup"><span data-stu-id="d2904-119">This can be done either at design time or at run time.</span></span>  
  
### <a name="to-set-the-progressbar-value-directly"></a><span data-ttu-id="d2904-120">K nastavení hodnoty ProgressBar přímo</span><span class="sxs-lookup"><span data-stu-id="d2904-120">To set the ProgressBar value directly</span></span>  
  
1.  <span data-ttu-id="d2904-121">Nastavte <xref:System.Windows.Forms.ProgressBar> ovládacího prvku <xref:System.Windows.Forms.ProgressBar.Minimum%2A> a <xref:System.Windows.Forms.ProgressBar.Maximum%2A> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d2904-121">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2.  <span data-ttu-id="d2904-122">V kódu, nastavit u tohoto prvku <xref:System.Windows.Forms.ProgressBar.Value%2A> vlastnost na celočíselnou hodnotu mezi minimální a maximální hodnoty, které jste stanovili.</span><span class="sxs-lookup"><span data-stu-id="d2904-122">In code, set the control's <xref:System.Windows.Forms.ProgressBar.Value%2A> property to an integer value between the minimum and maximum values you have established.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2904-123">Pokud nastavíte <xref:System.Windows.Forms.ProgressBar.Value%2A> vlastnost mimo hranice vytvořené <xref:System.Windows.Forms.ProgressBar.Minimum%2A> a <xref:System.Windows.Forms.ProgressBar.Maximum%2A> vyvolá vlastností, ovládacího prvku <xref:System.ArgumentException> výjimky.</span><span class="sxs-lookup"><span data-stu-id="d2904-123">If you set the <xref:System.Windows.Forms.ProgressBar.Value%2A> property outside the boundaries established by the <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> properties, the control throws an <xref:System.ArgumentException> exception.</span></span>  
  
     <span data-ttu-id="d2904-124">Následující příklad kódu ukazuje, jak nastavit <xref:System.Windows.Forms.ProgressBar> hodnotu přímo.</span><span class="sxs-lookup"><span data-stu-id="d2904-124">The following code example illustrates how to set the <xref:System.Windows.Forms.ProgressBar> value directly.</span></span> <span data-ttu-id="d2904-125">Kód čte záznamy ze zdroje dat a aktualizuje indikátor průběhu a popisek pokaždé, když je záznam dat pro čtení.</span><span class="sxs-lookup"><span data-stu-id="d2904-125">The code reads records from a data source and updates the progress bar and label every time a data record is read.</span></span> <span data-ttu-id="d2904-126">Tento příklad vyžaduje, že váš formulář má <xref:System.Windows.Forms.Label> ovládací prvek, <xref:System.Windows.Forms.ProgressBar> ovládacího prvku a tabulku dat s názvem řádek `CustomerRow` s `FirstName` a `LastName` pole.</span><span class="sxs-lookup"><span data-stu-id="d2904-126">This example requires that your form has a <xref:System.Windows.Forms.Label> control, a <xref:System.Windows.Forms.ProgressBar> control, and a data table with a row called `CustomerRow` with `FirstName` and `LastName` fields.</span></span>  
  
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
  
     Pokud jsou zobrazení průběhu, který pokračuje v pevně zadaném intervalu, můžete nastavit hodnotu a poté zavolejte metodu, která se zvyšuje <xref:System.Windows.Forms.ProgressBar> hodnotu ovládacího prvku pomocí tohoto intervalu. <span data-ttu-id="d2904-128">To je užitečné pro časovačů a další scénáře, ve kterém nejsou měření průběhu jako procenta celku.</span><span class="sxs-lookup"><span data-stu-id="d2904-128">This is useful for timers and other scenarios where you are not measuring progress as a percentage of the whole.</span></span>  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a><span data-ttu-id="d2904-129">Indikátor průběhu zvýšit pevná hodnota</span><span class="sxs-lookup"><span data-stu-id="d2904-129">To increase the progress bar by a fixed value</span></span>  
  
1.  <span data-ttu-id="d2904-130">Nastavte <xref:System.Windows.Forms.ProgressBar> ovládacího prvku <xref:System.Windows.Forms.ProgressBar.Minimum%2A> a <xref:System.Windows.Forms.ProgressBar.Maximum%2A> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d2904-130">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2.  <span data-ttu-id="d2904-131">Nastavit u tohoto prvku <xref:System.Windows.Forms.ProgressBar.Step%2A> vlastnost na celé číslo představující dobu, zvětšete indikátoru průběhu zobrazí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d2904-131">Set the control's <xref:System.Windows.Forms.ProgressBar.Step%2A> property to an integer representing the amount to increase the progress bar's displayed value.</span></span>  
  
3.  <span data-ttu-id="d2904-132">Volání <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> metody, chcete-li změnit hodnoty zobrazené množství v <xref:System.Windows.Forms.ProgressBar.Step%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d2904-132">Call the <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> method to change the value displayed by the amount set in the <xref:System.Windows.Forms.ProgressBar.Step%2A> property.</span></span>  
  
     <span data-ttu-id="d2904-133">Následující příklad kódu ukazuje, jak můžete indikátor průběhu udržovat počet souborů v operaci kopírování.</span><span class="sxs-lookup"><span data-stu-id="d2904-133">The following code example illustrates how a progress bar can maintain a count of the files in a copy operation.</span></span>  
  
     <span data-ttu-id="d2904-134">V následujícím příkladu se jako každého souboru je načíst do paměti, indikátor průběhu a popisek se aktualizují tak, aby odrážely čtení celkový počet souborů.</span><span class="sxs-lookup"><span data-stu-id="d2904-134">In the following example, as each file is read into memory, the progress bar and label are updated to reflect the total files read.</span></span> <span data-ttu-id="d2904-135">Tento příklad vyžaduje, že váš formulář má <xref:System.Windows.Forms.Label> ovládacího prvku a <xref:System.Windows.Forms.ProgressBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d2904-135">This example requires that your form has a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.ProgressBar> control.</span></span>  
  
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
  
     Nakonec můžete zvýšit hodnotu tak, aby každý nárůst jedinečný částka zobrazuje indikátor průběhu. <span data-ttu-id="d2904-137">To je užitečné, když jste se neudržují přehled o řadě jedinečných operací, jako je například zápis souborů různých velikostí pevného disku nebo měření průběhu jako procenta celku.</span><span class="sxs-lookup"><span data-stu-id="d2904-137">This is useful when you are keeping track of a series of unique operations, such as writing files of different sizes to a hard disk, or measuring progress as a percentage of the whole.</span></span>  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a><span data-ttu-id="d2904-138">Indikátor průběhu zvýšit dynamické hodnoty</span><span class="sxs-lookup"><span data-stu-id="d2904-138">To increase the progress bar by a dynamic value</span></span>  
  
1.  <span data-ttu-id="d2904-139">Nastavte <xref:System.Windows.Forms.ProgressBar> ovládacího prvku <xref:System.Windows.Forms.ProgressBar.Minimum%2A> a <xref:System.Windows.Forms.ProgressBar.Maximum%2A> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d2904-139">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2.  <span data-ttu-id="d2904-140">Volání <xref:System.Windows.Forms.ProgressBar.Increment%2A> metoda ke změně hodnoty zobrazí celé číslo, které zadáte.</span><span class="sxs-lookup"><span data-stu-id="d2904-140">Call the <xref:System.Windows.Forms.ProgressBar.Increment%2A> method to change the value displayed by an integer you specify.</span></span>  
  
     <span data-ttu-id="d2904-141">Následující příklad kódu ukazuje, jak indikátor průběhu můžete vypočítat, kolik místa na disku se použil během operace kopírování.</span><span class="sxs-lookup"><span data-stu-id="d2904-141">The following code example illustrates how a progress bar can calculate how much disk space has been used during a copy operation.</span></span>  
  
     <span data-ttu-id="d2904-142">V následujícím příkladu jak každého souboru je zapsána do pevného disku, indikátor průběhu a popisek se aktualizují tak, aby odrážely množství volného místa na pevném disku.</span><span class="sxs-lookup"><span data-stu-id="d2904-142">In the following example, as each file is written to the hard disk, the progress bar and label are updated to reflect the amount of hard-disk space available.</span></span> <span data-ttu-id="d2904-143">Tento příklad vyžaduje, že váš formulář má <xref:System.Windows.Forms.Label> ovládacího prvku a <xref:System.Windows.Forms.ProgressBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d2904-143">This example requires that your form has a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.ProgressBar> control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d2904-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2904-144">See also</span></span>

- <xref:System.Windows.Forms.ProgressBar>
- <xref:System.Windows.Forms.ToolStripProgressBar>
- [<span data-ttu-id="d2904-145">Přehled ovládacího prvku ProgressBar</span><span class="sxs-lookup"><span data-stu-id="d2904-145">ProgressBar Control Overview</span></span>](progressbar-control-overview-windows-forms.md)
- [<span data-ttu-id="d2904-146">Ovládací prvek ProgressBar</span><span class="sxs-lookup"><span data-stu-id="d2904-146">ProgressBar Control</span></span>](progressbar-control-windows-forms.md)
