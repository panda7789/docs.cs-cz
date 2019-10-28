---
title: Základní programování WCF
ms.date: 03/30/2017
helpviewer_keywords:
- basic programming [WCF]
- WCF [WCF], basic programming
- WCF [WCF], programming
- Windows Communication Foundation [WCF], basic programming
- Windows Communication Foundation [WCF], programming
ms.assetid: 3ae3d498-f43c-4ecc-8cc0-6cbe36b62593
ms.openlocfilehash: eff565fa18e3360170584395adcf2a3e7029ac07
ms.sourcegitcommit: 9b2ef64c4fc10a4a10f28a223d60d17d7d249ee8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/26/2019
ms.locfileid: "72960936"
---
# <a name="basic-wcf-programming"></a><span data-ttu-id="7a0d2-102">Základní programování WCF</span><span class="sxs-lookup"><span data-stu-id="7a0d2-102">Basic WCF programming</span></span>

<span data-ttu-id="7a0d2-103">V této části se seznámíte se základy vytváření aplikací Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7a0d2-103">This section presents the fundamentals for creating Windows Communication Foundation (WCF) applications.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="7a0d2-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="7a0d2-104">In this section</span></span>

 <span data-ttu-id="7a0d2-105">[Základní životní cyklus programování](basic-programming-lifecycle.md)</span><span class="sxs-lookup"><span data-stu-id="7a0d2-105">[Basic Programming Lifecycle](basic-programming-lifecycle.md)</span></span>\
 <span data-ttu-id="7a0d2-106">Popisuje životní cyklus navrhování, sestavování a nasazování služeb WCF a klientských aplikací.</span><span class="sxs-lookup"><span data-stu-id="7a0d2-106">Describes the lifecycle of designing, building, and deploying WCF service and client applications.</span></span>

 <span data-ttu-id="7a0d2-107">[Navrhování a implementace služeb](designing-and-implementing-services.md)</span><span class="sxs-lookup"><span data-stu-id="7a0d2-107">[Designing and Implementing Services](designing-and-implementing-services.md)</span></span>\
 <span data-ttu-id="7a0d2-108">V této části najdete popis postupu při návrhu a implementaci kontraktu služby, výběru způsobu výměny zpráv, určení smlouvy o selhání a dalších základních aspektů služeb.</span><span class="sxs-lookup"><span data-stu-id="7a0d2-108">Describes how to design and implement a service contract, choose a message exchange pattern, specify a fault contract, and other basic aspects of services.</span></span>

 <span data-ttu-id="7a0d2-109">[Konfigurace služeb](configuring-services.md)</span><span class="sxs-lookup"><span data-stu-id="7a0d2-109">[Configuring Services](configuring-services.md)</span></span>\
 <span data-ttu-id="7a0d2-110">Popisuje, jak nakonfigurovat službu WCF pro podporu požadavků na kontrakt, přizpůsobit chování místního prostředí za běhu a označit adresu pro publikování služby.</span><span class="sxs-lookup"><span data-stu-id="7a0d2-110">Describes how to configure a WCF service to support the contract requirements, customize local runtime behavior, and indicate the address to publish the service.</span></span>

 <span data-ttu-id="7a0d2-111">\ [hostování služeb](hosting-services.md)</span><span class="sxs-lookup"><span data-stu-id="7a0d2-111">[Hosting Services](hosting-services.md)\</span></span>
 <span data-ttu-id="7a0d2-112">Popisuje základy hostování služeb v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7a0d2-112">Describes the basics of hosting services in an application.</span></span>

 <span data-ttu-id="7a0d2-113">[Sestavování klientů](building-clients.md)</span><span class="sxs-lookup"><span data-stu-id="7a0d2-113">[Building Clients](building-clients.md)</span></span>\
 <span data-ttu-id="7a0d2-114">Popisuje, jak získat metadata ze služeb, jak je převést na kód klienta WCF, zvládnout problémy zabezpečení a sestavovat, konfigurovat a hostovat klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="7a0d2-114">Describes how to obtain metadata from services, convert that into WCF client code, handle security issues, and build, configure, and host a WCF client.</span></span>

 <span data-ttu-id="7a0d2-115">[Úvod do rozšíření](introduction-to-extensibility.md)</span><span class="sxs-lookup"><span data-stu-id="7a0d2-115">[Introduction to Extensibility](introduction-to-extensibility.md)</span></span>\
 <span data-ttu-id="7a0d2-116">Popisuje, jak rozšiřuje WCF na vytváření vlastních řešení.</span><span class="sxs-lookup"><span data-stu-id="7a0d2-116">Describes how to extend WCF to create custom solutions.</span></span>

 <span data-ttu-id="7a0d2-117">[Řešení potíží s rychlým startem WCF](wcf-troubleshooting-quickstart.md)</span><span class="sxs-lookup"><span data-stu-id="7a0d2-117">[WCF Troubleshooting Quickstart](wcf-troubleshooting-quickstart.md)</span></span>\
 <span data-ttu-id="7a0d2-118">Popisuje některé z nejběžnějších problémů, ke kterým dochází, co můžete udělat k jejich řešení a kde najdete další informace o problému.</span><span class="sxs-lookup"><span data-stu-id="7a0d2-118">Describes some of the most common issues that occur, what you can do to solve them, and where to locate more information about the issue.</span></span>

 <span data-ttu-id="7a0d2-119">\ [webového rozhraní API WCF a ASP.NET](wcf-and-aspnet-web-api.md)</span><span class="sxs-lookup"><span data-stu-id="7a0d2-119">[WCF and ASP.NET Web API](wcf-and-aspnet-web-api.md)\</span></span>
 <span data-ttu-id="7a0d2-120">Popisuje tyto dvě technologie, jejich vzájemné propojení a kdy je lze použít.</span><span class="sxs-lookup"><span data-stu-id="7a0d2-120">Discusses the two technologies, how they relate to each other, and when to use them.</span></span>

