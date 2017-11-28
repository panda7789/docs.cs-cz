---
title: "While...End While – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5f831f233eaa4f1c38d56f3a89bda9b0cf1bccaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="whileend-while-statement-visual-basic"></a>While...End While – příkaz (Visual Basic)
Spouští řadu příkazů, dokud danou podmínkou je `True`.  
  
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
|`condition`|Požadováno. `Boolean`výraz. Pokud `condition` je `Nothing`, Visual Basic považuje za `False`.|  
|`statements`|Volitelné. Jeden nebo více následujících příkazů `While`, která spustit pokaždé, když `condition` je `True`.|  
|`Continue While`|Volitelné. Přenosy ovládacího prvku do další iterace `While` bloku.|  
|`Exit While`|Volitelné. Přenosy ovládacího prvku z `While` bloku.|  
|`End While`|Požadováno. Ukončí definice `While` bloku.|  
  
## <a name="remarks"></a>Poznámky  
 Použití `While...End While` struktury, pokud chcete sadu příkazů na nekonečný počet dobu, opakujte, dokud zůstává podmínku `True`. Pokud chcete větší flexibilitu s kde otestuje podmínku nebo co výsledný můžete otestovat pro možná budete chtít [provést... Cykly příkaz](../../../visual-basic/language-reference/statements/do-loop-statement.md). Pokud chcete opakujte příkazy se stanoveným počtem dobu, [pro... Další příkaz](../../../visual-basic/language-reference/statements/for-next-statement.md) je obvykle lepší volbou.  
  
> [!NOTE]
>  `While` – Klíčové slovo je používán také [provést... Cykly příkaz](../../../visual-basic/language-reference/statements/do-loop-statement.md), [Skip While – klauzule](../../../visual-basic/language-reference/queries/skip-while-clause.md) a [Take While – klauzule](../../../visual-basic/language-reference/queries/take-while-clause.md).  
  
 Pokud `condition` je `True`, všechny z `statements` spuštění, dokud `End While` příkaz je zjistil. Pak vrátí k řízení `While` příkaz, a `condition` je znovu zaškrtnuté. Pokud `condition` stále `True`, tento proces se opakuje. Pokud má `False`, řídit předává do příkazu, který odpovídá `End While` příkaz.  
  
 `While` Příkaz vždy kontroluje podmínku před spuštěním smyčky. Ve smyčce bude pokračovat při současném zachování stavu `True`. Pokud `condition` je `False` když poprvé vstoupíte smyčky, nefunguje i jednou.  
  
 `condition` Obvykle způsobují porovnání dvou hodnot, ale může být libovolný výraz, který se vyhodnocuje [datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) hodnotu (`True` nebo `False`). Tento výraz může obsahovat hodnotu jiného datového typu, jako je například číselného typu, který byl převeden na `Boolean`.  
  
 Lze vnořit `While` smyčky tím, že jeden smyčky v rámci jiného. Můžete také vnořovat různé druhy řídicí struktury v rámci jednu na druhou. Další informace najdete v tématu [vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-while"></a>Při ukončení  
 [Ukončete při](../../../visual-basic/language-reference/statements/exit-statement.md) příkaz můžete zadat jiný způsob, jak ukončit `While` smyčky. `Exit While`příkaz, který následuje okamžitě předá řízení `End While` příkaz.  
  
 Obvykle použijete `Exit While` po některé podmínka vyhodnocena (například v `If...Then...Else` struktura). Můžete chtít ukončit smyčku, pokud zjistíte podmínku, která umožňuje nepotřebné nebo dokonce znemožňují pokračujte iterace, třeba chybná hodnota nebo žádost o ukončení. Můžete použít `Exit While` při testování pro podmínku, která by mohla způsobovat *nekonečná smyčka*, což je smyčku, který by mohl spustit i nekonečné nebo velmi velký počet časy. Pak můžete použít `Exit While` abyste se vyhnuli smyčky.  
  
 Můžete umístit libovolný počet `Exit While` příkazy kdekoli v `While` smyčky.  
  
 Při použití uvnitř vnořené `While` smyčky, `Exit While` přenosy ovládacího prvku mimo nejvnitřnější smyčky a do další vyšší úroveň vnoření.  
  
 `Continue While` Příkaz okamžitě přenosy ovládacího prvku do další iterace smyčky. Další informace najdete v tématu [pokračovat příkaz](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu, příkazy v smyčky dál běžet, dokud `index` proměnná je větší než 10.  
  
 [!code-vb[VbVbalrStatements#171](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_1.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití `Continue While` a `Exit While` příkazy.  
  
 [!code-vb[VbVbalrStatements#172](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_2.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad načte všechny řádky v textovém souboru. <xref:System.IO.File.OpenText%2A> Metoda otevře soubor a vrátí <xref:System.IO.StreamReader> , který čte znaky. V `While` podmínky, <xref:System.IO.StreamReader.Peek%2A> metodu `StreamReader` Určuje, zda soubor obsahuje další znaky.  
  
 [!code-vb[VbVbalrStatements#173](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_3.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Struktury smyčky](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Provést... Příkaz smyčky](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [Pro... Next – příkaz](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Boolean – datový typ](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [Vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Exit – příkaz](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Continue – příkaz](../../../visual-basic/language-reference/statements/continue-statement.md)
