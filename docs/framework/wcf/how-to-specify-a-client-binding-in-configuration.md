---
title: 'Postupy: Zadání klientské vazby v konfiguraci'
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: 574f56173c2acfcf41a5e9a9e99abe45281e3636
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184041"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a><span data-ttu-id="5d82a-102">Postupy: Zadání klientské vazby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="5d82a-102">How to: Specify a Client Binding in Configuration</span></span>
<span data-ttu-id="5d82a-103">V tomto příkladu je vytvořena aplikace klientské konzole pro použití služby kalkulačky a vazba pro tohoto klienta je zadána deklarativně v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="5d82a-103">In this example, a client console application is created to use a calculator service, and the binding for that client is specified declaratively in configuration.</span></span> <span data-ttu-id="5d82a-104">Klient přistupuje k `CalculatorService` `ICalculator` aplikaci , která implementuje <xref:System.ServiceModel.BasicHttpBinding> rozhraní, a služba i klient používají třídu.</span><span class="sxs-lookup"><span data-stu-id="5d82a-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="5d82a-105">Uvedený postup předpokládá, že je spuštěna služba kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="5d82a-105">The procedure outlined assumes that the calculator service is running.</span></span> <span data-ttu-id="5d82a-106">Informace o tom, jak vytvořit službu, naleznete v [tématu How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="5d82a-106">For information about how to build the service, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="5d82a-107">Používá také [ServiceModel Metadata Utility Tool (Svcutil.exe),](servicemodel-metadata-utility-tool-svcutil-exe.md) který poskytuje Windows Communication Foundation (WCF) automaticky generovat klientské součásti.</span><span class="sxs-lookup"><span data-stu-id="5d82a-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) that Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="5d82a-108">Nástroj generuje klientský kód a konfiguraci pro přístup ke službě.</span><span class="sxs-lookup"><span data-stu-id="5d82a-108">The tool generates the client code and configuration for accessing the service.</span></span>  
  
 <span data-ttu-id="5d82a-109">Klient je postaven ve dvou částech.</span><span class="sxs-lookup"><span data-stu-id="5d82a-109">The client is built in two parts.</span></span> <span data-ttu-id="5d82a-110">Svcutil.exe `ClientCalculator` generuje, který implementuje `ICalculator` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5d82a-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="5d82a-111">Tato klientská aplikace je pak vytvořena `ClientCalculator`vytvořením instance aplikace .</span><span class="sxs-lookup"><span data-stu-id="5d82a-111">This client application is then constructed by constructing an instance of `ClientCalculator`.</span></span>  
  
 <span data-ttu-id="5d82a-112">Obvykle je osvědčeným postupem zadat vazby a adresu informace deklarativně v konfiguraci, nikoli imperativně v kódu.</span><span class="sxs-lookup"><span data-stu-id="5d82a-112">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="5d82a-113">Definování koncových bodů v kódu obvykle není praktické, protože vazby a adresy pro nasazenou službu se obvykle liší od těch, které se používají při vývoji služby.</span><span class="sxs-lookup"><span data-stu-id="5d82a-113">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="5d82a-114">Obecněji řečeno, udržování vazby a adresování informace z kódu umožňuje změnit bez nutnosti znovu zkompilovat nebo znovu nasadit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5d82a-114">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="5d82a-115">Pomocí [nástroje Editor configuration Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md)můžete provést všechny následující kroky konfigurace .</span><span class="sxs-lookup"><span data-stu-id="5d82a-115">You can perform all of the following configuration steps by using the [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="5d82a-116">Zdrojovou kopii tohoto příkladu naleznete v ukázce [BasicBinding.](./samples/basicbinding.md)</span><span class="sxs-lookup"><span data-stu-id="5d82a-116">For the source copy of this example, see the [BasicBinding](./samples/basicbinding.md) sample.</span></span>  
  
### <a name="specifying-a-client-binding-in-configuration"></a><span data-ttu-id="5d82a-117">Určení vazby klienta v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="5d82a-117">Specifying a client binding in configuration</span></span>  
  
1. <span data-ttu-id="5d82a-118">Pomocí příkazu Svcutil.exe z příkazového řádku vygenerujte kód z metadat služby.</span><span class="sxs-lookup"><span data-stu-id="5d82a-118">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="5d82a-119">Klient, který je generován `ICalculator` obsahuje rozhraní, které definuje servisní smlouvy, které implementace klienta musí splňovat.</span><span class="sxs-lookup"><span data-stu-id="5d82a-119">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3. <span data-ttu-id="5d82a-120">Vygenerovaný klient také `ClientCalculator`obsahuje implementaci .</span><span class="sxs-lookup"><span data-stu-id="5d82a-120">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4. <span data-ttu-id="5d82a-121">Svcutil.exe také generuje konfiguraci pro klienta, který používá třídu. <xref:System.ServiceModel.BasicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="5d82a-121">Svcutil.exe also generates the configuration for the client that uses the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span> <span data-ttu-id="5d82a-122">Při použití sady Visual Studio pojmenujte tento soubor App.config. Všimněte si, že adresa a informace o vazbě nejsou zadány nikde v rámci implementace služby.</span><span class="sxs-lookup"><span data-stu-id="5d82a-122">When using Visual Studio, name this file App.config. Note that the address and binding information are not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="5d82a-123">Kód také nemusí být zapsán, aby bylo možné načíst tyto informace z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="5d82a-123">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]

5. <span data-ttu-id="5d82a-124">Vytvořte instanci `ClientCalculator` v aplikaci a potom zavolejte operace služby.</span><span class="sxs-lookup"><span data-stu-id="5d82a-124">Create an instance of the `ClientCalculator` in an application, and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6. <span data-ttu-id="5d82a-125">Zkompilujte a spusťte klienta.</span><span class="sxs-lookup"><span data-stu-id="5d82a-125">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d82a-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d82a-126">See also</span></span>

- [<span data-ttu-id="5d82a-127">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="5d82a-127">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
