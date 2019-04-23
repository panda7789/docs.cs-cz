---
ms.openlocfilehash: 6cdd410cc818c2c0a993a364e550f5f92ed6a821
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981823"
---
### <a name="resgen-refuses-to-load-content-from-the-web"></a>Resgen odmítá k načtení obsahu z webu

|   |   |
|---|---|
|Podrobnosti|binární formátovaný vstup může obsahovat soubory .resx. Pokud se pokusíte použít aplikaci resgen se načíst soubor, který byl stažen z nedůvěryhodného umístění, se nepovedlo se načíst vstupní ve výchozím nastavení.|
|Doporučení|Resgen, kteří vyžadují načítání binární formátovaný vstup z nedůvěryhodného umístění můžete odebrat značku webu ze vstupního souboru nebo použít datového toku zvuku nabízí výslovného nesouhlasu s. Přidejte následující nastavení registru použít počítač široký odhlásit datového toku zvuku nabízí: [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework\SDK] &quot;AllowProcessOfUntrustedResourceFiles&quot;=&quot;true&quot;|
|Rozsah|Edge|
|Version|4.7.2|
|Type|Změna cílení|
