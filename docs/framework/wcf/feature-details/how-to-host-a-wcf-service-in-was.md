---
title: 'Postupy: Hostování služby WCF ve WAS'
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: 7050d866233b248c7c8f9f41337ce451b5510c30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492665"
---
# <a name="how-to-host-a-wcf-service-in-was"></a><span data-ttu-id="8b929-102">Postupy: Hostování služby WCF ve WAS</span><span class="sxs-lookup"><span data-stu-id="8b929-102">How to: Host a WCF Service in WAS</span></span>
<span data-ttu-id="8b929-103">Toto téma obsahuje přehled základní kroky potřebné pro vytvoření služby Aktivace procesů systému Windows (WAS) hostovaná služba Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="8b929-103">This topic outlines the basic steps required to create a Windows Process Activation Services (also known as WAS) hosted Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="8b929-104">BYL je nová služba aktivace procesů, která je generalizace funkcí Internetové informační služby (IIS), které pracují s jiným protokolem než HTTP přenosové protokoly.</span><span class="sxs-lookup"><span data-stu-id="8b929-104">WAS is the new process activation service that is a generalization of Internet Information Services (IIS) features that work with non-HTTP transport protocols.</span></span> <span data-ttu-id="8b929-105">WCF používá rozhraní adaptér naslouchání pro komunikaci žádosti o aktivaci, které jsou přijaty prostřednictvím protokolů než HTTP nepodporuje WCF, jako je například TCP, pojmenované kanály a služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="8b929-105">WCF uses the listener adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by WCF, such as TCP, named pipes, and Message Queuing.</span></span>  
  
 <span data-ttu-id="8b929-106">Tato hostování možnost vyžaduje součásti aktivace WAS správně nainstalován a nakonfigurován, ale nevyžaduje žádné hostování kódu má být zapsán v rámci aplikace.</span><span class="sxs-lookup"><span data-stu-id="8b929-106">This hosting option requires that WAS activation components are properly installed and configured, but it does not require any hosting code to be written as part of the application.</span></span> <span data-ttu-id="8b929-107">Další informace o instalaci a konfiguraci WAS najdete v tématu [postupy: instalace a konfigurace aktivačních komponent WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span><span class="sxs-lookup"><span data-stu-id="8b929-107">For more information about installing and configuring WAS, see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="8b929-108">BYLA aktivace není podporováno, pokud kanál pro zpracování požadavku webový server je nastaven na klasickém režimu.</span><span class="sxs-lookup"><span data-stu-id="8b929-108">WAS activation is not supported if the web server’s request processing pipeline is set to Classic mode.</span></span> <span data-ttu-id="8b929-109">Kanál pro zpracování požadavku webový server musí být nastavena pro integrovaný režim, pokud je aktivace WAS pro použití.</span><span class="sxs-lookup"><span data-stu-id="8b929-109">The web server’s request processing pipeline must be set to Integrated mode if WAS activation is to be used.</span></span>  
  
 <span data-ttu-id="8b929-110">Při je hostování služby WCF ve WAS se používají standardní vazby obvyklým způsobem.</span><span class="sxs-lookup"><span data-stu-id="8b929-110">When a WCF service is hosted in WAS, the standard bindings are used in the usual way.</span></span> <span data-ttu-id="8b929-111">Ale při použití <xref:System.ServiceModel.NetTcpBinding> a <xref:System.ServiceModel.NetNamedPipeBinding> konfigurace WAS hostované služby, je nutné splnit omezení.</span><span class="sxs-lookup"><span data-stu-id="8b929-111">However, when using the <xref:System.ServiceModel.NetTcpBinding> and the <xref:System.ServiceModel.NetNamedPipeBinding> to configure a WAS-hosted service, a constraint must be satisfied.</span></span> <span data-ttu-id="8b929-112">Když různými koncovými body používají stejné přenos, závazné nastavení se tak, aby odpovídala na sedm následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="8b929-112">When different endpoints use the same transport, the binding settings have to match on the following seven properties:</span></span>  
  
-   <span data-ttu-id="8b929-113">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="8b929-113">ConnectionBufferSize</span></span>  
  
-   <span data-ttu-id="8b929-114">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="8b929-114">ChannelInitializationTimeout</span></span>  
  
-   <span data-ttu-id="8b929-115">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="8b929-115">MaxPendingConnections</span></span>  
  
-   <span data-ttu-id="8b929-116">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="8b929-116">MaxOutputDelay</span></span>  
  
-   <span data-ttu-id="8b929-117">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="8b929-117">MaxPendingAccepts</span></span>  
  
-   <span data-ttu-id="8b929-118">ConnectionPoolSettings.IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="8b929-118">ConnectionPoolSettings.IdleTimeout</span></span>  
  
-   <span data-ttu-id="8b929-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="8b929-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span></span>  
  
 <span data-ttu-id="8b929-120">Jinak koncového bodu, který je inicializován nejdřív vždy zjistí hodnoty těchto vlastností a výjimku později přidat koncové body <xref:System.ServiceModel.ServiceActivationException> Pokud tato nastavení nejsou shodné.</span><span class="sxs-lookup"><span data-stu-id="8b929-120">Otherwise, the endpoint that is initialized first always determines the values of these properties, and endpoints added later throw a <xref:System.ServiceModel.ServiceActivationException> if they do not match those settings.</span></span>  
  
 <span data-ttu-id="8b929-121">Zdroj kopírování tohoto příkladu, najdete v části [Aktivace protokolem TCP](../../../../docs/framework/wcf/samples/tcp-activation.md).</span><span class="sxs-lookup"><span data-stu-id="8b929-121">For the source copy of this example, see [TCP Activation](../../../../docs/framework/wcf/samples/tcp-activation.md).</span></span>  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a><span data-ttu-id="8b929-122">Chcete-li vytvořit základní služba hostovaná společností WAS</span><span class="sxs-lookup"><span data-stu-id="8b929-122">To create a basic service hosted by WAS</span></span>  
  
1.  <span data-ttu-id="8b929-123">Definování kontraktu služby pro typ služby.</span><span class="sxs-lookup"><span data-stu-id="8b929-123">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2.  <span data-ttu-id="8b929-124">Implementujte kontrakt služby v třídě služby.</span><span class="sxs-lookup"><span data-stu-id="8b929-124">Implement the service contract in a service class.</span></span> <span data-ttu-id="8b929-125">Všimněte si, že není adresu nebo vazba informace zadat v rámci implementace služby.</span><span class="sxs-lookup"><span data-stu-id="8b929-125">Note that address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="8b929-126">Kód také nemá k zapsání k načtení těchto informací z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="8b929-126">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3.  <span data-ttu-id="8b929-127">Vytvořte soubor Web.config k definování <xref:System.ServiceModel.NetTcpBinding> vazby má být používána `CalculatorService` koncové body.</span><span class="sxs-lookup"><span data-stu-id="8b929-127">Create a Web.config file to define the <xref:System.ServiceModel.NetTcpBinding> binding to be used by the `CalculatorService` endpoints.</span></span>  
  
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
  
4.  <span data-ttu-id="8b929-128">Vytvořte soubor Service.svc, který obsahuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="8b929-128">Create a Service.svc file that contains the following code.</span></span>  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
5.  <span data-ttu-id="8b929-129">Umístěte soubor Service.svc virtuální adresáře služby IIS.</span><span class="sxs-lookup"><span data-stu-id="8b929-129">Place the Service.svc file in your IIS virtual directory.</span></span>  
  
### <a name="to-create-a-client-to-use-the-service"></a><span data-ttu-id="8b929-130">Chcete-li vytvořit klienta k využití služby</span><span class="sxs-lookup"><span data-stu-id="8b929-130">To create a client to use the service</span></span>  
  
1.  <span data-ttu-id="8b929-131">Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z příkazového řádku pro generování kódu z metadat služby.</span><span class="sxs-lookup"><span data-stu-id="8b929-131">Use [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  <span data-ttu-id="8b929-132">Obsahuje klienta, který se generuje `ICalculator` rozhraní, které definuje kontrakt služby, které musí splňovat implementace klienta.</span><span class="sxs-lookup"><span data-stu-id="8b929-132">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3.  <span data-ttu-id="8b929-133">Generovaného klienta aplikace také obsahuje implementace `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="8b929-133">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="8b929-134">Všimněte si, že informace o adrese a vazba není zadán kdekoli uvnitř implementace služby.</span><span class="sxs-lookup"><span data-stu-id="8b929-134">Note that the address and binding information is not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="8b929-135">Kód také nemá k zapsání k načtení těchto informací z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="8b929-135">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4.  <span data-ttu-id="8b929-136">Konfigurace pro klienta, který používá <xref:System.ServiceModel.NetTcpBinding> je také generován Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="8b929-136">The configuration for the client that uses the <xref:System.ServiceModel.NetTcpBinding> is also generated by Svcutil.exe.</span></span> <span data-ttu-id="8b929-137">Tento soubor má název v souboru App.config, když pomocí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8b929-137">This file should be named in the App.config file when using Visual Studio.</span></span>  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]   
  
5.  <span data-ttu-id="8b929-138">Vytvoření instance `ClientCalculator` v aplikaci a pak volání operací služby.</span><span class="sxs-lookup"><span data-stu-id="8b929-138">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6.  <span data-ttu-id="8b929-139">Zkompilování a spuštění klienta.</span><span class="sxs-lookup"><span data-stu-id="8b929-139">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b929-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b929-140">See Also</span></span>  
 [<span data-ttu-id="8b929-141">Aktivace protokolu TCP</span><span class="sxs-lookup"><span data-stu-id="8b929-141">TCP Activation</span></span>](../../../../docs/framework/wcf/samples/tcp-activation.md)  
 [<span data-ttu-id="8b929-142">Hostování funkcí systému Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="8b929-142">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
