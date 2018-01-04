---
title: "Postupy: Zadání klientské vazby v konfiguraci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 08cbf0145a2ac3f19e51a065acf97e3cf23b7986
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a><span data-ttu-id="a0cf5-102">Postupy: Zadání klientské vazby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="a0cf5-102">How to: Specify a Client Binding in Configuration</span></span>
<span data-ttu-id="a0cf5-103">V tomto příkladu aplikace konzoly klienta se vytvoří pomocí kalkulačky služby a vazby pro tohoto klienta je deklarativně zadaný v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="a0cf5-103">In this example, a client console application is created to use a calculator service, and the binding for that client is specified declaratively in configuration.</span></span> <span data-ttu-id="a0cf5-104">Klient přistupuje k `CalculatorService`, který implementuje `ICalculator` rozhraní a jak službu a klienta použít <xref:System.ServiceModel.BasicHttpBinding> třídy.</span><span class="sxs-lookup"><span data-stu-id="a0cf5-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="a0cf5-105">Podle uvedeného postupu předpokládá, že je spuštěna služba kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="a0cf5-105">The procedure outlined assumes that the calculator service is running.</span></span> <span data-ttu-id="a0cf5-106">Informace o tom, jak sestavit službu najdete v tématu [postupy: zadání vazby služby v konfiguraci](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="a0cf5-106">For information about how to build the service, see [How to: Specify a Service Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="a0cf5-107">Používá také [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) , [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] poskytuje k automatickému generování součásti klienta.</span><span class="sxs-lookup"><span data-stu-id="a0cf5-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) that [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] provides to automatically generate the client components.</span></span> <span data-ttu-id="a0cf5-108">Nástroj generuje kód klienta a konfigurace přístupu ke službě.</span><span class="sxs-lookup"><span data-stu-id="a0cf5-108">The tool generates the client code and configuration for accessing the service.</span></span>  
  
 <span data-ttu-id="a0cf5-109">Klient je součástí dvě části.</span><span class="sxs-lookup"><span data-stu-id="a0cf5-109">The client is built in two parts.</span></span> <span data-ttu-id="a0cf5-110">Generuje svcutil.exe `ClientCalculator` , která implementuje `ICalculator` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a0cf5-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="a0cf5-111">Tuto aplikaci klienta je pak vytvořený vytvořením instance `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="a0cf5-111">This client application is then constructed by constructing an instance of `ClientCalculator`.</span></span>  
  
 <span data-ttu-id="a0cf5-112">Obvykle je osvědčeným postupem zadejte vazby a informace o adrese deklarativně v konfiguraci, nikoli imperativní v kódu.</span><span class="sxs-lookup"><span data-stu-id="a0cf5-112">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="a0cf5-113">Definování koncové body v kódu obvykle není praktické protože jsou obvykle liší od těch, které používá při služby je vyvíjen vazeb a adresy pro v nasazené službě.</span><span class="sxs-lookup"><span data-stu-id="a0cf5-113">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="a0cf5-114">Obecně platí udržování vazby a adresování informace mimo kód jim umožňuje změnit bez nutnosti znovu zkompiluje nebo znovu nasadit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a0cf5-114">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="a0cf5-115">Všechny tyto kroky konfigurace můžete provádět pomocí [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="a0cf5-115">You can perform all of the following configuration steps by using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="a0cf5-116">Zdroj kopírování tohoto příkladu, najdete v článku [základní vazby](../../../docs/framework/wcf/samples/basicbinding.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="a0cf5-116">For the source copy of this example, see the [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) sample.</span></span>  
  
### <a name="specifying-a-client-binding-in-configuration"></a><span data-ttu-id="a0cf5-117">Určení vazby v konfiguraci klienta</span><span class="sxs-lookup"><span data-stu-id="a0cf5-117">Specifying a client binding in configuration</span></span>  
  
1.  <span data-ttu-id="a0cf5-118">Generování kódu z metadat služby pomocí Svcutil.exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a0cf5-118">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  <span data-ttu-id="a0cf5-119">Obsahuje klienta, který se generuje `ICalculator` rozhraní, které definuje kontrakt služby, které musí splňovat implementace klienta.</span><span class="sxs-lookup"><span data-stu-id="a0cf5-119">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3.  <span data-ttu-id="a0cf5-120">Generovaného klienta obsahuje také provádění `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="a0cf5-120">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4.  <span data-ttu-id="a0cf5-121">Svcutil.exe také generuje konfiguraci pro klienta, který používá <xref:System.ServiceModel.BasicHttpBinding> třídy.</span><span class="sxs-lookup"><span data-stu-id="a0cf5-121">Svcutil.exe also generates the configuration for the client that uses the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span> <span data-ttu-id="a0cf5-122">Při použití [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], název tohoto souboru App.config. Všimněte si, že adresu a informace o vazbě nejsou zadat kdekoli v rámci implementace služby.</span><span class="sxs-lookup"><span data-stu-id="a0cf5-122">When using [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], name this file App.config. Note that the address and binding information are not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="a0cf5-123">Kód také nemá k zapsání k načtení těchto informací z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="a0cf5-123">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]   
            
5.  <span data-ttu-id="a0cf5-124">Vytvoření instance `ClientCalculator` v aplikaci a pak volání operací služby.</span><span class="sxs-lookup"><span data-stu-id="a0cf5-124">Create an instance of the `ClientCalculator` in an application, and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6.  <span data-ttu-id="a0cf5-125">Zkompilování a spuštění klienta.</span><span class="sxs-lookup"><span data-stu-id="a0cf5-125">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0cf5-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0cf5-126">See Also</span></span>  
 [<span data-ttu-id="a0cf5-127">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="a0cf5-127">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
