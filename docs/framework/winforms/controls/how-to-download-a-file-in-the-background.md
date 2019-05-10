---
title: 'Postupy: Stahování souboru na pozadí'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9b7bc5ae-051c-4904-9720-18f6667388bd
ms.openlocfilehash: 1d62bbac8550a5e632760e196463285e4c9a14ce
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651761"
---
# <a name="how-to-download-a-file-in-the-background"></a><span data-ttu-id="11f94-102">Postupy: Stahování souboru na pozadí</span><span class="sxs-lookup"><span data-stu-id="11f94-102">How to: Download a File in the Background</span></span>
<span data-ttu-id="11f94-103">Stažení souboru je běžný úkol a často je užitečné k provedení této operace může trvat delší dobu na samostatném vlákně.</span><span class="sxs-lookup"><span data-stu-id="11f94-103">Downloading a file is a common task, and it is often useful to run this potentially time-consuming operation on a separate thread.</span></span> <span data-ttu-id="11f94-104">Použití <xref:System.ComponentModel.BackgroundWorker> komponenty, které chcete provést tuto úlohu s velmi malým množstvím kódu.</span><span class="sxs-lookup"><span data-stu-id="11f94-104">Use the <xref:System.ComponentModel.BackgroundWorker> component to accomplish this task with very little code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11f94-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="11f94-105">Example</span></span>  
 <span data-ttu-id="11f94-106">Následující příklad kódu ukazuje, jak používat <xref:System.ComponentModel.BackgroundWorker> komponenty se načíst soubor XML z adresy URL.</span><span class="sxs-lookup"><span data-stu-id="11f94-106">The following code example demonstrates how to use a <xref:System.ComponentModel.BackgroundWorker> component to load an XML file from a URL.</span></span> <span data-ttu-id="11f94-107">Pokud uživatel klikne **Stáhnout** tlačítko, <xref:System.Windows.Forms.Control.Click> volání obsluhy události <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metodu <xref:System.ComponentModel.BackgroundWorker> součásti spustit operaci stahování.</span><span class="sxs-lookup"><span data-stu-id="11f94-107">When the user clicks the **Download** button, the <xref:System.Windows.Forms.Control.Click> event handler calls the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method of a <xref:System.ComponentModel.BackgroundWorker> component to start the download operation.</span></span> <span data-ttu-id="11f94-108">Tlačítka je zakázán dobu stahování a poté povoleny po dokončení stahování.</span><span class="sxs-lookup"><span data-stu-id="11f94-108">The button is disabled for the duration of the download, and then enabled when the download is complete.</span></span> <span data-ttu-id="11f94-109">A <xref:System.Windows.Forms.MessageBox> zobrazí obsah souboru.</span><span class="sxs-lookup"><span data-stu-id="11f94-109">A <xref:System.Windows.Forms.MessageBox> displays the contents of the file.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#1)]  
  
 <span data-ttu-id="11f94-110">**Stahování souboru**</span><span class="sxs-lookup"><span data-stu-id="11f94-110">**Downloading the file**</span></span>  
  
 <span data-ttu-id="11f94-111">Soubor se stáhne na <xref:System.ComponentModel.BackgroundWorker> komponenty pracovní podproces, který se spouští <xref:System.ComponentModel.BackgroundWorker.DoWork> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="11f94-111">The file is downloaded on the <xref:System.ComponentModel.BackgroundWorker> component's worker thread, which runs the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span> <span data-ttu-id="11f94-112">Toto vlákno spustí, když kód volá <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="11f94-112">This thread starts when your code calls the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#3)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#3)]  
  
 <span data-ttu-id="11f94-113">**Čekání na BackgroundWorker – dokončení**</span><span class="sxs-lookup"><span data-stu-id="11f94-113">**Waiting for a BackgroundWorker to finish**</span></span>  
  
 <span data-ttu-id="11f94-114">`downloadButton_Click` Obslužné rutiny události ukazuje postup při čekání <xref:System.ComponentModel.BackgroundWorker> součást, kterou dokončit jeho asynchronní úlohu.</span><span class="sxs-lookup"><span data-stu-id="11f94-114">The `downloadButton_Click` event handler demonstrates how to wait for a <xref:System.ComponentModel.BackgroundWorker> component to finish its asynchronous task.</span></span>  
  
 <span data-ttu-id="11f94-115">Pokud pouze aplikaci reagovat na události a nechcete, aby provedete jakékoli práce v hlavním vlákně, čekají na vlákně na pozadí k dokončení právě ukončení obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="11f94-115">If you only want the application to respond to events and do not want to do any work in the main thread while you wait for the background thread to complete, just exit the handler.</span></span>  
  
 <span data-ttu-id="11f94-116">Pokud chcete pokračovat v provádění práce v hlavním vlákně, použijte <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> a určí, zda <xref:System.ComponentModel.BackgroundWorker> vlákna je stále spuštěn.</span><span class="sxs-lookup"><span data-stu-id="11f94-116">If you want to continue doing work in the main thread, use the <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> property to determine whether the <xref:System.ComponentModel.BackgroundWorker> thread is still running.</span></span> <span data-ttu-id="11f94-117">V tomto příkladu se aktualizuje indikátor průběhu během zpracování stahování.</span><span class="sxs-lookup"><span data-stu-id="11f94-117">In the example, a progress bar is updated while the download is processing.</span></span> <span data-ttu-id="11f94-118">Nezapomeňte volat <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> metoda zachovat interaktivní uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="11f94-118">Be sure to call the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method to keep the UI responsive.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#2)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#2)]  
  
 <span data-ttu-id="11f94-119">**Zobrazení výsledku**</span><span class="sxs-lookup"><span data-stu-id="11f94-119">**Displaying the result**</span></span>  
  
 <span data-ttu-id="11f94-120">`backgroundWorker1_RunWorkerCompleted` Metoda obslužné rutiny <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> událostí a je volána po dokončení operace na pozadí.</span><span class="sxs-lookup"><span data-stu-id="11f94-120">The `backgroundWorker1_RunWorkerCompleted` method handles the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event and is called when the background operation is completed.</span></span> <span data-ttu-id="11f94-121">Tato metoda nejprve zkontroluje, <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="11f94-121">This method first checks the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="11f94-122">Pokud <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> je `null`, pak tato metoda zobrazí obsah souboru.</span><span class="sxs-lookup"><span data-stu-id="11f94-122">If <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> is `null`, then this method displays the contents of the file.</span></span> <span data-ttu-id="11f94-123">Pak povolí tlačítko Stáhnout, který byl zakázán, když začalo stahování, a obnoví indikátor průběhu.</span><span class="sxs-lookup"><span data-stu-id="11f94-123">It then enables the download button, which was disabled when the download began, and it resets the progress bar.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#4)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="11f94-124">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="11f94-124">Compiling the Code</span></span>  
 <span data-ttu-id="11f94-125">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="11f94-125">This example requires:</span></span>  
  
- <span data-ttu-id="11f94-126">Odkazy na sestavení System.Xml, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="11f94-126">References to the System.Drawing, System.Windows.Forms, and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="11f94-127">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="11f94-127">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="11f94-128">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="11f94-128">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="11f94-129">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="11f94-129">Robust Programming</span></span>  
 <span data-ttu-id="11f94-130">Vždy zkontrolujte <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> vlastnost v vaše <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obslužná rutina události, než se pokusíte o přístup k <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> vlastnost nebo jakýkoli jiný objekt, který může mít byl ovlivněn <xref:System.ComponentModel.BackgroundWorker.DoWork> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="11f94-130">Always check the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> property in your <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler before attempting to access the <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> property or any other object that may have been affected by the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11f94-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11f94-131">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- [<span data-ttu-id="11f94-132">Postupy: Spuštění operace na pozadí</span><span class="sxs-lookup"><span data-stu-id="11f94-132">How to: Run an Operation in the Background</span></span>](how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="11f94-133">Postupy: Implementace formuláře, který používá operaci na pozadí</span><span class="sxs-lookup"><span data-stu-id="11f94-133">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)
