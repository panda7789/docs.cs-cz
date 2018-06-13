---
title: Chyba automatizace
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: fdd77510d03cd9e5228be1ba9ec9f746dcc0dfe4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583874"
---
# <a name="automation-error"></a><span data-ttu-id="d6518-102">Chyba automatizace</span><span class="sxs-lookup"><span data-stu-id="d6518-102">Automation error</span></span>
<span data-ttu-id="d6518-103">Došlo k chybě při spuštění metody nebo získání nebo nastavení vlastností proměnné objektu.</span><span class="sxs-lookup"><span data-stu-id="d6518-103">An error occurred while executing a method or getting or setting a property of an object variable.</span></span> <span data-ttu-id="d6518-104">Chyba byla hlášena aplikace, která vytvoří objekt.</span><span class="sxs-lookup"><span data-stu-id="d6518-104">The error was reported by the application that created the object.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d6518-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="d6518-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="d6518-106">Zkontrolujte vlastnosti `Err` objektem pro určení zdroj a povaze chyby.</span><span class="sxs-lookup"><span data-stu-id="d6518-106">Check the properties of the `Err` object to determine the source and nature of the error.</span></span>  
  
2.  <span data-ttu-id="d6518-107">Použití `On Error Resume Next` bezprostředně před přístupem příkaz a potom vyhledejte chyby okamžitě po příkazu přístupem.</span><span class="sxs-lookup"><span data-stu-id="d6518-107">Use the `On Error Resume Next` statement immediately before the accessing statement, and then check for errors immediately after the accessing statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6518-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6518-108">See Also</span></span>  
 [<span data-ttu-id="d6518-109">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="d6518-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="d6518-110">Kontaktujte nás</span><span class="sxs-lookup"><span data-stu-id="d6518-110">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
