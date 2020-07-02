---
ms.openlocfilehash: 1d2e4a058008676c6ea85becebd4bb9220569ef3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621160"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a>Kontrola pravopisu v jazyce WPF v ovládacích prvcích s podporou textu nebude ve Windows 10 fungovat pro jazyky, které nejsou v seznamu vstupních jazyků v operačním systému.

#### <a name="details"></a>Podrobnosti

Při spuštění ve Windows 10 nemusí kontrola pravopisu fungovat pro ovládací prvky s povoleným textem WPF, protože možnosti kontroly pravopisu platformy jsou dostupné jenom pro jazyky, které jsou k dispozici v seznamu vstupní jazyky. V systému Windows 10 se při přidání jazyka do seznamu dostupných klávesnic automaticky stáhne a nainstaluje odpovídající balíček funkce na vyžádání (FRANCOUZSKÝch), který poskytuje funkce kontroly pravopisu. Když přidáte jazyk do seznamu vstupní jazyky, bude se tato kontrola pravopisu podporovat.

#### <a name="suggestion"></a>Návrh

Počítejte s tím, že jazyk nebo text, který má být kontrolován pravopisem, musí být přidán jako vstupní jazyk pro kontrolu pravopisu pro práci ve Windows 10.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.6|
|Typ|Modul runtime|
