---
ms.openlocfilehash: 8049bf01bc10c5913fa11b25e49afd1b1317eecc
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761313"
---
### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a>Kontrola pravopisu WPF selže neočekávaným způsobem

|   |   |
|---|---|
|Podrobnosti|To zahrnuje celou řadu problémů WPF kontrolu pravopisu:<ul><li>Kontrola pravopisu WPF někdy vyvolá. <xref:System.Runtime.InteropServices.COMException?displayProperty=name></li><li>Kontrola pravopisu WPF se nezdaří s <xref:System.UnauthorizedAccessException> při spouštění aplikací pomocí příkazu "Spustit jako jiný uživatel.</li><li>Kontrola pravopisu WPF nesprávně identifikován pravopisných chyb ve složených slov, jako je "Hausnummer" v němčině.</li></ul>|
|Doporučení|Problém #1 - Tato chyba byla opravena v rozhraní .NET Framework 4.6.2 problém č. 2 – WPF kontrolu pravopisu je již nejsou podporovány při spouštění aplikací pomocí příkazu "Spustit jako jiný uživatel". Spouštění rozhraní .NET Framework 4.6.2, aplikace spustit tímto způsobem havaruje už neočekávaně – místo toho bude nástroj pro kontrolu pravopisu tiše zakázán. Problém #3 – Tato chyba byla opravena v rozhraní .NET Framework 4.6.2.|
|Rozsah|Edge|
|Version|4.6.1|
|Type|Modul runtime|

