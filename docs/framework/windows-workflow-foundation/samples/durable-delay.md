---
title: Trvalá prodleva
ms.date: 03/30/2017
ms.assetid: 220ec240-b958-430c-81ff-b734a6aa97ae
ms.openlocfilehash: 2a7692e28d60232913ae5d11a90025e59664c0e5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406573"
---
# <a name="durable-delay"></a><span data-ttu-id="627b6-102">Trvalá prodleva</span><span class="sxs-lookup"><span data-stu-id="627b6-102">Durable Delay</span></span>
<span data-ttu-id="627b6-103">Tato ukázka demonstruje použití trvalá prodleva, což je zpoždění, které se přenese pracovního postupu odolné zařízení během zpoždění.</span><span class="sxs-lookup"><span data-stu-id="627b6-103">This sample demonstrates how to use a durable delay, which is a delay that persists the workflow to a durable device during the delay.</span></span> <span data-ttu-id="627b6-104">Ukázkový pracovní postup obsahuje dvě zprávy do konzoly nástroje, které jsou odděleny ke zpoždění.</span><span class="sxs-lookup"><span data-stu-id="627b6-104">The sample workflow contains two messages to the console that are separated by a delay.</span></span> <span data-ttu-id="627b6-105">Když se aktivuje zpoždění, pracovní postup bude uvolněna a čeká 5 sekund do úložiště instancí pracovních postupů, než se znovu načten v paměti.</span><span class="sxs-lookup"><span data-stu-id="627b6-105">When the delay is triggered, the workflow is unloaded and waits 5 seconds in the workflow instance store before being reloaded in memory.</span></span>  
  
## <a name="workflow-details"></a><span data-ttu-id="627b6-106">Podrobnosti pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="627b6-106">Workflow Details</span></span>  
 <span data-ttu-id="627b6-107">Hostitel služby pracovního postupu pracovní postup hostuje a spravuje instancí pracovních postupů pomocí načítání a uvolňování je.</span><span class="sxs-lookup"><span data-stu-id="627b6-107">The workflow service host hosts the workflow and manages the workflow instances by loading and unloading them.</span></span> <span data-ttu-id="627b6-108">Spuštění instance definice pracovního postupu, vzorku nastaví proxy server, která odesílá zprávy <xref:System.ServiceModel.Activities.Receive> aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="627b6-108">To start an instance of the workflow definition, the sample sets a proxy that sends a message to the <xref:System.ServiceModel.Activities.Receive> activity in the workflow.</span></span> <span data-ttu-id="627b6-109"><xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> Je nastavena na `true`, aby mohla vytvořit novou instanci pracovního postupu, jakmile obdrží zprávu.</span><span class="sxs-lookup"><span data-stu-id="627b6-109">The <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> property is set to `true`, enabling it to create a new instance of the workflow once it receives a message.</span></span>  
  
 <span data-ttu-id="627b6-110">Následující seznam obsahuje podrobnosti o nastavení hostitele služby pracovního postupu při inicializaci.</span><span class="sxs-lookup"><span data-stu-id="627b6-110">The following list details the set-up by the workflow service host during initialization.</span></span>  
  
