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
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a><span data-ttu-id="5e891-102">Postupy: Spuštění aplikace a zasílání informací o stisknutých klávesách do aplikace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e891-102">How to: Start an Application and Send it Keystrokes (Visual Basic)</span></span>
<span data-ttu-id="5e891-103">Tento příklad používá `Shell` funkci, aby se spustit program Kalkulačka aplikaci a potom dvou čísel vynásobí odesílání stisknutí kláves pomocí `My.Computer.Keyboard.SendKeys` metoda.</span><span class="sxs-lookup"><span data-stu-id="5e891-103">This example uses the `Shell` function to start the calculator application and then multiplies two numbers by sending keystrokes using the `My.Computer.Keyboard.SendKeys` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e891-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="5e891-104">Example</span></span>  
 [!code-vb[VbVbalrMyComputer#25](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-start-an-application-and-send-it-keystrokes_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="5e891-105">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="5e891-105">Robust Programming</span></span>  
 <span data-ttu-id="5e891-106">A <xref:System.ArgumentException> je vyvolána výjimka, pokud aplikace s požadovaným identifikátorem procesu nelze nalézt.</span><span class="sxs-lookup"><span data-stu-id="5e891-106">A <xref:System.ArgumentException> exception is raised if an application with the requested process identifier cannot be found.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="5e891-107">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5e891-107">.NET Framework Security</span></span>  
 <span data-ttu-id="5e891-108">Volání `Shell` funkce vyžaduje úplný vztah důvěryhodnosti (<xref:System.Security.SecurityException> třídy).</span><span class="sxs-lookup"><span data-stu-id="5e891-108">The call to the `Shell` function requires full trust (<xref:System.Security.SecurityException> class).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e891-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="5e891-109">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>  
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>  
 <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
