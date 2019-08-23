---
title: Not – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
ms.openlocfilehash: 29e2b159e4c6261a62e788b537102b9b457fe0c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955821"
---
# <a name="not-operator-visual-basic"></a>Not – operátor (Visual Basic)
Provede logickou negaci `Boolean` výrazu nebo bitovou negaci číselného výrazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = Not expression  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Povinný parametr. Libovolný `Boolean` nebo numerický výraz.  
  
 `expression`  
 Povinný parametr. Libovolný `Boolean` nebo numerický výraz.  
  
## <a name="remarks"></a>Poznámky  
 V `Boolean` případě výrazů ukazuje následující tabulka, jak `result` je určena.  
  
|Pokud `expression` je|Hodnota `result` je|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 U numerických výrazů `Not` operátor obrátí bitové hodnoty libovolného číselného výrazu a nastaví odpovídající bit v `result` závislosti na následující tabulce.  
  
|Pokud je bit `expression` v|Bit v `result` je|  
|-------------------------------|----------------------------|  
|1|0|  
|0|1|  
  
> [!NOTE]
> Vzhledem k tomu, že logické a bitové operátory mají nižší prioritu než jiné aritmetické a relační operátory, měly by být všechny bitové operace uzavřeny v závorkách, aby bylo zajištěno přesné provedení.  
  
## <a name="data-types"></a>Datové typy  
 Pro logickou negaci je `Boolean`datový typ výsledku. Pro bitovou negaci je výsledný datový typ stejný jako `expression`u. Nicméně pokud je `Decimal`výraz, je `Long`výsledkem.  
  
## <a name="overloading"></a>Přetížení  
 Operátor může být přetížen, což znamená, že třída nebo struktura může předefinovat své chování, pokud má jeho operand typ této třídy nebo struktury. `Not` Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Not` operátor k provedení logické negace `Boolean` výrazu. Výsledkem je `Boolean` hodnota, která představuje obrácenou hodnotu výrazu.  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 Předchozí příklad vytvoří výsledky `False` a `True`v uvedeném pořadí.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Not` operátor k provedení logické negace jednotlivých bitů číselného výrazu. Bit ve vzorci výsledků je nastaven na zpětný výsledek odpovídajícího bitu ve vzoru operandu, včetně bitu znaménka.  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 Předchozí příklad vytvoří výsledky – 11, – 9 a – 7 v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také:

- [Logické/bitové operátory (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Logické a bitové operátory v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
