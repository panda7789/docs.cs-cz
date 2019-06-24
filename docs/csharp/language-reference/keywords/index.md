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
ms.openlocfilehash: 1aff57186f08a651aaf5e8dfaa988b5fb296768d
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306604"
---
# <a name="c-keywords"></a>Klíčová slova jazyka C#

Klíčová slova jsou předdefinované, vyhrazené identifikátory, které mají speciální význam pro kompilátor. Nelze je použít jako identifikátory v programu Pokud ovšem neobsahují `@` jako předponu. Například `@if` je platný identifikátor, ale `if` není, protože `if` je klíčové slovo.  
  
 V první tabulce v tomto tématu jsou uvedeny klíčová slova, která jsou vyhrazené identifikátory v jakékoli části programu v jazyce C#. V druhé tabulce v tomto tématu jsou uvedeny kontextová klíčová slova v jazyce C#. Kontextová klíčová slova mají zvláštní význam pouze v kontextu omezené programu a může sloužit jako identifikátory mimo tento kontext. Obecně platí protože nová klíčová slova jsou přidány do jazyka C#, se přidají jako kontextová klíčová slova Pokud se chcete vyhnout přerušení programy vytvořené ve starších verzích.  
  
|||||  
|---|---|---|---|  
|[abstract](abstract.md)|[as](../operators/type-testing-and-conversion-operators.md#as-operator)|[base](base.md)|[bool](bool.md)|  
|[break](break.md)|[byte](byte.md)|[case](switch.md)|[catch](try-catch.md)|  
|[char](char.md)|[checked](checked.md)|[class](class.md)|[const](const.md)|  
|[continue](continue.md)|[decimal](decimal.md)|[default](default.md)|[delegate](delegate.md)|  
|[do](do.md)|[double](double.md)|[else](if-else.md)|[enum](enum.md)|  
|[event](event.md)|[explicit](explicit.md)|[extern](extern.md)|[false](false-literal.md)|  
|[finally](try-finally.md)|[Oprava](fixed-statement.md)|[float](float.md)|[for](for.md)|  
|[Foreach](foreach-in.md)|[goto](goto.md)|[if](if-else.md)|[implicit](implicit.md)|  
|[in](in.md)|[int](int.md)|[interface](interface.md)|[internal](internal.md)|
|[is](is.md)|[lock](lock-statement.md)|[long](long.md)|[namespace](namespace.md)|
|[new](new.md)|[null](null.md)|[object](object.md)|[operator](operator.md)|
|[out](out.md)|[override](override.md)|[params](params.md)|[private](private.md)|
|[protected](protected.md)|[public](public.md)|[readonly](readonly.md)|[ref](ref.md)|
|[return](return.md)|[sbyte](sbyte.md)|[sealed](sealed.md)|[short](short.md)||
[sizeof](sizeof.md)|[stackalloc](../operators/stackalloc.md)|[static](static.md)|[string](string.md)|
|[struct](struct.md)|[switch](switch.md)|[this](this.md)|[throw](throw.md)|
|[true](true-literal.md)|[try](try-catch.md)|[typeof](../operators/type-testing-and-conversion-operators.md#typeof-operator)|[uint](uint.md)|
|[ulong](ulong.md)|[unchecked](unchecked.md)|[unsafe](unsafe.md)|[ushort](ushort.md)|
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
|[group](group-clause.md)|[into](into.md)|[join](join-clause.md)|
|[let](let-clause.md)|[nameof](nameof.md)|[on](on.md)|
|[Řadit podle](orderby-clause.md)|[partial (typ)](partial-type.md)|[partial (metoda)](partial-method.md)|
|[remove](remove.md)|[select](select-clause.md)|[set](set.md)|
|[value](value.md)|[var](var.md)|[when (podmínka filtru)](when.md)|
|[where (omezení obecného typu)](where-generic-type-constraint.md)|[kde (klauzule dotazu)](where-clause.md)|[yield](yield.md)|
  
## <a name="see-also"></a>Viz také:

- [C#referenční dokumentace](../index.md)
