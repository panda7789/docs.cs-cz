---
title: "Nelze získat úplný název operačního systému z důvodu vnitřní chyby"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 65796c41d2a9fbd03517e7b15bc6b566ba4364fb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a>Nelze získat úplný název operačního systému z důvodu vnitřní chyby
Nelze získat úplný název operačního systému z důvodu vnitřní chyby. To může být způsobeno WMI není existující do aktuálního počítače.  
  
 Volání `My.Computer.Info.OSFullName` vlastností se nezdařilo. Možnou příčinou této chyby je, pokud není v aktuální počítači nainstalována služba Windows Management Instrumentation (WMI).  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Přidat `Try...Catch` bloku kolem volání `My.Computer.Info.OSFullName` vlastnost.  
  
2.  Další informace o rozhraní WMI a k jeho instalaci přejděte na a vyhledejte řetězec "Windows Management Instrumentation základního".  
  
## <a name="see-also"></a>Viz také  
 [Vlastnost My.Computer.Info.OSFullName](http://msdn.microsoft.com/en-us/b3b0fbd1-4dc5-428a-ad04-0d9fc9c2a9be)  
 [Výjimky a zpracování chyb v jazyce Visual Basic](http://msdn.microsoft.com/en-us/3e351e73-cf23-40ab-8b60-05794160529e)  
 [Try... Catch... Finally – příkaz](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
