---
title: 'Postupy: Volání obslužné rutiny událostí v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
ms.openlocfilehash: 58a96ccd06b70d481de335af5c3cd2be565cbd92
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973519"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a>Postupy: Volání obslužné rutiny událostí v jazyce Visual Basic
*Události* je akce nebo výskyt – například myši klikněte na tlačítko nebo kreditního limitu překročil – v některých součástí programu, a pro která můžete napsat kód, který je rozpoznán reagovat. *Obslužná rutina události* se psaní kódu pro reakci na událost.  
  
 Obslužné rutiny události v jazyce Visual Basic je `Sub` postup. Však můžete normálně ho nevolají stejný způsobem jako ostatní `Sub` postupy. Místo toho postup identifikovat jako obslužnou rutinu pro událost. Uděláte to buď s [zpracovává](../../../../visual-basic/language-reference/statements/handles-clause.md) klauzule a [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) proměnnou, nebo s [AddHandler – příkaz](../../../../visual-basic/language-reference/statements/addhandler-statement.md). Použití `Handles` klauzule je výchozí způsob, jak deklarovat obslužné rutiny události v jazyce Visual Basic. Toto je způsob, jakým obslužné rutiny událostí jsou zapsány pomocí návrhářů, když je program v integrovaném vývojovém prostředí (IDE). `AddHandler` Příkaz je vhodný pro vyvolání události dynamicky za běhu.  
  
 Při výskytu události, Visual Basic automaticky volá proceduru obslužné rutiny události. Veškerý kód, který má přístup k této události může způsobit, že dojde k spuštěním [RaiseEvent – příkaz](../../../../visual-basic/language-reference/statements/raiseevent-statement.md).  
  
 Více než jednu obslužnou rutinu události můžete přidružit stejné události. V některých případech můžete zrušit přidružení obslužné rutiny z události. Další informace najdete v tématu [události](../../../../visual-basic/programming-guide/language-features/events/index.md).  
  
### <a name="to-call-an-event-handler-using-handles-and-withevents"></a>Pro volání obslužné rutiny události pomocí obslužné rutiny a WithEvents  
  
1.  Ujistěte se, že událost je deklarována pomocí [Event – příkaz](../../../../visual-basic/language-reference/statements/event-statement.md).  
  
2.  Deklarace proměnné objektu v modulu nebo třídy úrovni pomocí [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) – klíčové slovo. `As` Klauzuli pro tuto proměnnou musí být zadána třída, která vyvolává událost.  
  
3.  V prohlášení o zpracování událostí `Sub` postupu přidat [zpracovává](../../../../visual-basic/language-reference/statements/handles-clause.md) klauzuli, která určuje, `WithEvents` proměnné a název události.  
  
4.  Při výskytu události, Visual Basic automaticky volá `Sub` postup. Váš kód může použít `RaiseEvent` příkaz, ujistěte se, dojde k události.  
  
     Následující příklad definuje události a `WithEvents` proměnné, která odkazuje na třídu, která vyvolává událost. Zpracování událostí `Sub` postup používá `Handles` klauzule k určení třídy a zpracovává události.  
  
     [!code-vb[VbVbcnProcedures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#4)]  
  
### <a name="to-call-an-event-handler-using-addhandler"></a>Pro volání obslužné rutiny události pomocí AddHandler  
  
1.  Ujistěte se, že událost je deklarována pomocí `Event` příkazu.  
  
2.  Spuštění [AddHandler – příkaz](../../../../visual-basic/language-reference/statements/addhandler-statement.md) dynamicky připojit zpracování událostí `Sub` procedury s událostí.  
  
3.  Při výskytu události, Visual Basic automaticky volá `Sub` postup. Váš kód může použít `RaiseEvent` příkaz, ujistěte se, dojde k události.  
  
     Následující příklad definuje `Sub` postupu ke zpracování <xref:System.Windows.Forms.Form.Closing> událost formuláře. Poté použije [AddHandler – příkaz](../../../../visual-basic/language-reference/statements/addhandler-statement.md) přidružení `catchClose` postupu jako obslužná rutina události <xref:System.Windows.Forms.Form.Closing>.  
  
     [!code-vb[VbVbcnProcedures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#5)]  
  
     Obslužná rutina události z události můžete oddělit pomocí provádí [RemoveHandler – příkaz](../../../../visual-basic/language-reference/statements/removehandler-statement.md).  
  
## <a name="see-also"></a>Viz také:
- [Procedury](./index.md)
- [Procedury Sub](./sub-procedures.md)
- [Příkaz Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Operátor AddressOf](../../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Postupy: Vytvoření procedury](./how-to-create-a-procedure.md)
- [Postupy: Volání procedury, která nevrací hodnotu](./how-to-call-a-procedure-that-does-not-return-a-value.md)
