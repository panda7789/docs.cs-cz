---
title: 'Postupy: Volání obslužné rutiny události (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2b8a35459fdeb7cce0b494a9b3024a79bd4173cc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a>Postupy: Volání obslužné rutiny události (Visual Basic)
*Událostí* je akce nebo výskyt – například myši klikněte na tlačítko nebo platební limit překročen – některých součástí programu, a který můžete napsat kód je rozpoznán reagovat. *Obslužné rutiny události* je kód, který vytváříte reagovat na událost.  
  
 Obslužné rutiny události v jazyce Visual Basic je `Sub` postupu. Však můžete normálně ho nevolají stejný způsobem jako ostatní `Sub` postupy. Místo toho identifikujete postupu jako obslužná rutina události. To provedete buď pomocí [zpracovává](../../../../visual-basic/language-reference/statements/handles-clause.md) klauzule a [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) proměnnou, nebo se [AddHandler – příkaz](../../../../visual-basic/language-reference/statements/addhandler-statement.md). Použití `Handles` klauzule je způsob výchozí deklarace obslužné rutiny události v jazyce Visual Basic. Toto je způsob, jakým obslužné rutiny událostí se zapisují návrháři, když budete programu v integrované vývojové prostředí (IDE). `AddHandler` Příkaz je vhodný pro vyvolávání událostí dynamicky za běhu.  
  
 Při výskytu události, Visual Basic automaticky volá proceduru obslužná rutina události. Kód, který má přístup k události může způsobit tak, aby spuštěním [RaiseEvent – příkaz](../../../../visual-basic/language-reference/statements/raiseevent-statement.md).  
  
 Více než jeden obslužné rutiny události můžete přidružit jednu událost. V některých případech můžete zrušit přidružení obslužnou rutinu z události. Další informace najdete v tématu [události](../../../../visual-basic/programming-guide/language-features/events/index.md).  
  
### <a name="to-call-an-event-handler-using-handles-and-withevents"></a>K volání obslužné rutiny události pomocí obslužných rutin a WithEvents  
  
1.  Ujistěte se, že událost je deklarovaný s [Event – příkaz](../../../../visual-basic/language-reference/statements/event-statement.md).  
  
2.  Deklarace proměnné objektu v modulu nebo třída úrovně, pomocí [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) – klíčové slovo. `As` Klauzuli pro tato proměnná musí být zadána třída, která vyvolá událost.  
  
3.  V deklaraci zpracování událostí `Sub` postupu přidat [zpracovává](../../../../visual-basic/language-reference/statements/handles-clause.md) klauzuli, která určuje, `WithEvents` proměnné a z názvu události.  
  
4.  Když dojde k události, Visual Basic automaticky zavolá `Sub` postupu. Váš kód můžete použít `RaiseEvent` příkaz a ujistěte se, dojde k události.  
  
     V následujícím příkladu definuje události a `WithEvents` proměnné, která odkazuje na třídu, která vyvolává událost. Zpracování událostí `Sub` postup používá `Handles` klauzule zadat třídu a zpracovává události.  
  
     [!code-vb[VbVbcnProcedures#4](./codesnippet/VisualBasic/how-to-call-an-event-handler_1.vb)]  
  
### <a name="to-call-an-event-handler-using-addhandler"></a>K volání obslužné rutiny události pomocí AddHandler  
  
1.  Ujistěte se, že událost je deklarovaný s `Event` příkaz.  
  
2.  Spuštění [AddHandler – příkaz](../../../../visual-basic/language-reference/statements/addhandler-statement.md) dynamicky připojit zpracování událostí `Sub` postup k události.  
  
3.  Když dojde k události, Visual Basic automaticky zavolá `Sub` postupu. Váš kód můžete použít `RaiseEvent` příkaz a ujistěte se, dojde k události.  
  
     V následujícím příkladu definuje `Sub` postup zpracování <xref:System.Windows.Forms.Form.Closing> událost formuláře. Poté použije [AddHandler – příkaz](../../../../visual-basic/language-reference/statements/addhandler-statement.md) přidružit `catchClose` postupu jako obslužné rutiny události pro <xref:System.Windows.Forms.Form.Closing>.  
  
     [!code-vb[VbVbcnProcedures#5](./codesnippet/VisualBasic/how-to-call-an-event-handler_2.vb)]  
  
     Obslužné rutiny události z události můžete zrušit přidružení spuštěním [RemoveHandler – příkaz](../../../../visual-basic/language-reference/statements/removehandler-statement.md).  
  
## <a name="see-also"></a>Viz také  
 [Procedury](./index.md)  
 [Procedury Sub](./sub-procedures.md)  
 [Příkaz Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Operátor AddressOf](../../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Postupy: Vytvoření procedury](./how-to-create-a-procedure.md)  
 [Postupy: Volání procedury, která nevrací hodnotu](./how-to-call-a-procedure-that-does-not-return-a-value.md)
