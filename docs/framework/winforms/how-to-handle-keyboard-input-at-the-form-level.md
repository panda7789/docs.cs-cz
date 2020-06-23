---
title: 'Postupy: Obsluha vstupu klávesnice na úrovni formuláře'
description: Naučte se, jak zpracovat vstup z klávesnice pro model Windows Forms na úrovni formuláře, než se zprávy dostanou k ovládacímu prvku.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input [Windows Forms], at form level
- Windows Forms, handling keyboard input
- keyboards [Windows Forms], form-level input
ms.assetid: d7f8b390-dc91-42d2-ae0f-2ffa388127ad
ms.openlocfilehash: 6f0695b6f665a613e0e4e001a4f9bbfc09dd45ed
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904153"
---
# <a name="how-to-handle-keyboard-input-at-the-form-level"></a><span data-ttu-id="55a49-103">Postupy: Obsluha vstupu klávesnice na úrovni formuláře</span><span class="sxs-lookup"><span data-stu-id="55a49-103">How to: Handle Keyboard Input at the Form Level</span></span>
<span data-ttu-id="55a49-104">Model Windows Forms poskytuje možnost zpracovávat zprávy klávesnice na úrovni formuláře před tím, než se zprávy dostanou k ovládacímu prvku.</span><span class="sxs-lookup"><span data-stu-id="55a49-104">Windows Forms provides the ability to handle keyboard messages at the form level, before the messages reach a control.</span></span> <span data-ttu-id="55a49-105">V tomto tématu se dozvíte, jak tento úkol provést.</span><span class="sxs-lookup"><span data-stu-id="55a49-105">This topic shows how to accomplish this task.</span></span>  
  
### <a name="to-handle-a-keyboard-message-at-the-form-level"></a><span data-ttu-id="55a49-106">Zpracování zprávy klávesnice na úrovni formuláře</span><span class="sxs-lookup"><span data-stu-id="55a49-106">To handle a keyboard message at the form level</span></span>  
  
- <span data-ttu-id="55a49-107">Zpracujte <xref:System.Windows.Forms.Control.KeyPress> událost nebo <xref:System.Windows.Forms.Control.KeyDown> formuláře po spuštění a nastavte <xref:System.Windows.Forms.Form.KeyPreview%2A> vlastnost formuláře tak, aby byla `true` zpráva klávesnicí přijímána formulářem předtím, než dosáhnou všech ovládacích prvků ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="55a49-107">Handle the <xref:System.Windows.Forms.Control.KeyPress> or <xref:System.Windows.Forms.Control.KeyDown> event of the startup form, and set the <xref:System.Windows.Forms.Form.KeyPreview%2A> property of the form to `true` so that keyboard messages are received by the form before they reach any controls on the form.</span></span> <span data-ttu-id="55a49-108">Následující příklad kódu zpracovává <xref:System.Windows.Forms.Control.KeyPress> událost tím, že detekuje všechny klíče čísel a spotřebovává "1", "4" a "7".</span><span class="sxs-lookup"><span data-stu-id="55a49-108">The following code example handles the <xref:System.Windows.Forms.Control.KeyPress> event by detecting all of the number keys and consuming '1', '4', and '7'.</span></span>  
  
     [!code-cpp[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="55a49-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="55a49-109">Example</span></span>  
 <span data-ttu-id="55a49-110">Následující příklad kódu je celá aplikace pro výše uvedený příklad.</span><span class="sxs-lookup"><span data-stu-id="55a49-110">The following code example is the entire application for the above example.</span></span> <span data-ttu-id="55a49-111">Aplikace zahrnuje <xref:System.Windows.Forms.TextBox> spolu s několika dalšími ovládacími prvky, které umožňují přesunout fokus z <xref:System.Windows.Forms.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="55a49-111">The application includes a <xref:System.Windows.Forms.TextBox> along with several other controls that allow you to move focus from the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="55a49-112"><xref:System.Windows.Forms.Control.KeyPress> <xref:System.Windows.Forms.Form> Při zobrazení zbývajících klíčů událost Main spotřebuje "1", "4" a "7" a <xref:System.Windows.Forms.Control.KeyPress> událost " <xref:System.Windows.Forms.TextBox> 2", "5" a "8".</span><span class="sxs-lookup"><span data-stu-id="55a49-112">The <xref:System.Windows.Forms.Control.KeyPress> event of the main <xref:System.Windows.Forms.Form> consumes '1', '4', and '7', and the <xref:System.Windows.Forms.Control.KeyPress> event of the <xref:System.Windows.Forms.TextBox> consumes '2', '5', and '8' while displaying the remaining keys.</span></span> <span data-ttu-id="55a49-113">Porovnejte <xref:System.Windows.Forms.MessageBox> výstup, když stisknete klávesu s číslem, zatímco při <xref:System.Windows.Forms.TextBox> stisknutí klávesy s číslem se zaměříte na <xref:System.Windows.Forms.MessageBox> výstup, zatímco se fokus nachází na jednom z dalších ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="55a49-113">Compare the <xref:System.Windows.Forms.MessageBox> output when you press a number key while the <xref:System.Windows.Forms.TextBox> has focus with the <xref:System.Windows.Forms.MessageBox> output when you press a number key while focus is on one of the other controls.</span></span>  
  
 [!code-cpp[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="55a49-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="55a49-114">Compiling the Code</span></span>  
 <span data-ttu-id="55a49-115">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="55a49-115">This example requires:</span></span>  
  
- <span data-ttu-id="55a49-116">Odkazy na sestavení System, System. Drawing a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="55a49-116">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55a49-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="55a49-117">See also</span></span>

- [<span data-ttu-id="55a49-118">Vstup z klávesnice ve formulářové aplikaci Windows</span><span class="sxs-lookup"><span data-stu-id="55a49-118">Keyboard Input in a Windows Forms Application</span></span>](keyboard-input-in-a-windows-forms-application.md)
