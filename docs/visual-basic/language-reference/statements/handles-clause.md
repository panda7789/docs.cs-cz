---
title: Handles – Klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: 15ce6a25aa5f403a2e55beb57b3693095743e52f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="handles-clause-visual-basic"></a>Handles – Klauzule (Visual Basic)
Deklaruje, že procedury zpracovává zadané události.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a>Součásti  
 `proceduredeclaration`  
 `Sub` Postup deklarace pro proceduru, která zpracovává událost.  
  
 `eventlist`  
 Seznam událostí pro `proceduredeclaration` pro zpracování, oddělených čárkami. Události musí být vyvolány buď základní třída pro aktuální třídu nebo objektem deklarováno s použitím `WithEvents` – klíčové slovo.  
  
## <a name="remarks"></a>Poznámky  
 Použití `Handles` – klíčové slovo na konci tohoto postupu deklarace způsobí zpracovávat události vyvolané službou proměnné objektu deklarováno s použitím `WithEvents` – klíčové slovo. `Handles` – Klíčové slovo lze použít také v odvozené třídě zpracování událostí ze základní třídy.  
  
 `Handles` – Klíčové slovo a `AddHandler` příkaz oba umožňují určit, že konkrétní postupy zpracování konkrétní události, ale jsou rozdíly. Použití `Handles` – klíčové slovo při definování postup, chcete-li určit, která byla zjištěna určitá událost. `AddHandler` Příkaz připojí postupy pro události za běhu. Další informace najdete v tématu [AddHandler – příkaz](../../../visual-basic/language-reference/statements/addhandler-statement.md).  
  
 Pro vlastní události aplikace spustí události `AddHandler` přistupujícího objektu, když přidá postupu jako obslužnou rutinu události. Další informace o vlastních událostí najdete v tématu [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrEvents#2](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_1.vb)]  
  
 Následující příklad ukazuje, jak můžete použít třídu odvozenou `Handles` příkaz zpracovat události ze základní třídy.  
  
 [!code-vb[VbVbalrEvents#3](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_2.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje dvě obslužné rutiny tlačítko událostí pro **aplikaci WPF** projektu.  
  
 [!code-vb[VbVbalrEvents#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_3.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad je ekvivalentní předchozí příklad. `eventlist` v `Handles` klauzule WHERE obsahuje události pro obě tlačítka.  
  
 [!code-vb[VbVbalrEvents#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_4.vb)]  
  
## <a name="see-also"></a>Viz také  
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)  
 [Příkaz AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [Příkaz RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Příkaz RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md)  
 [Události](../../../visual-basic/programming-guide/language-features/events/index.md)
