---
title: Nepovedlo se získat úplný název operačního systému z důvodu vnitřní chyby
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: ecbed5b59d36b1984c0b0ae161821ea99d28e090
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59334637"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a>Nepovedlo se získat úplný název operačního systému z důvodu vnitřní chyby
Nepovedlo se získat úplný název operačního systému z důvodu vnitřní chyby. To může být způsobeno WMI neexistují na aktuálním počítači.  
  
 Volání `My.Computer.Info.OSFullName` vlastnost se nezdařilo. Možnou příčinou této chyby je, pokud není v aktuálním počítači nainstalován Windows Management Instrumentation (WMI).  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Přidat `Try...Catch` blok po volání `My.Computer.Info.OSFullName` vlastnost.  
  
2. Další informace o rozhraní WMI a jak ji nainstalovat, přejděte na, vyhledejte "Windows Management Instrumentation základní".  
  
## <a name="see-also"></a>Viz také:

- [My.Computer.Info.OSFullName](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)
- [Zpracování a vyvolání výjimek v rozhraní .NET](../../standard/exceptions/index.md)
- [Příkaz Try...Catch...Finally](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
