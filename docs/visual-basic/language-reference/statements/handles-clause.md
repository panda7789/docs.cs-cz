---
title: Handles – klauzule
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: df786e4b0f0ab3795592ea57f7af17695b086cfa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404573"
---
# <a name="handles-clause-visual-basic"></a>Handles – Klauzule (Visual Basic)
Deklaruje, že procedura zpracovává určenou událost.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a>Součásti  
 `proceduredeclaration`  
 `Sub`Deklarace procedury pro proceduru, která zpracuje událost.  
  
 `eventlist`  
 Seznam událostí `proceduredeclaration` , které se mají zpracovat, oddělené čárkami Události musí být vyvolány buď základní třídou pro aktuální třídu, nebo objektem deklarovaným pomocí `WithEvents` klíčového slova.  
  
## <a name="remarks"></a>Poznámky  
 Použijte `Handles` klíčové slovo na konci deklarace procedury k tomu, aby zpracovával události vyvolané proměnnou objektu deklarované pomocí `WithEvents` klíčového slova. `Handles`Klíčové slovo lze také použít v odvozené třídě pro zpracování událostí ze základní třídy.  
  
 `Handles`Klíčové slovo a `AddHandler` příkaz umožňují určit, že konkrétní procedury budou zpracovávat konkrétní události, ale existují rozdíly. `Handles`Při definování procedury použijte klíčové slovo, které určuje, že zpracuje konkrétní událost. `AddHandler`Příkaz propojuje procedury s událostmi v době běhu. Další informace naleznete v tématu [addHandler – příkaz](addhandler-statement.md).  
  
 Pro vlastní události aplikace vyvolá `AddHandler` přistupující objekt události při přidání procedury jako obslužné rutiny události. Další informace o vlastních událostech naleznete v tématu [příkaz Event](event-statement.md).  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#2)]  
  
 Následující příklad ukazuje, jak může odvozená třída použít `Handles` příkaz ke zpracování události ze základní třídy.  
  
 [!code-vb[VbVbalrEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#3)]  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje dvě obslužné rutiny událostí tlačítek pro projekt **aplikace WPF** .  
  
 [!code-vb[VbVbalrEvents#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#41)]  
  
## <a name="example"></a>Příklad  
 Následující příklad je ekvivalentní k předchozímu příkladu. `eventlist` `Handles` Klauzule in obsahuje události pro obě tlačítka.  
  
 [!code-vb[VbVbalrEvents#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#42)]  
  
## <a name="see-also"></a>Viz také

- [WithEvents](../modifiers/withevents.md)
- [AddHandler – příkaz](addhandler-statement.md)
- [RemoveHandler – příkaz](removehandler-statement.md)
- [Event – příkaz](event-statement.md)
- [RaiseEvent – příkaz](raiseevent-statement.md)
- [Události](../../programming-guide/language-features/events/index.md)
