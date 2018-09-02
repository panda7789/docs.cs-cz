---
title: 'Postupy: vytvoření aplikace Windows Forms z příkazového řádku'
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
ms.openlocfilehash: 7cfd90c5d38be788125af3bafe1e9ba034e9b957
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43400377"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a><span data-ttu-id="4e440-102">Postupy: vytvoření aplikace Windows Forms z příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="4e440-102">How to: Create a Windows Forms application from the command line</span></span>
<span data-ttu-id="4e440-103">Následující postupy popisují základní kroky, které je třeba provést k vytvoření a spuštění aplikace modelu Windows Forms z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="4e440-103">The following procedures describe the basic steps that you must complete to create and run a Windows Forms application from the command line.</span></span> <span data-ttu-id="4e440-104">Není k dispozici rozsáhlou podporu pro tyto postupy v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4e440-104">There is extensive support for these procedures in Visual Studio.</span></span>  <span data-ttu-id="4e440-105">Viz také [návod: vytvoření jednoduchého formuláře Windows](https://msdn.microsoft.com/library/z9w2f38k\(v=vs.100\)).</span><span class="sxs-lookup"><span data-stu-id="4e440-105">Also see [Walkthrough: Creating a Simple Windows Form](https://msdn.microsoft.com/library/z9w2f38k\(v=vs.100\)).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="4e440-106">Postup</span><span class="sxs-lookup"><span data-stu-id="4e440-106">Procedure</span></span>  
  
#### <a name="to-create-the-form"></a><span data-ttu-id="4e440-107">Vytvoření formuláře</span><span class="sxs-lookup"><span data-stu-id="4e440-107">To create the form</span></span>  
  
1.  <span data-ttu-id="4e440-108">Prázdný soubor kódu zadejte následující import nebo příkazy using:</span><span class="sxs-lookup"><span data-stu-id="4e440-108">In an empty code file, type the following import or using statements:</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2.  <span data-ttu-id="4e440-109">Deklarovat třídu s názvem `Form1` , která dědí z třídy formuláře.</span><span class="sxs-lookup"><span data-stu-id="4e440-109">Declare a class named `Form1` that inherits from the Form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3.  <span data-ttu-id="4e440-110">Výchozí konstruktor pro vytvoření `Form1`.</span><span class="sxs-lookup"><span data-stu-id="4e440-110">Create a default constructor for `Form1`.</span></span>  
  
     <span data-ttu-id="4e440-111">Přidejte další kód do konstruktoru v následujícím postupu.</span><span class="sxs-lookup"><span data-stu-id="4e440-111">You will add more code to the constructor in a subsequent procedure.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4.  <span data-ttu-id="4e440-112">Přidat `Main` metodu do třídy.</span><span class="sxs-lookup"><span data-stu-id="4e440-112">Add a `Main` method to the class.</span></span>  
  
    1.  <span data-ttu-id="4e440-113">Použít <xref:System.STAThreadAttribute> jazyka C# `Main` metoda k určení aplikace Windows Forms je jednovláknový apartment.</span><span class="sxs-lookup"><span data-stu-id="4e440-113">Apply the <xref:System.STAThreadAttribute> to the C# `Main` method to specify your Windows Forms application is a single-threaded apartment.</span></span> <span data-ttu-id="4e440-114">(Atribut není nutné v jazyce Visual Basic, protože aplikace Windows forms vyvinutých s využitím jazyka Visual Basic jednovláknový apartment modelu ve výchozím nastavení.)</span><span class="sxs-lookup"><span data-stu-id="4e440-114">(The attribute is not necessary in Visual Basic, since Windows forms applications developed with Visual Basic use a single-threaded apartment model by default.)</span></span>  
  
    2.  <span data-ttu-id="4e440-115">Volání <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> pro používání stylů pro operační systém pro vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="4e440-115">Call <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> to apply operating system styles to your application.</span></span>  
  
    3.  <span data-ttu-id="4e440-116">Vytvoření instance formuláře a spustíme ji.</span><span class="sxs-lookup"><span data-stu-id="4e440-116">Create an instance of the form and run it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a><span data-ttu-id="4e440-117">Kompilace a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="4e440-117">To compile and run the application</span></span>  
  
