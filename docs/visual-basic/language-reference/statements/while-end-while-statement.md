---
title: While...End While – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
ms.openlocfilehash: 5da05835998b2e9ef9aeefe5b00faf9e1ecb9ce2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582262"
---
# <a name="whileend-while-statement-visual-basic"></a>While...End While – příkaz (Visual Basic)
Spustí sérii příkazů, pokud je zadaná podmínka `True`.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`condition`|Požadováno. výraz `Boolean` Pokud je `condition` `Nothing`, Visual Basic považuje za `False`.|  
|`statements`|Volitelné. Jeden nebo více příkazů, které následují `While`, které se spustí pokaždé, když `condition` `True`.|  
|`Continue While`|Volitelné. Přenáší řízení na další iteraci `While` bloku.|  
|`Exit While`|Volitelné. Přenáší řízení z `While`ho bloku.|  
|`End While`|Požadováno. Ukončí definici bloku `While`.|  
  
## <a name="remarks"></a>Poznámky  
 @No__t_0 strukturu použijte v případě, že chcete opakovat sadu příkazů v neurčitém počtu opakování, pokud podmínka zůstane `True`. Pokud potřebujete větší flexibilitu při testování podmínky nebo k tomu, pro který výsledek testujete, můžete preferovat do.. [. Příkaz LOOP](../../../visual-basic/language-reference/statements/do-loop-statement.md) Pokud chcete příkazy opakovat v nastaveném počtu opakování, [pro... Další příkaz](../../../visual-basic/language-reference/statements/for-next-statement.md) je obvykle lepší volbou.  
  
> [!NOTE]
> Klíčové slovo `While` se také používá v do [... Příkaz LOOP](../../../visual-basic/language-reference/statements/do-loop-statement.md), [klauzule Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md) a [klauzuli HAVING while](../../../visual-basic/language-reference/queries/take-while-clause.md).  
  
 Pokud je `condition` `True`, všechny `statements` spustit až do chvíle, kdy se nenajde příkaz `End While`. Ovládací prvek se pak vrátí do příkazu `While` a `condition` znovu zaškrtnuto. Pokud je `condition` stále `True`, proces se opakuje. Pokud je `False`, řízení se předá do příkazu, který následuje po příkazu `End While`.  
  
 Příkaz `While` vždy před spuštěním smyčky vždycky kontroluje podmínku. Opakování pokračuje, dokud podmínka zůstane `True`. Pokud je při prvním zadání smyčky `condition` `False`, nespustí se ani jednou.  
  
 @No__t_0 obvykle vede k porovnání dvou hodnot, ale může to být libovolný výraz, který je vyhodnocen jako logická hodnota [datového typu](../../../visual-basic/language-reference/data-types/boolean-data-type.md) (`True` nebo `False`). Tento výraz může obsahovat hodnotu jiného datového typu, jako je například číselný typ, který byl převeden na `Boolean`.  
  
 Smyčky `While` můžete vnořovat vložením jedné smyčky do jiné. Můžete také vnořit různé druhy řídicích struktur mezi sebou. Další informace najdete v tématu [vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-while"></a>Ukončit během  
 Příkaz [Exit while](../../../visual-basic/language-reference/statements/exit-statement.md) může poskytnout jiný způsob, jak ukončit smyčku `While`. `Exit While` okamžitě přenáší řízení na příkaz, který následuje po příkazu `End While`.  
  
 Obvykle používáte `Exit While` po vyhodnocení některé podmínky (například ve struktuře `If...Then...Else`). Můžete chtít ukončit smyčku, pokud zjistíte podmínku, která je nepotřebná nebo nemožná, aby pokračovala v iteraci, jako je například chybná hodnota nebo žádost o ukončení. Můžete použít `Exit While` při testování podmínky, která by mohla způsobit *nekonečnou smyčku*, což je smyčka, která by mohla běžet velmi velký nebo dokonce nekonečný počet časů. Potom můžete pomocí `Exit While` řídicí smyčku.  
  
 Libovolný počet `Exit While` příkazů můžete umístit kdekoli v `While` smyčce.  
  
 Při použití ve vnořených cyklech `While` `Exit While` přenáší řízení z nejvnitřnější smyčky a na další vyšší úroveň vnoření.  
  
 Příkaz `Continue While` okamžitě přenáší řízení na další iteraci smyčky. Další informace najdete v tématu [příkaz Continue](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu budou příkazy ve smyčce nadále spuštěny, dokud je proměnná `index` větší než 10.  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití příkazů `Continue While` a `Exit While`.  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a>Příklad  
 Následující příklad přečte všechny řádky v textovém souboru. Metoda <xref:System.IO.File.OpenText%2A> otevře soubor a vrátí <xref:System.IO.StreamReader>, který přečte znaky. V `While` podmínka určuje <xref:System.IO.StreamReader.Peek%2A> metoda `StreamReader`, zda soubor obsahuje další znaky.  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury smyčky](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Příkaz Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Příkaz For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Příkaz Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Příkaz Continue](../../../visual-basic/language-reference/statements/continue-statement.md)
