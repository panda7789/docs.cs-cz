---
title: While...End While – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
ms.openlocfilehash: d9eb8cb95d46e860aa127954d7b44e37991d4a13
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84391583"
---
# <a name="whileend-while-statement-visual-basic"></a>While...End While – příkaz (Visual Basic)
Spustí sérii příkazů, pokud je daná podmínka `True` .  
  
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
  
|Pojem|Definice|  
|---|---|  
|`condition`|Povinná hodnota. `Boolean`vyjádření. Pokud `condition` je `Nothing` , Visual Basic považuje za `False` .|  
|`statements`|Nepovinný parametr. Jeden nebo více níže uvedených příkazů `While` , které jsou spouštěny pokaždé, když `condition` je `True` .|  
|`Continue While`|Nepovinný parametr. Přenáší řízení na další iteraci `While` bloku.|  
|`Exit While`|Nepovinný parametr. Přenáší řízení z `While` bloku.|  
|`End While`|Povinná hodnota. Ukončí definici `While` bloku.|  
  
## <a name="remarks"></a>Poznámky  
 Strukturu použijte `While...End While` , pokud chcete opakovat sadu příkazů neurčitému počtu výskytů, dokud podmínka zůstane `True` . Pokud potřebujete větší flexibilitu při testování podmínky nebo k tomu, pro který výsledek testujete, můžete preferovat do.. [. Příkaz LOOP](do-loop-statement.md) Pokud chcete příkazy opakovat v nastaveném počtu opakování, [pro... Další příkaz](for-next-statement.md) je obvykle lepší volbou.  
  
> [!NOTE]
> `While`Klíčové slovo se používá také v do [... Příkaz LOOP](do-loop-statement.md), [klauzule Skip While](../queries/skip-while-clause.md) a [klauzuli HAVING while](../queries/take-while-clause.md).  
  
 Pokud `condition` je `True` , všechny `statements` spuštění až do chvíle, kdy se `End While` příkaz vyskytne. Ovládací prvek se pak vrátí do `While` příkazu a `condition` znovu se vyhradí. Pokud `condition` je stále `True` , proces se opakuje. Pokud je `False` , řízení se předá příkazu, který následuje po `End While` příkazu.  
  
 `While`Příkaz vždy před spuštěním smyčky kontroluje podmínku. Opakování pokračuje, i když podmínka zůstane `True` . Pokud `condition` je `False` při prvním zadání smyčky, nebude spuštěna ani jednou.  
  
 `condition`Obvykle je výsledkem porovnání dvou hodnot, ale může to být libovolný výraz, který je vyhodnocen jako logická hodnota [datového typu](../data-types/boolean-data-type.md) ( `True` nebo `False` ). Tento výraz může obsahovat hodnotu jiného datového typu, jako je například číselný typ, který byl převeden na `Boolean` .  
  
 Smyčky můžete vnořovat `While` vložením jedné smyčky do jiné. Můžete také vnořit různé druhy řídicích struktur mezi sebou. Další informace najdete v tématu [vnořené řídicí struktury](../../programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-while"></a>Ukončit během  
 Příkaz [Exit while](exit-statement.md) může poskytnout jiný způsob, jak ukončit `While` smyčku. `Exit While`okamžitě přenese řízení na příkaz, který následuje po `End While` příkazu.  
  
 Obvykle se používá `Exit While` po vyhodnocení některé podmínky (například ve `If...Then...Else` struktuře). Můžete chtít ukončit smyčku, pokud zjistíte podmínku, která je nepotřebná nebo nemožná, aby pokračovala v iteraci, jako je například chybná hodnota nebo žádost o ukončení. Můžete použít `Exit While` při testování podmínky, která by mohla způsobit *nekonečnou smyčku*, což je smyčka, která by mohla běžet velmi velkým nebo dokonce nekonečným počtem výskytů. Pak můžete použít `Exit While` k řídicímu cyklu smyčky.  
  
 Libovolný počet příkazů můžete umístit `Exit While` kdekoli ve `While` smyčce.  
  
 Při použití v rámci vnořených `While` smyček `Exit While` přenáší řízení z nejvnitřnější smyčky a na další vyšší úroveň vnoření.  
  
 `Continue While`Příkaz okamžitě převede řízení na další iteraci smyčky. Další informace najdete v tématu [příkaz Continue](continue-statement.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu jsou příkazy ve smyčce nadále spuštěny, dokud `index` je proměnná větší než 10.  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ilustruje použití `Continue While` `Exit While` příkazů a.  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a>Příklad  
 Následující příklad přečte všechny řádky v textovém souboru. <xref:System.IO.File.OpenText%2A>Metoda otevře soubor a vrátí hodnotu <xref:System.IO.StreamReader> , která přečte znaky. V `While` podmínce <xref:System.IO.StreamReader.Peek%2A> Metoda `StreamReader` Určuje, zda soubor obsahuje další znaky.  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a>Viz také

- [Struktury smyčky](../../programming-guide/language-features/control-flow/loop-structures.md)
- [Do...Loop – příkaz](do-loop-statement.md)
- [For...Next – příkaz](for-next-statement.md)
- [Boolean – datový typ](../data-types/boolean-data-type.md)
- [Vnořené řídicí struktury](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit – příkaz](exit-statement.md)
- [Continue – příkaz](continue-statement.md)
