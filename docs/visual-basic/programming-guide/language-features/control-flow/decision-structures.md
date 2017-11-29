---
title: "Struktury rozhodování (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 38820b6ca0a8f716dcaa28644bb25eb4899bd511
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="decision-structures-visual-basic"></a>Struktury rozhodování (Visual Basic)
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Umožňuje testovacích podmínkách a provádět různé operace v závislosti na výsledky testu. Můžete otestovat podmínku true nebo false, pro různé hodnoty výrazu, nebo pro různé výjimky, které jsou generovány, pokud provádějí sérii příkazů.  
  
 Následující obrázek znázorňuje rozhodovací strukturu, která se testuje podmínku se skutečnou a trvá různé akce v závislosti na tom, jestli je true nebo false.  
  
 ![Vývojový diagram Pokud... Potom... Else konstrukce](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "IfThenElse –")  
Pořízení různé akce, pokud je podmínka true a kdy je false  
  
## <a name="ifthenelse-construction"></a>If... Potom... Else konstrukce  
 `If...Then...Else`konstrukce umožňuje otestovat pro jednu nebo víc podmínek a spustit jeden nebo více příkazů v závislosti na každé podmínky. Můžete si otestovat podmínky a kroky následujícími způsoby:  
  
-   Pokud je podmínka spuštění jeden nebo více příkazů`True`  
  
-   Pokud je podmínka spuštění jeden nebo více příkazů`False`  
  
-   Pokud je podmínka spuštění některé příkazy `True` a jiné, pokud je`False`  
  
-   Pokud je předběžnou podmínku otestovat další podmínky`False`  
  
 Ovládací prvek struktura, která nabízí tyto možnosti je [Pokud... Potom... Else – příkaz](../../../../visual-basic/language-reference/statements/if-then-else-statement.md). Pokud máte pouze jeden test a jeden příkaz ke spuštění, můžete použít verzi jeden řádek. Pokud máte složitější sadu podmínek a akcí, můžete použít verzi více řádků.  
  
## <a name="selectcase-construction"></a>Vyberte... Case konstrukce  
 `Select...Case` Konstrukce umožňuje vyhodnocení výrazu jednou a spouštět různé sady příkazů na základě různých možných hodnot. Další informace najdete v tématu [vyberte... Příkaz případ](../../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="trycatchfinally-construction"></a>Try... Catch... Nakonec konstrukce  
 `Try...Catch...Finally`konstrukce umožňují spustit sadu příkazů v prostředí, které zachovává řízení, pokud kterákoli vaší příkazů dojde k výjimce. Můžete provádět různé akce pro různé výjimky. Volitelně můžete zadat blok kódu, který se spustí před ukončete celek `Try...Catch...Finally` konstrukce, bez ohledu na to, co se stane. Další informace najdete v tématu [zkuste... Catch... Finally – příkaz](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
>  Pro mnoho řídicí struktury po kliknutí na tlačítko klíčové slovo, všechny klíčová slova ve struktuře jsou vyznačené. Například když kliknete na tlačítko `If` v `If...Then...Else` konstrukce, všechny instance `If`, `Then`, `ElseIf`, `Else`, a `End If` jsou vyznačené při sestavování. Chcete-li přesunout další nebo předchozí zvýrazněný – klíčové slovo, stiskněte CTRL + SHIFT + šipka dolů nebo CTRL + SHIFT + šipka nahoru.  
  
## <a name="see-also"></a>Viz také  
 [Tok řízení](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [Struktury smyčky](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Ostatní řídicí struktury](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)  
 [Vnořené řídicí struktury](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Pokud operátor](../../../../visual-basic/language-reference/operators/if-operator.md)
