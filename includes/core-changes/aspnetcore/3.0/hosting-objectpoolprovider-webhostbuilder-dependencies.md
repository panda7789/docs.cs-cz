---
ms.openlocfilehash: 4d99d0b6e99a7a9b976cf11832b33ad3bdc6d299
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901719"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a>Hostování: ObjectPoolProvider se odebral ze závislostí WebHostBuilder.

V rámci zvýšení ASP.NET Core platíte za Play se `ObjectPoolProvider` odebral z hlavní sady závislostí. Konkrétní komponenty, které se spoléhají na `ObjectPoolProvider` nyní přidat sami sebe.

Diskuzi najdete v tématu [dotnet/aspnetcore # 5944](https://github.com/dotnet/aspnetcore/issues/5944).

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="old-behavior"></a>Staré chování

`WebHostBuilder` poskytuje `ObjectPoolProvider` ve výchozím nastavení v kontejneru DI.

#### <a name="new-behavior"></a>Nové chování

`WebHostBuilder` už v kontejneru DI neposkytuje `ObjectPoolProvider` ve výchozím nastavení.

#### <a name="reason-for-change"></a>Důvod změny

Tato změna se provedla, aby se zajistilo ASP.NET Core více platíte za Play.

#### <a name="recommended-action"></a>Doporučená akce

Pokud vaše komponenta vyžaduje `ObjectPoolProvider`, je nutné ji přidat do svých závislostí prostřednictvím `IServiceCollection`.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
