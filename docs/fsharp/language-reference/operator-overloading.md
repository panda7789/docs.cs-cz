---
title: Přetížení operátoru (F#)
description: Zjistěte, jak přetěžovat aritmetické operátory ve třídě nebo typ záznamu a na globální úrovni v jazyce F#.
ms.date: 05/16/2016
ms.openlocfilehash: 6232ebf215289e6a22b9d77fbd5fa67b82460486
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "44087296"
---
# <a name="operator-overloading"></a>Přetížení operátoru

Toto téma popisuje, jak přetěžovat aritmetické operátory ve třídě nebo v typu záznamu a na globální úrovni.

## <a name="syntax"></a>Syntaxe

```fsharp
// Overloading an operator as a class or record member.
static member (operator-symbols) (parameter-list) =
    method-body
// Overloading an operator at the global level
let [inline] (operator-symbols) parameter-list = function-body
```

## <a name="remarks"></a>Poznámky

V předchozí syntaxi *symbol operátoru* je jedním z `+`, `-`, `*`, `/`, `=`, a tak dále. *Seznam parametrů* určuje operandy v pořadí, jsou uvedeny v běžné syntaxi pro daný operátor. *Tělo metody* vytvoří výslednou hodnotu.

Přetížení operátoru musí být statické. Přetížení operátoru unárních operátorů, například `+` a `-`, musí pomocí tildy (`~`) v *symbol operátoru* označuje, že operátor unární operátor a binárních operátorů, jak je znázorněno následující deklarace.

```fsharp
static member (~-) (v : Vector)
```

Následující kód ukazuje třídu Vector, která má pouze dva operátory, jeden pro unární mínus a jeden pro násobení pomocí skaláru. V tomto příkladu jsou pro skalární násobení potřeba dvě přetížení, protože operátor musí fungovat bez ohledu na pořadí vektoru a skaláru.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4001.fs)]

## <a name="creating-new-operators"></a>Vytvoření nových operátorů

Přetížit lze všechny standardní operátory, avšak můžete také vytvořit nové operátory mimo sekvence určitých znaků. Povolené znaky operátoru jsou `!`, `%`, `&`, `*`, `+`, `-`, `.`, `/`, `<`, `=`, `>`, `?`, `@`, `^`, `|`, a `~`. Znak `~` má zvláštní význam, který vytváří z operátoru unární operátor a není součástí sekvence znaků operátoru. Ne všechny operátory mohou být unární.

V závislosti na přesné posloupnosti znaků bude mít operátor určitou přednost a asociativitu. Asociativita může být buď zleva doprava, nebo zprava doleva a používá se při zobrazení sekvence operátorů stejné úrovně priority bez použití závorek.

Znak operátoru `.` neovlivňuje prioritu, takže pokud je například třeba definovat vlastní verzi násobení, která má stejnou prioritu a asociativitu operátorů jako obyčejné násobení, je možné vytvořit operátory, jako například `.*`.

Pouze operátory `?` a `?<-` může začínat `?`.

Tabulku, která ukazuje priority všech operátorů v jazyce F# lze nalézt v [operátor referenční dokumentace symbolů a](symbol-and-operator-reference/index.md).

## <a name="overloaded-operator-names"></a>Názvy přetíženého operátoru

Když kompilátor jazyka F# kompiluje výraz operátoru, generuje metodu, která má pro tento operátor název vygenerovaný kompilátorem. Jde o název, který se pro metodu zobrazuje v jazyce MSIL (Microsoft Intermediate Language) a také v reflexi a v technologii IntelliSense. V kódu jazyka F# obvykle není nutné tyto názvy používat.

Následující tabulka uvádí standardní operátory a jejich odpovídající vygenerované názvy.

