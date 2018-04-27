---
title: 'Postupy: Obsluha vstupu klávesnice na úrovni formuláře'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input [Windows Forms], at form level
- Windows Forms, handling keyboard input
- keyboards [Windows Forms], form-level input
ms.assetid: d7f8b390-dc91-42d2-ae0f-2ffa388127ad
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 21fd7549c0d5000bac2b7a2d92d203855912d9eb
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-handle-keyboard-input-at-the-form-level"></a><span data-ttu-id="7b412-102">Postupy: Obsluha vstupu klávesnice na úrovni formuláře</span><span class="sxs-lookup"><span data-stu-id="7b412-102">How to: Handle Keyboard Input at the Form Level</span></span>
<span data-ttu-id="7b412-103">Windows Forms poskytuje možnost pro zpracování zprávy klávesnice na úrovni formuláře před zprávy dosáhnout ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7b412-103">Windows Forms provides the ability to handle keyboard messages at the form level, before the messages reach a control.</span></span> <span data-ttu-id="7b412-104">Toto téma ukazuje, jak k provedení této úlohy.</span><span class="sxs-lookup"><span data-stu-id="7b412-104">This topic shows how to accomplish this task.</span></span>  
  
### <a name="to-handle-a-keyboard-message-at-the-form-level"></a><span data-ttu-id="7b412-105">Zpracování zpráv klávesnice na úrovni formuláře</span><span class="sxs-lookup"><span data-stu-id="7b412-105">To handle a keyboard message at the form level</span></span>  
  
-   <span data-ttu-id="7b412-106">Zpracování <xref:System.Windows.Forms.Control.KeyPress> nebo <xref:System.Windows.Forms.Control.KeyDown> události formulář spuštění a nastavte <xref:System.Windows.Forms.Form.KeyPreview%2A> vlastnost formuláře `true` tak, aby přijímá zprávy klávesnice formuláře než dosáhnou všechny ovládací prvky na formuláři.</span><span class="sxs-lookup"><span data-stu-id="7b412-106">Handle the <xref:System.Windows.Forms.Control.KeyPress> or <xref:System.Windows.Forms.Control.KeyDown> event of the startup form, and set the <xref:System.Windows.Forms.Form.KeyPreview%2A> property of the form to `true` so that keyboard messages are received by the form before they reach any controls on the form.</span></span> <span data-ttu-id="7b412-107">Následující kód například zpracovává <xref:System.Windows.Forms.Control.KeyPress> událostí zjišťuje všechny číslicemi a využívání '1', '4' a '7'.</span><span class="sxs-lookup"><span data-stu-id="7b412-107">The following code example handles the <xref:System.Windows.Forms.Control.KeyPress> event by detecting all of the number keys and consuming '1', '4', and '7'.</span></span>  
  
     [!code-cpp[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="7b412-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="7b412-108">Example</span></span>  
 <span data-ttu-id="7b412-109">Následující příklad kódu se bude celá aplikace pro výše uvedeném příkladu.</span><span class="sxs-lookup"><span data-stu-id="7b412-109">The following code example is the entire application for the above example.</span></span> <span data-ttu-id="7b412-110">Zahrnuje aplikace <xref:System.Windows.Forms.TextBox> společně s několik dalších ovládacích prvků, které umožňují přesunout fokus z <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="7b412-110">The application includes a <xref:System.Windows.Forms.TextBox> along with several other controls that allow you to move focus from the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="7b412-111"><xref:System.Windows.Forms.Control.KeyPress> Událostí hlavních <xref:System.Windows.Forms.Form> využívá '1', '4' a '7' a <xref:System.Windows.Forms.Control.KeyPress> události <xref:System.Windows.Forms.TextBox> využívá '2', '5' a '8' při zobrazování zbývající klíče.</span><span class="sxs-lookup"><span data-stu-id="7b412-111">The <xref:System.Windows.Forms.Control.KeyPress> event of the main <xref:System.Windows.Forms.Form> consumes '1', '4', and '7', and the <xref:System.Windows.Forms.Control.KeyPress> event of the <xref:System.Windows.Forms.TextBox> consumes '2', '5', and '8' while displaying the remaining keys.</span></span> <span data-ttu-id="7b412-112">Porovnání <xref:System.Windows.Forms.MessageBox> výstup po stisknutí klávesy číslo klíče chvíli <xref:System.Windows.Forms.TextBox> má právě fokus s <xref:System.Windows.Forms.MessageBox> výstup po stisknutí kláves číslo při zaměřuje se na některý z dalších ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="7b412-112">Compare the <xref:System.Windows.Forms.MessageBox> output when you press a number key while the <xref:System.Windows.Forms.TextBox> has focus with the <xref:System.Windows.Forms.MessageBox> output when you press a number key while focus is on one of the other controls.</span></span>  
  
 [!code-cpp[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7b412-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7b412-113">Compiling the Code</span></span>  
 <span data-ttu-id="7b412-114">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="7b412-114">This example requires:</span></span>  
  
-   <span data-ttu-id="7b412-115">Odkazy na systém, System.Drawing a System.Windows.Forms sestavení.</span><span class="sxs-lookup"><span data-stu-id="7b412-115">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="7b412-116">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="7b412-116">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="7b412-117">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="7b412-117">You can also build this example in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="7b412-118">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="7b412-118">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b412-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b412-119">See Also</span></span>  
 [<span data-ttu-id="7b412-120">Vstup z klávesnice v aplikaci Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7b412-120">Keyboard Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)
