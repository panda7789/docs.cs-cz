---
title: Chyba automatizace
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: 8370f744b916ce4a797c808ed58c5fc9580e6278
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304308"
---
# <a name="automation-error"></a><span data-ttu-id="40f26-102">Chyba automatizace</span><span class="sxs-lookup"><span data-stu-id="40f26-102">Automation error</span></span>
<span data-ttu-id="40f26-103">Při provádění metody nebo získání nebo nastavení vlastnosti proměnné objektu došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="40f26-103">An error occurred while executing a method or getting or setting a property of an object variable.</span></span> <span data-ttu-id="40f26-104">Aplikace, který vytvořil objekt ohlásil chybu.</span><span class="sxs-lookup"><span data-stu-id="40f26-104">The error was reported by the application that created the object.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="40f26-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="40f26-105">To correct this error</span></span>  
  
1. <span data-ttu-id="40f26-106">Zkontrolujte vlastnosti `Err` objektu určit zdroj a povaze chyby.</span><span class="sxs-lookup"><span data-stu-id="40f26-106">Check the properties of the `Err` object to determine the source and nature of the error.</span></span>  
  
2. <span data-ttu-id="40f26-107">Použití `On Error Resume Next` příkaz bezprostředně před přístupem k příkazu a pak vyhledejte chyby ihned po přístupu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="40f26-107">Use the `On Error Resume Next` statement immediately before the accessing statement, and then check for errors immediately after the accessing statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40f26-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40f26-108">See also</span></span>

- [<span data-ttu-id="40f26-109">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="40f26-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="40f26-110">Kontaktujte nás</span><span class="sxs-lookup"><span data-stu-id="40f26-110">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
