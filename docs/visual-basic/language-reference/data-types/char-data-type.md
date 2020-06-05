---
title: Char – datový typ
ms.date: 07/20/2015
f1_keywords:
- vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
ms.openlocfilehash: 3dbbf9f6a2c4079775e05f5d2dcd8704c1ec4259
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387475"
---
# <a name="char-data-type-visual-basic"></a>Char – datový typ (Visual Basic)

Obsahuje nepodepsaný 16bitový (2 bajt) body kódu v rozsahu od 0 do 65535. Každý *bod kódu*nebo kód znaku představuje jeden znak Unicode.

## <a name="remarks"></a>Poznámky

`Char`Datový typ použijte v případě, že potřebujete držet jenom jeden znak a nemusíte mít režii `String` . V některých případech můžete použít `Char()` pole `Char` prvků pro uložení více znaků.

Výchozí hodnota `Char` je znak s bodem kódu 0.

## <a name="unicode-characters"></a>Znaky Unicode

Prvních 128 kódových bodů (0 – 127) Unicode odpovídá písmenům a symbolům na standardní americké klávesnici. Tyto první body kódu 128 jsou stejné jako ty, které definuje znaková sada ASCII. Druhý bod kódu 128 (128 – 255) představuje speciální znaky, jako jsou písmena abecedy založená na latince, zvýraznění, symboly měn a zlomky. Kódování Unicode používá zbývající body kódu (256-65535) pro širokou škálu symbolů, včetně celosvětových textových znaků, diakritických znamének a matematických a technických symbolů.

<xref:System.Char.IsDigit%2A>K určení klasifikace Unicode můžete použít metody jako a <xref:System.Char.IsPunctuation%2A> na `Char` proměnné.

## <a name="type-conversions"></a>Převody typu

Visual Basic nepřevádí přímo mezi `Char` a číselnými typy. Můžete použít <xref:Microsoft.VisualBasic.Strings.Asc%2A> <xref:Microsoft.VisualBasic.Strings.AscW%2A> funkci nebo pro převod `Char` hodnoty na `Integer` , která představuje jeho bod kódu. Můžete použít <xref:Microsoft.VisualBasic.Strings.Chr%2A> <xref:Microsoft.VisualBasic.Strings.ChrW%2A> funkci nebo pro převod `Integer` hodnoty na `Char` , která má tento kódový bod.

Pokud je přepínač pro kontrolu typu ( [příkaz Option Strict](../statements/option-strict-statement.md)) zapnutý, je nutné připojit znak literálového typu k řetězcovému literálu s jedním znakem a identifikovat ho jako `Char` datový typ. Toto dokládá následující příklad. První přiřazení k `charVar` proměnné generuje chybu kompilátoru [BC30512](../../misc/bc30512.md) `Option Strict` , protože je zapnuto. Druhé kompilování bylo úspěšné, protože `c` literální znak literálu identifikuje literál jako `Char` hodnotu.

```vb
Option Strict On

Module CharType
    Public Sub Main()
        Dim charVar As Char

        ' This statement generates compiler error BC30512 because Option Strict is On.  
        charVar = "Z"  

        ' The following statement succeeds because it specifies a Char literal.  
        charVar = "Z"c
    End Sub
End Module
```

## <a name="programming-tips"></a>Tipy k programování

- **Záporná čísla.** `Char`je typ bez znaménka a nemůže představovat zápornou hodnotu. V žádném případě byste neměli používat `Char` k ukládání číselných hodnot.

- **Problematika spolupráce.** Pokud rozhraní s komponentami, které nejsou zapsány pro .NET Framework, například automatizace nebo objekty COM, pamatujte, že typy znaků mají v jiných prostředích jinou šířku dat (8 bitů). Pokud předáte 8bitovému argumentu takové součásti, deklarujte ji jako `Byte` místo `Char` v novém Visual Basic kódu.

- **Rozšiřující.** `Char`Datový typ se rozšíří na `String` . To znamená, že můžete převést na a nemůžete se `Char` `String` setkat s <xref:System.OverflowException?displayProperty=nameWithType> .

- **Znaky typu.** Připojení znaku literálového typu `C` k řetězcovému literálu s jedním znakem vynutí `Char` datový typ. `Char`nemá žádný znak typu identifikátoru.

- **Typ rozhraní.** Odpovídající typ v .NET Framework je <xref:System.Char?displayProperty=nameWithType> Struktura.

## <a name="see-also"></a>Viz také

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [Datové typy](index.md)
- [Datový typ String](string-data-type.md)
- [Funkce pro převod typů](../functions/type-conversion-functions.md)
- [Souhrn převodu](../keywords/conversion-summary.md)
- [Postupy: Volání funkce Windows, která přebírá typy bez znaménka](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Účinné používání datových typů](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
