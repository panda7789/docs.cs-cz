---
title: Přístupový objekt 'Set' vlastnosti '<propertyname>' není dostupný.
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: 1539eb1652d93402c349c65f77a3edc65b3beb57
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277560"
---
# <a name="set-accessor-of-property-propertyname-is-not-accessible"></a><span data-ttu-id="88f30-102">Nastavte přistupující objekt vlastnosti '\<propertyname >' není dostupný</span><span class="sxs-lookup"><span data-stu-id="88f30-102">'Set' accessor of property '\<propertyname>' is not accessible</span></span>
<span data-ttu-id="88f30-103">Příkaz se pokusí uložit hodnotu vlastnosti nemá přístup k vlastnosti `Set` postup.</span><span class="sxs-lookup"><span data-stu-id="88f30-103">A statement attempts to store the value of a property when it does not have access to the property's `Set` procedure.</span></span>  
  
 <span data-ttu-id="88f30-104">Pokud [nastavit příkaz](../../../visual-basic/language-reference/statements/set-statement.md) je označená pomocí více omezující přístup k úrovni než jeho [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md), pokus o nastavení hodnoty vlastností by mohlo selhat v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="88f30-104">If the [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md) is marked with a more restrictive access level than its [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md), an attempt to set the property value could fail in the following cases:</span></span>  
  
-   <span data-ttu-id="88f30-105">`Set` Označený příkaz [privátní](../../../visual-basic/language-reference/modifiers/private.md) a volající kód je mimo třídy nebo struktury, ve kterém je definována vlastnost.</span><span class="sxs-lookup"><span data-stu-id="88f30-105">The `Set` statement is marked [Private](../../../visual-basic/language-reference/modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
-   <span data-ttu-id="88f30-106">`Set` Označený příkaz [chráněné](../../../visual-basic/language-reference/modifiers/protected.md) a volající kód je v odvozené třídě, ani není v dané třídy nebo struktury, ve kterém je definována vlastnost.</span><span class="sxs-lookup"><span data-stu-id="88f30-106">The `Set` statement is marked [Protected](../../../visual-basic/language-reference/modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
-   <span data-ttu-id="88f30-107">`Set` Označený příkaz [Friend](../../../visual-basic/language-reference/modifiers/friend.md) a volající kód není ve stejném sestavení, ve kterém je definována vlastnost.</span><span class="sxs-lookup"><span data-stu-id="88f30-107">The `Set` statement is marked [Friend](../../../visual-basic/language-reference/modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="88f30-108">**ID chyby:** BC31102</span><span class="sxs-lookup"><span data-stu-id="88f30-108">**Error ID:** BC31102</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="88f30-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="88f30-109">To correct this error</span></span>  
  
-   <span data-ttu-id="88f30-110">Pokud máte kontrolu nad zdrojový kód, který definuje vlastnost, vezměte v úvahu deklaraci `Set` postup se stejnou úrovní přístupu jako samotné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="88f30-110">If you have control of the source code defining the property, consider declaring the `Set` procedure with the same access level as the property itself.</span></span>  
  
-   <span data-ttu-id="88f30-111">Pokud máte kontrolu nad zdrojový kód, který definuje vlastnost, nebo musíte omezit `Set` postup úroveň přístupu více, než se pokusí přesunout příkaz, který nastavuje hodnotu vlastnosti do oblasti kódu, který má lepší přístup k samotné, vlastnosti Vlastnost.</span><span class="sxs-lookup"><span data-stu-id="88f30-111">If you do not have control of the source code defining the property, or you must restrict the `Set` procedure access level more than the property itself, try to move the statement that sets the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88f30-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="88f30-112">See also</span></span>
- [<span data-ttu-id="88f30-113">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="88f30-113">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="88f30-114">Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu</span><span class="sxs-lookup"><span data-stu-id="88f30-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
