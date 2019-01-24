---
title: '&#39;Nastavte&#39; přistupující objekt vlastnosti &#39; &lt;propertyname&gt; &#39; není dostupný'
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: a543506b06742f3ee9101edbac962e761ddd531d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606566"
---
# <a name="39set39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a><span data-ttu-id="b2f18-102">&#39;Nastavte&#39; přistupující objekt vlastnosti &#39; &lt;propertyname&gt; &#39; není dostupný</span><span class="sxs-lookup"><span data-stu-id="b2f18-102">&#39;Set&#39; accessor of property &#39;&lt;propertyname&gt;&#39; is not accessible</span></span>
<span data-ttu-id="b2f18-103">Příkaz se pokusí uložit hodnotu vlastnosti nemá přístup k vlastnosti `Set` postup.</span><span class="sxs-lookup"><span data-stu-id="b2f18-103">A statement attempts to store the value of a property when it does not have access to the property's `Set` procedure.</span></span>  
  
 <span data-ttu-id="b2f18-104">Pokud [nastavit příkaz](../../../visual-basic/language-reference/statements/set-statement.md) je označená pomocí více omezující přístup k úrovni než jeho [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md), pokus o nastavení hodnoty vlastností by mohlo selhat v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="b2f18-104">If the [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md) is marked with a more restrictive access level than its [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md), an attempt to set the property value could fail in the following cases:</span></span>  
  
-   <span data-ttu-id="b2f18-105">`Set` Označený příkaz [privátní](../../../visual-basic/language-reference/modifiers/private.md) a volající kód je mimo třídy nebo struktury, ve kterém je definována vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b2f18-105">The `Set` statement is marked [Private](../../../visual-basic/language-reference/modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
-   <span data-ttu-id="b2f18-106">`Set` Označený příkaz [chráněné](../../../visual-basic/language-reference/modifiers/protected.md) a volající kód je v odvozené třídě, ani není v dané třídy nebo struktury, ve kterém je definována vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b2f18-106">The `Set` statement is marked [Protected](../../../visual-basic/language-reference/modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
-   <span data-ttu-id="b2f18-107">`Set` Označený příkaz [Friend](../../../visual-basic/language-reference/modifiers/friend.md) a volající kód není ve stejném sestavení, ve kterém je definována vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b2f18-107">The `Set` statement is marked [Friend](../../../visual-basic/language-reference/modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="b2f18-108">**ID chyby:** BC31102</span><span class="sxs-lookup"><span data-stu-id="b2f18-108">**Error ID:** BC31102</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b2f18-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="b2f18-109">To correct this error</span></span>  
  
-   <span data-ttu-id="b2f18-110">Pokud máte kontrolu nad zdrojový kód, který definuje vlastnost, vezměte v úvahu deklaraci `Set` postup se stejnou úrovní přístupu jako samotné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b2f18-110">If you have control of the source code defining the property, consider declaring the `Set` procedure with the same access level as the property itself.</span></span>  
  
-   <span data-ttu-id="b2f18-111">Pokud máte kontrolu nad zdrojový kód, který definuje vlastnost, nebo musíte omezit `Set` postup úroveň přístupu více, než se pokusí přesunout příkaz, který nastavuje hodnotu vlastnosti do oblasti kódu, který má lepší přístup k samotné, vlastnosti Vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b2f18-111">If you do not have control of the source code defining the property, or you must restrict the `Set` procedure access level more than the property itself, try to move the statement that sets the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2f18-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b2f18-112">See also</span></span>
- [<span data-ttu-id="b2f18-113">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b2f18-113">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="b2f18-114">Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu</span><span class="sxs-lookup"><span data-stu-id="b2f18-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
