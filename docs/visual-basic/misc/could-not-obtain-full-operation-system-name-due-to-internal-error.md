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
ms.openlocfilehash: c67d47126718c3d90d853add61b7d06aaf84fc70
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a>Nelze získat úplný název operačního systému z důvodu vnitřní chyby
Nelze získat úplný název operačního systému z důvodu vnitřní chyby. To může být způsobeno WMI není existující do aktuálního počítače.  
  
 Volání `My.Computer.Info.OSFullName` vlastností se nezdařilo. Možnou příčinou této chyby je, pokud není v aktuální počítači nainstalována služba Windows Management Instrumentation (WMI).  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Přidat `Try...Catch` bloku kolem volání `My.Computer.Info.OSFullName` vlastnost.  
  
2.  Další informace o rozhraní WMI a k jeho instalaci přejděte na a vyhledejte řetězec "Windows Management Instrumentation základního".  
  
## <a name="see-also"></a>Viz také  
 [My.Computer.Info.OSFullName](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)  
 [Výjimky a zpracování chyb v jazyce Visual Basic](http://msdn.microsoft.com/en-us/3e351e73-cf23-40ab-8b60-05794160529e)  
 [Příkaz Try...Catch...Finally](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
