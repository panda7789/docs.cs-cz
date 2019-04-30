---
title: 'Postupy: Určení modifikační klávesy, která byla stisknuta'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input
- shift keys
- events [Windows Forms], mouse
- Keys.ControlKey enumeration member
- keys [Windows Forms], control keys
- user input [Windows Forms], checking for keyboard
- keys [Windows Forms], determining last pressed
- keys [Windows Forms], shift keys
- keys [Windows Forms], modifier keys
- control keys
- keys [Windows Forms], alt keys
- alt keys
- Keys.Shift enumeration member
- events [Windows Forms], keyboard
- keyboards [Windows Forms], keyboard input
- Keys.Alt enumeration member
- modifier keys
ms.assetid: 1e184048-0ae3-4067-a200-d4ba31dbc2cb
ms.openlocfilehash: 571af49cdf82b876cfb72a7c7636874c8d155fb7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803139"
---
# <a name="how-to-determine-which-modifier-key-was-pressed"></a><span data-ttu-id="eef4c-102">Postupy: Určení modifikační klávesy, která byla stisknuta</span><span class="sxs-lookup"><span data-stu-id="eef4c-102">How to: Determine Which Modifier Key Was Pressed</span></span>
<span data-ttu-id="eef4c-103">Když vytvoříte aplikaci, která přijímá stisknutí kláves uživatele, můžete také sledovat modifikační klávesy, jako je například klávesy SHIFT, ALT a CTRL.</span><span class="sxs-lookup"><span data-stu-id="eef4c-103">When you create an application that accepts the user's keystrokes, you may also want to monitor for modifier keys such as the SHIFT, ALT, and CTRL keys.</span></span> <span data-ttu-id="eef4c-104">Při stisknutí modifikační klávesa v kombinaci s další klíče nebo pomocí kliknutí myší, může vaše aplikace reagovat odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="eef4c-104">When a modifier key is pressed in combination with other keys, or with mouse clicks, your application can respond appropriately.</span></span> <span data-ttu-id="eef4c-105">Například pokud se stiskne písmeno S, to může způsobit jednoduše "s" se zobrazí na obrazovce, ale pokud stisknutí kláves CTRL + S, může být aktuální dokument uložen.</span><span class="sxs-lookup"><span data-stu-id="eef4c-105">For example, if the letter S is pressed, this may simply cause an "s" to appear on the screen, but if the keys CTRL+S are pressed, the current document may be saved.</span></span> <span data-ttu-id="eef4c-106">Pokud zpracováváte <xref:System.Windows.Forms.Control.KeyDown> událostí, <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> vlastnost <xref:System.Windows.Forms.KeyEventArgs> přijatá událost obslužné rutiny Určuje, která modifikátor stisknutí kláves.</span><span class="sxs-lookup"><span data-stu-id="eef4c-106">If you handle the <xref:System.Windows.Forms.Control.KeyDown> event, the <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> property of the <xref:System.Windows.Forms.KeyEventArgs> received by the event handler specifies which modifier keys are pressed.</span></span> <span data-ttu-id="eef4c-107">Další možností <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> vlastnost <xref:System.Windows.Forms.KeyEventArgs> Určuje znak, která byla stisknuta stejně jako jakékoli modifikační klávesy, v kombinaci s bitový operátor OR.</span><span class="sxs-lookup"><span data-stu-id="eef4c-107">Alternatively, the <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> property of <xref:System.Windows.Forms.KeyEventArgs> specifies the character that was pressed as well as any modifier keys combined with a bitwise OR.</span></span> <span data-ttu-id="eef4c-108">Nicméně pokud obsluhujete <xref:System.Windows.Forms.Control.KeyPress> událost nebo událost myši, obslužná rutina události neobdrží tyto informace.</span><span class="sxs-lookup"><span data-stu-id="eef4c-108">However, if you are handling the <xref:System.Windows.Forms.Control.KeyPress> event or a mouse event, the event handler does not receive this information.</span></span> <span data-ttu-id="eef4c-109">V takovém případě musíte použít <xref:System.Windows.Forms.Control.ModifierKeys%2A> vlastnost <xref:System.Windows.Forms.Control> třídy.</span><span class="sxs-lookup"><span data-stu-id="eef4c-109">In this case, you must use the <xref:System.Windows.Forms.Control.ModifierKeys%2A> property of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="eef4c-110">V obou případech je nutné provést bitový operátor AND příslušné <xref:System.Windows.Forms.Keys> hodnoty a hodnoty, které testujete.</span><span class="sxs-lookup"><span data-stu-id="eef4c-110">In either case, you must perform a bitwise AND of the appropriate <xref:System.Windows.Forms.Keys> value and the value you are testing.</span></span> <span data-ttu-id="eef4c-111"><xref:System.Windows.Forms.Keys> Výčet nabízí varianty každého modifikační klávesa, takže je důležité, abyste provedli bitový a správnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="eef4c-111">The <xref:System.Windows.Forms.Keys> enumeration offers variations of each modifier key, so it is important that you perform the bitwise AND with the correct value.</span></span> <span data-ttu-id="eef4c-112">Například je reprezentována klávesu SHIFT <xref:System.Windows.Forms.Keys.Shift>, <xref:System.Windows.Forms.Keys.ShiftKey>, <xref:System.Windows.Forms.Keys.RShiftKey> a <xref:System.Windows.Forms.Keys.LShiftKey> správnou hodnotu pro testování SHIFT je modifikační klávesa <xref:System.Windows.Forms.Keys.Shift>.</span><span class="sxs-lookup"><span data-stu-id="eef4c-112">For example, the SHIFT key is represented by <xref:System.Windows.Forms.Keys.Shift>, <xref:System.Windows.Forms.Keys.ShiftKey>, <xref:System.Windows.Forms.Keys.RShiftKey> and <xref:System.Windows.Forms.Keys.LShiftKey> The correct value to test SHIFT as a modifier key is <xref:System.Windows.Forms.Keys.Shift>.</span></span> <span data-ttu-id="eef4c-113">Obdobně test pro CTRL a ALT jako modifikátory jste měli by používat <xref:System.Windows.Forms.Keys.Control> a <xref:System.Windows.Forms.Keys.Alt> hodnoty v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="eef4c-113">Similarly, to test for CTRL and ALT as modifiers you should use the <xref:System.Windows.Forms.Keys.Control> and <xref:System.Windows.Forms.Keys.Alt> values, respectively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eef4c-114">Programátoři v jazyce Visual Basic se dostanete také informace o klíči prostřednictvím <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> vlastnost</span><span class="sxs-lookup"><span data-stu-id="eef4c-114">Visual Basic programmers can also access key information through the <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> property</span></span>  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a><span data-ttu-id="eef4c-115">K určení modifikační klávesy, která byla stisknuta</span><span class="sxs-lookup"><span data-stu-id="eef4c-115">To determine which modifier key was pressed</span></span>  
  
