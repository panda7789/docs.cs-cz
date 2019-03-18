---
title: Nepovedlo se získat úplný název operačního systému z důvodu vnitřní chyby
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: 6a0e24743c861ba92fc284a84fa4ef26e2ee48a8
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2019
ms.locfileid: "58022768"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a>Nepovedlo se získat úplný název operačního systému z důvodu vnitřní chyby
Nepovedlo se získat úplný název operačního systému z důvodu vnitřní chyby. To může být způsobeno WMI neexistují na aktuálním počítači.  
  
 Volání `My.Computer.Info.OSFullName` vlastnost se nezdařilo. Možnou příčinou této chyby je, pokud není v aktuálním počítači nainstalován Windows Management Instrumentation (WMI).  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Přidat `Try...Catch` blok po volání `My.Computer.Info.OSFullName` vlastnost.  
  
2.  Další informace o rozhraní WMI a jak ji nainstalovat, přejděte na, vyhledejte "Windows Management Instrumentation základní".  
  
## <a name="see-also"></a>Viz také:

- [My.Computer.Info.OSFullName](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)
- [Zpracování a vyvolání výjimek v rozhraní .NET](../../standard/exceptions/index.md)
- [Příkaz Try...Catch...Finally](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
