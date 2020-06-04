---
title: Protokolování informací z aplikace
ms.date: 07/20/2015
helpviewer_keywords:
- Log object
- My.Log object
- applications [Visual Basic], logging information from
- logging
- My.Application.Log object
- examples [Visual Basic], logging application information
ms.assetid: 8bf4f047-22d6-48d6-aec5-93b98ad5b8e8
ms.openlocfilehash: 43738b2d654435532a98654cbc40af134d43f02c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410020"
---
# <a name="logging-information-from-the-application-visual-basic"></a>Protokolování informací z aplikace (Visual Basic)

Tato část obsahuje témata, která pokrývají, jak protokolovat informace z vaší aplikace pomocí `My.Application.Log` `My.Log` objektu nebo a jak rozšiřuje možnosti protokolování aplikace.  
  
 `Log`Objekt poskytuje metody pro zápis informací do protokolu naslouchacího procesu aplikace a `Log` vlastnost Advanced objektu `TraceSource` poskytuje podrobné informace o konfiguraci. `Log`Objekt je konfigurován pomocí konfiguračního souboru aplikace.  
  
 `My.Log`Objekt je k dispozici pouze pro aplikace ASP.NET. Pro klientské aplikace použijte `My.Application.Log` . Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Logging.Log>.  
  
## <a name="tasks"></a>Úlohy  
  
|Akce|Seznamte se s |  
|--------|---------|  
|Zapište informace události do protokolů aplikace.|[Postupy: Zápis zpráv protokolu](how-to-write-log-messages.md)|  
|Zapište informace o výjimce do protokolů aplikace.|[Postupy: Protokolování výjimek](how-to-log-exceptions.md)|  
|Zapište trasovací informace do protokolů aplikace při spuštění a ukončení aplikace.|[Postupy: Protokolování zpráv při spuštění nebo ukončení aplikace](how-to-log-messages-when-the-application-starts-or-shuts-down.md)|  
|Nakonfigurujte `My.Application.Log` pro zápis informací do textového souboru.|[Postupy: Zápis informací o události do textového souboru](how-to-write-event-information-to-a-text-file.md)|  
|Nakonfigurujte `My.Application.Log` , aby se zapisovaly informace do protokolu událostí.|[Postupy: Zápis do protokolu událostí aplikace](how-to-write-to-an-application-event-log.md)|  
|Změnit, kde `My.Application.Log` zapisuje informace.|[Návod: Změna místa, kam objekt My.Application.Log zapisuje informace](walkthrough-changing-where-my-application-log-writes-information.md)|  
|Určete, kde `My.Application.Log` zapisuje informace.|[Návod: Zjištění, kam objekt My.Application.Log zapisuje informace](walkthrough-determining-where-my-application-log-writes-information.md)|  
|Vytvořte vlastní naslouchací proces protokolu pro `My.Application.Log` .|[Návod: Vytváření vlastních součástí naslouchajících protokolům](walkthrough-creating-custom-log-listeners.md)|  
|Filtrujte výstup `My.Application.Log` protokolů.|[Návod: Filtrování výstupu My.Application.Log](walkthrough-filtering-my-application-log-output.md)|  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Práce s protokoly aplikací](working-with-application-logs.md)
- [Řešení potíží: Komponenty naslouchající protokolům](troubleshooting-log-listeners.md)
