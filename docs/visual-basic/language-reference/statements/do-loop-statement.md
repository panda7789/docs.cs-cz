---
title: Do...Loop – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Do
- vb.Loop
- vb.Until
helpviewer_keywords:
- conditional statements [Visual Basic], Do�Loop
- while statement [Visual Basic], Do...Loop
- execution [Visual Basic], conditional
- Do loops
- Until keyword [Visual Basic], Do...Loop statement
- Do...Loop statement
- instructions, repeating
- Do statement [Visual Basic]
- Exit statement [Visual Basic], in Do...Loop statements
- loop structures [Visual Basic], Do�Loop statements
- do-while statements [Visual Basic]
- loops, exiting
- Loop keyword [Visual Basic], Do...Loop statement
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
ms.openlocfilehash: eff5239e07ca27f40ece5af68f46c491be91cf09
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583446"
---
# <a name="doloop-statement-visual-basic"></a>Do...Loop – příkaz (Visual Basic)
Opakuje blok příkazů, dokud je podmínka `Boolean` `True` nebo dokud podmínka nebude `True`.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
' -or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`Do`|Požadováno. Spustí definici smyčky `Do`.|  
|`While`|Povinné, pokud se nepoužívá `Until`. Opakujte smyčku, dokud není `False` `condition`.|  
|`Until`|Povinné, pokud se nepoužívá `While`. Opakujte smyčku, dokud není `True` `condition`.|  
|`condition`|Volitelné. výraz `Boolean` Pokud je `condition` `Nothing`, Visual Basic považuje za `False`.|  
|`statements`|Volitelné. Jeden nebo více příkazů, které se opakují, nebo dokud `condition` `True`.|  
|`Continue Do`|Volitelné. Přenese řízení na další iteraci `Do` smyčky.|  
|`Exit Do`|Volitelné. Přenáší řízení ze smyčky `Do`.|  
|`Loop`|Požadováno. Ukončí definici smyčky `Do`.|  
  
## <a name="remarks"></a>Poznámky  
 @No__t_0 strukturu použijte v případě, že chcete opakovat sadu příkazů v neurčitém počtu výskytů, dokud není splněna podmínka. Pokud chcete příkazy opakovat v nastaveném počtu opakování, [pro... Další příkaz](../../../visual-basic/language-reference/statements/for-next-statement.md) je obvykle lepší volbou.  
  
 K určení `condition`, ale ne obojí, můžete použít buď `While`, nebo `Until`.  
  
 Můžete testovat `condition` jenom jednou, a to buď na začátku, nebo na konci smyčky. Pokud testujete `condition` na začátku smyčky (v příkazu `Do`), smyčka nemusí běžet ještě jednou. Pokud testujete na konci smyčky (v příkazu `Loop`), smyčka vždy proběhne alespoň jednou.  
  
 Podmínka obvykle je výsledkem porovnání dvou hodnot, ale může to být libovolný výraz, který je vyhodnocen jako logická hodnota [datového typu](../../../visual-basic/language-reference/data-types/boolean-data-type.md) (`True` nebo `False`). To zahrnuje hodnoty jiných datových typů, například číselné typy, které byly převedeny na `Boolean`.  
  
 Smyčky `Do` můžete vnořovat vložením jedné smyčky do jiné. Můžete také vnořit různé druhy řídicích struktur mezi sebou. Další informace najdete v tématu [vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
> Struktura `Do...Loop` poskytuje větší flexibilitu než [while... Příkaz End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md) , protože umožňuje rozhodnout, jestli se má ukončit smyčka, když se `condition` zastaví `True` nebo když se poprvé stane `True`. Také umožňuje testovat `condition` na začátku nebo na konci smyčky.  
  
## <a name="exit-do"></a>Ukončit  
 Příkaz [Exit](../../../visual-basic/language-reference/statements/exit-statement.md) do může nabídnout alternativní způsob, jak ukončit `Do…Loop`. `Exit Do` přenáší řízení okamžitě na příkaz, který následuje po příkazu `Loop`.  
  
 `Exit Do` se často používá po vyhodnocení některé podmínky, například ve struktuře `If...Then...Else`. Můžete chtít ukončit smyčku, pokud zjistíte podmínku, která je nepotřebná nebo nemožná, aby pokračovala v iteraci, jako je například chybná hodnota nebo žádost o ukončení. Jedním z použití `Exit Do` je testování podmínky, která by mohla způsobit nekonečnou *smyčku*, což je smyčka, která by mohla běžet velkým nebo dokonce nekonečným počtem výskytů. K ukončení smyčky můžete použít `Exit Do`.  
  
 Libovolný počet příkazů `Exit Do` můžete umístit kdekoli v `Do…Loop`.  
  
 Při použití ve vnořených cyklech `Do` `Exit Do` přenáší řízení z nejvnitřnější smyčky a na další vyšší úroveň vnoření.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu budou příkazy ve smyčce nadále spuštěny, dokud je proměnná `index` větší než 10. Klauzule `Until` je na konci smyčky.  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá klauzuli `While` namísto klauzule `Until` a `condition` je testován na začátku cyklu namísto na konci.  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `condition` zastaví smyčku, pokud je proměnná `index` větší než 100. Příkaz `If` ve smyčce ale způsobí, že příkaz `Exit Do` zastaví smyčku v případě, že je proměnná indexu větší než 10.  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a>Příklad  
 Následující příklad přečte všechny řádky v textovém souboru. Metoda <xref:System.IO.File.OpenText%2A> otevře soubor a vrátí <xref:System.IO.StreamReader>, který přečte znaky. V `Do...Loop` podmínka určuje <xref:System.IO.StreamReader.Peek%2A> metoda `StreamReader`, zda existují nějaké další znaky.  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury smyčky](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Příkaz For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Příkaz Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Příkaz While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
