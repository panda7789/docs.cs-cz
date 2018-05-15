---
title: Aktivace podle konfigurace
ms.date: 03/30/2017
ms.assetid: 21bb762e-c43e-4b0c-887b-5e434d665838
ms.openlocfilehash: 3ac4edd2a51e4ed8a5c0b7e73d7d1afa31334c33
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="configuration-based-activation"></a><span data-ttu-id="7dcd8-102">Aktivace podle konfigurace</span><span class="sxs-lookup"><span data-stu-id="7dcd8-102">Configuration-Based Activation</span></span>
<span data-ttu-id="7dcd8-103">Tento příklad znázorňuje postup aktivace služby Windows Communication Foundation (WCF) bez nutnosti .svc souboru.</span><span class="sxs-lookup"><span data-stu-id="7dcd8-103">This sample demonstrates how to activate Windows Communication Foundation (WCF) services without requiring a .svc file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7dcd8-104">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="7dcd8-104">The samples may already be installed on your computer.</span></span> <span data-ttu-id="7dcd8-105">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="7dcd8-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7dcd8-106">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="7dcd8-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7dcd8-107">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="7dcd8-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\ConfigBasedActivation`  
  
## <a name="sample-details"></a><span data-ttu-id="7dcd8-108">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="7dcd8-108">Sample Details</span></span>  
 <span data-ttu-id="7dcd8-109">V této ukázce je klient testovacího klienta WCF a služba je hostovaná ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="7dcd8-109">In this sample, the client is the WCF test client and the service is hosted in IIS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7dcd8-110">Instalační program a sestavení pokyny v tomto příkladu jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="7dcd8-110">The setup and build instructions for this sample are located at the end of this topic.</span></span>  
  
### <a name="activation-of-services-without-requiring-a-svc-file"></a><span data-ttu-id="7dcd8-111">Aktivace služby bez nutnosti soubor .svc</span><span class="sxs-lookup"><span data-stu-id="7dcd8-111">Activation of services without requiring a .svc file</span></span>  
 <span data-ttu-id="7dcd8-112">V [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], soubor .svc nebyla nutná pro aktivaci služby.</span><span class="sxs-lookup"><span data-stu-id="7dcd8-112">In [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], a .svc file was required for activating a service.</span></span> <span data-ttu-id="7dcd8-113">Příčinou další správní režii, protože další soubor je potřeba nasadit a udržovat spolu s aplikací.</span><span class="sxs-lookup"><span data-stu-id="7dcd8-113">This caused additional management overhead, because an additional file was required to be deployed and maintained along with the application.</span></span> <span data-ttu-id="7dcd8-114">S vydáním [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], aktivačních komponent lze nakonfigurovat pomocí konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="7dcd8-114">With the release of [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], the activation components can be configured using the application configuration file.</span></span>  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]<span data-ttu-id="7dcd8-115"> zavádí nový element konfigurace (<xref:System.ServiceModel.Configuration.ServiceActivationElement>) v <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="7dcd8-115"> introduces a new configuration element (<xref:System.ServiceModel.Configuration.ServiceActivationElement>), in the <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> of the application configuration file.</span></span> <span data-ttu-id="7dcd8-116"><xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> Kolekci lze používat pouze kolekce služeb, které chcete aktivovat, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="7dcd8-116">The <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> collection accepts a collection of services to activate, as shown in the following code example.</span></span>  
  
```xml  
<serviceActivations>  
   <add relativeAddress="Calculator.svc" service="Microsoft.ServiceModel.Samples.CalculatorService" />  
  
