---
title: Model hierarchické konfigurace
ms.date: 03/30/2017
ms.assetid: 28dcc698-226c-4b77-9e51-8bf45a36216c
ms.openlocfilehash: 8ca9b01eb022e2e2ab940866a6230e8227ceb2dc
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43499338"
---
# <a name="hierarchical-configuration-model"></a><span data-ttu-id="13be7-102">Model hierarchické konfigurace</span><span class="sxs-lookup"><span data-stu-id="13be7-102">Hierarchical Configuration Model</span></span>
<span data-ttu-id="13be7-103">Tento příklad ukazuje, jak implementovat hierarchii konfigurační soubory pro služby.</span><span class="sxs-lookup"><span data-stu-id="13be7-103">This sample demonstrates how to implement a hierarchy of configuration files for services.</span></span> <span data-ttu-id="13be7-104">Profil také ukazuje, jak vazby, chování služby a chování koncového bodu se dědí z vyšší úrovně v hierarchii.</span><span class="sxs-lookup"><span data-stu-id="13be7-104">It also shows how bindings, service behaviors, and endpoint behaviors are inherited from higher levels in the hierarchy.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="13be7-105">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="13be7-105">Sample details</span></span>  
 <span data-ttu-id="13be7-106">Jednou z funkcí vyvinutý pro službu WCF v [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] je zvýšení model hierarchické konfigurace.</span><span class="sxs-lookup"><span data-stu-id="13be7-106">One of the features developed for WCF in [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] is the improvement in the hierarchical configuration model.</span></span> <span data-ttu-id="13be7-107">Příkladem model hierarchické konfigurace může být definováno Machine.config -> Rootweb.config -> souboru Web.config. V [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], tyto vazby a chování, které jsou definovány v vyšší úrovně v hierarchii konfigurace se přidají do vaší služby bez explicitní konfigurace.</span><span class="sxs-lookup"><span data-stu-id="13be7-107">An example of a hierarchical configuration model would be the one defined by Machine.config -> Rootweb.config -> Web.config. In [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], those bindings and behaviors that are defined in upper levels in the configuration hierarchy are added to your services with no explicit configuration.</span></span> <span data-ttu-id="13be7-108">Tato ukázka předvádí, jak je možné pro zjednodušení konfigurace služby pomocí konfigurační prvky, které jsou definované na úrovni aplikace nebo počítače.</span><span class="sxs-lookup"><span data-stu-id="13be7-108">This sample shows how it is possible to simplify your service configuration by relying on configuration elements defined at the computer or the application level.</span></span>  
  
 <span data-ttu-id="13be7-109">Tento příklad se skládá z devíti služeb, definovaný ve třech úrovních hierarchie.</span><span class="sxs-lookup"><span data-stu-id="13be7-109">This sample consists of nine services, defined in three levels of hierarchy.</span></span> <span data-ttu-id="13be7-110">`Service1` je v kořenovém adresáři.</span><span class="sxs-lookup"><span data-stu-id="13be7-110">`Service1` is at the root.</span></span> <span data-ttu-id="13be7-111">`Service2` a `Service3` dědit výchozími prvky z `Service1`.</span><span class="sxs-lookup"><span data-stu-id="13be7-111">`Service2` and `Service3` inherit the default elements from `Service1`.</span></span> <span data-ttu-id="13be7-112">`Service4`, `Service5`, `Service6` a `Service7` jsou definované na třetí úrovni hierarchie dědění výchozími prvky z `Service3`.</span><span class="sxs-lookup"><span data-stu-id="13be7-112">`Service4`, `Service5`, `Service6` and `Service7` are defined at a third level of the hierarchy, inheriting the default elements from `Service3`.</span></span> <span data-ttu-id="13be7-113">Nakonec `Service10` a `Service11` jsou na čtvrtou úrovně v hierarchii.</span><span class="sxs-lookup"><span data-stu-id="13be7-113">Finally `Service10` and `Service11` are at a fourth level of the hierarchy.</span></span>  
  
 <span data-ttu-id="13be7-114">Implementovat všechny služby `IDesc` kontraktu.</span><span class="sxs-lookup"><span data-stu-id="13be7-114">All the services implement the `IDesc` contract.</span></span> <span data-ttu-id="13be7-115">Tady je definice `IDesc` rozhraní, které zobrazuje metod v tomto rozhraní zpřístupněny.</span><span class="sxs-lookup"><span data-stu-id="13be7-115">The following is the definition of the `IDesc` interface that shows the methods exposed in this interface.</span></span> <span data-ttu-id="13be7-116">`IDesc` Rozhraní je definováno v souborech Service1.cs.</span><span class="sxs-lookup"><span data-stu-id="13be7-116">The `IDesc` interface is defined in Service1.cs.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="13be7-117">Implementace těchto metod prostřednictvím služeb je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="13be7-117">The implementation of these methods by the services is straightforward.</span></span> <span data-ttu-id="13be7-118">`ListEndpoints` Iteruje přes všechny koncové body služby a vrátí seznam všech koncových bodů, které má služba.</span><span class="sxs-lookup"><span data-stu-id="13be7-118">`ListEndpoints` iterates through all the service endpoints and returns a list of all the endpoints that the service has.</span></span> <span data-ttu-id="13be7-119">`ListServiceBehaviors` Iteruje přes všechny chování, které jsou přidány do služby a vrátí seznam všech chování služby související se službou.</span><span class="sxs-lookup"><span data-stu-id="13be7-119">`ListServiceBehaviors` iterates through all the behaviors added to the service and returns the list of all the service behaviors associated with the service.</span></span> <span data-ttu-id="13be7-120">`ListEndpointBehaviors` chová podobným způsobem jako `ListServiceBehaviors`, ale místo toho vrátí seznam chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="13be7-120">`ListEndpointBehaviors` behaves in a similar way to `ListServiceBehaviors`, but it returns the list of endpoint behaviors instead.</span></span>  
  
 <span data-ttu-id="13be7-121">Tato implementace umožňuje vystavuje klienta vědět, kolik koncových bodů služby a které chování služby a chování koncového bodu se přidaly do služby.</span><span class="sxs-lookup"><span data-stu-id="13be7-121">This implementation allows the client to know how many endpoints the service is exposing and which service behaviors and endpoint behaviors have been added to the service.</span></span> <span data-ttu-id="13be7-122">Klienta, která je implementovaná jako součást vzorku přidá odkaz na službu pro všechny služby v řešení a zobrazuje tyto prvky pro každé z nich služeb.</span><span class="sxs-lookup"><span data-stu-id="13be7-122">The client that has been implemented as part of the sample adds a service reference to all the services in the solution and shows these elements for each one of the services.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="13be7-123">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="13be7-123">To use this sample</span></span>  
  
