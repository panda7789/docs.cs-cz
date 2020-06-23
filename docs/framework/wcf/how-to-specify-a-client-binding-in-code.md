---
title: 'Postupy: Zadání klientské vazby v kódu'
description: Naučte se, jak určit vazbu pro klienta WCF imperativně v kódu. V tomto příkladu přistupuje klient ke službě.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: e5e1dff98121985a598579d83043de838e21e5f1
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244501"
---
# <a name="how-to-specify-a-client-binding-in-code"></a><span data-ttu-id="fce97-104">Postupy: Zadání klientské vazby v kódu</span><span class="sxs-lookup"><span data-stu-id="fce97-104">How to: Specify a Client Binding in Code</span></span>
<span data-ttu-id="fce97-105">V tomto příkladu je vytvořen klient pro použití služby kalkulačky a vazba pro tohoto klienta je v kódu určena imperativně.</span><span class="sxs-lookup"><span data-stu-id="fce97-105">In this example, a client is created to use a calculator service and the binding for that client is specified imperatively in code.</span></span> <span data-ttu-id="fce97-106">Klient přistupuje k `CalculatorService` rozhraní, které implementuje `ICalculator` rozhraní a jak službu, tak i klient používající <xref:System.ServiceModel.BasicHttpBinding> třídu.</span><span class="sxs-lookup"><span data-stu-id="fce97-106">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="fce97-107">Tento postup předpokládá, že je spuštěná služba kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="fce97-107">This procedure assumes that the calculator service is running.</span></span> <span data-ttu-id="fce97-108">Informace o sestavování služby najdete v tématu [How to: určení vazby služby v konfiguraci](how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="fce97-108">For information about building the service, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="fce97-109">K automatickému generování komponent klienta používá také nástroj pro dodávání [metadat (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="fce97-109">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="fce97-110">Nástroj vygeneruje kód klienta pro přístup ke službě.</span><span class="sxs-lookup"><span data-stu-id="fce97-110">The tool generates the client code for accessing the service.</span></span>  
  
 <span data-ttu-id="fce97-111">Klient je sestaven ve dvou částech.</span><span class="sxs-lookup"><span data-stu-id="fce97-111">The client is built in two parts.</span></span> <span data-ttu-id="fce97-112">Svcutil.exe generuje `ClientCalculator` rozhraní, které implementuje `ICalculator` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fce97-112">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="fce97-113">Tato klientská aplikace je pak vytvořena konstrukcí instance `ClientCalculator` a pak zadáním vazby a adresy služby v kódu.</span><span class="sxs-lookup"><span data-stu-id="fce97-113">This client application is then constructed by constructing an instance of `ClientCalculator` and then specifying the binding and the address for the service in code.</span></span>  
  
 <span data-ttu-id="fce97-114">Zdrojovou kopii tohoto příkladu najdete v ukázce [BasicBinding](./samples/basicbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="fce97-114">For the source copy of this example, see the [BasicBinding](./samples/basicbinding.md) sample.</span></span>  
  
### <a name="to-specify-a-custom-binding-in-code"></a><span data-ttu-id="fce97-115">Určení vlastní vazby v kódu</span><span class="sxs-lookup"><span data-stu-id="fce97-115">To specify a custom binding in code</span></span>  
  
1. <span data-ttu-id="fce97-116">K vygenerování kódu z metadat služby použijte Svcutil.exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="fce97-116">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="fce97-117">Vygenerovaný klient obsahuje `ICalculator` rozhraní, které definuje kontrakt služby, který musí implementace klienta splňovat.</span><span class="sxs-lookup"><span data-stu-id="fce97-117">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. <span data-ttu-id="fce97-118">Vygenerovaný klient také obsahuje implementaci `ClientCalculator` .</span><span class="sxs-lookup"><span data-stu-id="fce97-118">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. <span data-ttu-id="fce97-119">Vytvořte instanci `ClientCalculator` , která používá <xref:System.ServiceModel.BasicHttpBinding> třídu v klientské aplikaci, a potom zavolejte operace služby na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="fce97-119">Create an instance of the `ClientCalculator` that uses the <xref:System.ServiceModel.BasicHttpBinding> class in a client application, and then call the service operations at the specified address.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. <span data-ttu-id="fce97-120">Zkompilujte a spusťte klienta.</span><span class="sxs-lookup"><span data-stu-id="fce97-120">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fce97-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="fce97-121">See also</span></span>

- [<span data-ttu-id="fce97-122">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="fce97-122">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
