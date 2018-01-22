---
title: "Návod: Spuštění operace na pozadí"
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
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 1b9a4e0a-f134-48ff-a1be-c461446a31ba
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ca0892e9d384eefb0fec87a7717222fefb779d12
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-running-an-operation-in-the-background"></a><span data-ttu-id="6e933-102">Návod: Spuštění operace na pozadí</span><span class="sxs-lookup"><span data-stu-id="6e933-102">Walkthrough: Running an Operation in the Background</span></span>
<span data-ttu-id="6e933-103">Pokud máte operace, která bude trvat dlouhou dobu pro dokončení, a nechcete způsobit zpoždění v uživatelském rozhraní, můžete použít <xref:System.ComponentModel.BackgroundWorker> třídy spusťte operaci na jiné vlákno.</span><span class="sxs-lookup"><span data-stu-id="6e933-103">If you have an operation that will take a long time to complete, and you do not want to cause delays in your user interface, you can use the <xref:System.ComponentModel.BackgroundWorker> class to run the operation on another thread.</span></span>  
  
 <span data-ttu-id="6e933-104">Úplný seznam všech kód v tomto příkladu používá, najdete v části [postupy: spuštění operace na pozadí](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="6e933-104">For a complete listing of the code used in this example, see [How to: Run an Operation in the Background](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e933-105">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="6e933-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="6e933-106">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="6e933-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="6e933-107">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="6e933-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-run-an-operation-in-the-background"></a><span data-ttu-id="6e933-108">Spuštění operace na pozadí</span><span class="sxs-lookup"><span data-stu-id="6e933-108">To run an operation in the background</span></span>  
  
1.  <span data-ttu-id="6e933-109">Pomocí svého formuláře v Návrháři formulářů Windows aktivní, přetáhněte dva <xref:System.Windows.Forms.Button> z ovládací prvky **sada nástrojů** formuláře a potom nastavte `Name` a <xref:System.Windows.Forms.Control.Text%2A> vlastnosti tlačítek podle následující tabulky.</span><span class="sxs-lookup"><span data-stu-id="6e933-109">With your form active in the Windows Forms Designer, drag two <xref:System.Windows.Forms.Button> controls from the **Toolbox** to the form, and then set the `Name` and <xref:System.Windows.Forms.Control.Text%2A> properties of the buttons according to the following table.</span></span>  
  
    |<span data-ttu-id="6e933-110">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="6e933-110">Button</span></span>|<span data-ttu-id="6e933-111">Název</span><span class="sxs-lookup"><span data-stu-id="6e933-111">Name</span></span>|<span data-ttu-id="6e933-112">Text</span><span class="sxs-lookup"><span data-stu-id="6e933-112">Text</span></span>|  
    |------------|----------|----------|  
    |`button1`|`startBtn`|<span data-ttu-id="6e933-113">**Start**</span><span class="sxs-lookup"><span data-stu-id="6e933-113">**Start**</span></span>|  
    |`button2`|`cancelBtn`|<span data-ttu-id="6e933-114">**Zrušit**</span><span class="sxs-lookup"><span data-stu-id="6e933-114">**Cancel**</span></span>|  
  
2.  <span data-ttu-id="6e933-115">Otevřete **sada nástrojů**, klikněte na tlačítko **součásti** kartě a poté přetáhněte <xref:System.ComponentModel.BackgroundWorker> součásti do formuláře.</span><span class="sxs-lookup"><span data-stu-id="6e933-115">Open the **Toolbox**, click the **Components** tab, and then drag the <xref:System.ComponentModel.BackgroundWorker> component onto your form.</span></span>  
  
     <span data-ttu-id="6e933-116">`backgroundWorker1` Součást se zobrazí v **komponent**.</span><span class="sxs-lookup"><span data-stu-id="6e933-116">The `backgroundWorker1` component appears in the **Component Tray**.</span></span>  
  
3.  <span data-ttu-id="6e933-117">V **vlastnosti** nastavte <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="6e933-117">In the **Properties** window, set the <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> property to `true`.</span></span>  
  
4.  <span data-ttu-id="6e933-118">V **vlastnosti** klikněte na **události** tlačítko a potom dvakrát klikněte na <xref:System.ComponentModel.BackgroundWorker.DoWork> a <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> události pro vytváření obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="6e933-118">In the **Properties** window, click on the **Events** button, and then double-click the <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> events to create event handlers.</span></span>  
  
5.  <span data-ttu-id="6e933-119">Vložit časově náročné kódu do <xref:System.ComponentModel.BackgroundWorker.DoWork> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="6e933-119">Insert your time-consuming code into the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
6.  <span data-ttu-id="6e933-120">Extrahování parametry požadované operace z <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> vlastnost <xref:System.ComponentModel.DoWorkEventArgs> parametr.</span><span class="sxs-lookup"><span data-stu-id="6e933-120">Extract any parameters required by the operation from the <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> property of the <xref:System.ComponentModel.DoWorkEventArgs> parameter.</span></span>  
  
7.  <span data-ttu-id="6e933-121">Výsledek výpočtu pro přiřazení <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> vlastnost <xref:System.ComponentModel.DoWorkEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="6e933-121">Assign the result of the computation to the <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> property of the <xref:System.ComponentModel.DoWorkEventArgs>.</span></span>  
  
     <span data-ttu-id="6e933-122">Toto je bude mít k dispozici <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="6e933-122">This is will be available to the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#2)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#2)]  
  
8.  <span data-ttu-id="6e933-123">Vložení kódu pro načítání výsledek vaše operace v <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="6e933-123">Insert code for retrieving the result of your operation in the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#3)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#3)]  
  
9. <span data-ttu-id="6e933-124">Implementace `TimeConsumingOperation` metoda.</span><span class="sxs-lookup"><span data-stu-id="6e933-124">Implement the `TimeConsumingOperation` method.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#4)]  
  
10. <span data-ttu-id="6e933-125">V Návrháři formulářů Windows, klikněte dvakrát na `startButton` vytvořit <xref:System.Windows.Forms.Control.Click> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="6e933-125">In the Windows Forms Designer, double-click `startButton` to create the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
11. <span data-ttu-id="6e933-126">Volání <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metoda v <xref:System.Windows.Forms.Control.Click> obslužné rutiny události pro `startButton`.</span><span class="sxs-lookup"><span data-stu-id="6e933-126">Call the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method in the <xref:System.Windows.Forms.Control.Click> event handler for `startButton`.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#5)]  
  
12. <span data-ttu-id="6e933-127">V Návrháři formulářů Windows, klikněte dvakrát na `cancelButton` vytvořit <xref:System.Windows.Forms.Control.Click> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="6e933-127">In the Windows Forms Designer, double-click `cancelButton` to create the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
13. <span data-ttu-id="6e933-128">Volání <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> metoda v <xref:System.Windows.Forms.Control.Click> obslužné rutiny události pro `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="6e933-128">Call the <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> method in the <xref:System.Windows.Forms.Control.Click> event handler for `cancelButton`.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#6)]  
  
14. <span data-ttu-id="6e933-129">V horní části souboru importujte System.ComponentModel a System.Threading – obory názvů.</span><span class="sxs-lookup"><span data-stu-id="6e933-129">At the top of the file, import the System.ComponentModel and System.Threading namespaces.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#7)]  
  
15. <span data-ttu-id="6e933-130">Stiskněte klávesu F6 sestavte řešení a potom stiskněte klávesu CTRL + F5 a spusťte aplikaci mimo ladicí program.</span><span class="sxs-lookup"><span data-stu-id="6e933-130">Press F6 to build the solution, and then press CTRL-F5 to run the application outside the debugger.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e933-131">Pokud je stisknutím klávesy F5 aplikaci spustit v ladicím programu, výjimka vyvolána v `TimeConsumingOperation` metoda zachycení a zobrazit pomocí ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="6e933-131">If you press F5 to run the application under the debugger, the exception raised in the `TimeConsumingOperation` method is caught and displayed by the debugger.</span></span> <span data-ttu-id="6e933-132">Při spuštění aplikace mimo ladicí program, <xref:System.ComponentModel.BackgroundWorker> ošetří výjimku a ukládá ho do mezipaměti <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> vlastnost <xref:System.ComponentModel.RunWorkerCompletedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="6e933-132">When you run the application outside the debugger, the <xref:System.ComponentModel.BackgroundWorker> handles the exception and caches it in the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> property of the <xref:System.ComponentModel.RunWorkerCompletedEventArgs>.</span></span>  
  
1.  <span data-ttu-id="6e933-133">Klikněte na tlačítko **spustit** tlačítko Spustit asynchronní operaci a potom klikněte na **zrušit** tlačítko zastavení spuštění asynchronní operaci.</span><span class="sxs-lookup"><span data-stu-id="6e933-133">Click the **Start** button to run an asynchronous operation, and then click the **Cancel** button to stop a running asynchronous operation.</span></span>  
  
     <span data-ttu-id="6e933-134">Výsledek každé operace se zobrazí v <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="6e933-134">The outcome of each operation is displayed in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="6e933-135">Další kroky</span><span class="sxs-lookup"><span data-stu-id="6e933-135">Next Steps</span></span>  
  
-   <span data-ttu-id="6e933-136">Implementace formuláře, který sestavy průběhu jako asynchronní operaci pokračuje.</span><span class="sxs-lookup"><span data-stu-id="6e933-136">Implement a form that reports progress as an asynchronous operation proceeds.</span></span> <span data-ttu-id="6e933-137">Další informace najdete v tématu [postupy: implementace formuláře, který používá operaci na pozadí](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).</span><span class="sxs-lookup"><span data-stu-id="6e933-137">For more information, see [How to: Implement a Form That Uses a Background Operation](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).</span></span>  
  
-   <span data-ttu-id="6e933-138">Implementujte třídu, která podporuje asynchronní vzor pro součásti.</span><span class="sxs-lookup"><span data-stu-id="6e933-138">Implement a class that supports the Asynchronous Pattern for Components.</span></span> <span data-ttu-id="6e933-139">Další informace najdete v tématu [implementace asynchronního vzoru založeného na událostech](../../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="6e933-139">For more information, see [Implementing the Event-based Asynchronous Pattern](../../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e933-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e933-140">See Also</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.DoWorkEventArgs>  
 [<span data-ttu-id="6e933-141">Postupy: Implementace formuláře, který používá operaci na pozadí</span><span class="sxs-lookup"><span data-stu-id="6e933-141">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [<span data-ttu-id="6e933-142">Postupy: Spuštění operace na pozadí</span><span class="sxs-lookup"><span data-stu-id="6e933-142">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [<span data-ttu-id="6e933-143">Komponenta BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="6e933-143">BackgroundWorker Component</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
