---
ms.openlocfilehash: 16b9fde49f513643a37f65f3e926a34fc991c55a
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394077"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a>Hostování: ObjectPoolProvider se odebral ze závislostí WebHostBuilder.

V rámci zvýšení ASP.NET Core platíte za Play se `ObjectPoolProvider` odebral z hlavní sady závislostí. Konkrétní komponenty spoléhají na `ObjectPoolProvider` nyní přidat sami sebe.

Diskuzi najdete v tématu [ASPNET/AspNetCore # 5944](https://github.com/aspnet/AspNetCore/issues/5944).

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="old-behavior"></a>Staré chování

`WebHostBuilder` poskytuje ve výchozím nastavení `ObjectPoolProvider` v kontejneru DI.

#### <a name="new-behavior"></a>Nové chování

`WebHostBuilder` již ve výchozím nastavení v kontejneru DI neposkytuje `ObjectPoolProvider`.

#### <a name="reason-for-change"></a>Důvod změny

Tato změna se provedla, aby se zajistilo ASP.NET Core více platíte za Play.

#### <a name="recommended-action"></a>Doporučená akce

Pokud vaše komponenta vyžaduje `ObjectPoolProvider`, je nutné ji přidat k vašim závislostem prostřednictvím `IServiceCollection`.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
