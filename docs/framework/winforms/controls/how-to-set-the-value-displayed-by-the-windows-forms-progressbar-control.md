---
title: Nastavení hodnoty zobrazované ovládacím prvkem ProgressBar
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ProgressBar control [Windows Forms], setting value displayed
- progress controls [Windows Forms], setting value displayed
ms.assetid: 0e5010ad-1e9a-4271-895e-5a3d24d37a26
ms.openlocfilehash: 79ce1e576652d00b323d31dfc6551e168ea0a9a0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743801"
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a><span data-ttu-id="97905-102">Postupy: Nastavení hodnoty zobrazované ovládacím prvkem Windows Forms ProgressBar</span><span class="sxs-lookup"><span data-stu-id="97905-102">How to: Set the Value Displayed by the Windows Forms ProgressBar Control</span></span>
> [!IMPORTANT]
> <span data-ttu-id="97905-103">Ovládací prvek <xref:System.Windows.Forms.ToolStripProgressBar> nahrazuje a přidává funkce do ovládacího prvku <xref:System.Windows.Forms.ProgressBar>; Nicméně ovládací prvek <xref:System.Windows.Forms.ProgressBar> se zachovává pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.</span><span class="sxs-lookup"><span data-stu-id="97905-103">The <xref:System.Windows.Forms.ToolStripProgressBar> control replaces and adds functionality to the <xref:System.Windows.Forms.ProgressBar> control; however, the <xref:System.Windows.Forms.ProgressBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="97905-104">.NET Framework poskytuje několik různých způsobů zobrazení dané hodnoty v rámci <xref:System.Windows.Forms.ProgressBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="97905-104">The .NET Framework gives you several different ways to display a given value within the <xref:System.Windows.Forms.ProgressBar> control.</span></span> <span data-ttu-id="97905-105">Jaký přístup zvolíte, bude záviset na úloze nebo na problému, který řešíte.</span><span class="sxs-lookup"><span data-stu-id="97905-105">Which approach you choose will depend on the task at hand or the problem you are solving.</span></span> <span data-ttu-id="97905-106">Následující tabulka uvádí přístupy, které můžete zvolit.</span><span class="sxs-lookup"><span data-stu-id="97905-106">The following table shows the approaches you can choose.</span></span>  
  
|<span data-ttu-id="97905-107">Přístup</span><span class="sxs-lookup"><span data-stu-id="97905-107">Approach</span></span>|<span data-ttu-id="97905-108">Popis</span><span class="sxs-lookup"><span data-stu-id="97905-108">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="97905-109">Nastavte hodnotu ovládacího prvku <xref:System.Windows.Forms.ProgressBar> přímo.</span><span class="sxs-lookup"><span data-stu-id="97905-109">Set the value of the <xref:System.Windows.Forms.ProgressBar> control directly.</span></span>|<span data-ttu-id="97905-110">Tento přístup je užitečný pro úlohy, u kterých víte, že celkový počet měřených položek, které budou zahrnuty, jako je například čtení záznamů ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="97905-110">This approach is useful for tasks where you know the total of the item measured that will be involved, such as reading records from a data source.</span></span> <span data-ttu-id="97905-111">Kromě toho, pokud potřebujete pouze nastavit hodnotu pouze jednou nebo dvakrát, je to jednoduchý způsob, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="97905-111">Additionally, if you only need to set the value once or twice, this is an easy way to do it.</span></span> <span data-ttu-id="97905-112">Nakonec tento postup použijte v případě, že potřebujete snížit hodnotu zobrazenou indikátorem průběhu.</span><span class="sxs-lookup"><span data-stu-id="97905-112">Finally, use this process if you need to decrease the value displayed by the progress bar.</span></span>|  
|<span data-ttu-id="97905-113">Zvětšete <xref:System.Windows.Forms.ProgressBar> zobrazení o pevnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="97905-113">Increase the <xref:System.Windows.Forms.ProgressBar> display by a fixed value.</span></span>|<span data-ttu-id="97905-114">Tento přístup je užitečný, když zobrazujete jednoduchý počet mezi minimální a maximální, například uplynulý čas nebo počet souborů, které byly zpracovány ze známého celku.</span><span class="sxs-lookup"><span data-stu-id="97905-114">This approach is useful when you are displaying a simple count between the minimum and maximum, such as elapsed time or the number of files that have been processed out of a known total.</span></span>|  
|<span data-ttu-id="97905-115">Zvětšete <xref:System.Windows.Forms.ProgressBar> zobrazení podle hodnoty, která se liší.</span><span class="sxs-lookup"><span data-stu-id="97905-115">Increase the <xref:System.Windows.Forms.ProgressBar> display by a value that varies.</span></span>|<span data-ttu-id="97905-116">Tento přístup je užitečný v případě, že potřebujete změnit zobrazenou hodnotu v různých částkách.</span><span class="sxs-lookup"><span data-stu-id="97905-116">This approach is useful when you need to change the displayed value a number of times in different amounts.</span></span> <span data-ttu-id="97905-117">V příkladu se zobrazilo množství místa na pevném disku, které se spotřebovává při zápisu řady souborů na disk.</span><span class="sxs-lookup"><span data-stu-id="97905-117">An example would be showing the amount of hard-disk space being consumed while writing a series of files to the disk.</span></span>|  
  
 <span data-ttu-id="97905-118">Nejpřímější způsob, jak nastavit hodnotu zobrazenou indikátorem průběhu, je nastavením vlastnosti <xref:System.Windows.Forms.ProgressBar.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="97905-118">The most direct way to set the value displayed by a progress bar is by setting the <xref:System.Windows.Forms.ProgressBar.Value%2A> property.</span></span> <span data-ttu-id="97905-119">To lze provést buď v době návrhu, nebo v době běhu.</span><span class="sxs-lookup"><span data-stu-id="97905-119">This can be done either at design time or at run time.</span></span>  
  
