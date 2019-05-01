---
title: 'Řešení potíží: Součásti naslouchající protokolům (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: 12282df50bc42d2a153a9aa8db01f2654acd91ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013852"
---
# <a name="troubleshooting-log-listeners-visual-basic"></a>Řešení potíží: Součásti naslouchající protokolům (Visual Basic)
Můžete použít `My.Application.Log` a `My.Log` objekty k protokolování informací o události, ke kterým dochází ve vaší aplikaci.  
  
 Pokud chcete zjistit, jaké součásti naslouchající protokolům příjem těchto zpráv, najdete v článku [názorný postup: Určení, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).  
  
 `Log` Objektu můžete použít protokol filtrování a omezit tak množství informací, které zaznamenává. Pokud jsou špatně nakonfigurované filtry, protokoly mohou obsahovat nesprávné informace. Další informace o filtrování najdete v tématu [názorný postup: Filtrování výstupu My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).  
  
 Ale pokud protokol není správně nakonfigurovaná, můžete další informace o své aktuální konfiguraci. Můžete získat tyto informace prostřednictvím protokolu rozšířeným `TraceSource` vlastnost.  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a>Chcete-li zjistit součásti naslouchající protokolům pro objekt protokolu v kódu  
  
1. Import <xref:System.Diagnostics> oboru názvů na začátku souboru kódu. Další informace najdete v tématu [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
     [!code-vb[VbVbalrMyApplicationLog#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#13)]  
  
2. Vytvoření funkce, která vrací řetězec obsahující informace pro všechny moduly pro naslouchání v protokolu.  
  
     [!code-vb[VbVbalrMyApplicationLog#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#14)]  
  
3. Kolekce naslouchacích procesů trasování v protokolu k předání `GetListeners` fungovat a zobrazit návratovou hodnotu.  
  
     [!code-vb[VbVbalrMyApplicationLog#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#19)]  
  
     Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Návod: Určení, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
