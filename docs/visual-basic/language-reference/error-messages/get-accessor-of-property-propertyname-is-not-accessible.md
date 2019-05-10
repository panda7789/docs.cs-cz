---
title: Přístupový objekt 'Get' vlastnosti '<propertyname>' není dostupný.
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: 92cc6d732b59617a6043bd71a9549649ff1ad356
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662047"
---
# <a name="get-accessor-of-property-propertyname-is-not-accessible"></a><span data-ttu-id="dda4e-102">Získat přistupující objekt vlastnosti '\<propertyname >' není dostupný</span><span class="sxs-lookup"><span data-stu-id="dda4e-102">'Get' accessor of property '\<propertyname>' is not accessible</span></span>
<span data-ttu-id="dda4e-103">Příkaz se pokusí načíst hodnotu vlastnosti, pokud nemá přístup k vlastnosti `Get` postup.</span><span class="sxs-lookup"><span data-stu-id="dda4e-103">A statement attempts to retrieve the value of a property when it does not have access to the property's `Get` procedure.</span></span>  
  
 <span data-ttu-id="dda4e-104">Pokud [získat příkaz](../../../visual-basic/language-reference/statements/get-statement.md) je označená pomocí více omezující přístup k úrovni než jeho [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md), pokus o čtení hodnoty vlastnosti by mohlo selhat v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="dda4e-104">If the [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md) is marked with a more restrictive access level than its [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md), an attempt to read the property value could fail in the following cases:</span></span>  
  
- <span data-ttu-id="dda4e-105">`Get` Označený příkaz [privátní](../../../visual-basic/language-reference/modifiers/private.md) a volající kód je mimo třídy nebo struktury, ve kterém je definována vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dda4e-105">The `Get` statement is marked [Private](../../../visual-basic/language-reference/modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
- <span data-ttu-id="dda4e-106">`Get` Označený příkaz [chráněné](../../../visual-basic/language-reference/modifiers/protected.md) a volající kód je v odvozené třídě, ani není v dané třídy nebo struktury, ve kterém je definována vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dda4e-106">The `Get` statement is marked [Protected](../../../visual-basic/language-reference/modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
- <span data-ttu-id="dda4e-107">`Get` Označený příkaz [Friend](../../../visual-basic/language-reference/modifiers/friend.md) a volající kód není ve stejném sestavení, ve kterém je definována vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dda4e-107">The `Get` statement is marked [Friend](../../../visual-basic/language-reference/modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="dda4e-108">**ID chyby:** BC31103</span><span class="sxs-lookup"><span data-stu-id="dda4e-108">**Error ID:** BC31103</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="dda4e-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="dda4e-109">To correct this error</span></span>  
  
- <span data-ttu-id="dda4e-110">Pokud máte kontrolu nad zdrojový kód, který definuje vlastnost, vezměte v úvahu deklaraci `Get` postup se stejnou úrovní přístupu jako samotné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dda4e-110">If you have control of the source code defining the property, consider declaring the `Get` procedure with the same access level as the property itself.</span></span>  
  
- <span data-ttu-id="dda4e-111">Pokud máte kontrolu nad zdrojový kód, který definuje vlastnost, nebo musíte omezit `Get` postup úroveň přístupu více, než se pokusí přesunout příkaz, který čte hodnoty vlastnosti do oblasti kódu, který má lepší přístup k samotné, vlastnosti Vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dda4e-111">If you do not have control of the source code defining the property, or you must restrict the `Get` procedure access level more than the property itself, try to move the statement that reads the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dda4e-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dda4e-112">See also</span></span>

- [<span data-ttu-id="dda4e-113">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="dda4e-113">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="dda4e-114">Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu</span><span class="sxs-lookup"><span data-stu-id="dda4e-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
