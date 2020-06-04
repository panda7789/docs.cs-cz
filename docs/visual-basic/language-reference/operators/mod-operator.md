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
ms.openlocfilehash: 32065567799b023556a018ae2f5ba338796e0b49
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401508"
---
# <a name="mod-operator-visual-basic"></a>Mod – operátor (Visual Basic)

Vydělí dvě čísla a vrátí pouze zbytek.

## <a name="syntax"></a>Syntaxe

```vb
result = number1 Mod number2
```

## <a name="parts"></a>Součásti

`result` \
Povinná hodnota. Jakákoli číselná proměnná nebo vlastnost.

`number1` \
Povinná hodnota. Libovolný číselný výraz.

`number2` \
Povinná hodnota. Libovolný číselný výraz.

## <a name="supported-types"></a>Podporované typy

Všechny číselné typy. To zahrnuje typy unsigned a float-Point a `Decimal` .

## <a name="result"></a>Výsledek

Výsledek je zbytek po `number1` dělení `number2` . Například výraz se `14 Mod 4` vyhodnotí jako 2.

> [!NOTE]
> Existuje rozdíl mezi *zbytkem* a *modulem* v matematice s různými výsledky pro záporná čísla. `Mod`Operátor v Visual Basic, `op_Modulus` operátor .NET Framework a podkladová instrukce [rem](<xref:System.Reflection.Emit.OpCodes.Rem>) Il provádí zbývající operaci.

Výsledkem `Mod` operace zůstane znaménko dividendy, `number1` , a tak může být kladné nebo záporné. Výsledek je vždy v rozsahu (- `number2` , `number2` ), exkluzivní. Příklad:

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

Pokud buď `number1` nebo je hodnota s plovoucí desetinnou čárkou `number2` , vrátí zbytek dělení plovoucí desetinné čárky. Datový typ výsledku je nejmenší datový typ, který může uchovávat všechny možné hodnoty, které jsou výsledkem dělení s datovými typy `number1` a `number2` .

Pokud `number1` je nebo se `number2` vyhodnotí jako [Nothing](../nothing.md), bude se zacházet jako nula.

Mezi související operátory patří následující:

- [Operátor \ (Visual Basic)](integer-division-operator.md) vrátí celočíselnou podíl dělení. Například výraz se `14 \ 4` vyhodnotí jako 3.

- [Operátor/(Visual Basic)](floating-point-division-operator.md) vrátí úplný podíl včetně zbytku jako čísla s plovoucí desetinnou čárkou. Například výraz se `14 / 4` vyhodnotí jako 3,5.

## <a name="attempted-division-by-zero"></a>Došlo k pokusu o dělení nulou.

Pokud je `number2` hodnota vyhodnocena jako nula, chování `Mod` operátoru závisí na datovém typu operandů:

- Celočíselné dělení vyvolá <xref:System.DivideByZeroException> výjimku, pokud `number2` nelze určit v době kompilace a generuje chybu při kompilaci, `BC30542 Division by zero occurred while evaluating this expression` Pokud `number2` je v době kompilace vyhodnocena jako nula.
- Dělení s plovoucí desetinnou čárkou se vrátí <xref:System.Double.NaN?displayProperty=nameWithType> .

## <a name="equivalent-formula"></a>Ekvivalentní vzorec

Výraz `a Mod b` je ekvivalentem některého z následujících vzorců:

`a - (b * (a \ b))`

`a - (b * Fix(a / b))`

## <a name="floating-point-imprecision"></a>Nepřesnost plovoucí desetinné čárky

Když pracujete s čísly s plovoucí desetinnou čárkou, mějte na paměti, že v paměti nemají vždy přesné desetinné vyjádření. To může vést k neočekávaným výsledkům z určitých operací, jako je například porovnání hodnot a `Mod` operátor. Další informace najdete v tématu [řešení potíží s datovými typy](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).

## <a name="overloading"></a>Přetížení

`Mod`Operátor může být *přetížen*, což znamená, že třída nebo struktura může změnit své chování. Pokud se váš kód vztahuje `Mod` na instanci třídy nebo struktury, která obsahuje takové přetížení, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).

## <a name="example"></a>Příklad

Následující příklad používá `Mod` operátor k rozdělení dvou čísel a vrácení pouze zbytku. Pokud je jedno číslo číslo s plovoucí desetinnou čárkou, výsledkem je číslo s plovoucí desetinnou čárkou, které představuje zbytek.

[!code-vb[VbVbalrOperators#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#31)]

## <a name="example"></a>Příklad

Následující příklad ukazuje potenciální nepřesnost operandů s plovoucí desetinnou čárkou. V prvním příkazu jsou operandy `Double` a 0,2 nekonečně opakující se binární zlomek s uloženou hodnotou 0.20000000000000001. Ve druhém příkazu vynucuje znak typu literálu `D` oba operandy `Decimal` a 0,2 má přesnou reprezentaci.

[!code-vb[VbVbalrOperators#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#32)]

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- [Aritmetické operátory](arithmetic-operators.md)
- [Priorita operátorů v jazyce Visual Basic](operator-precedence.md)
- [Operátory uvedené podle funkce](operators-listed-by-functionality.md)
- [Řešení potíží s datovými typy](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Aritmetické operátory v jazyce Visual Basic](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [\ – Operátor (Visual Basic)](integer-division-operator.md)
