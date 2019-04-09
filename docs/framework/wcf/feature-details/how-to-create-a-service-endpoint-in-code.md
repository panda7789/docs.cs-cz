---
title: 'Postupy: Vytvoření koncového bodu služby v kódu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fbb22fa-2930-48b8-b437-def1de87c6a0
ms.openlocfilehash: 0b51018a5940e01b38b00addb762fa6504495a4c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139864"
---
# <a name="how-to-create-a-service-endpoint-in-code"></a><span data-ttu-id="c4c0a-102">Postupy: Vytvoření koncového bodu služby v kódu</span><span class="sxs-lookup"><span data-stu-id="c4c0a-102">How to: Create a Service Endpoint in Code</span></span>
<span data-ttu-id="c4c0a-103">V tomto příkladu `ICalculator` smlouvy je definován pro službu kalkulačky, služba se implementuje v `CalculatorService` třídě a následně svůj koncový bod je definováno v kódu, kde je zadán, že musíte použít službu <xref:System.ServiceModel.BasicHttpBinding> třídy.</span><span class="sxs-lookup"><span data-stu-id="c4c0a-103">In this example, an `ICalculator` contract is defined for a calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is defined in code, where it is specified that the service must use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="c4c0a-104">Obvykle je osvědčeným postupem určete vazbu a informace o adrese deklarativně v konfiguraci, nikoli imperativně v kódu.</span><span class="sxs-lookup"><span data-stu-id="c4c0a-104">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="c4c0a-105">Definování koncových bodů v kódu není obvykle praktické protože vazeb a adresy pro službu nasazenou se obvykle liší od nastavení použít, je vyvíjena služby.</span><span class="sxs-lookup"><span data-stu-id="c4c0a-105">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="c4c0a-106">Obecně platí udržování vazby a adresování informace mimo kód jim umožňuje změnit bez nutnosti znovu kompilovat nebo znovu nasadit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c4c0a-106">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
#### <a name="to-create-a-service-endpoint-in-code"></a><span data-ttu-id="c4c0a-107">Vytvoření koncového bodu služby v kódu</span><span class="sxs-lookup"><span data-stu-id="c4c0a-107">To create a service endpoint in code</span></span>  
  
1.  <span data-ttu-id="c4c0a-108">Vytvoření rozhraní definuje kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="c4c0a-108">Create the interface that defines the service contract.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[c_HowTo_CodeServiceBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2.  <span data-ttu-id="c4c0a-109">Implementace kontraktu služby, který je definovaný v kroku 1.</span><span class="sxs-lookup"><span data-stu-id="c4c0a-109">Implement the service contract defined in step 1.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[c_HowTo_CodeServiceBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3.  <span data-ttu-id="c4c0a-110">V hostitelské aplikace vytvořte základní adresa služby a vazby pro použití se službou.</span><span class="sxs-lookup"><span data-stu-id="c4c0a-110">In the hosting application, create the base address for the service and the binding to be used with the service.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[c_HowTo_CodeServiceBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4.  <span data-ttu-id="c4c0a-111">Vytvoření hostitele a volání <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29> nebo jednoho z přetížení přidat koncový bod služby pro hostitele.</span><span class="sxs-lookup"><span data-stu-id="c4c0a-111">Create the host and call <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29> or one of the other overloads to add the service endpoint for the host.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#6)]
     [!code-vb[c_HowTo_CodeServiceBinding#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#6)]  
  
     <span data-ttu-id="c4c0a-112">Určení vazby v kódu, ale používat výchozí koncové body poskytovaný modulem runtime, předat adresu basů konstruktoru při vytváření <xref:System.ServiceModel.ServiceHost>a Nevolejte <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>.</span><span class="sxs-lookup"><span data-stu-id="c4c0a-112">To specify the binding in code, but to use the default endpoints provided by the runtime, pass the bass address into constructor when creating the <xref:System.ServiceModel.ServiceHost>, and do not call <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#7)]
     [!code-vb[c_HowTo_CodeServiceBinding#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#7)]  
  
     <span data-ttu-id="c4c0a-113">Další informace o výchozí koncové body, naleznete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="c4c0a-113">For more information about default endpoints, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4c0a-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4c0a-114">See also</span></span>

- [<span data-ttu-id="c4c0a-115">Postupy: Určení vazby služby v kódu</span><span class="sxs-lookup"><span data-stu-id="c4c0a-115">How to: Specify a Service Binding in Code</span></span>](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md)
