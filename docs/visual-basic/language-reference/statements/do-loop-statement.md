---
title: Do...Loop – příkaz
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
ms.openlocfilehash: a9ec6caccbe161a39b592a642a938b81bae911a6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404781"
---
# <a name="doloop-statement-visual-basic"></a>Do...Loop – příkaz (Visual Basic)
Opakuje blok příkazů, dokud `Boolean` je podmínka `True` nebo dokud se podmínka nevrátí `True` .  
  
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
  
|Pojem|Definice|  
|---|---|  
|`Do`|Povinná hodnota. Spustí definici `Do` smyčky.|  
|`While`|Povinné `Until` , pokud se nepoužívá. Opakujte smyčku, dokud `condition` není `False` .|  
|`Until`|Povinné `While` , pokud se nepoužívá. Opakujte smyčku, dokud `condition` není `True` .|  
|`condition`|Nepovinný parametr. `Boolean`vyjádření. Pokud `condition` je `Nothing` , Visual Basic považuje za `False` .|  
|`statements`|Nepovinný parametr. Jeden nebo více příkazů, které se opakují během nebo do `condition` `True` .|  
|`Continue Do`|Nepovinný parametr. Přenese řízení na další iteraci `Do` smyčky.|  
|`Exit Do`|Nepovinný parametr. Přenese řízení ze `Do` smyčky.|  
|`Loop`|Povinná hodnota. Ukončí definici `Do` smyčky.|  
  
## <a name="remarks"></a>Poznámky  
 Strukturu použijte `Do...Loop` , pokud chcete opakovat sadu příkazů neurčitým počtem opakování, dokud není splněna podmínka. Pokud chcete příkazy opakovat v nastaveném počtu opakování, [pro... Další příkaz](for-next-statement.md) je obvykle lepší volbou.  
  
 Můžete použít buď `While` nebo `Until` k zadání `condition` , ale ne obojího.  
  
 Můžete testovat `condition` pouze jednou, a to buď na začátku, nebo na konci smyčky. Pokud testujete `condition` na začátku smyčky (v `Do` příkazu), smyčka nemusí běžet současně. Pokud testujete na konci smyčky (v `Loop` příkazu), smyčka vždy proběhne alespoň jednou.  
  
 Podmínka obvykle je výsledkem porovnání dvou hodnot, ale může to být libovolný výraz, který je vyhodnocen jako logická hodnota [datového typu](../data-types/boolean-data-type.md) ( `True` nebo `False` ). To zahrnuje hodnoty jiných datových typů, například číselné typy, které byly převedeny na `Boolean` .  
  
 Smyčky můžete vnořovat vložením `Do` jedné smyčky do jiné. Můžete také vnořit různé druhy řídicích struktur mezi sebou. Další informace najdete v tématu [vnořené řídicí struktury](../../programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
> `Do...Loop`Struktura poskytuje větší flexibilitu než [while... Příkaz End While](while-end-while-statement.md) , protože umožňuje rozhodnout, zda chcete ukončit smyčku při `condition` zastavení `True` nebo kdy se bude nacházet poprvé `True` . Také vám umožňuje testovat buď na `condition` začátku, nebo na konci smyčky.  
  
## <a name="exit-do"></a>Ukončit  
 Příkaz [Exit](exit-statement.md) do může nabídnout alternativní způsob, jak ukončit `Do…Loop` . `Exit Do`přenáší řízení okamžitě na příkaz, který následuje po `Loop` příkazu.  
  
 `Exit Do`se často používá po vyhodnocení některé podmínky, například ve `If...Then...Else` struktuře. Můžete chtít ukončit smyčku, pokud zjistíte podmínku, která je nepotřebná nebo nemožná, aby pokračovala v iteraci, jako je například chybná hodnota nebo žádost o ukončení. Jedním z nich `Exit Do` je testování podmínky, která by mohla způsobit *nekonečné opakování*, což je smyčka, která by mohla vést k velkému nebo dokonce nekonečnému počtu časů. Můžete použít `Exit Do` k opuštění smyčky.  
  
 Můžete zahrnout libovolný počet `Exit Do` příkazů kdekoli v `Do…Loop` .  
  
 Při použití v rámci vnořených `Do` smyček `Exit Do` přenáší řízení z nejvnitřnější smyčky a na další vyšší úroveň vnoření.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu jsou příkazy ve smyčce nadále spuštěny, dokud `index` je proměnná větší než 10. `Until`Klauzule je na konci smyčky.  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `While` klauzuli namísto `Until` klauzule a `condition` je testován na začátku smyčky místo na konci.  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `condition` zastaví smyčka, pokud `index` je proměnná větší než 100. `If`Příkaz ve smyčce ale způsobí, že `Exit Do` příkaz zastaví smyčku, když je proměnná indexu větší než 10.  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a>Příklad  
 Následující příklad přečte všechny řádky v textovém souboru. <xref:System.IO.File.OpenText%2A>Metoda otevře soubor a vrátí hodnotu <xref:System.IO.StreamReader> , která přečte znaky. V `Do...Loop` podmínce <xref:System.IO.StreamReader.Peek%2A> Metoda `StreamReader` Určuje, zda existují nějaké další znaky.  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a>Viz také

- [Struktury smyčky](../../programming-guide/language-features/control-flow/loop-structures.md)
- [For...Next – příkaz](for-next-statement.md)
- [Boolean – datový typ](../data-types/boolean-data-type.md)
- [Vnořené řídicí struktury](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit – příkaz](exit-statement.md)
- [While...End While – příkaz](while-end-while-statement.md)
