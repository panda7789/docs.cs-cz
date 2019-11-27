---
title: Mod – operátor
ms.date: 04/24/2018
f1_keywords:
- vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
ms.openlocfilehash: b7552550d4b0496d6ad7ee76a7327054d544b874
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350921"
---
# <a name="mod-operator-visual-basic"></a>Mod – operátor (Visual Basic)

Vydělí dvě čísla a vrátí pouze zbytek.

## <a name="syntax"></a>Syntaxe

```vb
result = number1 Mod number2
```

## <a name="parts"></a>Součásti

`result` \
Požadováno. Jakákoli číselná proměnná nebo vlastnost.

`number1` \
Požadováno. Libovolný číselný výraz.

`number2` \
Požadováno. Libovolný číselný výraz.

## <a name="supported-types"></a>Podporované typy

Všechny číselné typy. To zahrnuje typy bez znaménka a typy s plovoucí desetinnou čárkou a `Decimal`.

## <a name="result"></a>Výsledek

Výsledek je zbytek po `number1` dělený `number2`. Výraz `14 Mod 4` například vyhodnotí jako 2.

> [!NOTE]
> Existuje rozdíl mezi *zbytkem* a *modulem* v matematice s různými výsledky pro záporná čísla. Operátor `Mod` v Visual Basic, operátor .NET Framework `op_Modulus` a podkladová instrukce [rem](<xref:System.Reflection.Emit.OpCodes.Rem>) Il provádí zbývající operaci.

Výsledkem operace `Mod` zůstává zachováno znaménko dividendy, `number1`a tak může být kladné nebo záporné. Výsledek je vždy v rozsahu (-`number2`, `number2`), exkluzivní. Příklad:

```vb
Public Module Example
   Public Sub Main()
      Console.WriteLine($" 8 Mod  3 = {8 Mod 3}")
      Console.WriteLine($"-8 Mod  3 = {-8 Mod 3}")
      Console.WriteLine($" 8 Mod -3 = {8 Mod -3}")
      Console.WriteLine($"-8 Mod -3 = {-8 Mod -3}")
   End Sub
End Module
' The example displays the following output:
'       8 Mod  3 = 2
'      -8 Mod  3 = -2
'       8 Mod -3 = 2
'      -8 Mod -3 = -2
```

## <a name="remarks"></a>Poznámky

Je-li hodnota `number1` nebo `number2` typu s plovoucí desetinnou čárkou, bude vrácena část dělení s plovoucí desetinnou čárkou. Datový typ výsledku je nejmenší datový typ, který může uchovávat všechny možné hodnoty, které jsou výsledkem dělení s datovými typy `number1` a `number2`.

Pokud se `number1` nebo `number2` vyhodnotí jako [Nothing](../../../visual-basic/language-reference/nothing.md), bude se jednat o nulu.

Mezi související operátory patří následující:

- [Operátor \ (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) vrátí celočíselnou podíl dělení. Výraz `14 \ 4` například vyhodnotí na 3.

- [Operátor/(Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) vrátí úplný podíl včetně zbytku jako čísla s plovoucí desetinnou čárkou. Výraz `14 / 4` například vyhodnotí jako 3,5.

## <a name="attempted-division-by-zero"></a>Došlo k pokusu o dělení nulou.

Pokud je `number2` vyhodnocen jako nula, chování operátoru `Mod` závisí na datovém typu operandů:

- Celočíselné dělení vyvolá výjimku <xref:System.DivideByZeroException>, pokud `number2` nelze určit v době kompilace a generuje chybu při kompilaci `BC30542 Division by zero occurred while evaluating this expression` Pokud je `number2` v době kompilace vyhodnocen jako nula.
- Dělení s plovoucí desetinnou čárkou vrací <xref:System.Double.NaN?displayProperty=nameWithType>.

## <a name="equivalent-formula"></a>Ekvivalentní vzorec

Výraz `a Mod b` je ekvivalentem některého z následujících vzorců:

`a - (b * (a \ b))`

`a - (b * Fix(a / b))`

## <a name="floating-point-imprecision"></a>Nepřesnost plovoucí desetinné čárky

Když pracujete s čísly s plovoucí desetinnou čárkou, mějte na paměti, že v paměti nemají vždy přesné desetinné vyjádření. To může vést k neočekávaným výsledkům z určitých operací, jako je například porovnání hodnot a operátor `Mod`. Další informace najdete v tématu [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).

## <a name="overloading"></a>Přetížení

Operátor `Mod` může být *přetížen*, což znamená, že třída nebo struktura může předefinovat chování. Pokud je váš kód použit `Mod` na instanci třídy nebo struktury, která obsahuje takové přetížení, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).

## <a name="example"></a>Příklad

Následující příklad používá operátor `Mod` k rozdělení dvou čísel a vrácení pouze zbytku. Pokud je jedno číslo číslo s plovoucí desetinnou čárkou, výsledkem je číslo s plovoucí desetinnou čárkou, které představuje zbytek.

[!code-vb[VbVbalrOperators#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#31)]

## <a name="example"></a>Příklad

Následující příklad ukazuje potenciální nepřesnost operandů s plovoucí desetinnou čárkou. V prvním příkazu jsou operandy `Double`a 0,2 je nekonečně opakující se binární zlomek s uloženou hodnotou 0.20000000000000001. Ve druhém příkazu, znak typu literálu `D` vynutí `Decimal`operandy a 0,2 má přesnou reprezentaci.

[!code-vb[VbVbalrOperators#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#32)]

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Aritmetické operátory v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [\ – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
