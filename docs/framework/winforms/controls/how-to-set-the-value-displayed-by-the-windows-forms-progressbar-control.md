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
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a><span data-ttu-id="5f3ab-102">Postupy: Nastavení hodnoty zobrazované ovládacím prvkem Windows Forms ProgressBar</span><span class="sxs-lookup"><span data-stu-id="5f3ab-102">How to: Set the Value Displayed by the Windows Forms ProgressBar Control</span></span>
> [!IMPORTANT]
> <span data-ttu-id="5f3ab-103">Ovládací <xref:System.Windows.Forms.ToolStripProgressBar> prvek nahradí a přidá <xref:System.Windows.Forms.ProgressBar> funkce ovládacího prvku; <xref:System.Windows.Forms.ProgressBar> ovládací prvek je však zachován a to jak pro zpětnou kompatibilitu, tak pro budoucí použití, pokud se rozhodnete.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-103">The <xref:System.Windows.Forms.ToolStripProgressBar> control replaces and adds functionality to the <xref:System.Windows.Forms.ProgressBar> control; however, the <xref:System.Windows.Forms.ProgressBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="5f3ab-104">Rozhraní .NET Framework poskytuje několik různých způsobů, <xref:System.Windows.Forms.ProgressBar> jak zobrazit danou hodnotu v rámci ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-104">The .NET Framework gives you several different ways to display a given value within the <xref:System.Windows.Forms.ProgressBar> control.</span></span> <span data-ttu-id="5f3ab-105">Jaký přístup si vyberete, bude záviset na daném úkolu nebo na problému, který řešíte.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-105">Which approach you choose will depend on the task at hand or the problem you are solving.</span></span> <span data-ttu-id="5f3ab-106">V následující tabulce jsou uvedeny přístupy, které si můžete vybrat.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-106">The following table shows the approaches you can choose.</span></span>  
  
|<span data-ttu-id="5f3ab-107">Přístup</span><span class="sxs-lookup"><span data-stu-id="5f3ab-107">Approach</span></span>|<span data-ttu-id="5f3ab-108">Popis</span><span class="sxs-lookup"><span data-stu-id="5f3ab-108">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="5f3ab-109">Nastavte hodnotu <xref:System.Windows.Forms.ProgressBar> ovládacího prvku přímo.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-109">Set the value of the <xref:System.Windows.Forms.ProgressBar> control directly.</span></span>|<span data-ttu-id="5f3ab-110">Tento přístup je užitečný pro úkoly, kde znáte součet měřené položky, která bude zapojena, jako je například čtení záznamů ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-110">This approach is useful for tasks where you know the total of the item measured that will be involved, such as reading records from a data source.</span></span> <span data-ttu-id="5f3ab-111">Navíc pokud potřebujete nastavit hodnotu pouze jednou nebo dvakrát, je to snadný způsob, jak to udělat.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-111">Additionally, if you only need to set the value once or twice, this is an easy way to do it.</span></span> <span data-ttu-id="5f3ab-112">Nakonec použijte tento proces, pokud potřebujete snížit hodnotu zobrazenou indikátorem průběhu.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-112">Finally, use this process if you need to decrease the value displayed by the progress bar.</span></span>|  
|<span data-ttu-id="5f3ab-113">Zvětšete <xref:System.Windows.Forms.ProgressBar> zobrazení o pevnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-113">Increase the <xref:System.Windows.Forms.ProgressBar> display by a fixed value.</span></span>|<span data-ttu-id="5f3ab-114">Tento přístup je užitečný, pokud zobrazujete jednoduchý počet mezi minimálním a maximálním, například uplynulý čas nebo počet souborů, které byly zpracovány ze známého součtu.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-114">This approach is useful when you are displaying a simple count between the minimum and maximum, such as elapsed time or the number of files that have been processed out of a known total.</span></span>|  
|<span data-ttu-id="5f3ab-115">Zvyšte <xref:System.Windows.Forms.ProgressBar> zobrazení o hodnotu, která se liší.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-115">Increase the <xref:System.Windows.Forms.ProgressBar> display by a value that varies.</span></span>|<span data-ttu-id="5f3ab-116">Tento přístup je užitečný, když potřebujete změnit zobrazenou hodnotu několikrát v různých částkách.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-116">This approach is useful when you need to change the displayed value a number of times in different amounts.</span></span> <span data-ttu-id="5f3ab-117">Příkladem může být zobrazení množství místa na pevném disku spotřebované při zápisu řady souborů na disk.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-117">An example would be showing the amount of hard-disk space being consumed while writing a series of files to the disk.</span></span>|  
  
 <span data-ttu-id="5f3ab-118">Nejpřímějším způsobem nastavení hodnoty zobrazené indikátorem průběhu <xref:System.Windows.Forms.ProgressBar.Value%2A> je nastavení vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-118">The most direct way to set the value displayed by a progress bar is by setting the <xref:System.Windows.Forms.ProgressBar.Value%2A> property.</span></span> <span data-ttu-id="5f3ab-119">To lze provést buď v době návrhu nebo za běhu.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-119">This can be done either at design time or at run time.</span></span>  
  
