---
title: CustomDiscoveryMetadata
ms.date: 03/30/2017
ms.assetid: c42455fd-3652-4b7e-b698-ab3a2bb52e48
ms.openlocfilehash: 3e3a173d99f2ba0a2fb33dfd8f91908f03e3e871
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33501046"
---
# <a name="customdiscoverymetadata"></a><span data-ttu-id="725f9-102">CustomDiscoveryMetadata</span><span class="sxs-lookup"><span data-stu-id="725f9-102">CustomDiscoveryMetadata</span></span>
<span data-ttu-id="725f9-103">Tento příklad ukazuje způsob vložení vlastních metadat XML do zjišťování metadat pro koncový bod zjistitelný zveřejněný prostřednictvím služby.</span><span class="sxs-lookup"><span data-stu-id="725f9-103">This sample shows how to insert custom XML metadata into the discovery metadata for a discoverable endpoint exposed by a service.</span></span> <span data-ttu-id="725f9-104">Ukázka pak ukazuje, jak klient vyhledejte službu a extrahovat tento vlastní data.</span><span class="sxs-lookup"><span data-stu-id="725f9-104">The sample then shows how a client can search for the service and extract this custom data.</span></span> <span data-ttu-id="725f9-105">Tato ukázka se skládá z dva projekty, klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="725f9-105">This sample consists of two projects, service and client.</span></span>  
  
## <a name="service"></a><span data-ttu-id="725f9-106">Služba</span><span class="sxs-lookup"><span data-stu-id="725f9-106">Service</span></span>  
 <span data-ttu-id="725f9-107">V `main` metody ukázky ukazuje, že objekt typu <xref:System.Xml.Linq.XElement> naplněný požadovaná pole a přidají se do <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>.</span><span class="sxs-lookup"><span data-stu-id="725f9-107">In the `main` method, the sample shows that an object of type <xref:System.Xml.Linq.XElement> is populated with the desired fields and is added to the <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>.</span></span> <span data-ttu-id="725f9-108">To <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> je přidán do konkrétní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="725f9-108">This <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> is added to a particular endpoint.</span></span> <span data-ttu-id="725f9-109">Pokud je zjištěno, že konkrétní koncový bod, zjišťování metadat obsahuje vlastní data, která byla přidána zde.</span><span class="sxs-lookup"><span data-stu-id="725f9-109">When that particular endpoint is discovered, the discovery metadata contains the custom data that was added here.</span></span>  
  
## <a name="client"></a><span data-ttu-id="725f9-110">Klient</span><span class="sxs-lookup"><span data-stu-id="725f9-110">Client</span></span>  
 <span data-ttu-id="725f9-111">Ukázka ukazuje <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metoda volaného na <xref:System.ServiceModel.Discovery.DiscoveryClient>.</span><span class="sxs-lookup"><span data-stu-id="725f9-111">The sample shows the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method being called on a <xref:System.ServiceModel.Discovery.DiscoveryClient>.</span></span> <span data-ttu-id="725f9-112">Výsledná <xref:System.ServiceModel.Discovery.FindResponse> je pak dotazován na elementy XML odpovídající a očekávané.</span><span class="sxs-lookup"><span data-stu-id="725f9-112">The resulting <xref:System.ServiceModel.Discovery.FindResponse> is then queried for the appropriate and expected XML elements.</span></span> <span data-ttu-id="725f9-113">Tyto prvky jsou pak vytištěny ke konzole.</span><span class="sxs-lookup"><span data-stu-id="725f9-113">These elements are then printed to the console.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="725f9-114">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="725f9-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="725f9-115">Načtení projektu řešení v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] a sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="725f9-115">Load the project solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="725f9-116">Nejprve spusťte aplikaci služby, vygenerovaných \service\bin\debug [základní adresář řešení] a pak spusťte klientské aplikace, vygenerovaných \Client\bin\debug [základní adresář řešení]</span><span class="sxs-lookup"><span data-stu-id="725f9-116">First run the Service application, generated in [solution base directory]\service\bin\debug, and then run the Client application, generated in [solution base directory]\Client\bin\debug</span></span>  
  
3.  <span data-ttu-id="725f9-117">Všimněte si, že služba přepne do režimu online, klient vyhledá službu a vypíše metadata publikované v koncovém bodě.</span><span class="sxs-lookup"><span data-stu-id="725f9-117">Note that the service comes online, the client locates the service and prints the metadata published in the endpoint.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="725f9-118">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="725f9-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="725f9-119">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="725f9-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="725f9-120">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="725f9-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="725f9-121">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="725f9-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DiscoveryExtensibility\CustomDiscoveryMetadata`  
  
## <a name="see-also"></a><span data-ttu-id="725f9-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="725f9-122">See Also</span></span>
