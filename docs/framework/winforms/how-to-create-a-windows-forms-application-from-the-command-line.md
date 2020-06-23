---
title: Vytvoření aplikace model Windows Forms z příkazového řádku
titleSuffix: ''
description: Naučte se, jak provést základní kroky pro vytvoření a spuštění aplikace model Windows Forms z příkazového řádku.
ms.date: 03/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
ms.openlocfilehash: b63bf884b9fd03a0510c7f240f19d7a14196971a
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903451"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a><span data-ttu-id="cae35-103">Postupy: Vytvoření aplikace model Windows Forms z příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="cae35-103">How to: Create a Windows Forms application from the command line</span></span>

<span data-ttu-id="cae35-104">Následující postupy popisují základní kroky, které je nutné provést, chcete-li vytvořit a spustit aplikaci model Windows Forms z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="cae35-104">The following procedures describe the basic steps that you must complete to create and run a Windows Forms application from the command line.</span></span> <span data-ttu-id="cae35-105">Existuje Rozsáhlá podpora těchto postupů v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cae35-105">There is extensive support for these procedures in Visual Studio.</span></span>  <span data-ttu-id="cae35-106">Viz také [Návod: hostování ovládacího prvku model Windows Forms v](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)subsystému WPF.</span><span class="sxs-lookup"><span data-stu-id="cae35-106">Also see [Walkthrough: Hosting a Windows Forms Control in WPF](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>
  
## <a name="procedure"></a><span data-ttu-id="cae35-107">Postup</span><span class="sxs-lookup"><span data-stu-id="cae35-107">Procedure</span></span>  
  
#### <a name="to-create-the-form"></a><span data-ttu-id="cae35-108">Vytvoření formuláře</span><span class="sxs-lookup"><span data-stu-id="cae35-108">To create the form</span></span>  
  
1. <span data-ttu-id="cae35-109">V prázdném souboru kódu zadejte následující `Imports` `using` příkazy nebo:</span><span class="sxs-lookup"><span data-stu-id="cae35-109">In an empty code file, type the following `Imports` or `using` statements:</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. <span data-ttu-id="cae35-110">Deklarovat třídu s názvem `Form1` , která dědí z třídy Form:</span><span class="sxs-lookup"><span data-stu-id="cae35-110">Declare a class named `Form1` that inherits from the Form class:</span></span>
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. <span data-ttu-id="cae35-111">Vytvořte konstruktor bez parametrů pro `Form1` .</span><span class="sxs-lookup"><span data-stu-id="cae35-111">Create a parameterless constructor for `Form1`.</span></span>
  
     <span data-ttu-id="cae35-112">V následné proceduře přidáte do konstruktoru více kódu.</span><span class="sxs-lookup"><span data-stu-id="cae35-112">You will add more code to the constructor in a subsequent procedure.</span></span>
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. <span data-ttu-id="cae35-113">Přidejte `Main` do třídy metodu.</span><span class="sxs-lookup"><span data-stu-id="cae35-113">Add a `Main` method to the class.</span></span>
  
    1. <span data-ttu-id="cae35-114">Použijte <xref:System.STAThreadAttribute> pro metodu jazyka C# `Main` k určení vaší aplikace model Windows Forms je jeden vláknový objekt Apartment.</span><span class="sxs-lookup"><span data-stu-id="cae35-114">Apply the <xref:System.STAThreadAttribute> to the C# `Main` method to specify your Windows Forms application is a single-threaded apartment.</span></span> <span data-ttu-id="cae35-115">(Atribut není v Visual Basic potřebný, protože aplikace Windows Forms vyvinuté pomocí Visual Basic ve výchozím nastavení používají model Apartment s jedním vláknem.)</span><span class="sxs-lookup"><span data-stu-id="cae35-115">(The attribute is not necessary in Visual Basic, since Windows forms applications developed with Visual Basic use a single-threaded apartment model by default.)</span></span>  
  
    2. <span data-ttu-id="cae35-116">Zavolejte <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> na použít pro aplikaci styly operačního systému.</span><span class="sxs-lookup"><span data-stu-id="cae35-116">Call <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> to apply operating system styles to your application.</span></span>  
  
    3. <span data-ttu-id="cae35-117">Vytvořte instanci formuláře a spusťte ji.</span><span class="sxs-lookup"><span data-stu-id="cae35-117">Create an instance of the form and run it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a><span data-ttu-id="cae35-118">Kompilace a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="cae35-118">To compile and run the application</span></span>  
  
