---
title: 'Postupy: Spuštění aplikace a zasílání informací o stisknutých klávesách do aplikace (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
ms.openlocfilehash: 716c88153ad01c7b225f31948c8aaaa2694dc512
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582145"
---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a><span data-ttu-id="e9a60-102">Postupy: Spuštění aplikace a zasílání informací o stisknutých klávesách do aplikace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9a60-102">How to: Start an Application and Send it Keystrokes (Visual Basic)</span></span>
<span data-ttu-id="e9a60-103">Tento příklad používá `Shell` funkci, aby se spustit program Kalkulačka aplikaci a potom dvou čísel vynásobí odesílání stisknutí kláves pomocí `My.Computer.Keyboard.SendKeys` metoda.</span><span class="sxs-lookup"><span data-stu-id="e9a60-103">This example uses the `Shell` function to start the calculator application and then multiplies two numbers by sending keystrokes using the `My.Computer.Keyboard.SendKeys` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9a60-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e9a60-104">Example</span></span>  
 [!code-vb[VbVbalrMyComputer#25](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-start-an-application-and-send-it-keystrokes_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="e9a60-105">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="e9a60-105">Robust Programming</span></span>  
 <span data-ttu-id="e9a60-106">A <xref:System.ArgumentException> je vyvolána výjimka, pokud aplikace s požadovaným identifikátorem procesu nelze nalézt.</span><span class="sxs-lookup"><span data-stu-id="e9a60-106">A <xref:System.ArgumentException> exception is raised if an application with the requested process identifier cannot be found.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="e9a60-107">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e9a60-107">.NET Framework Security</span></span>  
 <span data-ttu-id="e9a60-108">Volání `Shell` funkce vyžaduje úplný vztah důvěryhodnosti (<xref:System.Security.SecurityException> třídy).</span><span class="sxs-lookup"><span data-stu-id="e9a60-108">The call to the `Shell` function requires full trust (<xref:System.Security.SecurityException> class).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9a60-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9a60-109">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>  
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>  
 <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
