---
ms.openlocfilehash: ee5070a1a4c58d6c1282ba47c921436ca22722ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858523"
---
### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a>Rozhraní .NET Framework 4.6 nepoužívá verzi 4.5.x.x při registraci v registru

|   |   |
|---|---|
|Podrobnosti|Jak by se dalo očekávat, klíč verze <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>nastavený v registru (na ) pro rozhraní .NET Framework 4.6 začíná na "4.6", nikoli na "4.5". Aplikace, které jsou závislé na těchto klíčích registru, aby věděly, které verze rozhraní .NET Framework jsou nainstalovány v počítači, by měly být aktualizovány, aby pochopily, že 4.6 je nová možná verze a verze, která je kompatibilní s předchozími verzemi 4.5.x.|
|Návrh|Aktualizujte aplikace sondování pro instalaci rozhraní .NET Framework 4.5 hledáním klíčů registru 4.5, které také přijměte 4.6.|
|Rozsah|Edge|
|Version|4.6|
|Typ|Modul runtime|
