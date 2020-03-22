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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352098"
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a>Postupy: Protokolování zpráv při spuštění nebo ukončení aplikace (Visual Basic)

Objekty `My.Application.Log` a `My.Log` můžete použít k protokolování informací o událostech, ke kterým dochází ve vaší aplikaci. Tento příklad ukazuje, `My.Application.Log.WriteEntry` jak používat `Startup` `Shutdown` metodu s a události k zápisu trasování informace.  
  
### <a name="to-access-the-applications-event-handler-code"></a>Přístup ke kódu obslužné rutiny události aplikace  
  
1. V **Průzkumníku řešení**je vybrán projekt . V nabídce **Projekt** zvolte **Vlastnosti**.  
  
2. Klikněte na kartu **Aplikace.**  
  
3. Kliknutím na tlačítko **Zobrazit události aplikace** otevřete Editor kódu.  
  
     Tím se otevře soubor ApplicationEvents.vb.  
  
### <a name="to-log-messages-when-the-application-starts"></a>Protokolování zpráv při spuštění aplikace  
  
1. Otevřete soubor ApplicationEvents.vb v Editoru kódu. V nabídce **Obecné** zvolte **MyApplication Events**.  
  
2. V nabídce **Declarations** zvolte **Startup**.  
  
     Aplikace vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> událost před spuštěním hlavní aplikace.  
  
3. Přidejte `My.Application.Log.WriteEntry` metodu `Startup` do obslužné rutiny události.  
  
     [!code-vb[VbVbalrMyApplicationLog#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#1)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a>Protokolování zpráv při vypnutí aplikace  
  
1. Otevřete soubor ApplicationEvents.vb v Editoru kódu. V nabídce **Obecné** zvolte **MyApplication Events**.  
  
2. V nabídce **Declarations** zvolte **Shutdown**.  
  
     Aplikace vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> událost po spuštění hlavní aplikace, ale před jeho vypnutím.  
  
3. Přidejte `My.Application.Log.WriteEntry` metodu `Shutdown` do obslužné rutiny události.  
  
     [!code-vb[VbVbalrMyApplicationLog#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#2)]  
  
## <a name="example"></a>Příklad  

 **Návrháře projektu** můžete použít pro přístup k událostem aplikace v Editoru kódu. Další informace naleznete v [tématu Stránka aplikace, Návrhář projektu (Visual Basic).](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
  
 [!code-vb[VbVbalrMyApplicationLog#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#3)]  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Stránka Aplikace, návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
