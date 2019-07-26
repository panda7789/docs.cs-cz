---
title: Char – datový typ (Visual Basic)
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
ms.openlocfilehash: ca40e6c8dcba3da29bdb68b29c91c852e477f8f7
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512794"
---
# <a name="char-data-type-visual-basic"></a>Char – datový typ (Visual Basic)

Obsahuje nepodepsaný 16bitový (2 bajt) body kódu v rozsahu od 0 do 65535. Každý *bod kódu*nebo kód znaku představuje jeden znak Unicode.

## <a name="remarks"></a>Poznámky

Datový typ `Char` použijte v případě, že potřebujete držet jenom jeden znak a nemusíte mít `String`režii. V některých případech můžete použít `Char()` `Char` pole prvků pro uložení více znaků.

Výchozí hodnota `Char` je znak s bodem kódu 0.

## <a name="unicode-characters"></a>Znaky Unicode

Prvních 128 kódových bodů (0 – 127) Unicode odpovídá písmenům a symbolům na standardní americké klávesnici. Tyto první body kódu 128 jsou stejné jako ty, které definuje znaková sada ASCII. Druhý bod kódu 128 (128 – 255) představuje speciální znaky, jako jsou písmena abecedy založená na latince, zvýraznění, symboly měn a zlomky. Kódování Unicode používá zbývající body kódu (256-65535) pro širokou škálu symbolů, včetně celosvětových textových znaků, diakritických znamének a matematických a technických symbolů.

K určení klasifikace Unicode můžete <xref:System.Char.IsDigit%2A> použít <xref:System.Char.IsPunctuation%2A> metody jako `Char` a na proměnné.

## <a name="type-conversions"></a>Převody typu

Visual Basic nepřevádí přímo mezi `Char` a číselnými typy. Můžete použít <xref:Microsoft.VisualBasic.Strings.Asc%2A> funkci nebo <xref:Microsoft.VisualBasic.Strings.AscW%2A> `Char` pro`Integer` převod hodnoty na, která představuje jeho bod kódu. Můžete použít <xref:Microsoft.VisualBasic.Strings.Chr%2A> funkci nebo <xref:Microsoft.VisualBasic.Strings.ChrW%2A> `Integer` pro`Char` převod hodnoty na, která má tento kódový bod.

Pokud je zapnut přepínač pro kontrolu typu ([příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)), je nutné připojit znak literálového typu k řetězcovému literálu s jedním znakem, aby byl `Char` identifikován jako datový typ. Toto dokládá následující příklad.

```vb
Option Strict On
Dim charVar As Char
' The following statement attempts to convert a String literal to Char.
' Because Option Strict is On, it generates a compiler error.
charVar = "Z"
' The following statement succeeds because it specifies a Char literal.
charVar = "Z"C
```

## <a name="programming-tips"></a>Tipy k programování

- **Záporná čísla.** `Char`je typ bez znaménka a nemůže představovat zápornou hodnotu. V žádném případě byste neměli používat `Char` k ukládání číselných hodnot.

- **Problematika spolupráce.** Pokud rozhraní s komponentami, které nejsou zapsány pro .NET Framework, například automatizace nebo objekty COM, pamatujte, že typy znaků mají v jiných prostředích jinou šířku dat (8 bitů). Pokud předáte 8bitovému argumentu takové součásti, deklarujte ji jako `Byte` `Char` místo v novém Visual Basic kódu.

- **Rozšiřující.** Datový typ se rozšíří na `String`. `Char` To znamená, že můžete `Char` převést `String` na a nemůžete <xref:System.OverflowException?displayProperty=nameWithType> se setkat s chybou.

- **Znaky typu.** Připojení znaku `C` literálového typu k řetězcovému literálu s jedním znakem vynutí `Char` datový typ. `Char`nemá žádný znak typu identifikátoru.

- **Typ rozhraní.** Odpovídající typ v .NET Framework je <xref:System.Char?displayProperty=nameWithType> struktura.

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
- [Postupy: Volání funkce Windows, která přebírá typy bez znaménka](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
