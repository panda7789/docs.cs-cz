---
title: "Postupy: Zadání klientské vazby v kódu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ad7dcaee93385d2409c2255a6f0bd950bd2f9821
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-specify-a-client-binding-in-code"></a><span data-ttu-id="39a29-102">Postupy: Zadání klientské vazby v kódu</span><span class="sxs-lookup"><span data-stu-id="39a29-102">How to: Specify a Client Binding in Code</span></span>
<span data-ttu-id="39a29-103">V tomto příkladu se vytvoří klienta pomocí kalkulačky služby a vazby pro tohoto klienta je imperativní zadaný v kódu.</span><span class="sxs-lookup"><span data-stu-id="39a29-103">In this example, a client is created to use a calculator service and the binding for that client is specified imperatively in code.</span></span> <span data-ttu-id="39a29-104">Klient přistupuje k `CalculatorService`, který implementuje `ICalculator` rozhraní a jak službu a klienta použít <xref:System.ServiceModel.BasicHttpBinding> třídy.</span><span class="sxs-lookup"><span data-stu-id="39a29-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="39a29-105">Tento postup předpokládá, že je spuštěna služba kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="39a29-105">This procedure assumes that the calculator service is running.</span></span> <span data-ttu-id="39a29-106">Informace o vytváření služby najdete v tématu [postupy: zadání vazby služby v konfiguraci](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="39a29-106">For information about building the service, see [How to: Specify a Service Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="39a29-107">Používá také [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] poskytuje k automatickému generování součásti klienta.</span><span class="sxs-lookup"><span data-stu-id="39a29-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] provides to automatically generate the client components.</span></span> <span data-ttu-id="39a29-108">Nástroj generuje kód klienta pro přístup k službě.</span><span class="sxs-lookup"><span data-stu-id="39a29-108">The tool generates the client code for accessing the service.</span></span>  
  
 <span data-ttu-id="39a29-109">Klient je součástí dvě části.</span><span class="sxs-lookup"><span data-stu-id="39a29-109">The client is built in two parts.</span></span> <span data-ttu-id="39a29-110">Generuje svcutil.exe `ClientCalculator` , která implementuje `ICalculator` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="39a29-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="39a29-111">Tuto aplikaci klienta je pak vytvořený vytvořením instanci `ClientCalculator` a potom zadáte vazby a adresu pro služby v kódu.</span><span class="sxs-lookup"><span data-stu-id="39a29-111">This client application is then constructed by constructing an instance of `ClientCalculator` and then specifying the binding and the address for the service in code.</span></span>  
  
 <span data-ttu-id="39a29-112">Zdroj kopírování tohoto příkladu, najdete v článku [základní vazby](../../../docs/framework/wcf/samples/basicbinding.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="39a29-112">For the source copy of this example, see the [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) sample.</span></span>  
  
### <a name="to-specify-a-custom-binding-in-code"></a><span data-ttu-id="39a29-113">Chcete-li určit vlastní vazby v kódu</span><span class="sxs-lookup"><span data-stu-id="39a29-113">To specify a custom binding in code</span></span>  
  
1.  <span data-ttu-id="39a29-114">Generování kódu z metadat služby pomocí Svcutil.exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="39a29-114">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  <span data-ttu-id="39a29-115">Obsahuje klienta, který se generuje `ICalculator` rozhraní, které definuje kontrakt služby, které musí splňovat implementace klienta.</span><span class="sxs-lookup"><span data-stu-id="39a29-115">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3.  <span data-ttu-id="39a29-116">Generovaného klienta obsahuje také provádění `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="39a29-116">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4.  <span data-ttu-id="39a29-117">Vytvoření instance `ClientCalculator` používající <xref:System.ServiceModel.BasicHttpBinding> třídy v aplikaci klienta a pak volání operací služby na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="39a29-117">Create an instance of the `ClientCalculator` that uses the <xref:System.ServiceModel.BasicHttpBinding> class in a client application, and then call the service operations at the specified address.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5.  <span data-ttu-id="39a29-118">Zkompilování a spuštění klienta.</span><span class="sxs-lookup"><span data-stu-id="39a29-118">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39a29-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="39a29-119">See Also</span></span>  
 [<span data-ttu-id="39a29-120">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="39a29-120">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
