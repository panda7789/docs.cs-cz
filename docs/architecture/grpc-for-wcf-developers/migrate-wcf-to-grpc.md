---
title: Migrace řešení WCF do gRPC-gRPC pro vývojáře WCF
description: Postup migrace různých typů služeb WCF na ekvivalent v gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 12e724ab46a33547d352da7a604a5a994e617bc2
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628511"
---
# <a name="migrate-a-wcf-solution-to-grpc"></a><span data-ttu-id="3a128-103">Migrace řešení WCF do gRPC</span><span class="sxs-lookup"><span data-stu-id="3a128-103">Migrate a WCF solution to gRPC</span></span>

<span data-ttu-id="3a128-104">Tato kapitola popisuje, jak pracovat s projekty ASP.NET Core 3,0 gRPC a předvést migraci různých typů služeb Windows Communication Foundation (WCF) na gRPC ekvivalent:</span><span class="sxs-lookup"><span data-stu-id="3a128-104">This chapter will describe how to work with ASP.NET Core 3.0 gRPC projects and demonstrate migrating different types of Windows Communication Foundation (WCF) services to the gRPC equivalent:</span></span>

- <span data-ttu-id="3a128-105">Vytvořte projekt ASP.NET Core 3,0 gRPC.</span><span class="sxs-lookup"><span data-stu-id="3a128-105">Create an ASP.NET Core 3.0 gRPC project.</span></span>
- <span data-ttu-id="3a128-106">Jednoduché operace požadavek-odpověď na gRPC unárního RPC.</span><span class="sxs-lookup"><span data-stu-id="3a128-106">Simple request-reply operations to gRPC unary RPC.</span></span>
- <span data-ttu-id="3a128-107">Jednosměrné operace pro gRPC streamování klientů RPC</span><span class="sxs-lookup"><span data-stu-id="3a128-107">One-way operations to gRPC client streaming RPC.</span></span>
- <span data-ttu-id="3a128-108">Plně duplexní služby pro gRPC obousměrného streamování RPC.</span><span class="sxs-lookup"><span data-stu-id="3a128-108">Full-duplex services to gRPC bidirectional streaming RPC.</span></span>

<span data-ttu-id="3a128-109">Existuje také porovnání používání služby streamování a opakujících se polí pro vrácení datových sad a existuje diskuze o použití klientských knihoven na konci kapitoly.</span><span class="sxs-lookup"><span data-stu-id="3a128-109">There's also a comparison of using streaming services versus repeated fields for returning datasets, and there's a discussion of the use of client libraries at the end of the chapter.</span></span>

<span data-ttu-id="3a128-110">Ukázková aplikace WCF je minimální zástupná procedura sady burzovních obchodních služeb.</span><span class="sxs-lookup"><span data-stu-id="3a128-110">The sample WCF application is a minimal stub of a set of stock trading services.</span></span> <span data-ttu-id="3a128-111">Pro vkládání závislostí používá knihovnu kontejnerů Open Source Inversion Control (IoC) s názvem Autofac.</span><span class="sxs-lookup"><span data-stu-id="3a128-111">It uses the open-source Inversion of Control (IoC) container library called Autofac for dependency injection.</span></span> <span data-ttu-id="3a128-112">Zahrnuje tři služby, jeden pro každý typ služby WCF.</span><span class="sxs-lookup"><span data-stu-id="3a128-112">It includes three services, one for each WCF service type.</span></span> <span data-ttu-id="3a128-113">V následujících částech jsou popsány podrobné informace o službách.</span><span class="sxs-lookup"><span data-stu-id="3a128-113">The services will be discussed in more detail in the following sections.</span></span> <span data-ttu-id="3a128-114">Řešení můžete stáhnout z příkazu [dotnet-Architecture/grpc-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="3a128-114">You can download the solutions from [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) on GitHub.</span></span> <span data-ttu-id="3a128-115">Služby používají falešná data k minimalizaci externích závislostí.</span><span class="sxs-lookup"><span data-stu-id="3a128-115">The services use fake data to minimize external dependencies.</span></span>

<span data-ttu-id="3a128-116">Ukázky zahrnují implementace WCF a gRPC každé služby.</span><span class="sxs-lookup"><span data-stu-id="3a128-116">The samples include the WCF and gRPC implementations of each service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="3a128-117">[Předchozí](ws-protocols.md)
>[Další](create-project.md)</span><span class="sxs-lookup"><span data-stu-id="3a128-117">[Previous](ws-protocols.md)
[Next](create-project.md)</span></span>