<serviceActivations>  
```  
  
 <span data-ttu-id="7dcd8-117">Pozorování, aby je, že konfigurace je velmi podobná konfigurace souborů .svc.</span><span class="sxs-lookup"><span data-stu-id="7dcd8-117">The observation to make is the configuration looks very similar to the configuration of .svc files.</span></span> <span data-ttu-id="7dcd8-118">Další atribut, který byl představen `relativeAddress` adresu služby, který poskytuje.</span><span class="sxs-lookup"><span data-stu-id="7dcd8-118">An additional attribute that is introduced is the `relativeAddress` that provides the address of the service.</span></span> <span data-ttu-id="7dcd8-119">Relativní adresa je také virtuální cestu pro službu.</span><span class="sxs-lookup"><span data-stu-id="7dcd8-119">The relative address is also the virtual path for the service.</span></span> <span data-ttu-id="7dcd8-120">Hostitel načítá soubor ze souboru Web.config `virtualPath` umístění, pokud existuje; jinak hodnota hostitele Vyhledá rekurzivně jeho nadřazené složky.</span><span class="sxs-lookup"><span data-stu-id="7dcd8-120">The host retrieves the Web.config file of the file from the `virtualPath` location, if present; otherwise the host searches its parent folder recursively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7dcd8-121">Tato ukázka vyžaduje hostování funkce ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="7dcd8-121">This sample requires hosting in IIS to function.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="7dcd8-122">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="7dcd8-122">To use this sample</span></span>  
  
1.  <span data-ttu-id="7dcd8-123">Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor Service.csproj.</span><span class="sxs-lookup"><span data-stu-id="7dcd8-123">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the Service.csproj file.</span></span>  
  
2.  <span data-ttu-id="7dcd8-124">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="7dcd8-124">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="7dcd8-125">Testování služby spuštěním WCFTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="7dcd8-125">Test the service by running WCFTestClient.exe.</span></span>  
  
4.  <span data-ttu-id="7dcd8-126">Pomocí [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], přejděte do složky 10.0\Common7\IDE %SystemDrive%\Program Files\Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7dcd8-126">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], navigate to the %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE folder.</span></span>  
  
5.  <span data-ttu-id="7dcd8-127">Spusťte WcfTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="7dcd8-127">Run WcfTestClient.exe.</span></span>  
  
6.  <span data-ttu-id="7dcd8-128">Nastavte adresu MEX služby.</span><span class="sxs-lookup"><span data-stu-id="7dcd8-128">Set the MEX address of the service.</span></span>  
  
7.  <span data-ttu-id="7dcd8-129">Stisknutím kombinace kláves CTRL + SHIFT + A nastavit adresu služby.</span><span class="sxs-lookup"><span data-stu-id="7dcd8-129">Press CTRL+SHIFT+A to set the service address.</span></span>  
  
8.  <span data-ttu-id="7dcd8-130">Nastavena adresa http://localhost/ServiceModelSamples/Calculator.svc.</span><span class="sxs-lookup"><span data-stu-id="7dcd8-130">Set the address to http://localhost/ServiceModelSamples/Calculator.svc.</span></span>  
  
9. <span data-ttu-id="7dcd8-131">Proveďte `Add` operace.</span><span class="sxs-lookup"><span data-stu-id="7dcd8-131">Perform the `Add` operation.</span></span> <span data-ttu-id="7dcd8-132">Nastavit hodnotu `n1` parametr 10 a nastavte hodnotu na `n2` parametru 15.</span><span class="sxs-lookup"><span data-stu-id="7dcd8-132">Set value on the `n1` parameter to 10 and set value on the `n2` parameter to 15.</span></span>  
  
10. <span data-ttu-id="7dcd8-133">Stiskněte klávesu **vyvolání**.</span><span class="sxs-lookup"><span data-stu-id="7dcd8-133">Press **Invoke**.</span></span>  
  
     <span data-ttu-id="7dcd8-134">Očekávaný výsledek je 25.</span><span class="sxs-lookup"><span data-stu-id="7dcd8-134">The expected result is 25.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7dcd8-135">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="7dcd8-135">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7dcd8-136">Ujistěte se, kterou jste udělali [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7dcd8-136">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="7dcd8-137">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7dcd8-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="7dcd8-138">Po řešení byla vytvořena, spusťte Setup.bat nastavit ServiceModelSamples aplikace ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="7dcd8-138">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS.</span></span> <span data-ttu-id="7dcd8-139">Adresář ServiceModelSamples by se měla zobrazit jako aplikace služby IIS.</span><span class="sxs-lookup"><span data-stu-id="7dcd8-139">The ServiceModelSamples directory should now appear as an IIS Application.</span></span>  
  
4.  <span data-ttu-id="7dcd8-140">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7dcd8-140">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dcd8-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="7dcd8-141">See Also</span></span>  
 [<span data-ttu-id="7dcd8-142">Ukázky trvalosti a hostování AppFabric</span><span class="sxs-lookup"><span data-stu-id="7dcd8-142">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
