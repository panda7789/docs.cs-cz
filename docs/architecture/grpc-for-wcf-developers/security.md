---
title: Zabezpečení v gRPC aplikacích – gRPC pro vývojáře WCF
description: Přehled ověřování volání a kanálu a autorizaci v gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: d5804ad5de4a834eb81b90fa1ea7a61969a0b42f
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503419"
---
# <a name="security-in-grpc-applications"></a><span data-ttu-id="5a4d8-103">Zabezpečení v aplikacích gRPC</span><span class="sxs-lookup"><span data-stu-id="5a4d8-103">Security in gRPC applications</span></span>

<span data-ttu-id="5a4d8-104">V jakémkoli scénáři reálného světa je zabezpečení aplikací a služeb zásadní.</span><span class="sxs-lookup"><span data-stu-id="5a4d8-104">In any real-world scenario, securing applications and services is essential.</span></span> <span data-ttu-id="5a4d8-105">Zabezpečení pokrývá tři klíčové oblasti:</span><span class="sxs-lookup"><span data-stu-id="5a4d8-105">Security covers three key areas:</span></span> 

* <span data-ttu-id="5a4d8-106">Šifrování síťového provozu, aby nedocházelo ke škodlivému hackerům v zachycení.</span><span class="sxs-lookup"><span data-stu-id="5a4d8-106">Encrypting network traffic to prevent malicious hackers from intercepting it.</span></span>
* <span data-ttu-id="5a4d8-107">Ověřování klientů a serverů k navázání identity a vztahu důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="5a4d8-107">Authenticating clients and servers to establish identity and trust.</span></span>
* <span data-ttu-id="5a4d8-108">Autorizace klientů pro řízení přístupu k systémům a uplatnění oprávnění na základě identity.</span><span class="sxs-lookup"><span data-stu-id="5a4d8-108">Authorizing clients to control access to systems and apply permissions based on identity.</span></span>

> [!NOTE]
> <span data-ttu-id="5a4d8-109">*Ověřování* se týká vytvoření identity klienta nebo serveru.</span><span class="sxs-lookup"><span data-stu-id="5a4d8-109">*Authentication* is concerned with establishing the identity of a client or server.</span></span> <span data-ttu-id="5a4d8-110">K určení toho, jestli má klient oprávnění pro přístup k prostředku nebo k vystavení příkazu, se jedná o *autorizaci* .</span><span class="sxs-lookup"><span data-stu-id="5a4d8-110">*Authorization* is concerned with determining whether a client has permission to access a resource or issue a command.</span></span>

<span data-ttu-id="5a4d8-111">Tato kapitola se zabývá zařízeními pro ověřování a autorizaci v gRPC pro ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="5a4d8-111">This chapter will cover the facilities for authentication and authorization in gRPC for ASP.NET Core.</span></span> <span data-ttu-id="5a4d8-112">Bude taky projednávat zabezpečení sítě prostřednictvím šifrovaných připojení TLS.</span><span class="sxs-lookup"><span data-stu-id="5a4d8-112">It will also discuss network security through TLS encrypted connections.</span></span>

## <a name="wcf-authentication-and-authorization"></a><span data-ttu-id="5a4d8-113">Ověřování a autorizace WCF</span><span class="sxs-lookup"><span data-stu-id="5a4d8-113">WCF authentication and authorization</span></span>

<span data-ttu-id="5a4d8-114">V Windows Communication Foundation (WCF) byly ověřování a autorizace zpracovávány různými způsoby v závislosti na používaných přenosech a vazbách.</span><span class="sxs-lookup"><span data-stu-id="5a4d8-114">In Windows Communication Foundation (WCF), authentication and authorization were handled in different ways, depending on the transports and bindings being used.</span></span> <span data-ttu-id="5a4d8-115">Služba WCF podporuje různé standardy zabezpečení WS-\*.</span><span class="sxs-lookup"><span data-stu-id="5a4d8-115">WCF supported various WS-\* security standards.</span></span> <span data-ttu-id="5a4d8-116">Také podporuje ověřování systému Windows pro služby HTTP spuštěné ve službě IIS nebo NetTCP Services mezi systémy Windows.</span><span class="sxs-lookup"><span data-stu-id="5a4d8-116">It also supported Windows authentication for HTTP services running in IIS or NetTCP services between Windows systems.</span></span>

## <a name="grpc-authentication-and-authorization"></a><span data-ttu-id="5a4d8-117">ověřování a autorizace gRPC</span><span class="sxs-lookup"><span data-stu-id="5a4d8-117">gRPC authentication and authorization</span></span>

<span data-ttu-id="5a4d8-118">ověřování a autorizace gRPC funguje na dvou úrovních:</span><span class="sxs-lookup"><span data-stu-id="5a4d8-118">gRPC authentication and authorization works on two levels:</span></span>

