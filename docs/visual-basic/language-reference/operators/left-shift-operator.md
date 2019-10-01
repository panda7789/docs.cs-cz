---
title: Operátor < < (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: 1300ab60e825e7910825be2c65dcab90135ba988
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701116"
---
# <a name="-operator-visual-basic"></a>Operátor \< @ no__t-1 (Visual Basic)
Provede aritmetický levý posun na bitový vzorek.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = pattern << amount  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Požadováno. Integrální číselná hodnota. Výsledek posunu bitového vzoru. Datový typ je stejný jako u `pattern`.  
  
 `pattern`  
 Požadováno. Integrální číselný výraz. Bitový vzorek, který se má posunout. Datový typ musí být integrální typ (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long` nebo `ULong`).  
  
 `amount`  
 Požadováno. Číselný výraz. Počet bitů pro posunutí bitového vzoru. Datový typ musí být `Integer` nebo rozšířit na `Integer`.  
  
## <a name="remarks"></a>Poznámky  
 Aritmetické posuny nejsou cyklické, což znamená, že bity posunuté o jeden konec výsledku nejsou znovu zavedeny na druhém konci. V aritmetickém levém Shift se bity, které přesahují rozsah výsledných dat, zahodí a bitové pozice uvolněné na pravé straně mají nastavenou hodnotu nula.  
  
 Chcete-li zabránit posunu více bitů, než je výsledek, Visual Basic, maskuje hodnotu `amount` s maskou velikosti, která odpovídá datovému typu `pattern`. Binární soubor a tyto hodnoty se použijí pro velikost Shift. Masky velikosti jsou následující:  
  
|Datový typ `pattern`|Velikost – maska (desítková)|Velikost – maska (šestnáctkově)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|čl|& H00000007|  
|`Short`, `UShort`|15|& H0000000F|  
|`Integer`, `UInteger`|čl|& H0000001F|  
|`Long`, `ULong`|63|& H0000003F|  
  
 Pokud je `amount` nula, hodnota `result` je shodná s hodnotou `pattern`. Je-li hodnota `amount` záporná, je převedena jako hodnota bez znaménka a maskována odpovídající maskou velikosti.  
  
 Aritmetické posuny nikdy negenerují výjimky přetečení.  
  
> [!NOTE]
> Operátor `<<` lze přetížit, což znamená, že třída nebo struktura může předefinovat *chování, pokud*operand má typ této třídy nebo struktury. Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je použit operátor `<<` pro provádění aritmetických posunutí doleva u celočíselných hodnot. Výsledek má vždycky stejný datový typ jako výraz, který se posouvá.  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 Výsledky předchozího příkladu jsou následující:  
  
- `result1` je 192 (0000 0000 1100 0000).  
  
- `result2` je 3072 (0000 1100 0000 0000).  
  
- `result3` je-32768 (1000 0000 0000 0000).  
  
- `result4` je 384 (0000 0001 1000 0000).  
  
- `result5` je 0 (posun 15 míst doleva).  
  
 Hodnota SHIFT pro `result4` se počítá jako 17 a 15, což se rovná 1.  
  
## <a name="see-also"></a>Viz také:

- [Operátory bitového posunu](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operátor <<=](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Aritmetické operátory v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
