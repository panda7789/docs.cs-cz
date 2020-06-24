---
title: 'Postupy: Vytvoření koncového bodu služby v kódu'
description: Přečtěte si, jak implementovat službu ve třídě a jak programově definovat její koncový bod. V rámci služby WCF jsou koncové body obvykle definovány v konfiguračním souboru.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fbb22fa-2930-48b8-b437-def1de87c6a0
ms.openlocfilehash: 3b2ff2a17975bc381db61edc2c0f85f67edd3325
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247049"
---
# <a name="how-to-create-a-service-endpoint-in-code"></a><span data-ttu-id="7b8c1-104">Postupy: Vytvoření koncového bodu služby v kódu</span><span class="sxs-lookup"><span data-stu-id="7b8c1-104">How to: Create a Service Endpoint in Code</span></span>
<span data-ttu-id="7b8c1-105">V tomto příkladu `ICalculator` je smlouva definována pro službu kalkulačky, služba je implementována ve `CalculatorService` třídě a poté je její koncový bod definován v kódu, kde je určeno, že služba musí <xref:System.ServiceModel.BasicHttpBinding> třídu používat.</span><span class="sxs-lookup"><span data-stu-id="7b8c1-105">In this example, an `ICalculator` contract is defined for a calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is defined in code, where it is specified that the service must use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="7b8c1-106">Obvykle je osvědčeným postupem zadat vazby a informace o adrese deklarativně v konfiguraci, nikoli imperativně v kódu.</span><span class="sxs-lookup"><span data-stu-id="7b8c1-106">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="7b8c1-107">Definování koncových bodů v kódu obvykle není praktické, protože vazby a adresy nasazené služby se obvykle liší od těch, které se použily při vývoji služby.</span><span class="sxs-lookup"><span data-stu-id="7b8c1-107">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="7b8c1-108">Obecně platí, že zachování vazby a adresování informací z kódu umožňuje jejich změnu bez nutnosti opětovné kompilace nebo opětovného nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b8c1-108">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
#### <a name="to-create-a-service-endpoint-in-code"></a><span data-ttu-id="7b8c1-109">Vytvoření koncového bodu služby v kódu</span><span class="sxs-lookup"><span data-stu-id="7b8c1-109">To create a service endpoint in code</span></span>  
  
1. <span data-ttu-id="7b8c1-110">Vytvořte rozhraní, které definuje kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="7b8c1-110">Create the interface that defines the service contract.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[c_HowTo_CodeServiceBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2. <span data-ttu-id="7b8c1-111">Implementujte kontrakt služby definovaný v kroku 1.</span><span class="sxs-lookup"><span data-stu-id="7b8c1-111">Implement the service contract defined in step 1.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[c_HowTo_CodeServiceBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3. <span data-ttu-id="7b8c1-112">V hostitelské aplikaci vytvořte základní adresu pro službu a vazbu, která se má používat se službou.</span><span class="sxs-lookup"><span data-stu-id="7b8c1-112">In the hosting application, create the base address for the service and the binding to be used with the service.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[c_HowTo_CodeServiceBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4. <span data-ttu-id="7b8c1-113">Vytvořte hostitele a volání <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29?displayProperty=nameWithType> nebo jedno z dalších přetížení pro přidání koncového bodu služby pro hostitele.</span><span class="sxs-lookup"><span data-stu-id="7b8c1-113">Create the host and call <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29?displayProperty=nameWithType> or one of the other overloads to add the service endpoint for the host.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#6)]
     [!code-vb[c_HowTo_CodeServiceBinding#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#6)]  
  
     <span data-ttu-id="7b8c1-114">Chcete-li zadat vazbu v kódu, ale chcete použít výchozí koncové body poskytované modulem runtime, předejte základní adresu do konstruktoru při vytváření <xref:System.ServiceModel.ServiceHost> a Nevolejte <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7b8c1-114">To specify the binding in code but to use the default endpoints provided by the runtime, pass the base address into the constructor when creating the <xref:System.ServiceModel.ServiceHost>, and do not call <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A?displayProperty=nameWithType>.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#7)]
     [!code-vb[c_HowTo_CodeServiceBinding#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#7)]  
  
     <span data-ttu-id="7b8c1-115">Další informace o výchozích koncových bodech najdete v tématu [zjednodušená konfigurace](../simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="7b8c1-115">For more information about default endpoints, see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b8c1-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b8c1-116">See also</span></span>

- [<span data-ttu-id="7b8c1-117">Postupy: Určení vazby služby v kódu</span><span class="sxs-lookup"><span data-stu-id="7b8c1-117">How to: Specify a Service Binding in Code</span></span>](../how-to-specify-a-service-binding-in-code.md)
