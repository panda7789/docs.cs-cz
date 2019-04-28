---
title: Handles – Klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: 50a449ea8a5131c878cf703f44695cd2e2304444
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638030"
---
# <a name="handles-clause-visual-basic"></a>Handles – Klauzule (Visual Basic)
Deklaruje, že procedura zpracovává určenou událost.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a>Součásti  
 `proceduredeclaration`  
 `Sub` Deklarace procedury pro proces, který bude zpracovávat události.  
  
 `eventlist`  
 Seznam událostí pro `proceduredeclaration` pro zpracování, oddělené čárkami. Události musí být vyvolány, buď základní třídou pro aktuální třídu nebo objektem deklarovány pomocí `WithEvents` – klíčové slovo.  
  
## <a name="remarks"></a>Poznámky  
 Použití `Handles` klíčového slova na konci deklaraci procedury způsobit zpracovávat události vyvolané službou objektová proměnná deklarovaná pomocí `WithEvents` – klíčové slovo. `Handles` – Klíčové slovo lze použít také v odvozené třídě pro zpracování událostí ze základní třídy.  
  
 `Handles` – Klíčové slovo a `AddHandler` příkaz oba umožňují určit, že konkrétní postupy zpracování určité události, ale existují rozdíly. Použití `Handles` – klíčové slovo při definování proceduru k určení, že zpracovává konkrétní události. `AddHandler` Příkaz se připojí postupy k událostem v době běhu. Další informace najdete v tématu [AddHandler – příkaz](../../../visual-basic/language-reference/statements/addhandler-statement.md).  
  
 Pro vlastní události aplikace vyvolává události `AddHandler` přistupujícího objektu, když přidá postup jako obslužné rutiny události. Další informace o vlastních událostech najdete v tématu [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#2)]  
  
 Následující příklad ukazuje, jak můžete použít odvozenou třídu `Handles` příkaz pro zpracování události ze základní třídy.  
  
 [!code-vb[VbVbalrEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#3)]  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje dva tlačítko obslužné rutiny **aplikace WPF** projektu.  
  
 [!code-vb[VbVbalrEvents#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#41)]  
  
## <a name="example"></a>Příklad  
 Následující příklad je ekvivalentní předchozí příklad. `eventlist` v `Handles` klauzule WHERE obsahuje události pro obě tlačítka.  
  
 [!code-vb[VbVbalrEvents#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#42)]  
  
## <a name="see-also"></a>Viz také:

- [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
- [Příkaz AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [Příkaz RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)
- [Příkaz RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
- [Události](../../../visual-basic/programming-guide/language-features/events/index.md)
