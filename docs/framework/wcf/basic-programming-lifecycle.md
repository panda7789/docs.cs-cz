---
title: Základní programovací životní cyklus
ms.date: 03/30/2017
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
ms.openlocfilehash: fe578ba3c655c9c9ea8398b9b2e4d4f974153c8e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320815"
---
# <a name="basic-programming-lifecycle"></a><span data-ttu-id="d88e8-102">Základní programovací životní cyklus</span><span class="sxs-lookup"><span data-stu-id="d88e8-102">Basic Programming Lifecycle</span></span>
<span data-ttu-id="d88e8-103">Windows Communication Foundation (WCF) umožňuje aplikacím komunikovat bez ohledu na to, jestli jsou ve stejném počítači, přes Internet nebo na různých aplikačních platformách.</span><span class="sxs-lookup"><span data-stu-id="d88e8-103">Windows Communication Foundation (WCF) enables applications to communicate whether they are on the same computer, across the Internet, or on different application platforms.</span></span> <span data-ttu-id="d88e8-104">Toto téma popisuje úkoly, které jsou nutné k vytvoření aplikace WCF.</span><span class="sxs-lookup"><span data-stu-id="d88e8-104">This topic outlines the tasks that are required to build a WCF application.</span></span> <span data-ttu-id="d88e8-105">Pracovní ukázkovou aplikaci najdete v tématu [Začínáme kurzu](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="d88e8-105">For a working sample application, see [Getting Started Tutorial](getting-started-tutorial.md).</span></span>  
  
## <a name="the-basic-tasks"></a><span data-ttu-id="d88e8-106">Základní úlohy</span><span class="sxs-lookup"><span data-stu-id="d88e8-106">The Basic Tasks</span></span>  
 <span data-ttu-id="d88e8-107">Základní úkoly, které je potřeba provést, jsou v uvedeném pořadí:</span><span class="sxs-lookup"><span data-stu-id="d88e8-107">The basic tasks to perform are, in order:</span></span>  
  
1. <span data-ttu-id="d88e8-108">Definujte kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="d88e8-108">Define the service contract.</span></span> <span data-ttu-id="d88e8-109">Kontrakt služby určuje podpis služby, data, která vyměňuje, a další smluvní požadovaná data.</span><span class="sxs-lookup"><span data-stu-id="d88e8-109">A service contract specifies the signature of a service, the data it exchanges, and other contractually required data.</span></span> <span data-ttu-id="d88e8-110">Další informace najdete v tématu [Navrhování kontraktů služby](designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="d88e8-110">For more information, see [Designing Service Contracts](designing-service-contracts.md).</span></span>  
  
2. <span data-ttu-id="d88e8-111">Implementujte kontrakt.</span><span class="sxs-lookup"><span data-stu-id="d88e8-111">Implement the contract.</span></span> <span data-ttu-id="d88e8-112">Chcete-li implementovat kontrakt služby, vytvořte třídu, která implementuje kontrakt a určete vlastní chování, které má modul runtime mít.</span><span class="sxs-lookup"><span data-stu-id="d88e8-112">To implement a service contract, create a class that implements the contract and specify custom behaviors that the runtime should have.</span></span> <span data-ttu-id="d88e8-113">Další informace najdete v tématu [implementace kontraktů služeb](implementing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="d88e8-113">For more information, see [Implementing Service Contracts](implementing-service-contracts.md).</span></span>  
  
3. <span data-ttu-id="d88e8-114">Nakonfigurujte službu zadáním koncových bodů a dalších informací o chování.</span><span class="sxs-lookup"><span data-stu-id="d88e8-114">Configure the service by specifying endpoints and other behavior information.</span></span> <span data-ttu-id="d88e8-115">Další informace najdete v tématu [Konfigurace služeb](configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="d88e8-115">For more information, see [Configuring Services](configuring-services.md).</span></span>  
  
4. <span data-ttu-id="d88e8-116">Hostování služby.</span><span class="sxs-lookup"><span data-stu-id="d88e8-116">Host the service.</span></span> <span data-ttu-id="d88e8-117">Další informace najdete v tématu [hostující služby](hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="d88e8-117">For more information, see [Hosting Services](hosting-services.md).</span></span>  
  
5. <span data-ttu-id="d88e8-118">Sestavte klientskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d88e8-118">Build a client application.</span></span> <span data-ttu-id="d88e8-119">Další informace najdete v tématu [sestavování klientů](building-clients.md).</span><span class="sxs-lookup"><span data-stu-id="d88e8-119">For more information, see [Building Clients](building-clients.md).</span></span>  
  
 <span data-ttu-id="d88e8-120">I když se témata v této části řídí tímto pořadím, některé scénáře se na začátku nespustí.</span><span class="sxs-lookup"><span data-stu-id="d88e8-120">Although the topics in this section follow this order, some scenarios do not start at the beginning.</span></span> <span data-ttu-id="d88e8-121">Pokud například chcete vytvořit klienta pro existující službu, začněte v kroku 5.</span><span class="sxs-lookup"><span data-stu-id="d88e8-121">For example, if you want to build a client for a pre-existing service, you start at step 5.</span></span> <span data-ttu-id="d88e8-122">Nebo pokud vytváříte službu, kterou budou používat jiní uživatelé, můžete přeskočit krok 5.</span><span class="sxs-lookup"><span data-stu-id="d88e8-122">Or if you are building a service that others will use, you may skip step 5.</span></span>  
  
 <span data-ttu-id="d88e8-123">Jakmile se seznámíte s vývojem kontraktů služby, můžete si také přečíst [Úvod k rozšíření](introduction-to-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="d88e8-123">Once you are familiar with developing service contracts, you can also read [Introduction to Extensibility](introduction-to-extensibility.md).</span></span> <span data-ttu-id="d88e8-124">Pokud máte ve své službě problémy, podívejte se na [rychlý Start pro řešení potíží WCF](wcf-troubleshooting-quickstart.md) a podívejte se, jestli mají ostatní stejné nebo podobné problémy.</span><span class="sxs-lookup"><span data-stu-id="d88e8-124">If you have problems with your service, check [WCF Troubleshooting Quickstart](wcf-troubleshooting-quickstart.md) to see whether others have the same or similar problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d88e8-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d88e8-125">See also</span></span>

- [<span data-ttu-id="d88e8-126">Implementace kontraktů služeb</span><span class="sxs-lookup"><span data-stu-id="d88e8-126">Implementing Service Contracts</span></span>](implementing-service-contracts.md)
