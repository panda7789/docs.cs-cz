---
title: 'Postupy: Řízení vytváření instancí služby'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e0b12b34-8004-443a-a46d-83a5c00f2601
ms.openlocfilehash: 8a73dd90d268c61e0df974861753119e205a870f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599071"
---
# <a name="how-to-control-service-instancing"></a><span data-ttu-id="f65d4-102">Postupy: Řízení vytváření instancí služby</span><span class="sxs-lookup"><span data-stu-id="f65d4-102">How to: Control Service Instancing</span></span>
<span data-ttu-id="f65d4-103">Nastavení režimu instance služby vám umožní určit, kdy <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> se vytvoří (a přidružený objekt služby definované uživatelem).</span><span class="sxs-lookup"><span data-stu-id="f65d4-103">Setting the instance mode of a service enables you to specify when a <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (and its associated user-defined service object) is created.</span></span> <span data-ttu-id="f65d4-104">Podívejte se na <xref:System.ServiceModel.InstanceContextMode> výčet možných režimů.</span><span class="sxs-lookup"><span data-stu-id="f65d4-104">See the <xref:System.ServiceModel.InstanceContextMode> enumeration for the possible modes.</span></span> <span data-ttu-id="f65d4-105">Další informace o chování najdete v tématu [Konfigurace a rozšíření modulu runtime s chováním](../extending/configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="f65d4-105">For more information about behaviors, see [Configuring and Extending the Runtime with Behaviors](../extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span> <span data-ttu-id="f65d4-106">Pracovní příklady najdete v tématu [chování](../samples/behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="f65d4-106">For working examples, see [Behaviors](../samples/behaviors.md).</span></span>  
  
### <a name="to-control-the-service-instance-lifetime-using-code"></a><span data-ttu-id="f65d4-107">Řízení životnosti instance služby pomocí kódu</span><span class="sxs-lookup"><span data-stu-id="f65d4-107">To control the service instance lifetime using code</span></span>  
  
1. <span data-ttu-id="f65d4-108">Použijte <xref:System.ServiceModel.ServiceBehaviorAttribute> pro třídu služby.</span><span class="sxs-lookup"><span data-stu-id="f65d4-108">Apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> to the service class.</span></span>  
  
2. <span data-ttu-id="f65d4-109">Nastavte <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnost na jednu z následujících hodnot: <xref:System.ServiceModel.InstanceContextMode.PerCall> , <xref:System.ServiceModel.InstanceContextMode.PerSession> , nebo <xref:System.ServiceModel.InstanceContextMode.Single> .</span><span class="sxs-lookup"><span data-stu-id="f65d4-109">Set the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property to one of the following values: <xref:System.ServiceModel.InstanceContextMode.PerCall>, <xref:System.ServiceModel.InstanceContextMode.PerSession>, or <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span>  
  
     [!code-csharp[C_ControlServiceInstancing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#1)]
     [!code-vb[C_ControlServiceInstancing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="f65d4-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="f65d4-110">Example</span></span>  
 <span data-ttu-id="f65d4-111">Následující příklad kódu nastaví <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnost <xref:System.ServiceModel.ServiceBehaviorAttribute> atributu na <xref:System.ServiceModel.InstanceContextMode.PerCall> .</span><span class="sxs-lookup"><span data-stu-id="f65d4-111">The following code example sets the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property of the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to <xref:System.ServiceModel.InstanceContextMode.PerCall>.</span></span>  
  
 [!code-csharp[c_ControlServiceInstancing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#2)]
 [!code-vb[c_ControlServiceInstancing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f65d4-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="f65d4-112">See also</span></span>

- <xref:System.ServiceModel.ServiceBehaviorAttribute>
- <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>
- <xref:System.ServiceModel.InstanceContextMode>
- [<span data-ttu-id="f65d4-113">Služba: ukázky chování</span><span class="sxs-lookup"><span data-stu-id="f65d4-113">Service: Behaviors Samples</span></span>](../samples/behaviors.md)
