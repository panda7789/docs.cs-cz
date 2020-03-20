---
title: Zjednodušená konfigurace pro služby WCF
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: f3c4df5ae3fe5426c8b26142807f16b60db001c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183356"
---
# <a name="simplified-configuration-for-wcf-services"></a><span data-ttu-id="5564c-102">Zjednodušená konfigurace pro služby WCF</span><span class="sxs-lookup"><span data-stu-id="5564c-102">Simplified Configuration for WCF Services</span></span>
<span data-ttu-id="5564c-103">Tato ukázka ukazuje, jak implementovat a nakonfigurovat typické služby a klienta pomocí Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5564c-103">This sample demonstrates how to implement and configure a typical service and client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="5564c-104">Tento vzorek je základem pro všechny ostatní základní vzorky technologie.</span><span class="sxs-lookup"><span data-stu-id="5564c-104">This sample is the basis for all other basic technology samples.</span></span>  
  
 <span data-ttu-id="5564c-105">Tato služba, která zveřejňuje koncový bod pro komunikaci se službou, používá zjednodušenou konfiguraci v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="5564c-105">This service, which exposes an endpoint for communicating with the service, uses the simplified configuration in .NET Framework 4.</span></span> <span data-ttu-id="5564c-106">Před rozhraním .NET Framework 4 je koncový bod obvykle definován v konfiguračním souboru (Web.config), jak je znázorněno v následujícím příkladu konfiguračního kódu.</span><span class="sxs-lookup"><span data-stu-id="5564c-106">Prior to .NET Framework 4, the endpoint is typically defined in a configuration file (Web.config), as shown in the following example configuration code.</span></span>  
  
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
  
 <span data-ttu-id="5564c-107">V rozhraní .NET `<service>` Framework 4 je prvek volitelný.</span><span class="sxs-lookup"><span data-stu-id="5564c-107">In .NET Framework 4, the `<service>` element is optional.</span></span> <span data-ttu-id="5564c-108">Pokud služba nedefinuje žádné koncové body, koncový bod pro každou základní adresu a implementovanou smlouvu jsou přidány do služby.</span><span class="sxs-lookup"><span data-stu-id="5564c-108">When a service does not define any endpoints, an endpoint for each base address and contract implemented are added to the service.</span></span> <span data-ttu-id="5564c-109">Základní adresa je připojena k názvu smlouvy k určení koncového bodu a vazba je určena schématem adresy.</span><span class="sxs-lookup"><span data-stu-id="5564c-109">The base address is appended to the contract name to determine the endpoint and the binding is determined by the address scheme.</span></span> <span data-ttu-id="5564c-110">Následující příklad kódu ukazuje zjednodušený konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="5564c-110">The following code example demonstrates a simplified configuration file.</span></span> <span data-ttu-id="5564c-111">Podle konfigurace, služba může být `http://localhost/servicemodelsamples/service.svc` přístupná klientem ve stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="5564c-111">As configured, the service can be accessed at `http://localhost/servicemodelsamples/service.svc` by a client on the same computer.</span></span> <span data-ttu-id="5564c-112">Pro klienty ve vzdálených počítačích pro přístup ke službě musí být zadán plně kvalifikovaný název domény namísto localhost.</span><span class="sxs-lookup"><span data-stu-id="5564c-112">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span> <span data-ttu-id="5564c-113">Služba nezveřejňuje metadata ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="5564c-113">The service does not expose metadata by default.</span></span> <span data-ttu-id="5564c-114">Jako takové služba zapne <xref:System.ServiceModel.Description.ServiceMetadataBehavior> chování.</span><span class="sxs-lookup"><span data-stu-id="5564c-114">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> behavior.</span></span>  
  
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
  
### <a name="to-use-this-sample"></a><span data-ttu-id="5564c-115">Chcete-li použít tento vzorek</span><span class="sxs-lookup"><span data-stu-id="5564c-115">To use this sample</span></span>  
  
1. <span data-ttu-id="5564c-116">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5564c-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5564c-117">Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5564c-117">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="5564c-118">Ukázku spusťte takto:</span><span class="sxs-lookup"><span data-stu-id="5564c-118">Run the sample by following these steps:</span></span>  
  
    1. <span data-ttu-id="5564c-119">Klepněte pravým tlačítkem myši na projekt **servisu** a vyberte **příkaz Nastavit jako projekt spuštění**a stiskněte **kombinaci kláves Ctrl+F5**.</span><span class="sxs-lookup"><span data-stu-id="5564c-119">Right click the **Service** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
    2. <span data-ttu-id="5564c-120">Počkejte na výstup konzoly potvrzující, že služba je v provozu.</span><span class="sxs-lookup"><span data-stu-id="5564c-120">Wait for the console output confirming that the service is up and running.</span></span>  
  
    3. <span data-ttu-id="5564c-121">Klepněte pravým tlačítkem myši na **projekt Klient** a vyberte příkaz Nastavit jako **počáteční projekt**a stiskněte **kombinaci kláves Ctrl+F5**.</span><span class="sxs-lookup"><span data-stu-id="5564c-121">Right click the **Client** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5564c-122">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="5564c-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5564c-123">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="5564c-123">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5564c-124">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="5564c-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5564c-125">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="5564c-125">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a><span data-ttu-id="5564c-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="5564c-126">See also</span></span>

- <span data-ttu-id="5564c-127">[Ukázky správy appfabricu](https://docs.microsoft.com/previous-versions/appfabric/ff383405(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="5564c-127">[AppFabric Management Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383405(v=azure.10))</span></span>
- [<span data-ttu-id="5564c-128">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="5564c-128">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)
