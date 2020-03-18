---
ms.openlocfilehash: 06d5f48566c239e37355496c3f27163d952602c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901713"
---
### <a name="kestrel-connection-adapters-removed"></a>Poštolka: Připojení adaptéry odstraněny

V rámci přesunu "pubternal" API `public`do aplikace byl `IConnectionAdapter` z Kestrelu odstraněn koncept konceptu a. Adaptéry připojení jsou nahrazovány middleware připojení (podobně jako http middleware v kanálu ASP.NET Core, ale pro připojení nižší úrovně). Protokolování protokolu HTTPS a připojení se přesunulo z adaptérů připojení na middleware připojení. Tyto metody rozšíření by měly i nadále fungovat bez problémů, ale podrobnosti implementace se změnily.

Další informace naleznete [v tématu dotnet/aspnetcore#11412](https://github.com/dotnet/aspnetcore/pull/11412). Diskuse naleznete [v tématu dotnet/aspnetcore#11475](https://github.com/dotnet/aspnetcore/issues/11475).

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Součásti rozšiřitelnosti kestrelu `IConnectionAdapter`byly vytvořeny pomocí .

#### <a name="new-behavior"></a>Nové chování

Komponenty rozšiřitelnosti kestrelu jsou vytvořeny jako [middleware](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).

#### <a name="reason-for-change"></a>Důvod změny

Tato změna má poskytnout flexibilnější architekturu rozšiřitelnosti.

#### <a name="recommended-action"></a>Doporučená akce

Převést všechny `IConnectionAdapter` implementace použít nový middleware vzor, jak je znázorněno [zde](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->
