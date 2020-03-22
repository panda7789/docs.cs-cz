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
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a><span data-ttu-id="2d63a-102">Postup: spuštění aplikace a její odeslání úhozů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d63a-102">How to: start an application and send it keystrokes (Visual Basic)</span></span>

<span data-ttu-id="2d63a-103">Tento příklad <xref:Microsoft.VisualBasic.Interaction.Shell%2A> používá metodu ke spuštění aplikace Poznámkový blok a potom vytiskne větu odesláním úhozů pomocí metody [My.Computer.Keyboard.SendKeys.](xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A)</span><span class="sxs-lookup"><span data-stu-id="2d63a-103">This example uses the <xref:Microsoft.VisualBasic.Interaction.Shell%2A> method to start the Notepad application and then prints a sentence by sending keystrokes using the [My.Computer.Keyboard.SendKeys](xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A) method.</span></span>

## <a name="example"></a><span data-ttu-id="2d63a-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="2d63a-104">Example</span></span>

[!code-vb[VbVbalrMyComputer#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#25)]

## <a name="robust-programming"></a><span data-ttu-id="2d63a-105">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="2d63a-105">Robust programming</span></span>

<span data-ttu-id="2d63a-106">Výjimka <xref:System.ArgumentException> je vyvolána, pokud nelze najít aplikaci s požadovaným identifikátorem procesu.</span><span class="sxs-lookup"><span data-stu-id="2d63a-106">An <xref:System.ArgumentException> exception is raised if an application with the requested process identifier cannot be found.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="2d63a-107">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2d63a-107">.NET Framework Security</span></span>

<span data-ttu-id="2d63a-108">Volání funkce `Shell` vyžaduje úplnou<xref:System.Security.SecurityException> důvěryhodnost (třída).</span><span class="sxs-lookup"><span data-stu-id="2d63a-108">The call to the `Shell` function requires full trust (<xref:System.Security.SecurityException> class).</span></span>

## <a name="see-also"></a><span data-ttu-id="2d63a-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="2d63a-109">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>
- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
