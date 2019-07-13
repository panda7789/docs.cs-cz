---
ms.openlocfilehash: 97ca78e154eb25e863256e06caa119fe753bc344
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858434"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a>WPF kontroly pravopisu v textu povoleno ovládací prvky nebudou fungovat ve Windows 10 pro jazyky, které nejsou v seznamu jazyk operačního systému.

|   |   |
|---|---|
|Podrobnosti|Při spuštění ve Windows 10, nástroj pro kontrolu pravopisu nemusí fungovat pro ovládací prvky WPF textu povoleno, protože jsou k dispozici pouze pro jazyky, které jsou k dispozici v seznamu jazyků funkce platformy pro kontrolu pravopisu. Ve Windows 10 když jazyk se přidá do seznamu dostupných klávesnice, Windows automaticky stáhne a nainstaluje odpovídající funkce na vyžádání (zámořských) balíčku, které poskytuje funkce pro kontrolu pravopisu. Přidáním jazyk do seznamu jazyků bude podporovaný nástroj pro kontrolu pravopisu.|
|Doporučení|Mějte na paměti, že jazyk nebo text, který má být kontrola pravopisu je nutné přidat jako jazyk pro kontrolu pravopisu pro práci ve Windows 10.|
|Scope|Edge|
|Version|4.6|
|type|Modul runtime|

