---
title: 'Postupy: Zadání klientské vazby v konfiguraci'
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: 2441b307961079c28e114b4fed69c252ff42e0d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606384"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a><span data-ttu-id="5bb09-102">Postupy: Zadání klientské vazby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="5bb09-102">How to: Specify a Client Binding in Configuration</span></span>
<span data-ttu-id="5bb09-103">V tomto příkladu se vytvoří konzolovou aplikaci klienta pro použití kalkulačky služby a vazby pro tohoto klienta je deklarativně zadaný v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="5bb09-103">In this example, a client console application is created to use a calculator service, and the binding for that client is specified declaratively in configuration.</span></span> <span data-ttu-id="5bb09-104">Klient přistupuje k `CalculatorService`, která implementuje `ICalculator` rozhraní a službě i klientovi použít <xref:System.ServiceModel.BasicHttpBinding> třídy.</span><span class="sxs-lookup"><span data-stu-id="5bb09-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="5bb09-105">Podle uvedeného postupu se předpokládá, že je spuštěna služba kalkulačku.</span><span class="sxs-lookup"><span data-stu-id="5bb09-105">The procedure outlined assumes that the calculator service is running.</span></span> <span data-ttu-id="5bb09-106">Informace o tom, jak sestavit službu, naleznete v tématu [jak: Zadání vazby služby v konfiguraci](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="5bb09-106">For information about how to build the service, see [How to: Specify a Service Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="5bb09-107">Využívá také [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) , Windows Communication Foundation (WCF) poskytuje klientské součásti budou automaticky generovány.</span><span class="sxs-lookup"><span data-stu-id="5bb09-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) that Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="5bb09-108">Nástroj vygeneruje kód klienta a konfigurace přístupu ke službě.</span><span class="sxs-lookup"><span data-stu-id="5bb09-108">The tool generates the client code and configuration for accessing the service.</span></span>  
  
 <span data-ttu-id="5bb09-109">Klient je vytvořená ve dvou částech.</span><span class="sxs-lookup"><span data-stu-id="5bb09-109">The client is built in two parts.</span></span> <span data-ttu-id="5bb09-110">Generuje svcutil.exe `ClientCalculator` , který implementuje `ICalculator` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5bb09-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="5bb09-111">Tato klientská aplikace pak konstruován tak, že vytváří instanci `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="5bb09-111">This client application is then constructed by constructing an instance of `ClientCalculator`.</span></span>  
  
 <span data-ttu-id="5bb09-112">Obvykle je osvědčeným postupem určete vazbu a informace o adrese deklarativně v konfiguraci, nikoli imperativně v kódu.</span><span class="sxs-lookup"><span data-stu-id="5bb09-112">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="5bb09-113">Definování koncových bodů v kódu není obvykle praktické protože vazeb a adresy pro službu nasazenou se obvykle liší od nastavení použít, je vyvíjena služby.</span><span class="sxs-lookup"><span data-stu-id="5bb09-113">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="5bb09-114">Obecně platí udržování vazby a adresování informace mimo kód jim umožňuje změnit bez nutnosti znovu kompilovat nebo znovu nasadit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5bb09-114">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="5bb09-115">Všechny následující kroky konfigurace můžete provádět pomocí [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5bb09-115">You can perform all of the following configuration steps by using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="5bb09-116">Pro zdrojovou kopii tohoto příkladu, najdete v článku [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="5bb09-116">For the source copy of this example, see the [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) sample.</span></span>  
  
### <a name="specifying-a-client-binding-in-configuration"></a><span data-ttu-id="5bb09-117">Zadání klientské vazby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="5bb09-117">Specifying a client binding in configuration</span></span>  
  
1.  <span data-ttu-id="5bb09-118">Pomocí Svcutil.exe lze generovat kód z metadat služby z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="5bb09-118">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  <span data-ttu-id="5bb09-119">Klient, který je generován obsahuje `ICalculator` rozhraní, které definuje kontrakt služby, který musí splňovat implementace klienta.</span><span class="sxs-lookup"><span data-stu-id="5bb09-119">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3.  <span data-ttu-id="5bb09-120">Také obsahuje implementaci generovaného klienta `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="5bb09-120">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4.  <span data-ttu-id="5bb09-121">Svcutil.exe také generuje konfiguraci pro klienta, který se používá <xref:System.ServiceModel.BasicHttpBinding> třídy.</span><span class="sxs-lookup"><span data-stu-id="5bb09-121">Svcutil.exe also generates the configuration for the client that uses the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span> <span data-ttu-id="5bb09-122">Když pomocí sady Visual Studio, název tohoto souboru App.config. Všimněte si, že adresa a informace o vazbě nejsou zadané kdekoli uvnitř implementace služby.</span><span class="sxs-lookup"><span data-stu-id="5bb09-122">When using Visual Studio, name this file App.config. Note that the address and binding information are not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="5bb09-123">Kód také, není nutné zapsat, aby načítal příslušné informace z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="5bb09-123">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]   
            
5.  <span data-ttu-id="5bb09-124">Vytvoření instance `ClientCalculator` v aplikaci a potom volání operací služby.</span><span class="sxs-lookup"><span data-stu-id="5bb09-124">Create an instance of the `ClientCalculator` in an application, and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6.  <span data-ttu-id="5bb09-125">Kompilace a spuštění klienta.</span><span class="sxs-lookup"><span data-stu-id="5bb09-125">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bb09-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5bb09-126">See also</span></span>
- [<span data-ttu-id="5bb09-127">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="5bb09-127">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
