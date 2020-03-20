---
title: 'Postupy: Hostování služby WCF ve WAS'
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: 823c3b8452a3fd1c95758d2d09a9effdf02075c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184915"
---
# <a name="how-to-host-a-wcf-service-in-was"></a><span data-ttu-id="f9e90-102">Postupy: Hostování služby WCF ve WAS</span><span class="sxs-lookup"><span data-stu-id="f9e90-102">How to: Host a WCF Service in WAS</span></span>
<span data-ttu-id="f9e90-103">Toto téma popisuje základní kroky potřebné k vytvoření služby aktivace procesů systému Windows (označované také jako SLUŽBA WAS) hostované službou WCF (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="f9e90-103">This topic outlines the basic steps required to create a Windows Process Activation Services (also known as WAS) hosted Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="f9e90-104">WAS je nová služba aktivace procesů, která je generalizací funkcí Internetové informační služby (IIS), které pracují s přenosovými protokoly bez protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="f9e90-104">WAS is the new process activation service that is a generalization of Internet Information Services (IIS) features that work with non-HTTP transport protocols.</span></span> <span data-ttu-id="f9e90-105">WCF používá rozhraní adaptéru naslouchacího procesu ke komunikaci požadavků na aktivaci, které jsou přijímány prostřednictvím protokolů bez protokolu HTTP podporovaných protokoly WCF, jako je například TCP, pojmenované kanály a služba Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="f9e90-105">WCF uses the listener adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by WCF, such as TCP, named pipes, and Message Queuing.</span></span>  
  
 <span data-ttu-id="f9e90-106">Tato možnost hostování vyžaduje, aby byly aktivační součásti služby WAS správně nainstalovány a nakonfigurovány, ale nevyžaduje, aby byl jako součást aplikace zapsán žádný kód pro hostování.</span><span class="sxs-lookup"><span data-stu-id="f9e90-106">This hosting option requires that WAS activation components are properly installed and configured, but it does not require any hosting code to be written as part of the application.</span></span> <span data-ttu-id="f9e90-107">Další informace o instalaci a konfiguraci služby WAS naleznete v [tématu Postup: Instalace a konfigurace součástí aktivace WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span><span class="sxs-lookup"><span data-stu-id="f9e90-107">For more information about installing and configuring WAS, see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="f9e90-108">Aktivace služby WAS není podporována, pokud je kanál zpracování požadavků webového serveru nastaven na klasický režim.</span><span class="sxs-lookup"><span data-stu-id="f9e90-108">WAS activation is not supported if the web server’s request processing pipeline is set to Classic mode.</span></span> <span data-ttu-id="f9e90-109">Kanál zpracování požadavků webového serveru musí být nastaven na integrovaný režim, pokud má být použita aktivace služby WAS.</span><span class="sxs-lookup"><span data-stu-id="f9e90-109">The web server’s request processing pipeline must be set to Integrated mode if WAS activation is to be used.</span></span>  
  
 <span data-ttu-id="f9e90-110">Pokud je služba WCF hostována v WAS, standardní vazby se používají obvyklým způsobem.</span><span class="sxs-lookup"><span data-stu-id="f9e90-110">When a WCF service is hosted in WAS, the standard bindings are used in the usual way.</span></span> <span data-ttu-id="f9e90-111">Však při <xref:System.ServiceModel.NetTcpBinding> použití <xref:System.ServiceModel.NetNamedPipeBinding> a konfigurovat službu hostované was, omezení musí být splněna.</span><span class="sxs-lookup"><span data-stu-id="f9e90-111">However, when using the <xref:System.ServiceModel.NetTcpBinding> and the <xref:System.ServiceModel.NetNamedPipeBinding> to configure a WAS-hosted service, a constraint must be satisfied.</span></span> <span data-ttu-id="f9e90-112">Pokud různé koncové body používají stejný přenos, nastavení vazby musí odpovídat následujících sedm vlastností:</span><span class="sxs-lookup"><span data-stu-id="f9e90-112">When different endpoints use the same transport, the binding settings have to match on the following seven properties:</span></span>  
  
- <span data-ttu-id="f9e90-113">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="f9e90-113">ConnectionBufferSize</span></span>  
  
- <span data-ttu-id="f9e90-114">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="f9e90-114">ChannelInitializationTimeout</span></span>  
  
- <span data-ttu-id="f9e90-115">MaxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="f9e90-115">MaxPendingConnections</span></span>  
  
- <span data-ttu-id="f9e90-116">Zpoždění max.4.</span><span class="sxs-lookup"><span data-stu-id="f9e90-116">MaxOutputDelay</span></span>  
  
- <span data-ttu-id="f9e90-117">MaxPendingPřijímá</span><span class="sxs-lookup"><span data-stu-id="f9e90-117">MaxPendingAccepts</span></span>  
  
- <span data-ttu-id="f9e90-118">ConnectionPoolSettings.IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="f9e90-118">ConnectionPoolSettings.IdleTimeout</span></span>  
  
- <span data-ttu-id="f9e90-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="f9e90-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span></span>  
  
 <span data-ttu-id="f9e90-120">V opačném případě koncový bod, který je inicializován nejprve vždy určuje <xref:System.ServiceModel.ServiceActivationException> hodnoty těchto vlastností a koncové body přidané později vyvolat, pokud neodpovídají těmto nastavením.</span><span class="sxs-lookup"><span data-stu-id="f9e90-120">Otherwise, the endpoint that is initialized first always determines the values of these properties, and endpoints added later throw a <xref:System.ServiceModel.ServiceActivationException> if they do not match those settings.</span></span>  
  
 <span data-ttu-id="f9e90-121">Zdrojovou kopii tohoto příkladu naleznete v tématu [Aktivace protokolu TCP](../../../../docs/framework/wcf/samples/tcp-activation.md).</span><span class="sxs-lookup"><span data-stu-id="f9e90-121">For the source copy of this example, see [TCP Activation](../../../../docs/framework/wcf/samples/tcp-activation.md).</span></span>  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a><span data-ttu-id="f9e90-122">Vytvoření základní služby hostované společností WAS</span><span class="sxs-lookup"><span data-stu-id="f9e90-122">To create a basic service hosted by WAS</span></span>  
  
1. <span data-ttu-id="f9e90-123">Definujte servisní smlouvu pro typ služby.</span><span class="sxs-lookup"><span data-stu-id="f9e90-123">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2. <span data-ttu-id="f9e90-124">Implementujte servisní smlouvu ve třídě služeb.</span><span class="sxs-lookup"><span data-stu-id="f9e90-124">Implement the service contract in a service class.</span></span> <span data-ttu-id="f9e90-125">Všimněte si, že adresa nebo informace o vazbě není zadán v rámci provádění služby.</span><span class="sxs-lookup"><span data-stu-id="f9e90-125">Note that address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="f9e90-126">Kód také nemusí být zapsán, aby bylo možné načíst tyto informace z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="f9e90-126">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3. <span data-ttu-id="f9e90-127">Vytvořte soubor Web.config <xref:System.ServiceModel.NetTcpBinding> a definujte vazbu, kterou mají `CalculatorService` koncové body používat.</span><span class="sxs-lookup"><span data-stu-id="f9e90-127">Create a Web.config file to define the <xref:System.ServiceModel.NetTcpBinding> binding to be used by the `CalculatorService` endpoints.</span></span>  
  
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
  
4. <span data-ttu-id="f9e90-128">Vytvořte soubor Service.svc, který obsahuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="f9e90-128">Create a Service.svc file that contains the following code.</span></span>  
  
   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```
  
5. <span data-ttu-id="f9e90-129">Umístěte soubor Service.svc do virtuálního adresáře služby IIS.</span><span class="sxs-lookup"><span data-stu-id="f9e90-129">Place the Service.svc file in your IIS virtual directory.</span></span>  
  
### <a name="to-create-a-client-to-use-the-service"></a><span data-ttu-id="f9e90-130">Vytvoření klienta pro použití služby</span><span class="sxs-lookup"><span data-stu-id="f9e90-130">To create a client to use the service</span></span>  
  
1. <span data-ttu-id="f9e90-131">Nástroj [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z příkazového řádku slouží ke generování kódu z metadat služby.</span><span class="sxs-lookup"><span data-stu-id="f9e90-131">Use [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>  
  
    ```console
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="f9e90-132">Klient, který je generován `ICalculator` obsahuje rozhraní, které definuje servisní smlouvy, které implementace klienta musí splňovat.</span><span class="sxs-lookup"><span data-stu-id="f9e90-132">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3. <span data-ttu-id="f9e90-133">Vygenerovaná klientská aplikace `ClientCalculator`také obsahuje implementaci .</span><span class="sxs-lookup"><span data-stu-id="f9e90-133">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="f9e90-134">Všimněte si, že adresa a informace o vazbě není zadán nikde uvnitř implementace služby.</span><span class="sxs-lookup"><span data-stu-id="f9e90-134">Note that the address and binding information is not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="f9e90-135">Kód také nemusí být zapsán, aby bylo možné načíst tyto informace z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="f9e90-135">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4. <span data-ttu-id="f9e90-136">Konfigurace pro klienta, <xref:System.ServiceModel.NetTcpBinding> který používá je také generovánsvcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="f9e90-136">The configuration for the client that uses the <xref:System.ServiceModel.NetTcpBinding> is also generated by Svcutil.exe.</span></span> <span data-ttu-id="f9e90-137">Tento soubor by měl být pojmenován v souboru App.config při použití sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f9e90-137">This file should be named in the App.config file when using Visual Studio.</span></span>  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]
  
5. <span data-ttu-id="f9e90-138">Vytvořte instanci v aplikaci `ClientCalculator` a pak volejte operace služby.</span><span class="sxs-lookup"><span data-stu-id="f9e90-138">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6. <span data-ttu-id="f9e90-139">Zkompilujte a spusťte klienta.</span><span class="sxs-lookup"><span data-stu-id="f9e90-139">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9e90-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="f9e90-140">See also</span></span>

- [<span data-ttu-id="f9e90-141">Aktivace protokolu TCP</span><span class="sxs-lookup"><span data-stu-id="f9e90-141">TCP Activation</span></span>](../../../../docs/framework/wcf/samples/tcp-activation.md)
- <span data-ttu-id="f9e90-142">[Funkce hostování prostředků pro aplikace systému Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="f9e90-142">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
