---
title: "Ukázka asynchronního hledání"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a713a25-c1f4-42e1-8c4a-93d64ca45a3b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 229e2ff6e630527e3735e3c48f698f582b0b60f8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="asynchronous-find-sample"></a><span data-ttu-id="db463-102">Ukázka asynchronního hledání</span><span class="sxs-lookup"><span data-stu-id="db463-102">Asynchronous Find Sample</span></span>
<span data-ttu-id="db463-103">Tento příklad ukazuje způsob použití operace asynchronní hledání z klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="db463-103">This sample shows how to use the asynchronous find operation from a client application.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="db463-104">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="db463-104">Sample Details</span></span>  
 <span data-ttu-id="db463-105">Výhodou následující tohoto vzoru návrhu je, že klient proběhne asynchronně koncových bodů umístěný jako výsledek požadavku najít.</span><span class="sxs-lookup"><span data-stu-id="db463-105">The benefit of following this design pattern is that the client is notified asynchronously of the endpoints located as a result of the find request.</span></span> <span data-ttu-id="db463-106">Pokud chcete zobrazit, jak to funguje, otevřete soubor Client.cs.</span><span class="sxs-lookup"><span data-stu-id="db463-106">To see how this works, open the Client.cs file.</span></span> <span data-ttu-id="db463-107">Poznámka: <xref:System.ServiceModel.Discovery.DiscoveryClient> objekt má dva delegáti připojené k jeho obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="db463-107">Note the <xref:System.ServiceModel.Discovery.DiscoveryClient> object has two delegates attached to its event handlers.</span></span> <span data-ttu-id="db463-108">Jeden delegáta je volána, když <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> událost se vyvolá, a jiné se nazývá pokaždé, když <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="db463-108">One delegate is called when a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> event is raised and another is called each time a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> event is raised.</span></span> <span data-ttu-id="db463-109">Ukázka ukazuje, jak můžete použít tento vzor ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="db463-109">The sample shows how you can utilize this pattern in your application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="db463-110">Tato ukázka používá koncových bodů protokolu HTTP a pokud chcete spustit, musí být přidán správné seznamy ACL adresy URL.</span><span class="sxs-lookup"><span data-stu-id="db463-110">This sample uses HTTP endpoints and to run, proper URL ACLs must be added.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="db463-111">[Konfigurace HTTP a HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="db463-111"> [Configuring HTTP and HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="db463-112">Spuštěním následujícího příkazu na zvýšená oprávnění měli přidat příslušné seznamy ACL.</span><span class="sxs-lookup"><span data-stu-id="db463-112">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="db463-113">Chcete nahradit domény a uživatelské jméno pro následující argumenty, pokud příkaz nefunguje, protože je.</span><span class="sxs-lookup"><span data-stu-id="db463-113">You may want to substitute your domain and username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="db463-114">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="db463-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="db463-115">Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete AsyncFind.sln.</span><span class="sxs-lookup"><span data-stu-id="db463-115">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the AsyncFind.sln.</span></span>  
  
2.  <span data-ttu-id="db463-116">Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.</span><span class="sxs-lookup"><span data-stu-id="db463-116">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="db463-117">Otevřete [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek a přejděte do adresáře \WCF\Basic\Discovery\AsyncFind\CS\service\bin\Debug nebo \WCF\Basic\Discovery\AsyncFind\VB\service\bin\Debug a spustit Service.exe.</span><span class="sxs-lookup"><span data-stu-id="db463-117">Open a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt and navigate to the \WCF\Basic\Discovery\AsyncFind\CS\service\bin\Debug or \WCF\Basic\Discovery\AsyncFind\VB\service\bin\Debug directory and run Service.exe.</span></span>  
  
4.  <span data-ttu-id="db463-118">Po spuštění služby, přejděte na daný adresář WCF\Basic\Discovery\AsyncFind\VB\client\bin\Debug nebo \WCF\Basic\Discovery\AsyncFind\CS\client\bin\Debug a spusťte Client.exe.</span><span class="sxs-lookup"><span data-stu-id="db463-118">After the service has started, navigate to the \WCF\Basic\Discovery\AsyncFind\CS\client\bin\Debug or WCF\Basic\Discovery\AsyncFind\VB\client\bin\Debug directory and run Client.exe.</span></span>  
  
5.  <span data-ttu-id="db463-119">Zkontrolujte, že klient je možné najít a volání služby.</span><span class="sxs-lookup"><span data-stu-id="db463-119">Observe the client is able to locate and call the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="db463-120">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="db463-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="db463-121">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="db463-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="db463-122">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="db463-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="db463-123">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="db463-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\AsyncFind`  
  
## <a name="see-also"></a><span data-ttu-id="db463-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="db463-124">See Also</span></span>
