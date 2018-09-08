---
title: Aktivace podle konfigurace
ms.date: 03/30/2017
ms.assetid: 21bb762e-c43e-4b0c-887b-5e434d665838
ms.openlocfilehash: e016dffdaf93b222c1fd2380bfa175256b009068
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44188303"
---
# <a name="configuration-based-activation"></a><span data-ttu-id="531b8-102">Aktivace podle konfigurace</span><span class="sxs-lookup"><span data-stu-id="531b8-102">Configuration-Based Activation</span></span>
<span data-ttu-id="531b8-103">Tato ukázka předvádí postup aktivace služby Windows Communication Foundation (WCF) bez nutnosti souboru SVC.</span><span class="sxs-lookup"><span data-stu-id="531b8-103">This sample demonstrates how to activate Windows Communication Foundation (WCF) services without requiring a .svc file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="531b8-104">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="531b8-104">The samples may already be installed on your computer.</span></span> <span data-ttu-id="531b8-105">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="531b8-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="531b8-106">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="531b8-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="531b8-107">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="531b8-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\ConfigBasedActivation`  
  
## <a name="sample-details"></a><span data-ttu-id="531b8-108">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="531b8-108">Sample Details</span></span>  
 <span data-ttu-id="531b8-109">V této ukázce testovací klient WCF je klient a služba je hostována ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="531b8-109">In this sample, the client is the WCF test client and the service is hosted in IIS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="531b8-110">Instalační program a sestavení pokyny pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="531b8-110">The setup and build instructions for this sample are located at the end of this topic.</span></span>  
  
### <a name="activation-of-services-without-requiring-a-svc-file"></a><span data-ttu-id="531b8-111">Aktivace služby, bez nutnosti souboru SVC</span><span class="sxs-lookup"><span data-stu-id="531b8-111">Activation of services without requiring a .svc file</span></span>  
 <span data-ttu-id="531b8-112">V [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], byl soubor SVC požadované pro aktivaci služby.</span><span class="sxs-lookup"><span data-stu-id="531b8-112">In [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], a .svc file was required for activating a service.</span></span> <span data-ttu-id="531b8-113">Důvodem další režie, protože je potřeba nasadit a udržovat spolu s aplikace další soubor.</span><span class="sxs-lookup"><span data-stu-id="531b8-113">This caused additional management overhead, because an additional file was required to be deployed and maintained along with the application.</span></span> <span data-ttu-id="531b8-114">S vydáním [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], aktivačních komponent lze konfigurovat pomocí konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="531b8-114">With the release of [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], the activation components can be configured using the application configuration file.</span></span>  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]<span data-ttu-id="531b8-115"> zavádí nový element konfigurace (<xref:System.ServiceModel.Configuration.ServiceActivationElement>) v <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="531b8-115"> introduces a new configuration element (<xref:System.ServiceModel.Configuration.ServiceActivationElement>), in the <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> of the application configuration file.</span></span> <span data-ttu-id="531b8-116"><xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> Kolekce přijímá kolekce služeb, které chcete aktivovat, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="531b8-116">The <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> collection accepts a collection of services to activate, as shown in the following code example.</span></span>  
  
```xml  
<serviceActivations>  
   <add relativeAddress="Calculator.svc" service="Microsoft.ServiceModel.Samples.CalculatorService" />  
  
<serviceActivations>  
```  
  
 <span data-ttu-id="531b8-117">Sledování, aby je že konfigurace vypadá podobně jako konfigurace hledání souborů .svc.</span><span class="sxs-lookup"><span data-stu-id="531b8-117">The observation to make is the configuration looks very similar to the configuration of .svc files.</span></span> <span data-ttu-id="531b8-118">Další atribut, který byl představen `relativeAddress` , který obsahuje adresu služby.</span><span class="sxs-lookup"><span data-stu-id="531b8-118">An additional attribute that is introduced is the `relativeAddress` that provides the address of the service.</span></span> <span data-ttu-id="531b8-119">Relativní adresa je také virtuální cestu pro službu.</span><span class="sxs-lookup"><span data-stu-id="531b8-119">The relative address is also the virtual path for the service.</span></span> <span data-ttu-id="531b8-120">Hostitel načítá soubor ze souboru Web.config `virtualPath` umístění, pokud je k dispozici; jinak prohledá hostitele své nadřazené složky rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="531b8-120">The host retrieves the Web.config file of the file from the `virtualPath` location, if present; otherwise the host searches its parent folder recursively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="531b8-121">Tato ukázka vyžaduje hostování ve službě IIS na funkci.</span><span class="sxs-lookup"><span data-stu-id="531b8-121">This sample requires hosting in IIS to function.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="531b8-122">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="531b8-122">To use this sample</span></span>  
  
