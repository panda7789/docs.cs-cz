---
title: "Model hierarchické konfigurace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28dcc698-226c-4b77-9e51-8bf45a36216c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cbcef9ebe1b4876e429da97b3e217dd32286e4d6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="hierarchical-configuration-model"></a><span data-ttu-id="81be6-102">Model hierarchické konfigurace</span><span class="sxs-lookup"><span data-stu-id="81be6-102">Hierarchical Configuration Model</span></span>
<span data-ttu-id="81be6-103">Tento příklad znázorňuje implementaci hierarchie konfigurační soubory pro služby.</span><span class="sxs-lookup"><span data-stu-id="81be6-103">This sample demonstrates how to implement a hierarchy of configuration files for services.</span></span> <span data-ttu-id="81be6-104">Také ukazuje, jak vazby, chování služby a chování koncový bod se dědí z vyšší úrovně v hierarchii.</span><span class="sxs-lookup"><span data-stu-id="81be6-104">It also shows how bindings, service behaviors, and endpoint behaviors are inherited from higher levels in the hierarchy.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="81be6-105">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="81be6-105">Sample details</span></span>  
 <span data-ttu-id="81be6-106">Jedna z funkcí vytvořených pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] v [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] vylepšením ve model hierarchické konfigurace.</span><span class="sxs-lookup"><span data-stu-id="81be6-106">One of the features developed for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] in [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] is the improvement in the hierarchical configuration model.</span></span> <span data-ttu-id="81be6-107">Příkladem hierarchické konfigurace modelu může být definováno Machine.config -> Rootweb.config -> souboru Web.config. V [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], tyto vazby a chování, které jsou definovány v horní úrovně v hierarchii konfigurace se přidají k vašim službám s žádné explicitní konfigurací.</span><span class="sxs-lookup"><span data-stu-id="81be6-107">An example of a hierarchical configuration model would be the one defined by Machine.config -> Rootweb.config -> Web.config. In [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], those bindings and behaviors that are defined in upper levels in the configuration hierarchy are added to your services with no explicit configuration.</span></span> <span data-ttu-id="81be6-108">Tento příklad ukazuje, jak je možné ke zjednodušení konfigurace služby podle konfigurace – elementy definované na počítači nebo na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="81be6-108">This sample shows how it is possible to simplify your service configuration by relying on configuration elements defined at the computer or the application level.</span></span>  
  
 <span data-ttu-id="81be6-109">Tato ukázka obsahuje devět služby, které jsou definované v tři úrovně hierarchie.</span><span class="sxs-lookup"><span data-stu-id="81be6-109">This sample consists of nine services, defined in three levels of hierarchy.</span></span> <span data-ttu-id="81be6-110">`Service1`je v kořenovém adresáři.</span><span class="sxs-lookup"><span data-stu-id="81be6-110">`Service1` is at the root.</span></span> <span data-ttu-id="81be6-111">`Service2`a `Service3` dědění výchozí elementy ze `Service1`.</span><span class="sxs-lookup"><span data-stu-id="81be6-111">`Service2` and `Service3` inherit the default elements from `Service1`.</span></span> <span data-ttu-id="81be6-112">`Service4`, `Service5`, `Service6` a `Service7` jsou definovány na třetí úrovni v hierarchii, dědění výchozí elementy ze `Service3`.</span><span class="sxs-lookup"><span data-stu-id="81be6-112">`Service4`, `Service5`, `Service6` and `Service7` are defined at a third level of the hierarchy, inheriting the default elements from `Service3`.</span></span> <span data-ttu-id="81be6-113">Nakonec `Service10` a `Service11` jsou čtvrtý úrovně v hierarchii.</span><span class="sxs-lookup"><span data-stu-id="81be6-113">Finally `Service10` and `Service11` are at a fourth level of the hierarchy.</span></span>  
  
 <span data-ttu-id="81be6-114">Všechny služby implementovat `IDesc` kontrakt.</span><span class="sxs-lookup"><span data-stu-id="81be6-114">All the services implement the `IDesc` contract.</span></span> <span data-ttu-id="81be6-115">Toto je definice `IDesc` rozhraní, které zobrazuje metody v tomto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="81be6-115">The following is the definition of the `IDesc` interface that shows the methods exposed in this interface.</span></span> <span data-ttu-id="81be6-116">`IDesc` Rozhraní je definováno v Service1.cs.</span><span class="sxs-lookup"><span data-stu-id="81be6-116">The `IDesc` interface is defined in Service1.cs.</span></span>  
  
