---
title: Řetězce
description: 'Přečtěte si, jak typ řetězce F # představuje neměnný text jako posloupnost znaků Unicode.'
ms.date: 07/05/2019
ms.openlocfilehash: 67a6506b4b8c479da1022c069a7f53402f904b4d
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855410"
---
# <a name="strings"></a>Řetězce

`string`Typ představuje neproměnlivý text jako posloupnost znaků Unicode. `string`je alias pro `System.String` v rozhraní .NET.

> [!NOTE]
> Reference k rozhraní docs.microsoft.com API pro F # není dokončená. Pokud narazíte na nefunkční odkazy, místo toho použijte [dokumentaci základní knihovny F #](https://fsharp.github.io/fsharp-core-docs/) .

## <a name="remarks"></a>Poznámky

Řetězcové literály jsou odděleny znakem uvozovky ("). Znak zpětného lomítka ( \\ ) se používá ke kódování určitých speciálních znaků. Zpětné lomítko a další znak dohromady se označují jako *řídicí sekvence*. Řídicí sekvence, které jsou podporovány v literálech řetězce F #, jsou uvedeny v následující tabulce.

|Znak|Řídicí sekvence|
|---------|---------------|
|Výstrahy|`\a`|
|Backspace|`\b`|
|Informační kanál formuláře|`\f`|
|Nového|`\n`|
|Návrat na začátek řádku|`\r`|
|Karta|`\t`|
|Vertikální tabulátor|`\v`|
|Zpětné lomítko|`\\`|
|Znak uvozovek|`\"`|
|Apostrof|`\'`|
|znak Unicode|`\DDD`(kde `D` označuje desítkovou číslici; rozsah 000-255; například `\231` = "ç")|
|znak Unicode|`\xHH`(kde `H` označuje hexadecimální číslo; rozsah 00-FF; například `\xE7` = "ç")|
|znak Unicode|`\uHHHH`(UTF-16) (kde `H` označuje šestnáctkovou číslici; rozsah 0000-FFFF;  například `\u00E7` = "ç")|
|znak Unicode|`\U00HHHHHH`(UTF-32) (kde `H` označuje hexadecimální číslici, rozsah 000000-10FFFF;  například `\U0001F47D` = " 👽 ")|

> [!IMPORTANT]
> `\DDD`Řídicí sekvence je Desítkový zápis, nikoli osmičkový zápis podobně jako ve většině ostatních jazyků. Proto číslice `8` a `9` jsou platné a sekvence `\032` představuje mezeru (U + 0020), zatímco stejný bod kódu v osmičkové notaci by byl `\040` .

> [!NOTE]
> S omezením na rozsah 0-255 (0xFF), `\DDD` `\x` řídicí sekvence a jsou efektivně nastaveny jako znaková sada [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) , protože se shoduje s 256 prvními body kódu Unicode.

## <a name="verbatim-strings"></a>Doslovné řetězce

Pokud předchází symbol @, je literál doslovného řetězce. To znamená, že všechny řídicí sekvence jsou ignorovány s tím rozdílem, že dva znaky uvozovek jsou interpretovány jako jeden znak uvozovky.

## <a name="triple-quoted-strings"></a>Trojité řetězce v uvozovkách

Navíc může být řetězec uzavřen třemi uvozovkami. V tomto případě jsou všechny řídicí sekvence ignorovány, včetně znaků dvojité uvozovky. Chcete-li zadat řetězec, který obsahuje vložený řetězec v uvozovkách, můžete buď použít doslovné řetězec nebo trojitý řetězec v uvozovkách. Pokud použijete doslovné řetězec, je nutné zadat dva znaky uvozovek, které označují znak jednoduché uvozovky. Použijete-li řetězec v uvozovkách, lze použít znaky jednoduchých uvozovek bez jejich analyzování jako konce řetězce. Tato technika může být užitečná při práci s XML nebo jinými strukturami, které zahrnují vložené uvozovky.

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

V kódu jsou řetězce, které mají zalomení řádků, přijaty a zalomení řádků jsou interpretovány jako newlines, pokud znak zpětného lomítka není poslední znak před koncem řádku. Počáteční prázdné místo na dalším řádku se při použití znaku zpětného lomítka ignoruje. Následující kód vytvoří řetězec `str1` , který má hodnotu `"abc\ndef"` a řetězec `str2` , který má hodnotu `"abcdef"` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a>Indexování řetězců a vytváření řezů

K jednotlivým znakům v řetězci můžete přistupovat pomocí syntaxe typu pole, a to následujícím způsobem.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

Výstup je `b` .

Nebo můžete extrahovat podřetězce pomocí syntaxe řezu pole, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

Výstup je následující.

```console
abc
def
```

Řetězce ASCII můžete reprezentovat poli bajtů bez znaménka, typ `byte[]` . Přidáte příponu `B` do řetězcového literálu, který označuje, že se jedná o řetězec ASCII. Řetězcové literály ASCII používané s poli bajtů podporují stejné řídicí sekvence jako řetězce Unicode, s výjimkou řídicích sekvencí Unicode.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a>Operátory řetězce

`+`Operátor lze použít k zřetězení řetězců a udržování kompatibility s funkcemi pro zpracování .NET Framework řetězců. Následující příklad znázorňuje zřetězení řetězců.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a>String – Třída

Vzhledem k tomu, že typ řetězce v jazyce F # je ve skutečnosti .NET Framework `System.String` typ, `System.String` jsou k dispozici všichni členové. To zahrnuje `+` operátor, který se používá ke zřetězení řetězců, `Length` vlastnost a `Chars` vlastnost, která vrací řetězec jako pole znaků Unicode. Další informace o řetězcích naleznete v tématu `System.String` .

Pomocí `Chars` vlastnosti `System.String` můžete k jednotlivým znakům v řetězci přistupovat zadáním indexu, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a>Řetězec – modul

Další funkce pro zpracování řetězců je obsažena v `String` modulu v `FSharp.Core` oboru názvů. Další informace najdete v tématu [modul Core. String](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka F #](index.md)
