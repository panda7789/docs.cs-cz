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
ms.openlocfilehash: e12cdc1ae405b877d4d27d1947c98dcb51938ba7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="doloop-statement-visual-basic"></a>Do...Loop – příkaz (Visual Basic)
Opakuje blok příkazů při `Boolean` podmínka je `True` nebo dokud nebude podmínku `True`.  
  
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
|`Do`|Požadováno. Spustí definice `Do` smyčky.|  
|`While`|Povinné Pokud `Until` se používá. Opakujte opakovat do `condition` je `False`.|  
|`Until`|Povinné Pokud `While` se používá. Opakujte opakovat do `condition` je `True`.|  
|`condition`|Volitelné. `Boolean` Výraz. Pokud `condition` je `Nothing`, Visual Basic považuje za `False`.|  
|`statements`|Volitelné. Jeden nebo více příkazů, které se opakují při nebo dokud, `condition` je `True`.|  
|`Continue Do`|Volitelné. Přenosy ovládacího prvku do další iterace `Do` smyčky.|  
|`Exit Do`|Volitelné. Přenosy ovládacího prvku mimo `Do` smyčky.|  
|`Loop`|Požadováno. Ukončí definice `Do` smyčky.|  
  
## <a name="remarks"></a>Poznámky  
 Použití `Do...Loop` struktury, pokud má být opakován sadu příkazů na nekonečný počet dobu, dokud je podmínka. Pokud chcete opakujte příkazy se stanoveným počtem dobu, [pro... Další příkaz](../../../visual-basic/language-reference/statements/for-next-statement.md) je obvykle lepší volbou.  
  
 Můžete použít buď `While` nebo `Until` k určení `condition`, ale ne obojí.  
  
 Můžete otestovat `condition` pouze jednou, při spuštění nebo ukončení smyčky. Pokud otestujete `condition` na začátku smyčky (v `Do` příkaz), smyčky nemusí být možné spustit ještě jednou. Pokud otestujete na konci smyčky (v `Loop` příkaz), provedení vždy cyklu aspoň jednou.  
  
 Podmínka obvykle výsledkem porovnání dvou hodnot, ale může být libovolný výraz, který se vyhodnocuje [datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) hodnotu (`True` nebo `False`). To zahrnuje hodnoty jiné datové typy, jako je například číselnými typy, které byly převedeny na `Boolean`.  
  
 Lze vnořit `Do` smyčky umístěním jednoho smyčky v rámci jiného. Můžete také vnořovat různé druhy řídicí struktury v rámci navzájem. Další informace najdete v tématu [vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
>  `Do...Loop` Struktura vám dává větší flexibilitu, než [při... End While – příkaz](../../../visual-basic/language-reference/statements/while-end-while-statement.md) vzhledem k tomu, že se můžete rozhodnout, zda chcete ukončení smyčky při `condition` zastaví se `True` nebo když se nejprve stane `True`. Také umožňuje otestovat `condition` na začátku nebo konci smyčky.  
  
## <a name="exit-do"></a>Ukončete proveďte  
 [Ukončete provést](../../../visual-basic/language-reference/statements/exit-statement.md) příkaz může poskytnout alternativní způsob ukončení `Do…Loop`. `Exit Do` předá řízení příkaz, který následuje `Loop` příkaz.  
  
 `Exit Do` Po vyhodnocení některé podmínky, například v se často používá `If...Then...Else` struktura. Můžete chtít ukončit smyčku, pokud zjistíte podmínku, která umožňuje nepotřebné nebo dokonce znemožňují pokračujte iterace, třeba chybná hodnota nebo žádost o ukončení. Jedno použití `Exit Do` je otestovat pro podmínku, která by mohla způsobovat *nekonečná smyčka*, což je smyčku, který by mohl spustit velký, nebo i nekonečné stanovený počet. Můžete použít `Exit Do` abyste se vyhnuli smyčky.  
  
 Může obsahovat libovolný počet `Exit Do` příkazy kdekoli v `Do…Loop`.  
  
 Při použití uvnitř vnořené `Do` smyčky, `Exit Do` přenosy ovládacího prvku mimo nejvnitřnější smyčky a do další vyšší úroveň vnoření.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu, příkazy v smyčky dál běžet, dokud `index` proměnná je větší než 10. `Until` Klauzule je na konci smyčky.  
  
 [!code-vb[VbVbalrStatements#131](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_1.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `While` klauzule místo `Until` klauzuli a `condition` je testován na začátku smyčky místo na konci.  
  
 [!code-vb[VbVbalrStatements#132](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_2.vb)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `condition` zastaví smyčky při `index` proměnné je větší než 100. `If` Příkaz ve smyčce, ale způsobuje `Exit Do` příkaz k zastavení smyčky do proměnné index je větší než 10.  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_3.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad načte všechny řádky v textovém souboru. <xref:System.IO.File.OpenText%2A> Metoda otevře soubor a vrátí <xref:System.IO.StreamReader> , který čte znaky. V `Do...Loop` podmínky, <xref:System.IO.StreamReader.Peek%2A> metodu `StreamReader` určí, zda jsou všechny další znaky.  
  
 [!code-vb[VbVbalrStatements#134](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_4.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Struktury smyčky](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Příkaz For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [Vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Příkaz Exit](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Příkaz While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
