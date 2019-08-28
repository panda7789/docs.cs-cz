---
title: Zjednodušená konfigurace pro služby WCF
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: 57aa92eb0a2978ab463c368ed70fb298cc5fb90d
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038862"
---
# <a name="simplified-configuration-for-wcf-services"></a><span data-ttu-id="79395-102">Zjednodušená konfigurace pro služby WCF</span><span class="sxs-lookup"><span data-stu-id="79395-102">Simplified Configuration for WCF Services</span></span>
<span data-ttu-id="79395-103">Tato ukázka předvádí, jak implementovat a nakonfigurovat typickou službu a klienta pomocí Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="79395-103">This sample demonstrates how to implement and configure a typical service and client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="79395-104">Tato ukázka je základem pro všechny ostatní základní ukázkové technologie.</span><span class="sxs-lookup"><span data-stu-id="79395-104">This sample is the basis for all other basic technology samples.</span></span>  
  
 <span data-ttu-id="79395-105">Tato služba, která zpřístupňuje koncový bod pro komunikaci se službou, používá zjednodušenou konfiguraci v [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]nástroji.</span><span class="sxs-lookup"><span data-stu-id="79395-105">This service, which exposes an endpoint for communicating with the service, uses the simplified configuration in [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].</span></span> <span data-ttu-id="79395-106">[!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]Před verzí je koncový bod obvykle definován v konfiguračním souboru (Web. config), jak je znázorněno v následujícím příkladu kódu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="79395-106">Prior to [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], the endpoint is typically defined in a configuration file (Web.config), as shown in the following example configuration code.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright ©) Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Samples.GettingStarted.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <endpoint address="" binding="basicHttpBinding" contract="ICalculator"/>  
        <endpoint address="mex" binding="mexHttpBinding" contract="IMetadataExchange"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="79395-107">V [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]nástrojije elementvolitelný.`<service>`</span><span class="sxs-lookup"><span data-stu-id="79395-107">In [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], the `<service>` element is optional.</span></span> <span data-ttu-id="79395-108">Pokud služba nedefinuje žádné koncové body, do služby se přidají koncový bod pro každou základní adresu a implementaci smlouvy.</span><span class="sxs-lookup"><span data-stu-id="79395-108">When a service does not define any endpoints, an endpoint for each base address and contract implemented are added to the service.</span></span> <span data-ttu-id="79395-109">Základní adresa se připojí k názvu kontraktu a určí koncový bod a vazba je určena schématem adres.</span><span class="sxs-lookup"><span data-stu-id="79395-109">The base address is appended to the contract name to determine the endpoint and the binding is determined by the address scheme.</span></span> <span data-ttu-id="79395-110">Následující příklad kódu ukazuje zjednodušený konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="79395-110">The following code example demonstrates a simplified configuration file.</span></span> <span data-ttu-id="79395-111">Jak je nakonfigurováno, může být služba k `http://localhost/servicemodelsamples/service.svc` dispozici klientovi ve stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="79395-111">As configured, the service can be accessed at `http://localhost/servicemodelsamples/service.svc` by a client on the same computer.</span></span> <span data-ttu-id="79395-112">Aby mohli klienti na vzdálených počítačích přistupovat ke službě, je třeba zadat plně kvalifikovaný název domény namísto localhost.</span><span class="sxs-lookup"><span data-stu-id="79395-112">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span> <span data-ttu-id="79395-113">Služba ve výchozím nastavení nevystavuje metadata.</span><span class="sxs-lookup"><span data-stu-id="79395-113">The service does not expose metadata by default.</span></span> <span data-ttu-id="79395-114">V takovém případě služba toto <xref:System.ServiceModel.Description.ServiceMetadataBehavior> chování zapne.</span><span class="sxs-lookup"><span data-stu-id="79395-114">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> behavior.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright © Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="79395-115">Použití této ukázky</span><span class="sxs-lookup"><span data-stu-id="79395-115">To use this sample</span></span>  
  
1. <span data-ttu-id="79395-116">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="79395-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="79395-117">Při sestavování řešení postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="79395-117">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="79395-118">Spusťte ukázku pomocí následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="79395-118">Run the sample by following these steps:</span></span>  
  
    1. <span data-ttu-id="79395-119">Klikněte pravým tlačítkem myši na projekt **služby** a vyberte **nastavit jako spouštěný projekt**a potom stiskněte klávesy **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="79395-119">Right click the **Service** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
    2. <span data-ttu-id="79395-120">Počkejte na výstup konzoly s potvrzením, že je služba spuštěná.</span><span class="sxs-lookup"><span data-stu-id="79395-120">Wait for the console output confirming that the service is up and running.</span></span>  
  
    3. <span data-ttu-id="79395-121">Klikněte pravým tlačítkem myši na projekt **klienta** a vyberte **nastavit jako spouštěný projekt**a potom stiskněte klávesy **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="79395-121">Right click the **Client** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="79395-122">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="79395-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="79395-123">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="79395-123">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="79395-124">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="79395-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="79395-125">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="79395-125">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a><span data-ttu-id="79395-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79395-126">See also</span></span>

- [<span data-ttu-id="79395-127">Ukázky správy technologie AppFabric</span><span class="sxs-lookup"><span data-stu-id="79395-127">AppFabric Management Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193960)
- [<span data-ttu-id="79395-128">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="79395-128">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)
