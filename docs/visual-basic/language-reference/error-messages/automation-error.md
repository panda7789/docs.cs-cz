---
title: Chyba automatizace
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: 8370f744b916ce4a797c808ed58c5fc9580e6278
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935288"
---
# <a name="automation-error"></a><span data-ttu-id="db196-102">Chyba automatizace</span><span class="sxs-lookup"><span data-stu-id="db196-102">Automation error</span></span>
<span data-ttu-id="db196-103">Při provádění metody nebo získání nebo nastavení vlastnosti proměnné objektu došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="db196-103">An error occurred while executing a method or getting or setting a property of an object variable.</span></span> <span data-ttu-id="db196-104">Aplikace, který vytvořil objekt ohlásil chybu.</span><span class="sxs-lookup"><span data-stu-id="db196-104">The error was reported by the application that created the object.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="db196-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="db196-105">To correct this error</span></span>  
  
1. <span data-ttu-id="db196-106">Zkontrolujte vlastnosti `Err` objektu určit zdroj a povaze chyby.</span><span class="sxs-lookup"><span data-stu-id="db196-106">Check the properties of the `Err` object to determine the source and nature of the error.</span></span>  
  
2. <span data-ttu-id="db196-107">Použití `On Error Resume Next` příkaz bezprostředně před přístupem k příkazu a pak vyhledejte chyby ihned po přístupu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="db196-107">Use the `On Error Resume Next` statement immediately before the accessing statement, and then check for errors immediately after the accessing statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db196-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db196-108">See also</span></span>

- [<span data-ttu-id="db196-109">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="db196-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="db196-110">Kontaktujte nás</span><span class="sxs-lookup"><span data-stu-id="db196-110">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
