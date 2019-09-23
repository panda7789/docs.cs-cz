---
title: Migrace řešení WCF do gRPC-gRPC pro vývojáře WCF
description: Postup migrace různých typů služby WCF na ekvivalent v gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: a9cfb87361194d998a3c4dfff4fe434be64f0d65
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184293"
---
# <a name="migrate-a-wcf-solution-to-grpc"></a><span data-ttu-id="0a461-103">Migrace řešení WCF do gRPC</span><span class="sxs-lookup"><span data-stu-id="0a461-103">Migrate a WCF solution to gRPC</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="0a461-104">V této kapitole se dozvíte, jak pracovat s projekty ASP.NET Core 3,0 gRPC a předvádíme migraci různých typů služeb WCF na gRPC ekvivalent:</span><span class="sxs-lookup"><span data-stu-id="0a461-104">This chapter will look at how to work with ASP.NET Core 3.0 gRPC projects and demonstrate migrating different types of WCF service to the gRPC equivalent:</span></span>

- <span data-ttu-id="0a461-105">Vytvořte projekt ASP.NET Core 3,0 gRPC.</span><span class="sxs-lookup"><span data-stu-id="0a461-105">Create an ASP.NET Core 3.0 gRPC project.</span></span>
- <span data-ttu-id="0a461-106">Jednoduché operace požadavek-odpověď na gRPC unárního RPC.</span><span class="sxs-lookup"><span data-stu-id="0a461-106">Simple Request-Reply operations to gRPC unary RPC.</span></span>
- <span data-ttu-id="0a461-107">Jednosměrné operace pro gRPC streamování klientů RPC</span><span class="sxs-lookup"><span data-stu-id="0a461-107">One-way operations to gRPC client streaming RPC.</span></span>
- <span data-ttu-id="0a461-108">Plně duplexní služby pro gRPC obousměrného streamování RPC.</span><span class="sxs-lookup"><span data-stu-id="0a461-108">Full Duplex services to gRPC bidirectional streaming RPC.</span></span>

<span data-ttu-id="0a461-109">Existuje také porovnání používání služby streamování a opakujících se polí pro vracení datových sad a použití klientských knihoven na konci kapitoly.</span><span class="sxs-lookup"><span data-stu-id="0a461-109">There's also a comparison of using streaming services versus repeated fields for returning data sets, and the use of client libraries at the end of the chapter.</span></span>

<span data-ttu-id="0a461-110">Ukázková aplikace WCF je minimální zástupná procedura sady burzovních obchodních služeb s použitím open source knihovny kontejnerů IoC (inverze Control) s názvem *Autofac* pro vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="0a461-110">The sample WCF application is a minimal stub of a set of stock trading services, using the open-source Inversion of Control (IoC) container library called *Autofac* for dependency injection.</span></span> <span data-ttu-id="0a461-111">Zahrnuje tři služby, jeden pro každý typ služby WCF.</span><span class="sxs-lookup"><span data-stu-id="0a461-111">It includes three services, one for each WCF service type.</span></span> <span data-ttu-id="0a461-112">V následujících částech jsou popsány podrobné informace o službách.</span><span class="sxs-lookup"><span data-stu-id="0a461-112">The services will be discussed in more detail in the following sections.</span></span> <span data-ttu-id="0a461-113">Řešení je možné stáhnout z [RendleLabs/grpc-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="0a461-113">The solutions can be downloaded from [RendleLabs/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) on GitHub.</span></span> <span data-ttu-id="0a461-114">Služby používají falešná data k minimalizaci externích závislostí.</span><span class="sxs-lookup"><span data-stu-id="0a461-114">The services use fake data to minimize external dependencies.</span></span>

<span data-ttu-id="0a461-115">Ukázky zahrnují implementace WCF a gRPC každé služby.</span><span class="sxs-lookup"><span data-stu-id="0a461-115">The samples include the WCF and gRPC implementations of each service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0a461-116">[Předchozí](ws-protocols.md)
>[Další](create-project.md)</span><span class="sxs-lookup"><span data-stu-id="0a461-116">[Previous](ws-protocols.md)
[Next](create-project.md)</span></span>
