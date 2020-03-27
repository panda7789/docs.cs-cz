---
ms.openlocfilehash: ca0792a3fd05d28cecceac1d644e3e4bf64722bc
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345226"
---
### <a name="signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package"></a>SignalR: MessagePack Hub Protocol byl přesunut na balíček MessagePack 2.x

ASP.NET Základní SignalR [MessagePack Hub Protocol](/aspnet/core/signalr/messagepackhubprotocol) používá [MessagePack NuGet balíček](https://www.nuget.org/packages/MessagePack) pro serializaci MessagePack. ASP.NET Core 5.0 upgraduje balíček z 1.x na nejnovější verzi balíčku 2.x.

Diskuse o tomto problému naleznete [v tématu dotnet/aspnetcore#18692](https://github.com/dotnet/aspnetcore/issues/18692).

#### <a name="version-introduced"></a>Zavedená verze

5.0 Náhled 1

#### <a name="old-behavior"></a>Staré chování

ASP.NET Core SignalR používá MessagePack 1.x balíček serializovat a rekonstruovat MessagePack zprávy.

#### <a name="new-behavior"></a>Nové chování

ASP.NET Core SignalR používá messagepack 2.x balíček serializovat a rekonstruovat MessagePack zprávy.

#### <a name="reason-for-change"></a>Důvod změny

Nejnovější vylepšení balíčku MessagePack 2.x přidat užitečné funkce.

#### <a name="recommended-action"></a>Doporučená akce

Tato změna porušení platí, pokud:

* Nastavení nebo konfigurace <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>hodnot v počítači .
* Použití MessagePack API přímo a pomocí ASP.NET Základní SignalR MessagePack Hub Protocol ve stejném projektu. Namísto předchozí verze bude načtena novější verze.

Pokyny k migraci od autorů balíčku naleznete [v tématu Migrace z MessagePack v1.x na MessagePack v2.x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md). Některé aspekty serializace zpráv a deserializace jsou ovlivněny. Konkrétně existují [změny chování, jak DateTime hodnoty serializovat](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes).

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
