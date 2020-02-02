---
ms.openlocfilehash: 98ec28fc1f91512a61f64a36f7749379e864fea1
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920666"
---

Při instalaci balíčku .NET Core se může zobrazit chyba podobná `Failed to fetch ... File has unexpected size ... Mirror sync in progress?`. Obecně řečeno, tato chyba znamená, že kanál balíčku pro .NET Core se upgraduje s novějšími verzemi balíčků a že byste se měli pokusit později. Během upgradu by kanál balíčku neměl být nedostupný po dobu delší než 30 minut. Pokud se tato chyba průběžně zobrazuje déle než 30 minut, uveďte problém na <https://github.com/dotnet/core/issues>.
