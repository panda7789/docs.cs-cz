---
title: Přístupový objekt 'Set' vlastnosti '<propertyname>' není dostupný.
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: 077533a5b1fe241b61ded9516ad8f450d7dbbf5e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400341"
---
# <a name="set-accessor-of-property-propertyname-is-not-accessible"></a><span data-ttu-id="a9bb9-102">Přístupový objekt 'Set' vlastnosti '\<propertyname>' není dostupný.</span><span class="sxs-lookup"><span data-stu-id="a9bb9-102">'Set' accessor of property '\<propertyname>' is not accessible</span></span>
<span data-ttu-id="a9bb9-103">Příkaz se pokusí uložit hodnotu vlastnosti, pokud nemá přístup k `Set` proceduře vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a9bb9-103">A statement attempts to store the value of a property when it does not have access to the property's `Set` procedure.</span></span>  
  
 <span data-ttu-id="a9bb9-104">Pokud je [příkaz set](../statements/set-statement.md) označený s více omezující úrovní přístupu, než je jeho [příkaz Property](../statements/property-statement.md), pokus o nastavení hodnoty vlastnosti může selhat v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="a9bb9-104">If the [Set Statement](../statements/set-statement.md) is marked with a more restrictive access level than its [Property Statement](../statements/property-statement.md), an attempt to set the property value could fail in the following cases:</span></span>  
  
- <span data-ttu-id="a9bb9-105">`Set`Příkaz je označen jako [Private](../modifiers/private.md) a volající kód je mimo třídu nebo strukturu, ve které je vlastnost definována.</span><span class="sxs-lookup"><span data-stu-id="a9bb9-105">The `Set` statement is marked [Private](../modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
- <span data-ttu-id="a9bb9-106">`Set`Příkaz je označen jako [Protected](../modifiers/protected.md) a volající kód není ve třídě nebo struktuře, ve které je vlastnost definována, ani v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="a9bb9-106">The `Set` statement is marked [Protected](../modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
- <span data-ttu-id="a9bb9-107">`Set`Příkaz je označen jako [Friend](../modifiers/friend.md) a volající kód není ve stejném sestavení, ve kterém je vlastnost definovaná.</span><span class="sxs-lookup"><span data-stu-id="a9bb9-107">The `Set` statement is marked [Friend](../modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="a9bb9-108">**ID chyby:** BC31102</span><span class="sxs-lookup"><span data-stu-id="a9bb9-108">**Error ID:** BC31102</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a9bb9-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="a9bb9-109">To correct this error</span></span>  
  
- <span data-ttu-id="a9bb9-110">Pokud máte kontrolu nad zdrojovým kódem, který definuje vlastnost, zvažte deklaraci `Set` procedury se stejnou úrovní přístupu jako vlastnost samotnou.</span><span class="sxs-lookup"><span data-stu-id="a9bb9-110">If you have control of the source code defining the property, consider declaring the `Set` procedure with the same access level as the property itself.</span></span>  
  
- <span data-ttu-id="a9bb9-111">Pokud nemáte kontrolu nad zdrojovým kódem, který definuje vlastnost, nebo je nutné omezit `Set` úroveň přístupu k proceduře více než samotnou vlastnost, zkuste přesunout příkaz, který nastaví hodnotu vlastnosti na oblast kódu, který má lepší přístup k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a9bb9-111">If you do not have control of the source code defining the property, or you must restrict the `Set` procedure access level more than the property itself, try to move the statement that sets the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9bb9-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="a9bb9-112">See also</span></span>

- [<span data-ttu-id="a9bb9-113">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a9bb9-113">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="a9bb9-114">Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu</span><span class="sxs-lookup"><span data-stu-id="a9bb9-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
