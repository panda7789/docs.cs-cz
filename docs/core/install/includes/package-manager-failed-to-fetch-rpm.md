---
ms.openlocfilehash: 96f3ef0160144322f77413995c842b745bb5bb1e
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920745"
---

Při instalaci balíčku .NET Core se může zobrazit chyba podobná `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'`. Obecně řečeno, tato chyba znamená, že kanál balíčku pro .NET Core se upgraduje s novějšími verzemi balíčků a že byste se měli pokusit později. Během upgradu by kanál balíčku neměl být nedostupný déle než 2 hodiny. Pokud se tato chyba průběžně zobrazuje déle než 2 hodiny, uveďte problém na <https://github.com/dotnet/core/issues>.
