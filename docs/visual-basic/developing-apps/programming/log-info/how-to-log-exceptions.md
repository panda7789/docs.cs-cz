---
title: 'Postupy: Výjimky protokolu v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
ms.openlocfilehash: 53bf93a326123ddb1e26ef5964fa057148505116
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59307220"
---
# <a name="how-to-log-exceptions-in-visual-basic"></a>Postupy: Výjimky protokolu v jazyce Visual Basic
Můžete použít `My.Application.Log` a `My.Log` objekty k protokolování informací o výjimkách, ke kterým dochází ve vaší aplikaci. Tyto příklady ukazují, jak používat `My.Application.Log.WriteException` metody do protokolu výjimky, které explicitně a výjimek, které nejsou zpracovány.  
  
 Protokolování informací o trasování, použijte `My.Application.Log.WriteEntry` metody. Další informace najdete v tématu <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
  
### <a name="to-log-a-handled-exception"></a>Do protokolu zpracování výjimek  
  
1. Vytvořte metodu, která bude generovat informace o výjimce.  
  
     [!code-vb[VbVbalrMyApplicationLog#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#9)]  
  
2. Použití `Try...Catch` bloku pro zachycení výjimky.  
  
     [!code-vb[VbVbalrMyApplicationLog#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#6)]  
  
3. Vložte kód, který může způsobit výjimku v `Try` bloku.  
  
     Zrušením komentáře u `Dim` a `MsgBox` řádky způsobí <xref:System.NullReferenceException> výjimky.  
  
     [!code-vb[VbVbalrMyApplicationLog#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#7)]  
  
4. V `Catch` zablokuje, použít `My.Application.Log.WriteException` metody zapsat informace o výjimce.  
  
     [!code-vb[VbVbalrMyApplicationLog#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#8)]  
  
     Následující příklad ukazuje kompletní kód pro protokolování zpracování výjimek.  
  
     [!code-vb[VbVbalrMyApplicationLog#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#10)]  
  
### <a name="to-log-an-unhandled-exception"></a>K protokolování neošetřené výjimky  
  
1. Mají projekt vybraný v **Průzkumníka řešení**. Na **projektu** nabídce zvolte **vlastnosti**.  
  
2. Klikněte na tlačítko **aplikace** kartu.  
  
3. Klikněte na tlačítko **zobrazení události aplikace** tlačítko k otevření editoru kódu.  
  
     Tím se otevře soubor ApplicationEvents.vb.  
  
4. Máte ApplicationEvents.vb soubor otevřete v editoru kódu. Na **Obecné** nabídce zvolte **události MyApplication**.  
  
5. Na **deklarace** nabídce zvolte **UnhandledException**.  
  
     Aplikace vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> událostí před spuštěním hlavní aplikace.  
  
6. Přidat `My.Application.Log.WriteException` metodu `UnhandledException` obslužné rutiny události.  
  
     [!code-vb[VbVbalrMyApplicationLog#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#4)]  
  
     Následující příklad ukazuje kompletní kód pro protokolování neošetřené výjimce.  
  
     [!code-vb[VbVbalrMyApplicationLog#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Postupy: Zápis zpráv protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [Návod: Určení, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [Návod: Změna, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
