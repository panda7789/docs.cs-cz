---
title: Handles – Klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: ae05e77515e4e2b50cdf5f9a1908375fa311c3a3
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581802"
---
# <a name="handles-clause-visual-basic"></a>Handles – Klauzule (Visual Basic)
Deklaruje, že procedura zpracovává určenou událost.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a>Součásti  
 `proceduredeclaration`  
 Deklarace procedury `Sub` pro proceduru, která zpracuje událost.  
  
 `eventlist`  
 Seznam událostí pro `proceduredeclaration`, které se mají zpracovat, oddělené čárkami Události musí být vyvolány buď základní třídou pro aktuální třídu, nebo objektem deklarovaným pomocí klíčového slova `WithEvents`.  
  
## <a name="remarks"></a>Poznámky  
 Použijte klíčové slovo `Handles` na konci deklarace procedury k tomu, aby zpracovával události vyvolané proměnnou objektu deklarované pomocí klíčového slova `WithEvents`. Klíčové slovo `Handles` lze také použít v odvozené třídě pro zpracování událostí ze základní třídy.  
  
 Klíčové slovo `Handles` a příkaz `AddHandler` umožňují určit, že konkrétní procedury budou zpracovávat konkrétní události, ale existují rozdíly. Při definování procedury použijte klíčové slovo `Handles`, které určuje, že zpracuje konkrétní událost. Příkaz `AddHandler` spojuje procedury s událostmi v době běhu. Další informace naleznete v tématu [addHandler – příkaz](../../../visual-basic/language-reference/statements/addhandler-statement.md).  
  
 Pro vlastní události aplikace vyvolá přistupující objekt `AddHandler` události při přidání procedury jako obslužné rutiny události. Další informace o vlastních událostech naleznete v tématu [příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#2)]  
  
 Následující příklad ukazuje, jak může odvozená třída použít příkaz `Handles` ke zpracování události ze základní třídy.  
  
 [!code-vb[VbVbalrEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#3)]  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje dvě obslužné rutiny událostí tlačítek pro projekt **aplikace WPF** .  
  
 [!code-vb[VbVbalrEvents#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#41)]  
  
## <a name="example"></a>Příklad  
 Následující příklad je ekvivalentní k předchozímu příkladu. @No__t_0 v klauzuli `Handles` obsahuje události pro obě tlačítka.  
  
 [!code-vb[VbVbalrEvents#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#42)]  
  
## <a name="see-also"></a>Viz také:

- [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
- [Příkaz AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [Příkaz RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)
- [Příkaz RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
- [Události](../../../visual-basic/programming-guide/language-features/events/index.md)
