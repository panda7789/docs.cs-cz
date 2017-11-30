---
title: "Postupy: vytvoření aplikace Windows Forms z příkazového řádku"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-winforms
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e6ddb27f724e30071be339ac753cfd85599ccd86
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a><span data-ttu-id="449ad-102">Postupy: vytvoření aplikace Windows Forms z příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="449ad-102">How to: Create a Windows Forms application from the command line</span></span>
<span data-ttu-id="449ad-103">Následující postupy popisují základní kroky, které je třeba provést k vytvoření a spuštění aplikace Windows Forms z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="449ad-103">The following procedures describe the basic steps that you must complete to create and run a Windows Forms application from the command line.</span></span> <span data-ttu-id="449ad-104">Rozsáhlá podpora pro tyto postupy v sadě Visual Studio není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="449ad-104">There is extensive support for these procedures in Visual Studio.</span></span>  <span data-ttu-id="449ad-105">Viz také [návod: vytvoření jednoduché formuláře Windows](http://msdn.microsoft.com/library/z9w2f38k\(v=vs.100\)).</span><span class="sxs-lookup"><span data-stu-id="449ad-105">Also see [Walkthrough: Creating a Simple Windows Form](http://msdn.microsoft.com/library/z9w2f38k\(v=vs.100\)).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="449ad-106">Postup</span><span class="sxs-lookup"><span data-stu-id="449ad-106">Procedure</span></span>  
  
#### <a name="to-create-the-form"></a><span data-ttu-id="449ad-107">Vytvoření formuláře</span><span class="sxs-lookup"><span data-stu-id="449ad-107">To create the form</span></span>  
  
1.  <span data-ttu-id="449ad-108">V souboru prázdný kód zadejte následující importu nebo pomocí příkazů:</span><span class="sxs-lookup"><span data-stu-id="449ad-108">In an empty code file, type the following import or using statements:</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2.  <span data-ttu-id="449ad-109">Deklarace třídy s názvem `Form1` , dědí z třídy formuláře.</span><span class="sxs-lookup"><span data-stu-id="449ad-109">Declare a class named `Form1` that inherits from the Form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3.  <span data-ttu-id="449ad-110">Výchozí konstruktor pro vytvoření `Form1`.</span><span class="sxs-lookup"><span data-stu-id="449ad-110">Create a default constructor for `Form1`.</span></span>  
  
     <span data-ttu-id="449ad-111">Další kód přidá do konstruktoru v následujícím postupu.</span><span class="sxs-lookup"><span data-stu-id="449ad-111">You will add more code to the constructor in a subsequent procedure.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4.  <span data-ttu-id="449ad-112">Přidat `Main` metody pro třídu.</span><span class="sxs-lookup"><span data-stu-id="449ad-112">Add a `Main` method to the class.</span></span>  
  
    1.  <span data-ttu-id="449ad-113">Použít <xref:System.STAThreadAttribute> k `Main` metoda k určení aplikace Windows Forms je jeden model typu apartment.</span><span class="sxs-lookup"><span data-stu-id="449ad-113">Apply the <xref:System.STAThreadAttribute> to the `Main` method to specify your Windows Forms application is a single threaded apartment.</span></span>  
  
    2.  <span data-ttu-id="449ad-114">Volání <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> vzhled Windows XP do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="449ad-114">Call <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> to give a Windows XP appearance to your application.</span></span>  
  
    3.  <span data-ttu-id="449ad-115">Vytvoření instance formuláře a potom ho spusťte.</span><span class="sxs-lookup"><span data-stu-id="449ad-115">Create an instance of the form and run it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a><span data-ttu-id="449ad-116">Pro zkompilování a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="449ad-116">To compile and run the application</span></span>  
  
1.  <span data-ttu-id="449ad-117">Na příkazovém řádku rozhraní .NET Framework přejděte do adresáře, který jste vytvořili `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="449ad-117">At the .NET Framework command prompt, navigate to the directory you created the `Form1` class.</span></span>  
  
2.  <span data-ttu-id="449ad-118">Zkompilujte formuláře.</span><span class="sxs-lookup"><span data-stu-id="449ad-118">Compile the form.</span></span>  
  
    -   <span data-ttu-id="449ad-119">Pokud používáte C#, zadejte:`csc form1.cs`</span><span class="sxs-lookup"><span data-stu-id="449ad-119">If you are using C#, type: `csc form1.cs`</span></span>  
  
         `-or-`  
  
    -   <span data-ttu-id="449ad-120">Pokud používáte Visual Basic, zadejte:`vbc form1.vb /r:system.dll,system.drawing.dll,system.windows.forms.dll`</span><span class="sxs-lookup"><span data-stu-id="449ad-120">If you are using Visual Basic, type: `vbc form1.vb /r:system.dll,system.drawing.dll,system.windows.forms.dll`</span></span>  
  
3.  <span data-ttu-id="449ad-121">Na příkazovém řádku zadejte:`Form1.exe`</span><span class="sxs-lookup"><span data-stu-id="449ad-121">At the command prompt, type: `Form1.exe`</span></span>  
  
## <a name="adding-a-control-and-handling-an-event"></a><span data-ttu-id="449ad-122">Přidání ovládacího prvku a zpracování události</span><span class="sxs-lookup"><span data-stu-id="449ad-122">Adding a Control and Handling an Event</span></span>  
 <span data-ttu-id="449ad-123">Předchozí kroky postupu ukázal, jak lze pouze vytvořit základní formuláře systému Windows, který se zkompiluje a spustí.</span><span class="sxs-lookup"><span data-stu-id="449ad-123">The previous procedure steps demonstrated how to just create a basic Windows Form that compiles and runs.</span></span> <span data-ttu-id="449ad-124">Následující postup vám ukáže, jak vytvořit a přidání ovládacího prvku formuláře a zpracovat události pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="449ad-124">The next procedure will show you how to create and add a control to the form, and handle an event for the control.</span></span> <span data-ttu-id="449ad-125">Další informace o ovládacích prvcích můžete přidat do formulářů Windows najdete v tématu [ovládacích prvků Windows Forms](../../../docs/framework/winforms/controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="449ad-125">For more information about the controls you can add to Windows Forms, see [Windows Forms Controls](../../../docs/framework/winforms/controls/index.md).</span></span>  
  
 <span data-ttu-id="449ad-126">Kromě vědět, jak vytvářet aplikace Windows Forms, byste měli vědět programování na základě událostí a jak se zpracovat vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="449ad-126">In addition to understanding how to create Windows Forms applications, you should understand event-based programming and how to handle user input.</span></span> <span data-ttu-id="449ad-127">Další informace najdete v tématu [vytváření obslužných rutin událostí v systému Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md), a [zpracování uživatelského vstupu](../../../docs/framework/winforms/controls/handling-user-input.md)</span><span class="sxs-lookup"><span data-stu-id="449ad-127">For more information, see [Creating Event Handlers in Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md), and [Handling User Input](../../../docs/framework/winforms/controls/handling-user-input.md)</span></span>  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a><span data-ttu-id="449ad-128">Deklarovat ovládacího prvku tlačítko a zpracování události jeho klikněte na</span><span class="sxs-lookup"><span data-stu-id="449ad-128">To declare a button control and handle its click event</span></span>  
  
1.  <span data-ttu-id="449ad-129">Deklarace tlačítko – ovládací prvek s názvem `button1`.</span><span class="sxs-lookup"><span data-stu-id="449ad-129">Declare a button control named `button1`.</span></span>  
  
2.  <span data-ttu-id="449ad-130">V konstruktoru, vytvořte na tlačítko a nastavit jeho <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> a <xref:System.Windows.Forms.Control.Text%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="449ad-130">In the constructor, create the button and set its <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Text%2A> properties.</span></span>  
  
3.  <span data-ttu-id="449ad-131">Přidání tlačítka do formuláře.</span><span class="sxs-lookup"><span data-stu-id="449ad-131">Add the button to the form.</span></span>  
  
     <span data-ttu-id="449ad-132">Následující příklad kódu ukazuje, jak deklarovat ovládacího prvku tlačítko.</span><span class="sxs-lookup"><span data-stu-id="449ad-132">The following code example demonstrates how to declare the button control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4.  <span data-ttu-id="449ad-133">Vytvoření metody pro zpracování <xref:System.Windows.Forms.Control.Click> události pro tlačítko.</span><span class="sxs-lookup"><span data-stu-id="449ad-133">Create a method to handle the <xref:System.Windows.Forms.Control.Click> event for the button.</span></span>  
  
5.  <span data-ttu-id="449ad-134">V obslužné rutiny události kliknutí zobrazí <xref:System.Windows.Forms.MessageBox> se zprávou "Hello World".</span><span class="sxs-lookup"><span data-stu-id="449ad-134">In the click event handler, display a <xref:System.Windows.Forms.MessageBox> with the message, "Hello World".</span></span>  
  
     <span data-ttu-id="449ad-135">Následující příklad kódu ukazuje, jak zpracovat tlačítko ovládacího prvku klikněte na události.</span><span class="sxs-lookup"><span data-stu-id="449ad-135">The following code example demonstrates how to handle the button control's click event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6.  <span data-ttu-id="449ad-136">Přidružení <xref:System.Windows.Forms.Control.Click> událostí pomocí metody, které jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="449ad-136">Associate the <xref:System.Windows.Forms.Control.Click> event with the method you created.</span></span>  
  
     <span data-ttu-id="449ad-137">Následující příklad kódu ukazuje, jak přiřadit událost metodu.</span><span class="sxs-lookup"><span data-stu-id="449ad-137">The following code example demonstrates how to associate the event with the method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7.  <span data-ttu-id="449ad-138">Zkompilování a spuštění aplikace, jak je popsáno v předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="449ad-138">Compile and run the application as described in the previous procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="449ad-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="449ad-139">Example</span></span>  
 <span data-ttu-id="449ad-140">Následující ukázka kódu je kompletní příklad z předchozích postupech.</span><span class="sxs-lookup"><span data-stu-id="449ad-140">Following code example is the complete example from the previous procedures.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="449ad-141">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="449ad-141">Compiling the Code</span></span>  
  
-   <span data-ttu-id="449ad-142">Kompilace kódu, postupujte podle pokynů v postupu budete pokračovat, které popisují, jak zkompilování a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="449ad-142">To compile the code, follow the instructions in the proceeding procedure that describe how to compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="449ad-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="449ad-143">See Also</span></span>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.Windows.Forms.Control>  
 [<span data-ttu-id="449ad-144">Změna vzhledu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="449ad-144">Changing the Appearance of Windows Forms</span></span>](../../../docs/framework/winforms/changing-the-appearance-of-windows-forms.md)  
 [<span data-ttu-id="449ad-145">Rozšiřování formulářových aplikací Windows</span><span class="sxs-lookup"><span data-stu-id="449ad-145">Enhancing Windows Forms Applications</span></span>](../../../docs/framework/winforms/advanced/index.md)  
 [<span data-ttu-id="449ad-146">Začínáme s Windows Forms</span><span class="sxs-lookup"><span data-stu-id="449ad-146">Getting Started with Windows Forms</span></span>](../../../docs/framework/winforms/getting-started-with-windows-forms.md)
