---
title: "& č. 39; & Nastavit č. 39; přistupující objekt vlastnosti & č. 39; &lt;propertyname&gt;& č. 39; není dostupný"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9256a09b719ad3890e1d7c2cc23ffb0d40eec62f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="39set39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a><span data-ttu-id="77ecd-102">& č. 39; & Nastavit č. 39; přistupující objekt vlastnosti & č. 39; &lt;propertyname&gt;& č. 39; není dostupný</span><span class="sxs-lookup"><span data-stu-id="77ecd-102">&#39;Set&#39; accessor of property &#39;&lt;propertyname&gt;&#39; is not accessible</span></span>
<span data-ttu-id="77ecd-103">Příkaz se pokusí uložit hodnota vlastnosti, pokud nemá přístup k vlastnosti `Set` postupu.</span><span class="sxs-lookup"><span data-stu-id="77ecd-103">A statement attempts to store the value of a property when it does not have access to the property's `Set` procedure.</span></span>  
  
 <span data-ttu-id="77ecd-104">Pokud [příkaz Set](../../../visual-basic/language-reference/statements/set-statement.md) je označen pro přístup k více omezující než úroveň jeho [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md), pokus o nastavení hodnoty vlastnosti může selhat v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="77ecd-104">If the [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md) is marked with a more restrictive access level than its [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md), an attempt to set the property value could fail in the following cases:</span></span>  
  
-   <span data-ttu-id="77ecd-105">`Set` Je označena příkaz [privátní](../../../visual-basic/language-reference/modifiers/private.md) a kód volání je mimo třídu nebo strukturu, ve kterém je definovaný vlastnost.</span><span class="sxs-lookup"><span data-stu-id="77ecd-105">The `Set` statement is marked [Private](../../../visual-basic/language-reference/modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
-   <span data-ttu-id="77ecd-106">`Set` Je označena příkaz [chráněné](../../../visual-basic/language-reference/modifiers/protected.md) a volací kód nejsou v třídu nebo strukturu, ve kterém je definovaný vlastnost ani v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="77ecd-106">The `Set` statement is marked [Protected](../../../visual-basic/language-reference/modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
-   <span data-ttu-id="77ecd-107">`Set` Je označena příkaz [Friend](../../../visual-basic/language-reference/modifiers/friend.md) a kód volání není ve stejném sestavení, ve kterém je definovaný vlastnost.</span><span class="sxs-lookup"><span data-stu-id="77ecd-107">The `Set` statement is marked [Friend](../../../visual-basic/language-reference/modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="77ecd-108">**ID chyby:** BC31102</span><span class="sxs-lookup"><span data-stu-id="77ecd-108">**Error ID:** BC31102</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="77ecd-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="77ecd-109">To correct this error</span></span>  
  
-   <span data-ttu-id="77ecd-110">Pokud máte řízení zdrojového kódu definování vlastnost, vezměte v úvahu deklarace `Set` procedura s stejnou úroveň přístupu jako samotné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="77ecd-110">If you have control of the source code defining the property, consider declaring the `Set` procedure with the same access level as the property itself.</span></span>  
  
-   <span data-ttu-id="77ecd-111">Pokud máte řízení zdrojového kódu definování vlastnost, nebo je třeba omezit `Set` postup úroveň přístupu, více než samotné, vlastnosti pokusem o přesun příkaz, který nastaví hodnotu vlastnosti na kód, který má lepší přístup k oblasti Vlastnost.</span><span class="sxs-lookup"><span data-stu-id="77ecd-111">If you do not have control of the source code defining the property, or you must restrict the `Set` procedure access level more than the property itself, try to move the statement that sets the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77ecd-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="77ecd-112">See Also</span></span>  
 [<span data-ttu-id="77ecd-113">Procedury vlastností</span><span class="sxs-lookup"><span data-stu-id="77ecd-113">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [<span data-ttu-id="77ecd-114">Postupy: deklarace vlastnosti se smíšenými úrovněmi přístupu</span><span class="sxs-lookup"><span data-stu-id="77ecd-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
