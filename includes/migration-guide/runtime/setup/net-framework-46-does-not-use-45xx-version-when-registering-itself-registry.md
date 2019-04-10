---
ms.openlocfilehash: ee5070a1a4c58d6c1282ba47c921436ca22722ff
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234166"
---
### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a>Rozhraní .NET Framework 4.6 nepoužívá verzi 4.5.x.x při registraci v registru

|   |   |
|---|---|
|Podrobnosti|Jak očekávat, klíč verze nastaven v registru (na <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) pro rozhraní .NET Framework 4.6 začíná řetězcem "4.6", ne "4.5". K tomu, že 4.6 je nová verze je to možné, a ten, který je kompatibilní s předchozím 4.5.x uvolní se musí aktualizovat aplikace, které závisí na těchto klíčů registru vědět, jaké verze rozhraní .NET Framework jsou nainstalovány v počítači.|
|Doporučení|Aktualizace aplikace zjišťování pro rozhraní .NET Framework 4.5 nainstalujte tím, že hledají 4.5 klíčů registru také přijímat 4.6.|
|Rozsah|Edge|
|Version|4.6|
|Type|Modul runtime|
