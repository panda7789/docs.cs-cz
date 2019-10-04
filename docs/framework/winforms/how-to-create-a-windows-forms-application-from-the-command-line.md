---
title: 'Postupy: Vytvoření aplikace model Windows Forms z příkazového řádku'
ms.date: 03/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da7fdab1cf67ffd47acb75533fcfdb89664c86d3
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834812"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a><span data-ttu-id="578fc-102">Postupy: Vytvoření aplikace model Windows Forms z příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="578fc-102">How to: Create a Windows Forms application from the command line</span></span>

<span data-ttu-id="578fc-103">Následující postupy popisují základní kroky, které je nutné provést, chcete-li vytvořit a spustit aplikaci model Windows Forms z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="578fc-103">The following procedures describe the basic steps that you must complete to create and run a Windows Forms application from the command line.</span></span> <span data-ttu-id="578fc-104">Existuje Rozsáhlá podpora těchto postupů v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="578fc-104">There is extensive support for these procedures in Visual Studio.</span></span>  <span data-ttu-id="578fc-105">Viz také [Návod: hostování ovládacího prvku model Windows Forms v](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)subsystému WPF.</span><span class="sxs-lookup"><span data-stu-id="578fc-105">Also see [Walkthrough: Hosting a Windows Forms Control in WPF](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>
  
## <a name="procedure"></a><span data-ttu-id="578fc-106">Postup</span><span class="sxs-lookup"><span data-stu-id="578fc-106">Procedure</span></span>  
  
#### <a name="to-create-the-form"></a><span data-ttu-id="578fc-107">Vytvoření formuláře</span><span class="sxs-lookup"><span data-stu-id="578fc-107">To create the form</span></span>  
  
1. <span data-ttu-id="578fc-108">V prázdném souboru kódu zadejte následující příkaz `Imports` nebo `using`:</span><span class="sxs-lookup"><span data-stu-id="578fc-108">In an empty code file, type the following `Imports` or `using` statements:</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. <span data-ttu-id="578fc-109">Deklarovat třídu s názvem `Form1`, která dědí z třídy Form:</span><span class="sxs-lookup"><span data-stu-id="578fc-109">Declare a class named `Form1` that inherits from the Form class:</span></span>
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. <span data-ttu-id="578fc-110">Vytvořte konstruktor bez parametrů pro `Form1`.</span><span class="sxs-lookup"><span data-stu-id="578fc-110">Create a parameterless constructor for `Form1`.</span></span>
  
     <span data-ttu-id="578fc-111">V následné proceduře přidáte do konstruktoru více kódu.</span><span class="sxs-lookup"><span data-stu-id="578fc-111">You will add more code to the constructor in a subsequent procedure.</span></span>
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. <span data-ttu-id="578fc-112">Přidejte do třídy metodu `Main`.</span><span class="sxs-lookup"><span data-stu-id="578fc-112">Add a `Main` method to the class.</span></span>
  
    1. <span data-ttu-id="578fc-113">Použijte <xref:System.STAThreadAttribute> na metodu C# `Main`, abyste určili, že vaše aplikace model Windows Forms je objekt Apartment s jedním vláknem.</span><span class="sxs-lookup"><span data-stu-id="578fc-113">Apply the <xref:System.STAThreadAttribute> to the C# `Main` method to specify your Windows Forms application is a single-threaded apartment.</span></span> <span data-ttu-id="578fc-114">(Atribut není v Visual Basic potřebný, protože aplikace Windows Forms vyvinuté pomocí Visual Basic ve výchozím nastavení používají model Apartment s jedním vláknem.)</span><span class="sxs-lookup"><span data-stu-id="578fc-114">(The attribute is not necessary in Visual Basic, since Windows forms applications developed with Visual Basic use a single-threaded apartment model by default.)</span></span>  
  
    2. <span data-ttu-id="578fc-115">Chcete-li pro aplikaci použít styly operačního systému, zavolejte <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span><span class="sxs-lookup"><span data-stu-id="578fc-115">Call <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> to apply operating system styles to your application.</span></span>  
  
    3. <span data-ttu-id="578fc-116">Vytvořte instanci formuláře a spusťte ji.</span><span class="sxs-lookup"><span data-stu-id="578fc-116">Create an instance of the form and run it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a><span data-ttu-id="578fc-117">Kompilace a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="578fc-117">To compile and run the application</span></span>  
  
1. <span data-ttu-id="578fc-118">Na příkazovém řádku .NET Framework přejděte do adresáře, který jste vytvořili `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="578fc-118">At the .NET Framework command prompt, navigate to the directory you created the `Form1` class.</span></span>  
  
2. <span data-ttu-id="578fc-119">Zkompilujte formulář.</span><span class="sxs-lookup"><span data-stu-id="578fc-119">Compile the form.</span></span>  
  
    - <span data-ttu-id="578fc-120">Pokud používáte C#, zadejte: `csc form1.cs`</span><span class="sxs-lookup"><span data-stu-id="578fc-120">If you are using C#, type: `csc form1.cs`</span></span>  
  
         `-or-`  
  
    - <span data-ttu-id="578fc-121">Pokud používáte Visual Basic, zadejte: `vbc form1.vb`</span><span class="sxs-lookup"><span data-stu-id="578fc-121">If you are using Visual Basic, type: `vbc form1.vb`</span></span>  
  
3. <span data-ttu-id="578fc-122">Do příkazového řádku zadejte: `Form1.exe`</span><span class="sxs-lookup"><span data-stu-id="578fc-122">At the command prompt, type: `Form1.exe`</span></span>  
  
## <a name="adding-a-control-and-handling-an-event"></a><span data-ttu-id="578fc-123">Přidání ovládacího prvku a zpracování události</span><span class="sxs-lookup"><span data-stu-id="578fc-123">Adding a control and handling an event</span></span>

<span data-ttu-id="578fc-124">Předchozí kroky postupu ukázaly, jak vytvořit základní formulář Windows, který se zkompiluje a spustí.</span><span class="sxs-lookup"><span data-stu-id="578fc-124">The previous procedure steps demonstrated how to just create a basic Windows Form that compiles and runs.</span></span> <span data-ttu-id="578fc-125">Další postup vám ukáže, jak vytvořit a přidat ovládací prvek do formuláře a zpracovat událost pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="578fc-125">The next procedure will show you how to create and add a control to the form, and handle an event for the control.</span></span> <span data-ttu-id="578fc-126">Další informace o ovládacích prvcích, které lze přidat do model Windows Forms, naleznete v tématu [model Windows Forms Controls](./controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="578fc-126">For more information about the controls you can add to Windows Forms, see [Windows Forms Controls](./controls/index.md).</span></span>
  
 <span data-ttu-id="578fc-127">Kromě pochopení způsobu vytváření model Windows Formsch aplikací byste měli pochopit programování založené na událostech a postup zpracování vstupu uživatele.</span><span class="sxs-lookup"><span data-stu-id="578fc-127">In addition to understanding how to create Windows Forms applications, you should understand event-based programming and how to handle user input.</span></span> <span data-ttu-id="578fc-128">Další informace naleznete v tématu [vytváření obslužných rutin událostí v model Windows Forms](creating-event-handlers-in-windows-forms.md)a [zpracování vstupu uživatele](./controls/handling-user-input.md) .</span><span class="sxs-lookup"><span data-stu-id="578fc-128">For more information, see [Creating Event Handlers in Windows Forms](creating-event-handlers-in-windows-forms.md), and [Handling User Input](./controls/handling-user-input.md)</span></span>  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a><span data-ttu-id="578fc-129">Deklarace ovládacího prvku tlačítko a zpracování jeho události Click</span><span class="sxs-lookup"><span data-stu-id="578fc-129">To declare a button control and handle its click event</span></span>  
  
1. <span data-ttu-id="578fc-130">Deklarujte ovládací prvek Button s názvem `button1`.</span><span class="sxs-lookup"><span data-stu-id="578fc-130">Declare a button control named `button1`.</span></span>  
  
2. <span data-ttu-id="578fc-131">V konstruktoru vytvořte tlačítko a nastavte jeho vlastnosti <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> a <xref:System.Windows.Forms.Control.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="578fc-131">In the constructor, create the button and set its <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Text%2A> properties.</span></span>  
  
3. <span data-ttu-id="578fc-132">Přidejte tlačítko do formuláře.</span><span class="sxs-lookup"><span data-stu-id="578fc-132">Add the button to the form.</span></span>  
  
     <span data-ttu-id="578fc-133">Následující příklad kódu ukazuje, jak deklarovat ovládací prvek tlačítko:</span><span class="sxs-lookup"><span data-stu-id="578fc-133">The following code example demonstrates how to declare the button control:</span></span>
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="578fc-134">Vytvořte metodu pro zpracování události <xref:System.Windows.Forms.Control.Click> pro tlačítko.</span><span class="sxs-lookup"><span data-stu-id="578fc-134">Create a method to handle the <xref:System.Windows.Forms.Control.Click> event for the button.</span></span>  
  
5. <span data-ttu-id="578fc-135">V obslužné rutině události Click Zobrazte <xref:System.Windows.Forms.MessageBox> se zprávou "Hello World".</span><span class="sxs-lookup"><span data-stu-id="578fc-135">In the click event handler, display a <xref:System.Windows.Forms.MessageBox> with the message, "Hello World".</span></span>  
  
     <span data-ttu-id="578fc-136">Následující příklad kódu ukazuje, jak zpracovat událost kliknutí ovládacího prvku tlačítko:</span><span class="sxs-lookup"><span data-stu-id="578fc-136">The following code example demonstrates how to handle the button control's click event:</span></span>
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. <span data-ttu-id="578fc-137">Přidružte událost <xref:System.Windows.Forms.Control.Click> k metodě, kterou jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="578fc-137">Associate the <xref:System.Windows.Forms.Control.Click> event with the method you created.</span></span>  
  
     <span data-ttu-id="578fc-138">Následující příklad kódu ukazuje, jak přidružit událost k metodě.</span><span class="sxs-lookup"><span data-stu-id="578fc-138">The following code example demonstrates how to associate the event with the method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. <span data-ttu-id="578fc-139">Zkompilujte a spusťte aplikaci, jak je popsáno v předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="578fc-139">Compile and run the application as described in the previous procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="578fc-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="578fc-140">Example</span></span>  
 
<span data-ttu-id="578fc-141">Následující příklad kódu je kompletní příklad z předchozích postupů:</span><span class="sxs-lookup"><span data-stu-id="578fc-141">The following code example is the complete example from the previous procedures:</span></span>
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="578fc-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="578fc-142">See also</span></span>

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [<span data-ttu-id="578fc-143">Změna vzhledu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="578fc-143">Changing the Appearance of Windows Forms</span></span>](changing-the-appearance-of-windows-forms.md)
- [<span data-ttu-id="578fc-144">Rozšiřování formulářových aplikací Windows</span><span class="sxs-lookup"><span data-stu-id="578fc-144">Enhancing Windows Forms Applications</span></span>](./advanced/index.md)
- [<span data-ttu-id="578fc-145">Začínáme s Windows Forms</span><span class="sxs-lookup"><span data-stu-id="578fc-145">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
