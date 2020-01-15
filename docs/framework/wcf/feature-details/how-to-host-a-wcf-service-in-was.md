---
title: 'Postupy: Hostování služby WCF ve WAS'
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: 9945e398bbd33776cce808b44388a4415da297a1
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964775"
---
# <a name="how-to-host-a-wcf-service-in-was"></a><span data-ttu-id="329b7-102">Postupy: Hostování služby WCF ve WAS</span><span class="sxs-lookup"><span data-stu-id="329b7-102">How to: Host a WCF Service in WAS</span></span>
<span data-ttu-id="329b7-103">Toto téma popisuje základní kroky potřebné k vytvoření služby Aktivace procesů systému Windows (označované také jako) hostované služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="329b7-103">This topic outlines the basic steps required to create a Windows Process Activation Services (also known as WAS) hosted Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="329b7-104">BYLA Nová aktivační služba procesů, která je generalizací funkcí služby Internetová informační služba (IIS), které fungují s protokoly přenosů bez protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="329b7-104">WAS is the new process activation service that is a generalization of Internet Information Services (IIS) features that work with non-HTTP transport protocols.</span></span> <span data-ttu-id="329b7-105">Služba WCF používá rozhraní naslouchacího adaptéru ke komunikaci s požadavky na aktivaci, které jsou přijímány prostřednictvím protokolů jiných než HTTP podporovaných službou WCF, jako je například TCP, pojmenované kanály a služba Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="329b7-105">WCF uses the listener adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by WCF, such as TCP, named pipes, and Message Queuing.</span></span>  
  
 <span data-ttu-id="329b7-106">Tato možnost hostování vyžaduje, aby byly aktivační komponenty správně nainstalované a nakonfigurované, ale nevyžadují, aby se v rámci aplikace napsal žádný hostující kód.</span><span class="sxs-lookup"><span data-stu-id="329b7-106">This hosting option requires that WAS activation components are properly installed and configured, but it does not require any hosting code to be written as part of the application.</span></span> <span data-ttu-id="329b7-107">Další informace o instalaci a konfiguraci nástroje najdete v tématu [Postupy: instalace a konfigurace aktivačních komponent WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span><span class="sxs-lookup"><span data-stu-id="329b7-107">For more information about installing and configuring WAS, see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="329b7-108">Aktivace byla Nepodporovaná, pokud je kanál pro zpracování požadavků webového serveru nastavený na klasický režim.</span><span class="sxs-lookup"><span data-stu-id="329b7-108">WAS activation is not supported if the web server’s request processing pipeline is set to Classic mode.</span></span> <span data-ttu-id="329b7-109">Pokud byla použita aktivace, musí být kanál zpracování požadavků webového serveru nastaven na integrovaný režim.</span><span class="sxs-lookup"><span data-stu-id="329b7-109">The web server’s request processing pipeline must be set to Integrated mode if WAS activation is to be used.</span></span>  
  
 <span data-ttu-id="329b7-110">Když je služba WCF hostována v nástroji, používají se standardní vazby obvyklým způsobem.</span><span class="sxs-lookup"><span data-stu-id="329b7-110">When a WCF service is hosted in WAS, the standard bindings are used in the usual way.</span></span> <span data-ttu-id="329b7-111">Při použití <xref:System.ServiceModel.NetTcpBinding> a <xref:System.ServiceModel.NetNamedPipeBinding> ke konfiguraci služby, která byla hostovaná, ale musí být splněno omezení.</span><span class="sxs-lookup"><span data-stu-id="329b7-111">However, when using the <xref:System.ServiceModel.NetTcpBinding> and the <xref:System.ServiceModel.NetNamedPipeBinding> to configure a WAS-hosted service, a constraint must be satisfied.</span></span> <span data-ttu-id="329b7-112">Pokud různé koncové body používají stejný přenos, nastavení vazby musí odpovídat následující sedm vlastností:</span><span class="sxs-lookup"><span data-stu-id="329b7-112">When different endpoints use the same transport, the binding settings have to match on the following seven properties:</span></span>  
  
- <span data-ttu-id="329b7-113">connectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="329b7-113">ConnectionBufferSize</span></span>  
  
- <span data-ttu-id="329b7-114">channelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="329b7-114">ChannelInitializationTimeout</span></span>  
  
- <span data-ttu-id="329b7-115">MaxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="329b7-115">MaxPendingConnections</span></span>  
  
- <span data-ttu-id="329b7-116">MaxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="329b7-116">MaxOutputDelay</span></span>  
  
- <span data-ttu-id="329b7-117">MaxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="329b7-117">MaxPendingAccepts</span></span>  
  
- <span data-ttu-id="329b7-118">ConnectionPoolSettings.IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="329b7-118">ConnectionPoolSettings.IdleTimeout</span></span>  
  
- <span data-ttu-id="329b7-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="329b7-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span></span>  
  
 <span data-ttu-id="329b7-120">V opačném případě bude koncový bod, který se inicializuje jako první, určit hodnoty těchto vlastností a koncové body přidané později vyvolají <xref:System.ServiceModel.ServiceActivationException>, pokud se neshodují s těmito nastaveními.</span><span class="sxs-lookup"><span data-stu-id="329b7-120">Otherwise, the endpoint that is initialized first always determines the values of these properties, and endpoints added later throw a <xref:System.ServiceModel.ServiceActivationException> if they do not match those settings.</span></span>  
  
 <span data-ttu-id="329b7-121">Zdrojovou kopii tohoto příkladu najdete v tématu [Aktivace protokolem TCP](../../../../docs/framework/wcf/samples/tcp-activation.md).</span><span class="sxs-lookup"><span data-stu-id="329b7-121">For the source copy of this example, see [TCP Activation](../../../../docs/framework/wcf/samples/tcp-activation.md).</span></span>  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a><span data-ttu-id="329b7-122">Vytvoření základní služby hostované nástrojem WAS</span><span class="sxs-lookup"><span data-stu-id="329b7-122">To create a basic service hosted by WAS</span></span>  
  
1. <span data-ttu-id="329b7-123">Definujte kontrakt služby pro typ služby.</span><span class="sxs-lookup"><span data-stu-id="329b7-123">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2. <span data-ttu-id="329b7-124">Implementujte kontrakt služby ve třídě služby.</span><span class="sxs-lookup"><span data-stu-id="329b7-124">Implement the service contract in a service class.</span></span> <span data-ttu-id="329b7-125">Všimněte si, že v rámci implementace služby není zadaná adresa nebo informace o vazbě.</span><span class="sxs-lookup"><span data-stu-id="329b7-125">Note that address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="329b7-126">Také není nutné zapisovat kód pro načtení těchto informací z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="329b7-126">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3. <span data-ttu-id="329b7-127">Vytvořte soubor Web. config a definujte <xref:System.ServiceModel.NetTcpBinding> vazby, které budou použity koncovými body `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="329b7-127">Create a Web.config file to define the <xref:System.ServiceModel.NetTcpBinding> binding to be used by the `CalculatorService` endpoints.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <bindings>  
          <netTcpBinding>  
            <binding portSharingEnabled="true">  
              <security mode="None" />  
            </binding>  
          </netTcpBinding>  
        </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4. <span data-ttu-id="329b7-128">Vytvořte soubor Service. svc, který obsahuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="329b7-128">Create a Service.svc file that contains the following code.</span></span>  
  
   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```
  
5. <span data-ttu-id="329b7-129">Umístěte soubor Service. svc do virtuálního adresáře služby IIS.</span><span class="sxs-lookup"><span data-stu-id="329b7-129">Place the Service.svc file in your IIS virtual directory.</span></span>  
  
### <a name="to-create-a-client-to-use-the-service"></a><span data-ttu-id="329b7-130">Vytvoření klienta pro používání služby</span><span class="sxs-lookup"><span data-stu-id="329b7-130">To create a client to use the service</span></span>  
  
1. <span data-ttu-id="329b7-131">K vygenerování kódu z metadat služby použijte [Nástroj Svcutil. exe (s metadaty ServiceModel)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="329b7-131">Use [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>  
  
    ```console
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="329b7-132">Vygenerovaný klient obsahuje rozhraní `ICalculator` definující kontrakt služby, který musí implementace klienta splňovat.</span><span class="sxs-lookup"><span data-stu-id="329b7-132">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3. <span data-ttu-id="329b7-133">Vygenerovaná klientská aplikace obsahuje také implementaci `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="329b7-133">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="329b7-134">Všimněte si, že informace o adrese a vazbě nejsou zadány kamkoli v rámci implementace služby.</span><span class="sxs-lookup"><span data-stu-id="329b7-134">Note that the address and binding information is not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="329b7-135">Také není nutné zapisovat kód pro načtení těchto informací z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="329b7-135">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4. <span data-ttu-id="329b7-136">Konfigurace klienta, který používá <xref:System.ServiceModel.NetTcpBinding>, je vygenerována také nástrojem Svcutil. exe.</span><span class="sxs-lookup"><span data-stu-id="329b7-136">The configuration for the client that uses the <xref:System.ServiceModel.NetTcpBinding> is also generated by Svcutil.exe.</span></span> <span data-ttu-id="329b7-137">Tento soubor by měl být pojmenován v souboru App. config při použití sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="329b7-137">This file should be named in the App.config file when using Visual Studio.</span></span>  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]   
  
5. <span data-ttu-id="329b7-138">Vytvořte v aplikaci instanci `ClientCalculator` a potom zavolejte operace služby.</span><span class="sxs-lookup"><span data-stu-id="329b7-138">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6. <span data-ttu-id="329b7-139">Zkompilujte a spusťte klienta.</span><span class="sxs-lookup"><span data-stu-id="329b7-139">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="329b7-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="329b7-140">See also</span></span>

- [<span data-ttu-id="329b7-141">Aktivace protokolu TCP</span><span class="sxs-lookup"><span data-stu-id="329b7-141">TCP Activation</span></span>](../../../../docs/framework/wcf/samples/tcp-activation.md)
- <span data-ttu-id="329b7-142">[Funkce hostování technologie Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="329b7-142">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
