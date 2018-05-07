---
title: 'Řešení potíží: Součásti naslouchající protokolům (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: 54c3ed0f607edf992fa3c40a8e6214252740587c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="troubleshooting-log-listeners-visual-basic"></a>Řešení potíží: Součásti naslouchající protokolům (Visual Basic)
Můžete použít `My.Application.Log` a `My.Log` objekty k protokolování informací o událostech, ke kterým dochází ve vaší aplikaci.  
  
 Pokud chcete zjistit, kteří posluchači přijímat zprávy, najdete v části [návod: určení kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).  
  
 `Log` Objekt můžete použít filtrování protokolu k omezení množství informací, které zaznamenává. Pokud jsou špatně nakonfigurované filtry, protokol může obsahovat nesprávné informace. Další informace o filtrování najdete v tématu [návod: filtrování výstupu My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).  
  
 Ale pokud protokolu není správně nakonfigurovaná, můžete další informace o své aktuální konfiguraci. Můžete získat tyto informace prostřednictvím protokolu rozšířenou `TraceSource` vlastnost.  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a>Chcete-li zjistit naslouchací procesy pro protokoly pro objekt protokolu v kódu  
  
1.  Import <xref:System.Diagnostics> oboru názvů na začátku souboru kódu. Další informace najdete v tématu [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
     [!code-vb[VbVbalrMyApplicationLog#13](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_1.vb)]  
  
2.  Vytvoří funkci, která vrátí řetězec, který se skládá z informace o pro všechny moduly pro naslouchání v protokolu.  
  
     [!code-vb[VbVbalrMyApplicationLog#14](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_2.vb)]  
  
3.  Předávání kolekce v protokolu trasování – moduly naslouchání na `GetListeners` funkce a zobrazit návratovou hodnotu.  
  
     [!code-vb[VbVbalrMyApplicationLog#19](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_3.vb)]  
  
     Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [Návod: Zjištění, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
