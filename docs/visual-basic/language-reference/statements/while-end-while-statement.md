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
ms.openlocfilehash: 00ca0ad24231128b25a988921386d6bd3265e9a0
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843705"
---
# <a name="whileend-while-statement-visual-basic"></a>While...End While – příkaz (Visual Basic)
Spustí řadu příkazů, dokud bude podmínka `True`.  
  
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
|`condition`|Povinný parametr. `Boolean` výraz. Pokud `condition` je `Nothing`, Visual Basic považuje za `False`.|  
|`statements`|Volitelné. Jeden nebo více následujících příkazů `While`, která spustí při každém `condition` je `True`.|  
|`Continue While`|Volitelné. Předá řízení následující iteraci `While` bloku.|  
|`Exit While`|Volitelné. Přenese ovládací prvek z celkového počtu `While` bloku.|  
|`End While`|Povinný parametr. Ukončí definici `While` bloku.|  
  
## <a name="remarks"></a>Poznámky  
 Použití `While...End While` struktury, pokud chcete sadu příkazů na nekonečný počet dob, opakujte tak dlouho, dokud zůstává podmínku `True`. Pokud chcete větší flexibilitu s kde otestuje podmínku nebo co výsledek, můžete ji otestovat pro můžete dát přednost [udělat... Smyčky příkaz](../../../visual-basic/language-reference/statements/do-loop-statement.md). Pokud chcete do sady počtu opakování, opakujte příkazy [pro... Další příkaz](../../../visual-basic/language-reference/statements/for-next-statement.md) je obvykle vhodnější použít.  
  
> [!NOTE]
>  `While` – Klíčové slovo se používá také v [udělat... Smyčky příkaz](../../../visual-basic/language-reference/statements/do-loop-statement.md), [Skip While – klauzule](../../../visual-basic/language-reference/queries/skip-while-clause.md) a [Take While – klauzule](../../../visual-basic/language-reference/queries/take-while-clause.md).  
  
 Pokud `condition` je `True`, všechny nástroje `statements` běhu až do `End While` příkaz dochází. Ovládací prvek vrátí na `While` příkaz, a `condition` proběhne znovu. Pokud `condition` je stále `True`, proces se opakuje. Pokud má `False`, řízení se předá příkazu, který následuje `End While` příkazu.  
  
 `While` Příkaz vždy zkontrolujte tuto podmínku před spuštěním smyčky. Opakování ve smyčce bude pokračovat, když podmínka zůstane `True`. Pokud `condition` je `False` při prvním zadání smyčky, nespustí ještě jednou.  
  
 `condition` Obvykle výsledkem porovnání dvou hodnot, ale může být libovolný výraz, který se vyhodnotí [datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) hodnotu (`True` nebo `False`). Tento výraz může obsahovat hodnotu jiného datového typu, jako je například číselného typu, který byl převeden na `Boolean`.  
  
 Je možné vnořovat `While` smyčky tak, že v jednom průchodu v rámci jiného. Lze také vnořit různé druhy řídicích struktur v rámci mezi sebou. Další informace najdete v tématu [vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-while"></a>Při ukončení  
 [Ukončení při](../../../visual-basic/language-reference/statements/exit-statement.md) příkazu můžete zadat další způsob, jak ukončit `While` smyčky. `Exit While` okamžitě přenese ovládací prvek na příkazu, který následuje `End While` příkazu.  
  
 Obvykle použijete `Exit While` po vyhodnocení některé podmínky (třeba v `If...Then...Else` struktura). Můžete chtít ukončení smyčky je-li zjistit podmínku, která umožňuje zbytečné nebo nemožné, chcete-li pokračovat, iterace, jako jsou chybné hodnotu nebo žádost o ukončení. Můžete použít `Exit While` při testování pro podmínku, která by mohla způsobit, že *vznik nekonečné smyčky*, což je smyčku, která může běžet velmi velká, nebo dokonce nekonečné počet pokusů. Pak můžete použít `Exit While` dostala mimo smyčku.  
  
 Umístíte libovolný počet `Exit While` příkazy kdekoli v `While` smyčky.  
  
 Při použití v rámci vnořené `While` smyčky, `Exit While` předává řízení mimo vnitřní smyčky a na další vyšší úroveň vnoření.  
  
 `Continue While` Příkaz okamžitě předá řízení další iteraci smyčky. Další informace najdete v tématu [pokračovat příkaz](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se příkazy ve smyčce dál běžet až `index` proměnnou je větší než 10.  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití `Continue While` a `Exit While` příkazy.  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a>Příklad  
 Následující příklad načte všechny řádky v textovém souboru. <xref:System.IO.File.OpenText%2A> Metoda otevře soubor a vrátí <xref:System.IO.StreamReader> , který čte znaky. V `While` podmínku, <xref:System.IO.StreamReader.Peek%2A> metodu `StreamReader` Určuje, zda soubor obsahuje další znaky.  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury smyčky](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Příkaz Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Příkaz For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Příkaz Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Příkaz Continue](../../../visual-basic/language-reference/statements/continue-statement.md)
