---
title: Mod – operátor (Visual Basic)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5120823f4e001fc3aff71f267176311e2465597a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="mod-operator-visual-basic"></a>Mod – operátor (Visual Basic)
Provede podíl dvou čísel a vrátí pouze zbytek.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
number1 Mod number2  
```  
  
## <a name="parts"></a>Součásti  
 `number1`  
 Požadováno. Jakýkoli číselný výraz.  
  
 `number2`  
 Požadováno. Jakýkoli číselný výraz.  
  
## <a name="supported-types"></a>Podporované typy  
 Všechny číselné typy. To zahrnuje typy bez znaménka a s plovoucí desetinnou čárkou a `Decimal`.  
  
## <a name="result"></a>Výsledek

Výsledkem je zbývající po `number1` dělení `number2`. Například výraz `14 Mod 4` vyhodnotí 2.  

> [!NOTE]
> Existuje rozdíl mezi *zbývající* a *numerického zbytku* v Matematika s odlišné výsledky pro záporná čísla. `Mod` Operátor v jazyce Visual Basic, rozhraní .NET Framework `op_Modulus` operátor a základní [rem]<xref:System.Reflection.Emit.OpCodes.Rem> IL instrukce všechny zbývající operaci provést.

Výsledek `Mod` operaci uchovává přihlašovací dělenec, `number1`, a proto může být kladná nebo záporná. Výsledkem je vždy v rozsahu (-`number2`, `number2`), výhradní. Příklad:

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
 Pokud má jedna `number1` nebo `number2` je hodnota s plovoucí desetinnou čárkou se vrátí zbytek divizi s plovoucí desetinnou čárkou. Datový typ výsledku je nejmenší datový typ, který může obsahovat všechny možné hodnoty, které jsou výsledkem dělení s typy dat `number1` a `number2`.  
  
 Pokud `number1` nebo `number2` vyhodnotí jako [nic](../../../visual-basic/language-reference/nothing.md), je považován za nula.  
  
 Související operátory zahrnují následující:  
  
-   [\ – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) vrátí celočíselný koeficient dělení. Například výraz `14 \ 4` vyhodnocen jako 3.  
  
-   [/ – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) vrátí úplné podílu, včetně zbývající, jako číslo s plovoucí desetinnou čárkou. Například výraz `14 / 4` vyhodnocuje 3.5.  
  
## <a name="attempted-division-by-zero"></a>Pokus o dělení nulou  
 Pokud `number2` vyhodnocen jako nula, chování `Mod` operátor závisí na typu dat operandy. Vyvolá celočíselné dělení <xref:System.DivideByZeroException> výjimka. Vrátí s plovoucí desetinnou čárkou dělení <xref:System.Double.NaN>.  
  
## <a name="equivalent-formula"></a>Ekvivalentní vzorec  
 Výraz `a Mod b` odpovídá buď následující vzorce:  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## <a name="floating-point-imprecision"></a>S plovoucí desetinnou čárkou nepřesnosti  
 Při práci s plovoucí desetinnou čárkou, mějte na paměti, že vždy nemají přesné decimal reprezentace v paměti. To může vést k neočekávaným výsledkům z určité operace, jako je například porovnání hodnoty a `Mod` operátor. Další informace najdete v tématu [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="overloading"></a>Přetížení  
 `Mod` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování. Pokud se váš kód vztahuje `Mod` na instanci třídy nebo struktura, která zahrnuje tyto přetížení se rozumět své Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Mod` operátor dělení dvou čísel a vrátí pouze zbytek. Pokud je buď číslo s plovoucí desetinnou čárkou číslo, výsledkem je číslo s plovoucí desetinnou čárkou, které představuje zbytek.  
  
 [!code-vb[VbVbalrOperators#31](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_1.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje potenciální nepřesnosti operandů s plovoucí desetinnou čárkou. V prvním příkazu, jsou operandy `Double`, a 0,2 nekonečnou opakovaný binární zlomek s hodnotou uloženou 0.20000000000000001. Literálové druhý příkaz, zadejte znak `D` vynutí oba operandy k `Decimal`, a 0,2 má znázornění přesné.  
  
 [!code-vb[VbVbalrOperators#32](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>  
 [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Aritmetické operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [\ – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
