---
title: 'Postupy: spuštění aplikace a odeslání klávesových úhozů – Visual Basic'
ms.date: 10/23/2019
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
ms.openlocfilehash: 033999c07bb5839a264122b2ca330916bdf844b8
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919394"
---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a>Postupy: spuštění aplikace a odeslání klávesových úhozů (Visual Basic)

Tento příklad používá metodu <xref:Microsoft.VisualBasic.Interaction.Shell%2A> ke spuštění aplikace v programu Poznámkový blok a pak vytiskne větu odesláním stisknutí kláves pomocí metody [My. Computer. Keyboard. SendKeys](xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A) .

## <a name="example"></a>Příklad

[!code-vb[VbVbalrMyComputer#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#25)]

## <a name="robust-programming"></a>Robustní programování

Pokud se aplikace s požadovaným identifikátorem procesu nenajde, vyvolá se výjimka <xref:System.ArgumentException>.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework

Volání funkce `Shell` vyžaduje úplný vztah důvěryhodnosti (<xref:System.Security.SecurityException> třídy).

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>
- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
