---
ms.openlocfilehash: 06d5f48566c239e37355496c3f27163d952602c6
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901713"
---
### <a name="kestrel-connection-adapters-removed"></a>Kestrel: odebrané adaptéry připojení

V rámci přesunutí pro přesunutí rozhraní API "pubternal" na `public`se koncept `IConnectionAdapter` odebral z Kestrel. Připojovací adaptéry se nahrazují pomocí middleware připojení (podobně jako middleware HTTP v kanálu ASP.NET Core, ale u připojení nižší úrovně). Protokolování HTTPS a připojení se přesunulo z připojovacích adaptérů na middleware připojení. Tyto metody rozšíření by měly nadále fungovat bez problémů, ale podrobnosti implementace se změnily.

Další informace naleznete v tématu [dotnet/aspnetcore # 11412](https://github.com/dotnet/aspnetcore/pull/11412). Diskuzi najdete v tématu [dotnet/aspnetcore # 11475](https://github.com/dotnet/aspnetcore/issues/11475).

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="old-behavior"></a>Staré chování

Komponenty rozšiřitelnosti Kestrel byly vytvořeny pomocí `IConnectionAdapter`.

#### <a name="new-behavior"></a>Nové chování

Komponenty rozšiřitelnosti Kestrel se vytvářejí jako [middleware](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).

#### <a name="reason-for-change"></a>Důvod změny

Tato změna je určená k zajištění flexibilní rozšiřitelné architektury.

#### <a name="recommended-action"></a>Doporučená akce

Převeďte všechny implementace `IConnectionAdapter`, aby používaly nový vzor middlewaru, jak je znázorněno [zde](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->
