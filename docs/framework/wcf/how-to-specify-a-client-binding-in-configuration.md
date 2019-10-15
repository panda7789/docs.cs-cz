---
title: 'Postupy: Zadání klientské vazby v konfiguraci'
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: b16f4b062f7f97a5855b06bdcf348911ee0497d2
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320865"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a><span data-ttu-id="665cf-102">Postupy: Zadání klientské vazby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="665cf-102">How to: Specify a Client Binding in Configuration</span></span>
<span data-ttu-id="665cf-103">V tomto příkladu je aplikace konzoly klienta vytvořena pro použití služby kalkulačky a vazba pro tohoto klienta je v konfiguraci určena deklarativně.</span><span class="sxs-lookup"><span data-stu-id="665cf-103">In this example, a client console application is created to use a calculator service, and the binding for that client is specified declaratively in configuration.</span></span> <span data-ttu-id="665cf-104">Klient přistupuje k `CalculatorService`, který implementuje rozhraní `ICalculator` a jak službu, tak i klient používající třídu <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="665cf-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="665cf-105">Tento postup předpokládá, že je spuštěná služba kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="665cf-105">The procedure outlined assumes that the calculator service is running.</span></span> <span data-ttu-id="665cf-106">Informace o tom, jak vytvořit službu, naleznete v tématu [How to: zadat vazbu služby v konfiguraci](how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="665cf-106">For information about how to build the service, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="665cf-107">Používá taky Nástroj pro dodávání [metadat (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) , který Windows Communication Foundation (WCF) poskytuje k automatickému generování komponent klienta.</span><span class="sxs-lookup"><span data-stu-id="665cf-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) that Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="665cf-108">Nástroj vygeneruje kód klienta a konfiguraci pro přístup ke službě.</span><span class="sxs-lookup"><span data-stu-id="665cf-108">The tool generates the client code and configuration for accessing the service.</span></span>  
  
 <span data-ttu-id="665cf-109">Klient je sestaven ve dvou částech.</span><span class="sxs-lookup"><span data-stu-id="665cf-109">The client is built in two parts.</span></span> <span data-ttu-id="665cf-110">Svcutil. exe vygeneruje `ClientCalculator`, který implementuje rozhraní `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="665cf-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="665cf-111">Tato klientská aplikace je pak vytvořena konstrukcí instance `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="665cf-111">This client application is then constructed by constructing an instance of `ClientCalculator`.</span></span>  
  
 <span data-ttu-id="665cf-112">Obvykle je osvědčeným postupem zadat vazby a informace o adrese deklarativně v konfiguraci, nikoli imperativně v kódu.</span><span class="sxs-lookup"><span data-stu-id="665cf-112">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="665cf-113">Definování koncových bodů v kódu obvykle není praktické, protože vazby a adresy nasazené služby se obvykle liší od těch, které se použily při vývoji služby.</span><span class="sxs-lookup"><span data-stu-id="665cf-113">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="665cf-114">Obecně platí, že zachování vazby a adresování informací z kódu umožňuje jejich změnu bez nutnosti opětovné kompilace nebo opětovného nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="665cf-114">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="665cf-115">Pomocí [nástroje Editor konfigurací (SvcConfigEditor. exe)](configuration-editor-tool-svcconfigeditor-exe.md)můžete provádět všechny následující konfigurační kroky.</span><span class="sxs-lookup"><span data-stu-id="665cf-115">You can perform all of the following configuration steps by using the [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="665cf-116">Zdrojovou kopii tohoto příkladu najdete v ukázce [BasicBinding](./samples/basicbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="665cf-116">For the source copy of this example, see the [BasicBinding](./samples/basicbinding.md) sample.</span></span>  
  
### <a name="specifying-a-client-binding-in-configuration"></a><span data-ttu-id="665cf-117">Určení vazby klienta v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="665cf-117">Specifying a client binding in configuration</span></span>  
  
1. <span data-ttu-id="665cf-118">K vygenerování kódu z metadat služby použijte Svcutil. exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="665cf-118">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. <span data-ttu-id="665cf-119">Vygenerovaný klient obsahuje rozhraní `ICalculator` definující kontrakt služby, který musí implementace klienta splňovat.</span><span class="sxs-lookup"><span data-stu-id="665cf-119">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3. <span data-ttu-id="665cf-120">Vygenerovaný klient obsahuje také implementaci `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="665cf-120">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4. <span data-ttu-id="665cf-121">Svcutil. exe také generuje konfiguraci pro klienta, který používá třídu <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="665cf-121">Svcutil.exe also generates the configuration for the client that uses the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span> <span data-ttu-id="665cf-122">Při použití sady Visual Studio pojmenujte tento soubor App. config. Všimněte si, že informace o adrese a vazbě nejsou zadány kamkoli v rámci implementace služby.</span><span class="sxs-lookup"><span data-stu-id="665cf-122">When using Visual Studio, name this file App.config. Note that the address and binding information are not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="665cf-123">Také není nutné zapisovat kód pro načtení těchto informací z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="665cf-123">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]   
            
5. <span data-ttu-id="665cf-124">Vytvořte v aplikaci instanci `ClientCalculator` a potom zavolejte operace služby.</span><span class="sxs-lookup"><span data-stu-id="665cf-124">Create an instance of the `ClientCalculator` in an application, and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6. <span data-ttu-id="665cf-125">Zkompilujte a spusťte klienta.</span><span class="sxs-lookup"><span data-stu-id="665cf-125">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="665cf-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="665cf-126">See also</span></span>

- [<span data-ttu-id="665cf-127">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="665cf-127">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
