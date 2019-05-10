---
title: 'Návod: Spuštění operace na pozadí'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 1b9a4e0a-f134-48ff-a1be-c461446a31ba
ms.openlocfilehash: 6c705c6d6ff9bbd233bbddc3a73acf8aca13a547
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211514"
---
# <a name="walkthrough-running-an-operation-in-the-background"></a><span data-ttu-id="71863-102">Návod: Spuštění operace na pozadí</span><span class="sxs-lookup"><span data-stu-id="71863-102">Walkthrough: Running an Operation in the Background</span></span>

<span data-ttu-id="71863-103">Pokud máte operace, která bude trvat dlouhou dobu pro dokončení, a nechcete způsobit prodlevy v uživatelském rozhraní, můžete použít <xref:System.ComponentModel.BackgroundWorker> má třída spustit operaci v jiném vlákně.</span><span class="sxs-lookup"><span data-stu-id="71863-103">If you have an operation that will take a long time to complete, and you do not want to cause delays in your user interface, you can use the <xref:System.ComponentModel.BackgroundWorker> class to run the operation on another thread.</span></span>

<span data-ttu-id="71863-104">Úplný seznam všech kód použitý v tomto příkladu najdete v části [jak: Spuštění operace na pozadí](how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="71863-104">For a complete listing of the code used in this example, see [How to: Run an Operation in the Background](how-to-run-an-operation-in-the-background.md).</span></span>

## <a name="run-an-operation-in-the-background"></a><span data-ttu-id="71863-105">Spuštění operace na pozadí</span><span class="sxs-lookup"><span data-stu-id="71863-105">Run an operation in the background</span></span>

1. <span data-ttu-id="71863-106">Je aktivní v Návrháři formulářů Windows v sadě Visual Studio váš formulář, přetáhněte dva <xref:System.Windows.Forms.Button> ovládacích prvků z **nástrojů** formulář a pak nastavte `Name` a <xref:System.Windows.Forms.Control.Text%2A> vlastnosti tlačítka podle Následující tabulka.</span><span class="sxs-lookup"><span data-stu-id="71863-106">With your form active in the Windows Forms Designer in Visual Studio, drag two <xref:System.Windows.Forms.Button> controls from the **Toolbox** to the form, and then set the `Name` and <xref:System.Windows.Forms.Control.Text%2A> properties of the buttons according to the following table.</span></span>

    |<span data-ttu-id="71863-107">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="71863-107">Button</span></span>|<span data-ttu-id="71863-108">Name</span><span class="sxs-lookup"><span data-stu-id="71863-108">Name</span></span>|<span data-ttu-id="71863-109">Text</span><span class="sxs-lookup"><span data-stu-id="71863-109">Text</span></span>|
    |------------|----------|----------|
    |`button1`|`startBtn`|<span data-ttu-id="71863-110">**Start**</span><span class="sxs-lookup"><span data-stu-id="71863-110">**Start**</span></span>|
    |`button2`|`cancelBtn`|<span data-ttu-id="71863-111">**Zrušení**</span><span class="sxs-lookup"><span data-stu-id="71863-111">**Cancel**</span></span>|

2. <span data-ttu-id="71863-112">Otevřít **nástrojů**, klikněte na tlačítko **součásti** kartu a potom přetáhněte <xref:System.ComponentModel.BackgroundWorker> komponentu do formuláře.</span><span class="sxs-lookup"><span data-stu-id="71863-112">Open the **Toolbox**, click the **Components** tab, and then drag the <xref:System.ComponentModel.BackgroundWorker> component onto your form.</span></span>

     <span data-ttu-id="71863-113">`backgroundWorker1` Součást se zobrazí v **komponent**.</span><span class="sxs-lookup"><span data-stu-id="71863-113">The `backgroundWorker1` component appears in the **Component Tray**.</span></span>

3. <span data-ttu-id="71863-114">V **vlastnosti** okno, nastaveno <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="71863-114">In the **Properties** window, set the <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> property to `true`.</span></span>

4. <span data-ttu-id="71863-115">V **vlastnosti** okna, klikněte na **události** tlačítko a pak dvakrát klikněte <xref:System.ComponentModel.BackgroundWorker.DoWork> a <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> událostí pro vytváření obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="71863-115">In the **Properties** window, click on the **Events** button, and then double-click the <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> events to create event handlers.</span></span>

5. <span data-ttu-id="71863-116">Vložit do časově náročný kód <xref:System.ComponentModel.BackgroundWorker.DoWork> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="71863-116">Insert your time-consuming code into the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>

6. <span data-ttu-id="71863-117">Extrahujte všechny parametry vyžadované operace <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> vlastnost <xref:System.ComponentModel.DoWorkEventArgs> parametru.</span><span class="sxs-lookup"><span data-stu-id="71863-117">Extract any parameters required by the operation from the <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> property of the <xref:System.ComponentModel.DoWorkEventArgs> parameter.</span></span>

7. <span data-ttu-id="71863-118">Přiřadit výsledek výpočtu k <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> vlastnost <xref:System.ComponentModel.DoWorkEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="71863-118">Assign the result of the computation to the <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> property of the <xref:System.ComponentModel.DoWorkEventArgs>.</span></span>

     <span data-ttu-id="71863-119">To bude mít k dispozici <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="71863-119">This is will be available to the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler.</span></span>

     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#2)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#2)]

8. <span data-ttu-id="71863-120">Vložte kód pro načtení výsledku operace v <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="71863-120">Insert code for retrieving the result of your operation in the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler.</span></span>

     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#3)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#3)]

9. <span data-ttu-id="71863-121">Implementace `TimeConsumingOperation` metody.</span><span class="sxs-lookup"><span data-stu-id="71863-121">Implement the `TimeConsumingOperation` method.</span></span>

     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#4)]

10. <span data-ttu-id="71863-122">V Návrháři formulářů Windows, klikněte dvakrát na `startButton` vytvořit <xref:System.Windows.Forms.Control.Click> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="71863-122">In the Windows Forms Designer, double-click `startButton` to create the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>

11. <span data-ttu-id="71863-123">Volání <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metodu <xref:System.Windows.Forms.Control.Click> obslužné rutiny události pro `startButton`.</span><span class="sxs-lookup"><span data-stu-id="71863-123">Call the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method in the <xref:System.Windows.Forms.Control.Click> event handler for `startButton`.</span></span>

     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#5)]

12. <span data-ttu-id="71863-124">V Návrháři formulářů Windows, klikněte dvakrát na `cancelButton` vytvořit <xref:System.Windows.Forms.Control.Click> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="71863-124">In the Windows Forms Designer, double-click `cancelButton` to create the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>

13. <span data-ttu-id="71863-125">Volání <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> metodu <xref:System.Windows.Forms.Control.Click> obslužné rutiny události pro `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="71863-125">Call the <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> method in the <xref:System.Windows.Forms.Control.Click> event handler for `cancelButton`.</span></span>

     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#6)]

14. <span data-ttu-id="71863-126">V horní části souboru importujte obory názvů System.ComponentModel a System.Threading.</span><span class="sxs-lookup"><span data-stu-id="71863-126">At the top of the file, import the System.ComponentModel and System.Threading namespaces.</span></span>

     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#7)]

15. <span data-ttu-id="71863-127">Stisknutím klávesy **F6** sestavte řešení a potom stiskněte klávesu **Ctrl**+**F5** ke spuštění aplikace mimo ladicí program.</span><span class="sxs-lookup"><span data-stu-id="71863-127">Press **F6** to build the solution, and then press **Ctrl**+**F5** to run the application outside the debugger.</span></span>

    > [!NOTE]
    > <span data-ttu-id="71863-128">Pokud stisknete **F5** spusťte aplikaci v ladicím programu, výjimka vyvolána v `TimeConsumingOperation` metoda je zachycena a zobrazené ladicím programem.</span><span class="sxs-lookup"><span data-stu-id="71863-128">If you press **F5** to run the application under the debugger, the exception raised in the `TimeConsumingOperation` method is caught and displayed by the debugger.</span></span> <span data-ttu-id="71863-129">Při spuštění aplikace mimo ladicí program, <xref:System.ComponentModel.BackgroundWorker> zpracovává výjimku a ukládá ho do mezipaměti <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> vlastnost <xref:System.ComponentModel.RunWorkerCompletedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="71863-129">When you run the application outside the debugger, the <xref:System.ComponentModel.BackgroundWorker> handles the exception and caches it in the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> property of the <xref:System.ComponentModel.RunWorkerCompletedEventArgs>.</span></span>

16. <span data-ttu-id="71863-130">Klikněte na tlačítko **Start** tlačítko Spustit asynchronní operace a pak klikněte na tlačítko **zrušit** tlačítko Zastavit spuštěné asynchronní operaci.</span><span class="sxs-lookup"><span data-stu-id="71863-130">Click the **Start** button to run an asynchronous operation, and then click the **Cancel** button to stop a running asynchronous operation.</span></span>

     <span data-ttu-id="71863-131">Se zobrazí výsledek každé operace <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="71863-131">The outcome of each operation is displayed in a <xref:System.Windows.Forms.MessageBox>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="71863-132">Další kroky</span><span class="sxs-lookup"><span data-stu-id="71863-132">Next steps</span></span>

- <span data-ttu-id="71863-133">Implementace formuláře, která hlásí průběh, protože probíhá asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="71863-133">Implement a form that reports progress as an asynchronous operation proceeds.</span></span> <span data-ttu-id="71863-134">Další informace najdete v tématu [jak: Implementace formuláře, který používá operaci na pozadí](how-to-implement-a-form-that-uses-a-background-operation.md).</span><span class="sxs-lookup"><span data-stu-id="71863-134">For more information, see [How to: Implement a Form That Uses a Background Operation](how-to-implement-a-form-that-uses-a-background-operation.md).</span></span>

- <span data-ttu-id="71863-135">Implementace třídy, která podporuje asynchronní vzor pro komponenty.</span><span class="sxs-lookup"><span data-stu-id="71863-135">Implement a class that supports the Asynchronous Pattern for Components.</span></span> <span data-ttu-id="71863-136">Další informace najdete v tématu [implementace asynchronního vzoru založeného na událostech](../../../standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="71863-136">For more information, see [Implementing the Event-based Asynchronous Pattern](../../../standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="71863-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="71863-137">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [<span data-ttu-id="71863-138">Postupy: Implementace formuláře, který používá operaci na pozadí</span><span class="sxs-lookup"><span data-stu-id="71863-138">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="71863-139">Postupy: Spuštění operace na pozadí</span><span class="sxs-lookup"><span data-stu-id="71863-139">How to: Run an Operation in the Background</span></span>](how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="71863-140">Komponenta BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="71863-140">BackgroundWorker Component</span></span>](backgroundworker-component.md)