### <a name="to-set-the-progressbar-value-directly"></a><span data-ttu-id="97905-120">Nastavení hodnoty ProgressBar přímo</span><span class="sxs-lookup"><span data-stu-id="97905-120">To set the ProgressBar value directly</span></span>  
  
1. <span data-ttu-id="97905-121">Nastavte <xref:System.Windows.Forms.ProgressBar.Minimum%2A> a hodnoty <xref:System.Windows.Forms.ProgressBar.Maximum%2A> ovládacího prvku <xref:System.Windows.Forms.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="97905-121">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2. <span data-ttu-id="97905-122">V kódu nastavte vlastnost <xref:System.Windows.Forms.ProgressBar.Value%2A> ovládacího prvku na celočíselnou hodnotu mezi minimální a maximální hodnotou, kterou jste nastavili.</span><span class="sxs-lookup"><span data-stu-id="97905-122">In code, set the control's <xref:System.Windows.Forms.ProgressBar.Value%2A> property to an integer value between the minimum and maximum values you have established.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="97905-123">Nastavíte-li vlastnost <xref:System.Windows.Forms.ProgressBar.Value%2A> mimo hranice stanovené vlastností <xref:System.Windows.Forms.ProgressBar.Minimum%2A> a <xref:System.Windows.Forms.ProgressBar.Maximum%2A>, vyvolá ovládací prvek výjimku <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="97905-123">If you set the <xref:System.Windows.Forms.ProgressBar.Value%2A> property outside the boundaries established by the <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> properties, the control throws an <xref:System.ArgumentException> exception.</span></span>  
  
     <span data-ttu-id="97905-124">Následující příklad kódu ukazuje, jak nastavit hodnotu <xref:System.Windows.Forms.ProgressBar> přímo.</span><span class="sxs-lookup"><span data-stu-id="97905-124">The following code example illustrates how to set the <xref:System.Windows.Forms.ProgressBar> value directly.</span></span> <span data-ttu-id="97905-125">Kód přečte záznamy ze zdroje dat a při každém čtení záznamu dat aktualizuje indikátor průběhu a popisek.</span><span class="sxs-lookup"><span data-stu-id="97905-125">The code reads records from a data source and updates the progress bar and label every time a data record is read.</span></span> <span data-ttu-id="97905-126">Tento příklad vyžaduje, aby formulář měl ovládací prvek <xref:System.Windows.Forms.Label>, ovládací prvek <xref:System.Windows.Forms.ProgressBar> a tabulku dat s řádkem s názvem `CustomerRow` s poli `FirstName` a `LastName`.</span><span class="sxs-lookup"><span data-stu-id="97905-126">This example requires that your form has a <xref:System.Windows.Forms.Label> control, a <xref:System.Windows.Forms.ProgressBar> control, and a data table with a row called `CustomerRow` with `FirstName` and `LastName` fields.</span></span>  
  
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
  
     Pokud zobrazujete průběh, který pokračuje pevným intervalem, můžete nastavit hodnotu a pak zavolat metodu, která zvýší hodnotu <xref:System.Windows.Forms.ProgressBar> ovládacího prvku o tento interval. <span data-ttu-id="97905-128">To je užitečné pro časovače a další scénáře, kdy neměříte průběh jako procento celého celku.</span><span class="sxs-lookup"><span data-stu-id="97905-128">This is useful for timers and other scenarios where you are not measuring progress as a percentage of the whole.</span></span>  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a><span data-ttu-id="97905-129">Postup zvýšení hodnoty indikátoru průběhu na pevnou hodnotu</span><span class="sxs-lookup"><span data-stu-id="97905-129">To increase the progress bar by a fixed value</span></span>  
  
1. <span data-ttu-id="97905-130">Nastavte <xref:System.Windows.Forms.ProgressBar.Minimum%2A> a hodnoty <xref:System.Windows.Forms.ProgressBar.Maximum%2A> ovládacího prvku <xref:System.Windows.Forms.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="97905-130">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2. <span data-ttu-id="97905-131">Nastavte vlastnost <xref:System.Windows.Forms.ProgressBar.Step%2A> ovládacího prvku na celé číslo představující množství pro zvýšení zobrazené hodnoty indikátoru průběhu.</span><span class="sxs-lookup"><span data-stu-id="97905-131">Set the control's <xref:System.Windows.Forms.ProgressBar.Step%2A> property to an integer representing the amount to increase the progress bar's displayed value.</span></span>  
  
