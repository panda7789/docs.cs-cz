---
title: Přístupový objekt 'Get' vlastnosti '<propertyname>' není dostupný.
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: cb953671e624d5b9170aa0b3a9dd80c7ba8337e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402911"
---
# <a name="get-accessor-of-property-propertyname-is-not-accessible"></a><span data-ttu-id="180ff-102">Přístupový objekt 'Get' vlastnosti '\<propertyname>' není dostupný.</span><span class="sxs-lookup"><span data-stu-id="180ff-102">'Get' accessor of property '\<propertyname>' is not accessible</span></span>
<span data-ttu-id="180ff-103">Příkaz se pokusí načíst hodnotu vlastnosti, pokud nemá přístup k `Get` proceduře vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="180ff-103">A statement attempts to retrieve the value of a property when it does not have access to the property's `Get` procedure.</span></span>  
  
 <span data-ttu-id="180ff-104">Pokud je [příkaz Get](../statements/get-statement.md) označen s více omezující úrovní přístupu, než je jeho [příkaz Property](../statements/property-statement.md), pokus o čtení hodnoty vlastnosti může selhat v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="180ff-104">If the [Get Statement](../statements/get-statement.md) is marked with a more restrictive access level than its [Property Statement](../statements/property-statement.md), an attempt to read the property value could fail in the following cases:</span></span>  
  
- <span data-ttu-id="180ff-105">`Get`Příkaz je označen jako [Private](../modifiers/private.md) a volající kód je mimo třídu nebo strukturu, ve které je vlastnost definována.</span><span class="sxs-lookup"><span data-stu-id="180ff-105">The `Get` statement is marked [Private](../modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
- <span data-ttu-id="180ff-106">`Get`Příkaz je označen jako [Protected](../modifiers/protected.md) a volající kód není ve třídě nebo struktuře, ve které je vlastnost definována, ani v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="180ff-106">The `Get` statement is marked [Protected](../modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
- <span data-ttu-id="180ff-107">`Get`Příkaz je označen jako [Friend](../modifiers/friend.md) a volající kód není ve stejném sestavení, ve kterém je vlastnost definovaná.</span><span class="sxs-lookup"><span data-stu-id="180ff-107">The `Get` statement is marked [Friend](../modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="180ff-108">**ID chyby:** BC31103</span><span class="sxs-lookup"><span data-stu-id="180ff-108">**Error ID:** BC31103</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="180ff-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="180ff-109">To correct this error</span></span>  
  
- <span data-ttu-id="180ff-110">Pokud máte kontrolu nad zdrojovým kódem, který definuje vlastnost, zvažte deklaraci `Get` procedury se stejnou úrovní přístupu jako vlastnost samotnou.</span><span class="sxs-lookup"><span data-stu-id="180ff-110">If you have control of the source code defining the property, consider declaring the `Get` procedure with the same access level as the property itself.</span></span>  
  
- <span data-ttu-id="180ff-111">Pokud nemáte kontrolu nad zdrojovým kódem, který definuje vlastnost, nebo je nutné omezit `Get` úroveň přístupu k proceduře více než samotnou vlastnost, zkuste přesunout příkaz, který přečte hodnotu vlastnosti, do oblasti kódu, která má lepší přístup k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="180ff-111">If you do not have control of the source code defining the property, or you must restrict the `Get` procedure access level more than the property itself, try to move the statement that reads the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="180ff-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="180ff-112">See also</span></span>

- [<span data-ttu-id="180ff-113">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="180ff-113">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="180ff-114">Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu</span><span class="sxs-lookup"><span data-stu-id="180ff-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
