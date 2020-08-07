---
title: Switch – výraz – Referenční dokumentace jazyka C#
description: Naučte se používat výraz přepínače C# pro porovnávání vzorů a jiné introspekce dat.
ms.date: 03/19/2020
ms.openlocfilehash: 2249afc1ff1cc81e9ad423d910ebb95df8c787d4
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916658"
---
# <a name="switch-expression-c-reference"></a>Switch – výraz (Referenční dokumentace jazyka C#)

Tento článek se věnuje `switch` výrazu zavedenému v C# 8,0. Informace o `switch` příkazu naleznete v článku na [ `switch` příkazu](../keywords/switch.md) v oddílu [příkazy](../keywords/index.md) .

## <a name="basic-example"></a>Základní příklad

`switch`Výraz poskytuje `switch` sémantiku podobně jako v kontextu výrazu. Poskytuje stručnou syntaxi, když zbraně přepínače vytvoří hodnotu. Následující příklad ukazuje strukturu výrazu přepínače. Překládá hodnoty z `enum` reprezentace vizuálních směrů v online mapě na odpovídající směr mohutnosti:

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetBasicStructure":::

Předchozí příklad ukazuje základní prvky výrazu Switch:

- *Výraz rozsahu*: předchozí příklad používá proměnnou `direction` jako výraz rozsahu.
- *Paže s výrazem přepínače*: každý výraz přepínače ARM obsahuje *vzor*, volitelný *případ Guard*, `=>` token a *výraz*.

Výsledek *výrazu Switch* je hodnota výrazu pro výraz sekvence prvního *přepínače ARM* , jehož *vzor* odpovídá *výrazu rozsahu* *a kde je, pokud je přítomen*, je vyhodnocen jako `true` . *Výraz* na pravé straně `=>` tokenu nemůže být příkaz výrazu.

*Paže výrazu přepínače* jsou vyhodnocovány v textovém pořadí. Kompilátor vystaví chybu, pokud nelze zvolit *ARM výrazu* dolního přepínače, protože *ARM výrazu* vyššího přepínače odpovídá všem jeho hodnotám.

## <a name="patterns-and-case-guards"></a>Vzory a případové Guardy

V rukou výrazu Switch je podporováno mnoho vzorů. Předchozí příklad používá *konstantní vzorek*. *Konstantní vzor* porovnává výraz rozsahu s hodnotou. Tato hodnota musí být konstanta v době kompilace. *Vzor typu* porovnává výraz rozsahu se známým typem. Následující příklad načte třetí prvek z sekvence. Používá různé metody v závislosti na typu sekvence:

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetTypePattern":::

Vzorce mohou být rekurzivní, kde vzor testuje typ a pokud tento typ odpovídá, vzor odpovídá jedné nebo více hodnot vlastností ve výrazu rozsahu. Pomocí rekurzivních vzorů můžete výše uvedený příklad zvětšit. Pro pole, která mají méně než 3 prvky, přidejte paže výrazu přepínače. Rekurzivní vzory jsou uvedeny v následujícím příkladu:

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetRecursivePattern":::

Rekurzivní vzory mohou kontrolovat vlastnosti výrazu rozsahu, ale nemohou spustit libovolný kód. K poskytnutí podobných kontrol pro jiné typy sekvencí můžete použít *ochrannou velikost písmen*zadanou v `when` klauzuli.

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetGuardCase":::

Nakonec můžete přidat `_` vzor a `null` vzor pro zachycení argumentů, které nejsou zpracovávány jakýmkoli jiným ramenem výrazu Switch. Díky tomu je výraz Switch *vyčerpávající*, což znamená, že je zpracována jakákoli možná hodnota výrazu rozsahu. Následující příklad přidá tyto zbraně výrazů:

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetExhaustive":::

Předchozí příklad přidá `null` vzor a změní `IEnumerable<T>` vzorek typu na `_` vzor. `null`Vzor poskytuje kontrolu null jako ARM výrazu přepínače. Výraz pro tuto platformu ARM vyvolá <xref:System.ArgumentNullException> . `_`Vzor odpovídá všem vstupům, které nebyly porovnány s předchozími opěrkami. Musí se nacházet po `null` kontrole nebo by odpovídala `null` vstupům.

Můžete si přečíst další informace v návrhu specifikace jazyka C# pro [rekurzivní vzory](~/_csharplang/proposals/csharp-8.0/patterns.md#switch-expression).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory a výrazy v C#](index.md)
- [Porovnávání vzorů](../../pattern-matching.md)