## <a name="reference"></a><span data-ttu-id="7a0d2-121">Odkaz</span><span class="sxs-lookup"><span data-stu-id="7a0d2-121">Reference</span></span>

- <xref:System.ServiceModel>
- <xref:System.ServiceModel.Channels>
- <xref:System.ServiceModel.Description>

## <a name="related-sections"></a><span data-ttu-id="7a0d2-122">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="7a0d2-122">Related sections</span></span>

- [<span data-ttu-id="7a0d2-123">Koncepční přehled</span><span class="sxs-lookup"><span data-stu-id="7a0d2-123">Conceptual Overview</span></span>](conceptual-overview.md)
- [<span data-ttu-id="7a0d2-124">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="7a0d2-124">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="7a0d2-125">Pokyny a osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="7a0d2-125">Guidelines and Best Practices</span></span>](guidelines-and-best-practices.md)
- [<span data-ttu-id="7a0d2-126">Nástroje Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="7a0d2-126">Windows Communication Foundation Tools</span></span>](tools.md)
- [<span data-ttu-id="7a0d2-127">Ukázky Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="7a0d2-127">Windows Communication Foundation (WCF) samples</span></span>](./samples/index.md)
- [<span data-ttu-id="7a0d2-128">Začínáme</span><span class="sxs-lookup"><span data-stu-id="7a0d2-128">Getting Started</span></span>](./samples/getting-started-sample.md)
- [<span data-ttu-id="7a0d2-129">Hostování IIS pomocí vloženého kódu</span><span class="sxs-lookup"><span data-stu-id="7a0d2-129">IIS Hosting Using Inline Code</span></span>](./samples/iis-hosting-using-inline-code.md)
- [<span data-ttu-id="7a0d2-130">Vlastní hostování</span><span class="sxs-lookup"><span data-stu-id="7a0d2-130">Self-Host</span></span>](./samples/self-host.md)
