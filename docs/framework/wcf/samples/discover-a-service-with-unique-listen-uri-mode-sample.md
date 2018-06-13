---
title: Ukázka zjišťování služby s vlastností ListenUriMode nastavenou na Unique
ms.date: 03/30/2017
ms.assetid: 9a6d35b2-0469-43c8-a0c9-63623e3d2733
ms.openlocfilehash: e6129594df6170f94a06caa08a9f16e4770bbfd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33501452"
---
# <a name="discover-a-service-with-unique-listen-uri-mode-sample"></a><span data-ttu-id="33f6b-102">Ukázka zjišťování služby s vlastností ListenUriMode nastavenou na Unique</span><span class="sxs-lookup"><span data-stu-id="33f6b-102">Discover a Service with Unique Listen Uri Mode Sample</span></span>
<span data-ttu-id="33f6b-103">Tento příklad ukazuje, jak zjistit službu, která má <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> vlastnost nastavena na hodnotu <xref:System.ServiceModel.Description.ListenUriMode.Unique>.</span><span class="sxs-lookup"><span data-stu-id="33f6b-103">This sample demonstrates how to discover a service that has the <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> property set to <xref:System.ServiceModel.Description.ListenUriMode.Unique>.</span></span> <span data-ttu-id="33f6b-104">Když <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> je nastavena na <xref:System.ServiceModel.Description.ListenUriMode.Unique>, je zajištěno, že adrese ListenUri být jedinečný, a to nastavením portu být jedinečný, nebo pro danou cestu jako jedinečný identifikátor GUID připojením.</span><span class="sxs-lookup"><span data-stu-id="33f6b-104">When the <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> property is set to <xref:System.ServiceModel.Description.ListenUriMode.Unique>, the ListenUri is ensured to be unique by either setting the port to be unique or for the path to be unique by appending a GUID.</span></span>  
  
### <a name="features-on-the-service"></a><span data-ttu-id="33f6b-105">Funkce ve službě</span><span class="sxs-lookup"><span data-stu-id="33f6b-105">Features on the Service</span></span>  
 <span data-ttu-id="33f6b-106"><xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> Je nastavena na <xref:System.ServiceModel.Description.ListenUriMode.Unique> pro koncový bod TCP.</span><span class="sxs-lookup"><span data-stu-id="33f6b-106">The <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> property is set to <xref:System.ServiceModel.Description.ListenUriMode.Unique> for the TCP endpoint.</span></span> <span data-ttu-id="33f6b-107">Služba je potom k zjistitelný prostřednictvím <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> koncový bod.</span><span class="sxs-lookup"><span data-stu-id="33f6b-107">The service is then made discoverable over a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint.</span></span>  
  
### <a name="features-on-the-client"></a><span data-ttu-id="33f6b-108">Funkce na straně klienta</span><span class="sxs-lookup"><span data-stu-id="33f6b-108">Features on the Client</span></span>  
 <span data-ttu-id="33f6b-109">Tento klient připojí ke službě pomocí správného `Via.Uri` pomocí <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="33f6b-109">This client connects to the service using the correct `Via.Uri` by using the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method.</span></span> <span data-ttu-id="33f6b-110"><xref:System.ServiceModel.Discovery.FindResponse> , Vrátí metoda je pak dotazován na tom, zda obsahuje platné <xref:System.ServiceModel.Endpoint.ListenUri%2A> a jestli je jiný než `Address.Uri`.</span><span class="sxs-lookup"><span data-stu-id="33f6b-110">The <xref:System.ServiceModel.Discovery.FindResponse> that is returned from the method is then queried for whether it contains a valid <xref:System.ServiceModel.Endpoint.ListenUri%2A> and whether it is different than `Address.Uri`.</span></span> <span data-ttu-id="33f6b-111">Příslušné informace, které se pak předá do `InvokeCalculatorService` metoda.</span><span class="sxs-lookup"><span data-stu-id="33f6b-111">The appropriate information is then passed to the `InvokeCalculatorService` method.</span></span> <span data-ttu-id="33f6b-112">V `InvokeCalculatorService` metoda, <xref:System.ServiceModel.Endpoint.ListenUri%2A> byla předaná volající funkcí, pak `ClientViaBehavior` s správný `Via.Uri` je přidána ke koncovému bodu klienta.</span><span class="sxs-lookup"><span data-stu-id="33f6b-112">In the `InvokeCalculatorService` method, the <xref:System.ServiceModel.Endpoint.ListenUri%2A> was passed in by the caller, then a `ClientViaBehavior` with the correct `Via.Uri` is added to the client’s endpoint.</span></span>  
  
##### <a name="to-use-this-sample"></a><span data-ttu-id="33f6b-113">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="33f6b-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="33f6b-114">Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete UniqueListenUriMode.sln.</span><span class="sxs-lookup"><span data-stu-id="33f6b-114">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open UniqueListenUriMode.sln.</span></span>  
  
2.  <span data-ttu-id="33f6b-115">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="33f6b-115">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="33f6b-116">Spusťte aplikaci služby, která se generují ve složce \service\bin\debug [základní adresář řešení].</span><span class="sxs-lookup"><span data-stu-id="33f6b-116">Run the service application, which is generated in the [solution base directory]\service\bin\debug folder.</span></span>  
  
4.  <span data-ttu-id="33f6b-117">Spusťte klientskou aplikaci, která se generují ve složce \Client\bin\debug [základní adresář řešení].</span><span class="sxs-lookup"><span data-stu-id="33f6b-117">Run the client application, which is generated in the [solution base directory]\Client\bin\debug folder.</span></span>  
  
     <span data-ttu-id="33f6b-118">Klient vyhledá spuštěnou službu a zapíše do konzoly metadat, které zveřejnil koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="33f6b-118">The client locates the running service and writes to the console the metadata published by the service’s endpoint.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="33f6b-119">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="33f6b-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="33f6b-120">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="33f6b-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="33f6b-121">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="33f6b-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="33f6b-122">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="33f6b-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\UniqueListenUriMode`  
  
## <a name="see-also"></a><span data-ttu-id="33f6b-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="33f6b-123">See Also</span></span>