1.  <span data-ttu-id="627b6-111">Vytvoří hostitele služby s adresou (http://localhost:8080/Client).</span><span class="sxs-lookup"><span data-stu-id="627b6-111">Creates a service host with an address (http://localhost:8080/Client).</span></span>  
  
2.  <span data-ttu-id="627b6-112">Vytvoří koncový bod v hostiteli služby k umožnění komunikace s <xref:System.ServiceModel.Activities.Receive> aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="627b6-112">Creates an endpoint in the service host to enable communication with the <xref:System.ServiceModel.Activities.Receive> activity inside the workflow.</span></span>  
  
3.  <span data-ttu-id="627b6-113">Nastaví úložiště instancí SQL.</span><span class="sxs-lookup"><span data-stu-id="627b6-113">Sets up a SQL instance store.</span></span>  
  
4.  <span data-ttu-id="627b6-114">Přidá chování instance uvolnění z paměti, který určuje podmínky, za kterých by měl hostitel služby pracovního postupu uvolnit instance pracovního postupu do úložiště trvalosti SQL.</span><span class="sxs-lookup"><span data-stu-id="627b6-114">Adds an unload instance behavior that specifies the conditions under which the workflow service host should unload a workflow instance to the SQL persistence store.</span></span> <span data-ttu-id="627b6-115">V tomto příkladu je uvolněn instance okamžitě po ukončení pracovního postupu nečinnosti (v případě, že se aktivuje zpoždění).</span><span class="sxs-lookup"><span data-stu-id="627b6-115">For this sample, it unloads the instance immediately after the workflow goes idle (when the delay is triggered).</span></span>  
  
5.  <span data-ttu-id="627b6-116">Vytvoří proxy, která odešle zprávu <xref:System.ServiceModel.Activities.Receive> aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="627b6-116">Creates the proxy that sends a message to the <xref:System.ServiceModel.Activities.Receive> activity in the workflow.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="627b6-117">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="627b6-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="627b6-118">Nastavení databáze trvalosti.</span><span class="sxs-lookup"><span data-stu-id="627b6-118">Set up the persistence database.</span></span>  
  
    1.  <span data-ttu-id="627b6-119">Otevřít [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="627b6-119">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="627b6-120">Přejděte [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] adresáře (C:\Windows\Microsoft.NET\Framework\v4. X\\).</span><span class="sxs-lookup"><span data-stu-id="627b6-120">Navigate to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] directory (C:\Windows\Microsoft.NET\Framework\v4.X\\).</span></span>  
  
    3.  <span data-ttu-id="627b6-121">Upravte soubor WorkflowManagementService.exe.config a přidejte následující připojovací řetězec uvnitř <`database`> element.</span><span class="sxs-lookup"><span data-stu-id="627b6-121">Edit the WorkflowManagementService.exe.config file and add the following connection string inside the <`database`> element.</span></span>  
  
        ```xml  
        <database connectionString="Data Source=localhost\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True;Asynchronous Processing=True" />  
        ```  
  
    4.  <span data-ttu-id="627b6-122">Přejděte do adresáře DurableDelay\CS.</span><span class="sxs-lookup"><span data-stu-id="627b6-122">Navigate to the DurableDelay\CS directory.</span></span>  
  
    5.  <span data-ttu-id="627b6-123">Spusťte Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="627b6-123">Run Setup.cmd.</span></span>  
  
2.  <span data-ttu-id="627b6-124">Spustit [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] pomocí zvýšenou úroveň oprávnění kliknutím pravým tlačítkem myši [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikonu a vyberete **spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="627b6-124">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] using elevated permissions by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
3.  <span data-ttu-id="627b6-125">Otevřete soubor řešení Delay.sln.</span><span class="sxs-lookup"><span data-stu-id="627b6-125">Open the Delay.sln solution file.</span></span>  
  
4.  <span data-ttu-id="627b6-126">Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.</span><span class="sxs-lookup"><span data-stu-id="627b6-126">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
5.  <span data-ttu-id="627b6-127">Stisknutím kláves CTRL + F5 spusťte řešení.</span><span class="sxs-lookup"><span data-stu-id="627b6-127">Press CTRL+F5 to run the solution.</span></span>  
  
#### <a name="to-uninstall-this-sample"></a><span data-ttu-id="627b6-128">Chcete-li odinstalovat tuto ukázku</span><span class="sxs-lookup"><span data-stu-id="627b6-128">To uninstall this sample</span></span>  
  
1.  <span data-ttu-id="627b6-129">Otevřít [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="627b6-129">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
2.  <span data-ttu-id="627b6-130">Přejděte do adresáře DurableDelay\CS.</span><span class="sxs-lookup"><span data-stu-id="627b6-130">Navigate to the DurableDelay\CS directory.</span></span>  
  
3.  <span data-ttu-id="627b6-131">Spusťte Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="627b6-131">Run Cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="627b6-132">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="627b6-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="627b6-133">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="627b6-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="627b6-134">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="627b6-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="627b6-135">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="627b6-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelay`