---
title: Hodnoty (F#)
description: 'Zjistěte, jak jsou množství, které mají určitý typ hodnoty v jazyce F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: b40e4a0409a9161a4ef48c8d4ad82b4da346538e
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="values"></a>Hodnoty

Množství, které mají určitý typ; jsou hodnoty v jazyce F # hodnoty může být nedílnou nebo plovoucí desetinnou čárkou, znaků nebo text, seznamy, pořadí, pole, řazené kolekce členů, rozlišovaná sjednocení, záznamy, typy tříd nebo hodnoty funkce.


## <a name="binding-a-value"></a>Vazby hodnoty
Termín *vazby* znamená přidružení názvu definice. `let` – Klíčové slovo sváže hodnotu, jako v následujících příkladech:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet601.fs)]

Typ hodnoty je odvozen z definice. Typ primitivní typ, například bod integrální nebo plovoucí desetinné číslo, je určeno z typu literál. Proto v předchozím příkladu, kompilátor odvodí typ `b` být `unsigned int`, zatímco kompilátor odvodí typ `a` být `int`. Typ funkce hodnoty se určí z návratovou hodnotu v těle funkce. Další informace o typech hodnotu funkce najdete v tématu [funkce](../functions/index.md). Další informace o typy literálu najdete v tématu [literály](../literals.md).


## <a name="why-immutable"></a>Proč neměnné?
Neměnné hodnoty jsou hodnoty, které nelze změnit, aby během spuštění programu. Pokud jste zvyklí jazyků, například C++, Visual Basic nebo C#, je možné překvapivé, F # vloží nadřazenost přes neměnné hodnoty, nikoli proměnné, které je možné přiřadit nové hodnoty během provádění programu. Neměnné dat je důležitý prvek funkční programování. V prostředí s více vlákny je obtížné spravovat sdílené měnitelný proměnné, které může změnit mnoho různých vláknech. Navíc s měnitelnou proměnné, může v některých případech být obtížné zjistit, pokud proměnné může být změněn, pokud je předán do jiné funkce.

V čistě funkčních jazyků nejsou žádné proměnné a funkce výhradně chovat jako matematické funkce. Kde je kód v jazyce, procedurální používá přiřazení proměnné změnit hodnotu, ekvivalentní kód v jazyce, funkční má neměnné hodnotu, která je vstupní neměnné funkce a různé neměnné hodnoty jako výstup. Tato matematickém přísnosti umožňuje pro náročnější důvody o chování programu. Tato náročnější reasoning je co umožňuje kompilátory přísnější kontroluje kódu a optimalizovat efektivněji, a pomáhá usnadnit uživatelům pochopit a psát správný kód. Funkční kód je proto mohou být snazší ladění než obyčejnou procedurální kódu.

F # čistý funkční jazyk, ještě není plně podporuje funkční programování. Pomocí neměnné hodnot je vhodné, protože tato funkce umožňuje, aby váš kód, abyste mohli využívat výhod důležitým aspektem funkční programování.


## <a name="mutable-variables"></a>Měnitelný proměnné
Můžete použít klíčové slovo `mutable` zadat proměnné, která lze změnit. Měnitelný proměnné v jazyce F # obecně měli mít omezený rozsah, jako pole typu nebo jako místní hodnotu. Měnitelný proměnné s omezeným oborem se snadněji řídit a jsou méně pravděpodobné, že má být změněn nesprávné způsoby.

Počáteční hodnotu na měnitelnou proměnnou lze přiřadit pomocí `let` – klíčové slovo v stejným způsobem, jak můžete nadefinovat hodnotu. Ale rozdílem je, že lze následně nové hodnoty na měnitelný proměnné přiřadit pomocí `<-` operátor jako v následujícím příkladu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet602.fs)]
    
## <a name="related-topics"></a>Související témata


|Název|Popis|
|-----|-----------|
|[Vazby let](../functions/let-bindings.md)|Poskytuje informace o používání `let` – klíčové slovo k vytvoření vazby. názvy hodnot a funkce.|
|[Funkce](../functions/index.md)|Poskytuje přehled funkcí v F #.|

## <a name="see-also"></a>Viz také
[Hodnoty Null](null-Values.md)

[Referenční dokumentace jazyka F#](../index.md)
