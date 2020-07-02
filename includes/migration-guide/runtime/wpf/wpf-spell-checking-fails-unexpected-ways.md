---
ms.openlocfilehash: d4f0095bc9fde98087dce528c8154d9c9ac6ddb7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621786"
---
### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a>Neočekávaným způsobem se kontrola pravopisu WPF nezdařila.

#### <a name="details"></a>Podrobnosti

To zahrnuje řadu potíží s kontrolou pravopisu WPF:<ul><li>Nástroj pro kontrolu pravopisu WPF někdy vyvolá<xref:System.Runtime.InteropServices.COMException?displayProperty=fullName></li><li>Kontrola pravopisu WPF se nezdařila, <xref:System.UnauthorizedAccessException> Pokud se aplikace spouští pomocí příkazu Spustit jako jiný uživatel.</li><li>Kontrola pravopisu WPF nesprávně identifikuje pravopisné chyby ve složených slovech, jako je ' Hausnummer ' v němčině.</li></ul>

#### <a name="suggestion"></a>Návrh

Problémová #1 – Toto řešení bylo opraveno v .NET Framework 4.6.2 potíží #2 – Kontrola pravopisu WPF již není podporována, pokud se aplikace spouští pomocí příkazu Spustit jako jiný uživatel. Spuštění .NET Framework 4.6.2, aplikace spuštěné tímto způsobem už neočekávaně nezmizí – místo toho nebude kontrola pravopisu vypnutá. #3 problému – to bylo opraveno v .NET Framework 4.6.2.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.6.1|
|Typ|Modul runtime|
