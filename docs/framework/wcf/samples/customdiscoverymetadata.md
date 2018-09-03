---
title: CustomDiscoveryMetadata
ms.date: 03/30/2017
ms.assetid: c42455fd-3652-4b7e-b698-ab3a2bb52e48
ms.openlocfilehash: 181910db3f1dd6da892f6ae2ddcbf7bd5859ff17
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43465574"
---
# <a name="customdiscoverymetadata"></a><span data-ttu-id="f4bf6-102">CustomDiscoveryMetadata</span><span class="sxs-lookup"><span data-stu-id="f4bf6-102">CustomDiscoveryMetadata</span></span>
<span data-ttu-id="f4bf6-103">Tento příklad ukazuje, jak vložit vlastní XML metadat do zjišťování metadat pro koncový bod zjistitelné vystavený službou.</span><span class="sxs-lookup"><span data-stu-id="f4bf6-103">This sample shows how to insert custom XML metadata into the discovery metadata for a discoverable endpoint exposed by a service.</span></span> <span data-ttu-id="f4bf6-104">Ukázka pak ukazuje, jak extrahovat tento vlastní data a vyhledání služby klienta.</span><span class="sxs-lookup"><span data-stu-id="f4bf6-104">The sample then shows how a client can search for the service and extract this custom data.</span></span> <span data-ttu-id="f4bf6-105">Tato ukázka se skládá ze dvou projektů, klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="f4bf6-105">This sample consists of two projects, service and client.</span></span>  
  
## <a name="service"></a><span data-ttu-id="f4bf6-106">Služba</span><span class="sxs-lookup"><span data-stu-id="f4bf6-106">Service</span></span>  
 <span data-ttu-id="f4bf6-107">V `main` metody, příklad ukazuje, že objekt typu <xref:System.Xml.Linq.XElement> se vyplní požadované pole a je přidán <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>.</span><span class="sxs-lookup"><span data-stu-id="f4bf6-107">In the `main` method, the sample shows that an object of type <xref:System.Xml.Linq.XElement> is populated with the desired fields and is added to the <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>.</span></span> <span data-ttu-id="f4bf6-108">To <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> se přidá do konkrétní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="f4bf6-108">This <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> is added to a particular endpoint.</span></span> <span data-ttu-id="f4bf6-109">Při zjištění tohoto konkrétního koncového bodu zjišťování metadat obsahuje vlastní data, která byla přidána tady.</span><span class="sxs-lookup"><span data-stu-id="f4bf6-109">When that particular endpoint is discovered, the discovery metadata contains the custom data that was added here.</span></span>  
  
## <a name="client"></a><span data-ttu-id="f4bf6-110">Klient</span><span class="sxs-lookup"><span data-stu-id="f4bf6-110">Client</span></span>  
 <span data-ttu-id="f4bf6-111">Vzorek ukazuje <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metoda se volá na <xref:System.ServiceModel.Discovery.DiscoveryClient>.</span><span class="sxs-lookup"><span data-stu-id="f4bf6-111">The sample shows the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method being called on a <xref:System.ServiceModel.Discovery.DiscoveryClient>.</span></span> <span data-ttu-id="f4bf6-112">Výsledná <xref:System.ServiceModel.Discovery.FindResponse> pak dotaz na prvky XML odpovídající a očekávané.</span><span class="sxs-lookup"><span data-stu-id="f4bf6-112">The resulting <xref:System.ServiceModel.Discovery.FindResponse> is then queried for the appropriate and expected XML elements.</span></span> <span data-ttu-id="f4bf6-113">Tyto prvky jsou pak vytištěna do konzoly.</span><span class="sxs-lookup"><span data-stu-id="f4bf6-113">These elements are then printed to the console.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="f4bf6-114">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="f4bf6-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="f4bf6-115">Načítání řešení projektu v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] a sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="f4bf6-115">Load the project solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="f4bf6-116">Nejprve spusťte aplikaci služby, vygenerované v \service\bin\debug [základní adresář řešení] a pak spusťte klientská aplikace vygenerované v \Client\bin\debug [základní adresář řešení]</span><span class="sxs-lookup"><span data-stu-id="f4bf6-116">First run the Service application, generated in [solution base directory]\service\bin\debug, and then run the Client application, generated in [solution base directory]\Client\bin\debug</span></span>  
  
3.  <span data-ttu-id="f4bf6-117">Všimněte si, že služba převede do režimu online, klient vyhledá službu a vypíše publikovat koncový bod metadat.</span><span class="sxs-lookup"><span data-stu-id="f4bf6-117">Note that the service comes online, the client locates the service and prints the metadata published in the endpoint.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f4bf6-118">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="f4bf6-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f4bf6-119">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="f4bf6-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f4bf6-120">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="f4bf6-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f4bf6-121">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f4bf6-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DiscoveryExtensibility\CustomDiscoveryMetadata`  
  
## <a name="see-also"></a><span data-ttu-id="f4bf6-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4bf6-122">See Also</span></span>
