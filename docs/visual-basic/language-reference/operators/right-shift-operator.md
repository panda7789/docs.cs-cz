---
title: '>> Operátor'
ms.date: 07/20/2015
f1_keywords:
- vb.>>
helpviewer_keywords:
- operator>>
- '>> operator [Visual Basic]'
- bit shift operators [Visual Basic]
- operator >>
- right shift operators [Visual Basic]
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
ms.openlocfilehash: 10b07da22b8b43d6a966fa7c334ac6a0ef4b430d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406363"
---
# <a name="-operator-visual-basic"></a>Operátor >> (Visual Basic)
Provede aritmetický pravý posun na bitový vzorek.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = pattern >> amount  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Povinná hodnota. Integrální číselná hodnota. Výsledek posunu bitového vzoru. Datový typ je stejný jako u `pattern` .  
  
 `pattern`  
 Povinná hodnota. Integrální číselný výraz. Bitový vzorek, který se má posunout. Datový typ musí být integrální typ ( `SByte` , `Byte` , `Short` , `UShort` , `Integer` , `UInteger` , `Long` , nebo `ULong` ).  
  
 `amount`  
 Povinná hodnota. Číselný výraz. Počet bitů pro posunutí bitového vzoru. Datový typ musí být `Integer` nebo rozšířit na `Integer` .  
  
## <a name="remarks"></a>Poznámky  
 Aritmetické posuny nejsou cyklické, což znamená, že bity posunuté o jeden konec výsledku nejsou znovu zavedeny na druhém konci. V aritmetickém pravém posunu se bity, které přesahují napravo od pozice vpravo, zahodí a bit úplně vlevo (znaménko) se rozšíří do bitových pozic uvolněné vlevo. To znamená, že pokud `pattern` má zápornou hodnotu, pozice uvolněné jsou nastaveny na jednu; v opačném případě jsou nastaveny na hodnotu nula.  
  
 Všimněte si, že datové typy `Byte` , `UShort` , `UInteger` a `ULong` jsou bez znaménka, takže neexistuje bit znaménka pro rozšíření. Pokud `pattern` je jakýkoli typ bez znaménka, pozice uvolněné jsou vždy nastaveny na hodnotu nula.  
  
 Aby nedocházelo k posunu více bitů, než může výsledek uchovávat, Visual Basic maskuje hodnotu `amount` s maskou velikosti odpovídající datovému typu `pattern` . Binární soubor a tyto hodnoty se použijí pro velikost Shift. Masky velikosti jsou následující:  
  
|Datový typ`pattern`|Velikost – maska (desítková)|Velikost – maska (šestnáctkově)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&H00000007|  
|`Short`, `UShort`|15|&H0000000F|  
|`Integer`, `UInteger`|31|&H0000001F|  
|`Long`, `ULong`|63|&H0000003F|  
  
 Pokud `amount` je nula, hodnota `result` je shodná s hodnotou `pattern` . Pokud `amount` je záporná, je pořízena jako hodnota bez znaménka a maskována odpovídající maskou velikosti.  
  
 Aritmetické posuny nikdy negenerují výjimky přetečení.  
  
## <a name="overloading"></a>Přetížení  
 `>>`Operátor může být *přetížen*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury. Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `>>` operátor k provádění aritmetických pravých posunů u integrálních hodnot. Výsledek má vždycky stejný datový typ jako výraz, který se posouvá.  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 Výsledky předchozího příkladu jsou následující:  
  
- `result1`je 2560 (0000 1010 0000 0000).  
  
- `result2`je 160 (0000 0000 1010 0000).  
  
- `result3`je 2 (0000 0000 0000 0010).  
  
- `result4`je 640 (0000 0010 1000 0000).  
  
- `result5`je 0 (posun 15 míst doprava).  
  
 Hodnota posunu pro `result4` se počítá jako 18 a 15, což se rovná 2.  
  
 Následující příklad ukazuje aritmetické posuny na zápornou hodnotu.  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 Výsledky předchozího příkladu jsou následující:  
  
- `negresult1`je-512 (1111 1110 0000 0000).  
  
- `negresult2`je-1 (bit znaménka je šířen).  
  
## <a name="see-also"></a>Viz také

- [Operátory bitového posunu](bit-shift-operators.md)
- [Operátory přiřazení](assignment-operators.md)
- [>>= – operátor](right-shift-assignment-operator.md)
- [Priorita operátorů v jazyce Visual Basic](operator-precedence.md)
- [Operátory uvedené podle funkce](operators-listed-by-functionality.md)
- [Aritmetické operátory v jazyce Visual Basic](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
