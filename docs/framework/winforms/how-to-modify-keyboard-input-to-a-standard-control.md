---
title: "Postupy: Úprava vstupu klávesnice do standardního ovládacího prvku"
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
- keyboard input [Windows Forms], modifying
- modifying keyboard input
- Windows Forms, modifying keyboard input
- keyboards [Windows Forms], keyboard input
ms.assetid: 626d3712-d866-4988-bcda-a2d5b36ec0ba
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2c95ba3ef1c590f5c7e5d5e89ed05cf28c7829d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-keyboard-input-to-a-standard-control"></a><span data-ttu-id="92d24-102">Postupy: Úprava vstupu klávesnice do standardního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="92d24-102">How to: Modify Keyboard Input to a Standard Control</span></span>
<span data-ttu-id="92d24-103">Windows Forms poskytuje možnost využívat a úprava vstupu klávesnice.</span><span class="sxs-lookup"><span data-stu-id="92d24-103">Windows Forms provides the ability to consume and modify keyboard input.</span></span> <span data-ttu-id="92d24-104">Využívání klíč odkazuje na zpracování klíč v rámci obslužnou rutinu metoda nebo událost, aby jiné metody a události, které dolů fronty zpráv neobdrží hodnota klíče.</span><span class="sxs-lookup"><span data-stu-id="92d24-104">Consuming a key refers to handling a key within a method or event handler so that other methods and events further down the message queue do not receive the key value.</span></span> <span data-ttu-id="92d24-105">Úprava klíč odkazuje na změnou hodnoty klíče, aby metody a obslužné rutiny událostí další dolů fronty zpráv s jinou hodnotou klíče.</span><span class="sxs-lookup"><span data-stu-id="92d24-105">Modifying a key refers to modifying the value of a key so that methods and event handlers further down the message queue receive a different key value.</span></span> <span data-ttu-id="92d24-106">Toto téma ukazuje, jak k těmto úkolům.</span><span class="sxs-lookup"><span data-stu-id="92d24-106">This topic shows how to accomplish these tasks.</span></span>  
  
### <a name="to-consume-a-key"></a><span data-ttu-id="92d24-107">Používat klíč</span><span class="sxs-lookup"><span data-stu-id="92d24-107">To consume a key</span></span>  
  
-   <span data-ttu-id="92d24-108">V <xref:System.Windows.Forms.Control.KeyPress> nastavit popisovač události <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> vlastnost <xref:System.Windows.Forms.KeyPressEventArgs> třídy k `true`.</span><span class="sxs-lookup"><span data-stu-id="92d24-108">In a <xref:System.Windows.Forms.Control.KeyPress> event handler, set the <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> class to `true`.</span></span>  
  
     <span data-ttu-id="92d24-109">-nebo-</span><span class="sxs-lookup"><span data-stu-id="92d24-109">-or-</span></span>  
  
     <span data-ttu-id="92d24-110">V <xref:System.Windows.Forms.Control.KeyDown> nastavit popisovač události <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> vlastnost <xref:System.Windows.Forms.KeyEventArgs> třídy k `true`.</span><span class="sxs-lookup"><span data-stu-id="92d24-110">In a <xref:System.Windows.Forms.Control.KeyDown> event handler, set the <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyEventArgs> class to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="92d24-111">Nastavení <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> vlastnost <xref:System.Windows.Forms.Control.KeyDown> obslužné rutiny události nezabrání <xref:System.Windows.Forms.Control.KeyPress> a <xref:System.Windows.Forms.Control.KeyUp> vyvolána pro aktuální klávesu.</span><span class="sxs-lookup"><span data-stu-id="92d24-111">Setting the <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> property in the <xref:System.Windows.Forms.Control.KeyDown> event handler does not prevent the <xref:System.Windows.Forms.Control.KeyPress> and <xref:System.Windows.Forms.Control.KeyUp> events from being raised for the current keystroke.</span></span> <span data-ttu-id="92d24-112">Použití <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> vlastnost pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="92d24-112">Use the <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> property for this purpose.</span></span>  
  
     <span data-ttu-id="92d24-113">Následující příklad je výňatek ze `switch` příkaz, který ověřuje, zda <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> vlastnost <xref:System.Windows.Forms.KeyPressEventArgs> přijatých <xref:System.Windows.Forms.Control.KeyPress> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="92d24-113">The following example is an excerpt from a `switch` statement that examines the <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> received by a <xref:System.Windows.Forms.Control.KeyPress> event handler.</span></span> <span data-ttu-id="92d24-114">Tento kód spotřebuje "A" a "a" znak klíče.</span><span class="sxs-lookup"><span data-stu-id="92d24-114">This code consumes the 'A' and 'a' character keys.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#6)]  
  
### <a name="to-modify-a-standard-character-key"></a><span data-ttu-id="92d24-115">Chcete-li upravit klíč standardní znak</span><span class="sxs-lookup"><span data-stu-id="92d24-115">To modify a standard character key</span></span>  
  
