---
title: Obecné pokyny
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Obecné pokyny
ms.date: 09/11/2018
ms.openlocfilehash: 2fa66d7593b764a8df4d9acc20f93d3f8fb26174
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73089653"
---
# <a name="general-guidance"></a>Obecné pokyny

Tato část obsahuje souhrn toho, kdy zvolit rozhraní .NET Core nebo .NET Framework. Další podrobnosti o těchto volbách poskytujeme v následujících částech.

Jádro .NET core s Linuxem nebo Kontejnery Windows byste měli použít pro kontejnerizovanou serverovou aplikaci Dockeru, když:

- Máte potřeby napříč platformami. Například chcete použít linuxové i windows kontejnery.

- Architektura aplikace je založena na mikroslužbách.

- Musíte rychle spustit kontejnery a chcete malé rozměry na kontejner, abyste dosáhli lepší hustoty nebo více kontejnerů na hardwarovou jednotku, abyste snížili náklady.

Stručně řečeno, při vytváření nových kontejnerizovaných aplikací .NET byste měli považovat .NET Core jako výchozí volbu. Má mnoho výhod a nejlépe se hodí k filozofii kontejnerů a stylu práce.

Další výhodou použití rozhraní .NET Core je, že můžete spustit vedle sebe verze .NET pro aplikace v rámci stejného počítače. Tato výhoda je důležitější pro servery nebo virtuální servery, které nepoužívají kontejnery, protože kontejnery izolovat verze rozhraní .NET, které aplikace potřebuje. (Pokud jsou kompatibilní s základním os.)

Rozhraní .NET Framework byste měli použít pro kontejnerizovanou serverovou aplikaci Dockeru, když:

- Aplikace aktuálně používá rozhraní .NET Framework a má silné závislosti na systému Windows.

- Je třeba použít rozhraní API systému Windows, které nejsou podporovány .NET Core.

- Musíte použít knihovny .NET jiných výrobců nebo balíčky NuGet, které nejsou k dispozici pro jádro .NET Core.

Použití rozhraní .NET Framework v Dockeru může zlepšit vaše možnosti nasazení minimalizací problémů s nasazením. Tento [scénář "lift and shift"](https://aka.ms/liftandshiftwithcontainersebook) je důležitý pro kontejnerizaci starších aplikací, které byly původně vyvinuty s tradiční rozhraní .NET Framework, jako jsou ASP.NET WebForms, MVC webové aplikace nebo WCF (Windows Communication Foundation) služby.

### <a name="additional-resources"></a>Další zdroje

- **E-kniha: Modernizace stávajících aplikací rozhraní .NET Framework pomocí kontejnerů Azure a Windows**  
    https://aka.ms/liftandshiftwithcontainersebook

- **Ukázkové aplikace: Modernizace starších ASP.NET webových aplikací pomocí kontejnerů windows**  
    https://aka.ms/eshopmodernizing

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](net-core-container-scenarios.md)