3. <span data-ttu-id="97905-132">Zavolejte metodu <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> pro změnu hodnoty zobrazené v rámci nastaveného množství ve vlastnosti <xref:System.Windows.Forms.ProgressBar.Step%2A>.</span><span class="sxs-lookup"><span data-stu-id="97905-132">Call the <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> method to change the value displayed by the amount set in the <xref:System.Windows.Forms.ProgressBar.Step%2A> property.</span></span>  
  
     <span data-ttu-id="97905-133">Následující příklad kódu ukazuje, jak může indikátor průběhu udržovat počet souborů v operaci kopírování.</span><span class="sxs-lookup"><span data-stu-id="97905-133">The following code example illustrates how a progress bar can maintain a count of the files in a copy operation.</span></span>  
  
     <span data-ttu-id="97905-134">V následujícím příkladu jsou jednotlivé soubory čteny do paměti, indikátor průběhu a popisek jsou aktualizovány tak, aby odrážely celkový počet čtených souborů.</span><span class="sxs-lookup"><span data-stu-id="97905-134">In the following example, as each file is read into memory, the progress bar and label are updated to reflect the total files read.</span></span> <span data-ttu-id="97905-135">Tento příklad vyžaduje, aby formulář měl ovládací prvek <xref:System.Windows.Forms.Label> a ovládací prvek <xref:System.Windows.Forms.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="97905-135">This example requires that your form has a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.ProgressBar> control.</span></span>  
  
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
  
     Nakonec můžete zvýšit hodnotu zobrazenou indikátorem průběhu, aby každé zvýšení bylo jedinečné. <span data-ttu-id="97905-137">To je užitečné v případě, že sledujete řadu jedinečných operací, například zápis souborů různých velikostí na pevný disk nebo měření postupu v procentech celého celku.</span><span class="sxs-lookup"><span data-stu-id="97905-137">This is useful when you are keeping track of a series of unique operations, such as writing files of different sizes to a hard disk, or measuring progress as a percentage of the whole.</span></span>  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a><span data-ttu-id="97905-138">Postup při zvýšení hodnoty indikátoru průběhu dynamickou hodnotou</span><span class="sxs-lookup"><span data-stu-id="97905-138">To increase the progress bar by a dynamic value</span></span>  
  
1. <span data-ttu-id="97905-139">Nastavte <xref:System.Windows.Forms.ProgressBar.Minimum%2A> a hodnoty <xref:System.Windows.Forms.ProgressBar.Maximum%2A> ovládacího prvku <xref:System.Windows.Forms.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="97905-139">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2. <span data-ttu-id="97905-140">Zavolejte metodu <xref:System.Windows.Forms.ProgressBar.Increment%2A> pro změnu hodnoty zobrazené podle celého čísla, které zadáte.</span><span class="sxs-lookup"><span data-stu-id="97905-140">Call the <xref:System.Windows.Forms.ProgressBar.Increment%2A> method to change the value displayed by an integer you specify.</span></span>  
  
     <span data-ttu-id="97905-141">Následující příklad kódu ukazuje, jak může indikátor průběhu vypočítat, kolik místa na disku bylo během operace kopírování použito.</span><span class="sxs-lookup"><span data-stu-id="97905-141">The following code example illustrates how a progress bar can calculate how much disk space has been used during a copy operation.</span></span>  
  
     <span data-ttu-id="97905-142">V následujícím příkladu se při zápisu jednotlivých souborů na pevný disk aktualizuje indikátor průběhu a popisek tak, aby odráželo množství dostupného místa na pevném disku.</span><span class="sxs-lookup"><span data-stu-id="97905-142">In the following example, as each file is written to the hard disk, the progress bar and label are updated to reflect the amount of hard-disk space available.</span></span> <span data-ttu-id="97905-143">Tento příklad vyžaduje, aby formulář měl ovládací prvek <xref:System.Windows.Forms.Label> a ovládací prvek <xref:System.Windows.Forms.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="97905-143">This example requires that your form has a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.ProgressBar> control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="97905-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="97905-144">See also</span></span>

- <xref:System.Windows.Forms.ProgressBar>
- <xref:System.Windows.Forms.ToolStripProgressBar>
- [<span data-ttu-id="97905-145">Přehled ovládacího prvku ProgressBar</span><span class="sxs-lookup"><span data-stu-id="97905-145">ProgressBar Control Overview</span></span>](progressbar-control-overview-windows-forms.md)
- [<span data-ttu-id="97905-146">Ovládací prvek ProgressBar</span><span class="sxs-lookup"><span data-stu-id="97905-146">ProgressBar Control</span></span>](progressbar-control-windows-forms.md)
