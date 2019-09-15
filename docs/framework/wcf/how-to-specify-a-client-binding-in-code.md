---
title: 'Postupy: Určení klientské vazby v kódu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: 37769a84ca623e2f7f246d36180aa17537e90bfa
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990233"
---
# <a name="how-to-specify-a-client-binding-in-code"></a><span data-ttu-id="38a68-102">Postupy: Určení klientské vazby v kódu</span><span class="sxs-lookup"><span data-stu-id="38a68-102">How to: Specify a Client Binding in Code</span></span>
<span data-ttu-id="38a68-103">V tomto příkladu je vytvořen klient pro použití služby kalkulačky a vazba pro tohoto klienta je v kódu určena imperativně.</span><span class="sxs-lookup"><span data-stu-id="38a68-103">In this example, a client is created to use a calculator service and the binding for that client is specified imperatively in code.</span></span> <span data-ttu-id="38a68-104">Klient přistupuje `CalculatorService`k `ICalculator` rozhraní, které implementuje rozhraní a jak službu, tak i klient používající <xref:System.ServiceModel.BasicHttpBinding> třídu.</span><span class="sxs-lookup"><span data-stu-id="38a68-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="38a68-105">Tento postup předpokládá, že je spuštěná služba kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="38a68-105">This procedure assumes that the calculator service is running.</span></span> <span data-ttu-id="38a68-106">Informace o tom, jak službu sestavovat, najdete v tématu [How to: Zadejte vazbu služby v konfiguraci](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="38a68-106">For information about building the service, see [How to: Specify a Service Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="38a68-107">K automatickému generování komponent klienta používá [Nástroj Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="38a68-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="38a68-108">Nástroj vygeneruje kód klienta pro přístup ke službě.</span><span class="sxs-lookup"><span data-stu-id="38a68-108">The tool generates the client code for accessing the service.</span></span>  
  
 <span data-ttu-id="38a68-109">Klient je sestaven ve dvou částech.</span><span class="sxs-lookup"><span data-stu-id="38a68-109">The client is built in two parts.</span></span> <span data-ttu-id="38a68-110">Svcutil. exe vygeneruje `ClientCalculator` `ICalculator` rozhraní, které implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="38a68-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="38a68-111">Tato klientská aplikace je pak vytvořena konstrukcí instance `ClientCalculator` a pak zadáním vazby a adresy služby v kódu.</span><span class="sxs-lookup"><span data-stu-id="38a68-111">This client application is then constructed by constructing an instance of `ClientCalculator` and then specifying the binding and the address for the service in code.</span></span>  
  
 <span data-ttu-id="38a68-112">Zdrojovou kopii tohoto příkladu najdete v ukázce [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="38a68-112">For the source copy of this example, see the [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) sample.</span></span>  
  
### <a name="to-specify-a-custom-binding-in-code"></a><span data-ttu-id="38a68-113">Určení vlastní vazby v kódu</span><span class="sxs-lookup"><span data-stu-id="38a68-113">To specify a custom binding in code</span></span>  
  
1. <span data-ttu-id="38a68-114">K vygenerování kódu z metadat služby použijte Svcutil. exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="38a68-114">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. <span data-ttu-id="38a68-115">Vygenerovaný klient obsahuje `ICalculator` rozhraní, které definuje kontrakt služby, který musí implementace klienta splňovat.</span><span class="sxs-lookup"><span data-stu-id="38a68-115">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. <span data-ttu-id="38a68-116">Vygenerovaný klient také obsahuje implementaci `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="38a68-116">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. <span data-ttu-id="38a68-117">Vytvořte instanci `ClientCalculator` , která <xref:System.ServiceModel.BasicHttpBinding> používá třídu v klientské aplikaci, a potom zavolejte operace služby na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="38a68-117">Create an instance of the `ClientCalculator` that uses the <xref:System.ServiceModel.BasicHttpBinding> class in a client application, and then call the service operations at the specified address.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. <span data-ttu-id="38a68-118">Zkompilujte a spusťte klienta.</span><span class="sxs-lookup"><span data-stu-id="38a68-118">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38a68-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38a68-119">See also</span></span>

- [<span data-ttu-id="38a68-120">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="38a68-120">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
