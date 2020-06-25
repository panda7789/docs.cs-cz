---
ms.openlocfilehash: 9a747d8fc15ca8fa2b915f89291f118d7344d172
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325251"
---
### <a name="httpsys-client-certificate-renegotiation-disabled-by-default"></a><span data-ttu-id="12b2f-101">HttpSys: nové vyjednávání klientského certifikátu je ve výchozím nastavení zakázané.</span><span class="sxs-lookup"><span data-stu-id="12b2f-101">HttpSys: Client certificate renegotiation disabled by default</span></span>

<span data-ttu-id="12b2f-102">Možnost opětovného vyjednání připojení a vyžádání klientského certifikátu je ve výchozím nastavení zakázaná.</span><span class="sxs-lookup"><span data-stu-id="12b2f-102">The option to renegotiate a connection and request a client certificate has been disabled by default.</span></span> <span data-ttu-id="12b2f-103">Diskuzi najdete v tématu problém [dotnet/aspnetcore # 23181](https://github.com/dotnet/aspnetcore/issues/23181).</span><span class="sxs-lookup"><span data-stu-id="12b2f-103">For discussion, see issue [dotnet/aspnetcore#23181](https://github.com/dotnet/aspnetcore/issues/23181).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="12b2f-104">Představená verze</span><span class="sxs-lookup"><span data-stu-id="12b2f-104">Version introduced</span></span>

<span data-ttu-id="12b2f-105">ASP.NET Core 5,0</span><span class="sxs-lookup"><span data-stu-id="12b2f-105">ASP.NET Core 5.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="12b2f-106">Staré chování</span><span class="sxs-lookup"><span data-stu-id="12b2f-106">Old behavior</span></span>

<span data-ttu-id="12b2f-107">Připojení se dá znovu vyjednávat pro vyžádání klientského certifikátu.</span><span class="sxs-lookup"><span data-stu-id="12b2f-107">The connection can be renegotiated to request a client certificate.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="12b2f-108">Nové chování</span><span class="sxs-lookup"><span data-stu-id="12b2f-108">New behavior</span></span>

<span data-ttu-id="12b2f-109">Klientské certifikáty je možné požadovat jenom při počátečním handshaki připojení.</span><span class="sxs-lookup"><span data-stu-id="12b2f-109">Client certificates can only be requested during the initial connection handshake.</span></span> <span data-ttu-id="12b2f-110">Další informace najdete v tématu o žádosti o získání dat [dotnet/aspnetcore # 23162](https://github.com/dotnet/aspnetcore/pull/23162).</span><span class="sxs-lookup"><span data-stu-id="12b2f-110">For more information, see pull request [dotnet/aspnetcore#23162](https://github.com/dotnet/aspnetcore/pull/23162).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="12b2f-111">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="12b2f-111">Reason for change</span></span>

<span data-ttu-id="12b2f-112">Nové vyjednávání způsobilo několik problémů s výkonem a zablokování.</span><span class="sxs-lookup"><span data-stu-id="12b2f-112">Renegotiation caused a number of performance and deadlock issues.</span></span> <span data-ttu-id="12b2f-113">V HTTP/2 to také není podporováno.</span><span class="sxs-lookup"><span data-stu-id="12b2f-113">It's also not supported in HTTP/2.</span></span> <span data-ttu-id="12b2f-114">Další kontext z toho, kdy se možnost řízení tohoto chování zavedla v ASP.NET Core 3,1, najdete v tématu problém [dotnet/aspnetcore # 14806](https://github.com/dotnet/aspnetcore/issues/14806).</span><span class="sxs-lookup"><span data-stu-id="12b2f-114">For additional context from when the option to control this behavior was introduced in ASP.NET Core 3.1, see issue [dotnet/aspnetcore#14806](https://github.com/dotnet/aspnetcore/issues/14806).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="12b2f-115">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="12b2f-115">Recommended action</span></span>

<span data-ttu-id="12b2f-116">Aplikace, které vyžadují klientské certifikáty, by se měly *netsh.exe* použít k nastavení `clientcertnegotiation` Možnosti na `enabled` .</span><span class="sxs-lookup"><span data-stu-id="12b2f-116">Apps that require client certificates should use *netsh.exe* to set the `clientcertnegotiation` option to `enabled`.</span></span> <span data-ttu-id="12b2f-117">Další informace najdete v tématu [příkazy netsh http](/windows-server/networking/technologies/netsh/netsh-http).</span><span class="sxs-lookup"><span data-stu-id="12b2f-117">For more information, see [netsh http commands](/windows-server/networking/technologies/netsh/netsh-http).</span></span>

<span data-ttu-id="12b2f-118">Pokud chcete, aby klientské certifikáty byly povolené jenom pro některé části vaší aplikace, přečtěte si pokyny v tématu [volitelné klientské certifikáty](/aspnet/core/security/authentication/certauth?view=aspnetcore-3.1#optional-client-certificates).</span><span class="sxs-lookup"><span data-stu-id="12b2f-118">If you want client certificates enabled for only some parts of your app, see the guidance at [Optional client certificates](/aspnet/core/security/authentication/certauth?view=aspnetcore-3.1#optional-client-certificates).</span></span>

<span data-ttu-id="12b2f-119">Pokud budete potřebovat původní chování redohadování, nastavte `HttpSysOptions.ClientCertificateMethod` na starou hodnotu `ClientCertificateMethod.AllowRenegotiate` .</span><span class="sxs-lookup"><span data-stu-id="12b2f-119">If you need the old renegotiate behavior, set `HttpSysOptions.ClientCertificateMethod` to the old value `ClientCertificateMethod.AllowRenegotiate`.</span></span> <span data-ttu-id="12b2f-120">To se nedoporučuje z důvodů uvedených výše a v propojených pokynech.</span><span class="sxs-lookup"><span data-stu-id="12b2f-120">This isn't recommended for the reasons outlined above and in the linked guidance.</span></span>

#### <a name="category"></a><span data-ttu-id="12b2f-121">Kategorie</span><span class="sxs-lookup"><span data-stu-id="12b2f-121">Category</span></span>

<span data-ttu-id="12b2f-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="12b2f-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="12b2f-123">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="12b2f-123">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.ConnectionInfo.ClientCertificate%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.ConnectionInfo.GetClientCertificateAsync%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Server.HttpSys.HttpSysOptions.ClientCertificateMethod%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Http.ConnectionInfo.ClientCertificate`
- `Overload:Microsoft.AspNetCore.Http.ConnectionInfo.GetClientCertificateAsync`
- `Overload:Microsoft.AspNetCore.Server.HttpSys.HttpSysOptions.ClientCertificateMethod`

-->
