---
ms.openlocfilehash: 4d99d0b6e99a7a9b976cf11832b33ad3bdc6d299
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901719"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a>Hostování: Objekt Usvého zprostředkovatele objectpoolu odebrán ze závislostí WebHostBuilder

Jako součást toho, ASP.NET Core více `ObjectPoolProvider` platit za hru, byl odstraněn z hlavní sady závislostí. Konkrétní součásti, `ObjectPoolProvider` na které se spoléhají, nyní přidávají sami.

Diskuse naleznete [v tématu dotnet/aspnetcore#5944](https://github.com/dotnet/aspnetcore/issues/5944).

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

`WebHostBuilder`poskytuje `ObjectPoolProvider` ve výchozím nastavení v kontejneru DI.

#### <a name="new-behavior"></a>Nové chování

`WebHostBuilder`již poskytuje `ObjectPoolProvider` ve výchozím nastavení v kontejneru DI.

#### <a name="reason-for-change"></a>Důvod změny

Tato změna byla provedena, aby se ASP.NET Core více platit za hru.

#### <a name="recommended-action"></a>Doporučená akce

Pokud vaše `ObjectPoolProvider`komponenta vyžaduje , je třeba přidat `IServiceCollection`do vašich závislostí prostřednictvím .

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádný

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
