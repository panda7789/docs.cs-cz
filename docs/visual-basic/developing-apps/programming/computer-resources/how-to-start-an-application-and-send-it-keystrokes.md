---
title: "Postupy: Spuštění aplikace a zasílání informací o stisknutých klávesách do aplikace (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8bf92a74bc1b60ea3213d80e4df373936c65d89e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a>Postupy: Spuštění aplikace a zasílání informací o stisknutých klávesách do aplikace (Visual Basic)
Tento příklad používá `Shell` funkci, aby se spustit program Kalkulačka aplikaci a potom dvou čísel vynásobí odesílání stisknutí kláves pomocí `My.Computer.Keyboard.SendKeys` metoda.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrMyComputer#25](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-start-an-application-and-send-it-keystrokes_1.vb)]  
  
## <a name="robust-programming"></a>Robustní programování  
 A <xref:System.ArgumentException> je vyvolána výjimka, pokud aplikace s požadovaným identifikátorem procesu nelze nalézt.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Volání `Shell` funkce vyžaduje úplný vztah důvěryhodnosti (<xref:System.Security.SecurityException> třídy).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>  
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>  
 <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
