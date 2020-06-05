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
ms.openlocfilehash: 1128b32a739e7dbf3893dcd19b37247cd4643c85
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370632"
---
# <a name="-operator-visual-basic"></a>\<\<– Operátor (Visual Basic)
Provede aritmetický levý posun na bitový vzorek.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = pattern << amount  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Povinná hodnota. Integrální číselná hodnota. Výsledek posunu bitového vzoru. Datový typ je stejný jako u `pattern` .  
  
 `pattern`  
 Povinná hodnota. Integrální číselný výraz. Bitový vzorek, který se má posunout. Datový typ musí být integrální typ ( `SByte` , `Byte` , `Short` , `UShort` , `Integer` , `UInteger` , `Long` , nebo `ULong` ).  
  
 `amount`  
 Povinná hodnota. Číselný výraz. Počet bitů pro posunutí bitového vzoru. Datový typ musí být `Integer` nebo rozšířit na `Integer` .  
  
## <a name="remarks"></a>Poznámky  
 Aritmetické posuny nejsou cyklické, což znamená, že bity posunuté o jeden konec výsledku nejsou znovu zavedeny na druhém konci. V aritmetickém levém Shift se bity, které přesahují rozsah výsledných dat, zahodí a bitové pozice uvolněné na pravé straně mají nastavenou hodnotu nula.  
  
 Aby se zabránilo posunu více bitů, než je výsledek, Visual Basic maskuje hodnotu `amount` s maskou velikosti, která odpovídá datovému typu `pattern` . Binární soubor a tyto hodnoty se použijí pro velikost Shift. Masky velikosti jsou následující:  
  
|Datový typ`pattern`|Velikost – maska (desítková)|Velikost – maska (šestnáctkově)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&H00000007|  
|`Short`, `UShort`|15|&H0000000F|  
|`Integer`, `UInteger`|31|&H0000001F|  
|`Long`, `ULong`|63|&H0000003F|  
  
 Pokud `amount` je nula, hodnota `result` je shodná s hodnotou `pattern` . Pokud `amount` je záporná, je pořízena jako hodnota bez znaménka a maskována odpovídající maskou velikosti.  
  
 Aritmetické posuny nikdy negenerují výjimky přetečení.  
  
> [!NOTE]
> `<<`Operátor může být *přetížen*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury. Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `<<` operátor k provádění aritmetických operací doleva u integrálních hodnot. Výsledek má vždycky stejný datový typ jako výraz, který se posouvá.  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 Výsledky předchozího příkladu jsou následující:  
  
- `result1`je 192 (0000 0000 1100 0000).  
  
- `result2`je 3072 (0000 1100 0000 0000).  
  
- `result3`je-32768 (1000 0000 0000 0000).  
  
- `result4`je 384 (0000 0001 1000 0000).  
  
- `result5`je 0 (posun 15 míst doleva).  
  
 Hodnota posunu pro `result4` se počítá jako 17 a 15, což se rovná 1.  
  
## <a name="see-also"></a>Viz také

- [Operátory bitového posunu](bit-shift-operators.md)
- [Operátory přiřazení](assignment-operators.md)
- [<<= – operátor](left-shift-assignment-operator.md)
- [Priorita operátorů v jazyce Visual Basic](operator-precedence.md)
- [Operátory uvedené podle funkce](operators-listed-by-functionality.md)
- [Aritmetické operátory v jazyce Visual Basic](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
