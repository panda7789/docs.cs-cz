---
title: Řetězce
description: Zjistěte, jak typ F# 'řetězec' představuje neměnný text jako posloupnost znaků Unicode.
ms.date: 07/05/2019
ms.openlocfilehash: 242a2cefa1cce8995090dddd1d1fd7181e0f5e0c
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739567"
---
# <a name="strings"></a>Řetězce

> [!NOTE]
> Odkazy na odkazy na odkazy na odkazy na rozhraní API v tomto článku přejdete na msdn.  Odkaz na rozhraní API docs.microsoft.com není dokončen.

Typ `string` představuje neměnný text jako posloupnost znaků Unicode. `string`je alias `System.String` v rozhraní .NET Framework.

## <a name="remarks"></a>Poznámky

Řetězcové literály jsou odděleny znakem uvozovky ("). Znak zpětného \\ lomítka ( ) se používá ke kódování určitých speciálních znaků. Zpětné lomítko a další znak společně jsou označovány jako *sekvence escape*. Sekvence escape podporované v literálech řetězce F# jsou uvedeny v následující tabulce.

|Znak|Úniková sekvence|
|---------|---------------|
|Výstrahy|`\a`|
|Backspace|`\b`|
|Informační kanál formuláře|`\f`|
|Newline|`\n`|
|Návrat na začátek řádku|`\r`|
|Karta|`\t`|
|Vertikální tabulátor|`\v`|
|Zpětné lomítko|`\\`|
|Uvozovky|`\"`|
|Apostrof|`\'`|
|znak Unicode|`\DDD`(kde `D` označuje desetinnou číslici; rozsah 000 - 255; například `\231` = "ç")|
|znak Unicode|`\xHH`(kde `H` označuje šestnáctkovou číslici; rozsah 00 - FF; `\xE7` například = "ç")|
|znak Unicode|`\uHHHH`(UTF-16) (kde `H` označuje šestnáctkovou číslici; rozsah 0000 - FFFF;  například `\u00E7` = "ç")|
|znak Unicode|`\U00HHHHHH`(UTF-32) (kde `H` označuje šestnáctkovou číslici; rozsah 000000 - 10FFFF;  například `\U0001F47D` =👽" ")|

> [!IMPORTANT]
> Escape `\DDD` sekvence je desetinné zápisy, nikoli osmičkové zápisy jako ve většině ostatních jazyků. Proto číslice `8` `9` a jsou platné a `\032` posloupnost představuje mezeru (U + 0020), vzhledem `\040`k tomu, že stejný bod kódu v osmičkové notaci by .

> [!NOTE]
> Omezena na rozsah 0 - 255 (0xFF), `\DDD` `\x` a escape sekvence jsou účinně [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) znakovou sadu, protože to odpovídá první 256 bodů kódu Unicode.

## <a name="verbatim-strings"></a>Doslovné řetězce

Pokud předchází symbol @, literál je doslovný řetězec. To znamená, že všechny sekvence escape jsou ignorovány, s tím rozdílem, že dva znaky uvozovek jsou interpretovány jako jeden znak uvozovky.

## <a name="triple-quoted-strings"></a>Trojité citované řetězce

Řetězec může být navíc uzavřen trojitými uvozovkami. V tomto případě jsou ignorovány všechny sekvence escape, včetně dvojitých uvozovek znaků. Chcete-li zadat řetězec, který obsahuje vložený řetězec v uvozovkách, můžete použít doslovný řetězec nebo řetězec s trojitým uvozovkami. Pokud používáte doslovný řetězec, musíte zadat dva znaky uvozovek, které označují jeden znak uvozovky. Pokud používáte řetězec s trojitým uvozovkami, můžete použít znaky jednoduchých uvozovek, aniž by byly analyzovány jako konec řetězce. Tato technika může být užitečná při práci s XML nebo jinými strukturami, které obsahují vložené uvozovky.

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

V kódu jsou přijaty řetězce, které mají konce řádků a konce řádků jsou interpretovány doslova jako nové řádky, pokud znak zpětného lomítka není posledním znakem před zalomení řádku. Úvodní prázdné místo na dalším řádku je při použití znaku zpětného lomítka ignorováno. Následující kód vytvoří `str1` řetězec, který `"abc\ndef"` má `str2` hodnotu `"abcdef"`a řetězec, který má hodnotu .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a>Indexování řetězců a krájení

K jednotlivým znakům v řetězci můžete přistupovat pomocí syntaxe podobné poli, a to následujícím způsobem.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

Výstup je `b`.

Nebo můžete extrahovat podřetězce pomocí syntaxe řezu pole, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

Výstup je následující.

```console
abc
def
```

Řetězce ASCII můžete reprezentovat podle polí nepodepsaných bajtů, zadejte `byte[]`. Přidáte příponu `B` do literálu řetězce označující, že se jedná o řetězec ASCII. Literály řetězce ASCII používané s bajtovými poli podporují stejné sekvence escape jako řetězce Unicode, s výjimkou řídicích sekvencí Unicode.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a>Operátory řetězce

Operátor `+` lze použít ke zřetězení řetězců, zachování kompatibility s funkcemi zpracování řetězce rozhraní .NET Framework. Následující příklad ilustruje zřetězení řetězců.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a>Třída řetězce

Vzhledem k tomu, že typ řetězce `System.String` v F# je ve skutečnosti typ rozhraní .NET Framework, jsou k dispozici všechny `System.String` členy. To zahrnuje `+` operátor, který se používá ke zřetězení řetězců, `Length` vlastnosti a `Chars` vlastnosti, která vrací řetězec jako pole znaků Unicode. Další informace o řetězcích `System.String`naleznete v tématu .

Pomocí vlastnosti `Chars` `System.String`, můžete přistupovat k jednotlivým znakům v řetězci zadáním indexu, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a>Modul řetězce

Další funkce pro zpracování řetězců `String` je součástí `FSharp.Core` modulu v oboru názvů. Další informace naleznete v tématu [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).

## <a name="see-also"></a>Viz také

- [Referenční příručka jazyka F#](index.md)