* <span data-ttu-id="5a4d8-119">Ověřování/autorizace na úrovni volání je obvykle zpracovávána prostřednictvím tokenů, které jsou v metadatech při volání aplikovány.</span><span class="sxs-lookup"><span data-stu-id="5a4d8-119">Call-level authentication/authorization is usually handled through tokens that are applied in metadata when the call is made.</span></span> 
* <span data-ttu-id="5a4d8-120">Ověřování na úrovni kanálu používá klientský certifikát, který je použit na úrovni připojení.</span><span class="sxs-lookup"><span data-stu-id="5a4d8-120">Channel-level authentication uses a client certificate that's applied at the connection level.</span></span> <span data-ttu-id="5a4d8-121">Může také zahrnovat ověřování na úrovni volání/přihlašovací údaje autorizace pro automatické použití na každé volání kanálu.</span><span class="sxs-lookup"><span data-stu-id="5a4d8-121">It can also include call-level authentication/authorization credentials to be applied to every call on the channel automatically.</span></span> 

<span data-ttu-id="5a4d8-122">Ke zvýšení zabezpečení služby můžete použít jeden nebo oba tyto mechanismy.</span><span class="sxs-lookup"><span data-stu-id="5a4d8-122">You can use either or both of these mechanisms to help secure your service.</span></span>

<span data-ttu-id="5a4d8-123">ASP.NET Core implementace gRPC podporuje ověřování a autorizaci prostřednictvím většiny standardních ASP.NET Core mechanismů:</span><span class="sxs-lookup"><span data-stu-id="5a4d8-123">The ASP.NET Core implementation of gRPC supports authentication and authorization through most of the standard ASP.NET Core mechanisms:</span></span>

- <span data-ttu-id="5a4d8-124">Volání ověřování</span><span class="sxs-lookup"><span data-stu-id="5a4d8-124">Call authentication</span></span>
  - <span data-ttu-id="5a4d8-125">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="5a4d8-125">Azure Active Directory</span></span>
  - <span data-ttu-id="5a4d8-126">IdentityServer</span><span class="sxs-lookup"><span data-stu-id="5a4d8-126">IdentityServer</span></span>
  - <span data-ttu-id="5a4d8-127">Nosný token JWT</span><span class="sxs-lookup"><span data-stu-id="5a4d8-127">JWT Bearer Token</span></span>
  - <span data-ttu-id="5a4d8-128">OAuth 2.0</span><span class="sxs-lookup"><span data-stu-id="5a4d8-128">OAuth 2.0</span></span>
  - <span data-ttu-id="5a4d8-129">OpenID Connect</span><span class="sxs-lookup"><span data-stu-id="5a4d8-129">OpenID Connect</span></span>
  - <span data-ttu-id="5a4d8-130">WS-Federation</span><span class="sxs-lookup"><span data-stu-id="5a4d8-130">WS-Federation</span></span>
- <span data-ttu-id="5a4d8-131">Ověřování kanálu</span><span class="sxs-lookup"><span data-stu-id="5a4d8-131">Channel authentication</span></span>
  - <span data-ttu-id="5a4d8-132">certifikát klienta</span><span class="sxs-lookup"><span data-stu-id="5a4d8-132">Client certificate</span></span>

<span data-ttu-id="5a4d8-133">Metody ověřování volání jsou všechny založené na *tokenech*.</span><span class="sxs-lookup"><span data-stu-id="5a4d8-133">The call authentication methods are all based on *tokens*.</span></span> <span data-ttu-id="5a4d8-134">Jediným skutečným rozdílem je způsob, jakým se generují tokeny, a knihovny, které slouží k ověření tokenů ve službě ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="5a4d8-134">The only real difference is how the tokens are generated and the libraries that are used to validate the tokens in the ASP.NET Core service.</span></span>

<span data-ttu-id="5a4d8-135">Další informace najdete v článku o [ověřování a autorizaci](/aspnet/core/grpc/authn-and-authz) .</span><span class="sxs-lookup"><span data-stu-id="5a4d8-135">For more information, see the [Authentication and authorization](/aspnet/core/grpc/authn-and-authz) article.</span></span>

> [!NOTE]
> <span data-ttu-id="5a4d8-136">Pokud používáte gRPC prostřednictvím připojení HTTP/2 zašifrovaného protokolem TLS, bude veškerý provoz mezi klienty a servery zašifrovaný, i když nepoužíváte ověřování na úrovni kanálu.</span><span class="sxs-lookup"><span data-stu-id="5a4d8-136">When you're using gRPC over a TLS-encrypted HTTP/2 connection, all traffic between clients and servers is encrypted, even if you don't use channel-level authentication.</span></span>

<span data-ttu-id="5a4d8-137">V této kapitole se dozvíte, jak použít přihlašovací údaje volání a přihlašovací údaje kanálu ke službě gRPC.</span><span class="sxs-lookup"><span data-stu-id="5a4d8-137">This chapter will show how to apply call credentials and channel credentials to a gRPC service.</span></span> <span data-ttu-id="5a4d8-138">Zobrazí také informace o použití přihlašovacích údajů z klienta .NET Core gRPC k ověřování pomocí služby.</span><span class="sxs-lookup"><span data-stu-id="5a4d8-138">It will also show how to use credentials from a .NET Core gRPC client to authenticate with the service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5a4d8-139">[Předchozí](client-libraries.md)
>[Další](call-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="5a4d8-139">[Previous](client-libraries.md)
[Next](call-credentials.md)</span></span>
