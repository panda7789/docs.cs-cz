---
title: Chyba automatizace
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: 8a00efe988eb39be75818b5c2c401b58e5f7f2ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54490879"
---
# <a name="automation-error"></a><span data-ttu-id="9536e-102">Chyba automatizace</span><span class="sxs-lookup"><span data-stu-id="9536e-102">Automation error</span></span>
<span data-ttu-id="9536e-103">Při provádění metody nebo získání nebo nastavení vlastnosti proměnné objektu došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="9536e-103">An error occurred while executing a method or getting or setting a property of an object variable.</span></span> <span data-ttu-id="9536e-104">Aplikace, který vytvořil objekt ohlásil chybu.</span><span class="sxs-lookup"><span data-stu-id="9536e-104">The error was reported by the application that created the object.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9536e-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="9536e-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="9536e-106">Zkontrolujte vlastnosti `Err` objektu určit zdroj a povaze chyby.</span><span class="sxs-lookup"><span data-stu-id="9536e-106">Check the properties of the `Err` object to determine the source and nature of the error.</span></span>  
  
2.  <span data-ttu-id="9536e-107">Použití `On Error Resume Next` příkaz bezprostředně před přístupem k příkazu a pak vyhledejte chyby ihned po přístupu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="9536e-107">Use the `On Error Resume Next` statement immediately before the accessing statement, and then check for errors immediately after the accessing statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9536e-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9536e-108">See also</span></span>
- [<span data-ttu-id="9536e-109">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="9536e-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="9536e-110">Kontaktujte nás</span><span class="sxs-lookup"><span data-stu-id="9536e-110">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