```  
// Define a service contract  
[ServiceContract(Namespace="http://Microsoft.Samples.ConfigHierarchicalModel")]  
public interface IDesc  
{  
    [OperationContract]  
    List<string> ListEndpoints();  
    [OperationContract]  
    List<string> ListServiceBehaviors();  
    [OperationContract]  
    List<string> ListEndpointBehaviors();  
}  
```  
  
 <span data-ttu-id="81be6-117">Implementace tyto metody službami je jednoduchá.</span><span class="sxs-lookup"><span data-stu-id="81be6-117">The implementation of these methods by the services is straightforward.</span></span> <span data-ttu-id="81be6-118">`ListEndpoints`iteruje všechny koncové body služby a vrátí seznam všech koncových bodů, které má služba.</span><span class="sxs-lookup"><span data-stu-id="81be6-118">`ListEndpoints` iterates through all the service endpoints and returns a list of all the endpoints that the service has.</span></span> <span data-ttu-id="81be6-119">`ListServiceBehaviors`iteruje všechny chování přidali do služby a vrátí seznam všech chování služby spojené s touto službou.</span><span class="sxs-lookup"><span data-stu-id="81be6-119">`ListServiceBehaviors` iterates through all the behaviors added to the service and returns the list of all the service behaviors associated with the service.</span></span> <span data-ttu-id="81be6-120">`ListEndpointBehaviors`chová podobným způsobem jako pro `ListServiceBehaviors`, ale místo toho vrátí seznam chování koncový bod.</span><span class="sxs-lookup"><span data-stu-id="81be6-120">`ListEndpointBehaviors` behaves in a similar way to `ListServiceBehaviors`, but it returns the list of endpoint behaviors instead.</span></span>  
  
 <span data-ttu-id="81be6-121">Tato implementace umožňuje klientovi vědět, kolik koncových bodů služby je vystavení a které chování služby a koncového bodu chování přidané do služby.</span><span class="sxs-lookup"><span data-stu-id="81be6-121">This implementation allows the client to know how many endpoints the service is exposing and which service behaviors and endpoint behaviors have been added to the service.</span></span> <span data-ttu-id="81be6-122">Klientovi, který byl implementován jako součást ukázka přidá odkaz na službu ke všem službám v řešení a zobrazuje tyto prvky pro každé z nich služeb.</span><span class="sxs-lookup"><span data-stu-id="81be6-122">The client that has been implemented as part of the sample adds a service reference to all the services in the solution and shows these elements for each one of the services.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="81be6-123">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="81be6-123">To use this sample</span></span>  
  
#### <a name="to-run-the-client"></a><span data-ttu-id="81be6-124">Spuštění klienta</span><span class="sxs-lookup"><span data-stu-id="81be6-124">To run the client</span></span>  
  
1.  <span data-ttu-id="81be6-125">Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor ConfigHierarchicalModel.sln.</span><span class="sxs-lookup"><span data-stu-id="81be6-125">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the ConfigHierarchicalModel.sln file.</span></span>  
  
2.  <span data-ttu-id="81be6-126">Projektu klienta nebude již nastavena jako spuštění projektu, postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="81be6-126">The client project is not already set up as the start-up project, follow these steps.</span></span>  
  
    1.  <span data-ttu-id="81be6-127">V **Průzkumníku řešení**, klikněte pravým tlačítkem na řešení a pak vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="81be6-127">In **Solution Explorer**, right-click the solution and then select **Properties**.</span></span>  
  
    2.  <span data-ttu-id="81be6-128">V **společných vlastností**, vyberte **spouštěný projekt**a potom klikněte na **jeden projekt po spuštění**.</span><span class="sxs-lookup"><span data-stu-id="81be6-128">In **Common Properties**, select **Startup Project**, and then click **Single startup project**.</span></span>  
  
    3.  <span data-ttu-id="81be6-129">Z **jeden projekt po spuštění** rozevíracího seznamu, vyberte **klienta**.</span><span class="sxs-lookup"><span data-stu-id="81be6-129">From the **Single startup project** drop-down, select **Client**.</span></span>  
  
    4.  <span data-ttu-id="81be6-130">Klikněte na tlačítko **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="81be6-130">Click **OK** to close the dialog.</span></span>  
  
3.  <span data-ttu-id="81be6-131">Chcete-li sestavit ukázku, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="81be6-131">To build the sample, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="81be6-132">Spuštění klienta, stiskněte Ctrl + F5.</span><span class="sxs-lookup"><span data-stu-id="81be6-132">To run the client, press Ctrl+F5.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81be6-133">Pokud tyto kroky nefungují, ujistěte se, že vaše prostředí správně nastavený, pomocí následujících kroků.</span><span class="sxs-lookup"><span data-stu-id="81be6-133">If these steps do not work, then make sure that your environment has been properly set up, using the following steps.</span></span>  
>   
>  1.  <span data-ttu-id="81be6-134">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="81be6-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
> 2.  <span data-ttu-id="81be6-135">Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="81be6-135">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
> 3.  <span data-ttu-id="81be6-136">Spustit ukázku v jedné nebo více konfigurací počítače, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="81be6-136">To run the sample in a single or multiple computer configurations, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="81be6-137">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="81be6-137">The samples may already be installed on your computer.</span></span> <span data-ttu-id="81be6-138">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="81be6-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="81be6-139">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="81be6-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="81be6-140">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="81be6-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigHierarchicalModel`  
  
## <a name="see-also"></a><span data-ttu-id="81be6-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="81be6-141">See Also</span></span>  
 [<span data-ttu-id="81be6-142">Ukázky správy AppFabric</span><span class="sxs-lookup"><span data-stu-id="81be6-142">AppFabric Management Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193960)
