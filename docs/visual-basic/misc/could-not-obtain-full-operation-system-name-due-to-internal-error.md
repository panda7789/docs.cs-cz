---
title: Nelze získat úplný název operačního systému z důvodu vnitřní chyby
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: f85ca5f7f325cb0dd2b8fc55d3f90f6abdfd4a7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a>Nelze získat úplný název operačního systému z důvodu vnitřní chyby
Nelze získat úplný název operačního systému z důvodu vnitřní chyby. To může být způsobeno WMI není existující do aktuálního počítače.  
  
 Volání `My.Computer.Info.OSFullName` vlastností se nezdařilo. Možnou příčinou této chyby je, pokud není v aktuální počítači nainstalována služba Windows Management Instrumentation (WMI).  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Přidat `Try...Catch` bloku kolem volání `My.Computer.Info.OSFullName` vlastnost.  
  
2.  Další informace o rozhraní WMI a k jeho instalaci přejděte na a vyhledejte řetězec "Windows Management Instrumentation základního".  
  
## <a name="see-also"></a>Viz také  
 [My.Computer.Info.OSFullName](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)  
 [Výjimky a zpracování chyb v jazyce Visual Basic](http://msdn.microsoft.com/library/3e351e73-cf23-40ab-8b60-05794160529e)  
 [Příkaz Try...Catch...Finally](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
