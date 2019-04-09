---
title: Implementace proxy zjišťování
ms.date: 03/30/2017
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
ms.openlocfilehash: 5d9296d8ba70d4c9e8d8339fa3a032d9c4c62826
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140996"
---
# <a name="implementing-a-discovery-proxy"></a><span data-ttu-id="27094-102">Implementace proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="27094-102">Implementing a Discovery Proxy</span></span>
<span data-ttu-id="27094-103">Tato část popisuje kroky potřebné k implementace zjišťování proxy.</span><span class="sxs-lookup"><span data-stu-id="27094-103">This section describes the steps required to implement a discovery proxy.</span></span> <span data-ttu-id="27094-104">Zjišťování proxy je samostatná služba, která obsahuje úložiště služby.</span><span class="sxs-lookup"><span data-stu-id="27094-104">A discovery proxy is a standalone service that contains a repository of services.</span></span> <span data-ttu-id="27094-105">Klienti mohou odesílat dotazy na zjišťování proxy k vyhledání zjistitelné služby, které si je vědoma proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="27094-105">Clients can query a discovery proxy to find discoverable services that the proxy is aware of.</span></span> <span data-ttu-id="27094-106">Jak se proxy server služby vyplní záleží implementátora.</span><span class="sxs-lookup"><span data-stu-id="27094-106">How a proxy is populated with services is up to the implementer.</span></span> <span data-ttu-id="27094-107">Například můžete proxy zjišťování připojit k existující služby úložiště a zjistitelnost těchto informací, Správce může pomocí rozhraní API pro správu přidejte zjistitelné služby pro proxy server nebo proxy zjišťování můžete použít funkce oznámení pro Aktualizujte vnitřní mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="27094-107">For example, a discovery proxy can connect to an existing service repository and make that information discoverable, an administrator can use a management API to add discoverable services to a proxy, or a discovery proxy can use the announcement functionality to update its internal cache.</span></span>  
  
 <span data-ttu-id="27094-108">Implementace WCF poskytuje základní třídy, které umožňují snadno vytvářet proxy server.</span><span class="sxs-lookup"><span data-stu-id="27094-108">The WCF implementation provides base classes that allow you to easily build a proxy.</span></span> <span data-ttu-id="27094-109">Můžete využívat tato rozhraní API k vytvoření zjišťování proxy serveru na svém stávajícím úložišti.</span><span class="sxs-lookup"><span data-stu-id="27094-109">You can utilize these APIs to build a Discovery Proxy on top of your existing repository.</span></span>  
  
 <span data-ttu-id="27094-110">Zde implementováno proxy zjišťování je stejně jako jiné služby WCF můžete také zjistitelnost proxy zjišťování a klientům vyhledat své koncové body.</span><span class="sxs-lookup"><span data-stu-id="27094-110">The discovery proxy implemented here is like any other WCF services, in that you can also make the discovery proxy discoverable and have the clients locate its endpoints.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="27094-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="27094-111">In This Section</span></span>  
 [<span data-ttu-id="27094-112">Postupy: Implementace zjišťování proxy</span><span class="sxs-lookup"><span data-stu-id="27094-112">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 <span data-ttu-id="27094-113">Popisuje způsob implementace zjišťování proxy.</span><span class="sxs-lookup"><span data-stu-id="27094-113">Describes how to implement a discovery proxy.</span></span>  
  
 [<span data-ttu-id="27094-114">Postupy: Implementace zjistitelné služby, která se registruje pomocí proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="27094-114">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 <span data-ttu-id="27094-115">Popisuje způsob implementace zjistitelné služby WCF, která se registruje pomocí proxy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="27094-115">Describes how to implement a discoverable WCF service that registers with the discovery proxy.</span></span>  
  
 [<span data-ttu-id="27094-116">Postupy: Implementace klientské aplikace používající zjišťování proxy k vyhledání služby</span><span class="sxs-lookup"><span data-stu-id="27094-116">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)  
 <span data-ttu-id="27094-117">Popisuje způsob implementace WCF klientské aplikace používající zjišťování proxy k vyhledání pro službu.</span><span class="sxs-lookup"><span data-stu-id="27094-117">Describes how to implement a WCF client application that uses the discovery proxy to search for a service.</span></span>  
  
 [<span data-ttu-id="27094-118">Postupy: Test proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="27094-118">How to: Test the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)  
 <span data-ttu-id="27094-119">Popisuje, jak testovat kód napsaný v předchozí tři témata.</span><span class="sxs-lookup"><span data-stu-id="27094-119">Describes how to test the code written in the previous three topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27094-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="27094-120">See also</span></span>

- [<span data-ttu-id="27094-121">Zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="27094-121">WCF Discovery</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)
- [<span data-ttu-id="27094-122">Postupy: Programové přidání možností rozpoznání do klienta a služby WCF</span><span class="sxs-lookup"><span data-stu-id="27094-122">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
