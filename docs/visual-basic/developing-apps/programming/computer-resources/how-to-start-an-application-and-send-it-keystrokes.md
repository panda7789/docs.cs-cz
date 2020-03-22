---
title: 'Postup: spuštění aplikace a její odeslání Úhozů - Visual Basic'
ms.date: 10/23/2019
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
ms.openlocfilehash: 033999c07bb5839a264122b2ca330916bdf844b8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "72919394"
---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a>Postup: spuštění aplikace a její odeslání úhozů (Visual Basic)

Tento příklad <xref:Microsoft.VisualBasic.Interaction.Shell%2A> používá metodu ke spuštění aplikace Poznámkový blok a potom vytiskne větu odesláním úhozů pomocí metody [My.Computer.Keyboard.SendKeys.](xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A)

## <a name="example"></a>Příklad

[!code-vb[VbVbalrMyComputer#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#25)]

## <a name="robust-programming"></a>Robustní programování

Výjimka <xref:System.ArgumentException> je vyvolána, pokud nelze najít aplikaci s požadovaným identifikátorem procesu.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework

Volání funkce `Shell` vyžaduje úplnou<xref:System.Security.SecurityException> důvěryhodnost (třída).

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>
- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
