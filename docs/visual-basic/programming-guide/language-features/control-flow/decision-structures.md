---
title: Struktury rozhodování (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
ms.openlocfilehash: f8b653b941c5959036256cde097a41f8c6251c7a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64601229"
---
# <a name="decision-structures-visual-basic"></a>Struktury rozhodování (Visual Basic)
Visual Basic umožňuje podmínky testu a provádět různé operace v závislosti na výsledcích testu. Můžete otestovat na hodnotu true nebo false pro různé hodnoty výrazu, nebo pro různé výjimky, které jsou generovány, pokud provedete sérii tvrzení, podmínku.  
  
 Následující ilustrace znázorňuje strukturu rozhodnutí, která otestuje podmínku je true a má různé akce v závislosti na tom, zda je hodnota true nebo false.  
  
 ![Vývojový diagram If... Potom... Ostatní konstrukce.](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a>If...Then...Else Construction  
 `If...Then...Else` konstrukce umožňují test pro jednu nebo více podmínek a spuštění jednoho nebo více příkazů v závislosti na každé podmínky. Můžete otestovat podmínek a akcí následujícími způsoby:  
  
- Spustit jeden nebo více příkazů, pokud je podmínka `True`  
  
- Spustit jeden nebo více příkazů, pokud je podmínka `False`  
  
- Spustit některé příkazy, pokud je podmínka `True` a dalších jde `False`  
  
- Vyzkoušejte další podmínky, pokud je předběžnou podmínku `False`  
  
 Je řídicí struktura, která nabízí tyto možnosti [Pokud... Potom... Else – příkaz](../../../../visual-basic/language-reference/statements/if-then-else-statement.md). Jednořádkový verze můžete použít, pokud máte pouze jeden test a jeden příkaz ke spuštění. Pokud máte složitější sadu podmínek a akcí, můžete použít verzi více řádků.  
  
## <a name="selectcase-construction"></a>Vyberte... Případu konstrukce  
 `Select...Case` Konstrukce umožňuje vyhodnocení výrazu jednou a spustit jinou sadu příkazů na základě různých možných hodnot. Další informace najdete v tématu [vyberte... Case – příkaz](../../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="trycatchfinally-construction"></a>Try... Catch... Nakonec konstrukce  
 `Try...Catch...Finally` konstrukce umožňují spustit sadu příkazů v rámci prostředí, který bude mít ovládací prvek, pokud některý z výpisy dojde k výjimce. Můžete provádět různé akce pro různé výjimky. Volitelně můžete zadat blok kódu, který se spustí před ukončením celé `Try...Catch...Finally` konstrukce, bez ohledu na to, co se stane. Další informace najdete v tématu [zkuste... Catch... Příkaz finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
>  Pro mnoho řídících struktur po kliknutí na klíčové slovo, všechna klíčová slova ve struktuře jsou zvýrazněné. Například po kliknutí na `If` v `If...Then...Else` konstrukce, všechny výskyty `If`, `Then`, `ElseIf`, `Else`, a `End If` jsou zvýrazněné v procesu vytváření. Přesunout další nebo předchozí zvýrazněný – klíčové slovo, stiskněte kombinaci kláves CTRL + SHIFT + šipka dolů nebo CTRL + SHIFT + šipka nahoru.  
  
## <a name="see-also"></a>Viz také:

- [Tok řízení](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Struktury smyčky](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Ostatní řídicí struktury](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [Vnořené řídicí struktury](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Operátor If](../../../../visual-basic/language-reference/operators/if-operator.md)
