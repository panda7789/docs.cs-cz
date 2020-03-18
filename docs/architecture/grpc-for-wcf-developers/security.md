---
title: Zabezpečení v gRPC aplikacích - gRPC pro vývojáře WCF
description: Přehled ověřování a autorizace volání a kanálů v gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 70cbf441bbc1b299b997f7d1f02bcd2bf7fde60c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147812"
---
# <a name="security-in-grpc-applications"></a><span data-ttu-id="a7ac3-103">Zabezpečení v aplikacích gRPC</span><span class="sxs-lookup"><span data-stu-id="a7ac3-103">Security in gRPC applications</span></span>

<span data-ttu-id="a7ac3-104">V každém reálném scénáři je zabezpečení aplikací a služeb nezbytné.</span><span class="sxs-lookup"><span data-stu-id="a7ac3-104">In any real-world scenario, securing applications and services is essential.</span></span> <span data-ttu-id="a7ac3-105">Bezpečnost zahrnuje tři klíčové oblasti:</span><span class="sxs-lookup"><span data-stu-id="a7ac3-105">Security covers three key areas:</span></span>

* <span data-ttu-id="a7ac3-106">Šifrování síťového provozu, aby se zabránilo škodlivým hackerům v jeho zachycení.</span><span class="sxs-lookup"><span data-stu-id="a7ac3-106">Encrypting network traffic to prevent malicious hackers from intercepting it.</span></span>
* <span data-ttu-id="a7ac3-107">Ověřování klientů a serverů za účelem vytvoření identity a důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="a7ac3-107">Authenticating clients and servers to establish identity and trust.</span></span>
* <span data-ttu-id="a7ac3-108">Autorizace klientů k řízení přístupu k systémům a použití oprávnění na základě identity.</span><span class="sxs-lookup"><span data-stu-id="a7ac3-108">Authorizing clients to control access to systems and apply permissions based on identity.</span></span>

> [!NOTE]
> <span data-ttu-id="a7ac3-109">*Ověřování* se týká zjištění identity klienta nebo serveru.</span><span class="sxs-lookup"><span data-stu-id="a7ac3-109">*Authentication* is concerned with establishing the identity of a client or server.</span></span> <span data-ttu-id="a7ac3-110">*Autorizace* se týká určení, zda má klient oprávnění k přístupu k prostředku nebo k vydání příkazu.</span><span class="sxs-lookup"><span data-stu-id="a7ac3-110">*Authorization* is concerned with determining whether a client has permission to access a resource or issue a command.</span></span>

<span data-ttu-id="a7ac3-111">Tato kapitola se bude týkat zařízení pro ověřování a autorizaci v gRPC pro ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7ac3-111">This chapter will cover the facilities for authentication and authorization in gRPC for ASP.NET Core.</span></span> <span data-ttu-id="a7ac3-112">Bude také diskutovat o zabezpečení sítě prostřednictvím šifrovaných připojení TLS.</span><span class="sxs-lookup"><span data-stu-id="a7ac3-112">It will also discuss network security through TLS encrypted connections.</span></span>

## <a name="wcf-authentication-and-authorization"></a><span data-ttu-id="a7ac3-113">Ověřování a autorizace WCF</span><span class="sxs-lookup"><span data-stu-id="a7ac3-113">WCF authentication and authorization</span></span>

<span data-ttu-id="a7ac3-114">V systému Windows Communication Foundation (WCF) ověřování a autorizace byly zpracovány různými způsoby, v závislosti na přenosy a vazby používané.</span><span class="sxs-lookup"><span data-stu-id="a7ac3-114">In Windows Communication Foundation (WCF), authentication and authorization were handled in different ways, depending on the transports and bindings being used.</span></span> <span data-ttu-id="a7ac3-115">WCF podporovalrůzné standardy\* zabezpečení WS.</span><span class="sxs-lookup"><span data-stu-id="a7ac3-115">WCF supported various WS-\* security standards.</span></span> <span data-ttu-id="a7ac3-116">Podporovala také ověřování systému Windows pro služby HTTP spuštěné ve službě IIS nebo nettcp služby mezi systémy Windows.</span><span class="sxs-lookup"><span data-stu-id="a7ac3-116">It also supported Windows authentication for HTTP services running in IIS or NetTCP services between Windows systems.</span></span>

## <a name="grpc-authentication-and-authorization"></a><span data-ttu-id="a7ac3-117">gRPC ověřování a autorizace</span><span class="sxs-lookup"><span data-stu-id="a7ac3-117">gRPC authentication and authorization</span></span>

<span data-ttu-id="a7ac3-118">gRPC ověřování a autorizace funguje na dvou úrovních:</span><span class="sxs-lookup"><span data-stu-id="a7ac3-118">gRPC authentication and authorization works on two levels:</span></span>

