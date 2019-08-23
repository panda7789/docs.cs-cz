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
# <a name="how-to-determine-which-modifier-key-was-pressed"></a>Postupy: Určení modifikační klávesy, která byla stisknuta
Když vytváříte aplikaci, která přijímá klávesové úhozy uživatele, můžete také sledovat modifikační klávesy, jako jsou klávesy SHIFT, ALT a CTRL. Při stisknutí modifikační klávesy v kombinaci s jinými klíči nebo při kliknutí myší může vaše aplikace správně reagovat. Například pokud je stisknuto písmeno S, může to způsobit, že se na obrazovce zobrazí "S", ale pokud jsou stisknuty klávesy CTRL + S, aktuální dokument může být uložen. Pokud <xref:System.Windows.Forms.Control.KeyDown> událost zpracováváte <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> , vlastnost <xref:System.Windows.Forms.KeyEventArgs> přijatá obslužnou rutinou události Určuje, které modifikační klávesy jsou stisknuty. <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> Alternativně<xref:System.Windows.Forms.KeyEventArgs> vlastnost určuje znak, který byl stisknut, a všechny modifikační klávesy kombinované s bitovým operátorem OR. Nicméně Pokud zpracováváte <xref:System.Windows.Forms.Control.KeyPress> událost nebo událost myši, obslužná rutina události tyto informace neobdrží. V takovém případě je nutné použít <xref:System.Windows.Forms.Control.ModifierKeys%2A> vlastnost <xref:System.Windows.Forms.Control> třídy. V obou případech je nutné provést bitovou a odpovídající <xref:System.Windows.Forms.Keys> hodnotu a hodnotu, kterou testujete. <xref:System.Windows.Forms.Keys> Výčet nabízí variace každé modifikační klávesy, takže je důležité, abyste provedli bitové a se správnou hodnotou. Například klávesa SHIFT <xref:System.Windows.Forms.Keys.Shift>je reprezentovaná pomocí <xref:System.Windows.Forms.Keys.RShiftKey> , <xref:System.Windows.Forms.Keys.ShiftKey>a <xref:System.Windows.Forms.Keys.LShiftKey> správná hodnota pro otestování posunu jako modifikační klávesa <xref:System.Windows.Forms.Keys.Shift>. Podobně pro testování kombinací kláves CTRL a ALT jako modifikátorů byste měli použít <xref:System.Windows.Forms.Keys.Control> hodnoty a <xref:System.Windows.Forms.Keys.Alt> v uvedeném pořadí.  
  
> [!NOTE]
> Visual Basic programátoři mohou také přistupovat k klíčovým informacím <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> prostřednictvím vlastnosti.  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a>Určení, která modifikační klávesa byla stisknuta  
  
- Použijte bitový `AND` operátor <xref:System.Windows.Forms.Control.ModifierKeys%2A> s vlastností <xref:System.Windows.Forms.Keys> a hodnotou výčtu k určení, zda je stisknuta určitá modifikační klávesa. Následující příklad kódu ukazuje, jak určit, zda je stisknuta klávesa SHIFT v <xref:System.Windows.Forms.Control.KeyPress> rámci obslužné rutiny události.  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Keys>
- <xref:System.Windows.Forms.Control.ModifierKeys%2A>
- [Vstup z klávesnice v aplikaci Windows Forms](keyboard-input-in-a-windows-forms-application.md)
- [Postupy: Určete, zda je zapnutý CapsLock v Visual Basic](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9c9d1fz9(v=vs.100))
