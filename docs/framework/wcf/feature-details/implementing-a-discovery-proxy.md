---
title: Implementace proxy zjišťování
ms.date: 03/30/2017
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
ms.openlocfilehash: 0c7086e0eecea6cc2d7494d6afda0abf056ba758
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492216"
---
# <a name="implementing-a-discovery-proxy"></a><span data-ttu-id="f14eb-102">Implementace proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="f14eb-102">Implementing a Discovery Proxy</span></span>
<span data-ttu-id="f14eb-103">Tato část popisuje kroky potřebné k implementace zjišťování proxy.</span><span class="sxs-lookup"><span data-stu-id="f14eb-103">This section describes the steps required to implement a discovery proxy.</span></span> <span data-ttu-id="f14eb-104">Zjišťování proxy je samostatné služby, který obsahuje úložiště služby.</span><span class="sxs-lookup"><span data-stu-id="f14eb-104">A discovery proxy is a standalone service that contains a repository of services.</span></span> <span data-ttu-id="f14eb-105">Klienti mohou odesílat dotazy na zjišťování proxy k vyhledání zjistitelný služby, které má informace o proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="f14eb-105">Clients can query a discovery proxy to find discoverable services that the proxy is aware of.</span></span> <span data-ttu-id="f14eb-106">Jak je proxy server naplněný služby závisí implementátor.</span><span class="sxs-lookup"><span data-stu-id="f14eb-106">How a proxy is populated with services is up to the implementer.</span></span> <span data-ttu-id="f14eb-107">Například zjišťování proxy můžete připojit k existující úložiště služby a zjistitelnost těchto informací, Správce může pomocí rozhraní API pro správu na přidání služeb zjistitelný na proxy server nebo proxy zjišťování můžete použít funkci oznámení na Aktualizujte vnitřní mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="f14eb-107">For example, a discovery proxy can connect to an existing service repository and make that information discoverable, an administrator can use a management API to add discoverable services to a proxy, or a discovery proxy can use the announcement functionality to update its internal cache.</span></span>  
  
 <span data-ttu-id="f14eb-108">Implementace WCF poskytuje základní třídy, které vám umožní snadno vytvářet proxy server.</span><span class="sxs-lookup"><span data-stu-id="f14eb-108">The WCF implementation provides base classes that allow you to easily build a proxy.</span></span> <span data-ttu-id="f14eb-109">Tato rozhraní API k vytvoření zjišťování Proxy na existující úložiště, můžete využít.</span><span class="sxs-lookup"><span data-stu-id="f14eb-109">You can utilize these APIs to build a Discovery Proxy on top of your existing repository.</span></span>  
  
 <span data-ttu-id="f14eb-110">Zjišťování proxy zde implementováno je jako ostatní služby WCF, můžete také zjistitelnost zjišťování proxy a klienti najít své koncové body.</span><span class="sxs-lookup"><span data-stu-id="f14eb-110">The discovery proxy implemented here is like any other WCF services, in that you can also make the discovery proxy discoverable and have the clients locate its endpoints.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f14eb-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f14eb-111">In This Section</span></span>  
 [<span data-ttu-id="f14eb-112">Postupy: Implementace proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="f14eb-112">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 <span data-ttu-id="f14eb-113">Popisuje způsob implementace zjišťování proxy.</span><span class="sxs-lookup"><span data-stu-id="f14eb-113">Describes how to implement a discovery proxy.</span></span>  
  
 [<span data-ttu-id="f14eb-114">Postupy: Implementace zjistitelné služby, která se registruje pomocí proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="f14eb-114">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 <span data-ttu-id="f14eb-115">Popisuje, jak implementovat zjistitelný služby WCF, který se zaregistruje zjišťování proxy.</span><span class="sxs-lookup"><span data-stu-id="f14eb-115">Describes how to implement a discoverable WCF service that registers with the discovery proxy.</span></span>  
  
 [<span data-ttu-id="f14eb-116">Postupy: Implementace klientské aplikace používající proxy zjišťování k vyhledání služby</span><span class="sxs-lookup"><span data-stu-id="f14eb-116">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)  
 <span data-ttu-id="f14eb-117">Popisuje způsob implementace WCF klientské aplikace používající zjišťování proxy k vyhledání pro službu.</span><span class="sxs-lookup"><span data-stu-id="f14eb-117">Describes how to implement a WCF client application that uses the discovery proxy to search for a service.</span></span>  
  
 [<span data-ttu-id="f14eb-118">Postupy: Test proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="f14eb-118">How to: Test the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)  
 <span data-ttu-id="f14eb-119">Popisuje, jak otestovat kód napsaný v předchozí tři témata.</span><span class="sxs-lookup"><span data-stu-id="f14eb-119">Describes how to test the code written in the previous three topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f14eb-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="f14eb-120">See Also</span></span>  
 [<span data-ttu-id="f14eb-121">Zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="f14eb-121">WCF Discovery</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
 [<span data-ttu-id="f14eb-122">Postupy: Programové přidání zjistitelnosti do klienta a služby WCF</span><span class="sxs-lookup"><span data-stu-id="f14eb-122">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
