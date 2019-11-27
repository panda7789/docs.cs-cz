---
title: 'Postupy: volání obslužné rutiny události'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
ms.openlocfilehash: 0c626a9ad92fe2cd0ea117a9abdd2965a09df2ea
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340418"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a>Postupy: Volání obslužné rutiny události (Visual Basic)

*Událost* je akce nebo výskyt – například kliknutí myší nebo překročení limitu úvěru, který je rozpoznáván některými součástmi programu a pro které můžete napsat kód, který bude reagovat. *Obslužná rutina události* je kód, který zapisujete pro reakci na událost.

 Obslužná rutina události v Visual Basic je `Sub` postup. Nebudete je ale normálně volat stejným způsobem jako jiné `Sub` postupy. Místo toho identifikujete proceduru jako obslužnou rutinu pro událost. To lze provést buď s klauzulí [Handles](../../../language-reference/statements/handles-clause.md) , a s proměnnou [WithEvents](../../../language-reference/modifiers/withevents.md) nebo s [příkazem AddHandler](../../../language-reference/statements/addhandler-statement.md). Použití klauzule `Handles` je výchozí způsob, jak deklarovat obslužnou rutinu události v Visual Basic. Toto je způsob, jakým jsou obslužné rutiny události zapisovány návrháři při programování v integrovaném vývojovém prostředí (IDE). Příkaz `AddHandler` je vhodný pro dynamické vyvolání událostí v době běhu.

 Když dojde k události, Visual Basic automaticky volá proceduru obslužné rutiny události. Jakýkoli kód, který má přístup k události, může způsobit, že dojde k provedení [příkazu RaiseEvent](../../../language-reference/statements/raiseevent-statement.md).

 Ke stejné události můžete přidružit více než jednu obslužnou rutinu události. V některých případech můžete zrušit přidružení obslužné rutiny od události. Další informace najdete v tématu [události](../events/index.md).

### <a name="to-call-an-event-handler-using-handles-and-withevents"></a>Volání obslužné rutiny události pomocí obslužných rutin a WithEvents

1. Ujistěte se, že je událost deklarovaná pomocí [příkazu Event](../../../language-reference/statements/event-statement.md).

2. Deklarujte proměnnou objektu na úrovni modulu nebo třídy pomocí klíčového slova [WithEvents](../../../language-reference/modifiers/withevents.md) . Klauzule `As` pro tuto proměnnou musí určovat třídu, která vyvolá událost.

3. V deklaraci procedury `Sub` zpracování událostí přidejte klauzuli [Handles](../../../language-reference/statements/handles-clause.md) , která určuje `WithEvents` proměnnou a název události.

4. Když dojde k události, Visual Basic automaticky volá proceduru `Sub`. Váš kód může použít příkaz `RaiseEvent` k tomu, aby došlo k události.

     Následující příklad definuje událost a `WithEvents` proměnnou, která odkazuje na třídu, která vyvolává událost. Procedura `Sub` zpracování událostí používá klauzuli `Handles` k určení třídy a události, kterou zpracovává.

     [!code-vb[VbVbcnProcedures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#4)]

### <a name="to-call-an-event-handler-using-addhandler"></a>Volání obslužné rutiny události pomocí AddHandler

1. Ujistěte se, že je událost deklarovaná pomocí příkazu `Event`.

2. Spusťte [příkaz AddHandler](../../../language-reference/statements/addhandler-statement.md) , který dynamicky připojí proceduru zpracování události `Sub` s událostí.

3. Když dojde k události, Visual Basic automaticky volá proceduru `Sub`. Váš kód může použít příkaz `RaiseEvent` k tomu, aby došlo k události.

     Následující příklad definuje `Sub` postup pro zpracování události <xref:System.Windows.Forms.Form.Closing> formuláře. Pak použije [příkaz AddHandler](../../../language-reference/statements/addhandler-statement.md) k přidružení `catchClose` procedury jako obslužné rutiny události pro <xref:System.Windows.Forms.Form.Closing>.

     [!code-vb[VbVbcnProcedures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#5)]

     Můžete zrušit přidružení obslužné rutiny události z události spuštěním [příkazu removeHandler](../../../language-reference/statements/removehandler-statement.md).

## <a name="see-also"></a>Viz také:

- [Procedury](index.md)
- [Procedury Sub](sub-procedures.md)
- [Příkaz Sub](../../../language-reference/statements/sub-statement.md)
- [Operátor AddressOf](../../../language-reference/operators/addressof-operator.md)
- [Postupy: Vytvoření procedury](how-to-create-a-procedure.md)
- [Postupy: Volání procedury, která nevrací hodnotu](how-to-call-a-procedure-that-does-not-return-a-value.md)
