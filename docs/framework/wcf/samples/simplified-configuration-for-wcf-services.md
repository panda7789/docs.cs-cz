---
title: Zjednodušená konfigurace pro služby WCF
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: 47af8dcba35ba31f25597c946596b0cbcac93b4d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007848"
---
# <a name="simplified-configuration-for-wcf-services"></a><span data-ttu-id="2510c-102">Zjednodušená konfigurace pro služby WCF</span><span class="sxs-lookup"><span data-stu-id="2510c-102">Simplified Configuration for WCF Services</span></span>
<span data-ttu-id="2510c-103">Tento příklad ukazuje, jak implementovat a konfigurovat typické službu a klienta s použitím Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="2510c-103">This sample demonstrates how to implement and configure a typical service and client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="2510c-104">Tato ukázka představuje základ pro všechny další ukázky základní technologii.</span><span class="sxs-lookup"><span data-stu-id="2510c-104">This sample is the basis for all other basic technology samples.</span></span>  
  
 <span data-ttu-id="2510c-105">Tato služba, která zpřístupňuje koncový bod pro komunikaci se službou, využívá zjednodušenou konfiguraci v [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2510c-105">This service, which exposes an endpoint for communicating with the service, uses the simplified configuration in [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].</span></span> <span data-ttu-id="2510c-106">Před verzí [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], koncový bod je obvykle definováno v souboru konfigurace (Web.config), jak je znázorněno v následujícím příkladu kódu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="2510c-106">Prior to [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], the endpoint is typically defined in a configuration file (Web.config), as shown in the following example configuration code.</span></span>  
  
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
  
 <span data-ttu-id="2510c-107">V [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], `<service>` element je volitelné.</span><span class="sxs-lookup"><span data-stu-id="2510c-107">In [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], the `<service>` element is optional.</span></span> <span data-ttu-id="2510c-108">Když služba nedefinuje žádné koncové body, koncový bod pro každou základní adresu a implementovat kontrakt jsou přidány do služby.</span><span class="sxs-lookup"><span data-stu-id="2510c-108">When a service does not define any endpoints, an endpoint for each base address and contract implemented are added to the service.</span></span> <span data-ttu-id="2510c-109">Základní adresa je připojeným k názvu kontraktu určit koncový bod a vazbu určuje schéma adres.</span><span class="sxs-lookup"><span data-stu-id="2510c-109">The base address is appended to the contract name to determine the endpoint and the binding is determined by the address scheme.</span></span> <span data-ttu-id="2510c-110">Následující příklad kódu ukazuje zjednodušený konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="2510c-110">The following code example demonstrates a simplified configuration file.</span></span> <span data-ttu-id="2510c-111">Podle konfigurace, služba může získat přístup na adrese `http://localhost/servicemodelsamples/service.svc` klientem na stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="2510c-111">As configured, the service can be accessed at `http://localhost/servicemodelsamples/service.svc` by a client on the same computer.</span></span> <span data-ttu-id="2510c-112">Pro klienty ve vzdálených počítačích pro přístup ke službě musí se zadat název plně kvalifikované domény místo localhost.</span><span class="sxs-lookup"><span data-stu-id="2510c-112">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span> <span data-ttu-id="2510c-113">Služba nevystavuje metadata ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="2510c-113">The service does not expose metadata by default.</span></span> <span data-ttu-id="2510c-114">V důsledku toho služba Zapne <xref:System.ServiceModel.Description.ServiceMetadataBehavior> chování.</span><span class="sxs-lookup"><span data-stu-id="2510c-114">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> behavior.</span></span>  
  
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
  
### <a name="to-use-this-sample"></a><span data-ttu-id="2510c-115">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="2510c-115">To use this sample</span></span>  
  
1. <span data-ttu-id="2510c-116">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2510c-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="2510c-117">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2510c-117">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="2510c-118">Spusťte ukázku pomocí následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="2510c-118">Run the sample by following these steps:</span></span>  
  
    1. <span data-ttu-id="2510c-119">Klikněte pravým tlačítkem myši **služby** projektu a vyberte **nastavit jako spouštěný projekt**, stiskněte klávesu **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="2510c-119">Right click the **Service** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
    2. <span data-ttu-id="2510c-120">Vyčkat, než bude výstup konzoly potvrzení, zda je služba nahoru a spouštění.</span><span class="sxs-lookup"><span data-stu-id="2510c-120">Wait for the console output confirming that the service is up and running.</span></span>  
  
    3. <span data-ttu-id="2510c-121">Klikněte pravým tlačítkem myši **klienta** projektu a vyberte **nastavit jako spouštěný projekt**, stiskněte klávesu **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="2510c-121">Right click the **Client** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2510c-122">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="2510c-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="2510c-123">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="2510c-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2510c-124">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="2510c-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2510c-125">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="2510c-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a><span data-ttu-id="2510c-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2510c-126">See also</span></span>

- [<span data-ttu-id="2510c-127">Ukázky správy AppFabric</span><span class="sxs-lookup"><span data-stu-id="2510c-127">AppFabric Management Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193960)
- [<span data-ttu-id="2510c-128">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="2510c-128">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)
