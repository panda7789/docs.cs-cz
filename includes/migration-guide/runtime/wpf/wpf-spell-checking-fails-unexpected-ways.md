---
ms.openlocfilehash: 09e3f0e168e0dcbe79d8ee7216f2671c67bfb87e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664585"
---
### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a>Kontrola pravopisu WPF selže neočekávaným způsobem

|   |   |
|---|---|
|Podrobnosti|To zahrnuje celou řadu problémů WPF kontrolu pravopisu:<ul><li>Kontrola pravopisu WPF někdy vyvolá. <xref:System.Runtime.InteropServices.COMException?displayProperty=name></li><li>Kontrola pravopisu WPF se nezdaří s <xref:System.UnauthorizedAccessException> při spouštění aplikací pomocí příkazu "Spustit jako jiný uživatel.</li><li>Kontrola pravopisu WPF nesprávně identifikován pravopisných chyb ve složených slov, jako je "Hausnummer" v němčině.</li></ul>|
|Doporučení|Problém #1 - Tato chyba byla opravena v rozhraní .NET Framework 4.6.2 problém č. 2 – WPF kontrolu pravopisu je již nejsou podporovány při spouštění aplikací pomocí příkazu "Spustit jako jiný uživatel". Spouštění rozhraní .NET Framework 4.6.2, aplikace spustit tímto způsobem havaruje už neočekávaně – místo toho bude nástroj pro kontrolu pravopisu tiše zakázán. Problém #3 – Tato chyba byla opravena v rozhraní .NET Framework 4.6.2.|
|Rozsah|Edge|
|Version|4.6.1|
|Type|Modul runtime|