- <span data-ttu-id="eef4c-116">Použít bitový `AND` operátor s <xref:System.Windows.Forms.Control.ModifierKeys%2A> vlastnosti a hodnotu <xref:System.Windows.Forms.Keys> výčet k určení, zda je konkrétní modifikační klávesa stisknuta.</span><span class="sxs-lookup"><span data-stu-id="eef4c-116">Use the bitwise `AND` operator with the <xref:System.Windows.Forms.Control.ModifierKeys%2A> property and a value of the <xref:System.Windows.Forms.Keys> enumeration to determine whether a particular modifier key is pressed.</span></span> <span data-ttu-id="eef4c-117">Následující příklad kódu ukazuje, jak určit, zda je klávesa SHIFT stisknuta v rámci <xref:System.Windows.Forms.Control.KeyPress> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="eef4c-117">The following code example shows how to determine whether the SHIFT key is pressed within a <xref:System.Windows.Forms.Control.KeyPress> event handler.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="eef4c-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eef4c-118">See also</span></span>

- <xref:System.Windows.Forms.Keys>
- <xref:System.Windows.Forms.Control.ModifierKeys%2A>
- [<span data-ttu-id="eef4c-119">Vstup z klávesnice v aplikaci Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eef4c-119">Keyboard Input in a Windows Forms Application</span></span>](keyboard-input-in-a-windows-forms-application.md)
- <span data-ttu-id="eef4c-120">[Postupy: Určení, že CapsLock – Pokud je v jazyce Visual Basic](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9c9d1fz9(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="eef4c-120">[How to: Determine If CapsLock is On in Visual Basic](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9c9d1fz9(v=vs.100))</span></span>
