---
title: Struktury smyčky
ms.date: 07/20/2015
helpviewer_keywords:
- control flow [Visual Basic], loops
- For keyword [Visual Basic], loop structures
- loops
- loop structures [Visual Basic]
- statements [Visual Basic], loop
- Do statement [Visual Basic], Do loops
- conditional statements [Visual Basic], loop structures
ms.assetid: ecacb09b-a4c9-42be-98b2-a15d368b5db8
ms.openlocfilehash: 3f60e9dc83dc7174e765903be13f2870ea40ce4c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403512"
---
# <a name="loop-structures-visual-basic"></a>Struktury smyčky (Visual Basic)
Struktury smyčky Visual Basic umožňují spustit jeden nebo více řádků kódu opakovaně. Příkazy lze opakovat ve struktuře smyčky, dokud není podmínka, `True` dokud není podmínka `False` , zadaný počet opakování nebo jednou pro každý prvek v kolekci.  
  
 Následující ilustrace znázorňuje strukturu smyčky, která spouští sadu příkazů, dokud podmínka nebude pravdivá:  
  
 ![Vývojový diagram, který zobrazuje do... Do smyčky.](./media/loop-structures/do-until-loop-true-condition.gif)  
  
## <a name="while-loops"></a>Cykly ve smyčce  
 `While`Konstrukce... `End While` spouští sadu příkazů, pokud je podmínka zadaná v `While` příkazu `True` . Další informace najdete v části [while... Příkaz End While](../../../language-reference/statements/while-end-while-statement.md).  
  
## <a name="do-loops"></a>Do smyček  
 `Do`Konstrukce... `Loop` umožňuje testovat podmínku buď na začátku, nebo na konci struktury smyčky. Můžete také určit, jestli se má opakovat smyčka, když podmínka zůstane `True` nebo dokud se nespustí `True` . Další informace najdete v části [do... Příkaz LOOP](../../../language-reference/statements/do-loop-statement.md)  
  
## <a name="for-loops"></a>Smyčka for  
 `For`Konstrukce... `Next` provádí smyčku v nastaveném počtu opakování. K udržení přehledu opakování používá proměnnou ovládacího prvku smyčky, která se označuje také jako *čítač*. Zadejte počáteční a koncové hodnoty pro tento čítač a můžete volitelně zadat hodnotu, o kterou se zvýší z jednoho opakování na další. Další informace najdete v tématu [... Další příkaz](../../../language-reference/statements/for-next-statement.md).  
  
## <a name="for-each-loops"></a>Pro každou smyčku  
 `For Each`Konstrukce... `Next` spouští sadu příkazů jednou pro každý prvek v kolekci. Zadáte řídicí proměnnou smyčky, ale nemusíte určit počáteční nebo koncové hodnoty. Další informace najdete v tématu [for each... Další příkaz](../../../language-reference/statements/for-each-next-statement.md).  
  
## <a name="see-also"></a>Viz také

- [Tok řízení](index.md)
- [Struktury rozhodování](decision-structures.md)
- [Ostatní řídicí struktury](other-control-structures.md)
- [Vnořené řídicí struktury](nested-control-structures.md)
