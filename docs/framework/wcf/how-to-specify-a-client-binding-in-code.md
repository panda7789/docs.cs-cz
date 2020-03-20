---
title: 'Postupy: Zadání klientské vazby v kódu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: 9be571d7be020aef546fdd7ec7cb7519a48ea350
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184059"
---
# <a name="how-to-specify-a-client-binding-in-code"></a><span data-ttu-id="2286e-102">Postupy: Zadání klientské vazby v kódu</span><span class="sxs-lookup"><span data-stu-id="2286e-102">How to: Specify a Client Binding in Code</span></span>
<span data-ttu-id="2286e-103">V tomto příkladu je klient vytvořen pro použití služby kalkulačky a vazba pro tohoto klienta je zadána imperativně v kódu.</span><span class="sxs-lookup"><span data-stu-id="2286e-103">In this example, a client is created to use a calculator service and the binding for that client is specified imperatively in code.</span></span> <span data-ttu-id="2286e-104">Klient přistupuje k `CalculatorService` `ICalculator` aplikaci , která implementuje <xref:System.ServiceModel.BasicHttpBinding> rozhraní, a služba i klient používají třídu.</span><span class="sxs-lookup"><span data-stu-id="2286e-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="2286e-105">Tento postup předpokládá, že je spuštěna služba kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="2286e-105">This procedure assumes that the calculator service is running.</span></span> <span data-ttu-id="2286e-106">Informace o vytváření služby naleznete v [tématu Postup: Zadání vazby služby v konfiguraci](how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="2286e-106">For information about building the service, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="2286e-107">Používá také [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) poskytuje automaticky generovat klientské součásti.</span><span class="sxs-lookup"><span data-stu-id="2286e-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="2286e-108">Nástroj generuje kód klienta pro přístup ke službě.</span><span class="sxs-lookup"><span data-stu-id="2286e-108">The tool generates the client code for accessing the service.</span></span>  
  
 <span data-ttu-id="2286e-109">Klient je postaven ve dvou částech.</span><span class="sxs-lookup"><span data-stu-id="2286e-109">The client is built in two parts.</span></span> <span data-ttu-id="2286e-110">Svcutil.exe `ClientCalculator` generuje, který implementuje `ICalculator` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2286e-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="2286e-111">Tato klientská aplikace je pak vytvořena `ClientCalculator` vytvořením instance a zadáním vazby a adresy pro službu v kódu.</span><span class="sxs-lookup"><span data-stu-id="2286e-111">This client application is then constructed by constructing an instance of `ClientCalculator` and then specifying the binding and the address for the service in code.</span></span>  
  
 <span data-ttu-id="2286e-112">Zdrojovou kopii tohoto příkladu naleznete v ukázce [BasicBinding.](./samples/basicbinding.md)</span><span class="sxs-lookup"><span data-stu-id="2286e-112">For the source copy of this example, see the [BasicBinding](./samples/basicbinding.md) sample.</span></span>  
  
### <a name="to-specify-a-custom-binding-in-code"></a><span data-ttu-id="2286e-113">Určení vlastní vazby v kódu</span><span class="sxs-lookup"><span data-stu-id="2286e-113">To specify a custom binding in code</span></span>  
  
1. <span data-ttu-id="2286e-114">Pomocí příkazu Svcutil.exe z příkazového řádku vygenerujte kód z metadat služby.</span><span class="sxs-lookup"><span data-stu-id="2286e-114">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="2286e-115">Klient, který je generován `ICalculator` obsahuje rozhraní, které definuje servisní smlouvy, které implementace klienta musí splňovat.</span><span class="sxs-lookup"><span data-stu-id="2286e-115">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. <span data-ttu-id="2286e-116">Vygenerovaný klient také `ClientCalculator`obsahuje implementaci .</span><span class="sxs-lookup"><span data-stu-id="2286e-116">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. <span data-ttu-id="2286e-117">Vytvořte `ClientCalculator` instanci, <xref:System.ServiceModel.BasicHttpBinding> která používá třídu v klientské aplikaci, a pak zavolejte operace služby na zadanou adresu.</span><span class="sxs-lookup"><span data-stu-id="2286e-117">Create an instance of the `ClientCalculator` that uses the <xref:System.ServiceModel.BasicHttpBinding> class in a client application, and then call the service operations at the specified address.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. <span data-ttu-id="2286e-118">Zkompilujte a spusťte klienta.</span><span class="sxs-lookup"><span data-stu-id="2286e-118">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2286e-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="2286e-119">See also</span></span>

- [<span data-ttu-id="2286e-120">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="2286e-120">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
