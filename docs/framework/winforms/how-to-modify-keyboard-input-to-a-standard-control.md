---
title: 'Postupy: Úprava vstupu klávesnice do standardního ovládacího prvku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyboard input [Windows Forms], modifying
- modifying keyboard input
- Windows Forms, modifying keyboard input
- keyboards [Windows Forms], keyboard input
ms.assetid: 626d3712-d866-4988-bcda-a2d5b36ec0ba
ms.openlocfilehash: 81d33234670fb8ae5445cc86a79f5c3b6a647a03
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225778"
---
# <a name="how-to-modify-keyboard-input-to-a-standard-control"></a><span data-ttu-id="4492a-102">Postupy: Úprava vstupu klávesnice do standardního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="4492a-102">How to: Modify Keyboard Input to a Standard Control</span></span>
<span data-ttu-id="4492a-103">Windows Forms poskytuje možnost využívat a úprava vstupu klávesnice.</span><span class="sxs-lookup"><span data-stu-id="4492a-103">Windows Forms provides the ability to consume and modify keyboard input.</span></span> <span data-ttu-id="4492a-104">Využívání klíč odkazuje na zpracování klíč v rámci obslužnou rutinu metody nebo události tak, aby jiné metody a události, které dolů fronty zpráv neobdrží hodnotu klíče.</span><span class="sxs-lookup"><span data-stu-id="4492a-104">Consuming a key refers to handling a key within a method or event handler so that other methods and events further down the message queue do not receive the key value.</span></span> <span data-ttu-id="4492a-105">Úprava klíč odkazuje na úpravy hodnoty vlastnosti klíč tak, aby metody a obslužné rutiny událostí další dolů fronty zpráv dostávat na jinou hodnotu klíče.</span><span class="sxs-lookup"><span data-stu-id="4492a-105">Modifying a key refers to modifying the value of a key so that methods and event handlers further down the message queue receive a different key value.</span></span> <span data-ttu-id="4492a-106">Toto téma ukazuje, jak provádět tyto úlohy.</span><span class="sxs-lookup"><span data-stu-id="4492a-106">This topic shows how to accomplish these tasks.</span></span>  
  
### <a name="to-consume-a-key"></a><span data-ttu-id="4492a-107">Používat klíče</span><span class="sxs-lookup"><span data-stu-id="4492a-107">To consume a key</span></span>  
  
-   <span data-ttu-id="4492a-108">V <xref:System.Windows.Forms.Control.KeyPress> nastavena obslužná rutina události, <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> vlastnost <xref:System.Windows.Forms.KeyPressEventArgs> třídu `true`.</span><span class="sxs-lookup"><span data-stu-id="4492a-108">In a <xref:System.Windows.Forms.Control.KeyPress> event handler, set the <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> class to `true`.</span></span>  
  
     <span data-ttu-id="4492a-109">-nebo-</span><span class="sxs-lookup"><span data-stu-id="4492a-109">-or-</span></span>  
  
     <span data-ttu-id="4492a-110">V <xref:System.Windows.Forms.Control.KeyDown> nastavena obslužná rutina události, <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> vlastnost <xref:System.Windows.Forms.KeyEventArgs> třídu `true`.</span><span class="sxs-lookup"><span data-stu-id="4492a-110">In a <xref:System.Windows.Forms.Control.KeyDown> event handler, set the <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyEventArgs> class to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4492a-111">Nastavení <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> vlastnost <xref:System.Windows.Forms.Control.KeyDown> obslužná rutina události byste nezabránili <xref:System.Windows.Forms.Control.KeyPress> a <xref:System.Windows.Forms.Control.KeyUp> událostí vyvolaných pro aktuální stisknutí klávesy.</span><span class="sxs-lookup"><span data-stu-id="4492a-111">Setting the <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> property in the <xref:System.Windows.Forms.Control.KeyDown> event handler does not prevent the <xref:System.Windows.Forms.Control.KeyPress> and <xref:System.Windows.Forms.Control.KeyUp> events from being raised for the current keystroke.</span></span> <span data-ttu-id="4492a-112">Použití <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> vlastnost pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="4492a-112">Use the <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> property for this purpose.</span></span>  
  
     <span data-ttu-id="4492a-113">Následující příklad je výpisem z `switch` příkaz, který prověří <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> vlastnost <xref:System.Windows.Forms.KeyPressEventArgs> přijatých <xref:System.Windows.Forms.Control.KeyPress> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="4492a-113">The following example is an excerpt from a `switch` statement that examines the <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> received by a <xref:System.Windows.Forms.Control.KeyPress> event handler.</span></span> <span data-ttu-id="4492a-114">Tento kód využívá "A" a "a" klávesy znaku.</span><span class="sxs-lookup"><span data-stu-id="4492a-114">This code consumes the 'A' and 'a' character keys.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#6)]  
  
### <a name="to-modify-a-standard-character-key"></a><span data-ttu-id="4492a-115">Chcete-li změnit klíč standardnímu znaku</span><span class="sxs-lookup"><span data-stu-id="4492a-115">To modify a standard character key</span></span>  
  
