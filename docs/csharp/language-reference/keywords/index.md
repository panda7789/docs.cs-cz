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
ms.custom: updateeachrelease
ms.assetid: e929b0f2-4b92-4d37-8060-23d323b098ad
ms.openlocfilehash: 51e3802ba7b78dab4c3f96365c51af83098c05c7
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656121"
---
# <a name="c-keywords"></a>Klíčová slova jazyka C#

Klíčová slova jsou předdefinovaná, rezervované identifikátory, které mají zvláštní význam pro kompilátor. Nelze je použít jako identifikátory v programu, pokud nejsou zahrnuty `@` jako předpony. Například `@if` je platný identifikátor, ale není to, `if` protože `if` je klíčové slovo.  
  
 První tabulka v tomto tématu uvádí klíčová slova, která jsou rezervované identifikátory v jakékoli části programu v jazyce C#. Druhá tabulka v tomto tématu uvádí kontextová klíčová slova v jazyce C#. Kontextová klíčová slova mají zvláštní význam pouze v omezeném kontextu programu a lze je použít jako identifikátory mimo tento kontext. Obecně platí, že když jsou nová klíčová slova přidána do jazyka C#, přidají se jako kontextová klíčová slova, aby se předešlo narušení napsaným v dřívějších verzích.  
  
|||||  
|---|---|---|---|  
|[Výtah](abstract.md)|[formátu](../operators/type-testing-and-cast.md#as-operator)|[base](base.md)|[bool](../builtin-types/bool.md)|  
|[break](break.md)|[bytové](../builtin-types/integral-numeric-types.md)|[tom](switch.md)|[catch](try-catch.md)|  
|[char](../builtin-types/char.md)|[kontrolovaný](checked.md)|[Deník](class.md)|[const](const.md)|  
|[pokraeovat](continue.md)|[decimal](../builtin-types/floating-point-numeric-types.md)|[výchozí](default.md)|[dostával](../builtin-types/reference-types.md)|  
|[do](do.md)|[double](../builtin-types/floating-point-numeric-types.md)|jinak ([else](if-else.md))|[vytváření](../builtin-types/enum.md)|  
|[událostí](event.md)|[explicitně](../operators/user-defined-conversion-operators.md)|[extern](extern.md)|[chybné](../builtin-types/bool.md)|  
|[finally](try-finally.md)|[určí](fixed-statement.md)|[float](../builtin-types/floating-point-numeric-types.md)|[pro](for.md)|  
|[foreach](foreach-in.md)|[goto](goto.md)|[if](if-else.md)|[nepřímo](../operators/user-defined-conversion-operators.md)|  
|[pro](in.md)|[int](../builtin-types/integral-numeric-types.md)|[prostředí](interface.md)|[internal](internal.md)|
|[dojde](is.md)|[získáte](lock-statement.md)|[long](../builtin-types/integral-numeric-types.md)|[hosting](namespace.md)|
|[New](../operators/new-operator.md)|[null](null.md)|[object](../builtin-types/reference-types.md)|[podnikatel](../operators/operator-overloading.md)|
|[mimo](out.md)|[override](override.md)|[params](params.md)|[private](private.md)|
|[protected](protected.md)|[public](public.md)|[readonly](readonly.md)|[ref](ref.md)|
|[return](return.md)|[SByte](../builtin-types/integral-numeric-types.md)|[sealed](sealed.md)|[short](../builtin-types/integral-numeric-types.md)||
[sizeof](../operators/sizeof.md)|[stackalloc](../operators/stackalloc.md)|[static](static.md)|[řetezce](../builtin-types/reference-types.md)|
|[nemají](../builtin-types/struct.md)|[přepnutí](switch.md)|[this](this.md)|[throw](throw.md)|
|[podmínka](../builtin-types/bool.md)|[Zkuste](try-catch.md)|[typeof](../operators/type-testing-and-cast.md#typeof-operator)|[uint](../builtin-types/integral-numeric-types.md)|
|[ulong](../builtin-types/integral-numeric-types.md)|[unchecked](unchecked.md)|[UNSAFE](unsafe.md)|[ushort](../builtin-types/integral-numeric-types.md)|
|[using](using.md)|[virtual](virtual.md)|[void](../builtin-types/void.md)|[volatile](volatile.md)|
|[while](while.md)|

## <a name="contextual-keywords"></a>Kontextová klíčová slova

 Kontextové klíčové slovo se používá k poskytnutí konkrétního významu v kódu, ale není to rezervované slovo v jazyce C#. Některá kontextová klíčová slova, například `partial` a `where` , mají zvláštní význam ve dvou nebo více kontextech.  
  
||||  
|---|---|---|  
|[add](add.md)|[zástupný](extern-alias.md)|[ascending](ascending.md)|
|[async](async.md)|[await](../operators/await.md)|[by](by.md)|
|[descending](descending.md)|[dynamic](../builtin-types/reference-types.md)|[rovná](equals.md)|
|[Výsledkem](from-clause.md)|[get](get.md)|[globální](../operators/namespace-alias-qualifier.md)|
|[skupina](group-clause.md)|[uskladněn](into.md)|[zúčastnit](join-clause.md)|
|[aplikaci](let-clause.md)|[nameof](../operators/nameof.md)|[pnete](on.md)|
|[OrderBy](orderby-clause.md)|[částečný (typ)](partial-type.md)|[Partial (metoda)](partial-method.md)|
|[odebrány](remove.md)|[vybrali](select-clause.md)|[stanovenými](set.md)|
|[nespravované (omezení obecného typu)](where-generic-type-constraint.md)|[osa](value.md)|[Proměnná](var.md)|
|[when (podmínka filtru)](when.md)|[where (omezení obecného typu)](where-generic-type-constraint.md)|[WHERE (klauzule dotazu)](where-clause.md)|
|[yield](yield.md)| | |
  
## <a name="see-also"></a>Viz také:

- [Referenční dokumentace k jazyku C#](../index.md)
