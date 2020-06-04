---
title: 'Postupy: Protokolování výjimek'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
ms.openlocfilehash: 59ed7b836126a38f32b7c6f479570a566d236e6c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410111"
---
# <a name="how-to-log-exceptions-in-visual-basic"></a>Postupy: Protokolování výjimek v jazyce Visual Basic

Pomocí `My.Application.Log` objektů a můžete `My.Log` protokolovat informace o výjimkách, ke kterým dochází ve vaší aplikaci. Tyto příklady ukazují, jak použít `My.Application.Log.WriteException` metodu k protokolování výjimek, které jsou zachyceny explicitně a výjimek, které jsou neošetřené.  
  
 Pro informace o trasování protokolu použijte `My.Application.Log.WriteEntry` metodu. Další informace najdete v tématu <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>.  
  
### <a name="to-log-a-handled-exception"></a>Protokolování ošetřené výjimky  
  
1. Vytvořte metodu, která bude generovat informace o výjimce.  
  
     [!code-vb[VbVbalrMyApplicationLog#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#9)]  
  
2. `Try...Catch`K zachycení výjimky použijte blok.  
  
     [!code-vb[VbVbalrMyApplicationLog#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#6)]  
  
3. Vložte kód, který by mohl vytvořit výjimku v `Try` bloku.  
  
     Odkomentujte `Dim` řádky a, `MsgBox` abyste způsobili <xref:System.NullReferenceException> výjimku.  
  
     [!code-vb[VbVbalrMyApplicationLog#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#7)]  
  
4. V `Catch` bloku použijte `My.Application.Log.WriteException` metodu k zápisu informací o výjimce.  
  
     [!code-vb[VbVbalrMyApplicationLog#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#8)]  
  
     Následující příklad ukazuje úplný kód pro protokolování ošetřené výjimky.  
  
     [!code-vb[VbVbalrMyApplicationLog#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#10)]  
  
### <a name="to-log-an-unhandled-exception"></a>Postup při protokolování neošetřené výjimky  
  
1. Máte projekt vybraný v **Průzkumník řešení**. V nabídce **projekt** klikněte na příkaz **vlastnosti**.  
  
2. Klikněte na kartu **aplikace** .  
  
3. Kliknutím na tlačítko **Zobrazit události aplikace** otevřete Editor kódu.  
  
     Tím se otevře soubor ApplicationEvents. vb.  
  
4. Otevřete soubor ApplicationEvents. vb v editoru kódu. V nabídce **Obecné** vyberte **události MyApplication**.  
  
5. V nabídce **deklarace** vyberte možnost **UnhandledException**.  
  
     Aplikace vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> událost před spuštěním hlavní aplikace.  
  
6. Přidejte `My.Application.Log.WriteException` metodu do `UnhandledException` obslužné rutiny události.  
  
     [!code-vb[VbVbalrMyApplicationLog#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#4)]  
  
     Následující příklad ukazuje úplný kód pro protokolování neošetřené výjimky.  
  
     [!code-vb[VbVbalrMyApplicationLog#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#5)]  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Práce s protokoly aplikací](working-with-application-logs.md)
- [Postupy: Zápis zpráv protokolu](how-to-write-log-messages.md)
- [Návod: Zjištění, kam objekt My.Application.Log zapisuje informace](walkthrough-determining-where-my-application-log-writes-information.md)
- [Návod: Změna místa, kam objekt My.Application.Log zapisuje informace](walkthrough-changing-where-my-application-log-writes-information.md)
