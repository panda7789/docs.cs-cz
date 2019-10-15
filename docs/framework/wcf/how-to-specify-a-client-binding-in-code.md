---
title: 'Postupy: Zadání klientské vazby v kódu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: ec5db7a305a63ac7ae9c2e2a7bb1c9c7691b8daa
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320890"
---
# <a name="how-to-specify-a-client-binding-in-code"></a><span data-ttu-id="eebe6-102">Postupy: Zadání klientské vazby v kódu</span><span class="sxs-lookup"><span data-stu-id="eebe6-102">How to: Specify a Client Binding in Code</span></span>
<span data-ttu-id="eebe6-103">V tomto příkladu je vytvořen klient pro použití služby kalkulačky a vazba pro tohoto klienta je v kódu určena imperativně.</span><span class="sxs-lookup"><span data-stu-id="eebe6-103">In this example, a client is created to use a calculator service and the binding for that client is specified imperatively in code.</span></span> <span data-ttu-id="eebe6-104">Klient přistupuje k `CalculatorService`, který implementuje rozhraní `ICalculator` a jak službu, tak i klient používající třídu <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="eebe6-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="eebe6-105">Tento postup předpokládá, že je spuštěná služba kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="eebe6-105">This procedure assumes that the calculator service is running.</span></span> <span data-ttu-id="eebe6-106">Informace o sestavování služby najdete v tématu [How to: určení vazby služby v konfiguraci](how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="eebe6-106">For information about building the service, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="eebe6-107">K automatickému generování komponent klienta používá [Nástroj Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="eebe6-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="eebe6-108">Nástroj vygeneruje kód klienta pro přístup ke službě.</span><span class="sxs-lookup"><span data-stu-id="eebe6-108">The tool generates the client code for accessing the service.</span></span>  
  
 <span data-ttu-id="eebe6-109">Klient je sestaven ve dvou částech.</span><span class="sxs-lookup"><span data-stu-id="eebe6-109">The client is built in two parts.</span></span> <span data-ttu-id="eebe6-110">Svcutil. exe vygeneruje `ClientCalculator`, který implementuje rozhraní `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="eebe6-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="eebe6-111">Tato klientská aplikace je pak vytvořena konstrukcí instance `ClientCalculator` a zadáním vazby a adresy pro službu v kódu.</span><span class="sxs-lookup"><span data-stu-id="eebe6-111">This client application is then constructed by constructing an instance of `ClientCalculator` and then specifying the binding and the address for the service in code.</span></span>  
  
 <span data-ttu-id="eebe6-112">Zdrojovou kopii tohoto příkladu najdete v ukázce [BasicBinding](./samples/basicbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="eebe6-112">For the source copy of this example, see the [BasicBinding](./samples/basicbinding.md) sample.</span></span>  
  
### <a name="to-specify-a-custom-binding-in-code"></a><span data-ttu-id="eebe6-113">Určení vlastní vazby v kódu</span><span class="sxs-lookup"><span data-stu-id="eebe6-113">To specify a custom binding in code</span></span>  
  
1. <span data-ttu-id="eebe6-114">K vygenerování kódu z metadat služby použijte Svcutil. exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="eebe6-114">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. <span data-ttu-id="eebe6-115">Vygenerovaný klient obsahuje rozhraní `ICalculator` definující kontrakt služby, který musí implementace klienta splňovat.</span><span class="sxs-lookup"><span data-stu-id="eebe6-115">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. <span data-ttu-id="eebe6-116">Vygenerovaný klient obsahuje také implementaci `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="eebe6-116">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. <span data-ttu-id="eebe6-117">Vytvořte instanci `ClientCalculator`, která používá třídu <xref:System.ServiceModel.BasicHttpBinding> v klientské aplikaci, a pak na zadané adrese volejte operace služby.</span><span class="sxs-lookup"><span data-stu-id="eebe6-117">Create an instance of the `ClientCalculator` that uses the <xref:System.ServiceModel.BasicHttpBinding> class in a client application, and then call the service operations at the specified address.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. <span data-ttu-id="eebe6-118">Zkompilujte a spusťte klienta.</span><span class="sxs-lookup"><span data-stu-id="eebe6-118">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eebe6-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eebe6-119">See also</span></span>

- [<span data-ttu-id="eebe6-120">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="eebe6-120">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
