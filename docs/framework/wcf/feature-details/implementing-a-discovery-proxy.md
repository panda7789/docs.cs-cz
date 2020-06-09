---
title: Implementace proxy zjišťování
ms.date: 03/30/2017
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
ms.openlocfilehash: 382df95fef2108d338e4ea327da9185c856eca5a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579238"
---
# <a name="implementing-a-discovery-proxy"></a><span data-ttu-id="1cdd6-102">Implementace proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="1cdd6-102">Implementing a Discovery Proxy</span></span>
<span data-ttu-id="1cdd6-103">Tato část popisuje kroky potřebné k implementaci proxy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="1cdd6-103">This section describes the steps required to implement a discovery proxy.</span></span> <span data-ttu-id="1cdd6-104">Proxy zjišťování je samostatná služba, která obsahuje úložiště služeb.</span><span class="sxs-lookup"><span data-stu-id="1cdd6-104">A discovery proxy is a standalone service that contains a repository of services.</span></span> <span data-ttu-id="1cdd6-105">Klienti mohou zadat dotaz na proxy zjišťování a vyhledat tak zjistitelné služby, na kterých je daný proxy vědět.</span><span class="sxs-lookup"><span data-stu-id="1cdd6-105">Clients can query a discovery proxy to find discoverable services that the proxy is aware of.</span></span> <span data-ttu-id="1cdd6-106">Způsob naplnění proxy služeb službami je až implementátor.</span><span class="sxs-lookup"><span data-stu-id="1cdd6-106">How a proxy is populated with services is up to the implementer.</span></span> <span data-ttu-id="1cdd6-107">Například proxy zjišťování se může připojit k existujícímu úložišti služeb a učinit tyto informace zjistitelným správcem může pomocí rozhraní API pro správu přidat zjistitelné služby na proxy server nebo proxy zjišťování může pomocí funkce oznámení aktualizovat svou interní mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="1cdd6-107">For example, a discovery proxy can connect to an existing service repository and make that information discoverable, an administrator can use a management API to add discoverable services to a proxy, or a discovery proxy can use the announcement functionality to update its internal cache.</span></span>  
  
 <span data-ttu-id="1cdd6-108">Implementace WCF poskytuje základní třídy, které umožňují snadno vytvořit proxy server.</span><span class="sxs-lookup"><span data-stu-id="1cdd6-108">The WCF implementation provides base classes that allow you to easily build a proxy.</span></span> <span data-ttu-id="1cdd6-109">Tato rozhraní API můžete využít k vytvoření proxy serveru zjišťování nad stávajícím úložištěm.</span><span class="sxs-lookup"><span data-stu-id="1cdd6-109">You can utilize these APIs to build a Discovery Proxy on top of your existing repository.</span></span>  
  
 <span data-ttu-id="1cdd6-110">Proxy zjišťování implementované tady je stejně jako jakékoli jiné služby WCF. v takovém případě můžete také nastavit, aby byl proxy zjišťování zjistitelný a aby klienti našli své koncové body.</span><span class="sxs-lookup"><span data-stu-id="1cdd6-110">The discovery proxy implemented here is like any other WCF services, in that you can also make the discovery proxy discoverable and have the clients locate its endpoints.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1cdd6-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="1cdd6-111">In This Section</span></span>  
 [<span data-ttu-id="1cdd6-112">Postupy: Implementace zjišťování proxy</span><span class="sxs-lookup"><span data-stu-id="1cdd6-112">How to: Implement a Discovery Proxy</span></span>](how-to-implement-a-discovery-proxy.md)  
 <span data-ttu-id="1cdd6-113">Popisuje, jak implementovat proxy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="1cdd6-113">Describes how to implement a discovery proxy.</span></span>  
  
 [<span data-ttu-id="1cdd6-114">Postupy: Implementace zjistitelné služby, která se registruje pomocí proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="1cdd6-114">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](discoverable-service-that-registers-with-the-discovery-proxy.md)  
 <span data-ttu-id="1cdd6-115">Popisuje, jak implementovat zjistitelnou službu WCF, která se registruje pomocí proxy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="1cdd6-115">Describes how to implement a discoverable WCF service that registers with the discovery proxy.</span></span>  
  
 [<span data-ttu-id="1cdd6-116">Postupy: Implementace klientské aplikace používající proxy zjišťování k vyhledání služby</span><span class="sxs-lookup"><span data-stu-id="1cdd6-116">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](client-app-discovery-proxy-to-find-a-service.md)  
 <span data-ttu-id="1cdd6-117">Popisuje implementaci klientské aplikace WCF, která používá proxy zjišťování k hledání služby.</span><span class="sxs-lookup"><span data-stu-id="1cdd6-117">Describes how to implement a WCF client application that uses the discovery proxy to search for a service.</span></span>  
  
 [<span data-ttu-id="1cdd6-118">Postupy: Test proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="1cdd6-118">How to: Test the Discovery Proxy</span></span>](how-to-test-the-discovery-proxy.md)  
 <span data-ttu-id="1cdd6-119">Popisuje, jak otestovat kód napsaný v předchozích třech tématech.</span><span class="sxs-lookup"><span data-stu-id="1cdd6-119">Describes how to test the code written in the previous three topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cdd6-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="1cdd6-120">See also</span></span>

- [<span data-ttu-id="1cdd6-121">Zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="1cdd6-121">WCF Discovery</span></span>](wcf-discovery.md)
- [<span data-ttu-id="1cdd6-122">Postupy: Programové přidání zjistitelnosti do klienta a služby WCF</span><span class="sxs-lookup"><span data-stu-id="1cdd6-122">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