* <span data-ttu-id="a7ac3-119">Ověřování/autorizace na úrovni volání se obvykle zpracovává prostřednictvím tokenů, které jsou použity v metadatech při volání.</span><span class="sxs-lookup"><span data-stu-id="a7ac3-119">Call-level authentication/authorization is usually handled through tokens that are applied in metadata when the call is made.</span></span>
* <span data-ttu-id="a7ac3-120">Ověřování na úrovni kanálu používá klientský certifikát, který je použit na úrovni připojení.</span><span class="sxs-lookup"><span data-stu-id="a7ac3-120">Channel-level authentication uses a client certificate that's applied at the connection level.</span></span> <span data-ttu-id="a7ac3-121">Může také obsahovat pověření pro ověřování/autorizaci na úrovni volání, která se použijí na každé volání v kanálu automaticky.</span><span class="sxs-lookup"><span data-stu-id="a7ac3-121">It can also include call-level authentication/authorization credentials to be applied to every call on the channel automatically.</span></span>

<span data-ttu-id="a7ac3-122">Můžete použít jeden nebo oba tyto mechanismy k zabezpečení služby.</span><span class="sxs-lookup"><span data-stu-id="a7ac3-122">You can use either or both of these mechanisms to help secure your service.</span></span>

<span data-ttu-id="a7ac3-123">ASP.NET Core implementace gRPC podporuje ověřování a autorizaci prostřednictvím většiny standardních ASP.NET core mechanismy:</span><span class="sxs-lookup"><span data-stu-id="a7ac3-123">The ASP.NET Core implementation of gRPC supports authentication and authorization through most of the standard ASP.NET Core mechanisms:</span></span>

- <span data-ttu-id="a7ac3-124">Ověření volání</span><span class="sxs-lookup"><span data-stu-id="a7ac3-124">Call authentication</span></span>
  - <span data-ttu-id="a7ac3-125">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="a7ac3-125">Azure Active Directory</span></span>
  - <span data-ttu-id="a7ac3-126">IdentityServer</span><span class="sxs-lookup"><span data-stu-id="a7ac3-126">IdentityServer</span></span>
  - <span data-ttu-id="a7ac3-127">JWT Žeton nosiče</span><span class="sxs-lookup"><span data-stu-id="a7ac3-127">JWT Bearer Token</span></span>
  - <span data-ttu-id="a7ac3-128">OAuth 2.0</span><span class="sxs-lookup"><span data-stu-id="a7ac3-128">OAuth 2.0</span></span>
  - <span data-ttu-id="a7ac3-129">OpenID Connect</span><span class="sxs-lookup"><span data-stu-id="a7ac3-129">OpenID Connect</span></span>
  - <span data-ttu-id="a7ac3-130">WS-Federation</span><span class="sxs-lookup"><span data-stu-id="a7ac3-130">WS-Federation</span></span>
- <span data-ttu-id="a7ac3-131">Ověřování kanálu</span><span class="sxs-lookup"><span data-stu-id="a7ac3-131">Channel authentication</span></span>
  - <span data-ttu-id="a7ac3-132">Klientský certifikát</span><span class="sxs-lookup"><span data-stu-id="a7ac3-132">Client certificate</span></span>

<span data-ttu-id="a7ac3-133">Všechny metody ověřování volání jsou založeny na *tokenech*.</span><span class="sxs-lookup"><span data-stu-id="a7ac3-133">The call authentication methods are all based on *tokens*.</span></span> <span data-ttu-id="a7ac3-134">Jediným skutečným rozdílem je, jak jsou generovány tokeny a knihovny, které se používají k ověření tokeny ve službě ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7ac3-134">The only real difference is how the tokens are generated and the libraries that are used to validate the tokens in the ASP.NET Core service.</span></span>

<span data-ttu-id="a7ac3-135">Další informace naleznete v článku [Ověřování a autorizace.](/aspnet/core/grpc/authn-and-authz)</span><span class="sxs-lookup"><span data-stu-id="a7ac3-135">For more information, see the [Authentication and authorization](/aspnet/core/grpc/authn-and-authz) article.</span></span>

> [!NOTE]
> <span data-ttu-id="a7ac3-136">Pokud používáte gRPC přes připojení HTTP/2 šifrované protokolem TLS, veškerý provoz mezi klienty a servery je šifrován, i když nepoužíváte ověřování na úrovni kanálu.</span><span class="sxs-lookup"><span data-stu-id="a7ac3-136">When you're using gRPC over a TLS-encrypted HTTP/2 connection, all traffic between clients and servers is encrypted, even if you don't use channel-level authentication.</span></span>

<span data-ttu-id="a7ac3-137">Tato kapitola ukáže, jak použít pověření volání a pověření kanálu pro službu gRPC.</span><span class="sxs-lookup"><span data-stu-id="a7ac3-137">This chapter will show how to apply call credentials and channel credentials to a gRPC service.</span></span> <span data-ttu-id="a7ac3-138">Také ukáže, jak používat pověření z klienta .NET Core gRPC k ověření se službou.</span><span class="sxs-lookup"><span data-stu-id="a7ac3-138">It will also show how to use credentials from a .NET Core gRPC client to authenticate with the service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a7ac3-139">[Předchozí](client-libraries.md)
>[další](call-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="a7ac3-139">[Previous](client-libraries.md)
[Next](call-credentials.md)</span></span>
