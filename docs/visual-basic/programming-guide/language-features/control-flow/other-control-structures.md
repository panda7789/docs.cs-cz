---
title: Ostatní řídicí struktury
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: c6d80b237c7c3512c2904547842fdeb3c69bef68
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402015"
---
# <a name="other-control-structures-visual-basic"></a>Ostatní řídicí struktury (Visual Basic)
Visual Basic poskytuje řídicí struktury, které vám pomůžou uvolnit prostředek nebo snížit počet pokusů o opakování odkazu na objekt.  
  
## <a name="usingend-using-construction"></a>Pomocí... Konec používání konstrukce  
 `Using...End Using`Konstrukce vytvoří blok příkazů, ve kterém budete používat prostředek, jako je třeba připojení SQL. Volitelně můžete získat prostředek pomocí `Using` příkazu. Po ukončení `Using` bloku Visual Basic automaticky odstraní prostředek, aby byl k dispozici pro použití pro jiný kód. Prostředek musí být místní a na jedno použití. Další informace naleznete v tématu [using – příkaz](../../../language-reference/statements/using-statement.md).  
  
## <a name="withend-with-construction"></a>S... Ukončit se konstrukcí  
 `With...End With`Konstrukce umožňuje zadat odkaz na objekt jednou a potom spustit sérii příkazů, které přistupují k jeho členům. To může zjednodušit váš kód a zvýšit výkon, protože Visual Basic není nutné znovu vytvořit odkaz pro každý příkaz, který k němu přistupuje. Další informace najdete v tématu [s... Příkaz end with](../../../language-reference/statements/with-end-with-statement.md)  
  
## <a name="see-also"></a>Viz také

- [Tok řízení](index.md)
- [Struktury rozhodování](decision-structures.md)
- [Struktury smyčky](loop-structures.md)
- [Vnořené řídicí struktury](nested-control-structures.md)
- [Using – příkaz](../../../language-reference/statements/using-statement.md)
- [With...End With – příkaz](../../../language-reference/statements/with-end-with-statement.md)