1.  <span data-ttu-id="4e440-118">Na příkazovém řádku rozhraní .NET Framework, přejděte do adresáře, který jste vytvořili `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="4e440-118">At the .NET Framework command prompt, navigate to the directory you created the `Form1` class.</span></span>  
  
2.  <span data-ttu-id="4e440-119">Zkompilujte formuláře.</span><span class="sxs-lookup"><span data-stu-id="4e440-119">Compile the form.</span></span>  
  
    -   <span data-ttu-id="4e440-120">Pokud používáte C#, zadejte: `csc form1.cs`</span><span class="sxs-lookup"><span data-stu-id="4e440-120">If you are using C#, type: `csc form1.cs`</span></span>  
  
         `-or-`  
  
    -   <span data-ttu-id="4e440-121">Pokud používáte Visual Basic, zadejte: `vbc form1.vb`</span><span class="sxs-lookup"><span data-stu-id="4e440-121">If you are using Visual Basic, type: `vbc form1.vb`</span></span>  
  
3.  <span data-ttu-id="4e440-122">Na příkazovém řádku zadejte: `Form1.exe`</span><span class="sxs-lookup"><span data-stu-id="4e440-122">At the command prompt, type: `Form1.exe`</span></span>  
  
## <a name="adding-a-control-and-handling-an-event"></a><span data-ttu-id="4e440-123">Přidání ovládacího prvku a zpracování událostí</span><span class="sxs-lookup"><span data-stu-id="4e440-123">Adding a Control and Handling an Event</span></span>  
 <span data-ttu-id="4e440-124">Předchozí kroky postupu jsme vám ukázali jen vytvoření základního formuláře Windows, který zkompiluje a spustí.</span><span class="sxs-lookup"><span data-stu-id="4e440-124">The previous procedure steps demonstrated how to just create a basic Windows Form that compiles and runs.</span></span> <span data-ttu-id="4e440-125">Následující postup obsahuje pokyny k vytvoření a přidání ovládacího prvku na formuláři a zpracovat události pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="4e440-125">The next procedure will show you how to create and add a control to the form, and handle an event for the control.</span></span> <span data-ttu-id="4e440-126">Další informace o ovládacích prvků můžete přidat do formulářů Windows, naleznete v tématu [ovládacích prvků Windows Forms](../../../docs/framework/winforms/controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="4e440-126">For more information about the controls you can add to Windows Forms, see [Windows Forms Controls](../../../docs/framework/winforms/controls/index.md).</span></span>  
  
 <span data-ttu-id="4e440-127">Kromě pochopení způsobu, jak vytvořit aplikace Windows Forms, měli byste porozumět programování založené na událostech a způsob zpracování vstupu uživatele.</span><span class="sxs-lookup"><span data-stu-id="4e440-127">In addition to understanding how to create Windows Forms applications, you should understand event-based programming and how to handle user input.</span></span> <span data-ttu-id="4e440-128">Další informace najdete v tématu [vytváření obslužných rutin událostí ve Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md), a [zpracování uživatelského vstupu](../../../docs/framework/winforms/controls/handling-user-input.md)</span><span class="sxs-lookup"><span data-stu-id="4e440-128">For more information, see [Creating Event Handlers in Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md), and [Handling User Input](../../../docs/framework/winforms/controls/handling-user-input.md)</span></span>  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a><span data-ttu-id="4e440-129">Deklarovat ovládací prvek button a zpracovat jeho událost click</span><span class="sxs-lookup"><span data-stu-id="4e440-129">To declare a button control and handle its click event</span></span>  
  
1.  <span data-ttu-id="4e440-130">Deklarovat ovládacího prvku tlačítko s názvem `button1`.</span><span class="sxs-lookup"><span data-stu-id="4e440-130">Declare a button control named `button1`.</span></span>  
  
2.  <span data-ttu-id="4e440-131">V konstruktoru, vytvořit tlačítko a nastavte jeho <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> a <xref:System.Windows.Forms.Control.Text%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4e440-131">In the constructor, create the button and set its <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Text%2A> properties.</span></span>  
  
3.  <span data-ttu-id="4e440-132">Přidání tlačítka do formuláře.</span><span class="sxs-lookup"><span data-stu-id="4e440-132">Add the button to the form.</span></span>  
  
     <span data-ttu-id="4e440-133">Následující příklad kódu ukazuje, jak deklarovat ovládací prvek tlačítko.</span><span class="sxs-lookup"><span data-stu-id="4e440-133">The following code example demonstrates how to declare the button control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4.  <span data-ttu-id="4e440-134">Vytvořit metodu ke zpracování <xref:System.Windows.Forms.Control.Click> události pro tlačítko.</span><span class="sxs-lookup"><span data-stu-id="4e440-134">Create a method to handle the <xref:System.Windows.Forms.Control.Click> event for the button.</span></span>  
  
5.  <span data-ttu-id="4e440-135">V obslužné rutině události kliknutí, zobrazení <xref:System.Windows.Forms.MessageBox> zprávou "Hello World".</span><span class="sxs-lookup"><span data-stu-id="4e440-135">In the click event handler, display a <xref:System.Windows.Forms.MessageBox> with the message, "Hello World".</span></span>  
  
     <span data-ttu-id="4e440-136">Následující příklad kódu ukazuje, jak zpracovat tlačítko ovládacího prvku klikněte na událost.</span><span class="sxs-lookup"><span data-stu-id="4e440-136">The following code example demonstrates how to handle the button control's click event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6.  <span data-ttu-id="4e440-137">Přidružit <xref:System.Windows.Forms.Control.Click> událostí pomocí metody, které jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="4e440-137">Associate the <xref:System.Windows.Forms.Control.Click> event with the method you created.</span></span>  
  
     <span data-ttu-id="4e440-138">Následující příklad kódu ukazuje, jak přidružit metodu události.</span><span class="sxs-lookup"><span data-stu-id="4e440-138">The following code example demonstrates how to associate the event with the method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7.  <span data-ttu-id="4e440-139">Kompilace a spuštění aplikace, jak je popsáno v předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="4e440-139">Compile and run the application as described in the previous procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e440-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="4e440-140">Example</span></span>  
 <span data-ttu-id="4e440-141">Následující ukázka kódu je kompletní příklad z předchozích kroků.</span><span class="sxs-lookup"><span data-stu-id="4e440-141">Following code example is the complete example from the previous procedures.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4e440-142">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="4e440-142">Compiling the Code</span></span>  
  
-   <span data-ttu-id="4e440-143">Chcete-li kód zkompilovat, postupujte podle pokynů v postupu budete pokračovat, které popisují, jak kompilace a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="4e440-143">To compile the code, follow the instructions in the proceeding procedure that describe how to compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e440-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e440-144">See Also</span></span>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.Windows.Forms.Control>  
 [<span data-ttu-id="4e440-145">Změna vzhledu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e440-145">Changing the Appearance of Windows Forms</span></span>](../../../docs/framework/winforms/changing-the-appearance-of-windows-forms.md)  
 [<span data-ttu-id="4e440-146">Rozšiřování aplikací Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e440-146">Enhancing Windows Forms Applications</span></span>](../../../docs/framework/winforms/advanced/index.md)  
 [<span data-ttu-id="4e440-147">Začínáme s Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e440-147">Getting Started with Windows Forms</span></span>](../../../docs/framework/winforms/getting-started-with-windows-forms.md)
