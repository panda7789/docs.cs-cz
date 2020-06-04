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
ms.openlocfilehash: aac9844240defc5a21a3f4e6090fa8f49e6348a1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403511"
---
# <a name="decision-structures-visual-basic"></a>Struktury rozhodování (Visual Basic)
Visual Basic umožňuje testovat podmínky a provádět různé operace v závislosti na výsledcích tohoto testu. Můžete testovat podmínku true nebo false, pro různé hodnoty výrazu nebo pro různé výjimky vygenerované při spuštění řady příkazů.  
  
 Následující ilustrace znázorňuje rozhodovací strukturu, která testuje podmínku na hodnotu true a provede různé akce v závislosti na tom, zda je hodnota true nebo false.  
  
 ![Vývojový diagram if... Pak... Jinak konstrukce.](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a>Pokud... Pak... Konstrukce else  
 `If...Then...Else`konstrukce umožňují otestovat jednu nebo více podmínek a spustit jeden nebo více příkazů v závislosti na každé podmínce. Můžete testovat podmínky a provádět akce následujícími způsoby:  
  
- Spustit jeden nebo více příkazů, pokud je podmínka`True`  
  
- Spustit jeden nebo více příkazů, pokud je podmínka`False`  
  
- Spustit některé příkazy, pokud je podmínka `True` , a další, pokud jsou`False`  
  
- Test další podmínky, pokud je předchozí podmínka`False`  
  
 Struktura ovládacího prvku, která nabízí všechny tyto možnosti, je [if... Pak... ELSE – příkaz](../../../language-reference/statements/if-then-else-statement.md). Pokud máte pouze jeden test a jeden příkaz ke spuštění, můžete použít jednořádkových verzí. Pokud máte složitější sadu podmínek a akcí, můžete použít víceřádkovou verzi.  
  
## <a name="selectcase-construction"></a>Vybrat... Konstrukce případu  
 `Select...Case`Konstrukce umožňuje vyhodnotit výraz jednou a spouštět různé sady příkazů na základě různých možných hodnot. Další informace najdete v tématu věnovaném [výběru... Příkaz Case](../../../language-reference/statements/select-case-statement.md).  
  
## <a name="trycatchfinally-construction"></a>Zkusit... Zachytit... Nakonec konstrukce  
 `Try...Catch...Finally`konstrukce umožňují spustit sadu příkazů v prostředí, které si zachovají řízení, pokud některý z vašich příkazů způsobí výjimku. Můžete provádět různé akce pro různé výjimky. Volitelně můžete zadat blok kódu, který se spustí před ukončením celé `Try...Catch...Finally` konstrukce bez ohledu na to, co se děje. Další informace najdete v tématu [Try... Zachytit... Finally – příkaz](../../../language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
> U mnoha řídicích struktur se při kliknutí na klíčové slovo zvýrazní všechna klíčová slova ve struktuře. Například při kliknutí na `If` `If...Then...Else` konstrukci `If` `Then` jsou zvýrazněny všechny instance,,, `ElseIf` `Else` a `End If` v konstrukci. Chcete-li přejít na další nebo předchozí zvýrazněné klíčové slovo, stiskněte klávesy CTRL + SHIFT + šipka dolů nebo CTRL + SHIFT + šipka nahoru.  
  
## <a name="see-also"></a>Viz také

- [Tok řízení](index.md)
- [Struktury smyčky](loop-structures.md)
- [Ostatní řídicí struktury](other-control-structures.md)
- [Vnořené řídicí struktury](nested-control-structures.md)
- [If – operátor](../../../language-reference/operators/if-operator.md)
