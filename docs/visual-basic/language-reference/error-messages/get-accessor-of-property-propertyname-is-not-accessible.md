---
title: "& č. 39; Get & č. 39; přistupující objekt vlastnosti & č. 39; &lt;propertyname&gt;& č. 39; není dostupný"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 167e040570af1fc78ce48f5e930e54981ba909ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="39get39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a><span data-ttu-id="a2809-102">& č. 39; Get & č. 39; přistupující objekt vlastnosti & č. 39; &lt;propertyname&gt;& č. 39; není dostupný</span><span class="sxs-lookup"><span data-stu-id="a2809-102">&#39;Get&#39; accessor of property &#39;&lt;propertyname&gt;&#39; is not accessible</span></span>
<span data-ttu-id="a2809-103">Příkaz se pokusí načíst hodnotu vlastnosti, pokud nemá přístup k vlastnosti `Get` postupu.</span><span class="sxs-lookup"><span data-stu-id="a2809-103">A statement attempts to retrieve the value of a property when it does not have access to the property's `Get` procedure.</span></span>  
  
 <span data-ttu-id="a2809-104">Pokud [získat příkaz](../../../visual-basic/language-reference/statements/get-statement.md) je označen pro přístup k více omezující než úroveň jeho [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md), pokus o čtení hodnoty vlastnosti může selhat v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="a2809-104">If the [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md) is marked with a more restrictive access level than its [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md), an attempt to read the property value could fail in the following cases:</span></span>  
  
-   <span data-ttu-id="a2809-105">`Get` Je označena příkaz [privátní](../../../visual-basic/language-reference/modifiers/private.md) a kód volání je mimo třídu nebo strukturu, ve kterém je definovaný vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a2809-105">The `Get` statement is marked [Private](../../../visual-basic/language-reference/modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
-   <span data-ttu-id="a2809-106">`Get` Je označena příkaz [chráněné](../../../visual-basic/language-reference/modifiers/protected.md) a volací kód nejsou v třídu nebo strukturu, ve kterém je definovaný vlastnost ani v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="a2809-106">The `Get` statement is marked [Protected](../../../visual-basic/language-reference/modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
-   <span data-ttu-id="a2809-107">`Get` Je označena příkaz [Friend](../../../visual-basic/language-reference/modifiers/friend.md) a kód volání není ve stejném sestavení, ve kterém je definovaný vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a2809-107">The `Get` statement is marked [Friend](../../../visual-basic/language-reference/modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="a2809-108">**ID chyby:** BC31103</span><span class="sxs-lookup"><span data-stu-id="a2809-108">**Error ID:** BC31103</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a2809-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="a2809-109">To correct this error</span></span>  
  
-   <span data-ttu-id="a2809-110">Pokud máte řízení zdrojového kódu definování vlastnost, vezměte v úvahu deklarace `Get` procedura s stejnou úroveň přístupu jako samotné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a2809-110">If you have control of the source code defining the property, consider declaring the `Get` procedure with the same access level as the property itself.</span></span>  
  
-   <span data-ttu-id="a2809-111">Pokud máte řízení zdrojového kódu definování vlastnost, nebo je třeba omezit `Get` postup více, než se pokusí přesunout příkaz, který čte hodnota vlastnosti v oblasti kód, který má lepší přístup k samotné, vlastnosti úroveň přístupu Vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a2809-111">If you do not have control of the source code defining the property, or you must restrict the `Get` procedure access level more than the property itself, try to move the statement that reads the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2809-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="a2809-112">See Also</span></span>  
 [<span data-ttu-id="a2809-113">Procedury vlastností</span><span class="sxs-lookup"><span data-stu-id="a2809-113">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [<span data-ttu-id="a2809-114">Postupy: deklarace vlastnosti se smíšenými úrovněmi přístupu</span><span class="sxs-lookup"><span data-stu-id="a2809-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
