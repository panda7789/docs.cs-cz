---
title: 'Postupy: Zadání klientské vazby v konfiguraci'
description: Naučte se, jak zadat vazbu pro klienta WCF deklarativně v konfiguračním souboru. V tomto příkladu přistupuje klient ke službě.
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: 28778b6ae853199c5d7943f329bb087760f4bb11
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244488"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a><span data-ttu-id="59255-104">Postupy: Zadání klientské vazby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="59255-104">How to: Specify a Client Binding in Configuration</span></span>
<span data-ttu-id="59255-105">V tomto příkladu je aplikace konzoly klienta vytvořena pro použití služby kalkulačky a vazba pro tohoto klienta je v konfiguraci určena deklarativně.</span><span class="sxs-lookup"><span data-stu-id="59255-105">In this example, a client console application is created to use a calculator service, and the binding for that client is specified declaratively in configuration.</span></span> <span data-ttu-id="59255-106">Klient přistupuje k `CalculatorService` rozhraní, které implementuje `ICalculator` rozhraní a jak službu, tak i klient používající <xref:System.ServiceModel.BasicHttpBinding> třídu.</span><span class="sxs-lookup"><span data-stu-id="59255-106">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="59255-107">Tento postup předpokládá, že je spuštěná služba kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="59255-107">The procedure outlined assumes that the calculator service is running.</span></span> <span data-ttu-id="59255-108">Informace o tom, jak vytvořit službu, naleznete v tématu [How to: zadat vazbu služby v konfiguraci](how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="59255-108">For information about how to build the service, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="59255-109">Používá také nástroj pro dodávání [metadat (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) , který Windows Communication Foundation (WCF) poskytuje k automatickému generování komponent klienta.</span><span class="sxs-lookup"><span data-stu-id="59255-109">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) that Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="59255-110">Nástroj vygeneruje kód klienta a konfiguraci pro přístup ke službě.</span><span class="sxs-lookup"><span data-stu-id="59255-110">The tool generates the client code and configuration for accessing the service.</span></span>  
  
 <span data-ttu-id="59255-111">Klient je sestaven ve dvou částech.</span><span class="sxs-lookup"><span data-stu-id="59255-111">The client is built in two parts.</span></span> <span data-ttu-id="59255-112">Svcutil.exe generuje `ClientCalculator` rozhraní, které implementuje `ICalculator` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="59255-112">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="59255-113">Tato klientská aplikace je pak vytvořena konstrukcí instance `ClientCalculator` .</span><span class="sxs-lookup"><span data-stu-id="59255-113">This client application is then constructed by constructing an instance of `ClientCalculator`.</span></span>  
  
 <span data-ttu-id="59255-114">Obvykle je osvědčeným postupem zadat vazby a informace o adrese deklarativně v konfiguraci, nikoli imperativně v kódu.</span><span class="sxs-lookup"><span data-stu-id="59255-114">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="59255-115">Definování koncových bodů v kódu obvykle není praktické, protože vazby a adresy nasazené služby se obvykle liší od těch, které se použily při vývoji služby.</span><span class="sxs-lookup"><span data-stu-id="59255-115">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="59255-116">Obecně platí, že zachování vazby a adresování informací z kódu umožňuje jejich změnu bez nutnosti opětovné kompilace nebo opětovného nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="59255-116">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="59255-117">Pomocí [nástroje Editor konfigurací (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md)můžete provádět všechny následující konfigurační kroky.</span><span class="sxs-lookup"><span data-stu-id="59255-117">You can perform all of the following configuration steps by using the [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="59255-118">Zdrojovou kopii tohoto příkladu najdete v ukázce [BasicBinding](./samples/basicbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="59255-118">For the source copy of this example, see the [BasicBinding](./samples/basicbinding.md) sample.</span></span>  
  
### <a name="specifying-a-client-binding-in-configuration"></a><span data-ttu-id="59255-119">Určení vazby klienta v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="59255-119">Specifying a client binding in configuration</span></span>  
  
1. <span data-ttu-id="59255-120">K vygenerování kódu z metadat služby použijte Svcutil.exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="59255-120">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="59255-121">Vygenerovaný klient obsahuje `ICalculator` rozhraní, které definuje kontrakt služby, který musí implementace klienta splňovat.</span><span class="sxs-lookup"><span data-stu-id="59255-121">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3. <span data-ttu-id="59255-122">Vygenerovaný klient také obsahuje implementaci `ClientCalculator` .</span><span class="sxs-lookup"><span data-stu-id="59255-122">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4. <span data-ttu-id="59255-123">Svcutil.exe také generuje konfiguraci pro klienta, který používá <xref:System.ServiceModel.BasicHttpBinding> třídu.</span><span class="sxs-lookup"><span data-stu-id="59255-123">Svcutil.exe also generates the configuration for the client that uses the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span> <span data-ttu-id="59255-124">Při použití sady Visual Studio pojmenujte tento soubor App.config. Všimněte si, že informace o adrese a vazbě nejsou zadány kamkoli v rámci implementace služby.</span><span class="sxs-lookup"><span data-stu-id="59255-124">When using Visual Studio, name this file App.config. Note that the address and binding information are not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="59255-125">Také není nutné zapisovat kód pro načtení těchto informací z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="59255-125">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]

5. <span data-ttu-id="59255-126">Vytvořte instanci `ClientCalculator` v aplikaci a potom zavolejte operace služby.</span><span class="sxs-lookup"><span data-stu-id="59255-126">Create an instance of the `ClientCalculator` in an application, and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6. <span data-ttu-id="59255-127">Zkompilujte a spusťte klienta.</span><span class="sxs-lookup"><span data-stu-id="59255-127">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59255-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="59255-128">See also</span></span>

- [<span data-ttu-id="59255-129">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="59255-129">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
