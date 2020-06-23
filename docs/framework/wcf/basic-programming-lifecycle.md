---
title: Základní programovací životní cyklus
description: Přečtěte si informace o úlohách pro sestavení aplikace WCF. WCF umožňuje aplikacím komunikovat na stejném počítači, v sítích nebo na různých platformách aplikace.
ms.date: 03/30/2017
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
ms.openlocfilehash: c672827fff780fd263f5355520bb6ccf02bb902e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245528"
---
# <a name="basic-programming-lifecycle"></a><span data-ttu-id="88dc9-104">Základní programovací životní cyklus</span><span class="sxs-lookup"><span data-stu-id="88dc9-104">Basic Programming Lifecycle</span></span>
<span data-ttu-id="88dc9-105">Windows Communication Foundation (WCF) umožňuje aplikacím komunikovat bez ohledu na to, jestli jsou ve stejném počítači, přes Internet nebo na různých aplikačních platformách.</span><span class="sxs-lookup"><span data-stu-id="88dc9-105">Windows Communication Foundation (WCF) enables applications to communicate whether they are on the same computer, across the Internet, or on different application platforms.</span></span> <span data-ttu-id="88dc9-106">Toto téma popisuje úkoly, které jsou nutné k vytvoření aplikace WCF.</span><span class="sxs-lookup"><span data-stu-id="88dc9-106">This topic outlines the tasks that are required to build a WCF application.</span></span> <span data-ttu-id="88dc9-107">Pracovní ukázkovou aplikaci najdete v tématu [Začínáme kurzu](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="88dc9-107">For a working sample application, see [Getting Started Tutorial](getting-started-tutorial.md).</span></span>  
  
## <a name="the-basic-tasks"></a><span data-ttu-id="88dc9-108">Základní úlohy</span><span class="sxs-lookup"><span data-stu-id="88dc9-108">The Basic Tasks</span></span>  
 <span data-ttu-id="88dc9-109">Základní úkoly, které je potřeba provést, jsou v uvedeném pořadí:</span><span class="sxs-lookup"><span data-stu-id="88dc9-109">The basic tasks to perform are, in order:</span></span>  
  
1. <span data-ttu-id="88dc9-110">Definujte kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="88dc9-110">Define the service contract.</span></span> <span data-ttu-id="88dc9-111">Kontrakt služby určuje podpis služby, data, která vyměňuje, a další smluvní požadovaná data.</span><span class="sxs-lookup"><span data-stu-id="88dc9-111">A service contract specifies the signature of a service, the data it exchanges, and other contractually required data.</span></span> <span data-ttu-id="88dc9-112">Další informace najdete v tématu [Navrhování kontraktů služby](designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="88dc9-112">For more information, see [Designing Service Contracts](designing-service-contracts.md).</span></span>  
  
2. <span data-ttu-id="88dc9-113">Implementujte kontrakt.</span><span class="sxs-lookup"><span data-stu-id="88dc9-113">Implement the contract.</span></span> <span data-ttu-id="88dc9-114">Chcete-li implementovat kontrakt služby, vytvořte třídu, která implementuje kontrakt a určete vlastní chování, které má modul runtime mít.</span><span class="sxs-lookup"><span data-stu-id="88dc9-114">To implement a service contract, create a class that implements the contract and specify custom behaviors that the runtime should have.</span></span> <span data-ttu-id="88dc9-115">Další informace najdete v tématu [implementace kontraktů služeb](implementing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="88dc9-115">For more information, see [Implementing Service Contracts](implementing-service-contracts.md).</span></span>  
  
3. <span data-ttu-id="88dc9-116">Nakonfigurujte službu zadáním koncových bodů a dalších informací o chování.</span><span class="sxs-lookup"><span data-stu-id="88dc9-116">Configure the service by specifying endpoints and other behavior information.</span></span> <span data-ttu-id="88dc9-117">Další informace najdete v tématu [Konfigurace služeb](configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="88dc9-117">For more information, see [Configuring Services](configuring-services.md).</span></span>  
  
4. <span data-ttu-id="88dc9-118">Hostování služby.</span><span class="sxs-lookup"><span data-stu-id="88dc9-118">Host the service.</span></span> <span data-ttu-id="88dc9-119">Další informace najdete v tématu [hostující služby](hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="88dc9-119">For more information, see [Hosting Services](hosting-services.md).</span></span>  
  
5. <span data-ttu-id="88dc9-120">Sestavte klientskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="88dc9-120">Build a client application.</span></span> <span data-ttu-id="88dc9-121">Další informace najdete v tématu [sestavování klientů](building-clients.md).</span><span class="sxs-lookup"><span data-stu-id="88dc9-121">For more information, see [Building Clients](building-clients.md).</span></span>  
  
 <span data-ttu-id="88dc9-122">I když se témata v této části řídí tímto pořadím, některé scénáře se na začátku nespustí.</span><span class="sxs-lookup"><span data-stu-id="88dc9-122">Although the topics in this section follow this order, some scenarios do not start at the beginning.</span></span> <span data-ttu-id="88dc9-123">Pokud například chcete vytvořit klienta pro existující službu, začněte v kroku 5.</span><span class="sxs-lookup"><span data-stu-id="88dc9-123">For example, if you want to build a client for a pre-existing service, you start at step 5.</span></span> <span data-ttu-id="88dc9-124">Nebo pokud vytváříte službu, kterou budou používat jiní uživatelé, můžete přeskočit krok 5.</span><span class="sxs-lookup"><span data-stu-id="88dc9-124">Or if you are building a service that others will use, you may skip step 5.</span></span>  
  
 <span data-ttu-id="88dc9-125">Jakmile se seznámíte s vývojem kontraktů služby, můžete si také přečíst [Úvod k rozšíření](introduction-to-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="88dc9-125">Once you are familiar with developing service contracts, you can also read [Introduction to Extensibility](introduction-to-extensibility.md).</span></span> <span data-ttu-id="88dc9-126">Pokud máte ve své službě problémy, podívejte se na [rychlý Start pro řešení potíží WCF](wcf-troubleshooting-quickstart.md) a podívejte se, jestli mají ostatní stejné nebo podobné problémy.</span><span class="sxs-lookup"><span data-stu-id="88dc9-126">If you have problems with your service, check [WCF Troubleshooting Quickstart](wcf-troubleshooting-quickstart.md) to see whether others have the same or similar problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88dc9-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="88dc9-127">See also</span></span>

- [<span data-ttu-id="88dc9-128">Implementace kontraktů služeb</span><span class="sxs-lookup"><span data-stu-id="88dc9-128">Implementing Service Contracts</span></span>](implementing-service-contracts.md)
