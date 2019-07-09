---
title: Řetězce
description: Zjistěte, jak F# typ "řetězec" představuje neměnné text jako posloupnost znaků Unicode.
ms.date: 07/05/2019
ms.openlocfilehash: ec895723cc6d21a701a27b5d70d053bb681ce2b3
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67660599"
---
# <a name="strings"></a>Řetězce

> [!NOTE]
> Rozhraní API referenčních odkazů v tomto článku se dostanete na webu MSDN.  Reference k rozhraní API webu docs.microsoft.com není dokončena.

`string` Typ představuje neměnné text jako posloupnost znaků Unicode. `string` je alias pro `System.String` v rozhraní .NET Framework.

## <a name="remarks"></a>Poznámky

Řetězcové literály jsou oddělené znakem uvozovky ("). Znak zpětného lomítka ( \\ ) slouží ke kódování některé speciální znaky. Zpětné lomítko a další znak společně se nazývají *sekvence escape*. Řídicí sekvence, které jsou podporovány v F# řetězcové literály jsou uvedeny v následující tabulce.

|Znak|Řídicí sekvence|
|---------|---------------|
|Výstrahy|`\a`|
|Backspace|`\b`|
|Posun strany|`\f`|
|nový řádek|`\n`|
|Návrat na začátek řádku|`\r`|
|Karta|`\t`|
|Vertikální tabulátor|`\v`|
|Zpětné lomítko|`\\`|
|Znak uvozovek|`\"`|
|Apostrof|`\'`|
|znak Unicode|`\DDD` (kde `D` označuje desítkové číslice; rozsah 000 - 255, například `\231` = "ç")|
|znak Unicode|`\xHH` (kde `H` označuje šestnáctková číslice; rozsahu 00 - FF; například `\xE7` = "ç")|
|znak Unicode|`\uHHHH` (UTF-16) (kde `H` označuje šestnáctková číslice; rozsah 0000 - FFFF;  například `\u00E7` = "ç")|
|znak Unicode|`\U00HHHHHH` (UTF-32) (kde `H` označuje šestnáctková číslice; rozsah 000000 - 10FFFF.;  například `\U0001F47D` = "👽")|

> [!IMPORTANT]
> `\DDD` Řídicí sekvence je desítkový zápis, nikoli osmičkové soustavě stejně jako v většina jiných jazycích. Proto číslic `8` a `9` jsou platné a sekvencí `\032` představuje mezery (U + 0020), zatímco by tento stejný bod kódu v osmičkové soustavě `\040`.

> [!NOTE]
> Je omezené na rozsah 0 – 255 (0xFF) `\DDD` a `\x` řídicí sekvence jsou účinně [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) znaková sada, protože odpovídající prvních 256 kódové body sady Unicode.

Předchází-li symbolem @, je literál doslovný řetězec. To znamená, že jsou ignorovány všechny řídicí sekvence, s tím rozdílem, že jsou dva znaky uvozovek interpretován jako znak jeden znak uvozovek.

Kromě toho řetězec může být uzavřená v trojité uvozovky. V tomto případě jsou ignorovány všechny řídicí sekvence, včetně dvojité uvozovky znaků. Pokud chcete zadat řetězec, který obsahuje vložený řetězec v uvozovkách, můžete použít buď doslovný řetězec nebo řetězce uvozené třemi uvozovkami. Pokud používáte doslovný řetězec, musíte zadat dva znaky uvozovek označuje znak jednoduché uvozovky. Pokud používáte řetězce uvozené třemi uvozovkami, můžete použít jednoduché uvozovky znaků bez je analyzován jako konec řetězce. Tato technika může být užitečné při práci s XML nebo jiných struktur, které zahrnují uvozovky.

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

V kódu jsou přijaty řetězce, které mají konce řádků a zalomení řádků jsou interpretovány literálně jako vložení znaků newline, není-li znak zpětného lomítka před koncem řádku poslední znak. Úvodních mezer na dalším řádku je ignorován, pokud se používá znak zpětného lomítka. Následující kód vytvoří řetězec `str1` , která má hodnotu `"abc\ndef"` a řetězec `str2` , která má hodnotu `"abcdef"`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

Jednotlivé znaky v řetězci můžete přistupovat pomocí syntaxe jako pole.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

Výstup je `b`.

Nebo extrahujete dílčí řetězce pomocí syntaxe řez pole, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

Výstup je následující.

```
abc
def
```

Může představovat řetězce ASCII pomocí polí bajtů bez znaménka, typ `byte[]`. Přidat příponu `B` na řetězcový literál, že je řetězec ve formátu ASCII. Použít s pole bajtů ASCII řetězcové literály podporují stejné sekvence escape jako řetězce Unicode, s výjimkou řídicí sekvence Unicode.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a>Operátory řetězce

Existují dva způsoby, jak zřetězení řetězců: pomocí `+` operátor nebo s použitím `^` operátor. `+` Operátor udržuje kompatibilitu s zpracování funkce rozhraní .NET Framework řetězce.

Následující příklad ukazuje zřetězení řetězců.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a>Třída String

Protože typ řetězce v F# je ve skutečnosti na rozhraní .NET Framework `System.String` typ, všechny `System.String` členy jsou k dispozici. Jedná se o `+` operátor, který slouží k řetězení řetězců, `Length` vlastnost a `Chars` vlastnost, která vrací řetězec jako pole znaků Unicode. Další informace o řetězcích naleznete v tématu `System.String`.

S použitím `Chars` vlastnost `System.String`, dostanete jednotlivých znaků v řetězci tak, že zadáte indexu, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a>Řetězec modulu

Další funkce pro manipulaci s řetězci jsou součástí `String` v modulu `FSharp.Core` oboru názvů. Další informace najdete v tématu [Core.String – modul](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
