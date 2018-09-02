---
title: Ukázka asynchronního hledání
ms.date: 03/30/2017
ms.assetid: 7a713a25-c1f4-42e1-8c4a-93d64ca45a3b
ms.openlocfilehash: 37edcb4d1f04eb56d3f24ca3acc3543d7f9696f5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43424388"
---
# <a name="asynchronous-find-sample"></a><span data-ttu-id="ba14a-102">Ukázka asynchronního hledání</span><span class="sxs-lookup"><span data-stu-id="ba14a-102">Asynchronous Find Sample</span></span>
<span data-ttu-id="ba14a-103">Tento příklad ukazuje způsob použití operace asynchronního hledání z klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="ba14a-103">This sample shows how to use the asynchronous find operation from a client application.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="ba14a-104">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ba14a-104">Sample Details</span></span>  
 <span data-ttu-id="ba14a-105">Výhodou po tomto vzoru návrhu je, že klient obdrží oznámení asynchronně koncových bodů umístěný jako výsledek požadavku hledání.</span><span class="sxs-lookup"><span data-stu-id="ba14a-105">The benefit of following this design pattern is that the client is notified asynchronously of the endpoints located as a result of the find request.</span></span> <span data-ttu-id="ba14a-106">Pokud chcete zobrazit, jak to funguje, otevřete soubor Client.cs.</span><span class="sxs-lookup"><span data-stu-id="ba14a-106">To see how this works, open the Client.cs file.</span></span> <span data-ttu-id="ba14a-107">Poznámka: <xref:System.ServiceModel.Discovery.DiscoveryClient> objekt má dva delegáty připojené k jeho obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="ba14a-107">Note the <xref:System.ServiceModel.Discovery.DiscoveryClient> object has two delegates attached to its event handlers.</span></span> <span data-ttu-id="ba14a-108">Jeden delegáta je volána, když <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> událost se vyvolá, a druhé je volána pokaždé, když <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="ba14a-108">One delegate is called when a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> event is raised and another is called each time a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> event is raised.</span></span> <span data-ttu-id="ba14a-109">Tato ukázka vysvětluje, jak tento vzor můžete využít ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ba14a-109">The sample shows how you can utilize this pattern in your application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ba14a-110">Tato ukázka používá koncové body HTTP a spustit, musí být přidán správné seznamy ACL adresy URL.</span><span class="sxs-lookup"><span data-stu-id="ba14a-110">This sample uses HTTP endpoints and to run, proper URL ACLs must be added.</span></span> <span data-ttu-id="ba14a-111">Další informace najdete v tématu [konfigurace HTTP a HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="ba14a-111">For more information, see [Configuring HTTP and HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="ba14a-112">Provádění se zvýšenými oprávněními následující příkaz by měl přidat příslušné seznamy ACL.</span><span class="sxs-lookup"><span data-stu-id="ba14a-112">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="ba14a-113">Můžete se k nahrazení domény a uživatelské jméno pro následující argumenty, pokud příkaz nefunguje, jak je.</span><span class="sxs-lookup"><span data-stu-id="ba14a-113">You may want to substitute your domain and username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ba14a-114">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="ba14a-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ba14a-115">Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete AsyncFind.sln.</span><span class="sxs-lookup"><span data-stu-id="ba14a-115">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the AsyncFind.sln.</span></span>  
  
2.  <span data-ttu-id="ba14a-116">Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.</span><span class="sxs-lookup"><span data-stu-id="ba14a-116">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="ba14a-117">Otevřít [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek a přejděte do adresáře \WCF\Basic\Discovery\AsyncFind\CS\service\bin\Debug nebo \WCF\Basic\Discovery\AsyncFind\VB\service\bin\Debug a spustit Service.exe.</span><span class="sxs-lookup"><span data-stu-id="ba14a-117">Open a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt and navigate to the \WCF\Basic\Discovery\AsyncFind\CS\service\bin\Debug or \WCF\Basic\Discovery\AsyncFind\VB\service\bin\Debug directory and run Service.exe.</span></span>  
  
4.  <span data-ttu-id="ba14a-118">Po spuštění služby, přejděte do \WCF\Basic\Discovery\AsyncFind\CS\client\bin\Debug nebo WCF\Basic\Discovery\AsyncFind\VB\client\bin\Debug adresáře a spusťte Client.exe.</span><span class="sxs-lookup"><span data-stu-id="ba14a-118">After the service has started, navigate to the \WCF\Basic\Discovery\AsyncFind\CS\client\bin\Debug or WCF\Basic\Discovery\AsyncFind\VB\client\bin\Debug directory and run Client.exe.</span></span>  
  
5.  <span data-ttu-id="ba14a-119">Podívejte se, že klient moci vyhledat a volání služby.</span><span class="sxs-lookup"><span data-stu-id="ba14a-119">Observe the client is able to locate and call the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ba14a-120">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="ba14a-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ba14a-121">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ba14a-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ba14a-122">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="ba14a-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ba14a-123">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="ba14a-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\AsyncFind`  
  
## <a name="see-also"></a><span data-ttu-id="ba14a-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="ba14a-124">See Also</span></span>
