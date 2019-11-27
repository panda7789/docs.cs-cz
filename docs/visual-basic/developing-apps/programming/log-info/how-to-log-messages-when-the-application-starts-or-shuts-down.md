---
title: 'Postupy: Protokolování zpráv při spuštění nebo ukončení aplikace'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
ms.openlocfilehash: 5a4ef3888ba8371d26204c3569b5fb9bae1f15f2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352098"
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a>Postupy: Protokolování zpráv při spuštění nebo ukončení aplikace (Visual Basic)

Pomocí objektů `My.Application.Log` a `My.Log` můžete protokolovat informace o událostech, ke kterým dochází ve vaší aplikaci. Tento příklad ukazuje, jak použít metodu `My.Application.Log.WriteEntry` s událostmi `Startup` a `Shutdown` k zápisu trasovacích informací.  
  
### <a name="to-access-the-applications-event-handler-code"></a>Přístup k kódu obslužné rutiny událostí aplikace  
  
1. Máte projekt vybraný v **Průzkumník řešení**. V nabídce **projekt** klikněte na příkaz **vlastnosti**.  
  
2. Klikněte na kartu **aplikace** .  
  
3. Kliknutím na tlačítko **Zobrazit události aplikace** otevřete Editor kódu.  
  
     Tím se otevře soubor ApplicationEvents. vb.  
  
### <a name="to-log-messages-when-the-application-starts"></a>Protokolování zpráv při spuštění aplikace  
  
1. Otevřete soubor ApplicationEvents. vb v editoru kódu. V nabídce **Obecné** vyberte **události MyApplication**.  
  
2. V nabídce **deklarace** vyberte možnost **po spuštění**.  
  
     Aplikace vyvolá událost <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> před spuštěním hlavní aplikace.  
  
3. Přidejte metodu `My.Application.Log.WriteEntry` do obslužné rutiny události `Startup`.  
  
     [!code-vb[VbVbalrMyApplicationLog#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#1)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a>Protokolování zpráv při ukončení aplikace  
  
1. Otevřete soubor ApplicationEvents. vb v editoru kódu. V nabídce **Obecné** vyberte **události MyApplication**.  
  
2. V nabídce **deklarace** vyberte možnost **vypnout**.  
  
     Aplikace vyvolá událost <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> po spuštění hlavní aplikace, ale před vypnutím.  
  
3. Přidejte metodu `My.Application.Log.WriteEntry` do obslužné rutiny události `Shutdown`.  
  
     [!code-vb[VbVbalrMyApplicationLog#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#2)]  
  
## <a name="example"></a>Příklad  

 **Návrhář projektu** můžete použít pro přístup k událostem aplikace v editoru kódu. Další informace naleznete na [stránce aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
 [!code-vb[VbVbalrMyApplicationLog#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Stránka Aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