-   <span data-ttu-id="4492a-116">V <xref:System.Windows.Forms.Control.KeyPress> nastavena obslužná rutina události, <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> vlastnost <xref:System.Windows.Forms.KeyPressEventArgs> třídy k hodnotě nový klíč znak.</span><span class="sxs-lookup"><span data-stu-id="4492a-116">In a <xref:System.Windows.Forms.Control.KeyPress> event handler, set the <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> class to the value of the new character key.</span></span>  
  
     <span data-ttu-id="4492a-117">Následující příklad je výpisem z `switch` příkaz, který upravuje "B" do "A" a "b" do "a".</span><span class="sxs-lookup"><span data-stu-id="4492a-117">The following example is an excerpt from a `switch` statement that modifies 'B' to 'A' and 'b' to 'a'.</span></span> <span data-ttu-id="4492a-118">Všimněte si, že <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> vlastnost <xref:System.Windows.Forms.KeyPressEventArgs> parametr je nastaven na `false`, aby se nová hodnota klíče je postoupena do jiné metody a události do fronty zpráv.</span><span class="sxs-lookup"><span data-stu-id="4492a-118">Note that the <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> parameter is set to `false`, so that the new key value is propagated to other methods and events in the message queue.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#7)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#7)]  
  
### <a name="to-modify-a-noncharacter-key"></a><span data-ttu-id="4492a-119">Chcete-li změnit neznakové klávesy</span><span class="sxs-lookup"><span data-stu-id="4492a-119">To modify a noncharacter key</span></span>  
  
-   <span data-ttu-id="4492a-120">Přepsat <xref:System.Windows.Forms.Control> metodu, která zpracovává zprávy Windows detekovat zpráva WM_KEYDOWN nebo WM_SYSKEYDOWN a nastavit <xref:System.Windows.Forms.Message.WParam%2A> vlastnost <xref:System.Windows.Forms.Message> parametr <xref:System.Windows.Forms.Keys> hodnotu, která představuje nový neznakové klíč.</span><span class="sxs-lookup"><span data-stu-id="4492a-120">Override a <xref:System.Windows.Forms.Control> method that processes Windows messages, detect the WM_KEYDOWN or WM_SYSKEYDOWN message, and set the <xref:System.Windows.Forms.Message.WParam%2A> property of the <xref:System.Windows.Forms.Message> parameter to the <xref:System.Windows.Forms.Keys> value that represents the new noncharacter key.</span></span>  
  
     <span data-ttu-id="4492a-121">Následující příklad kódu ukazuje, jak přepsat <xref:System.Windows.Forms.Control.PreProcessMessage%2A> metoda ovládacího prvku na detekci klávesy F1 až F9 a upravit F3 stisknutí klávesy F1.</span><span class="sxs-lookup"><span data-stu-id="4492a-121">The following code example demonstrates how to override the <xref:System.Windows.Forms.Control.PreProcessMessage%2A> method of a control to detect keys F1 through F9 and modify any F3 key press to F1.</span></span> <span data-ttu-id="4492a-122">Další informace o <xref:System.Windows.Forms.Control> metody, které můžete přepsat, aby se zachytily zprávy týkající se klávesnice, naleznete v tématu [uživatelský vstup ve formulářové aplikaci Windows](user-input-in-a-windows-forms-application.md) a [jak funguje vstup klávesnice](how-keyboard-input-works.md).</span><span class="sxs-lookup"><span data-stu-id="4492a-122">For more information on <xref:System.Windows.Forms.Control> methods that you can override to intercept keyboard messages, see [User Input in a Windows Forms Application](user-input-in-a-windows-forms-application.md) and [How Keyboard Input Works](how-keyboard-input-works.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="4492a-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="4492a-123">Example</span></span>  
 <span data-ttu-id="4492a-124">Následující příklad kódu je je aplikace dokončena a příklady kódu v předchozích částech.</span><span class="sxs-lookup"><span data-stu-id="4492a-124">The following code example is the complete application for the code examples in the previous sections.</span></span> <span data-ttu-id="4492a-125">Aplikace používá vlastní ovládací prvek odvozen od <xref:System.Windows.Forms.TextBox> třídy využívat a úprava vstupu klávesnice.</span><span class="sxs-lookup"><span data-stu-id="4492a-125">The application uses a custom control derived from the <xref:System.Windows.Forms.TextBox> class to consume and modify keyboard input.</span></span>  
  
 [!code-csharp[System.Windows.Forms.KeyBoardInput#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInput#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4492a-126">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="4492a-126">Compiling the Code</span></span>  
 <span data-ttu-id="4492a-127">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="4492a-127">This example requires:</span></span>  
  
-   <span data-ttu-id="4492a-128">Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="4492a-128">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="4492a-129">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="4492a-129">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="4492a-130">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="4492a-130">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4492a-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4492a-131">See also</span></span>

- [<span data-ttu-id="4492a-132">Vstup z klávesnice ve formulářové aplikaci Windows</span><span class="sxs-lookup"><span data-stu-id="4492a-132">Keyboard Input in a Windows Forms Application</span></span>](keyboard-input-in-a-windows-forms-application.md)
- [<span data-ttu-id="4492a-133">Uživatelský vstup v aplikaci Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4492a-133">User Input in a Windows Forms Application</span></span>](user-input-in-a-windows-forms-application.md)
- [<span data-ttu-id="4492a-134">Jak funguje vstup z klávesnice</span><span class="sxs-lookup"><span data-stu-id="4492a-134">How Keyboard Input Works</span></span>](how-keyboard-input-works.md)
