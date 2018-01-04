---
title: "Postupy: Kontrola nebo úprava parametrů"
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
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5f1a0ef31ba074082e4c3aa8a26e6a59502a7566
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-inspect-or-modify-parameters"></a><span data-ttu-id="8267e-102">Postupy: Kontrola nebo úprava parametrů</span><span class="sxs-lookup"><span data-stu-id="8267e-102">How to: Inspect or Modify Parameters</span></span>
<span data-ttu-id="8267e-103">Můžete zkontrolovat nebo upravit příchozích nebo odchozích zpráv pro jednu operaci na [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] objekt klienta nebo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby implementací <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> rozhraní a jejich vložení do klienta služby Windows nebo modul runtime.</span><span class="sxs-lookup"><span data-stu-id="8267e-103">You can inspect or modify the incoming or outgoing messages for a single operation on a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client object or a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service by implementing the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface and inserting it into the client or service runtime.</span></span> <span data-ttu-id="8267e-104">Obvykle se používá operaci chování k přidání inspektoři parametr pro jednu operaci; jiného chování slouží k poskytování snadného přístupu pro modul runtime na větší rozsah.</span><span class="sxs-lookup"><span data-stu-id="8267e-104">Typically an operation behavior is used to add parameter inspectors for a single operation; other behaviors can be used to provide easy access to the runtime at a greater scope.</span></span> <span data-ttu-id="8267e-105">Další informace najdete v tématu [rozšíření klienti](../../../../docs/framework/wcf/extending/extending-clients.md) a [rozšíření dispečerů](../../../../docs/framework/wcf/extending/extending-dispatchers.md).</span><span class="sxs-lookup"><span data-stu-id="8267e-105">For more information, see [Extending Clients](../../../../docs/framework/wcf/extending/extending-clients.md) and [Extending Dispatchers](../../../../docs/framework/wcf/extending/extending-dispatchers.md).</span></span>  
  
### <a name="inspecting-or-modifying-parameters"></a><span data-ttu-id="8267e-106">Probíhá kontrola nebo úprava parametrů</span><span class="sxs-lookup"><span data-stu-id="8267e-106">Inspecting or Modifying Parameters</span></span>  
  
1.  <span data-ttu-id="8267e-107">Implementace <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8267e-107">Implement the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface.</span></span>  
  
2.  <span data-ttu-id="8267e-108">Implementace <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (v závislosti na požadované oboru) přidat vaše parametr inspector buď <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8267e-108">Implement a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (depending upon the required scope) to add your parameter inspector to either the <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> or <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> properties.</span></span>  
  
3.  <span data-ttu-id="8267e-109">Vložit chování vaší před voláním <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> nebo <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> metodu <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8267e-109">Insert your behavior prior to calling <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8267e-110">Podrobnosti najdete v tématu [konfigurace a rozšíření modulu Runtime s chováním](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="8267e-110">For details, see [Configuring and Extending the Runtime with Behaviors](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8267e-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="8267e-111">Example</span></span>  
 <span data-ttu-id="8267e-112">Následující příklady kódu zobrazit v pořadí:</span><span class="sxs-lookup"><span data-stu-id="8267e-112">The following code examples show, in order:</span></span>  
  
-   <span data-ttu-id="8267e-113">Implementace parametr inspector.</span><span class="sxs-lookup"><span data-stu-id="8267e-113">A parameter inspector implementation.</span></span>  
  
-   <span data-ttu-id="8267e-114">Implementace chování, která vloží inspector parametr pomocí <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>a <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8267e-114">The behavior implementation that inserts the parameter inspector using a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, and an <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="8267e-115">Konfigurační soubor, který načte a spustí chování koncového bodu v aplikaci klienta k vložení parametru inspector na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="8267e-115">A configuration file that loads and runs the endpoint behavior in a client application to insert the parameter inspector on the client.</span></span>  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code-xml[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  
  
## <a name="see-also"></a><span data-ttu-id="8267e-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="8267e-116">See Also</span></span>  
 [<span data-ttu-id="8267e-117">Konfigurace a rozšíření modulu runtime pomocí chování</span><span class="sxs-lookup"><span data-stu-id="8267e-117">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
