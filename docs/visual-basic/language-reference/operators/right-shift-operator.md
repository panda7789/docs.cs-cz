---
title: '>> – Operátor (Visual Basic)'
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
ms.openlocfilehash: 8803dc2e25edde756958a243d429dd30c5c78bcf
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816964"
---
# <a name="-operator-visual-basic"></a>>> – Operátor (Visual Basic)
Provede aritmetický posunutí doprava bitový vzor.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = pattern >> amount  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Povinný parametr. Integrální číselné hodnoty. Výsledek posunu bitový vzor. Datový typ je stejné jako u `pattern`.  
  
 `pattern`  
 Povinný parametr. Integrální číselný výraz. Bitový vzor posunutí. Datový typ musí být celočíselného typu (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, nebo `ULong`).  
  
 `amount`  
 Povinný parametr. Číselný výraz. Počet bitů, chcete-li posunout bitový vzor. Datový typ musí být `Integer` nebo rozšířit na `Integer`.  
  
## <a name="remarks"></a>Poznámky  
 Aritmetické staffhubu nejsou cyklické, což znamená, že nejsou na druhém konci znovuzavedeno bity posunuly jeden konec výsledek. V aritmetické posunutí doprava bity posunuta nad rámec úplně vpravo bitová pozice se zahodí a bit nejvíce vlevo (sign) je postoupena do bitové pozice uvolněné na levé straně. To znamená, že pokud `pattern` má zápornou hodnotu uvolněných pozic jsou nastavené na jednu; v opačném případě jsou nastaveny na hodnotu nula.  
  
 Všimněte si, že datové typy, které `Byte`, `UShort`, `UInteger`, a `ULong` jsou bez znaménka, takže neexistuje žádný bit znaménka rozšíření. Pokud `pattern` je některý typ bez znaménka, uvolněných pozic jsou vždy nastaveny na hodnotu nula.  
  
 Aby posunutí ve více bitů než výsledek může obsahovat jazyka Visual Basic zakrývá hodnotu `amount` s maskou velikost odpovídající datový typ `pattern`. Binární a tyto hodnoty se používá pro hodnota shift. Velikost masky jsou následující:  
  
|Datový typ `pattern`|Maska velikost (decimální)|Maska velikost (v šestnáctkové hodnotě)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&H00000007|  
|`Short`, `UShort`|15|&H0000000F|  
|`Integer`, `UInteger`|31|&H0000001F|  
|`Long`, `ULong`|63|&H0000003F|  
  
 Pokud `amount` je nula, hodnota `result` je stejná jako hodnota `pattern`. Pokud `amount` je záporný, je provedena jako hodnoty bez znaménka a maskována pomocí masky odpovídající velikost.  
  
 Aritmetické staffhubu nikdy generovat výjimky přetečení.  
  
## <a name="overloading"></a>Přetížení  
 `>>` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře. Pokud váš kód používá tento operátor na takové třídy nebo struktury, ujistěte se, že rozumíte jeho Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `>>` operátor aritmetické posuny doprava na integrální hodnoty. Výsledek je vždy stejný datový typ jako, který se posune výrazu.  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 Výsledky v předchozím příkladu jsou následující:  
  
-   `result1` is 2560 (0000 1010 0000 0000).  
  
-   `result2` je 160 (0000 0000 1010 0000).  
  
-   `result3` is 2 (0000 0000 0000 0010).  
  
-   `result4` is 640 (0000 0010 1000 0000).  
  
-   `result5` je 0 (posunuté 15 míst napravo).  
  
 Hodnota shift pro `result4` se vypočte takto: 18 a 15, které se rovná 2.  
  
 Následující příklad ukazuje aritmetické staffhubu na zápornou hodnotu.  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 Výsledky v předchozím příkladu jsou následující:  
  
-   `negresult1` is -512 (1111 1110 0000 0000).  
  
-   `negresult2` je -1 (rozšířeno na bit znaménka).  
  
## <a name="see-also"></a>Viz také:

- [Operátory bitového posunu](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [>>= – operátor](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)
- [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Aritmetické operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
