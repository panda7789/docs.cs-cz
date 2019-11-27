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
ms.openlocfilehash: cabf8c569435cc0fc98282f5e8f5fd410e6708dc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347824"
---
# <a name="-operator-visual-basic"></a>Operátor > > (Visual Basic)
Provede aritmetický pravý posun na bitový vzorek.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = pattern >> amount  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Požadováno. Integrální číselná hodnota. Výsledek posunu bitového vzoru. Datový typ je stejný jako u `pattern`.  
  
 `pattern`  
 Požadováno. Integrální číselný výraz. Bitový vzorek, který se má posunout. Datový typ musí být integrální typ (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`nebo `ULong`).  
  
 `amount`  
 Požadováno. Číselný výraz. Počet bitů pro posunutí bitového vzoru. Datový typ musí být `Integer` nebo se rozšířit na `Integer`.  
  
## <a name="remarks"></a>Poznámky  
 Aritmetické posuny nejsou cyklické, což znamená, že bity posunuté o jeden konec výsledku nejsou znovu zavedeny na druhém konci. V aritmetickém pravém posunu se bity, které přesahují napravo od pozice vpravo, zahodí a bit úplně vlevo (znaménko) se rozšíří do bitových pozic uvolněné vlevo. To znamená, že pokud má `pattern` zápornou hodnotu, pozice uvolněné se nastaví na hodnotu jedna; v opačném případě jsou nastaveny na hodnotu nula.  
  
 Všimněte si, že datové typy `Byte`, `UShort`, `UInteger`a `ULong` jsou bez znaménka, takže není k dispozici žádný bit znaménka pro rozšíření. Pokud je `pattern` libovolného typu bez znaménka, pozice uvolněné se vždycky nastaví na hodnotu nula.  
  
 Aby nedocházelo k posunu více bitů, než může výsledek uchovávat, Visual Basic maskuje hodnotu `amount` s maskou velikosti odpovídající datovému typu `pattern`. Binární soubor a tyto hodnoty se použijí pro velikost Shift. Masky velikosti jsou následující:  
  
|Datový typ `pattern`|Velikost – maska (desítková)|Velikost – maska (šestnáctkově)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte``Byte`|7|&H00000007|  
|`Short``UShort`|15|&H0000000F|  
|`Integer``UInteger`|31|&H0000001F|  
|`Long``ULong`|63|&H0000003F|  
  
 Pokud je `amount` nula, hodnota `result` je shodná s hodnotou `pattern`. Pokud je `amount` záporné, je převedena jako hodnota bez znaménka a s maskou odpovídající velikosti.  
  
 Aritmetické posuny nikdy negenerují výjimky přetečení.  
  
## <a name="overloading"></a>Přetížení  
 Operátor `>>` lze přetížit, což znamená, že třída nebo struktura může předefinovat své *chování, pokud*má operand typ této třídy nebo struktury. Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá operátor `>>` k provádění aritmetických pravých posunů u integrálních hodnot. Výsledek má vždycky stejný datový typ jako výraz, který se posouvá.  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 Výsledky předchozího příkladu jsou následující:  
  
- `result1` je 2560 (0000 1010 0000 0000).  
  
- `result2` je 160 (0000 0000 1010 0000).  
  
- `result3` je 2 (0000 0000 0000 0010).  
  
- `result4` je 640 (0000 0010 1000 0000).  
  
- `result5` je 0 (posun 15 míst doprava).  
  
 Velikost posunutí pro `result4` se počítá jako 18 a 15, což se rovná 2.  
  
 Následující příklad ukazuje aritmetické posuny na zápornou hodnotu.  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 Výsledky předchozího příkladu jsou následující:  
  
- `negresult1` je-512 (1111 1110 0000 0000).  
  
- `negresult2` je-1 (bit znaménka je šířen).  
  
## <a name="see-also"></a>Viz také:

- [Operátory bitového posunu](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [>>= – operátor](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Aritmetické operátory v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
