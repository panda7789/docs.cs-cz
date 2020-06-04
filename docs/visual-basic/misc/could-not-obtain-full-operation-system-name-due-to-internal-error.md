---
title: Kvůli vnitřní chybě se nepovedlo získat úplný název operačního systému.
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: 67e8fb5e906800d28bf15714463b7ff6ae585693
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402275"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a>Kvůli vnitřní chybě se nepovedlo získat úplný název operačního systému.
Kvůli vnitřní chybě se nepovedlo získat úplný název operačního systému. To může být způsobeno tím, že rozhraní WMI není v aktuálním počítači existující.  
  
 Volání `My.Computer.Info.OSFullName` vlastnosti se nezdařilo. Možnou příčinou této chyby je, pokud v aktuálním počítači není nainstalovaná rozhraní WMI (Windows Management Instrumentation) (WMI).  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Přidejte `Try...Catch` blok kolem volání do `My.Computer.Info.OSFullName` Vlastnosti.  
  
2. Další informace o rozhraní WMI a o tom, jak ho nainstalovat, najdete v tématu a vyhledejte "rozhraní WMI (Windows Management Instrumentation) Core".  
  
## <a name="see-also"></a>Viz také

- [My. Computer. info. OSFullName](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)
- [Zpracování a vyvolávání výjimek v rozhraní .NET](../../standard/exceptions/index.md)
- [Try...Catch....Finally – příkaz](../language-reference/statements/try-catch-finally-statement.md)
