---
title: 'Postupy: Volání obslužné rutiny události v Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
ms.openlocfilehash: a9e090e83b180686ccb832aa6efb314c7e0fcc9a
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216625"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a>Postupy: Volání obslužné rutiny události v Visual Basic

*Událost* je akce nebo výskyt – například kliknutí myší nebo překročení limitu úvěru, který je rozpoznáván některými součástmi programu a pro které můžete napsat kód, který bude reagovat. *Obslužná rutina události* je kód, který zapisujete pro reakci na událost.

 Obslužná rutina události v Visual Basic je `Sub` procedura. Nebudete je však obvykle volat stejným způsobem jako jiné `Sub` postupy. Místo toho identifikujete proceduru jako obslužnou rutinu pro událost. To lze provést buď s klauzulí [Handles](../../../language-reference/statements/handles-clause.md) , a s proměnnou [WithEvents](../../../language-reference/modifiers/withevents.md) nebo s [příkazem AddHandler](../../../language-reference/statements/addhandler-statement.md). `Handles` Použití klauzule je výchozí způsob, jak deklarovat obslužnou rutinu události v Visual Basic. Toto je způsob, jakým jsou obslužné rutiny události zapisovány návrháři při programování v integrovaném vývojovém prostředí (IDE). `AddHandler` Příkaz je vhodný pro dynamické vyvolání událostí v době běhu.

 Když dojde k události, Visual Basic automaticky volá proceduru obslužné rutiny události. Jakýkoli kód, který má přístup k události, může způsobit, že dojde k provedení [příkazu RaiseEvent](../../../language-reference/statements/raiseevent-statement.md).

 Ke stejné události můžete přidružit více než jednu obslužnou rutinu události. V některých případech můžete zrušit přidružení obslužné rutiny od události. Další informace najdete v tématu [události](../events/index.md).

### <a name="to-call-an-event-handler-using-handles-and-withevents"></a>Volání obslužné rutiny události pomocí obslužných rutin a WithEvents

1. Ujistěte se, že je událost deklarovaná pomocí [příkazu Event](../../../language-reference/statements/event-statement.md).

2. Deklarujte proměnnou objektu na úrovni modulu nebo třídy pomocí klíčového slova [WithEvents](../../../language-reference/modifiers/withevents.md) . `As` Klauzule pro tuto proměnnou musí určovat třídu, která vyvolá událost.

3. V deklaraci procedury zpracování `Sub` událostí přidejte `WithEvents` klauzuli [Handles](../../../language-reference/statements/handles-clause.md) , která určuje proměnnou a název události.

4. Když dojde k události, Visual Basic automaticky volá `Sub` proceduru. Váš kód může použít `RaiseEvent` příkaz k provedení události.

     Následující příklad definuje událost a `WithEvents` proměnnou, která odkazuje na třídu, která vyvolá událost. Procedura zpracování `Sub` událostí `Handles` používá klauzuli k určení třídy a události, kterou zpracovává.

     [!code-vb[VbVbcnProcedures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#4)]

### <a name="to-call-an-event-handler-using-addhandler"></a>Volání obslužné rutiny události pomocí AddHandler

1. Ujistěte se, že je událost deklarovaná `Event` pomocí příkazu.

2. Spusťte [příkaz AddHandler](../../../language-reference/statements/addhandler-statement.md) k dynamickému propojení procedury zpracování `Sub` události s událostí.

3. Když dojde k události, Visual Basic automaticky volá `Sub` proceduru. Váš kód může použít `RaiseEvent` příkaz k provedení události.

     Následující příklad definuje `Sub` proceduru pro <xref:System.Windows.Forms.Form.Closing> zpracování události formuláře. Pak použije [příkaz AddHandler](../../../language-reference/statements/addhandler-statement.md) k přidružení `catchClose` procedury jako obslužné rutiny události pro <xref:System.Windows.Forms.Form.Closing>.

     [!code-vb[VbVbcnProcedures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#5)]

     Můžete zrušit přidružení obslužné rutiny události z události spuštěním [příkazu removeHandler](../../../language-reference/statements/removehandler-statement.md).

## <a name="see-also"></a>Viz také:

- [Procedury](index.md)
- [Procedury Sub](sub-procedures.md)
- [Příkaz Sub](../../../language-reference/statements/sub-statement.md)
- [Operátor AddressOf](../../../language-reference/operators/addressof-operator.md)
- [Postupy: Vytvořit proceduru](how-to-create-a-procedure.md)
- [Postupy: Volání procedury, která nevrací hodnotu](how-to-call-a-procedure-that-does-not-return-a-value.md)
