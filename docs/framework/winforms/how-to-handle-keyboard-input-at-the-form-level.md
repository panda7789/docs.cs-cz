---
title: 'Postupy: Obsluha vstupu klávesnice na úrovni formuláře'
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
ms.openlocfilehash: c10852273eeb3caea01f448e4cbef571f20769bd
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592042"
---
# <a name="how-to-handle-keyboard-input-at-the-form-level"></a><span data-ttu-id="e181c-102">Postupy: Obsluha vstupu klávesnice na úrovni formuláře</span><span class="sxs-lookup"><span data-stu-id="e181c-102">How to: Handle Keyboard Input at the Form Level</span></span>
<span data-ttu-id="e181c-103">Windows Forms poskytuje možnost zpracovávat zprávy týkající se klávesnice na úrovni formuláře před mailů ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e181c-103">Windows Forms provides the ability to handle keyboard messages at the form level, before the messages reach a control.</span></span> <span data-ttu-id="e181c-104">Toto téma ukazuje, jak tento úkol provést.</span><span class="sxs-lookup"><span data-stu-id="e181c-104">This topic shows how to accomplish this task.</span></span>  
  
### <a name="to-handle-a-keyboard-message-at-the-form-level"></a><span data-ttu-id="e181c-105">Aby se zpracovala zpráva klávesnice na úrovni formuláře</span><span class="sxs-lookup"><span data-stu-id="e181c-105">To handle a keyboard message at the form level</span></span>  
  
- <span data-ttu-id="e181c-106">Zpracování <xref:System.Windows.Forms.Control.KeyPress> nebo <xref:System.Windows.Forms.Control.KeyDown> událost úvodní formulář a nastavte <xref:System.Windows.Forms.Form.KeyPreview%2A> vlastnost formuláře `true` tak, aby klávesnice zprávy jsou přijímány formuláři dřív, než dorazí všechny ovládací prvky ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="e181c-106">Handle the <xref:System.Windows.Forms.Control.KeyPress> or <xref:System.Windows.Forms.Control.KeyDown> event of the startup form, and set the <xref:System.Windows.Forms.Form.KeyPreview%2A> property of the form to `true` so that keyboard messages are received by the form before they reach any controls on the form.</span></span> <span data-ttu-id="e181c-107">Následující kód například zpracovává <xref:System.Windows.Forms.Control.KeyPress> události zjišťuje všechny číslicemi a využívání '1', '4' a '7'.</span><span class="sxs-lookup"><span data-stu-id="e181c-107">The following code example handles the <xref:System.Windows.Forms.Control.KeyPress> event by detecting all of the number keys and consuming '1', '4', and '7'.</span></span>  
  
     [!code-cpp[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="e181c-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="e181c-108">Example</span></span>  
 <span data-ttu-id="e181c-109">Následující příklad kódu je celá aplikace výše uvedeného příkladu.</span><span class="sxs-lookup"><span data-stu-id="e181c-109">The following code example is the entire application for the above example.</span></span> <span data-ttu-id="e181c-110">Zahrnuje aplikace <xref:System.Windows.Forms.TextBox> společně s několika další ovládací prvky, které umožňují přesunout zaměření <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="e181c-110">The application includes a <xref:System.Windows.Forms.TextBox> along with several other controls that allow you to move focus from the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="e181c-111"><xref:System.Windows.Forms.Control.KeyPress> Událostí hlavním <xref:System.Windows.Forms.Form> využívá '1', '4' a '7' a <xref:System.Windows.Forms.Control.KeyPress> událost <xref:System.Windows.Forms.TextBox> využívá '2', '5' a '8' při zobrazování zbývající klíče.</span><span class="sxs-lookup"><span data-stu-id="e181c-111">The <xref:System.Windows.Forms.Control.KeyPress> event of the main <xref:System.Windows.Forms.Form> consumes '1', '4', and '7', and the <xref:System.Windows.Forms.Control.KeyPress> event of the <xref:System.Windows.Forms.TextBox> consumes '2', '5', and '8' while displaying the remaining keys.</span></span> <span data-ttu-id="e181c-112">Porovnání <xref:System.Windows.Forms.MessageBox> výstup, když stisknete klávesu chvíli počet klíčů <xref:System.Windows.Forms.TextBox> má fokus se <xref:System.Windows.Forms.MessageBox> výstup po stisknutí kláves čísel při, zaměřuje se na jeden z jiných ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="e181c-112">Compare the <xref:System.Windows.Forms.MessageBox> output when you press a number key while the <xref:System.Windows.Forms.TextBox> has focus with the <xref:System.Windows.Forms.MessageBox> output when you press a number key while focus is on one of the other controls.</span></span>  
  
 [!code-cpp[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e181c-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e181c-113">Compiling the Code</span></span>  
 <span data-ttu-id="e181c-114">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="e181c-114">This example requires:</span></span>  
  
- <span data-ttu-id="e181c-115">Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="e181c-115">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e181c-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e181c-116">See also</span></span>

- [<span data-ttu-id="e181c-117">Vstup z klávesnice v aplikaci Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e181c-117">Keyboard Input in a Windows Forms Application</span></span>](keyboard-input-in-a-windows-forms-application.md)
