---
ms.openlocfilehash: 7a05f60cf1c04d3d73dadb54541254a83b4ea855
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507072"
---
### <a name="signalr-messagepack-hub-protocol-options-type-changed"></a><span data-ttu-id="13642-101">Signal: typ možností protokolu centra MessagePack se změnil.</span><span class="sxs-lookup"><span data-stu-id="13642-101">SignalR: MessagePack Hub Protocol options type changed</span></span>

<span data-ttu-id="13642-102">Typ možností protokolu centra ASP.NET Core Signal MessagePack se změnil z `IList<MessagePack.IFormatterResolver>` na `MessagePackSerializerOptions` typ knihovny [MessagePack](https://www.nuget.org/packages/MessagePack) .</span><span class="sxs-lookup"><span data-stu-id="13642-102">The ASP.NET Core SignalR MessagePack Hub Protocol options type has changed from `IList<MessagePack.IFormatterResolver>` to the [MessagePack](https://www.nuget.org/packages/MessagePack) library's `MessagePackSerializerOptions` type.</span></span>

<span data-ttu-id="13642-103">Diskuzi o této změně najdete v tématu [dotnet/aspnetcore # 20506](https://github.com/dotnet/aspnetcore/issues/20506).</span><span class="sxs-lookup"><span data-stu-id="13642-103">For discussion on this change, see [dotnet/aspnetcore#20506](https://github.com/dotnet/aspnetcore/issues/20506).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="13642-104">Představená verze</span><span class="sxs-lookup"><span data-stu-id="13642-104">Version introduced</span></span>

<span data-ttu-id="13642-105">5,0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="13642-105">5.0 Preview 4</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="13642-106">Staré chování</span><span class="sxs-lookup"><span data-stu-id="13642-106">Old behavior</span></span>

<span data-ttu-id="13642-107">Můžete přidat do možností, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="13642-107">You can add to the options as shown in the following example:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.FormatterResolvers.Add(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

<span data-ttu-id="13642-108">A nahraďte tyto možnosti následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="13642-108">And replace the options as follows:</span></span>

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

#### <a name="new-behavior"></a><span data-ttu-id="13642-109">Nové chování</span><span class="sxs-lookup"><span data-stu-id="13642-109">New behavior</span></span>

<span data-ttu-id="13642-110">Můžete přidat do možností, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="13642-110">You can add to the options as shown in the following example:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.SerializerOptions =
            options.SerializeOptions.WithResolver(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

<span data-ttu-id="13642-111">A nahraďte tyto možnosti následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="13642-111">And replace the options as follows:</span></span>

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

#### <a name="reason-for-change"></a><span data-ttu-id="13642-112">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="13642-112">Reason for change</span></span>

<span data-ttu-id="13642-113">Tato změna je součástí přechodu na MessagePack v2. x, která byla oznámena v [ASPNET/oznámeních # 404](https://github.com/aspnet/Announcements/issues/404).</span><span class="sxs-lookup"><span data-stu-id="13642-113">This change is part of moving to MessagePack v2.x, which was announced in [aspnet/Announcements#404](https://github.com/aspnet/Announcements/issues/404).</span></span> <span data-ttu-id="13642-114">Knihovna v2. x přidala rozhraní API možností, které je snazší použít a poskytuje více funkcí než seznam `MessagePack.IFormatterResolver` , který byl dříve zveřejněn.</span><span class="sxs-lookup"><span data-stu-id="13642-114">The v2.x library has added an options API that's easier to use and provides more features than the list of `MessagePack.IFormatterResolver` that was exposed before.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="13642-115">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="13642-115">Recommended action</span></span>

<span data-ttu-id="13642-116">Tato zásadní změna má vliv na uživatele, kteří konfigurují <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>hodnoty na.</span><span class="sxs-lookup"><span data-stu-id="13642-116">This breaking change affects anyone who is configuring values on <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>.</span></span> <span data-ttu-id="13642-117">Pokud používáte protokol služby ASP.NET Core Signal MessagePack a upravujete možnosti, aktualizujte své využití tak, aby používalo nové rozhraní API možností, jak je uvedeno výše.</span><span class="sxs-lookup"><span data-stu-id="13642-117">If you're using the ASP.NET Core SignalR MessagePack Hub Protocol and modifying the options, update your usage to use the new options API as shown above.</span></span>

#### <a name="category"></a><span data-ttu-id="13642-118">Kategorie</span><span class="sxs-lookup"><span data-stu-id="13642-118">Category</span></span>

<span data-ttu-id="13642-119">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="13642-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="13642-120">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="13642-120">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
