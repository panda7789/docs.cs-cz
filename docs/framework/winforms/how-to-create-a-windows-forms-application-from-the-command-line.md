---
title: Vytvoření aplikace pro Windows Forms z příkazového řádku
titleSuffix: ''
ms.date: 03/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
ms.openlocfilehash: 7bd3add526a6b60d628b05d46eca22ce407c36b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181990"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a><span data-ttu-id="46d7a-102">Postup: Vytvoření aplikace pro Windows Forms z příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="46d7a-102">How to: Create a Windows Forms application from the command line</span></span>

<span data-ttu-id="46d7a-103">Následující postupy popisují základní kroky, které je nutné provést k vytvoření a spuštění aplikace windows forms z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="46d7a-103">The following procedures describe the basic steps that you must complete to create and run a Windows Forms application from the command line.</span></span> <span data-ttu-id="46d7a-104">Existuje rozsáhlá podpora pro tyto postupy v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="46d7a-104">There is extensive support for these procedures in Visual Studio.</span></span>  <span data-ttu-id="46d7a-105">Viz [také návod: Hostování ovládacího prvku Windows Forms Ve wpf](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="46d7a-105">Also see [Walkthrough: Hosting a Windows Forms Control in WPF](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>
  
## <a name="procedure"></a><span data-ttu-id="46d7a-106">Postup</span><span class="sxs-lookup"><span data-stu-id="46d7a-106">Procedure</span></span>  
  
#### <a name="to-create-the-form"></a><span data-ttu-id="46d7a-107">Vytvoření formuláře</span><span class="sxs-lookup"><span data-stu-id="46d7a-107">To create the form</span></span>  
  
1. <span data-ttu-id="46d7a-108">Do prázdného souboru kódu `Imports` `using` zadejte následující příkazy nebo příkazy:</span><span class="sxs-lookup"><span data-stu-id="46d7a-108">In an empty code file, type the following `Imports` or `using` statements:</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. <span data-ttu-id="46d7a-109">Deklarujte `Form1` třídu s názvem, která dědí z třídy Form:</span><span class="sxs-lookup"><span data-stu-id="46d7a-109">Declare a class named `Form1` that inherits from the Form class:</span></span>
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. <span data-ttu-id="46d7a-110">Vytvořte konstruktor bez `Form1`parametrů pro .</span><span class="sxs-lookup"><span data-stu-id="46d7a-110">Create a parameterless constructor for `Form1`.</span></span>
  
     <span data-ttu-id="46d7a-111">Přidáte další kód konstruktoru v následném postupu.</span><span class="sxs-lookup"><span data-stu-id="46d7a-111">You will add more code to the constructor in a subsequent procedure.</span></span>
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. <span data-ttu-id="46d7a-112">Přidejte `Main` metodu do třídy.</span><span class="sxs-lookup"><span data-stu-id="46d7a-112">Add a `Main` method to the class.</span></span>
  
    1. <span data-ttu-id="46d7a-113">Použijte <xref:System.STAThreadAttribute> metodu C# `Main` k určení aplikace Windows Forms je apartment s jedním podprocesem.</span><span class="sxs-lookup"><span data-stu-id="46d7a-113">Apply the <xref:System.STAThreadAttribute> to the C# `Main` method to specify your Windows Forms application is a single-threaded apartment.</span></span> <span data-ttu-id="46d7a-114">(Atribut není nutné v jazyce Visual Basic, protože formuláře systému Windows aplikace vyvinuté v jazyce Visual Basic použít model apartment s jedním podprocesem ve výchozím nastavení.)</span><span class="sxs-lookup"><span data-stu-id="46d7a-114">(The attribute is not necessary in Visual Basic, since Windows forms applications developed with Visual Basic use a single-threaded apartment model by default.)</span></span>  
  
    2. <span data-ttu-id="46d7a-115">Volání <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> použít styly operačního systému pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="46d7a-115">Call <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> to apply operating system styles to your application.</span></span>  
  
    3. <span data-ttu-id="46d7a-116">Vytvořte instanci formuláře a spusťte ji.</span><span class="sxs-lookup"><span data-stu-id="46d7a-116">Create an instance of the form and run it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a><span data-ttu-id="46d7a-117">Kompilace a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="46d7a-117">To compile and run the application</span></span>  
  
1. <span data-ttu-id="46d7a-118">Na příkazovém řádku rozhraní .NET Framework `Form1` přejděte do adresáře, který jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="46d7a-118">At the .NET Framework command prompt, navigate to the directory you created the `Form1` class.</span></span>  
  
2. <span data-ttu-id="46d7a-119">Zkompilujte formulář.</span><span class="sxs-lookup"><span data-stu-id="46d7a-119">Compile the form.</span></span>  
  
    - <span data-ttu-id="46d7a-120">Pokud používáte C#, zadejte:`csc form1.cs`</span><span class="sxs-lookup"><span data-stu-id="46d7a-120">If you are using C#, type: `csc form1.cs`</span></span>  
  
         `-or-`  
  
    - <span data-ttu-id="46d7a-121">Pokud používáte jazyk Visual Basic, zadejte:`vbc form1.vb`</span><span class="sxs-lookup"><span data-stu-id="46d7a-121">If you are using Visual Basic, type: `vbc form1.vb`</span></span>  
  
3. <span data-ttu-id="46d7a-122">Na příkazovém řádku zadejte:`Form1.exe`</span><span class="sxs-lookup"><span data-stu-id="46d7a-122">At the command prompt, type: `Form1.exe`</span></span>  
  
## <a name="adding-a-control-and-handling-an-event"></a><span data-ttu-id="46d7a-123">Přidání ovládacího prvku a zpracování události</span><span class="sxs-lookup"><span data-stu-id="46d7a-123">Adding a control and handling an event</span></span>

<span data-ttu-id="46d7a-124">Předchozí kroky postupu ukázaly, jak pouze vytvořit základní formulář systému Windows, který kompiluje a spouští.</span><span class="sxs-lookup"><span data-stu-id="46d7a-124">The previous procedure steps demonstrated how to just create a basic Windows Form that compiles and runs.</span></span> <span data-ttu-id="46d7a-125">Další postup vám ukáže, jak vytvořit a přidat ovládací prvek do formuláře a zpracovat událost pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="46d7a-125">The next procedure will show you how to create and add a control to the form, and handle an event for the control.</span></span> <span data-ttu-id="46d7a-126">Další informace o ovládacích prvcích, které lze přidat do systému Windows Forms, naleznete v [tématu Ovládací prvky forem systému Windows](./controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="46d7a-126">For more information about the controls you can add to Windows Forms, see [Windows Forms Controls](./controls/index.md).</span></span>
  
 <span data-ttu-id="46d7a-127">Kromě pochopení, jak vytvářet aplikace windows forms, měli byste pochopit programování založené na událostech a jak zpracovat vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="46d7a-127">In addition to understanding how to create Windows Forms applications, you should understand event-based programming and how to handle user input.</span></span> <span data-ttu-id="46d7a-128">Další informace naleznete [v tématech Vytváření obslužných rutin událostí ve formulářích systému Windows](creating-event-handlers-in-windows-forms.md)a Zpracování vstupu [uživatele.](./controls/handling-user-input.md)</span><span class="sxs-lookup"><span data-stu-id="46d7a-128">For more information, see [Creating Event Handlers in Windows Forms](creating-event-handlers-in-windows-forms.md), and [Handling User Input](./controls/handling-user-input.md)</span></span>  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a><span data-ttu-id="46d7a-129">Deklarování ovládacího prvku tlačítka a zpracování události kliknutí</span><span class="sxs-lookup"><span data-stu-id="46d7a-129">To declare a button control and handle its click event</span></span>  
  
1. <span data-ttu-id="46d7a-130">Deklarujte `button1`ovládací prvek tlačítka s názvem .</span><span class="sxs-lookup"><span data-stu-id="46d7a-130">Declare a button control named `button1`.</span></span>  
  
2. <span data-ttu-id="46d7a-131">V konstruktoru vytvořte tlačítko <xref:System.Windows.Forms.Control.Size%2A>a <xref:System.Windows.Forms.Control.Location%2A> <xref:System.Windows.Forms.Control.Text%2A> nastavte jeho vlastnosti a vlastnosti .</span><span class="sxs-lookup"><span data-stu-id="46d7a-131">In the constructor, create the button and set its <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Text%2A> properties.</span></span>  
  
3. <span data-ttu-id="46d7a-132">Přidejte tlačítko do formuláře.</span><span class="sxs-lookup"><span data-stu-id="46d7a-132">Add the button to the form.</span></span>  
  
     <span data-ttu-id="46d7a-133">Následující příklad kódu ukazuje, jak deklarovat ovládací prvek tlačítka:</span><span class="sxs-lookup"><span data-stu-id="46d7a-133">The following code example demonstrates how to declare the button control:</span></span>
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="46d7a-134">Vytvořte metodu <xref:System.Windows.Forms.Control.Click> pro zpracování události pro tlačítko.</span><span class="sxs-lookup"><span data-stu-id="46d7a-134">Create a method to handle the <xref:System.Windows.Forms.Control.Click> event for the button.</span></span>  
  
5. <span data-ttu-id="46d7a-135">V obslužné <xref:System.Windows.Forms.MessageBox> rutině události kliknutí zobrazte a se zprávou "Hello World".</span><span class="sxs-lookup"><span data-stu-id="46d7a-135">In the click event handler, display a <xref:System.Windows.Forms.MessageBox> with the message, "Hello World".</span></span>  
  
     <span data-ttu-id="46d7a-136">Následující příklad kódu ukazuje, jak zpracovat událost kliknutí ovládacího prvku tlačítka:</span><span class="sxs-lookup"><span data-stu-id="46d7a-136">The following code example demonstrates how to handle the button control's click event:</span></span>
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. <span data-ttu-id="46d7a-137">Přidružte <xref:System.Windows.Forms.Control.Click> událost k metodě, kterou jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="46d7a-137">Associate the <xref:System.Windows.Forms.Control.Click> event with the method you created.</span></span>  
  
     <span data-ttu-id="46d7a-138">Následující příklad kódu ukazuje, jak přidružit událost k metodě.</span><span class="sxs-lookup"><span data-stu-id="46d7a-138">The following code example demonstrates how to associate the event with the method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. <span data-ttu-id="46d7a-139">Zkompilujte a spusťte aplikaci, jak je popsáno v předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="46d7a-139">Compile and run the application as described in the previous procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46d7a-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="46d7a-140">Example</span></span>  

<span data-ttu-id="46d7a-141">Následující příklad kódu je úplný příklad z předchozích postupů:</span><span class="sxs-lookup"><span data-stu-id="46d7a-141">The following code example is the complete example from the previous procedures:</span></span>
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="46d7a-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="46d7a-142">See also</span></span>

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [<span data-ttu-id="46d7a-143">Změna vzhledu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="46d7a-143">Changing the Appearance of Windows Forms</span></span>](changing-the-appearance-of-windows-forms.md)
- [<span data-ttu-id="46d7a-144">Rozšiřování formulářových aplikací Windows</span><span class="sxs-lookup"><span data-stu-id="46d7a-144">Enhancing Windows Forms Applications</span></span>](./advanced/index.md)
- [<span data-ttu-id="46d7a-145">Začínáme s Windows Forms</span><span class="sxs-lookup"><span data-stu-id="46d7a-145">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
