---
title: Protokolování informací z aplikace
ms.date: 07/20/2015
helpviewer_keywords:
- Log object
- My.Log object
- applications [Visual Basic], logging information from
- logging
- My.Application.Log object
- examples [Visual Basic], logging application information
ms.assetid: 8bf4f047-22d6-48d6-aec5-93b98ad5b8e8
ms.openlocfilehash: dace4bac3bf7529b8c50a492a092ad478f4d9e2d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353257"
---
# <a name="logging-information-from-the-application-visual-basic"></a>Protokolování informací z aplikace (Visual Basic)

Tato část obsahuje témata, která pokrývají, jak protokolovat informace z vaší aplikace pomocí objektu `My.Application.Log` nebo `My.Log` a jak rozšiřuje možnosti protokolování aplikace.  
  
 Objekt `Log` poskytuje metody pro zápis informací do protokolu naslouchacího procesu aplikace a vlastnost pokročilé `TraceSource` objektu `Log` poskytuje podrobné informace o konfiguraci. Objekt `Log` je konfigurován pomocí konfiguračního souboru aplikace.  
  
 Objekt `My.Log` je k dispozici pouze pro aplikace ASP.NET. Pro klientské aplikace použijte `My.Application.Log`. Další informace najdete v tématu <xref:Microsoft.VisualBasic.Logging.Log>.  
  
## <a name="tasks"></a>Tasks  
  
|Pro|Další informace naleznete v tématu|  
|--------|---------|  
|Zapište informace události do protokolů aplikace.|[Postupy: Zápis zpráv protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)|  
|Zapište informace o výjimce do protokolů aplikace.|[Postupy: Protokolování výjimek](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)|  
|Zapište trasovací informace do protokolů aplikace při spuštění a ukončení aplikace.|[Postupy: Protokolování zpráv při spuštění nebo ukončení aplikace](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-messages-when-the-application-starts-or-shuts-down.md)|  
|Nakonfigurujte `My.Application.Log` pro zápis informací do textového souboru.|[Postupy: Zápis informací o události do textového souboru](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)|  
|Nakonfigurujte `My.Application.Log` pro zápis informací do protokolu událostí.|[Postupy: Zápis do protokolu událostí aplikace](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)|  
|Změňte, kde `My.Application.Log` zapisuje informace.|[Návod: Změna místa, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)|  
|Určete, kde `My.Application.Log` zapisuje informace.|[Návod: Zjištění, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)|  
|Vytvořte vlastní naslouchací proces protokolu pro `My.Application.Log`.|[Návod: Vytváření vlastních součástí naslouchajících protokolům](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)|  
|Filtrujte výstup protokolů `My.Application.Log`.|[Návod: Filtrování výstupu My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)|  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Řešení potíží: Součásti naslouchající protokolům](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
