---
ms.openlocfilehash: abb89099c4c8a5d9c0e55ef8f357faf44e75b045
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858434"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a>WPF kontrola pravopisu v text-dát povolené ovládací prvky nebude fungovat v systému Windows 10 pro jazyky, které nejsou v seznamu jazyka zadávání operačního systému

|   |   |
|---|---|
|Podrobnosti|Při spuštění v systému Windows 10 nemusí kontrola pravopisu fungovat pro ovládací prvky s podporou textu WPF, protože funkce kontroly pravopisu platformy jsou k dispozici pouze pro jazyky v seznamu vstupních jazyků. Při přidání jazyka do seznamu dostupných klávesnic systém Windows při přidání jazyka do seznamu dostupných klávesnic automaticky stáhne a nainstaluje odpovídající balíček Funkce na vyžádání (FOD), který poskytuje funkce kontroly pravopisu. Přidáním jazyka do seznamu vstupních jazyků bude kontrola pravopisu podporována.|
|Návrh|Uvědomte si, že jazyk nebo text, který má být kontrolován pravopisem, musí být přidán jako vstupní jazyk pro kontrolu pravopisu, aby fungoval v systému Windows 10.|
|Rozsah|Edge|
|Version|4.6|
|Typ|Modul runtime|
