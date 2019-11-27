---
title: << – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: 327d0e5cbd1ebcc43bd47fb068f4513940c2165a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350985"
---
# <a name="-operator-visual-basic"></a>Operátor \<\< (Visual Basic)
Provede aritmetický levý posun na bitový vzorek.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = pattern << amount  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Požadováno. Integrální číselná hodnota. Výsledek posunu bitového vzoru. Datový typ je stejný jako u `pattern`.  
  
 `pattern`  
 Požadováno. Integrální číselný výraz. Bitový vzorek, který se má posunout. Datový typ musí být integrální typ (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`nebo `ULong`).  
  
 `amount`  
 Požadováno. Číselný výraz. Počet bitů pro posunutí bitového vzoru. Datový typ musí být `Integer` nebo se rozšířit na `Integer`.  
  
## <a name="remarks"></a>Poznámky  
 Aritmetické posuny nejsou cyklické, což znamená, že bity posunuté o jeden konec výsledku nejsou znovu zavedeny na druhém konci. V aritmetickém levém Shift se bity, které přesahují rozsah výsledných dat, zahodí a bitové pozice uvolněné na pravé straně mají nastavenou hodnotu nula.  
  
 Aby se zabránilo posunu více bitů, než je výsledek, Visual Basic maskuje hodnotu `amount` s maskou velikosti, která odpovídá datovému typu `pattern`. Binární soubor a tyto hodnoty se použijí pro velikost Shift. Masky velikosti jsou následující:  
  
|Datový typ `pattern`|Velikost – maska (desítková)|Velikost – maska (šestnáctkově)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte``Byte`|7|&H00000007|  
|`Short``UShort`|15|&H0000000F|  
|`Integer``UInteger`|31|&H0000001F|  
|`Long``ULong`|63|&H0000003F|  
  
 Pokud je `amount` nula, hodnota `result` je shodná s hodnotou `pattern`. Pokud je `amount` záporné, je převedena jako hodnota bez znaménka a s maskou odpovídající velikosti.  
  
 Aritmetické posuny nikdy negenerují výjimky přetečení.  
  
> [!NOTE]
> Operátor `<<` lze přetížit, což znamená, že třída nebo struktura může předefinovat své *chování, pokud*má operand typ této třídy nebo struktury. Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá operátor `<<` k provádění aritmetických posunů v celočíselných hodnotách. Výsledek má vždycky stejný datový typ jako výraz, který se posouvá.  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 Výsledky předchozího příkladu jsou následující:  
  
- `result1` je 192 (0000 0000 1100 0000).  
  
- `result2` je 3072 (0000 1100 0000 0000).  
  
- `result3` je-32768 (1000 0000 0000 0000).  
  
- `result4` je 384 (0000 0001 1000 0000).  
  
- `result5` je 0 (přesune se na 15 míst vlevo).  
  
 Velikost posunutí pro `result4` se počítá jako 17 a 15, což se rovná 1.  
  
## <a name="see-also"></a>Viz také:

- [Operátory bitového posunu](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<<= – operátor](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Aritmetické operátory v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
