---
title: 'Postupy: Spusťte aplikaci a odeslat stisknutí kláves (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
ms.openlocfilehash: 9519fd85177d5d2adf97b54652c19330954edadf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976388"
---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a>Postupy: Spusťte aplikaci a odeslat stisknutí kláves (Visual Basic)
Tento příklad používá `Shell` funkce a spusťte tak aplikaci kalkulačky a pak zasláním klávesových úhozů pomocí součin dvou čísel `My.Computer.Keyboard.SendKeys` metody.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrMyComputer#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#25)]  
  
## <a name="robust-programming"></a>Robustní programování  
 A <xref:System.ArgumentException> je vyvolána výjimka, pokud aplikace s požadovaným identifikátorem procesu nebyl nalezen.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Volání `Shell` funkce vyžaduje úplný vztah důvěryhodnosti (<xref:System.Security.SecurityException> třídy).  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>
- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
