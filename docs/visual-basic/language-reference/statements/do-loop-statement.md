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
ms.openlocfilehash: 75a2129a9f332024831d97021e381f1b3d4fa048
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942999"
---
# <a name="doloop-statement-visual-basic"></a>Do...Loop – příkaz (Visual Basic)
Opakuje blok příkazů `Boolean` , dokud je `True` podmínka `True`nebo dokud se podmínka nevrátí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
-or-  
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
|`Do`|Povinný parametr. Spustí definici `Do` smyčky.|  
|`While`|Povinné, `Until` Pokud se nepoužívá. Opakujte smyčku, `condition` dokud `False`není.|  
|`Until`|Povinné, `While` Pokud se nepoužívá. Opakujte smyčku, `condition` dokud `True`není.|  
|`condition`|Volitelný parametr. `Boolean`vyjádření. Pokud `condition` `False`je `Nothing`, Visual Basic považuje za.|  
|`statements`|Volitelný parametr. Jeden nebo více příkazů, které se opakují během nebo do `condition`. `True`|  
|`Continue Do`|Volitelný parametr. Přenese řízení na další iteraci `Do` smyčky.|  
|`Exit Do`|Volitelný parametr. Přenese řízení ze `Do` smyčky.|  
|`Loop`|Povinný parametr. Ukončí definici `Do` smyčky.|  
  
## <a name="remarks"></a>Poznámky  
 `Do...Loop` Strukturu použijte, pokud chcete opakovat sadu příkazů neurčitým počtem opakování, dokud není splněna podmínka. Pokud chcete příkazy opakovat v nastaveném počtu opakování, [pro... Další příkaz](../../../visual-basic/language-reference/statements/for-next-statement.md) je obvykle lepší volbou.  
  
 Můžete použít buď `While` nebo `Until` k zadání `condition`, ale ne obojího.  
  
 Můžete testovat `condition` pouze jednou, a to buď na začátku, nebo na konci smyčky. Pokud testujete `condition` na začátku smyčky ( `Do` v příkazu), smyčka nemusí běžet současně. Pokud testujete na konci smyčky (v `Loop` příkazu), smyčka vždy proběhne alespoň jednou.  
  
 Podmínka obvykle je výsledkem porovnání dvou hodnot, ale může to být libovolný výraz, který je vyhodnocen jako logická hodnota [datového typu](../../../visual-basic/language-reference/data-types/boolean-data-type.md) (`True` nebo `False`). To zahrnuje hodnoty jiných datových typů, například číselné typy, které byly převedeny na `Boolean`.  
  
 Smyčky můžete vnořovat `Do` vložením jedné smyčky do jiné. Můžete také vnořit různé druhy řídicích struktur mezi sebou. Další informace najdete v tématu [vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
> `Do...Loop` Struktura poskytuje větší flexibilitu než while [... Příkaz End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md) , protože umožňuje rozhodnout, zda chcete ukončit smyčku při `condition` zastavení `True` nebo kdy se bude nacházet `True`poprvé. Také vám umožňuje testovat `condition` buď na začátku, nebo na konci smyčky.  
  
## <a name="exit-do"></a>Ukončit  
 Příkaz [Exit](../../../visual-basic/language-reference/statements/exit-statement.md) do může nabídnout alternativní způsob, jak ukončit `Do…Loop`. `Exit Do`přenáší řízení okamžitě na příkaz, který následuje `Loop` po příkazu.  
  
 `Exit Do`se často používá po vyhodnocení některé podmínky, například ve `If...Then...Else` struktuře. Můžete chtít ukončit smyčku, pokud zjistíte podmínku, která je nepotřebná nebo nemožná, aby pokračovala v iteraci, jako je například chybná hodnota nebo žádost o ukončení. Jedním z `Exit Do` nich je testování podmínky, která by mohla způsobit *nekonečné opakování*, což je smyčka, která by mohla vést k velkému nebo dokonce nekonečnému počtu časů. Můžete použít `Exit Do` k opuštění smyčky.  
  
 Můžete zahrnout libovolný počet `Exit Do` příkazů kdekoli `Do…Loop`v.  
  
 Při použití v rámci `Do` vnořených smyček `Exit Do` přenáší řízení z nejvnitřnější smyčky a na další vyšší úroveň vnoření.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu jsou příkazy ve smyčce nadále spuštěny, `index` dokud je proměnná větší než 10. `Until` Klauzule je na konci smyčky.  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `While` klauzuli namísto `Until` klauzule a `condition` je testován na začátku smyčky místo na konci.  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu zastaví smyčka, `condition` `index` Pokud je proměnná větší než 100. Příkaz ve smyčce ale způsobí, že `Exit Do` příkaz zastaví smyčku, když je proměnná indexu větší než 10. `If`  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a>Příklad  
 Následující příklad přečte všechny řádky v textovém souboru. Metoda otevře soubor a <xref:System.IO.StreamReader> vrátí hodnotu, která přečte znaky. <xref:System.IO.File.OpenText%2A> V podmínce <xref:System.IO.StreamReader.Peek%2A> Metoda`StreamReader` určuje, zda existují nějaké další znaky. `Do...Loop`  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury smyčky](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Příkaz For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Příkaz Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Příkaz While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
