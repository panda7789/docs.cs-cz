---
title: "Řízení výkonu služby WCF pomocí třídy ServiceThrottlingBehavior"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: behavior [WCF], service performance
ms.assetid: f9dc120c-dc24-49d5-930e-b22f5bc73423
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2b7e00e70bab0c5652bbc721d582a1b276e6a3fa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-servicethrottlingbehavior-to-control-wcf-service-performance"></a><span data-ttu-id="76155-102">Řízení výkonu služby WCF pomocí třídy ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="76155-102">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>
<span data-ttu-id="76155-103"><xref:System.ServiceModel.Description.ServiceThrottlingBehavior> Třída zpřístupní vlastnosti, které můžete použít k omezení, kolik instancí nebo relací jsou vytvořené na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="76155-103">The <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> class exposes properties that you can use to limit how many instances or sessions are created at the application level.</span></span> <span data-ttu-id="76155-104">Pomocí tohoto chování, lze optimalizovat výkon vaší [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="76155-104">Using this behavior, you can fine-tune the performance of your [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application.</span></span>  
  
## <a name="controlling-service-instances-and-concurrent-calls"></a><span data-ttu-id="76155-105">Řízení instance služby a souběžných volání</span><span class="sxs-lookup"><span data-stu-id="76155-105">Controlling Service Instances and Concurrent Calls</span></span>  
 <span data-ttu-id="76155-106">Použití <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> vlastnosti a určit maximální počet zpráv aktivně zpracovávají napříč <xref:System.ServiceModel.ServiceHost> třída a <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> vlastnosti a určit maximální počet <xref:System.ServiceModel.InstanceContext> objekty ve službě.</span><span class="sxs-lookup"><span data-stu-id="76155-106">Use the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> property to specify the maximum number of messages actively processing across a <xref:System.ServiceModel.ServiceHost> class, and the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> property to specify the maximum number of <xref:System.ServiceModel.InstanceContext> objects in the service.</span></span>  
  
 <span data-ttu-id="76155-107">Protože určení nastavení pro tyto vlastnosti obvykle probíhá po spuštění aplikace proti praktických zkušeností načte, nastavení <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> vlastnosti se obvykle zadává v souboru konfigurace aplikace pomocí [ \<serviceThrottling >](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md) element.</span><span class="sxs-lookup"><span data-stu-id="76155-107">Because determining the settings for these properties usually takes place after real-world experience running the application against loads, the settings for the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> properties is typically specified in an application configuration file using the [\<serviceThrottling>](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md) element.</span></span>  
  
 <span data-ttu-id="76155-108">Následující příklad kódu ukazuje použití <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> třídy z konfiguračního souboru aplikace, který nastaví <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A>, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, a <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> vlastnosti na hodnotu 1 jako jednoduchý příklad.</span><span class="sxs-lookup"><span data-stu-id="76155-108">The following code example shows the use of the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> class from an application configuration file that sets the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A>, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, and <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> properties to 1 as a trivial example.</span></span> <span data-ttu-id="76155-109">Reálného prostředí určuje optimální nastavení pro všechny konkrétní aplikace.</span><span class="sxs-lookup"><span data-stu-id="76155-109">Real-world experience determines the optimal settings for any particular application.</span></span>  
  
 [!code-xml[ServiceThrottlingBehavior#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/servicethrottlingbehavior/cs/hostapplication.exe.config#3)]  
  
 <span data-ttu-id="76155-110">Přesný běhového chování závisí na hodnoty <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> a <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnosti, které řídí, kolik zpráv můžete provést uvnitř operace najednou a životnosti služby <xref:System.ServiceModel.InstanceContext> relativně k příchozích relací kanálu , v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="76155-110">The exact run-time behavior depends upon the values of the <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> and <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> properties, which control how many messages can execute inside an operation at once and the lifetimes of the service <xref:System.ServiceModel.InstanceContext> relative to incoming channel sessions, respectively.</span></span>  
  
 <span data-ttu-id="76155-111">Podrobnosti najdete v tématu <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, a <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>.</span><span class="sxs-lookup"><span data-stu-id="76155-111">For details, see <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, and <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76155-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="76155-112">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>  
 <xref:System.ServiceModel.NetTcpBinding.MaxConnections%2A>
