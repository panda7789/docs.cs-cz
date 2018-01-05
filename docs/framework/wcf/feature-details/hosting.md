---
title: Hosting2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0820c7e5-0b50-4cde-80e7-74e346513002
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f25f0c9e773bbadd992284adf6c79d77aaa2441c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="hosting"></a><span data-ttu-id="8f318-102">Hostování</span><span class="sxs-lookup"><span data-stu-id="8f318-102">Hosting</span></span>
<span data-ttu-id="8f318-103">Témata v této sekci popisují hostování služeb.</span><span class="sxs-lookup"><span data-stu-id="8f318-103">The topics in the section describe service hosting.</span></span> <span data-ttu-id="8f318-104">Služba může být hostovaný Internetové informační služby (IIS), služba aktivace procesů systému Windows (WAS), Windows Server AppFabric, služby systému Windows, nebo ve spravované aplikaci – tato možnost se často označuje jako *vlastní hostování*.</span><span class="sxs-lookup"><span data-stu-id="8f318-104">A service can be hosted by Internet Information Services (IIS), Windows Process Activation Service (WAS), Windows Server AppFabric, a Windows service, or by a managed application—this option is often referred to as *self hosting*.</span></span>  
  
 <span data-ttu-id="8f318-105">Je důležité si uvědomit, že spuštění služby nebo jakoukoli příponu z ohrožení zabezpečení služby nedůvěryhodné hostitele.</span><span class="sxs-lookup"><span data-stu-id="8f318-105">It is important to note that running a service or any extension from an untrusted host compromises security.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8f318-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="8f318-106">In This Section</span></span>  
 [<span data-ttu-id="8f318-107">Hostování v Internetové informační službě</span><span class="sxs-lookup"><span data-stu-id="8f318-107">Hosting in Internet Information Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 <span data-ttu-id="8f318-108">Popisuje, jak [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služba je hostována v Internetové informační službě nebo [Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=196496).</span><span class="sxs-lookup"><span data-stu-id="8f318-108">Describes how a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service is hosted in Internet Information Services or [Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=196496).</span></span>  
  
 [<span data-ttu-id="8f318-109">Hostování v Aktivační službě procesů systému Windows</span><span class="sxs-lookup"><span data-stu-id="8f318-109">Hosting in Windows Process Activation Service</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)  
 <span data-ttu-id="8f318-110">Popisuje, jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba je hostovaná služba aktivace procesů systému Windows.</span><span class="sxs-lookup"><span data-stu-id="8f318-110">Describes how a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted by Windows Process Activation Service.</span></span>  
  
 [<span data-ttu-id="8f318-111">Hostování v aplikaci služby pro Windows</span><span class="sxs-lookup"><span data-stu-id="8f318-111">Hosting in a Windows Service Application</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-a-windows-service-application.md)  
 <span data-ttu-id="8f318-112">Popisuje, jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba je hostována serverem služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="8f318-112">Describes how a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted by a Windows service.</span></span>  
  
 [<span data-ttu-id="8f318-113">Hostování ve spravované aplikaci</span><span class="sxs-lookup"><span data-stu-id="8f318-113">Hosting in a Managed Application</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)  
 <span data-ttu-id="8f318-114">Popisuje, jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba je hostována ve spravované aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8f318-114">Describes how a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted in a managed application.</span></span>  
  
 [<span data-ttu-id="8f318-115">Aktivace založená na konfiguraci v IIS a WAS</span><span class="sxs-lookup"><span data-stu-id="8f318-115">Configuration-Based Activation in IIS and WAS</span></span>](../../../../docs/framework/wcf/feature-details/configuration-based-activation-in-iis-and-was.md)  
 <span data-ttu-id="8f318-116">Popisuje, jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba je hostována v rámci služby IIS nebo WAS bez použití souboru .svc.</span><span class="sxs-lookup"><span data-stu-id="8f318-116">Describes how a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted under IIS or WAS without using a .svc file.</span></span>  
  
 [<span data-ttu-id="8f318-117">Podpora více vazeb webu IIS</span><span class="sxs-lookup"><span data-stu-id="8f318-117">Supporting Multiple IIS Site Bindings</span></span>](../../../../docs/framework/wcf/feature-details/supporting-multiple-iis-site-bindings.md)  
 <span data-ttu-id="8f318-118">Popisuje, jak lze zadat více základní adresy pro službu pomocí stejné schéma identifikátoru URI na jednom webu.</span><span class="sxs-lookup"><span data-stu-id="8f318-118">Describes how to specify multiple base addresses for a service using the same URI scheme on a single Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f318-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="8f318-119">See Also</span></span>  
 [<span data-ttu-id="8f318-120">Služby hostování</span><span class="sxs-lookup"><span data-stu-id="8f318-120">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)  
 [<span data-ttu-id="8f318-121">Hostování funkcí systému Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="8f318-121">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
