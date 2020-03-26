---
title: přepínat výraz - odkaz Jazyka C#
description: Naučte se používat výraz přepínače C# pro porovnávání vzorů a další introspekce dat
ms.date: 03/19/2020
ms.openlocfilehash: 9e609bcea0f92f492b5f9b07840e47f75c1b71e4
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249786"
---
# <a name="switch-expression-c-reference"></a>přepínat výraz (odkaz C# )

Tento článek `switch` popisuje výraz, zavedené v C# 8.0. Informace o `switch` prohlášení naleznete v článku o [ `switch` prohlášení](../keywords/switch.md) v části [příkazy.](../keywords/index.md)

## <a name="basic-example"></a>Základní příklad

Výraz `switch` poskytuje `switch`sémantiku -like v kontextu výrazu. Poskytuje stručnou syntaxi, když ramena přepínače vytvoří hodnotu. Následující příklad ukazuje strukturu výrazu přepínače. Překládá hodnoty z `enum` reprezentující vizuální směry v online mapě do odpovídajícího základního směru:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetBasicStructure":::

Předchozí ukázka ukazuje základní prvky výrazu přepínače:

- *Výraz rozsahu*: Předchozí příklad používá `direction` proměnnou jako výraz rozsahu.
- *Ramena výrazu switch*: Každé rameno výrazu přepínače `=>` obsahuje *vzorek*, volitelný kryt *případu*, token a *výraz*.

Výsledkem *výrazu switch* je hodnota výrazu prvního *ramene výrazu přepínače,* jehož *vzor* odpovídá `true` *výrazu rozsahu* a jehož ochrana *příčiny*, pokud je k dispozici, vyhodnotí na . *Výraz* na pravé straně `=>` tokenu nemůže být výraz příkazu.

*Ramena výrazu přepínače* jsou vyhodnocována v textovém pořadí. Kompilátor vydá chybu, když nelze vybrat *rameno výrazu* dolní přepínač, protože vyšší *rameno výrazu přepínače* odpovídá všem jeho hodnotám.

## <a name="patterns-and-case-guards"></a>Vzory a kryty skříně

Mnoho vzorů jsou podporovány v přepínači výraz zbraní. Předchozí příklad použil *vzor hodnoty*. *Vzorek hodnoty* porovná výraz rozsahu s hodnotou. Tato hodnota musí být konstanta času kompilace. *Vzorek typu* porovná výraz rozsahu se známým typem. Následující příklad načte třetí prvek z sekvence. Používá různé metody založené na typu sekvence:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetTypePattern":::

Vzorky mohou být rekurzivní, kde vzorek testuje typ a pokud tento typ odpovídá, vzorek odpovídá jedné nebo více hodnotám vlastností ve výrazu rozsahu. K rozšíření předchozího příkladu můžete použít rekurzivní vzorky. Můžete přidat příkazy výraz přepínače pro pole, která mají méně než 3 prvky. Rekurzivní vzory jsou uvedeny v následujícím příkladu:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetRecursivePattern":::

Rekurzivní vzory můžete zkoumat vlastnosti výrazu rozsahu, ale nelze spustit libovolný kód. Ochrannou *dobu případu*určenou `when` v klauzuli můžete použít k poskytnutí podobných kontrol pro jiné typy sekvencí:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetGuardCase":::

Nakonec můžete přidat `_` vzorek a `null` vzorek zachytit argumenty, které nejsou zpracovány žádné jiné rameno výraz u přepínače. To dělá výraz *přepínače vyčerpávající*, což znamená, že je zpracována jakákoli možná hodnota výrazu rozsahu. Následující příklad přidá tyto výrazzbraně:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetExhaustive":::

Předchozí příklad přidá `null` vzorek a změní `IEnumerable<T>` vzorek textu `_` na vzorek. Vzor `null` poskytuje kontrolu null jako rameno výrazu přepínače. Výraz pro tuto ruku <xref:System.ArgumentNullException>vyvolá . Vzor `_` odpovídá všem vstupům, které nebyly spárovány s předchozími rameny. Musí přijít po `null` kontrole, jinak `null` by odpovídala vstupům.

Můžete si přečíst více v návrhu c# jazyk spec pro [rekurzivní vzory](~/_csharplang/proposals/csharp-8.0/patterns.md#switch-expression).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
- [Porovnávání vzorů](../../pattern-matching.md)