|Operátor|Vygenerovaný název|
|--------|--------------|
|`[]`|`op_Nil`|
|`::`|`op_Cons`|
|`+`|`op_Addition`|
|`-`|`op_Subtraction`|
|`*`|`op_Multiply`|
|`/`|`op_Division`|
|`@`|`op_Append`|
|`^`|`op_Concatenate`|
|`%`|`op_Modulus`|
|`&&&`|`op_BitwiseAnd`|
|<code>&#124;&#124;&#124;</code>|`op_BitwiseOr`|
|`^^^`|`op_ExclusiveOr`|
|`<<<`|`op_LeftShift`|
|`~~~`|`op_LogicalNot`|
|`>>>`|`op_RightShift`|
|`~+`|`op_UnaryPlus`|
|`~-`|`op_UnaryNegation`|
|`=`|`op_Equality`|
|`<=`|`op_LessThanOrEqual`|
|`>=`|`op_GreaterThanOrEqual`|
|`<`|`op_LessThan`|
|`>`|`op_GreaterThan`|
|`?`|`op_Dynamic`|
|`?<-`|`op_DynamicAssignment`|
|<code>&#124;></code>|`op_PipeRight`|
|<code><&#124;</code>|`op_PipeLeft`|
|`!`|`op_Dereference`|
|`>>`|`op_ComposeRight`|
|`<<`|`op_ComposeLeft`|
|`<@ @>`|`op_Quotation`|
|`<@@ @@>`|`op_QuotationUntyped`|
|`+=`|`op_AdditionAssignment`|
|`-=`|`op_SubtractionAssignment`|
|`*=`|`op_MultiplyAssignment`|
|`/=`|`op_DivisionAssignment`|
|`..`|`op_Range`|
|`.. ..`|`op_RangeStep`|

Další kombinace znaků operátoru, které zde nejsou uvedeny, lze použít jako operátory a mohou mít názvy, jež jsou vytvořeny zřetězením názvů jednotlivých znaků z následující tabulky. Například +! změní `op_PlusBang`.

|Znak operátoru|Název|
|------------------|----|
|`>`|`Greater`|
|`<`|`Less`|
|`+`|`Plus`|
|`-`|`Minus`|
|`*`|`Multiply`|
|`/`|`Divide`|
|`=`|`Equals`|
|`~`|`Twiddle`|
|`%`|`Percent`|
|`.`|`Dot`|
|`&`|`Amp`|
|<code>&#124;</code>|`Bar`|
|`@`|`At`|
|`^`|`Hat`|
|`!`|`Bang`|
|`?`|`Qmark`|
|`(`|`LParen`|
|`,`|`Comma`|
|`)`|`RParen`|
|`[`|`LBrack`|
|`]`|`RBrack`|

## <a name="prefix-and-infix-operators"></a>Operátory Prefix a Infix

*Předpona* se očekává, že operátory budou umístěny před operand nebo operandy podobně jako funkce. *Infix* se očekává, že operátory budou umístěny mezi dva operandy.

Pouze některé operátory lze používat jako operátory Prefix. Některé operátory jsou vždy operátory Prefix, ostatní mohou být Prefix nebo Infix a zbývající jsou vždy operátory Infix. Operátory, které začínají znakem `!`, s výjimkou `!=` a operátoru `~` nebo opakované sekvence`~`, jsou vždy operátory Prefix. Operátory `+`, `-`, `+.`, `-.`, `&`, `&&`, `%` a `%%` mohou být operátory Prefix nebo Infix. Rozlišovat mezi Prefix a Infix verzí operátoru lze přidáním znaku `~` na začátek operátoru Prefix, a to při jeho definici. Znak `~` se nebude používat při použití operátoru, ale pouze při jeho definici.

## <a name="example"></a>Příklad

Následující kód ukazuje použití přetěžování pro implementaci typu zlomku. Zlomek je reprezentován čitatelem a jmenovatelem. Funkce `hcf` se používá k určení nejvyššího společného faktoru, který slouží k redukci zlomků.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4002.fs)]

**Výstup:**

```
3/4 + 1/2 = 5/4
3/4 - 1/2 = 1/4
3/4 * 1/2 = 3/8
3/4 / 1/2 = 3/2
3/4 + 1 = 7/4
```

## <a name="operators-at-the-global-level"></a>Operátory na globální úrovni

Je také možné definovat operátory na globální úrovni. Následující kód definuje operátor `+?`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4003.fs)]

Výstupem kódu uvedeného výše je `12`.

Vzhledem k tomu, že pravidla oboru jazyka F# nařizují, že nově definované operátory mají přednost před vestavěnými operátory, je možné tímto způsobem předefinovat běžné aritmetické operátory.

U globálních operátorů, které mnohdy představují malé funkce, jež jsou nejlépe začlenitelné do volaného kódu, se často používá klíčové slovo `inline`. Vložení funkcí operátoru umožňuje operátorům pracovat se staticky řešenými typy parametrů za účelem vytvoření staticky řešeného generického kódu. Další informace najdete v tématu [vložené funkce](functions/inline-functions.md) a [statisticky vyřešených parametrů typu](generics/statically-resolved-type-parameters.md).

## <a name="see-also"></a>Viz také:

- [Členové](members/index.md)
