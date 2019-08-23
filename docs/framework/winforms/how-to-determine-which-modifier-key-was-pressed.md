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
ms.openlocfilehash: 37fa897f5a2e1c65cbd5db9189f1500e3427c920
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964316"
---
# <a name="how-to-determine-which-modifier-key-was-pressed"></a><span data-ttu-id="7e1c8-102">Postupy: Určení modifikační klávesy, která byla stisknuta</span><span class="sxs-lookup"><span data-stu-id="7e1c8-102">How to: Determine Which Modifier Key Was Pressed</span></span>
<span data-ttu-id="7e1c8-103">Když vytváříte aplikaci, která přijímá klávesové úhozy uživatele, můžete také sledovat modifikační klávesy, jako jsou klávesy SHIFT, ALT a CTRL.</span><span class="sxs-lookup"><span data-stu-id="7e1c8-103">When you create an application that accepts the user's keystrokes, you may also want to monitor for modifier keys such as the SHIFT, ALT, and CTRL keys.</span></span> <span data-ttu-id="7e1c8-104">Při stisknutí modifikační klávesy v kombinaci s jinými klíči nebo při kliknutí myší může vaše aplikace správně reagovat.</span><span class="sxs-lookup"><span data-stu-id="7e1c8-104">When a modifier key is pressed in combination with other keys, or with mouse clicks, your application can respond appropriately.</span></span> <span data-ttu-id="7e1c8-105">Například pokud je stisknuto písmeno S, může to způsobit, že se na obrazovce zobrazí "S", ale pokud jsou stisknuty klávesy CTRL + S, aktuální dokument může být uložen.</span><span class="sxs-lookup"><span data-stu-id="7e1c8-105">For example, if the letter S is pressed, this may simply cause an "s" to appear on the screen, but if the keys CTRL+S are pressed, the current document may be saved.</span></span> <span data-ttu-id="7e1c8-106">Pokud <xref:System.Windows.Forms.Control.KeyDown> událost zpracováváte <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> , vlastnost <xref:System.Windows.Forms.KeyEventArgs> přijatá obslužnou rutinou události Určuje, které modifikační klávesy jsou stisknuty.</span><span class="sxs-lookup"><span data-stu-id="7e1c8-106">If you handle the <xref:System.Windows.Forms.Control.KeyDown> event, the <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> property of the <xref:System.Windows.Forms.KeyEventArgs> received by the event handler specifies which modifier keys are pressed.</span></span> <span data-ttu-id="7e1c8-107"><xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> Alternativně<xref:System.Windows.Forms.KeyEventArgs> vlastnost určuje znak, který byl stisknut, a všechny modifikační klávesy kombinované s bitovým operátorem OR.</span><span class="sxs-lookup"><span data-stu-id="7e1c8-107">Alternatively, the <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> property of <xref:System.Windows.Forms.KeyEventArgs> specifies the character that was pressed as well as any modifier keys combined with a bitwise OR.</span></span> <span data-ttu-id="7e1c8-108">Nicméně Pokud zpracováváte <xref:System.Windows.Forms.Control.KeyPress> událost nebo událost myši, obslužná rutina události tyto informace neobdrží.</span><span class="sxs-lookup"><span data-stu-id="7e1c8-108">However, if you are handling the <xref:System.Windows.Forms.Control.KeyPress> event or a mouse event, the event handler does not receive this information.</span></span> <span data-ttu-id="7e1c8-109">V takovém případě je nutné použít <xref:System.Windows.Forms.Control.ModifierKeys%2A> vlastnost <xref:System.Windows.Forms.Control> třídy.</span><span class="sxs-lookup"><span data-stu-id="7e1c8-109">In this case, you must use the <xref:System.Windows.Forms.Control.ModifierKeys%2A> property of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="7e1c8-110">V obou případech je nutné provést bitovou a odpovídající <xref:System.Windows.Forms.Keys> hodnotu a hodnotu, kterou testujete.</span><span class="sxs-lookup"><span data-stu-id="7e1c8-110">In either case, you must perform a bitwise AND of the appropriate <xref:System.Windows.Forms.Keys> value and the value you are testing.</span></span> <span data-ttu-id="7e1c8-111"><xref:System.Windows.Forms.Keys> Výčet nabízí variace každé modifikační klávesy, takže je důležité, abyste provedli bitové a se správnou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="7e1c8-111">The <xref:System.Windows.Forms.Keys> enumeration offers variations of each modifier key, so it is important that you perform the bitwise AND with the correct value.</span></span> <span data-ttu-id="7e1c8-112">Například klávesa SHIFT <xref:System.Windows.Forms.Keys.Shift>je reprezentovaná pomocí <xref:System.Windows.Forms.Keys.RShiftKey> , <xref:System.Windows.Forms.Keys.ShiftKey>a <xref:System.Windows.Forms.Keys.LShiftKey> správná hodnota pro otestování posunu jako modifikační klávesa <xref:System.Windows.Forms.Keys.Shift>.</span><span class="sxs-lookup"><span data-stu-id="7e1c8-112">For example, the SHIFT key is represented by <xref:System.Windows.Forms.Keys.Shift>, <xref:System.Windows.Forms.Keys.ShiftKey>, <xref:System.Windows.Forms.Keys.RShiftKey> and <xref:System.Windows.Forms.Keys.LShiftKey> The correct value to test SHIFT as a modifier key is <xref:System.Windows.Forms.Keys.Shift>.</span></span> <span data-ttu-id="7e1c8-113">Podobně pro testování kombinací kláves CTRL a ALT jako modifikátorů byste měli použít <xref:System.Windows.Forms.Keys.Control> hodnoty a <xref:System.Windows.Forms.Keys.Alt> v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="7e1c8-113">Similarly, to test for CTRL and ALT as modifiers you should use the <xref:System.Windows.Forms.Keys.Control> and <xref:System.Windows.Forms.Keys.Alt> values, respectively.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7e1c8-114">Visual Basic programátoři mohou také přistupovat k klíčovým informacím <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> prostřednictvím vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7e1c8-114">Visual Basic programmers can also access key information through the <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> property</span></span>  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a><span data-ttu-id="7e1c8-115">Určení, která modifikační klávesa byla stisknuta</span><span class="sxs-lookup"><span data-stu-id="7e1c8-115">To determine which modifier key was pressed</span></span>  
  
