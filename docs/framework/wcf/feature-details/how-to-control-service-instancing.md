---
title: "Postupy: vytváření instancí služby Řízení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: e0b12b34-8004-443a-a46d-83a5c00f2601
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 60a2537f1ddc4563c1514032f7df4894f6ef47af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-service-instancing"></a><span data-ttu-id="3b3c9-102">Postupy: vytváření instancí služby Řízení</span><span class="sxs-lookup"><span data-stu-id="3b3c9-102">How to: Control Service Instancing</span></span>
<span data-ttu-id="3b3c9-103">Nastavení režimu instance služby umožňuje určit, kdy <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (a jeho objekt přidružená služba definovaný uživatelem) je vytvořen.</span><span class="sxs-lookup"><span data-stu-id="3b3c9-103">Setting the instance mode of a service enables you to specify when a <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (and its associated user-defined service object) is created.</span></span> <span data-ttu-id="3b3c9-104">Najdete v článku <xref:System.ServiceModel.InstanceContextMode> výčet režimů možné.</span><span class="sxs-lookup"><span data-stu-id="3b3c9-104">See the <xref:System.ServiceModel.InstanceContextMode> enumeration for the possible modes.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="3b3c9-105">najdete v části chování, [konfigurace a rozšíření modulu Runtime s chováním](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="3b3c9-105"> behaviors, see [Configuring and Extending the Runtime with Behaviors](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span> <span data-ttu-id="3b3c9-106">Pracovní příklady najdete v tématu [chování](../../../../docs/framework/wcf/samples/behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="3b3c9-106">For working examples, see [Behaviors](../../../../docs/framework/wcf/samples/behaviors.md).</span></span>  
  
### <a name="to-control-the-service-instance-lifetime-using-code"></a><span data-ttu-id="3b3c9-107">K řízení životního cyklu instance služby pomocí kódu</span><span class="sxs-lookup"><span data-stu-id="3b3c9-107">To control the service instance lifetime using code</span></span>  
  
1.  <span data-ttu-id="3b3c9-108">Použít <xref:System.ServiceModel.ServiceBehaviorAttribute> k třídě služby.</span><span class="sxs-lookup"><span data-stu-id="3b3c9-108">Apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> to the service class.</span></span>  
  
2.  <span data-ttu-id="3b3c9-109">Nastavte <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnost na jednu z následujících hodnot: <xref:System.ServiceModel.InstanceContextMode.PerCall>, <xref:System.ServiceModel.InstanceContextMode.PerSession>, nebo <xref:System.ServiceModel.InstanceContextMode.Single>.</span><span class="sxs-lookup"><span data-stu-id="3b3c9-109">Set the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property to one of the following values: <xref:System.ServiceModel.InstanceContextMode.PerCall>, <xref:System.ServiceModel.InstanceContextMode.PerSession>, or <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span>  
  
     [!code-csharp[C_ControlServiceInstancing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#1)]
     [!code-vb[C_ControlServiceInstancing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="3b3c9-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="3b3c9-110">Example</span></span>  
 <span data-ttu-id="3b3c9-111">Následující příklad kódu nastaví <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnost <xref:System.ServiceModel.ServiceBehaviorAttribute> atribut <xref:System.ServiceModel.InstanceContextMode.PerCall>.</span><span class="sxs-lookup"><span data-stu-id="3b3c9-111">The following code example sets the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property of the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to <xref:System.ServiceModel.InstanceContextMode.PerCall>.</span></span>  
  
 [!code-csharp[c_ControlServiceInstancing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#2)]
 [!code-vb[c_ControlServiceInstancing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="3b3c9-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="3b3c9-112">See Also</span></span>  
 <xref:System.ServiceModel.ServiceBehaviorAttribute>  
 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>  
 <xref:System.ServiceModel.InstanceContextMode>  
 [<span data-ttu-id="3b3c9-113">Služby: Ukázky chování</span><span class="sxs-lookup"><span data-stu-id="3b3c9-113">Service: Behaviors Samples</span></span>](http://msdn.microsoft.com/en-us/4e3c6513-a7ff-4b35-8dcf-b5506c6f39a7)
