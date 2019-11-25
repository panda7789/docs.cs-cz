---
title: Chyba automatizace
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: df153167bc8c73a2d3760c8d7db30dccfa468e35
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976152"
---
# <a name="automation-error"></a><span data-ttu-id="6ba7e-102">Chyba automatizace</span><span class="sxs-lookup"><span data-stu-id="6ba7e-102">Automation error</span></span>

<span data-ttu-id="6ba7e-103">Při provádění metody nebo při získávání nebo nastavování vlastnosti proměnné objektu došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="6ba7e-103">An error occurred while executing a method or getting or setting a property of an object variable.</span></span> <span data-ttu-id="6ba7e-104">Aplikace ohlásila chybu, která vytvořila objekt.</span><span class="sxs-lookup"><span data-stu-id="6ba7e-104">The error was reported by the application that created the object.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6ba7e-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="6ba7e-105">To correct this error</span></span>  
  
1. <span data-ttu-id="6ba7e-106">Zkontrolujte vlastnosti objektu `Err` a určete zdroj a povahu chyby.</span><span class="sxs-lookup"><span data-stu-id="6ba7e-106">Check the properties of the `Err` object to determine the source and nature of the error.</span></span>  
  
2. <span data-ttu-id="6ba7e-107">Použijte příkaz `On Error Resume Next` bezprostředně před příkaz k přístupu a potom zkontrolujte chyby ihned po příkazu k přístupu.</span><span class="sxs-lookup"><span data-stu-id="6ba7e-107">Use the `On Error Resume Next` statement immediately before the accessing statement, and then check for errors immediately after the accessing statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ba7e-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6ba7e-108">See also</span></span>

- [<span data-ttu-id="6ba7e-109">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="6ba7e-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="6ba7e-110">Kontaktujte nás</span><span class="sxs-lookup"><span data-stu-id="6ba7e-110">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
