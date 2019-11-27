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
ms.openlocfilehash: 1ed5b19a307d094fc1d5a6bb0251c57052dc9bc1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344051"
---
# <a name="char-data-type-visual-basic"></a>Char – datový typ (Visual Basic)

Obsahuje nepodepsaný 16bitový (2 bajt) body kódu v rozsahu od 0 do 65535. Každý *bod kódu*nebo kód znaku představuje jeden znak Unicode.

## <a name="remarks"></a>Poznámky

Datový typ `Char` použijte v případě, že potřebujete držet jenom jeden znak a nemusíte mít režii `String`. V některých případech můžete použít `Char()`pole `Char` prvků pro uložení více znaků.

Výchozí hodnota `Char` je znak s bodem kódu 0.

## <a name="unicode-characters"></a>Znaky Unicode

Prvních 128 kódových bodů (0 – 127) Unicode odpovídá písmenům a symbolům na standardní americké klávesnici. Tyto první body kódu 128 jsou stejné jako ty, které definuje znaková sada ASCII. Druhý bod kódu 128 (128 – 255) představuje speciální znaky, jako jsou písmena abecedy založená na latince, zvýraznění, symboly měn a zlomky. Kódování Unicode používá zbývající body kódu (256-65535) pro širokou škálu symbolů, včetně celosvětových textových znaků, diakritických znamének a matematických a technických symbolů.

Pomocí metod, jako je <xref:System.Char.IsDigit%2A> a <xref:System.Char.IsPunctuation%2A>, můžete v proměnné `Char` určit svou klasifikaci Unicode.

## <a name="type-conversions"></a>Převody typu

Visual Basic nepřevádí přímo mezi `Char` a číselnými typy. Můžete použít funkci <xref:Microsoft.VisualBasic.Strings.Asc%2A> nebo <xref:Microsoft.VisualBasic.Strings.AscW%2A> k převedení `Char` hodnoty na `Integer`, který představuje jeho bod kódu. Můžete použít funkci <xref:Microsoft.VisualBasic.Strings.Chr%2A> nebo <xref:Microsoft.VisualBasic.Strings.ChrW%2A> k převedení `Integer` hodnoty na `Char`, který má tento bod kódu.

Pokud je přepínač pro kontrolu typu ( [příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)) zapnutý, je nutné připojit znak literálového typu k řetězcovému literálu s jedním znakem a identifikovat ho jako datový typ `Char`. Toto dokládá následující příklad. První přiřazení `charVar` proměnné generuje chybu kompilátoru [BC30512](../../misc/bc30512.md) , protože `Option Strict` je zapnuto. Druhé kompilování bylo úspěšné, protože znak typu literálu `c` identifikuje literál jako `Char`ovou hodnotu.

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

- **Záporná čísla.** `Char` je typ bez znaménka a nemůže představovat zápornou hodnotu. V žádném případě byste neměli používat `Char` k ukládání číselných hodnot.

- **Problematika spolupráce.** Pokud rozhraní s komponentami, které nejsou zapsány pro .NET Framework, například automatizace nebo objekty COM, pamatujte, že typy znaků mají v jiných prostředích jinou šířku dat (8 bitů). Pokud předáte 8bitovému argumentu takové součásti, deklarujte ji jako `Byte` místo `Char` v novém kódu Visual Basic.

- **Rozšiřující.** `Char` datový typ se rozšíří na `String`. To znamená, že můžete převést `Char` na `String` a nebude se nacházet <xref:System.OverflowException?displayProperty=nameWithType>.

- **Znaky typu.** Připojení znaku typu literálu `C` k řetězcovému literálu s jedním znakem je vynutí `Char` datový typ. `Char` nemá žádný znak typu identifikátoru.

- **Typ rozhraní.** Odpovídající typ v .NET Framework je struktura <xref:System.Char?displayProperty=nameWithType>.

## <a name="see-also"></a>Viz také:

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Datový typ String](../../../visual-basic/language-reference/data-types/string-data-type.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
