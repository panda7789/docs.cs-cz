---
title: Aktivace podle konfigurace
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21bb762e-c43e-4b0c-887b-5e434d665838
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d520a46bc3380fc5dff76f5df866ae3411d5a6a7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="configuration-based-activation"></a><span data-ttu-id="ada51-102">Aktivace podle konfigurace</span><span class="sxs-lookup"><span data-stu-id="ada51-102">Configuration-Based Activation</span></span>
<span data-ttu-id="ada51-103">Tento příklad ukazuje, jak aktivovat [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby bez nutnosti .svc souboru.</span><span class="sxs-lookup"><span data-stu-id="ada51-103">This sample demonstrates how to activate [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services without requiring a .svc file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ada51-104">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="ada51-104">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ada51-105">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ada51-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ada51-106">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="ada51-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ada51-107">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="ada51-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\ConfigBasedActivation`  
  
## <a name="sample-details"></a><span data-ttu-id="ada51-108">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ada51-108">Sample Details</span></span>  
 <span data-ttu-id="ada51-109">V této ukázce je klient [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] testovacího klienta a služby je hostovaný ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="ada51-109">In this sample, the client is the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client and the service is hosted in IIS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ada51-110">Instalační program a sestavení pokyny v tomto příkladu jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="ada51-110">The setup and build instructions for this sample are located at the end of this topic.</span></span>  
  
### <a name="activation-of-services-without-requiring-a-svc-file"></a><span data-ttu-id="ada51-111">Aktivace služby bez nutnosti soubor .svc</span><span class="sxs-lookup"><span data-stu-id="ada51-111">Activation of services without requiring a .svc file</span></span>  
 <span data-ttu-id="ada51-112">V [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], soubor .svc nebyla nutná pro aktivaci služby.</span><span class="sxs-lookup"><span data-stu-id="ada51-112">In [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], a .svc file was required for activating a service.</span></span> <span data-ttu-id="ada51-113">Příčinou další správní režii, protože další soubor je potřeba nasadit a udržovat spolu s aplikací.</span><span class="sxs-lookup"><span data-stu-id="ada51-113">This caused additional management overhead, because an additional file was required to be deployed and maintained along with the application.</span></span> <span data-ttu-id="ada51-114">S vydáním [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], aktivačních komponent lze nakonfigurovat pomocí konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="ada51-114">With the release of [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], the activation components can be configured using the application configuration file.</span></span>  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]<span data-ttu-id="ada51-115">zavádí nový element konfigurace (<xref:System.ServiceModel.Configuration.ServiceActivationElement>) v <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="ada51-115"> introduces a new configuration element (<xref:System.ServiceModel.Configuration.ServiceActivationElement>), in the <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> of the application configuration file.</span></span> <span data-ttu-id="ada51-116"><xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> Kolekci lze používat pouze kolekce služeb, které chcete aktivovat, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="ada51-116">The <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> collection accepts a collection of services to activate, as shown in the following code example.</span></span>  
  
```xml  
<serviceActivations>  
   <add relativeAddress="Calculator.svc" service="Microsoft.ServiceModel.Samples.CalculatorService" />  
  
<serviceActivations>  
```  
  
 <span data-ttu-id="ada51-117">Pozorování, aby je, že konfigurace je velmi podobná konfigurace souborů .svc.</span><span class="sxs-lookup"><span data-stu-id="ada51-117">The observation to make is the configuration looks very similar to the configuration of .svc files.</span></span> <span data-ttu-id="ada51-118">Další atribut, který byl představen `relativeAddress` adresu služby, který poskytuje.</span><span class="sxs-lookup"><span data-stu-id="ada51-118">An additional attribute that is introduced is the `relativeAddress` that provides the address of the service.</span></span> <span data-ttu-id="ada51-119">Relativní adresa je také virtuální cestu pro službu.</span><span class="sxs-lookup"><span data-stu-id="ada51-119">The relative address is also the virtual path for the service.</span></span> <span data-ttu-id="ada51-120">Hostitel načítá soubor ze souboru Web.config `virtualPath` umístění, pokud existuje; jinak hodnota hostitele Vyhledá rekurzivně jeho nadřazené složky.</span><span class="sxs-lookup"><span data-stu-id="ada51-120">The host retrieves the Web.config file of the file from the `virtualPath` location, if present; otherwise the host searches its parent folder recursively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ada51-121">Tato ukázka vyžaduje hostování funkce ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="ada51-121">This sample requires hosting in IIS to function.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="ada51-122">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="ada51-122">To use this sample</span></span>  
  
1.  <span data-ttu-id="ada51-123">Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor Service.csproj.</span><span class="sxs-lookup"><span data-stu-id="ada51-123">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the Service.csproj file.</span></span>  
  
2.  <span data-ttu-id="ada51-124">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="ada51-124">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="ada51-125">Testování služby spuštěním WCFTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="ada51-125">Test the service by running WCFTestClient.exe.</span></span>  
  
4.  <span data-ttu-id="ada51-126">Pomocí [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], přejděte do složky 10.0\Common7\IDE %SystemDrive%\Program Files\Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ada51-126">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], navigate to the %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE folder.</span></span>  
  
5.  <span data-ttu-id="ada51-127">Spusťte WcfTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="ada51-127">Run WcfTestClient.exe.</span></span>  
  
6.  <span data-ttu-id="ada51-128">Nastavte adresu MEX služby.</span><span class="sxs-lookup"><span data-stu-id="ada51-128">Set the MEX address of the service.</span></span>  
  
7.  <span data-ttu-id="ada51-129">Stisknutím kombinace kláves CTRL + SHIFT + A nastavit adresu služby.</span><span class="sxs-lookup"><span data-stu-id="ada51-129">Press CTRL+SHIFT+A to set the service address.</span></span>  
  
8.  <span data-ttu-id="ada51-130">Nastavena adresa http://localhost/ServiceModelSamples/Calculator.svc.</span><span class="sxs-lookup"><span data-stu-id="ada51-130">Set the address to http://localhost/ServiceModelSamples/Calculator.svc.</span></span>  
  
9. <span data-ttu-id="ada51-131">Proveďte `Add` operace.</span><span class="sxs-lookup"><span data-stu-id="ada51-131">Perform the `Add` operation.</span></span> <span data-ttu-id="ada51-132">Nastavit hodnotu `n1` parametr 10 a nastavte hodnotu na `n2` parametru 15.</span><span class="sxs-lookup"><span data-stu-id="ada51-132">Set value on the `n1` parameter to 10 and set value on the `n2` parameter to 15.</span></span>  
  
10. <span data-ttu-id="ada51-133">Stiskněte klávesu **vyvolání**.</span><span class="sxs-lookup"><span data-stu-id="ada51-133">Press **Invoke**.</span></span>  
  
     <span data-ttu-id="ada51-134">Očekávaný výsledek je 25.</span><span class="sxs-lookup"><span data-stu-id="ada51-134">The expected result is 25.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ada51-135">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="ada51-135">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ada51-136">Ujistěte se, kterou jste udělali [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ada51-136">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ada51-137">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ada51-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="ada51-138">Po řešení byla vytvořena, spusťte Setup.bat nastavit ServiceModelSamples aplikace ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="ada51-138">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS.</span></span> <span data-ttu-id="ada51-139">Adresář ServiceModelSamples by se měla zobrazit jako aplikace služby IIS.</span><span class="sxs-lookup"><span data-stu-id="ada51-139">The ServiceModelSamples directory should now appear as an IIS Application.</span></span>  
  
4.  <span data-ttu-id="ada51-140">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ada51-140">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ada51-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="ada51-141">See Also</span></span>  
 [<span data-ttu-id="ada51-142">Ukázky trvalosti a hostování AppFabric</span><span class="sxs-lookup"><span data-stu-id="ada51-142">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
