---
title: Zjednodušená konfigurace pro služby WCF
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: d303d298ca45504968b4b37bd2835381b7e2eee5
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094901"
---
# <a name="simplified-configuration-for-wcf-services"></a><span data-ttu-id="759ab-102">Zjednodušená konfigurace pro služby WCF</span><span class="sxs-lookup"><span data-stu-id="759ab-102">Simplified Configuration for WCF Services</span></span>
<span data-ttu-id="759ab-103">Tato ukázka předvádí, jak implementovat a nakonfigurovat typickou službu a klienta pomocí Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="759ab-103">This sample demonstrates how to implement and configure a typical service and client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="759ab-104">Tato ukázka je základem pro všechny ostatní základní ukázkové technologie.</span><span class="sxs-lookup"><span data-stu-id="759ab-104">This sample is the basis for all other basic technology samples.</span></span>  
  
 <span data-ttu-id="759ab-105">Tato služba, která zpřístupňuje koncový bod pro komunikaci se službou, používá zjednodušenou konfiguraci v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="759ab-105">This service, which exposes an endpoint for communicating with the service, uses the simplified configuration in .NET Framework 4.</span></span> <span data-ttu-id="759ab-106">Před .NET Framework 4 je koncový bod obvykle definován v konfiguračním souboru (Web. config), jak je znázorněno v následujícím příkladu kódu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="759ab-106">Prior to .NET Framework 4, the endpoint is typically defined in a configuration file (Web.config), as shown in the following example configuration code.</span></span>  
  
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
  
 <span data-ttu-id="759ab-107">V .NET Framework 4 je prvek `<service>` volitelný.</span><span class="sxs-lookup"><span data-stu-id="759ab-107">In .NET Framework 4, the `<service>` element is optional.</span></span> <span data-ttu-id="759ab-108">Pokud služba nedefinuje žádné koncové body, do služby se přidají koncový bod pro každou základní adresu a implementaci smlouvy.</span><span class="sxs-lookup"><span data-stu-id="759ab-108">When a service does not define any endpoints, an endpoint for each base address and contract implemented are added to the service.</span></span> <span data-ttu-id="759ab-109">Základní adresa se připojí k názvu kontraktu a určí koncový bod a vazba je určena schématem adres.</span><span class="sxs-lookup"><span data-stu-id="759ab-109">The base address is appended to the contract name to determine the endpoint and the binding is determined by the address scheme.</span></span> <span data-ttu-id="759ab-110">Následující příklad kódu ukazuje zjednodušený konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="759ab-110">The following code example demonstrates a simplified configuration file.</span></span> <span data-ttu-id="759ab-111">Jak je nakonfigurováno, může být služba k dispozici na `http://localhost/servicemodelsamples/service.svc` klienta ve stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="759ab-111">As configured, the service can be accessed at `http://localhost/servicemodelsamples/service.svc` by a client on the same computer.</span></span> <span data-ttu-id="759ab-112">Aby mohli klienti na vzdálených počítačích přistupovat ke službě, je třeba zadat plně kvalifikovaný název domény namísto localhost.</span><span class="sxs-lookup"><span data-stu-id="759ab-112">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span> <span data-ttu-id="759ab-113">Služba ve výchozím nastavení nevystavuje metadata.</span><span class="sxs-lookup"><span data-stu-id="759ab-113">The service does not expose metadata by default.</span></span> <span data-ttu-id="759ab-114">V takovém případě služba zapne chování <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.</span><span class="sxs-lookup"><span data-stu-id="759ab-114">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> behavior.</span></span>  
  
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
  
### <a name="to-use-this-sample"></a><span data-ttu-id="759ab-115">Použití této ukázky</span><span class="sxs-lookup"><span data-stu-id="759ab-115">To use this sample</span></span>  
  
1. <span data-ttu-id="759ab-116">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="759ab-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="759ab-117">Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="759ab-117">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="759ab-118">Spusťte ukázku pomocí následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="759ab-118">Run the sample by following these steps:</span></span>  
  
    1. <span data-ttu-id="759ab-119">Klikněte pravým tlačítkem myši na projekt **služby** a vyberte **nastavit jako spouštěný projekt**a potom stiskněte klávesy **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="759ab-119">Right click the **Service** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
    2. <span data-ttu-id="759ab-120">Počkejte na výstup konzoly s potvrzením, že je služba spuštěná.</span><span class="sxs-lookup"><span data-stu-id="759ab-120">Wait for the console output confirming that the service is up and running.</span></span>  
  
    3. <span data-ttu-id="759ab-121">Klikněte pravým tlačítkem myši na projekt **klienta** a vyberte **nastavit jako spouštěný projekt**a potom stiskněte klávesy **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="759ab-121">Right click the **Client** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="759ab-122">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="759ab-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="759ab-123">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="759ab-123">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="759ab-124">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="759ab-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="759ab-125">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="759ab-125">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a><span data-ttu-id="759ab-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="759ab-126">See also</span></span>

- <span data-ttu-id="759ab-127">[Ukázky správy technologie AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383405(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="759ab-127">[AppFabric Management Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383405(v=azure.10))</span></span>
- [<span data-ttu-id="759ab-128">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="759ab-128">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)
