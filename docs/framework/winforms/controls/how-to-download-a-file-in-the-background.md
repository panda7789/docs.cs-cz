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
ms.openlocfilehash: 616aa5495ec5ec5d3db6f816a96c34b3ac9f3fed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536566"
---
# <a name="how-to-download-a-file-in-the-background"></a><span data-ttu-id="7b28f-102">Postupy: Stahování souboru na pozadí</span><span class="sxs-lookup"><span data-stu-id="7b28f-102">How to: Download a File in the Background</span></span>
<span data-ttu-id="7b28f-103">Stažení souboru je běžné úlohy a je často užitečné ke spuštění této operace může trvat delší dobu na samostatné vlákno.</span><span class="sxs-lookup"><span data-stu-id="7b28f-103">Downloading a file is a common task, and it is often useful to run this potentially time-consuming operation on a separate thread.</span></span> <span data-ttu-id="7b28f-104">Použití <xref:System.ComponentModel.BackgroundWorker> součást k provedení této úlohy s kódem velmi malé.</span><span class="sxs-lookup"><span data-stu-id="7b28f-104">Use the <xref:System.ComponentModel.BackgroundWorker> component to accomplish this task with very little code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b28f-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="7b28f-105">Example</span></span>  
 <span data-ttu-id="7b28f-106">Následující příklad kódu ukazuje, jak používat <xref:System.ComponentModel.BackgroundWorker> součást se načíst soubor XML z adresy URL.</span><span class="sxs-lookup"><span data-stu-id="7b28f-106">The following code example demonstrates how to use a <xref:System.ComponentModel.BackgroundWorker> component to load an XML file from a URL.</span></span> <span data-ttu-id="7b28f-107">Když uživatel klikne **Stáhnout** tlačítko <xref:System.Windows.Forms.Control.Click> volání obslužné rutiny událostí <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metodu <xref:System.ComponentModel.BackgroundWorker> součásti spustit operaci stahování.</span><span class="sxs-lookup"><span data-stu-id="7b28f-107">When the user clicks the **Download** button, the <xref:System.Windows.Forms.Control.Click> event handler calls the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method of a <xref:System.ComponentModel.BackgroundWorker> component to start the download operation.</span></span> <span data-ttu-id="7b28f-108">Tlačítko je zakázána dobu stahování a povolena po dokončení stahování.</span><span class="sxs-lookup"><span data-stu-id="7b28f-108">The button is disabled for the duration of the download, and then enabled when the download is complete.</span></span> <span data-ttu-id="7b28f-109">A <xref:System.Windows.Forms.MessageBox> zobrazí obsah souboru.</span><span class="sxs-lookup"><span data-stu-id="7b28f-109">A <xref:System.Windows.Forms.MessageBox> displays the contents of the file.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#1)]  
  
 <span data-ttu-id="7b28f-110">**Stahování souboru**</span><span class="sxs-lookup"><span data-stu-id="7b28f-110">**Downloading the file**</span></span>  
  
 <span data-ttu-id="7b28f-111">Soubor se stáhne na <xref:System.ComponentModel.BackgroundWorker> součásti pracovní vlákno, který se spouští <xref:System.ComponentModel.BackgroundWorker.DoWork> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="7b28f-111">The file is downloaded on the <xref:System.ComponentModel.BackgroundWorker> component's worker thread, which runs the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span> <span data-ttu-id="7b28f-112">Tento přístup z více vláken spustí, když váš kód zavolá <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="7b28f-112">This thread starts when your code calls the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#3)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#3)]  
  
 <span data-ttu-id="7b28f-113">**BackgroundWorker – ukončíte čekání**</span><span class="sxs-lookup"><span data-stu-id="7b28f-113">**Waiting for a BackgroundWorker to finish**</span></span>  
  
 <span data-ttu-id="7b28f-114">`downloadButton_Click` Obslužné rutiny události ukazuje, jak čekat <xref:System.ComponentModel.BackgroundWorker> součást dokončení asynchronní úkolu.</span><span class="sxs-lookup"><span data-stu-id="7b28f-114">The `downloadButton_Click` event handler demonstrates how to wait for a <xref:System.ComponentModel.BackgroundWorker> component to finish its asynchronous task.</span></span>  
  
 <span data-ttu-id="7b28f-115">Pokud má aplikace reakce na události jenom a nechcete provádět v hlavní vlákno žádné operace, a počkat na dokončení vlákně na pozadí, ukončete právě obslužná rutina.</span><span class="sxs-lookup"><span data-stu-id="7b28f-115">If you only want the application to respond to events and do not want to do any work in the main thread while you wait for the background thread to complete, just exit the handler.</span></span>  
  
 <span data-ttu-id="7b28f-116">Pokud chcete pokračovat, pracuje v hlavní vlákno, použijte <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> vlastnosti k určení zda <xref:System.ComponentModel.BackgroundWorker> vlákno je stále spuštěná.</span><span class="sxs-lookup"><span data-stu-id="7b28f-116">If you want to continue doing work in the main thread, use the <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> property to determine whether the <xref:System.ComponentModel.BackgroundWorker> thread is still running.</span></span> <span data-ttu-id="7b28f-117">V příkladu se aktualizuje indikátor průběhu během zpracování stahování.</span><span class="sxs-lookup"><span data-stu-id="7b28f-117">In the example, a progress bar is updated while the download is processing.</span></span> <span data-ttu-id="7b28f-118">Volejte <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> metoda zachovat reagující uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7b28f-118">Be sure to call the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method to keep the UI responsive.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#2)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#2)]  
  
 <span data-ttu-id="7b28f-119">**Zobrazení výsledek**</span><span class="sxs-lookup"><span data-stu-id="7b28f-119">**Displaying the result**</span></span>  
  
 <span data-ttu-id="7b28f-120">`backgroundWorker1_RunWorkerCompleted` Metoda zpracovává <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> událostí a je volána po dokončení operace na pozadí.</span><span class="sxs-lookup"><span data-stu-id="7b28f-120">The `backgroundWorker1_RunWorkerCompleted` method handles the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event and is called when the background operation is completed.</span></span> <span data-ttu-id="7b28f-121">Tato metoda nejprve zkontroluje <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7b28f-121">This method first checks the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="7b28f-122">Pokud <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> je `null`, pak tato metoda zobrazí obsah souboru.</span><span class="sxs-lookup"><span data-stu-id="7b28f-122">If <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> is `null`, then this method displays the contents of the file.</span></span> <span data-ttu-id="7b28f-123">Umožňuje klikněte na tlačítko Stáhnout, který byl zakázán, když zahájil stahování, a obnoví indikátor průběhu.</span><span class="sxs-lookup"><span data-stu-id="7b28f-123">It then enables the download button, which was disabled when the download began, and it resets the progress bar.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#4)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7b28f-124">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7b28f-124">Compiling the Code</span></span>  
 <span data-ttu-id="7b28f-125">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="7b28f-125">This example requires:</span></span>  
  
