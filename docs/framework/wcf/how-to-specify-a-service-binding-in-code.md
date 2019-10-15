---
title: 'Postupy: Zadání vazby služby v kódu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 67ab5dd8-79c1-4e62-aa75-828ea918a53a
ms.openlocfilehash: 3c6cfd084055d59d3292b49897ff710f14f92737
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320876"
---
# <a name="how-to-specify-a-service-binding-in-code"></a><span data-ttu-id="2a5a8-102">Postupy: Zadání vazby služby v kódu</span><span class="sxs-lookup"><span data-stu-id="2a5a8-102">How to: Specify a Service Binding in Code</span></span>
<span data-ttu-id="2a5a8-103">V tomto příkladu je pro službu kalkulačky definována smlouva `ICalculator`, služba je implementována ve třídě `CalculatorService` a poté je její koncový bod definován v kódu, kde je určeno, že služba musí používat třídu <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="2a5a8-103">In this example, an `ICalculator` contract is defined for a calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is defined in code, where it is specified that the service must use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="2a5a8-104">Obvykle je osvědčeným postupem zadat vazby a informace o adrese deklarativně v konfiguraci, nikoli imperativně v kódu.</span><span class="sxs-lookup"><span data-stu-id="2a5a8-104">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="2a5a8-105">Definování koncových bodů v kódu obvykle není praktické, protože vazby a adresy nasazené služby se obvykle liší od těch, které se použily při vývoji služby.</span><span class="sxs-lookup"><span data-stu-id="2a5a8-105">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="2a5a8-106">Obecně platí, že zachování vazby a adresování informací z kódu umožňuje jejich změnu bez nutnosti opětovné kompilace nebo opětovného nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="2a5a8-106">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="2a5a8-107">Popis postupu konfigurace této služby pomocí prvků konfigurace namísto kódu naleznete v tématu [How to: zadat vazbu služby v konfiguraci](how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="2a5a8-107">For a description of how to configure this service using configuration elements instead of code, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
### <a name="to-specify-in-code-to-use-the-basichttpbinding-for-the-service"></a><span data-ttu-id="2a5a8-108">Zadání v kódu pro použití BasicHttpBinding pro službu</span><span class="sxs-lookup"><span data-stu-id="2a5a8-108">To specify in code to use the BasicHttpBinding for the service</span></span>  
  
1. <span data-ttu-id="2a5a8-109">Definujte kontrakt služby pro typ služby.</span><span class="sxs-lookup"><span data-stu-id="2a5a8-109">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2. <span data-ttu-id="2a5a8-110">Implementujte kontrakt služby ve třídě služby.</span><span class="sxs-lookup"><span data-stu-id="2a5a8-110">Implement the service contract in a service class.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3. <span data-ttu-id="2a5a8-111">V hostitelské aplikaci vytvořte základní adresu pro službu a vazbu, která se má používat se službou.</span><span class="sxs-lookup"><span data-stu-id="2a5a8-111">In the hosting application, create the base address for the service and the binding to use with the service.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4. <span data-ttu-id="2a5a8-112">Vytvořte hostitele pro službu, přidejte koncový bod a pak otevřete hostitele.</span><span class="sxs-lookup"><span data-stu-id="2a5a8-112">Create the host for the service, add the endpoint, and then open the host.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#4)]
     [!code-vb[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#4)]  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a><span data-ttu-id="2a5a8-113">Úprava výchozích hodnot vlastností vazby</span><span class="sxs-lookup"><span data-stu-id="2a5a8-113">To modify the default values of the binding properties</span></span>  
  
1. <span data-ttu-id="2a5a8-114">Chcete-li upravit jednu z hodnot výchozí vlastnosti třídy <xref:System.ServiceModel.BasicHttpBinding>, nastavte hodnotu vlastnosti vazby na novou hodnotu před vytvořením hostitele.</span><span class="sxs-lookup"><span data-stu-id="2a5a8-114">To modify one of the default property values of the <xref:System.ServiceModel.BasicHttpBinding> class, set the property value on the binding to the new value before creating the host.</span></span> <span data-ttu-id="2a5a8-115">Pokud například chcete změnit výchozí hodnoty časového limitu pro otevření a zavření 1 minuty na 2 minuty, použijte následující.</span><span class="sxs-lookup"><span data-stu-id="2a5a8-115">For example, to change the default open and close timeout values of 1 minute to 2 minutes, use the following.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#5)]
     [!code-vb[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="2a5a8-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2a5a8-116">See also</span></span>

- [<span data-ttu-id="2a5a8-117">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="2a5a8-117">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="2a5a8-118">Zadání adresy koncového bodu</span><span class="sxs-lookup"><span data-stu-id="2a5a8-118">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)
