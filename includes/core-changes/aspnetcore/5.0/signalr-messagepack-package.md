---
ms.openlocfilehash: ca0792a3fd05d28cecceac1d644e3e4bf64722bc
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345226"
---
### <a name="signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package"></a>Signal: protokol centra MessagePack se přesunul do balíčku MessagePack 2. x.

[Protokol MessagePack hub](/aspnet/core/signalr/messagepackhubprotocol) používá [MessagePack balíček NuGet](https://www.nuget.org/packages/MessagePack) pro serializaci MessagePack. ASP.NET Core ASP.NET Core 5,0 upgraduje balíček z 1. x na nejnovější verzi balíčku 2. x.

Diskuzi o tomto problému najdete v tématu [dotnet/aspnetcore # 18692](https://github.com/dotnet/aspnetcore/issues/18692).

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 1

#### <a name="old-behavior"></a>Staré chování

ASP.NET Core Signal používá balíček MessagePack 1. x k serializaci a deserializaci zpráv MessagePack.

#### <a name="new-behavior"></a>Nové chování

ASP.NET Core Signal používá k serializaci a deserializaci MessagePack zpráv balíček MessagePack 2. x.

#### <a name="reason-for-change"></a>Důvod změny

Nejnovější vylepšení v balíčku MessagePack 2. x přidávají užitečné funkce.

#### <a name="recommended-action"></a>Doporučená akce

Tato změna se projeví v těchto případech:

* Nastavení nebo konfigurace hodnot na <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions> .
* Pomocí rozhraní API MessagePack přímo a pomocí protokolu MessagePack (ASP.NET Core Signaler hub) ve stejném projektu. Místo předchozí verze se načte novější verze.

Pokyny k migraci pro autory balíčku najdete v tématu [migrace z MessagePack v1. x na MessagePack v2. x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md). Jsou ovlivněny některé aspekty serializace a deserializace zprávy. Konkrétně existují [změny chování při serializaci hodnot data a času](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes).

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
