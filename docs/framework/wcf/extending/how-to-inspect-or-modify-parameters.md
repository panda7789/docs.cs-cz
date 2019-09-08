---
title: 'Postupy: Kontrola nebo úprava parametrů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
ms.openlocfilehash: b4a673f97f06e8d489d9acc85d84e1ecea4656e4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795595"
---
# <a name="how-to-inspect-or-modify-parameters"></a><span data-ttu-id="d6ee0-102">Postupy: Kontrola nebo úprava parametrů</span><span class="sxs-lookup"><span data-stu-id="d6ee0-102">How to: Inspect or Modify Parameters</span></span>
<span data-ttu-id="d6ee0-103">Můžete zkontrolovat nebo upravit příchozí nebo odchozí zprávy pro jednu operaci na objektu klienta Windows Communication Foundation (WCF) nebo službě WCF implementací <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> rozhraní a jeho vložením do klienta nebo modulu runtime služby.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-103">You can inspect or modify the incoming or outgoing messages for a single operation on a Windows Communication Foundation (WCF) client object or a WCF service by implementing the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface and inserting it into the client or service runtime.</span></span> <span data-ttu-id="d6ee0-104">K přidání inspektorů parametrů pro jednu operaci se obvykle používá chování operace. Další chování lze použít k zajištění snadného přístupu k modulu runtime v širším rozsahu.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-104">Typically an operation behavior is used to add parameter inspectors for a single operation; other behaviors can be used to provide easy access to the runtime at a greater scope.</span></span> <span data-ttu-id="d6ee0-105">Další informace najdete v tématu [rozšíření klientů](extending-clients.md) a [rozšíření expedičních](extending-dispatchers.md)počítačů.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-105">For more information, see [Extending Clients](extending-clients.md) and [Extending Dispatchers](extending-dispatchers.md).</span></span>  
  
### <a name="inspecting-or-modifying-parameters"></a><span data-ttu-id="d6ee0-106">Kontrola nebo úprava parametrů</span><span class="sxs-lookup"><span data-stu-id="d6ee0-106">Inspecting or Modifying Parameters</span></span>  
  
1. <span data-ttu-id="d6ee0-107">Implementujte rozhraní <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-107">Implement the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="d6ee0-108"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> Implementujte<xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> , nebo (v<xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> závislosti na požadovaném oboru) přidejte svůj inspektor parametrů do vlastností nebo. <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="d6ee0-108">Implement a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (depending upon the required scope) to add your parameter inspector to either the <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> or <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> properties.</span></span>  
  
3. <span data-ttu-id="d6ee0-109">Vložte své chování před voláním <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> nebo metodou na <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-109">Insert your behavior prior to calling <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d6ee0-110">Podrobnosti najdete v tématu [Konfigurace a rozšíření modulu runtime s chováním](configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="d6ee0-110">For details, see [Configuring and Extending the Runtime with Behaviors](configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6ee0-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6ee0-111">Example</span></span>  
 <span data-ttu-id="d6ee0-112">Následující příklady kódu ukazují, v pořadí:</span><span class="sxs-lookup"><span data-stu-id="d6ee0-112">The following code examples show, in order:</span></span>  
  
- <span data-ttu-id="d6ee0-113">Implementace inspektoru parametru.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-113">A parameter inspector implementation.</span></span>  
  
- <span data-ttu-id="d6ee0-114">Implementace chování, která vloží inspektor parametru pomocí <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>a <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-114">The behavior implementation that inserts the parameter inspector using a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, and an <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="d6ee0-115">Konfigurační soubor, který načte a spustí chování koncového bodu v klientské aplikaci pro vložení inspektoru parametrů na klienta.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-115">A configuration file that loads and runs the endpoint behavior in a client application to insert the parameter inspector on the client.</span></span>  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code-xml[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  
  
## <a name="see-also"></a><span data-ttu-id="d6ee0-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6ee0-116">See also</span></span>

- [<span data-ttu-id="d6ee0-117">Konfigurace a rozšíření modulu runtime pomocí chování</span><span class="sxs-lookup"><span data-stu-id="d6ee0-117">Configuring and Extending the Runtime with Behaviors</span></span>](configuring-and-extending-the-runtime-with-behaviors.md)
