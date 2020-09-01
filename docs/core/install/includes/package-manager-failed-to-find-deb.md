---
ms.openlocfilehash: 9d4c031eda291b0a8832c824789efdffe4084926
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132938"
---

Pokud se zobrazí chybová zpráva podobná té, že se **nepovedlo najít balíček {Netcore-Package}** nebo **některé balíčky nešlo nainstalovat**, spusťte následující příkazy.

Následující sada příkazů obsahuje dva zástupné symboly.

- `{dotnet-package}`\
To představuje balíček .NET Core, který instalujete, například `aspnetcore-runtime-3.1` . Tento příkaz se používá v `sudo apt-get install` níže uvedeném příkazu.

- `{os-version}`\
To představuje verzi systému Linux, na které se nacházíte. Tento příkaz se používá v `wget` níže uvedeném příkazu.

Nejdřív zkuste seznam balíčků vypsat:

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
```

Pak zkuste znovu nainstalovat .NET Core. Pokud to nefunguje, můžete spustit ruční instalaci s následujícími příkazy:
