---
ms.openlocfilehash: 7a05f60cf1c04d3d73dadb54541254a83b4ea855
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507072"
---
### <a name="signalr-messagepack-hub-protocol-options-type-changed"></a>Signal: typ možností protokolu centra MessagePack se změnil.

Typ možností protokolu centra ASP.NET Core Signal MessagePack se změnil z `IList<MessagePack.IFormatterResolver>` na typ knihovny [MessagePack](https://www.nuget.org/packages/MessagePack) `MessagePackSerializerOptions` .

Diskuzi o této změně najdete v tématu [dotnet/aspnetcore # 20506](https://github.com/dotnet/aspnetcore/issues/20506).

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 4

#### <a name="old-behavior"></a>Staré chování

Můžete přidat do možností, jak je znázorněno v následujícím příkladu:

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.FormatterResolvers.Add(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

A nahraďte tyto možnosti následujícím způsobem:

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.FormatterResolvers = new List<MessagePack.IFormatterResolver>()
        {
            MessagePack.Resolvers.StandardResolver.Instance
        };
    });
```

#### <a name="new-behavior"></a>Nové chování

Můžete přidat do možností, jak je znázorněno v následujícím příkladu:

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.SerializerOptions =
            options.SerializeOptions.WithResolver(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

A nahraďte tyto možnosti následujícím způsobem:

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.SerializerOptions = MessagePackSerializerOptions
                .Standard
                .WithResolver(MessagePack.Resolvers.StandardResolver.Instance)
                .WithSecurity(MessagePackSecurity.UntrustedData);
    });
```

#### <a name="reason-for-change"></a>Důvod změny

Tato změna je součástí přechodu na MessagePack v2. x, která byla oznámena v [ASPNET/oznámeních # 404](https://github.com/aspnet/Announcements/issues/404). Knihovna v2. x přidala rozhraní API možností, které je snazší použít a poskytuje více funkcí než seznam `MessagePack.IFormatterResolver` , který byl dříve zveřejněn.

#### <a name="recommended-action"></a>Doporučená akce

Tato zásadní změna má vliv na uživatele, kteří konfigurují hodnoty na <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions> . Pokud používáte protokol služby ASP.NET Core Signal MessagePack a upravujete možnosti, aktualizujte své využití tak, aby používalo nové rozhraní API možností, jak je uvedeno výše.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
