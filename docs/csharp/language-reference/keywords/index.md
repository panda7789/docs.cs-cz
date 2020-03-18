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
ms.openlocfilehash: 928917d25b5f3f97c4b8cdff85efdaa1957be41e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399313"
---
# <a name="c-keywords"></a>Klíčová slova jazyka C#

Klíčová slova jsou předdefinované, vyhrazené identifikátory, které mají zvláštní význam pro kompilátor. Nelze je použít jako identifikátory v `@` programu, pokud neobsahují jako předponu. Například `@if` je platný identifikátor, `if` ale `if` není, protože je klíčové slovo.  
  
 První tabulka v tomto tématu uvádí klíčová slova, která jsou vyhrazenými identifikátory v libovolné části programu jazyka C#. Druhá tabulka v tomto tématu uvádí kontextová klíčová slova v c#. Kontextová klíčová slova mají zvláštní význam pouze v omezeném kontextu programu a lze je použít jako identifikátory mimo tento kontext. Obecně platí, že jako nová klíčová slova jsou přidány do jazyka C#, jsou přidány jako kontextová klíčová slova, aby se zabránilo přerušení programy napsané v dřívějších verzích.  
  
|||||  
|---|---|---|---|  
|[Abstraktní](abstract.md)|[Jako](../operators/type-testing-and-cast.md#as-operator)|[base](base.md)|[bool](../builtin-types/bool.md)|  
|[Přestávce](break.md)|[Bajt](../builtin-types/integral-numeric-types.md)|[Případě](switch.md)|[Chytit](try-catch.md)|  
|[char](../builtin-types/char.md)|[Kontrolovány](checked.md)|[Třída](class.md)|[const](const.md)|  
|[continue](continue.md)|[decimal](../builtin-types/floating-point-numeric-types.md)|[Výchozí](default.md)|[delegát](../builtin-types/reference-types.md)|  
|[dělat](do.md)|[double](../builtin-types/floating-point-numeric-types.md)|[Jiného](if-else.md)|[Výčtu](../builtin-types/enum.md)|  
|[Událost](event.md)|[explicit](../operators/user-defined-conversion-operators.md)|[Externí](extern.md)|[false (nepravda)](../builtin-types/bool.md)|  
|[Konečně](try-finally.md)|[Dlouhodobého](fixed-statement.md)|[float](../builtin-types/floating-point-numeric-types.md)|[Pro](for.md)|  
|[Foreach](foreach-in.md)|[Goto](goto.md)|[Pokud](if-else.md)|[implicit](../operators/user-defined-conversion-operators.md)|  
|[In](in.md)|[int](../builtin-types/integral-numeric-types.md)|[Rozhraní](interface.md)|[Vnitřní](internal.md)|
|[Je](is.md)|[Zámek](lock-statement.md)|[long](../builtin-types/integral-numeric-types.md)|[Namespace](namespace.md)|
|[Nwe](../operators/new-operator.md)|[null](null.md)|[Objekt](../builtin-types/reference-types.md)|[operator](../operators/operator-overloading.md)|
|[ven](out.md)|[override](override.md)|[params](params.md)|[Soukromé](private.md)|
|[protected](protected.md)|[Veřejné](public.md)|[Readonly](readonly.md)|[ref](ref.md)|
|[return](return.md)|[Sbyte](../builtin-types/integral-numeric-types.md)|[sealed](sealed.md)|[short](../builtin-types/integral-numeric-types.md)||
[sizeof](../operators/sizeof.md)|[stackalloc](../operators/stackalloc.md)|[Statické](static.md)|[Řetězec](../builtin-types/reference-types.md)|
|[Struct](../builtin-types/struct.md)|[Přepnout](switch.md)|[tohoto provozu](this.md)|[throw](throw.md)|
|[true](../builtin-types/bool.md)|[Zkuste](try-catch.md)|[typeof](../operators/type-testing-and-cast.md#typeof-operator)|[uint](../builtin-types/integral-numeric-types.md)|
|[ulong](../builtin-types/integral-numeric-types.md)|[unchecked](unchecked.md)|[unsafe](unsafe.md)|[ushort](../builtin-types/integral-numeric-types.md)|
|[Pomocí](using.md)|[použití statické](using-static.md)|[virtual](virtual.md)|[void](../builtin-types/void.md)|
|[volatile](volatile.md)|[Zatímco](while.md)|

## <a name="contextual-keywords"></a>Kontextová klíčová slova

 Kontextové klíčové slovo se používá k poskytnutí konkrétní význam v kódu, ale není vyhrazené slovo v C#. Některá kontextová klíčová slova, například `partial` a `where`, mají zvláštní význam ve dvou nebo více kontextech.  
  
||||  
|---|---|---|  
|[Přidat](add.md)|[alias](extern-alias.md)|[ascending](ascending.md)|
|[async](async.md)|[await](../operators/await.md)|[podle](by.md)|
|[descending](descending.md)|[Dynamické](../builtin-types/reference-types.md)|[equals](equals.md)|
|[Z](from-clause.md)|[get](get.md)|[Globální](../operators/namespace-alias-qualifier.md)|
|[skupina](group-clause.md)|[Do](into.md)|[Připojit](join-clause.md)|
|[Nechat](let-clause.md)|[nameof](../operators/nameof.md)|[Na](on.md)|
|[Orderby](orderby-clause.md)|[částečné (typ)](partial-type.md)|[částečná (metoda)](partial-method.md)|
|[Odebrat](remove.md)|[Vyberte](select-clause.md)|[Nastavit](set.md)|
|[nespravovaný (omezení obecného typu)](where-generic-type-constraint.md)|[Hodnotu](value.md)|[Var](var.md)|
|[when (podmínka filtru)](when.md)|[where (omezení obecného typu)](where-generic-type-constraint.md)|[kde (klauzule dotazu)](where-clause.md)|
|[yield](yield.md)| | |
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