-   <span data-ttu-id="92d24-116">V <xref:System.Windows.Forms.Control.KeyPress> nastavit popisovač události <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> vlastnost <xref:System.Windows.Forms.KeyPressEventArgs> třídu na hodnotu nový klíč znak.</span><span class="sxs-lookup"><span data-stu-id="92d24-116">In a <xref:System.Windows.Forms.Control.KeyPress> event handler, set the <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> class to the value of the new character key.</span></span>  
  
     <span data-ttu-id="92d24-117">Následující příklad je výňatek ze `switch` příkaz, který upravuje "B" na "A" a "b" na "a".</span><span class="sxs-lookup"><span data-stu-id="92d24-117">The following example is an excerpt from a `switch` statement that modifies 'B' to 'A' and 'b' to 'a'.</span></span> <span data-ttu-id="92d24-118">Všimněte si, že <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> vlastnost <xref:System.Windows.Forms.KeyPressEventArgs> parametr je nastaven na `false`tak, aby nová hodnota klíče se rozšíří do jiné metody a událostí ve frontě zpráv.</span><span class="sxs-lookup"><span data-stu-id="92d24-118">Note that the <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> parameter is set to `false`, so that the new key value is propagated to other methods and events in the message queue.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#7)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#7)]  
  
### <a name="to-modify-a-noncharacter-key"></a><span data-ttu-id="92d24-119">Chcete-li upravit noncharacter klíč</span><span class="sxs-lookup"><span data-stu-id="92d24-119">To modify a noncharacter key</span></span>  
  
-   <span data-ttu-id="92d24-120">Přepsání <xref:System.Windows.Forms.Control> metoda, která zpracuje zprávy Windows zjistit WM_KEYDOWN nebo WM_SYSKEYDOWN zprávu a nastavte <xref:System.Windows.Forms.Message.WParam%2A> vlastnost <xref:System.Windows.Forms.Message> parametru <xref:System.Windows.Forms.Keys> hodnotu, která představuje nový noncharacter klíč.</span><span class="sxs-lookup"><span data-stu-id="92d24-120">Override a <xref:System.Windows.Forms.Control> method that processes Windows messages, detect the WM_KEYDOWN or WM_SYSKEYDOWN message, and set the <xref:System.Windows.Forms.Message.WParam%2A> property of the <xref:System.Windows.Forms.Message> parameter to the <xref:System.Windows.Forms.Keys> value that represents the new noncharacter key.</span></span>  
  
     <span data-ttu-id="92d24-121">Následující příklad kódu ukazuje, jak lze přepsat <xref:System.Windows.Forms.Control.PreProcessMessage%2A> metoda ovládacího prvku ke zjištění klávesy F1 až F9 a upravit F3 stisknutí klávesy F1.</span><span class="sxs-lookup"><span data-stu-id="92d24-121">The following code example demonstrates how to override the <xref:System.Windows.Forms.Control.PreProcessMessage%2A> method of a control to detect keys F1 through F9 and modify any F3 key press to F1.</span></span> <span data-ttu-id="92d24-122">Další informace o <xref:System.Windows.Forms.Control> metody, které můžete přepsat zachytávat zprávy klávesnice, najdete v části [uživatelský vstup ve formulářové aplikaci Windows](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md) a [jak funguje vstup klávesnice](../../../docs/framework/winforms/how-keyboard-input-works.md).</span><span class="sxs-lookup"><span data-stu-id="92d24-122">For more information on <xref:System.Windows.Forms.Control> methods that you can override to intercept keyboard messages, see [User Input in a Windows Forms Application](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md) and [How Keyboard Input Works](../../../docs/framework/winforms/how-keyboard-input-works.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#12](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#12](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="92d24-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="92d24-123">Example</span></span>  
 <span data-ttu-id="92d24-124">Následující příklad kódu je úplná žádost o příklady kódu v předchozích částech.</span><span class="sxs-lookup"><span data-stu-id="92d24-124">The following code example is the complete application for the code examples in the previous sections.</span></span> <span data-ttu-id="92d24-125">Aplikace používá vlastní ovládací prvek odvozen od <xref:System.Windows.Forms.TextBox> třída spotřebovat a úprava vstupu klávesnice.</span><span class="sxs-lookup"><span data-stu-id="92d24-125">The application uses a custom control derived from the <xref:System.Windows.Forms.TextBox> class to consume and modify keyboard input.</span></span>  
  
 [!code-csharp[System.Windows.Forms.KeyBoardInput#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInput#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="92d24-126">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="92d24-126">Compiling the Code</span></span>  
 <span data-ttu-id="92d24-127">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="92d24-127">This example requires:</span></span>  
  
-   <span data-ttu-id="92d24-128">Odkazy na systém, System.Drawing a System.Windows.Forms sestavení.</span><span class="sxs-lookup"><span data-stu-id="92d24-128">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="92d24-129">Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="92d24-129">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="92d24-130">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="92d24-130">You can also build this example in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="92d24-131">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="92d24-131">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92d24-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="92d24-132">See Also</span></span>  
 [<span data-ttu-id="92d24-133">Vstup z klávesnice ve Windows Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="92d24-133">Keyboard Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [<span data-ttu-id="92d24-134">Uživatelský vstup ve Windows Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="92d24-134">User Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md)  
 [<span data-ttu-id="92d24-135">Jak funguje vstup z klávesnice</span><span class="sxs-lookup"><span data-stu-id="92d24-135">How Keyboard Input Works</span></span>](../../../docs/framework/winforms/how-keyboard-input-works.md)
