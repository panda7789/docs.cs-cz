---
title: Přetížení operátoru
description: Naučte se přetížit aritmetické operátory v typu třídy nebo záznamu a na globální úrovni v F#.
ms.date: 05/16/2016
ms.openlocfilehash: c656c1c47938e62386c8f063cf9a6caaaf69d0fe
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627386"
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

V předchozí syntaxi je *symbol operátoru* jedna z `+` `/` `-` `*`,,,, a tak dále. `=` *Seznam parametrů* určuje operandy v pořadí, v jakém jsou uvedeny v obvyklé syntaxi daného operátoru. *Tělo metody* vytvoří výslednou hodnotu.

Přetížení operátoru musí být statické. Přetížení operátoru pro unární operátory `+` , jako například a `-`, musí používat vlnovku (`~`) v *symbol operátoru* k označení, že operátor je unární operátor a nikoli binární operátor, jak je znázorněno v následujícím příkladu. změny.

```fsharp
static member (~-) (v : Vector)
```

Následující kód ukazuje třídu Vector, která má pouze dva operátory, jeden pro unární mínus a jeden pro násobení pomocí skaláru. V tomto příkladu jsou pro skalární násobení potřeba dvě přetížení, protože operátor musí fungovat bez ohledu na pořadí vektoru a skaláru.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4001.fs)]

## <a name="creating-new-operators"></a>Vytvoření nových operátorů

Přetížit lze všechny standardní operátory, avšak můžete také vytvořit nové operátory mimo sekvence určitých znaků. Povolené znaky operátoru `!`jsou `%`, `&`, `*`, `+`,, `-`, ,`/`,,, ,`>` `=` `<` `.` `?` ,`@`, `^` ,a`~`. `|` Znak `~` má zvláštní význam, který vytváří z operátoru unární operátor a není součástí sekvence znaků operátoru. Ne všechny operátory lze vytvořit unární.

V závislosti na přesné posloupnosti znaků bude mít operátor určitou přednost a asociativitu. Asociativita může být buď zleva doprava, nebo zprava doleva a používá se při zobrazení sekvence operátorů stejné úrovně priority bez použití závorek.

Znak operátoru `.` neovlivňuje prioritu, takže pokud je například třeba definovat vlastní verzi násobení, která má stejnou prioritu a asociativitu operátorů jako obyčejné násobení, je možné vytvořit operátory, jako například `.*`.

Jenom operátory `?` a `?<-` můžou začínat `?`na.

Tabulka, která zobrazuje prioritu všech operátorů v, F# je k dispozici v [odkazu symbol a operátor](./symbol-and-operator-reference/index.md).

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

Další kombinace znaků operátoru, které zde nejsou uvedeny, lze použít jako operátory a mohou mít názvy, jež jsou vytvořeny zřetězením názvů jednotlivých znaků z následující tabulky. Například +! bude `op_PlusBang`.

|Znak operátoru|Name|
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

Očekává se, že operátory prefixu budou umístěny před operand nebo operandy, podobně jako funkce. Očekává se, že operátory *vpony* umístit mezi dva operandy.

Pouze některé operátory lze používat jako operátory Prefix. Některé operátory jsou vždy operátory Prefix, ostatní mohou být Prefix nebo Infix a zbývající jsou vždy operátory Infix. Operátory, které začínají znakem `!`, s výjimkou `!=` a operátoru `~` nebo opakované sekvence`~`, jsou vždy operátory Prefix. Operátory `+`, `-`, `+.`, `-.`, `&`, `&&`, `%` a `%%` mohou být operátory Prefix nebo Infix. Rozlišovat mezi Prefix a Infix verzí operátoru lze přidáním znaku `~` na začátek operátoru Prefix, a to při jeho definici. Znak `~` se nebude používat při použití operátoru, ale pouze při jeho definici.

## <a name="example"></a>Příklad

Následující kód ukazuje použití přetěžování pro implementaci typu zlomku. Zlomek je reprezentován čitatelem a jmenovatelem. Funkce `hcf` se používá k určení nejvyššího společného faktoru, který slouží k redukci zlomků.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4002.fs)]

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

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4003.fs)]

Výstupem kódu uvedeného výše je `12`.

Vzhledem k tomu, že pravidla oboru jazyka F# nařizují, že nově definované operátory mají přednost před vestavěnými operátory, je možné tímto způsobem předefinovat běžné aritmetické operátory.

U globálních operátorů, které mnohdy představují malé funkce, jež jsou nejlépe začlenitelné do volaného kódu, se často používá klíčové slovo `inline`. Vložení funkcí operátoru umožňuje operátorům pracovat se staticky řešenými typy parametrů za účelem vytvoření staticky řešeného generického kódu. Další informace najdete v tématu [vložené funkce](./functions/inline-functions.md) a [staticky vyřešené parametry typu](./generics/statically-resolved-type-parameters.md).

## <a name="see-also"></a>Viz také:

- [Členové](./members/index.md)
