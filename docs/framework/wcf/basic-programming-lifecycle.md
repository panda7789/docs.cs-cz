---
title: Základní programovací životní cyklus
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
caps.latest.revision: 36
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ff735a8caf1fbaff636f94eee366b20c33d8f331
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="basic-programming-lifecycle"></a><span data-ttu-id="7a568-102">Základní programovací životní cyklus</span><span class="sxs-lookup"><span data-stu-id="7a568-102">Basic Programming Lifecycle</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="7a568-103"> umožňuje aplikacím komunikovat, zda jsou na stejném počítači, v Internetu, nebo na jinou aplikaci platformy.</span><span class="sxs-lookup"><span data-stu-id="7a568-103"> enables applications to communicate whether they are on the same computer, across the Internet, or on different application platforms.</span></span> <span data-ttu-id="7a568-104">Toto téma popisuje úkoly, které jsou nutné k vytvoření [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="7a568-104">This topic outlines the tasks that are required to build a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] application.</span></span> <span data-ttu-id="7a568-105">Ukázkovou aplikaci, práce, najdete v části [kurzu Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="7a568-105">For a working sample application, see [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>  
  
## <a name="the-basic-tasks"></a><span data-ttu-id="7a568-106">Základní úlohy</span><span class="sxs-lookup"><span data-stu-id="7a568-106">The Basic Tasks</span></span>  
 <span data-ttu-id="7a568-107">Základní úlohy musíte provést, jsou v pořadí:</span><span class="sxs-lookup"><span data-stu-id="7a568-107">The basic tasks to perform are, in order:</span></span>  
  
1.  <span data-ttu-id="7a568-108">Definování kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="7a568-108">Define the service contract.</span></span> <span data-ttu-id="7a568-109">Kontrakt služby Určuje podpis služby, data, která k výměně a další smluvně požadovaná data.</span><span class="sxs-lookup"><span data-stu-id="7a568-109">A service contract specifies the signature of a service, the data it exchanges, and other contractually required data.</span></span> <span data-ttu-id="7a568-110">Další informace najdete v tématu [navrhování kontraktů služby](../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="7a568-110">For more information, see [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
2.  <span data-ttu-id="7a568-111">Implementujte kontrakt.</span><span class="sxs-lookup"><span data-stu-id="7a568-111">Implement the contract.</span></span> <span data-ttu-id="7a568-112">K implementaci kontraktu služby, vytvořte třídu, která implementuje kontrakt a zadejte vlastní chování, které by měly mít modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="7a568-112">To implement a service contract, create a class that implements the contract and specify custom behaviors that the runtime should have.</span></span> <span data-ttu-id="7a568-113">Další informace najdete v tématu [implementace kontraktů služby](../../../docs/framework/wcf/implementing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="7a568-113">For more information, see [Implementing Service Contracts](../../../docs/framework/wcf/implementing-service-contracts.md).</span></span>  
  
3.  <span data-ttu-id="7a568-114">Konfigurovat službu zadáním koncových bodů a další informace o chování.</span><span class="sxs-lookup"><span data-stu-id="7a568-114">Configure the service by specifying endpoints and other behavior information.</span></span> <span data-ttu-id="7a568-115">Další informace najdete v tématu [konfigurace služby](../../../docs/framework/wcf/configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="7a568-115">For more information, see [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>  
  
4.  <span data-ttu-id="7a568-116">Hostitel služby.</span><span class="sxs-lookup"><span data-stu-id="7a568-116">Host the service.</span></span> <span data-ttu-id="7a568-117">Další informace najdete v tématu [hostování služeb](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="7a568-117">For more information, see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
5.  <span data-ttu-id="7a568-118">Vytvořit klientskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7a568-118">Build a client application.</span></span> <span data-ttu-id="7a568-119">Další informace najdete v tématu [sestavování klientů](../../../docs/framework/wcf/building-clients.md).</span><span class="sxs-lookup"><span data-stu-id="7a568-119">For more information, see [Building Clients](../../../docs/framework/wcf/building-clients.md).</span></span>  
  
 <span data-ttu-id="7a568-120">I když témata v této části použijte toto pořadí, některé scénáře nespouštějte na začátku.</span><span class="sxs-lookup"><span data-stu-id="7a568-120">Although the topics in this section follow this order, some scenarios do not start at the beginning.</span></span> <span data-ttu-id="7a568-121">Například pokud chcete k vytvoření klienta pro existující službu, můžete spustit v kroku 5.</span><span class="sxs-lookup"><span data-stu-id="7a568-121">For example, if you want to build a client for a pre-existing service, you start at step 5.</span></span> <span data-ttu-id="7a568-122">Nebo pokud vytváříte službu, která budou používat ostatní, může přeskočit krok 5.</span><span class="sxs-lookup"><span data-stu-id="7a568-122">Or if you are building a service that others will use, you may skip step 5.</span></span>  
  
 <span data-ttu-id="7a568-123">Jakmile jste obeznámeni s vývojem kontraktů služby, můžete si také přečíst [Úvod do rozšíření](../../../docs/framework/wcf/introduction-to-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="7a568-123">Once you are familiar with developing service contracts, you can also read [Introduction to Extensibility](../../../docs/framework/wcf/introduction-to-extensibility.md).</span></span> <span data-ttu-id="7a568-124">Pokud máte problémy s vaší služby, zkontrolujte [rychlý start řešení potíží s WCF](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) zobrazíte, zda ostatní uživatelé mají stejné nebo podobné problémy.</span><span class="sxs-lookup"><span data-stu-id="7a568-124">If you have problems with your service, check [WCF Troubleshooting Quickstart](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) to see whether others have the same or similar problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a568-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a568-125">See Also</span></span>  
 [<span data-ttu-id="7a568-126">Implementace kontraktů služeb</span><span class="sxs-lookup"><span data-stu-id="7a568-126">Implementing Service Contracts</span></span>](../../../docs/framework/wcf/implementing-service-contracts.md)
