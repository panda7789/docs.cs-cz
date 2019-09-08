---
title: 'Postupy: Kontrola a změny zpráv ve službě'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9c5b1cc7-84f3-45f8-9226-d59c278e8c42
ms.openlocfilehash: 1356983361c483170d9d7365932b788f2421bf09
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795598"
---
# <a name="how-to-inspect-and-modify-messages-on-the-service"></a><span data-ttu-id="ca825-102">Postupy: Kontrola a změny zpráv ve službě</span><span class="sxs-lookup"><span data-stu-id="ca825-102">How to: Inspect and Modify Messages on the Service</span></span>
<span data-ttu-id="ca825-103">Příchozí nebo odchozí zprávy můžete kontrolovat nebo upravovat v rámci klienta Windows Communication Foundation (WCF) implementací <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> a vložením do modulu runtime služby.</span><span class="sxs-lookup"><span data-stu-id="ca825-103">You can inspect or modify the incoming or outgoing messages across a Windows Communication Foundation (WCF) client by implementing a <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> and inserting it into the service runtime.</span></span> <span data-ttu-id="ca825-104">Další informace najdete v tématu [rozšíření expedičních](extending-dispatchers.md).</span><span class="sxs-lookup"><span data-stu-id="ca825-104">For more information, see [Extending Dispatchers](extending-dispatchers.md).</span></span> <span data-ttu-id="ca825-105">Ekvivalentní funkce služby je <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ca825-105">The equivalent feature on the service is the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-inspect-or-modify-messages"></a><span data-ttu-id="ca825-106">Kontrola nebo změna zpráv</span><span class="sxs-lookup"><span data-stu-id="ca825-106">To inspect or modify messages</span></span>  
  
1. <span data-ttu-id="ca825-107">Implementujte rozhraní <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ca825-107">Implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="ca825-108">Implementujte rozhraní <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> , nebo, v závislosti na rozsahu, ve kterém chcete snadno vložit kontrolu zpráv služby. <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ca825-108">Implement a <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> interface depending upon the scope at which you want to easily insert your service message inspector.</span></span>  
  
3. <span data-ttu-id="ca825-109">Před voláním <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> metody na, <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>vložte své chování.</span><span class="sxs-lookup"><span data-stu-id="ca825-109">Insert your behavior prior to calling the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ca825-110">Podrobnosti najdete v tématu [Konfigurace a rozšíření modulu runtime s chováním](configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="ca825-110">For details, see [Configuring and Extending the Runtime with Behaviors](configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca825-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="ca825-111">Example</span></span>  
 <span data-ttu-id="ca825-112">Následující příklady kódu ukazují, v pořadí:</span><span class="sxs-lookup"><span data-stu-id="ca825-112">The following code examples show, in order:</span></span>  
  
- <span data-ttu-id="ca825-113">Implementace v rámci kontroly služby.</span><span class="sxs-lookup"><span data-stu-id="ca825-113">A service inspector implementation.</span></span>  
  
- <span data-ttu-id="ca825-114">Chování služby, které vkládá kontroler.</span><span class="sxs-lookup"><span data-stu-id="ca825-114">A service behavior that inserts the inspector.</span></span>  
  
- <span data-ttu-id="ca825-115">Konfigurační soubor, který načte a spustí chování aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="ca825-115">A configuration file that loads and runs the behavior in a service application.</span></span>  
  
 [!code-csharp[Interceptors#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#7)]
 [!code-vb[Interceptors#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#7)]  
  
 [!code-csharp[Interceptors#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#8)]
 [!code-vb[Interceptors#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#8)]  
  
 [!code-xml[Interceptors#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/hostapplication.exe.config#9)]  
  
## <a name="see-also"></a><span data-ttu-id="ca825-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ca825-116">See also</span></span>

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [<span data-ttu-id="ca825-117">Konfigurace a rozšíření modulu runtime pomocí chování</span><span class="sxs-lookup"><span data-stu-id="ca825-117">Configuring and Extending the Runtime with Behaviors</span></span>](configuring-and-extending-the-runtime-with-behaviors.md)