1. <span data-ttu-id="cae35-119">Na příkazovém řádku .NET Framework přejděte do adresáře, ve kterém jste třídu vytvořili `Form1` .</span><span class="sxs-lookup"><span data-stu-id="cae35-119">At the .NET Framework command prompt, navigate to the directory you created the `Form1` class.</span></span>  
  
2. <span data-ttu-id="cae35-120">Zkompilujte formulář.</span><span class="sxs-lookup"><span data-stu-id="cae35-120">Compile the form.</span></span>  
  
    - <span data-ttu-id="cae35-121">Pokud používáte jazyk C#, zadejte:`csc form1.cs`</span><span class="sxs-lookup"><span data-stu-id="cae35-121">If you are using C#, type: `csc form1.cs`</span></span>  
  
         `-or-`  
  
    - <span data-ttu-id="cae35-122">Pokud používáte Visual Basic, zadejte:`vbc form1.vb`</span><span class="sxs-lookup"><span data-stu-id="cae35-122">If you are using Visual Basic, type: `vbc form1.vb`</span></span>  
  
3. <span data-ttu-id="cae35-123">Do příkazového řádku zadejte:`Form1.exe`</span><span class="sxs-lookup"><span data-stu-id="cae35-123">At the command prompt, type: `Form1.exe`</span></span>  
  
## <a name="adding-a-control-and-handling-an-event"></a><span data-ttu-id="cae35-124">Přidání ovládacího prvku a zpracování události</span><span class="sxs-lookup"><span data-stu-id="cae35-124">Adding a control and handling an event</span></span>