1.  <span data-ttu-id="531b8-123">Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor Service.csproj.</span><span class="sxs-lookup"><span data-stu-id="531b8-123">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the Service.csproj file.</span></span>  
  
2.  <span data-ttu-id="531b8-124">Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="531b8-124">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="531b8-125">Spuštěním WCFTestClient.exe otestování služby.</span><span class="sxs-lookup"><span data-stu-id="531b8-125">Test the service by running WCFTestClient.exe.</span></span>  
  
4.  <span data-ttu-id="531b8-126">Pomocí [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], přejděte do složky %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE.</span><span class="sxs-lookup"><span data-stu-id="531b8-126">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], navigate to the %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE folder.</span></span>  
  
5.  <span data-ttu-id="531b8-127">Spusťte WcfTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="531b8-127">Run WcfTestClient.exe.</span></span>  
  
6.  <span data-ttu-id="531b8-128">Nastavte adresu MEX služby.</span><span class="sxs-lookup"><span data-stu-id="531b8-128">Set the MEX address of the service.</span></span>  
  
7.  <span data-ttu-id="531b8-129">Stiskněte kombinaci kláves CTRL + SHIFT + A Chcete-li nastavit adresu služby.</span><span class="sxs-lookup"><span data-stu-id="531b8-129">Press CTRL+SHIFT+A to set the service address.</span></span>  
  
8.  <span data-ttu-id="531b8-130">Nastavena adresa http://localhost/ServiceModelSamples/Calculator.svc.</span><span class="sxs-lookup"><span data-stu-id="531b8-130">Set the address to http://localhost/ServiceModelSamples/Calculator.svc.</span></span>  
  
9. <span data-ttu-id="531b8-131">Provést `Add` operace.</span><span class="sxs-lookup"><span data-stu-id="531b8-131">Perform the `Add` operation.</span></span> <span data-ttu-id="531b8-132">Nastavte hodnotu na `n1` parametr na hodnotu 10 a nastavené na `n2` parametr do 15.</span><span class="sxs-lookup"><span data-stu-id="531b8-132">Set value on the `n1` parameter to 10 and set value on the `n2` parameter to 15.</span></span>  
  
10. <span data-ttu-id="531b8-133">Stisknutím klávesy **vyvolat**.</span><span class="sxs-lookup"><span data-stu-id="531b8-133">Press **Invoke**.</span></span>  
  
     <span data-ttu-id="531b8-134">Očekávaný výsledek je 25.</span><span class="sxs-lookup"><span data-stu-id="531b8-134">The expected result is 25.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="531b8-135">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="531b8-135">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="531b8-136">Ujistěte se, jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="531b8-136">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="531b8-137">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="531b8-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="531b8-138">Po řešení je sestavený Build, spusťte Setup.bat nastavení ServiceModelSamples aplikace ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="531b8-138">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS.</span></span> <span data-ttu-id="531b8-139">Adresář ServiceModelSamples by se měl objevit jako aplikace služby IIS.</span><span class="sxs-lookup"><span data-stu-id="531b8-139">The ServiceModelSamples directory should now appear as an IIS Application.</span></span>  
  
4.  <span data-ttu-id="531b8-140">Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="531b8-140">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="531b8-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="531b8-141">See Also</span></span>  
 [<span data-ttu-id="531b8-142">Hostování AppFabric a ukázky trvalosti</span><span class="sxs-lookup"><span data-stu-id="531b8-142">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
