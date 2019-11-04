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
ms.openlocfilehash: 3699d25b781ddf25fd917e49cf3cdf8d20ea090f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422743"
---
# <a name="c-keywords"></a>Klíčová slova jazyka C#

Klíčová slova jsou předdefinovaná, rezervované identifikátory, které mají zvláštní význam pro kompilátor. Nelze je použít jako identifikátory v programu, pokud neobsahují `@` jako předponu. Například `@if` je platný identifikátor, ale `if` není, protože `if` je klíčové slovo.  
  
 První tabulka v tomto tématu uvádí klíčová slova, která jsou rezervované identifikátory v jakékoli části C# programu. Druhá tabulka v tomto tématu uvádí kontextová klíčová slova C#v. Kontextová klíčová slova mají zvláštní význam pouze v omezeném kontextu programu a lze je použít jako identifikátory mimo tento kontext. Obecně platí, že když se do C# jazyka přidají nová klíčová slova, přidají se jako kontextová klíčová slova, aby se předešlo přerušení programů napsaných v dřívějších verzích.  
  
|||||  
|---|---|---|---|  
|[abstract](abstract.md)|[as](../operators/type-testing-and-cast.md#as-operator)|[base](base.md)|[bool](bool.md)|  
|[break](break.md)|[byte](../builtin-types/integral-numeric-types.md)|[case](switch.md)|[catch](try-catch.md)|  
|[char](char.md)|[checked](checked.md)|[class](class.md)|[const](const.md)|  
|[continue](continue.md)|[decimal](../builtin-types/floating-point-numeric-types.md)|[default](default.md)|[delegate](../builtin-types/reference-types.md)|  
|[do](do.md)|[double](../builtin-types/floating-point-numeric-types.md)|[ostatních](if-else.md)|[enum](enum.md)|  
|[event](event.md)|[explicit](../operators/user-defined-conversion-operators.md)|[extern](extern.md)|[false](false-literal.md)|  
|[finally](try-finally.md)|[určí](fixed-statement.md)|[float](../builtin-types/floating-point-numeric-types.md)|[for](for.md)|  
|[foreach](foreach-in.md)|[goto](goto.md)|[Přestože](if-else.md)|[implicit](../operators/user-defined-conversion-operators.md)|  
|[in](in.md)|[int](../builtin-types/integral-numeric-types.md)|[interface](interface.md)|[internal](internal.md)|
|[is](is.md)|[lock](lock-statement.md)|[long](../builtin-types/integral-numeric-types.md)|[namespace](namespace.md)|
|[new](../operators/new-operator.md)|[null](null.md)|[object](../builtin-types/reference-types.md)|[operator](../operators/operator-overloading.md)|
|[out](out.md)|[override](override.md)|[params](params.md)|[private](private.md)|
|[protected](protected.md)|[public](public.md)|[readonly](readonly.md)|[ref](ref.md)|
|[return](return.md)|[sbyte](../builtin-types/integral-numeric-types.md)|[sealed](sealed.md)|[short](../builtin-types/integral-numeric-types.md)||
[sizeof](../operators/sizeof.md)|[stackalloc](../operators/stackalloc.md)|[static](static.md)|[string](../builtin-types/reference-types.md)|
|[struct](struct.md)|[switch](switch.md)|[this](this.md)|[throw](throw.md)|
|[true](true-literal.md)|[Zkuste](try-catch.md)|[typeof](../operators/type-testing-and-cast.md#typeof-operator)|[uint](../builtin-types/integral-numeric-types.md)|
|[ulong](../builtin-types/integral-numeric-types.md)|[unchecked](unchecked.md)|[unsafe](unsafe.md)|[ushort](../builtin-types/integral-numeric-types.md)|
|[using](using.md)|[Použití static](using-static.md)|[virtual](virtual.md)|[void](void.md)|
|[volatile](volatile.md)|[while](while.md)|

## <a name="contextual-keywords"></a>Kontextová klíčová slova

 Kontextové klíčové slovo se používá k poskytnutí konkrétního významu v kódu, ale není to rezervované slovo v C#. Některá kontextová klíčová slova, například `partial` a `where`, mají zvláštní význam ve dvou nebo více kontextech.  
  
||||  
|---|---|---|  
|[add](add.md)|[zástupný](extern-alias.md)|[ascending](ascending.md)|
|[async](async.md)|[await](../operators/await.md)|[by](by.md)|
|[descending](descending.md)|[dynamic](../builtin-types/reference-types.md)|[equals](equals.md)|
|[Výsledkem](from-clause.md)|[get](get.md)|[global](../operators/namespace-alias-qualifier.md)|
|[skupiny](group-clause.md)|[into](into.md)|[zúčastnit](join-clause.md)|
|[aplikaci](let-clause.md)|[nameof](../operators/nameof.md)|[on](on.md)|
|[OrderBy](orderby-clause.md)|[částečný (typ)](partial-type.md)|[Partial (metoda)](partial-method.md)|
|[remove](remove.md)|[vybrali](select-clause.md)|[set](set.md)|
|[nespravované (omezení obecného typu)](where-generic-type-constraint.md)|[value](value.md)|[var](var.md)|
|[when (podmínka filtru)](when.md)|[where (omezení obecného typu)](where-generic-type-constraint.md)|[WHERE (klauzule dotazu)](where-clause.md)|
|[yield](yield.md)| | |
  
## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
