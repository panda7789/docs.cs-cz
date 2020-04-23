---
title: Klíčová slova jazyka C#
ms.date: 03/07/2017
f1_keywords:
- cs.keywords
helpviewer_keywords:
- keywords [C#]
- C# language, keywords
- Visual C#, keywords
- '@ keyword'
ms.assetid: e929b0f2-4b92-4d37-8060-23d323b098ad
ms.openlocfilehash: 251046a8bd825a90d817965f9f747d08d4492197
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102031"
---
# <a name="c-keywords"></a>Klíčová slova jazyka C#

Klíčová slova jsou předdefinované, vyhrazené identifikátory, které mají zvláštní význam pro kompilátor. Nelze je použít jako identifikátory v `@` programu, pokud neobsahují jako předponu. Například `@if` je platný identifikátor, `if` ale `if` není, protože je klíčové slovo.  
  
 První tabulka v tomto tématu uvádí klíčová slova, která jsou vyhrazenými identifikátory v libovolné části programu jazyka C#. Druhá tabulka v tomto tématu uvádí kontextová klíčová slova v c#. Kontextová klíčová slova mají zvláštní význam pouze v omezeném kontextu programu a lze je použít jako identifikátory mimo tento kontext. Obecně platí, že jako nová klíčová slova jsou přidány do jazyka C#, jsou přidány jako kontextová klíčová slova, aby se zabránilo přerušení programy napsané v dřívějších verzích.  
  
|||||  
|---|---|---|---|  
|[Abstraktní](abstract.md)|[Jako](../operators/type-testing-and-cast.md#as-operator)|[base](base.md)|[bool](../builtin-types/bool.md)|  
|[break](break.md)|[Bajt](../builtin-types/integral-numeric-types.md)|[Případě](switch.md)|[Chytit](try-catch.md)|  
|[char](../builtin-types/char.md)|[Kontrolovány](checked.md)|[třída](class.md)|[const](const.md)|  
|[continue](continue.md)|[decimal](../builtin-types/floating-point-numeric-types.md)|[default](default.md)|[delegát](../builtin-types/reference-types.md)|  
|[do](do.md)|[double](../builtin-types/floating-point-numeric-types.md)|[else](if-else.md)|[Výčtu](../builtin-types/enum.md)|  
|[event](event.md)|[explicit](../operators/user-defined-conversion-operators.md)|[extern](extern.md)|[False](../builtin-types/bool.md)|  
|[Konečně](try-finally.md)|[Dlouhodobého](fixed-statement.md)|[float](../builtin-types/floating-point-numeric-types.md)|[pro](for.md)|  
|[Foreach](foreach-in.md)|[goto](goto.md)|[if](if-else.md)|[implicit](../operators/user-defined-conversion-operators.md)|  
|[in](in.md)|[int](../builtin-types/integral-numeric-types.md)|[rozhraní](interface.md)|[internal](internal.md)|
|[is](is.md)|[Zámek](lock-statement.md)|[long](../builtin-types/integral-numeric-types.md)|[namespace](namespace.md)|
|[Nwe](../operators/new-operator.md)|[null](null.md)|[Objekt](../builtin-types/reference-types.md)|[operator](../operators/operator-overloading.md)|
|[ven](out.md)|[override](override.md)|[params](params.md)|[private](private.md)|
|[protected](protected.md)|[public](public.md)|[readonly](readonly.md)|[ref](ref.md)|
|[return](return.md)|[Sbyte](../builtin-types/integral-numeric-types.md)|[sealed](sealed.md)|[short](../builtin-types/integral-numeric-types.md)||
[sizeof](../operators/sizeof.md)|[stackalloc](../operators/stackalloc.md)|[static](static.md)|[řetězec](../builtin-types/reference-types.md)|
|[Struct](../builtin-types/struct.md)|[switch](switch.md)|[this](this.md)|[throw](throw.md)|
|[Pravda](../builtin-types/bool.md)|[Zkuste](try-catch.md)|[typeof](../operators/type-testing-and-cast.md#typeof-operator)|[uint](../builtin-types/integral-numeric-types.md)|
|[ulong](../builtin-types/integral-numeric-types.md)|[unchecked](unchecked.md)|[Nebezpečné](unsafe.md)|[ushort](../builtin-types/integral-numeric-types.md)|
|[using](using.md)|[virtual](virtual.md)|[void](../builtin-types/void.md)|[volatile](volatile.md)|
|[while](while.md)|

## <a name="contextual-keywords"></a>Kontextová klíčová slova

 Kontextové klíčové slovo se používá k poskytnutí konkrétní význam v kódu, ale není vyhrazené slovo v C#. Některá kontextová klíčová slova, například `partial` a `where`, mají zvláštní význam ve dvou nebo více kontextech.  
  
||||  
|---|---|---|  
|[add](add.md)|[alias](extern-alias.md)|[ascending](ascending.md)|
|[async](async.md)|[await](../operators/await.md)|[by](by.md)|
|[descending](descending.md)|[dynamic](../builtin-types/reference-types.md)|[equals](equals.md)|
|[Z](from-clause.md)|[Dostat](get.md)|[Globální](../operators/namespace-alias-qualifier.md)|
|[skupina](group-clause.md)|[into](into.md)|[Připojit](join-clause.md)|
|[Nechat](let-clause.md)|[nameof](../operators/nameof.md)|[on](on.md)|
|[Orderby](orderby-clause.md)|[částečné (typ)](partial-type.md)|[částečná (metoda)](partial-method.md)|
|[remove](remove.md)|[Vyberte](select-clause.md)|[Nastavit](set.md)|
|[nespravovaný (omezení obecného typu)](where-generic-type-constraint.md)|[value](value.md)|[var](var.md)|
|[when (podmínka filtru)](when.md)|[where (omezení obecného typu)](where-generic-type-constraint.md)|[kde (klauzule dotazu)](where-clause.md)|
|[yield](yield.md)| | |
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