### <a name="to-set-the-progressbar-value-directly"></a><span data-ttu-id="5f3ab-120">Nastavení hodnoty ProgressBar přímo</span><span class="sxs-lookup"><span data-stu-id="5f3ab-120">To set the ProgressBar value directly</span></span>  
  
1. <span data-ttu-id="5f3ab-121">Nastavte <xref:System.Windows.Forms.ProgressBar> hodnoty <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ovládacího <xref:System.Windows.Forms.ProgressBar.Maximum%2A> prvku a hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-121">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2. <span data-ttu-id="5f3ab-122">V kódu nastavte vlastnost <xref:System.Windows.Forms.ProgressBar.Value%2A> ovládacího prvku na celou hodnotu mezi minimální a maximální hodnoty, které jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-122">In code, set the control's <xref:System.Windows.Forms.ProgressBar.Value%2A> property to an integer value between the minimum and maximum values you have established.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5f3ab-123">Pokud <xref:System.Windows.Forms.ProgressBar.Value%2A> nastavíte vlastnost mimo hranice <xref:System.Windows.Forms.ProgressBar.Minimum%2A> <xref:System.Windows.Forms.ProgressBar.Maximum%2A> stanovené vlastnosti a, <xref:System.ArgumentException> ovládací prvek vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-123">If you set the <xref:System.Windows.Forms.ProgressBar.Value%2A> property outside the boundaries established by the <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> properties, the control throws an <xref:System.ArgumentException> exception.</span></span>  
  
     <span data-ttu-id="5f3ab-124">Následující příklad kódu ukazuje, jak <xref:System.Windows.Forms.ProgressBar> nastavit hodnotu přímo.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-124">The following code example illustrates how to set the <xref:System.Windows.Forms.ProgressBar> value directly.</span></span> <span data-ttu-id="5f3ab-125">Kód čte záznamy ze zdroje dat a aktualizuje indikátor průběhu a popisek při každém čtení datového záznamu.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-125">The code reads records from a data source and updates the progress bar and label every time a data record is read.</span></span> <span data-ttu-id="5f3ab-126">Tento příklad vyžaduje, aby <xref:System.Windows.Forms.Label> formulář <xref:System.Windows.Forms.ProgressBar> měl ovládací prvek, ovládací prvek `CustomerRow` `FirstName` a `LastName` tabulku dat s řádekem volaným s a poli.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-126">This example requires that your form has a <xref:System.Windows.Forms.Label> control, a <xref:System.Windows.Forms.ProgressBar> control, and a data table with a row called `CustomerRow` with `FirstName` and `LastName` fields.</span></span>  
  
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
  
     Pokud zobrazujete průběh, který probíhá v pevném intervalu, můžete nastavit <xref:System.Windows.Forms.ProgressBar> hodnotu a potom volat metodu, která zvyšuje hodnotu ovládacího prvku o tento interval. <span data-ttu-id="5f3ab-128">To je užitečné pro časovače a další scénáře, kde neměříte průběh jako procento celku.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-128">This is useful for timers and other scenarios where you are not measuring progress as a percentage of the whole.</span></span>  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a><span data-ttu-id="5f3ab-129">Zvýšení indikátoru průběhu o pevnou hodnotu</span><span class="sxs-lookup"><span data-stu-id="5f3ab-129">To increase the progress bar by a fixed value</span></span>  
  
1. <span data-ttu-id="5f3ab-130">Nastavte <xref:System.Windows.Forms.ProgressBar> hodnoty <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ovládacího <xref:System.Windows.Forms.ProgressBar.Maximum%2A> prvku a hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-130">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2. <span data-ttu-id="5f3ab-131">Nastavte vlastnost ovládacího <xref:System.Windows.Forms.ProgressBar.Step%2A> prvku na celé číslo představující částku pro zvýšení zobrazené hodnoty indikátoru průběhu.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-131">Set the control's <xref:System.Windows.Forms.ProgressBar.Step%2A> property to an integer representing the amount to increase the progress bar's displayed value.</span></span>  
  
