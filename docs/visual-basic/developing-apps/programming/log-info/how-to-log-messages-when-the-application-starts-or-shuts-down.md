---
title: 'Postupy: Protokolování zpráv při spuštění aplikace nebo jejím ukončení (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
ms.openlocfilehash: 20eabd08db0763ec08bb28add41ff63fa3196dd6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585627"
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a>Postupy: Protokolování zpráv při spuštění aplikace nebo jejím ukončení (Visual Basic)
Můžete použít `My.Application.Log` a `My.Log` objekty k protokolování informací o události, ke kterým dochází ve vaší aplikaci. Tento příklad ukazuje způsob použití `My.Application.Log.WriteEntry` metodou `Startup` a `Shutdown` události zapsat informace trasování.  
  
### <a name="to-access-the-applications-event-handler-code"></a>Přístup ke kódu obslužnou rutinu události aplikace  
  
1.  Mají projekt vybraný v **Průzkumníka řešení**. Na **projektu** nabídce zvolte **vlastnosti**.  
  
2.  Klikněte na tlačítko **aplikace** kartu.  
  
3.  Klikněte na tlačítko **zobrazení události aplikace** tlačítko k otevření editoru kódu.  
  
     Tím se otevře soubor ApplicationEvents.vb.  
  
### <a name="to-log-messages-when-the-application-starts"></a>Protokolování zpráv při spuštění aplikace  
  
1.  Máte ApplicationEvents.vb soubor otevřete v editoru kódu. Na **Obecné** nabídce zvolte **události MyApplication**.  
  
2.  Na **deklarace** nabídce zvolte **spuštění**.  
  
     Aplikace vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> událostí před spuštěním hlavní aplikace.  
  
3.  Přidat `My.Application.Log.WriteEntry` metodu `Startup` obslužné rutiny události.  
  
     [!code-vb[VbVbalrMyApplicationLog#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_1.vb)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a>Protokolování zpráv při ukončení aplikace  
  
1.  Máte ApplicationEvents.vb soubor otevřete v editoru kódu. Na **Obecné** nabídce zvolte **události MyApplication**.  
  
2.  Na **deklarace** nabídce zvolte **vypnutí**.  
  
     Aplikace vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> událostí po spuštění hlavní aplikace, ale předtím, než ho ukončí.  
  
3.  Přidat `My.Application.Log.WriteEntry` metodu `Shutdown` obslužné rutiny události.  
  
     [!code-vb[VbVbalrMyApplicationLog#2](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_2.vb)]  
  
## <a name="example"></a>Příklad  
 Můžete použít **Návrháře projektu** přistupovat k událostem aplikace v editoru kódu. Další informace najdete v tématu [stránka aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
 [!code-vb[VbVbalrMyApplicationLog#3](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_3.vb)]  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Stránka Aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
