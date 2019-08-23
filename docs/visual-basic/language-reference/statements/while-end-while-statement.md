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
ms.openlocfilehash: 7ea0814c587f65ddc1f114d2314ac7147143d40d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965815"
---
# <a name="whileend-while-statement-visual-basic"></a>While...End While – příkaz (Visual Basic)
Spustí sérii příkazů, pokud je `True`daná podmínka.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`condition`|Povinný parametr. `Boolean`vyjádření. Pokud `condition` `False`je `Nothing`, Visual Basic považuje za.|  
|`statements`|Volitelný parametr. Jeden nebo více níže uvedených `While`příkazů, které jsou spouštěny `True`pokaždé, když `condition` je.|  
|`Continue While`|Volitelný parametr. Přenáší řízení na další iteraci `While` bloku.|  
|`Exit While`|Volitelný parametr. Přenáší řízení `While` z bloku.|  
|`End While`|Povinný parametr. Ukončí definici `While` bloku.|  
  
## <a name="remarks"></a>Poznámky  
 Strukturu použijte, pokud chcete opakovat sadu příkazů neurčitému počtu výskytů, dokud podmínka zůstane `True`. `While...End While` Pokud potřebujete větší flexibilitu při testování podmínky nebo k tomu, pro který výsledek testujete, můžete preferovat do.. [. Příkaz LOOP](../../../visual-basic/language-reference/statements/do-loop-statement.md) Pokud chcete příkazy opakovat v nastaveném počtu opakování, [pro... Další příkaz](../../../visual-basic/language-reference/statements/for-next-statement.md) je obvykle lepší volbou.  
  
> [!NOTE]
> `While` Klíčové slovo se používá také v do [... Příkaz LOOP](../../../visual-basic/language-reference/statements/do-loop-statement.md), [klauzule Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md) a [klauzuli HAVING while](../../../visual-basic/language-reference/queries/take-while-clause.md).  
  
 Pokud `condition` je `True`, `End While` všechny `statements` spuštění až do chvíle, kdy se příkaz vyskytne. Ovládací prvek se pak vrátí `While` do příkazu a `condition` znovu se vyhradí. Pokud `condition` je stále `True`, proces se opakuje. Pokud je `End While` , řízení se předá příkazu, který následuje po příkazu. `False`  
  
 `While` Příkaz vždy před spuštěním smyčky kontroluje podmínku. Opakování pokračuje, i když podmínka zůstane `True`. Pokud `condition` je`False` při prvním zadání smyčky, nebude spuštěna ani jednou.  
  
 Obvykle `condition` je výsledkem porovnání dvou hodnot, ale může to být libovolný výraz, který je vyhodnocen jako logická hodnota [datového typu](../../../visual-basic/language-reference/data-types/boolean-data-type.md) (`True` nebo `False`). Tento výraz může obsahovat hodnotu jiného datového typu, jako je například číselný typ, který byl převeden na `Boolean`.  
  
 Smyčky můžete vnořovat `While` vložením jedné smyčky do jiné. Můžete také vnořit různé druhy řídicích struktur mezi sebou. Další informace najdete v tématu [vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-while"></a>Ukončit během  
 Příkaz [Exit while](../../../visual-basic/language-reference/statements/exit-statement.md) může poskytnout jiný způsob, jak ukončit `While` smyčku. `Exit While`okamžitě přenese řízení na příkaz, který následuje `End While` po příkazu.  
  
 Obvykle se používá `Exit While` po vyhodnocení některé podmínky (například `If...Then...Else` ve struktuře). Můžete chtít ukončit smyčku, pokud zjistíte podmínku, která je nepotřebná nebo nemožná, aby pokračovala v iteraci, jako je například chybná hodnota nebo žádost o ukončení. Můžete použít `Exit While` při testování podmínky, která by mohla způsobit nekonečnou *smyčku*, což je smyčka, která by mohla běžet velmi velkým nebo dokonce nekonečným počtem výskytů. Pak můžete použít `Exit While` k řídicímu cyklu smyčky.  
  
 Libovolný počet `Exit While` příkazů můžete umístit kdekoli `While` ve smyčce.  
  
 Při použití v rámci `While` vnořených smyček `Exit While` přenáší řízení z nejvnitřnější smyčky a na další vyšší úroveň vnoření.  
  
 `Continue While` Příkaz okamžitě převede řízení na další iteraci smyčky. Další informace najdete v tématu [příkaz Continue](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu jsou příkazy ve smyčce nadále spuštěny, `index` dokud je proměnná větší než 10.  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ilustruje použití `Continue While` příkazů a. `Exit While`  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a>Příklad  
 Následující příklad přečte všechny řádky v textovém souboru. Metoda otevře soubor a <xref:System.IO.StreamReader> vrátí hodnotu, která přečte znaky. <xref:System.IO.File.OpenText%2A> V podmínce <xref:System.IO.StreamReader.Peek%2A> Metoda`StreamReader` určuje, zda soubor obsahuje další znaky. `While`  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury smyčky](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Příkaz Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Příkaz For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Příkaz Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Příkaz Continue](../../../visual-basic/language-reference/statements/continue-statement.md)