3. <span data-ttu-id="5f3ab-132">Volání <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> metody změnit hodnotu zobrazenou částkou <xref:System.Windows.Forms.ProgressBar.Step%2A> nastavenou ve vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-132">Call the <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> method to change the value displayed by the amount set in the <xref:System.Windows.Forms.ProgressBar.Step%2A> property.</span></span>  
  
     <span data-ttu-id="5f3ab-133">Následující příklad kódu ukazuje, jak může indikátor průběhu udržovat počet souborů v operaci kopírování.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-133">The following code example illustrates how a progress bar can maintain a count of the files in a copy operation.</span></span>  
  
     <span data-ttu-id="5f3ab-134">V následujícím příkladu, jak každý soubor je číst do paměti, indikátor průběhu a popisek jsou aktualizovány tak, aby odrážely celkový počet přečtené soubory.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-134">In the following example, as each file is read into memory, the progress bar and label are updated to reflect the total files read.</span></span> <span data-ttu-id="5f3ab-135">Tento příklad vyžaduje, aby <xref:System.Windows.Forms.Label> formulář <xref:System.Windows.Forms.ProgressBar> měl ovládací prvek a ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-135">This example requires that your form has a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.ProgressBar> control.</span></span>  
  
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
  
     Nakonec můžete zvýšit hodnotu zobrazenou indikátorem průběhu tak, aby každé zvýšení bylo jedinečnou částkou. <span data-ttu-id="5f3ab-137">To je užitečné, když sledujete řadu jedinečných operací, jako je například zápis souborů různých velikostí na pevný disk nebo měření průběhu jako procento celku.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-137">This is useful when you are keeping track of a series of unique operations, such as writing files of different sizes to a hard disk, or measuring progress as a percentage of the whole.</span></span>  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a><span data-ttu-id="5f3ab-138">Zvýšení indikátoru průběhu o dynamickou hodnotu</span><span class="sxs-lookup"><span data-stu-id="5f3ab-138">To increase the progress bar by a dynamic value</span></span>  
  
1. <span data-ttu-id="5f3ab-139">Nastavte <xref:System.Windows.Forms.ProgressBar> hodnoty <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ovládacího <xref:System.Windows.Forms.ProgressBar.Maximum%2A> prvku a hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-139">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2. <span data-ttu-id="5f3ab-140">Voláním <xref:System.Windows.Forms.ProgressBar.Increment%2A> metody změňte hodnotu zobrazenou zadaným celé číslo.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-140">Call the <xref:System.Windows.Forms.ProgressBar.Increment%2A> method to change the value displayed by an integer you specify.</span></span>  
  
     <span data-ttu-id="5f3ab-141">Následující příklad kódu ukazuje, jak indikátor průběhu můžete vypočítat, kolik místa na disku bylo využito během operace kopírování.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-141">The following code example illustrates how a progress bar can calculate how much disk space has been used during a copy operation.</span></span>  
  
     <span data-ttu-id="5f3ab-142">V následujícím příkladu, jako každý soubor je zapsán na pevný disk, indikátor průběhu a popisek jsou aktualizovány tak, aby odrážely množství místa na pevném disku k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-142">In the following example, as each file is written to the hard disk, the progress bar and label are updated to reflect the amount of hard-disk space available.</span></span> <span data-ttu-id="5f3ab-143">Tento příklad vyžaduje, aby <xref:System.Windows.Forms.Label> formulář <xref:System.Windows.Forms.ProgressBar> měl ovládací prvek a ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="5f3ab-143">This example requires that your form has a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.ProgressBar> control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5f3ab-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="5f3ab-144">See also</span></span>

- <xref:System.Windows.Forms.ProgressBar>
- <xref:System.Windows.Forms.ToolStripProgressBar>
- [<span data-ttu-id="5f3ab-145">ProgressBar – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="5f3ab-145">ProgressBar Control Overview</span></span>](progressbar-control-overview-windows-forms.md)
- [<span data-ttu-id="5f3ab-146">Ovládací prvek ProgressBar</span><span class="sxs-lookup"><span data-stu-id="5f3ab-146">ProgressBar Control</span></span>](progressbar-control-windows-forms.md)