- <span data-ttu-id="7e1c8-116">Použijte bitový `AND` operátor <xref:System.Windows.Forms.Control.ModifierKeys%2A> s vlastností <xref:System.Windows.Forms.Keys> a hodnotou výčtu k určení, zda je stisknuta určitá modifikační klávesa.</span><span class="sxs-lookup"><span data-stu-id="7e1c8-116">Use the bitwise `AND` operator with the <xref:System.Windows.Forms.Control.ModifierKeys%2A> property and a value of the <xref:System.Windows.Forms.Keys> enumeration to determine whether a particular modifier key is pressed.</span></span> <span data-ttu-id="7e1c8-117">Následující příklad kódu ukazuje, jak určit, zda je stisknuta klávesa SHIFT v <xref:System.Windows.Forms.Control.KeyPress> rámci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="7e1c8-117">The following code example shows how to determine whether the SHIFT key is pressed within a <xref:System.Windows.Forms.Control.KeyPress> event handler.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="7e1c8-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7e1c8-118">See also</span></span>

- <xref:System.Windows.Forms.Keys>
- <xref:System.Windows.Forms.Control.ModifierKeys%2A>
- [<span data-ttu-id="7e1c8-119">Vstup z klávesnice v aplikaci Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7e1c8-119">Keyboard Input in a Windows Forms Application</span></span>](keyboard-input-in-a-windows-forms-application.md)
- <span data-ttu-id="7e1c8-120">[Postupy: Určete, zda je zapnutý CapsLock v Visual Basic](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9c9d1fz9(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7e1c8-120">[How to: Determine If CapsLock is On in Visual Basic](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9c9d1fz9(v=vs.100))</span></span>
