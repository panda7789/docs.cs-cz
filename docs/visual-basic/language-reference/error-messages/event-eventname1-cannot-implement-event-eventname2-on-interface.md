---
title: "Událost & č. 39; &lt;eventname1&gt;& č. 39; nelze implementovat, události & č. 39;&lt; eventname2&gt;& č. 39; na rozhraní & č. 39;&lt; rozhraní&gt;& č. 39; protože jejich typy delegáta & č. 39;&lt; delegate1&gt;& č. 39; a & č. 39;&lt; delegate2&gt;& č. 39; neshodují"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords: BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b0fcbbf8a6e23270e4dcbf9d813c773e1522a92a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="event-39lteventname1gt39-cannot-implement-event-39lteventname2gt39-on-interface-39ltinterfacegt39-because-their-delegate-types-39ltdelegate1gt39-and-39ltdelegate2gt39-do-not-match"></a><span data-ttu-id="409c1-102">Událost & č. 39; &lt;eventname1&gt;& č. 39; nelze implementovat, události & č. 39;&lt; eventname2&gt;& č. 39; na rozhraní & č. 39;&lt; rozhraní&gt;& č. 39; protože jejich typy delegáta & č. 39;&lt; delegate1&gt;& č. 39; a & č. 39;&lt; delegate2&gt;& č. 39; neshodují</span><span class="sxs-lookup"><span data-stu-id="409c1-102">Event &#39;&lt;eventname1&gt;&#39; cannot implement event &#39;&lt;eventname2&gt;&#39; on interface &#39;&lt;interface&gt;&#39; because their delegate types &#39;&lt;delegate1&gt;&#39; and &#39;&lt;delegate2&gt;&#39; do not match</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="409c1-103">událost nelze implementovat, protože typ delegáta události neodpovídá typu delegáta události v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="409c1-103"> cannot implement an event because the delegate type of the event does not match the delegate type of the event in the interface.</span></span> <span data-ttu-id="409c1-104">Této chybě může dojít, když definovat více událostí v rozhraní a pak pokus o jejich implementaci společně s stejnou událost.</span><span class="sxs-lookup"><span data-stu-id="409c1-104">This error can occur when you define multiple events in an interface and then attempt to implement them together with the same event.</span></span> <span data-ttu-id="409c1-105">Událost můžete implementovat dvě nebo více událostí pouze v případě, že všechny implementována události jsou deklarováno s použitím `As` syntaxe a specifikují stejný typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="409c1-105">An event can implement two or more events only if all implemented events are declared using the `As` syntax and specify the same delegate type.</span></span>  
  
 <span data-ttu-id="409c1-106">**ID chyby:** BC31423</span><span class="sxs-lookup"><span data-stu-id="409c1-106">**Error ID:** BC31423</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="409c1-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="409c1-107">To correct this error</span></span>  
  
-   <span data-ttu-id="409c1-108">Implementujte události samostatně.</span><span class="sxs-lookup"><span data-stu-id="409c1-108">Implement the events separately.</span></span>  
  
     <span data-ttu-id="409c1-109">—nebo—</span><span class="sxs-lookup"><span data-stu-id="409c1-109">—or—</span></span>  
  
-   <span data-ttu-id="409c1-110">Definování události v rozhraní pomocí `As` syntaxe a specifikují stejný typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="409c1-110">Define the events in the interface using the `As` syntax and specify the same delegate type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="409c1-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="409c1-111">See Also</span></span>  
 [<span data-ttu-id="409c1-112">Event – příkaz</span><span class="sxs-lookup"><span data-stu-id="409c1-112">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="409c1-113">Delegate – příkaz</span><span class="sxs-lookup"><span data-stu-id="409c1-113">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="409c1-114">Události</span><span class="sxs-lookup"><span data-stu-id="409c1-114">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
