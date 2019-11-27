---
title: Struktury rozhodování
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
ms.openlocfilehash: d0d4039ff2edc61ee8b4b732c6adcb6e420d73ea
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353964"
---
# <a name="decision-structures-visual-basic"></a>Struktury rozhodování (Visual Basic)
Visual Basic umožňuje testovat podmínky a provádět různé operace v závislosti na výsledcích tohoto testu. Můžete testovat podmínku true nebo false, pro různé hodnoty výrazu nebo pro různé výjimky vygenerované při spuštění řady příkazů.  
  
 Následující ilustrace znázorňuje rozhodovací strukturu, která testuje podmínku na hodnotu true a provede různé akce v závislosti na tom, zda je hodnota true nebo false.  
  
 ![Vývojový diagram If...Then...Else konstrukce.](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a>If...Then...Else konstrukce  
 `If...Then...Else` konstrukce umožňují testovat jednu nebo více podmínek a v závislosti na každé z nich spustit jeden nebo více příkazů. Můžete testovat podmínky a provádět akce následujícími způsoby:  
  
- Spustit jeden nebo více příkazů, pokud je podmínka `True`  
  
- Spustit jeden nebo více příkazů, pokud je podmínka `False`  
  
- Spustit některé příkazy, pokud je podmínka `True` a další, pokud je `False`  
  
- Test další podmínky, pokud je předchozí podmínka `False`  
  
 Struktura ovládacího prvku, která nabízí všechny tyto možnosti, je [if... Pak... ELSE – příkaz](../../../../visual-basic/language-reference/statements/if-then-else-statement.md). Pokud máte pouze jeden test a jeden příkaz ke spuštění, můžete použít jednořádkových verzí. Pokud máte složitější sadu podmínek a akcí, můžete použít víceřádkovou verzi.  
  
## <a name="selectcase-construction"></a>Select...Case konstrukce  
 Konstrukce `Select...Case` umožňuje vyhodnotit výraz jednou a spouštět různé sady příkazů na základě různých možných hodnot. Další informace najdete v tématu věnovaném [výběru... Příkaz Case](../../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="trycatchfinally-construction"></a>Try...Catch...Finally konstrukce  
 `Try...Catch...Finally` konstrukce umožňují spustit sadu příkazů v prostředí, které uchovává řízení, pokud některý z vašich příkazů způsobí výjimku. Můžete provádět různé akce pro různé výjimky. Volitelně můžete zadat blok kódu, který se spustí před ukončením celé `Try...Catch...Finally` konstrukce bez ohledu na to, co se děje. Další informace najdete v tématu [Try... Zachytit... Finally – příkaz](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
> U mnoha řídicích struktur se při kliknutí na klíčové slovo zvýrazní všechna klíčová slova ve struktuře. Například když v konstrukci `If...Then...Else` kliknete na `If`, všechny instance `If`, `Then`, `ElseIf`, `Else`a `End If` se zvýrazní. Chcete-li přejít na další nebo předchozí zvýrazněné klíčové slovo, stiskněte klávesy CTRL + SHIFT + šipka dolů nebo CTRL + SHIFT + šipka nahoru.  
  
## <a name="see-also"></a>Viz také:

- [Tok řízení](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Struktury smyčky](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Ostatní řídicí struktury](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [Vnořené řídicí struktury](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Operátor If](../../../../visual-basic/language-reference/operators/if-operator.md)
