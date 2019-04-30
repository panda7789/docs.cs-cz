---
title: 'Postupy: Určení vazby služby v kódu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 67ab5dd8-79c1-4e62-aa75-828ea918a53a
ms.openlocfilehash: 9f3320b031141246a394191a1924509204707dc1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61928801"
---
# <a name="how-to-specify-a-service-binding-in-code"></a><span data-ttu-id="50c55-102">Postupy: Určení vazby služby v kódu</span><span class="sxs-lookup"><span data-stu-id="50c55-102">How to: Specify a Service Binding in Code</span></span>
<span data-ttu-id="50c55-103">V tomto příkladu `ICalculator` smlouvy je definován pro službu kalkulačky, služba se implementuje v `CalculatorService` třídě a následně svůj koncový bod je definováno v kódu, kde je zadán, že musíte použít službu <xref:System.ServiceModel.BasicHttpBinding> třídy.</span><span class="sxs-lookup"><span data-stu-id="50c55-103">In this example, an `ICalculator` contract is defined for a calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is defined in code, where it is specified that the service must use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="50c55-104">Obvykle je osvědčeným postupem určete vazbu a informace o adrese deklarativně v konfiguraci, nikoli imperativně v kódu.</span><span class="sxs-lookup"><span data-stu-id="50c55-104">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="50c55-105">Definování koncových bodů v kódu není obvykle praktické protože vazeb a adresy pro službu nasazenou se obvykle liší od nastavení použít, je vyvíjena služby.</span><span class="sxs-lookup"><span data-stu-id="50c55-105">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="50c55-106">Obecně platí udržování vazby a adresování informace mimo kód jim umožňuje změnit bez nutnosti znovu kompilovat nebo znovu nasadit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="50c55-106">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="50c55-107">Popis, jak nakonfigurovat tuto službu, pomocí elementů konfigurace namísto kódu najdete v tématu [jak: Zadání vazby služby v konfiguraci](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="50c55-107">For a description of how to configure this service using configuration elements instead of code, see [How to: Specify a Service Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
### <a name="to-specify-in-code-to-use-the-basichttpbinding-for-the-service"></a><span data-ttu-id="50c55-108">Pokud chcete zadat do kódu pro použití BasicHttpBinding pro službu</span><span class="sxs-lookup"><span data-stu-id="50c55-108">To specify in code to use the BasicHttpBinding for the service</span></span>  
  
1. <span data-ttu-id="50c55-109">Definování kontraktu služby pro typ služby.</span><span class="sxs-lookup"><span data-stu-id="50c55-109">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2. <span data-ttu-id="50c55-110">Implementace kontraktu služby ve třídě služby.</span><span class="sxs-lookup"><span data-stu-id="50c55-110">Implement the service contract in a service class.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3. <span data-ttu-id="50c55-111">V hostitelské aplikace vytvořte základní adresa služby a vazby pro použití se službou.</span><span class="sxs-lookup"><span data-stu-id="50c55-111">In the hosting application, create the base address for the service and the binding to use with the service.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4. <span data-ttu-id="50c55-112">Vytvoření hostitele pro službu, přidat koncový bod a poté otevřete hostitele.</span><span class="sxs-lookup"><span data-stu-id="50c55-112">Create the host for the service, add the endpoint, and then open the host.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#4)]
     [!code-vb[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#4)]  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a><span data-ttu-id="50c55-113">Chcete-li změnit výchozí hodnoty vlastností vazby</span><span class="sxs-lookup"><span data-stu-id="50c55-113">To modify the default values of the binding properties</span></span>  
  
1. <span data-ttu-id="50c55-114">Chcete-li změnit jeden z výchozí hodnoty vlastností <xref:System.ServiceModel.BasicHttpBinding> třídy, nastavte hodnotu vlastností pro vazbu na novou hodnotu před vytvořením hostitele.</span><span class="sxs-lookup"><span data-stu-id="50c55-114">To modify one of the default property values of the <xref:System.ServiceModel.BasicHttpBinding> class, set the property value on the binding to the new value before creating the host.</span></span> <span data-ttu-id="50c55-115">Například pokud chcete změnit výchozí časový limit otevření a zavření hodnoty 1 minuta 2 minuty, použijte následující.</span><span class="sxs-lookup"><span data-stu-id="50c55-115">For example, to change the default open and close timeout values of 1 minute to 2 minutes, use the following.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#5)]
     [!code-vb[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="50c55-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50c55-116">See also</span></span>

- [<span data-ttu-id="50c55-117">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="50c55-117">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="50c55-118">Zadání adresy koncového bodu</span><span class="sxs-lookup"><span data-stu-id="50c55-118">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)
