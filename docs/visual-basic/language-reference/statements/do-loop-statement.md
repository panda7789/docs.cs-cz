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
ms.openlocfilehash: 8c965dc89794654127e4b872c6aebf55c8902468
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525145"
---
# <a name="doloop-statement-visual-basic"></a>Do...Loop – příkaz (Visual Basic)
Opakuje blok příkazů při `Boolean` podmínka je `True` nebo dokud se podmínka nestane `True`.  
  
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
|`While`|Vyžaduje se, pokud `Until` se používá. Opakování cyklu až do `condition` je `False`.|  
|`Until`|Vyžaduje se, pokud `While` se používá. Opakování cyklu až do `condition` je `True`.|  
|`condition`|Volitelné. `Boolean` výraz. Pokud `condition` je `Nothing`, Visual Basic považuje za `False`.|  
|`statements`|Volitelné. Jeden nebo více příkazů, které se opakují při nebo dokud, `condition` je `True`.|  
|`Continue Do`|Volitelné. Předá řízení následující iteraci `Do` smyčky.|  
|`Exit Do`|Volitelné. Přenese ovládací prvek z celkového počtu `Do` smyčky.|  
|`Loop`|Povinný parametr. Ukončí definici `Do` smyčky.|  
  
## <a name="remarks"></a>Poznámky  
 Použití `Do...Loop` struktury, pokud má být opakován sadu příkazů na nekonečný počet dob, dokud není splněna podmínka. Pokud chcete do sady počtu opakování, opakujte příkazy [pro... Další příkaz](../../../visual-basic/language-reference/statements/for-next-statement.md) je obvykle vhodnější použít.  
  
 Můžete použít buď `While` nebo `Until` k určení `condition`, ale ne obojí.  
  
 Můžete otestovat `condition` pouze jednou, na začátku nebo konci smyčky. Pokud testujete `condition` na začátek smyčky (v `Do` příkaz), smyčka nemusí spouštět ještě jednou. Pokud otestujete na konci smyčky (v `Loop` příkaz), vždycky cyklu aspoň jednou.  
  
 Podmínka obvykle výsledkem porovnání dvou hodnot, ale může být libovolný výraz, který se vyhodnotí [datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) hodnotu (`True` nebo `False`). To zahrnuje hodnoty jiné datové typy, jako je například číselné typy, které se převedly tak `Boolean`.  
  
 Je možné vnořovat `Do` smyčky vložením v jednom průchodu v rámci jiného. Lze také vnořit různé druhy řídicích struktur v sobě navzájem. Další informace najdete v tématu [vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
>  `Do...Loop` Struktury poskytuje větší flexibilitu než [během... End While – příkaz](../../../visual-basic/language-reference/statements/while-end-while-statement.md) vzhledem k tomu, že umožňuje rozhodnout, jestli se má ukončit smyčky při `condition` přestává být `True` nebo když se nejprve stane `True`. K otestování také umožňuje `condition` na začátku nebo konci smyčky.  
  
## <a name="exit-do"></a>Ukončit  
 [Ukončit proveďte](../../../visual-basic/language-reference/statements/exit-statement.md) příkaz může poskytnout alternativní způsob ukončení `Do…Loop`. `Exit Do` okamžitě přenese řízení příkazu následujícímu `Loop` příkazu.  
  
 `Exit Do` Po vyhodnocení některé podmínky, například se často používá `If...Then...Else` struktury. Můžete chtít ukončení smyčky je-li zjistit podmínku, která umožňuje zbytečné nebo nemožné, chcete-li pokračovat, iterace, jako jsou chybné hodnotu nebo žádost o ukončení. Jedno použití `Exit Do` je testovací podmínku, která by mohla způsobit, že *vznik nekonečné smyčky*, což je smyčku, která může běžet velká, nebo dokonce neomezený počet pokusů. Můžete použít `Exit Do` dostala mimo smyčku.  
  
 Může obsahovat libovolný počet `Exit Do` příkazy kdekoli v `Do…Loop`.  
  
 Při použití v rámci vnořené `Do` smyčky, `Exit Do` předává řízení mimo vnitřní smyčky a na další vyšší úroveň vnoření.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se příkazy ve smyčce dál běžet až `index` proměnnou je větší než 10. `Until` Klauzule je na konci smyčky.  
  
 [!code-vb[VbVbalrStatements#131](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_1.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `While` klauzule místo `Until` klauzule a `condition` je testován na začátek smyčky místo na konci.  
  
 [!code-vb[VbVbalrStatements#132](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_2.vb)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `condition` smyčky se zastaví při `index` proměnnou je větší než 100. `If` Příkaz ve smyčce, ale způsobí, že `Exit Do` příkaz zastaví smyčky, pokud indexovaná proměnná je větší než 10.  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_3.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad načte všechny řádky v textovém souboru. <xref:System.IO.File.OpenText%2A> Metoda otevře soubor a vrátí <xref:System.IO.StreamReader> , který čte znaky. V `Do...Loop` podmínku, <xref:System.IO.StreamReader.Peek%2A> metodu `StreamReader` Určuje, zda jsou mezi dalšími znaky.  
  
 [!code-vb[VbVbalrStatements#134](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_4.vb)]  
  
## <a name="see-also"></a>Viz také:
- [Struktury smyčky](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Příkaz For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Příkaz Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Příkaz While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
