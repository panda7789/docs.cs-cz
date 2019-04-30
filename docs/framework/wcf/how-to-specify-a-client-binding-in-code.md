---
title: 'Postupy: Určení klientské vazby v kódu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: c95e30c65c6096140fca0c1241e76fbc7af4df3d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929126"
---
# <a name="how-to-specify-a-client-binding-in-code"></a><span data-ttu-id="e61ee-102">Postupy: Určení klientské vazby v kódu</span><span class="sxs-lookup"><span data-stu-id="e61ee-102">How to: Specify a Client Binding in Code</span></span>
<span data-ttu-id="e61ee-103">V tomto příkladu se vytvoří klienta pro použití kalkulačky služby a vazby pro tohoto klienta je imperativně zadat v kódu.</span><span class="sxs-lookup"><span data-stu-id="e61ee-103">In this example, a client is created to use a calculator service and the binding for that client is specified imperatively in code.</span></span> <span data-ttu-id="e61ee-104">Klient přistupuje k `CalculatorService`, která implementuje `ICalculator` rozhraní a službě i klientovi použít <xref:System.ServiceModel.BasicHttpBinding> třídy.</span><span class="sxs-lookup"><span data-stu-id="e61ee-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="e61ee-105">Tento postup předpokládá, že je spuštěna služba kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="e61ee-105">This procedure assumes that the calculator service is running.</span></span> <span data-ttu-id="e61ee-106">Informace o vytváření služby najdete v tématu [jak: Zadání vazby služby v konfiguraci](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="e61ee-106">For information about building the service, see [How to: Specify a Service Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="e61ee-107">Využívá také [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) poskytuje klientské součásti budou automaticky generovány.</span><span class="sxs-lookup"><span data-stu-id="e61ee-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="e61ee-108">Nástroj vygeneruje kód klienta pro přístupu ke službě.</span><span class="sxs-lookup"><span data-stu-id="e61ee-108">The tool generates the client code for accessing the service.</span></span>  
  
 <span data-ttu-id="e61ee-109">Klient je vytvořená ve dvou částech.</span><span class="sxs-lookup"><span data-stu-id="e61ee-109">The client is built in two parts.</span></span> <span data-ttu-id="e61ee-110">Generuje svcutil.exe `ClientCalculator` , který implementuje `ICalculator` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e61ee-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="e61ee-111">Tato klientská aplikace pak konstruován tak, že vytváří instanci `ClientCalculator` a potom zadáte vazbu a adresu pro službu v kódu.</span><span class="sxs-lookup"><span data-stu-id="e61ee-111">This client application is then constructed by constructing an instance of `ClientCalculator` and then specifying the binding and the address for the service in code.</span></span>  
  
 <span data-ttu-id="e61ee-112">Pro zdrojovou kopii tohoto příkladu, najdete v článku [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="e61ee-112">For the source copy of this example, see the [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) sample.</span></span>  
  
### <a name="to-specify-a-custom-binding-in-code"></a><span data-ttu-id="e61ee-113">Chcete-li určit vlastní vazby v kódu</span><span class="sxs-lookup"><span data-stu-id="e61ee-113">To specify a custom binding in code</span></span>  
  
1. <span data-ttu-id="e61ee-114">Pomocí Svcutil.exe lze generovat kód z metadat služby z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="e61ee-114">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. <span data-ttu-id="e61ee-115">Klient, který je generován obsahuje `ICalculator` rozhraní, které definuje kontrakt služby, který musí splňovat implementace klienta.</span><span class="sxs-lookup"><span data-stu-id="e61ee-115">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. <span data-ttu-id="e61ee-116">Také obsahuje implementaci generovaného klienta `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="e61ee-116">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. <span data-ttu-id="e61ee-117">Vytvoření instance `ClientCalculator` , která používá <xref:System.ServiceModel.BasicHttpBinding> třídy v klientské aplikaci a potom volání operací služby na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="e61ee-117">Create an instance of the `ClientCalculator` that uses the <xref:System.ServiceModel.BasicHttpBinding> class in a client application, and then call the service operations at the specified address.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. <span data-ttu-id="e61ee-118">Kompilace a spuštění klienta.</span><span class="sxs-lookup"><span data-stu-id="e61ee-118">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e61ee-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e61ee-119">See also</span></span>

- [<span data-ttu-id="e61ee-120">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="e61ee-120">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
