---
title: Zjednodušená konfigurace pro služby WCF
description: Naučte se implementovat a nakonfigurovat typickou službu a klienta pomocí WCF. Služba komunikuje pomocí koncového bodu zadaného v konfiguračním souboru.
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: 46a0c878b29de34219413a508799ddaddf507dd8
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246216"
---
# <a name="simplified-configuration-for-wcf-services"></a><span data-ttu-id="d1b88-104">Zjednodušená konfigurace pro služby WCF</span><span class="sxs-lookup"><span data-stu-id="d1b88-104">Simplified Configuration for WCF Services</span></span>
<span data-ttu-id="d1b88-105">Tato ukázka předvádí, jak implementovat a nakonfigurovat typickou službu a klienta pomocí Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d1b88-105">This sample demonstrates how to implement and configure a typical service and client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="d1b88-106">Tato ukázka je základem pro všechny ostatní základní ukázkové technologie.</span><span class="sxs-lookup"><span data-stu-id="d1b88-106">This sample is the basis for all other basic technology samples.</span></span>  
  
 <span data-ttu-id="d1b88-107">Tato služba, která zpřístupňuje koncový bod pro komunikaci se službou, používá zjednodušenou konfiguraci v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d1b88-107">This service, which exposes an endpoint for communicating with the service, uses the simplified configuration in .NET Framework 4.</span></span> <span data-ttu-id="d1b88-108">Před .NET Framework 4 je koncový bod obvykle definován v konfiguračním souboru (Web.config), jak je znázorněno v následujícím příkladu kódu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="d1b88-108">Prior to .NET Framework 4, the endpoint is typically defined in a configuration file (Web.config), as shown in the following example configuration code.</span></span>  
  
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
  
 <span data-ttu-id="d1b88-109">V .NET Framework 4 `<service>` je element volitelný.</span><span class="sxs-lookup"><span data-stu-id="d1b88-109">In .NET Framework 4, the `<service>` element is optional.</span></span> <span data-ttu-id="d1b88-110">Pokud služba nedefinuje žádné koncové body, do služby se přidají koncový bod pro každou základní adresu a implementaci smlouvy.</span><span class="sxs-lookup"><span data-stu-id="d1b88-110">When a service does not define any endpoints, an endpoint for each base address and contract implemented are added to the service.</span></span> <span data-ttu-id="d1b88-111">Základní adresa se připojí k názvu kontraktu a určí koncový bod a vazba je určena schématem adres.</span><span class="sxs-lookup"><span data-stu-id="d1b88-111">The base address is appended to the contract name to determine the endpoint and the binding is determined by the address scheme.</span></span> <span data-ttu-id="d1b88-112">Následující příklad kódu ukazuje zjednodušený konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="d1b88-112">The following code example demonstrates a simplified configuration file.</span></span> <span data-ttu-id="d1b88-113">Jak je nakonfigurováno, může být služba k dispozici `http://localhost/servicemodelsamples/service.svc` klientovi ve stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="d1b88-113">As configured, the service can be accessed at `http://localhost/servicemodelsamples/service.svc` by a client on the same computer.</span></span> <span data-ttu-id="d1b88-114">Aby mohli klienti na vzdálených počítačích přistupovat ke službě, je třeba zadat plně kvalifikovaný název domény namísto localhost.</span><span class="sxs-lookup"><span data-stu-id="d1b88-114">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span> <span data-ttu-id="d1b88-115">Služba ve výchozím nastavení nevystavuje metadata.</span><span class="sxs-lookup"><span data-stu-id="d1b88-115">The service does not expose metadata by default.</span></span> <span data-ttu-id="d1b88-116">V takovém případě služba toto chování zapne <xref:System.ServiceModel.Description.ServiceMetadataBehavior> .</span><span class="sxs-lookup"><span data-stu-id="d1b88-116">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> behavior.</span></span>  
  
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
  
### <a name="to-use-this-sample"></a><span data-ttu-id="d1b88-117">Použití této ukázky</span><span class="sxs-lookup"><span data-stu-id="d1b88-117">To use this sample</span></span>  
  
1. <span data-ttu-id="d1b88-118">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d1b88-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d1b88-119">Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d1b88-119">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="d1b88-120">Spusťte ukázku pomocí následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="d1b88-120">Run the sample by following these steps:</span></span>  
  
    1. <span data-ttu-id="d1b88-121">Klikněte pravým tlačítkem myši na projekt **služby** a vyberte **nastavit jako spouštěný projekt**a potom stiskněte klávesy **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="d1b88-121">Right click the **Service** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
    2. <span data-ttu-id="d1b88-122">Počkejte na výstup konzoly s potvrzením, že je služba spuštěná.</span><span class="sxs-lookup"><span data-stu-id="d1b88-122">Wait for the console output confirming that the service is up and running.</span></span>  
  
    3. <span data-ttu-id="d1b88-123">Klikněte pravým tlačítkem myši na projekt **klienta** a vyberte **nastavit jako spouštěný projekt**a potom stiskněte klávesy **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="d1b88-123">Right click the **Client** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d1b88-124">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="d1b88-124">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d1b88-125">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="d1b88-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d1b88-126">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="d1b88-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d1b88-127">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="d1b88-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a><span data-ttu-id="d1b88-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1b88-128">See also</span></span>

- <span data-ttu-id="d1b88-129">[Ukázky správy technologie AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383405(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="d1b88-129">[AppFabric Management Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383405(v=azure.10))</span></span>
- [<span data-ttu-id="d1b88-130">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="d1b88-130">Simplified Configuration</span></span>](../simplified-configuration.md)
