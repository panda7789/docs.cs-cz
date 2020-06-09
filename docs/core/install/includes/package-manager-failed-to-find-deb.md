---
ms.openlocfilehash: 7d398df060c031ae891218b82a2712d74f4c33b7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602983"
---

Pokud se zobrazí chybová zpráva podobná té, že se **nepovedlo najít balíček {Netcore-Package}**, spusťte následující příkazy.

Následující sada příkazů obsahuje dva zástupné symboly.

- `{dotnet-package}`\
To představuje balíček .NET Core, který instalujete, například `aspnetcore-runtime-3.1` . Tento příkaz se používá v `sudo apt-get install` níže uvedeném příkazu.

- `{os-version}`\
To představuje verzi systému Linux, na které se nacházíte. Tento příkaz se používá v `wget` níže uvedeném příkazu.

Zkuste seznam balíčků vymazáním:

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {dotnet-package}
```

Pokud to nefunguje, můžete spustit ruční instalaci s následujícími příkazy:
