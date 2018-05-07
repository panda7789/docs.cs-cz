---
title: 'Postupy: Protokolování výjimek v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
ms.openlocfilehash: b8ec45f43438f8181d9e045cdf43c81db34e4242
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-log-exceptions-in-visual-basic"></a>Postupy: Protokolování výjimek v jazyce Visual Basic
Můžete použít `My.Application.Log` a `My.Log` objekty k protokolování informací o výjimkách, ke kterým dochází ve vaší aplikaci. Tyto příklady ukazují, jak používat `My.Application.Log.WriteException` metoda do protokolu explicitně a výjimek, které nejsou zpracovány.  
  
 Protokolování informací o trasování, použijte `My.Application.Log.WriteEntry` metoda. Další informace najdete v tématu <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
  
### <a name="to-log-a-handled-exception"></a>Do protokolu zpracování výjimek  
  
1.  Vytvořte metodu, která bude generovat informace o výjimce.  
  
     [!code-vb[VbVbalrMyApplicationLog#9](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_1.vb)]  
  
2.  Použití `Try...Catch` blok k zachycení výjimky.  
  
     [!code-vb[VbVbalrMyApplicationLog#6](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_2.vb)]  
  
3.  Vložit kód, který může generovat výjimky v `Try` bloku.  
  
     Zrušením komentáře u `Dim` a `MsgBox` řádky způsobí <xref:System.NullReferenceException> výjimka.  
  
     [!code-vb[VbVbalrMyApplicationLog#7](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_3.vb)]  
  
4.  V `Catch` blokovat, použijte `My.Application.Log.WriteException` metoda zapsat informace o výjimce.  
  
     [!code-vb[VbVbalrMyApplicationLog#8](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_4.vb)]  
  
     Následující příklad ukazuje kód dokončení pro protokolování zpracování výjimek.  
  
     [!code-vb[VbVbalrMyApplicationLog#10](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_5.vb)]  
  
### <a name="to-log-an-unhandled-exception"></a>K přihlášení k neošetřené výjimce  
  
1.  Máte projekt vybraný v **Průzkumníku řešení**. Na **projektu** nabídce zvolte **vlastnosti**.  
  
2.  Klikněte **aplikace** kartě.  
  
3.  Klikněte **zobrazení události aplikace** tlačítko otevřete Editor kódu.  
  
     Otevře se soubor ApplicationEvents.vb.  
  
4.  Byl ApplicationEvents.vb otevřen v editoru kódu. Na **Obecné** nabídce zvolte **Moje_aplikace události**.  
  
5.  Na **deklarace** nabídce zvolte **UnhandledException**.  
  
     Aplikace vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> událostí před spuštěním hlavní aplikace.  
  
6.  Přidat `My.Application.Log.WriteException` metodu `UnhandledException` obslužné rutiny události.  
  
     [!code-vb[VbVbalrMyApplicationLog#4](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_6.vb)]  
  
     Následující příklad ukazuje kód dokončení pro protokolování neošetřené výjimky.  
  
     [!code-vb[VbVbalrMyApplicationLog#5](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_7.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [Postupy: Zápis zpráv protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [Návod: Zjištění, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)  
 [Návod: Změna místa, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
