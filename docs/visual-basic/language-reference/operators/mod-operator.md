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
ms.openlocfilehash: 456c19fc8e28517a0662b58e338028e1c75cd8c8
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45585861"
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
 Všechny číselné typy. Jedná se o typy bez znaménka a s plovoucí desetinnou čárkou a `Decimal`.  
  
## <a name="result"></a>Výsledek

Výsledkem je zbytek po `number1` , je vyděleno hodnotou `number2`. Například výraz `14 Mod 4` vyhodnotí na 2.  

> [!NOTE]
> Existuje rozdíl mezi *zbývající* a *numerického zbytku* v matematice se různé výsledky pro záporná čísla. `Mod` Operátor v jazyce Visual Basic, rozhraní .NET Framework `op_Modulus` operátor a základní [rem](<xref:System.Reflection.Emit.OpCodes.Rem>) provádět všechny operace remainder instrukce IL.

Výsledek `Mod` operace uchovává znaménko podíl, `number1`, a proto může být pozitivní nebo negativní. Výsledek je vždycky v rozsahu (-`number2`, `number2`) exkluzivní. Příklad:

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
 Pokud `number1` nebo `number2` je hodnotu s plovoucí desetinnou čárkou se vrátí zbytek s plovoucí desetinnou čárkou dělení. Datový typ výsledku je nejmenší datový typ, který může uchovat všechny možné hodnoty, které jsou výsledkem dělení s datové typy `number1` a `number2`.  
  
 Pokud `number1` nebo `number2` vyhodnotí jako [nic](../../../visual-basic/language-reference/nothing.md), je považován za nulu.  
  
 Související operátory patří:  
  
-   [\ – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) vrátí podíl dělení celého čísla. Například výraz `14 \ 4` vyhodnocen jako 3.  
  
-   [/ – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) vrátí úplné podíl, včetně zbývající jako číslo s plovoucí desetinnou čárkou. Například výraz `14 / 4` vyhodnocen jako 3.5.  
  
## <a name="attempted-division-by-zero"></a>Pokus o dělení nulou  
 Pokud `number2` vyhodnocen jako nula, chování `Mod` operátor závisí na datový typ operandu. Vyvolá celočíselného dělení <xref:System.DivideByZeroException> výjimky. Vrátí hodnotu s plovoucí desetinnou čárkou dělení <xref:System.Double.NaN>.  
  
## <a name="equivalent-formula"></a>Ekvivalentní vzorce  
 Výraz `a Mod b` odpovídá některé z těchto vzorců:  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## <a name="floating-point-imprecision"></a>S plovoucí desetinnou čárkou nepřesnost  
 Při práci s čísly s plovoucí desetinnou čárkou, mějte na paměti, že vždy nemají reprezentaci přesné desítkové v paměti. To může vést k neočekávaným výsledkům z určité operace, jako je například porovnání hodnoty a `Mod` operátor. Další informace najdete v tématu [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="overloading"></a>Přetížení  
 `Mod` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování. Pokud se váš kód vztahuje `Mod` být do instance třídy nebo struktury, která obsahuje tato přetížení, že rozumíte jeho Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Mod` operátor dělení dvou čísel a vrátí pouze zbytek. Pokud je buď číslo s plovoucí desetinnou čárkou číslo, výsledkem je číslo s plovoucí desetinnou čárkou, které představuje zbytek.  
  
 [!code-vb[VbVbalrOperators#31](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_1.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje potenciál nepřesnost operandů s plovoucí desetinnou čárkou. V prvním příkazu, jsou jako operandy `Double`, a 0.2 je neomezeně opakovaný binární zlomek s hodnotou uloženou v 0.20000000000000001. V druhém příkazu znak typu literálu `D` vynutí oba operandy `Decimal`, a 0.2 má přesné reprezentaci.  
  
 [!code-vb[VbVbalrOperators#32](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_2.vb)]  
  
## <a name="see-also"></a>Viz také:  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>  
 [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Aritmetické operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [\ – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