-   <span data-ttu-id="7b28f-126">Odkazy na sestavení System.Drawing System.Windows.Forms a System.Xml.</span><span class="sxs-lookup"><span data-stu-id="7b28f-126">References to the System.Drawing, System.Windows.Forms, and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="7b28f-127">Informace o vytváření tento příklad z příkazového řádku pro visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="7b28f-127">For information about building this example from the command line for visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="7b28f-128">Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="7b28f-128">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="7b28f-129">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="7b28f-129">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="7b28f-130">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="7b28f-130">Robust Programming</span></span>  
 <span data-ttu-id="7b28f-131">Vždy zkontrolujte <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> vlastnost v vaší <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obslužné rutiny události před pokusem o přístup <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> vlastnost nebo jakýkoliv jiný objekt, který může mít byl ovlivněn <xref:System.ComponentModel.BackgroundWorker.DoWork> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="7b28f-131">Always check the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> property in your <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler before attempting to access the <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> property or any other object that may have been affected by the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b28f-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b28f-132">See Also</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 [<span data-ttu-id="7b28f-133">Postupy: Spuštění operace na pozadí</span><span class="sxs-lookup"><span data-stu-id="7b28f-133">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [<span data-ttu-id="7b28f-134">Postupy: Implementace formuláře, který používá operaci na pozadí</span><span class="sxs-lookup"><span data-stu-id="7b28f-134">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
