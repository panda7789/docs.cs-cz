---
ms.openlocfilehash: a916af91670dc9c5ceb2ff759cd8ae308fb2c2dc
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394368"
---
### <a name="kestrel-connection-adapters-removed"></a>Kestrel: odebrané adaptéry připojení

V rámci přesunutí na přesunutí rozhraní API "pubternal" na `public` se koncept `IConnectionAdapter` odebral z Kestrel. Připojovací adaptéry se nahrazují pomocí middleware připojení (podobně jako middleware HTTP v kanálu ASP.NET Core, ale u připojení nižší úrovně). Protokolování HTTPS a připojení se přesunulo z připojovacích adaptérů na middleware připojení. Tyto metody rozšíření by měly nadále fungovat bez problémů, ale podrobnosti implementace se změnily.

Další informace najdete v tématu [ASPNET/AspNetCore # 11412](https://github.com/aspnet/AspNetCore/pull/11412). Diskuzi najdete v tématu [ASPNET/AspNetCore # 11475](https://github.com/aspnet/AspNetCore/issues/11475).

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Komponenty rozšiřitelnosti Kestrel byly vytvořeny pomocí `IConnectionAdapter`.

#### <a name="new-behavior"></a>Nové chování

Komponenty rozšiřitelnosti Kestrel se vytvářejí jako [middleware](https://github.com/aspnet/AspNetCore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).

#### <a name="reason-for-change"></a>Důvod změny

Tato změna je určená k zajištění flexibilní rozšiřitelné architektury.

#### <a name="recommended-action"></a>Doporučená akce

Převeďte všechny implementace `IConnectionAdapter`, aby používaly nový vzor middlewaru, jak je znázorněno [zde](https://github.com/aspnet/AspNetCore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->
