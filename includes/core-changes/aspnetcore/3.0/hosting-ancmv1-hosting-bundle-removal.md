---
ms.openlocfilehash: 04e5ca41374fc333a31f0422bc2e89f54b3cb049
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394298"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a><span data-ttu-id="22c89-101">Hostování: AspNetCoreModule v1 odebrané ze sady hostování Windows</span><span class="sxs-lookup"><span data-stu-id="22c89-101">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>

<span data-ttu-id="22c89-102">Počínaje ASP.NET Core 3,0 sada hostitelů Windows nebude obsahovat AspNetCoreModule (ANCM) v1.</span><span class="sxs-lookup"><span data-stu-id="22c89-102">Starting with ASP.NET Core 3.0, the Windows Hosting Bundle won't contain AspNetCoreModule (ANCM) V1.</span></span>

<span data-ttu-id="22c89-103">ANCM v2 je zpětně kompatibilní s ANCM OutOfProcess a doporučuje se pro použití s aplikacemi ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="22c89-103">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="22c89-104">Diskuzi najdete v tématu [ASPNET/AspNetCore # 7095](https://github.com/aspnet/AspNetCore/issues/7095).</span><span class="sxs-lookup"><span data-stu-id="22c89-104">For discussion, see [aspnet/AspNetCore#7095](https://github.com/aspnet/AspNetCore/issues/7095).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="22c89-105">Představená verze</span><span class="sxs-lookup"><span data-stu-id="22c89-105">Version introduced</span></span>

<span data-ttu-id="22c89-106">3.0</span><span class="sxs-lookup"><span data-stu-id="22c89-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="22c89-107">Staré chování</span><span class="sxs-lookup"><span data-stu-id="22c89-107">Old behavior</span></span>

<span data-ttu-id="22c89-108">ANCM v1 je součástí sady hostování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="22c89-108">ANCM V1 is included in the Windows Hosting Bundle.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="22c89-109">Nové chování</span><span class="sxs-lookup"><span data-stu-id="22c89-109">New behavior</span></span>

<span data-ttu-id="22c89-110">ANCM v1 není součástí hostitelské sady Windows.</span><span class="sxs-lookup"><span data-stu-id="22c89-110">ANCM V1 isn't included in the Windows Hosting Bundle.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="22c89-111">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="22c89-111">Reason for change</span></span>

<span data-ttu-id="22c89-112">ANCM v2 je zpětně kompatibilní s ANCM OutOfProcess a doporučuje se pro použití s aplikacemi ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="22c89-112">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="22c89-113">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="22c89-113">Recommended action</span></span>

<span data-ttu-id="22c89-114">Použijte ANCM v2 s aplikacemi ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="22c89-114">Use ANCM V2 with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="22c89-115">Pokud je požadováno ANCM V1, může být nainstalováno pomocí hostitelské sady Windows ASP.NET Core 2,1 nebo 2,2.</span><span class="sxs-lookup"><span data-stu-id="22c89-115">If ANCM V1 is required, it can be installed using the ASP.NET Core 2.1 or 2.2 Windows Hosting Bundle.</span></span>

<span data-ttu-id="22c89-116">Tato změna způsobí přerušení aplikací ASP.NET Core 3,0, které:</span><span class="sxs-lookup"><span data-stu-id="22c89-116">This change will break ASP.NET Core 3.0 apps that:</span></span>

- <span data-ttu-id="22c89-117">Výslovný souhlas s používáním ANCM V1 s `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`.</span><span class="sxs-lookup"><span data-stu-id="22c89-117">Explicitly opted into using ANCM V1 with `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`.</span></span>
- <span data-ttu-id="22c89-118">Mít vlastní soubor *Web. config* s `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`.</span><span class="sxs-lookup"><span data-stu-id="22c89-118">Have a custom *web.config* file with `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`.</span></span>

#### <a name="category"></a><span data-ttu-id="22c89-119">Kategorie</span><span class="sxs-lookup"><span data-stu-id="22c89-119">Category</span></span>

<span data-ttu-id="22c89-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="22c89-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="22c89-121">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="22c89-121">Affected APIs</span></span>

<span data-ttu-id="22c89-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="22c89-122">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
