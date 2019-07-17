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
ms.openlocfilehash: 8bb61767324602ae54427c50c73e029a6c7bf3b7
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68236019"
---
# <a name="c-keywords"></a>Klíčová slova jazyka C#

Klíčová slova jsou předdefinované, vyhrazené identifikátory, které mají speciální význam pro kompilátor. Nelze je použít jako identifikátory v programu Pokud ovšem neobsahují `@` jako předponu. Například `@if` je platný identifikátor, ale `if` není, protože `if` je klíčové slovo.  
  
 V první tabulce v tomto tématu jsou uvedeny klíčová slova, která jsou vyhrazené identifikátory v jakékoli části programu v jazyce C#. V druhé tabulce v tomto tématu jsou uvedeny kontextová klíčová slova v jazyce C#. Kontextová klíčová slova mají zvláštní význam pouze v kontextu omezené programu a může sloužit jako identifikátory mimo tento kontext. Obecně platí protože nová klíčová slova jsou přidány do jazyka C#, se přidají jako kontextová klíčová slova Pokud se chcete vyhnout přerušení programy vytvořené ve starších verzích.  
  
|||||  
|---|---|---|---|  
|[abstract](abstract.md)|[as](../operators/type-testing-and-conversion-operators.md#as-operator)|[base](base.md)|[bool](bool.md)|  
|[break](break.md)|[byte](../builtin-types/integral-numeric-types.md)|[case](switch.md)|[catch](try-catch.md)|  
|[char](char.md)|[checked](checked.md)|[class](class.md)|[const](const.md)|  
|[continue](continue.md)|[decimal](../builtin-types/floating-point-numeric-types.md)|[default](default.md)|[delegate](delegate.md)|  
|[do](do.md)|[double](../builtin-types/floating-point-numeric-types.md)|[else](if-else.md)|[enum](enum.md)|  
|[event](event.md)|[explicit](../operators/user-defined-conversion-operators.md)|[extern](extern.md)|[false](false-literal.md)|  
|[finally](try-finally.md)|[Oprava](fixed-statement.md)|[float](../builtin-types/floating-point-numeric-types.md)|[for](for.md)|  
|[Foreach](foreach-in.md)|[goto](goto.md)|[if](if-else.md)|[implicit](../operators/user-defined-conversion-operators.md)|  
|[in](in.md)|[int](../builtin-types/integral-numeric-types.md)|[interface](interface.md)|[internal](internal.md)|
|[is](is.md)|[lock](lock-statement.md)|[long](../builtin-types/integral-numeric-types.md)|[namespace](namespace.md)|
|[new](../operators/new-operator.md)|[null](null.md)|[object](object.md)|[operator](../operators/operator-overloading.md)|
|[out](out.md)|[override](override.md)|[params](params.md)|[private](private.md)|
|[protected](protected.md)|[public](public.md)|[readonly](readonly.md)|[ref](ref.md)|
|[return](return.md)|[sbyte](../builtin-types/integral-numeric-types.md)|[sealed](sealed.md)|[short](../builtin-types/integral-numeric-types.md)||
[sizeof](sizeof.md)|[stackalloc](../operators/stackalloc.md)|[static](static.md)|[string](string.md)|
|[struct](struct.md)|[switch](switch.md)|[this](this.md)|[throw](throw.md)|
|[true](true-literal.md)|[Zkuste](try-catch.md)|[typeof](../operators/type-testing-and-conversion-operators.md#typeof-operator)|[uint](../builtin-types/integral-numeric-types.md)|
|[ulong](../builtin-types/integral-numeric-types.md)|[unchecked](unchecked.md)|[unsafe](unsafe.md)|[ushort](../builtin-types/integral-numeric-types.md)|
|[using](using.md)|[Pomocí statické](using-static.md)|[virtual](virtual.md)|[void](void.md)|
|[volatile](volatile.md)|[while](while.md)|

## <a name="contextual-keywords"></a>Kontextová klíčová slova

 Kontextové klíčové slovo slouží k poskytování zvláštní význam v kódu, ale to není rezervované slovo v jazyce C#. Některé kontextová klíčová slova, jako například `partial` a `where`, mají zvláštní význam ve dvou nebo více kontexty.  
  
||||  
|---|---|---|  
|[add](add.md)|[Alias](extern-alias.md)|[ascending](ascending.md)|
|[async](async.md)|[await](await.md)|[by](by.md)|
|[descending](descending.md)|[dynamic](dynamic.md)|[equals](equals.md)|
|[from](from-clause.md)|[get](get.md)|[global](global.md)|
|[Skupiny](group-clause.md)|[into](into.md)|[join](join-clause.md)|
|[let](let-clause.md)|[nameof](../operators/nameof.md)|[on](on.md)|
|[Řadit podle](orderby-clause.md)|[partial (typ)](partial-type.md)|[partial (metoda)](partial-method.md)|
|[remove](remove.md)|[Vyberte](select-clause.md)|[set](set.md)|
|[value](value.md)|[var](var.md)|[when (podmínka filtru)](when.md)|
|[where (omezení obecného typu)](where-generic-type-constraint.md)|[kde (klauzule dotazu)](where-clause.md)|[yield](yield.md)|
  
## <a name="see-also"></a>Viz také:

- [C#referenční dokumentace](../index.md)