<span data-ttu-id="cae35-125">Předchozí kroky postupu ukázaly, jak vytvořit základní formulář Windows, který se zkompiluje a spustí.</span><span class="sxs-lookup"><span data-stu-id="cae35-125">The previous procedure steps demonstrated how to just create a basic Windows Form that compiles and runs.</span></span> <span data-ttu-id="cae35-126">Další postup vám ukáže, jak vytvořit a přidat ovládací prvek do formuláře a zpracovat událost pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="cae35-126">The next procedure will show you how to create and add a control to the form, and handle an event for the control.</span></span> <span data-ttu-id="cae35-127">Další informace o ovládacích prvcích, které lze přidat do model Windows Forms, naleznete v tématu [model Windows Forms Controls](./controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="cae35-127">For more information about the controls you can add to Windows Forms, see [Windows Forms Controls](./controls/index.md).</span></span>
  
 <span data-ttu-id="cae35-128">Kromě pochopení způsobu vytváření model Windows Formsch aplikací byste měli pochopit programování založené na událostech a postup zpracování vstupu uživatele.</span><span class="sxs-lookup"><span data-stu-id="cae35-128">In addition to understanding how to create Windows Forms applications, you should understand event-based programming and how to handle user input.</span></span> <span data-ttu-id="cae35-129">Další informace naleznete v tématu [vytváření obslužných rutin událostí v model Windows Forms](creating-event-handlers-in-windows-forms.md)a [zpracování vstupu uživatele](./controls/handling-user-input.md) .</span><span class="sxs-lookup"><span data-stu-id="cae35-129">For more information, see [Creating Event Handlers in Windows Forms](creating-event-handlers-in-windows-forms.md), and [Handling User Input](./controls/handling-user-input.md)</span></span>  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a><span data-ttu-id="cae35-130">Deklarace ovládacího prvku tlačítko a zpracování jeho události Click</span><span class="sxs-lookup"><span data-stu-id="cae35-130">To declare a button control and handle its click event</span></span>  
  
1. <span data-ttu-id="cae35-131">Deklarujte ovládací prvek tlačítko s názvem `button1` .</span><span class="sxs-lookup"><span data-stu-id="cae35-131">Declare a button control named `button1`.</span></span>  
  
2. <span data-ttu-id="cae35-132">V konstruktoru vytvořte tlačítko a nastavte jeho <xref:System.Windows.Forms.Control.Size%2A> <xref:System.Windows.Forms.Control.Location%2A> <xref:System.Windows.Forms.Control.Text%2A> vlastnosti a.</span><span class="sxs-lookup"><span data-stu-id="cae35-132">In the constructor, create the button and set its <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Text%2A> properties.</span></span>  
  
3. <span data-ttu-id="cae35-133">Přidejte tlačítko do formuláře.</span><span class="sxs-lookup"><span data-stu-id="cae35-133">Add the button to the form.</span></span>  
  
     <span data-ttu-id="cae35-134">Následující příklad kódu ukazuje, jak deklarovat ovládací prvek tlačítko:</span><span class="sxs-lookup"><span data-stu-id="cae35-134">The following code example demonstrates how to declare the button control:</span></span>
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="cae35-135">Vytvořte metodu pro zpracování <xref:System.Windows.Forms.Control.Click> události pro tlačítko.</span><span class="sxs-lookup"><span data-stu-id="cae35-135">Create a method to handle the <xref:System.Windows.Forms.Control.Click> event for the button.</span></span>  
  
5. <span data-ttu-id="cae35-136">V obslužné rutině události Click se zobrazí <xref:System.Windows.Forms.MessageBox> zpráva "Hello World".</span><span class="sxs-lookup"><span data-stu-id="cae35-136">In the click event handler, display a <xref:System.Windows.Forms.MessageBox> with the message, "Hello World".</span></span>  
  
     <span data-ttu-id="cae35-137">Následující příklad kódu ukazuje, jak zpracovat událost kliknutí ovládacího prvku tlačítko:</span><span class="sxs-lookup"><span data-stu-id="cae35-137">The following code example demonstrates how to handle the button control's click event:</span></span>
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. <span data-ttu-id="cae35-138">Přidružte <xref:System.Windows.Forms.Control.Click> událost k metodě, kterou jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="cae35-138">Associate the <xref:System.Windows.Forms.Control.Click> event with the method you created.</span></span>  
  
     <span data-ttu-id="cae35-139">Následující příklad kódu ukazuje, jak přidružit událost k metodě.</span><span class="sxs-lookup"><span data-stu-id="cae35-139">The following code example demonstrates how to associate the event with the method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. <span data-ttu-id="cae35-140">Zkompilujte a spusťte aplikaci, jak je popsáno v předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="cae35-140">Compile and run the application as described in the previous procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cae35-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="cae35-141">Example</span></span>  

<span data-ttu-id="cae35-142">Následující příklad kódu je kompletní příklad z předchozích postupů:</span><span class="sxs-lookup"><span data-stu-id="cae35-142">The following code example is the complete example from the previous procedures:</span></span>
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="cae35-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="cae35-143">See also</span></span>

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [<span data-ttu-id="cae35-144">Změna vzhledu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cae35-144">Changing the Appearance of Windows Forms</span></span>](changing-the-appearance-of-windows-forms.md)
- [<span data-ttu-id="cae35-145">Rozšiřování formulářových aplikací Windows</span><span class="sxs-lookup"><span data-stu-id="cae35-145">Enhancing Windows Forms Applications</span></span>](./advanced/index.md)
- [<span data-ttu-id="cae35-146">Začínáme s Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cae35-146">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
