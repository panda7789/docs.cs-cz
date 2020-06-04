---
title: Not – operátor
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
ms.openlocfilehash: 56cdeb80a217dbce15921eddd6a43d8d1b049376
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401456"
---
# <a name="not-operator-visual-basic"></a>Not – operátor (Visual Basic)
Provede logickou negaci `Boolean` výrazu nebo bitovou negaci číselného výrazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = Not expression  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Povinná hodnota. Libovolný `Boolean` nebo numerický výraz.  
  
 `expression`  
 Povinná hodnota. Libovolný `Boolean` nebo numerický výraz.  
  
## <a name="remarks"></a>Poznámky  
 `Boolean`V případě výrazů ukazuje následující tabulka, jak `result` je určena.  
  
|Pokud `expression` je|Hodnota `result` je|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 U numerických výrazů `Not` operátor obrátí bitové hodnoty libovolného číselného výrazu a nastaví odpovídající bit v `result` závislosti na následující tabulce.  
  
|Pokud je bit v `expression`|Bit v `result` je|  
|-------------------------------|----------------------------|  
|1|0|  
|0|1|  
  
> [!NOTE]
> Vzhledem k tomu, že logické a bitové operátory mají nižší prioritu než jiné aritmetické a relační operátory, měly by být všechny bitové operace uzavřeny v závorkách, aby bylo zajištěno přesné provedení.  
  
## <a name="data-types"></a>Typy dat  
 Pro logickou negaci je datový typ výsledku `Boolean` . Pro bitovou negaci je výsledný datový typ stejný jako u `expression` . Nicméně pokud je výraz `Decimal` , je výsledkem `Long` .  
  
## <a name="overloading"></a>Přetížení  
 `Not`Operátor může být *přetížen*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má jeho operand typ této třídy nebo struktury. Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Not` operátor k provedení logické negace `Boolean` výrazu. Výsledkem je `Boolean` hodnota, která představuje obrácenou hodnotu výrazu.  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 Předchozí příklad vytvoří výsledky a v `False` `True` uvedeném pořadí.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Not` operátor k provedení logické negace jednotlivých bitů číselného výrazu. Bit ve vzorci výsledků je nastaven na zpětný výsledek odpovídajícího bitu ve vzoru operandu, včetně bitu znaménka.  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 Předchozí příklad vytvoří výsledky – 11, – 9 a – 7 v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také

- [Logické/bitové operátory (Visual Basic)](logical-bitwise-operators.md)
- [Priorita operátorů v jazyce Visual Basic](operator-precedence.md)
- [Operátory uvedené podle funkce](operators-listed-by-functionality.md)
- [Logické a bitové operátory v jazyce Visual Basic](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
