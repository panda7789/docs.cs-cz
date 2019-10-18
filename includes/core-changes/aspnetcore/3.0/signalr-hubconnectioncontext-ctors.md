---
ms.openlocfilehash: 8979b7ffc09726c6588fe3ba60b916202697648f
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522669"
---
### <a name="signalr-hubconnectioncontext-constructors-changed"></a><span data-ttu-id="4402b-101">Signál: HubConnectionContext konstruktory se změnily.</span><span class="sxs-lookup"><span data-stu-id="4402b-101">SignalR: HubConnectionContext constructors changed</span></span>

<span data-ttu-id="4402b-102">Konstruktory `HubConnectionContext` nástroje Signal se změnily tak, aby přijímaly typ možností místo více parametrů až po přidání možností do budoucna.</span><span class="sxs-lookup"><span data-stu-id="4402b-102">SignalR's `HubConnectionContext` constructors changed to accept an options type, rather than multiple parameters, to future-proof adding options.</span></span> <span data-ttu-id="4402b-103">Tato změna nahrazuje dva konstruktory jedním konstruktorem, který přijímá typ možností.</span><span class="sxs-lookup"><span data-stu-id="4402b-103">This change replaces two constructors with a single constructor that accepts an options type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4402b-104">Představená verze</span><span class="sxs-lookup"><span data-stu-id="4402b-104">Version introduced</span></span>

<span data-ttu-id="4402b-105">3.0</span><span class="sxs-lookup"><span data-stu-id="4402b-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="4402b-106">Staré chování</span><span class="sxs-lookup"><span data-stu-id="4402b-106">Old behavior</span></span>

<span data-ttu-id="4402b-107">`HubConnectionContext` má dva konstruktory:</span><span class="sxs-lookup"><span data-stu-id="4402b-107">`HubConnectionContext` has two constructors:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory);
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory, TimeSpan clientTimeoutInterval);
```

#### <a name="new-behavior"></a><span data-ttu-id="4402b-108">Nové chování</span><span class="sxs-lookup"><span data-stu-id="4402b-108">New behavior</span></span>

<span data-ttu-id="4402b-109">Dva konstruktory se odebraly a nahradily jedním konstruktorem:</span><span class="sxs-lookup"><span data-stu-id="4402b-109">The two constructors were removed and replaced with one constructor:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, HubConnectionContextOptions contextOptions, ILoggerFactory loggerFactory)
```

#### <a name="reason-for-change"></a><span data-ttu-id="4402b-110">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="4402b-110">Reason for change</span></span>

<span data-ttu-id="4402b-111">Nový konstruktor používá nový objekt Options.</span><span class="sxs-lookup"><span data-stu-id="4402b-111">The new constructor uses a new options object.</span></span> <span data-ttu-id="4402b-112">V důsledku toho mohou být funkce `HubConnectionContext` v budoucnu rozbaleny, aniž by bylo nutné vytvářet další konstruktory a zásadní změny.</span><span class="sxs-lookup"><span data-stu-id="4402b-112">Consequently, the features of `HubConnectionContext` can be expanded in the future without making more constructors and breaking changes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4402b-113">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="4402b-113">Recommended action</span></span>

<span data-ttu-id="4402b-114">Namísto použití následujícího konstruktoru:</span><span class="sxs-lookup"><span data-stu-id="4402b-114">Instead of using the following constructor:</span></span>

```csharp
HubConnectionContext connectionContext = new HubConnectionContext(
    connectionContext,
    keepAliveInterval: TimeSpan.FromSeconds(15),
    loggerFactory,
    clientTimeoutInterval: TimeSpan.FromSeconds(15));
```

<span data-ttu-id="4402b-115">Použijte následující konstruktor:</span><span class="sxs-lookup"><span data-stu-id="4402b-115">Use the following constructor:</span></span>

```csharp
HubConnectionContextOptions contextOptions = new HubConnectionContextOptions()
{
    KeepAliveInterval = TimeSpan.FromSeconds(15),
    ClientTimeoutInterval = TimeSpan.FromSeconds(15)
};
HubConnectionContext connectionContext = new HubConnectionContext(connectionContext, contextOptions, loggerFactory);
```

#### <a name="category"></a><span data-ttu-id="4402b-116">Kategorie</span><span class="sxs-lookup"><span data-stu-id="4402b-116">Category</span></span>

<span data-ttu-id="4402b-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4402b-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4402b-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="4402b-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)`
- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)`

-->
