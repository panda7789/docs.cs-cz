---
ms.openlocfilehash: 09e3f0e168e0dcbe79d8ee7216f2671c67bfb87e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802942"
---
### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a>WPF Kontrola pravopisu se nezdaří neočekávaným způsobem

|   |   |
|---|---|
|Podrobnosti|To zahrnuje řadu wpf kontrola pravopisu problémy:<ul><li>WPF Kontrola pravopisu někdy hodí<xref:System.Runtime.InteropServices.COMException?displayProperty=name></li><li>WPF Kontrola pravopisu <xref:System.UnauthorizedAccessException> selže s při spuštění aplikací pomocí 'spustit jako jiný uživatel'</li><li>WPF Kontrola pravopisu nesprávně identifikuje pravopisné chyby ve složených slovech jako 'Hausnummer' v němčině.</li></ul>|
|Návrh|Problém #1 - To bylo opraveno v rozhraní .NET Framework 4.6.2 Problém #2 - WPF Kontrola pravopisu již není podporována při spuštění aplikací pomocí 'spustit jako jiný uživatel'. Spuštění rozhraní .NET Framework 4.6.2 aplikace spuštěné tímto způsobem již nebudou neočekávaně zvrtnout – místo toho bude kontrola pravopisu tiše zakázána. Problém #3 - To bylo opraveno v rozhraní .NET Framework 4.6.2.|
|Rozsah|Edge|
|Version|4.6.1|
|Typ|Modul runtime|
