---
title: Ukázka zjišťování služby s vlastností ListenUriMode nastavenou na Unique
ms.date: 03/30/2017
ms.assetid: 9a6d35b2-0469-43c8-a0c9-63623e3d2733
ms.openlocfilehash: 7e1c5ae0cb1a44c72a27566035b4bc20acbf1614
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47077041"
---
# <a name="discover-a-service-with-unique-listen-uri-mode-sample"></a><span data-ttu-id="b6a48-102">Ukázka zjišťování služby s vlastností ListenUriMode nastavenou na Unique</span><span class="sxs-lookup"><span data-stu-id="b6a48-102">Discover a Service with Unique Listen Uri Mode Sample</span></span>
<span data-ttu-id="b6a48-103">Tato ukázka předvádí, jak zjistit službu, která má <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> nastavenou na <xref:System.ServiceModel.Description.ListenUriMode.Unique>.</span><span class="sxs-lookup"><span data-stu-id="b6a48-103">This sample demonstrates how to discover a service that has the <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> property set to <xref:System.ServiceModel.Description.ListenUriMode.Unique>.</span></span> <span data-ttu-id="b6a48-104">Když <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> je nastavena na <xref:System.ServiceModel.Description.ListenUriMode.Unique>, identifikátorem ListenUri je, že jsou splněné být jedinečný, tak, že nastavíte jedinečný port nebo pro cestu být jedinečný identifikátor GUID připojením.</span><span class="sxs-lookup"><span data-stu-id="b6a48-104">When the <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> property is set to <xref:System.ServiceModel.Description.ListenUriMode.Unique>, the ListenUri is ensured to be unique by either setting the port to be unique or for the path to be unique by appending a GUID.</span></span>  
  
### <a name="features-on-the-service"></a><span data-ttu-id="b6a48-105">Funkce služby</span><span class="sxs-lookup"><span data-stu-id="b6a48-105">Features on the Service</span></span>  
 <span data-ttu-id="b6a48-106"><xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> Je nastavena na <xref:System.ServiceModel.Description.ListenUriMode.Unique> pro koncový bod TCP.</span><span class="sxs-lookup"><span data-stu-id="b6a48-106">The <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> property is set to <xref:System.ServiceModel.Description.ListenUriMode.Unique> for the TCP endpoint.</span></span> <span data-ttu-id="b6a48-107">Služba poté je proveden zjistitelný prostřednictvím <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="b6a48-107">The service is then made discoverable over a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint.</span></span>  
  
### <a name="features-on-the-client"></a><span data-ttu-id="b6a48-108">Funkce na straně klienta</span><span class="sxs-lookup"><span data-stu-id="b6a48-108">Features on the Client</span></span>  
 <span data-ttu-id="b6a48-109">Tento klient připojí ke službě pomocí správné `Via.Uri` pomocí <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b6a48-109">This client connects to the service using the correct `Via.Uri` by using the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method.</span></span> <span data-ttu-id="b6a48-110"><xref:System.ServiceModel.Discovery.FindResponse> Vrácené z metody pak dotaz na tom, zda obsahuje platné <xref:System.ServiceModel.Endpoint.ListenUri%2A> a určuje, zda se liší od `Address.Uri`.</span><span class="sxs-lookup"><span data-stu-id="b6a48-110">The <xref:System.ServiceModel.Discovery.FindResponse> that is returned from the method is then queried for whether it contains a valid <xref:System.ServiceModel.Endpoint.ListenUri%2A> and whether it is different than `Address.Uri`.</span></span> <span data-ttu-id="b6a48-111">Příslušné informace je pak předán `InvokeCalculatorService` metody.</span><span class="sxs-lookup"><span data-stu-id="b6a48-111">The appropriate information is then passed to the `InvokeCalculatorService` method.</span></span> <span data-ttu-id="b6a48-112">V `InvokeCalculatorService` metody <xref:System.ServiceModel.Endpoint.ListenUri%2A> byla předána volajícím, o `ClientViaBehavior` se správnými `Via.Uri` se přidá do koncového bodu klienta.</span><span class="sxs-lookup"><span data-stu-id="b6a48-112">In the `InvokeCalculatorService` method, the <xref:System.ServiceModel.Endpoint.ListenUri%2A> was passed in by the caller, then a `ClientViaBehavior` with the correct `Via.Uri` is added to the client’s endpoint.</span></span>  
  
##### <a name="to-use-this-sample"></a><span data-ttu-id="b6a48-113">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="b6a48-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="b6a48-114">Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete UniqueListenUriMode.sln.</span><span class="sxs-lookup"><span data-stu-id="b6a48-114">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open UniqueListenUriMode.sln.</span></span>  
  
2.  <span data-ttu-id="b6a48-115">Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="b6a48-115">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="b6a48-116">Spusťte aplikaci služby, který je generován ve složce \service\bin\debug [základní adresář řešení].</span><span class="sxs-lookup"><span data-stu-id="b6a48-116">Run the service application, which is generated in the [solution base directory]\service\bin\debug folder.</span></span>  
  
4.  <span data-ttu-id="b6a48-117">Spuštění klientské aplikace, který je generován ve složce \Client\bin\debug [základní adresář řešení].</span><span class="sxs-lookup"><span data-stu-id="b6a48-117">Run the client application, which is generated in the [solution base directory]\Client\bin\debug folder.</span></span>  
  
     <span data-ttu-id="b6a48-118">Klient vyhledá spuštěnou službu a zapisuje do konzoly metadat publikoval(a) koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="b6a48-118">The client locates the running service and writes to the console the metadata published by the service’s endpoint.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b6a48-119">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="b6a48-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b6a48-120">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="b6a48-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b6a48-121">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="b6a48-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b6a48-122">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="b6a48-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\UniqueListenUriMode`  
  
## <a name="see-also"></a><span data-ttu-id="b6a48-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="b6a48-123">See Also</span></span>