#### <a name="to-run-the-client"></a><span data-ttu-id="13be7-124">A spusťte tak klienta</span><span class="sxs-lookup"><span data-stu-id="13be7-124">To run the client</span></span>  
  
1.  <span data-ttu-id="13be7-125">Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor ConfigHierarchicalModel.sln.</span><span class="sxs-lookup"><span data-stu-id="13be7-125">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the ConfigHierarchicalModel.sln file.</span></span>  
  
2.  <span data-ttu-id="13be7-126">Klientský projekt ještě nemáte nastavené jako počáteční projekt, postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="13be7-126">The client project is not already set up as the start-up project, follow these steps.</span></span>  
  
    1.  <span data-ttu-id="13be7-127">V **Průzkumníka řešení**, klikněte pravým tlačítkem na řešení a pak vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="13be7-127">In **Solution Explorer**, right-click the solution and then select **Properties**.</span></span>  
  
    2.  <span data-ttu-id="13be7-128">V **společné vlastnosti**vyberte **spouštěný projekt**a potom klikněte na tlačítko **jeden spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="13be7-128">In **Common Properties**, select **Startup Project**, and then click **Single startup project**.</span></span>  
  
    3.  <span data-ttu-id="13be7-129">Z **jeden spouštěný projekt** rozevíracího seznamu, vyberte **klienta**.</span><span class="sxs-lookup"><span data-stu-id="13be7-129">From the **Single startup project** drop-down, select **Client**.</span></span>  
  
    4.  <span data-ttu-id="13be7-130">Klikněte na tlačítko **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="13be7-130">Click **OK** to close the dialog.</span></span>  
  
3.  <span data-ttu-id="13be7-131">Chcete-li ukázku sestavit, stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="13be7-131">To build the sample, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="13be7-132">Pokud chcete spustit klienta, stiskněte Ctrl + F5.</span><span class="sxs-lookup"><span data-stu-id="13be7-132">To run the client, press Ctrl+F5.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13be7-133">Pokud tyto kroky nefungují, ujistěte se, že vaše prostředí je správně nastavený, pomocí následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="13be7-133">If these steps do not work, make sure that your environment has been properly set up, using the following steps:</span></span>  
>   
> 1.  <span data-ttu-id="13be7-134">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="13be7-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
> 2.  <span data-ttu-id="13be7-135">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="13be7-135">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
> 3.  <span data-ttu-id="13be7-136">Spusťte ukázku v jedné nebo více konfigurací počítače, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="13be7-136">To run the sample in a single or multiple computer configurations, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="13be7-137">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="13be7-137">The samples may already be installed on your computer.</span></span> <span data-ttu-id="13be7-138">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="13be7-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="13be7-139">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="13be7-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="13be7-140">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="13be7-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigHierarchicalModel`  
  
## <a name="see-also"></a><span data-ttu-id="13be7-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="13be7-141">See Also</span></span>  
 [<span data-ttu-id="13be7-142">Ukázky správy AppFabric</span><span class="sxs-lookup"><span data-stu-id="13be7-142">AppFabric Management Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193960)
