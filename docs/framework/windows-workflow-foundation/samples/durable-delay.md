---
title: Trvanlivý zpoždění
ms.date: 03/30/2017
ms.assetid: 220ec240-b958-430c-81ff-b734a6aa97ae
ms.openlocfilehash: 5307b8144e17f91cd3ba8c2e385492f86c167820
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516019"
---
# <a name="durable-delay"></a><span data-ttu-id="a6ac8-102">Trvanlivý zpoždění</span><span class="sxs-lookup"><span data-stu-id="a6ac8-102">Durable Delay</span></span>
<span data-ttu-id="a6ac8-103">Tento příklad znázorňuje způsob použití trvanlivý zpoždění, což je zpoždění, která je uchována pracovního postupu trvanlivý zařízení během zpoždění.</span><span class="sxs-lookup"><span data-stu-id="a6ac8-103">This sample demonstrates how to use a durable delay, which is a delay that persists the workflow to a durable device during the delay.</span></span> <span data-ttu-id="a6ac8-104">Ukázkový pracovní postup obsahuje dvě zpráv do konzoly, které jsou odděleny zpoždění.</span><span class="sxs-lookup"><span data-stu-id="a6ac8-104">The sample workflow contains two messages to the console that are separated by a delay.</span></span> <span data-ttu-id="a6ac8-105">Když se aktivuje zpoždění pracovní postup je odpojen a čeká 5 sekund v úložišti instance pracovního postupu, než se znovu načíst v paměti.</span><span class="sxs-lookup"><span data-stu-id="a6ac8-105">When the delay is triggered, the workflow is unloaded and waits 5 seconds in the workflow instance store before being reloaded in memory.</span></span>  
  
## <a name="workflow-details"></a><span data-ttu-id="a6ac8-106">Podrobnosti pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="a6ac8-106">Workflow Details</span></span>  
 <span data-ttu-id="a6ac8-107">Hostitel služby pracovního postupu hostuje pracovního postupu a instance pracovního postupu podle načítání a uvolňování je spravuje.</span><span class="sxs-lookup"><span data-stu-id="a6ac8-107">The workflow service host hosts the workflow and manages the workflow instances by loading and unloading them.</span></span> <span data-ttu-id="a6ac8-108">Pokud chcete spustit instance definice pracovního postupu, ukázky nastaví proxy server, který odešle zprávu, která <xref:System.ServiceModel.Activities.Receive> aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="a6ac8-108">To start an instance of the workflow definition, the sample sets a proxy that sends a message to the <xref:System.ServiceModel.Activities.Receive> activity in the workflow.</span></span> <span data-ttu-id="a6ac8-109"><xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> Je nastavena na `true`, kterých je možné vytvořit novou instanci pracovního postupu, jakmile obdrží zprávu.</span><span class="sxs-lookup"><span data-stu-id="a6ac8-109">The <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> property is set to `true`, enabling it to create a new instance of the workflow once it receives a message.</span></span>  
  
 <span data-ttu-id="a6ac8-110">Následující seznam popisuje, o nastavení hostitele služby pracovního postupu během inicializace.</span><span class="sxs-lookup"><span data-stu-id="a6ac8-110">The following list details the set-up by the workflow service host during initialization.</span></span>  
  
1.  <span data-ttu-id="a6ac8-111">Vytvoří hostitele služby s adresou (http://localhost:8080/Client).</span><span class="sxs-lookup"><span data-stu-id="a6ac8-111">Creates a service host with an address (http://localhost:8080/Client).</span></span>  
  
2.  <span data-ttu-id="a6ac8-112">Vytvoří koncový bod na hostiteli služby k umožnění komunikace s <xref:System.ServiceModel.Activities.Receive> aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="a6ac8-112">Creates an endpoint in the service host to enable communication with the <xref:System.ServiceModel.Activities.Receive> activity inside the workflow.</span></span>  
  
3.  <span data-ttu-id="a6ac8-113">Nastaví instance úložiště SQL.</span><span class="sxs-lookup"><span data-stu-id="a6ac8-113">Sets up a SQL instance store.</span></span>  
  
4.  <span data-ttu-id="a6ac8-114">Přidá uvolnění instance chování, které určuje podmínky, za kterých by měl hostitel služby pracovního postupu uvolnit instanci pracovního postupu do úložiště trvalosti SQL.</span><span class="sxs-lookup"><span data-stu-id="a6ac8-114">Adds an unload instance behavior that specifies the conditions under which the workflow service host should unload a workflow instance to the SQL persistence store.</span></span> <span data-ttu-id="a6ac8-115">Tato ukázka se uvolní instanci, ihned po pracovní postup přejde nečinnosti (když se spustí zpoždění).</span><span class="sxs-lookup"><span data-stu-id="a6ac8-115">For this sample, it unloads the instance immediately after the workflow goes idle (when the delay is triggered).</span></span>  
  
5.  <span data-ttu-id="a6ac8-116">Vytvoří proxy server, který odešle zprávu, která <xref:System.ServiceModel.Activities.Receive> aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="a6ac8-116">Creates the proxy that sends a message to the <xref:System.ServiceModel.Activities.Receive> activity in the workflow.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="a6ac8-117">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="a6ac8-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="a6ac8-118">Nastavení databáze trvalost.</span><span class="sxs-lookup"><span data-stu-id="a6ac8-118">Set up the persistence database.</span></span>  
  
    1.  <span data-ttu-id="a6ac8-119">Otevřete [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a6ac8-119">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="a6ac8-120">Přejděte do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] adresáře (C:\Windows\Microsoft.NET\Framework\v4. X\\).</span><span class="sxs-lookup"><span data-stu-id="a6ac8-120">Navigate to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] directory (C:\Windows\Microsoft.NET\Framework\v4.X\\).</span></span>  
  
    3.  <span data-ttu-id="a6ac8-121">Upravte soubor WorkflowManagementService.exe.config a přidejte následující připojovací řetězec uvnitř <`database`> elementu.</span><span class="sxs-lookup"><span data-stu-id="a6ac8-121">Edit the WorkflowManagementService.exe.config file and add the following connection string inside the <`database`> element.</span></span>  
  
        ```xml  
        <database connectionString="Data Source=localhost\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True;Asynchronous Processing=True" />  
        ```  
  
    4.  <span data-ttu-id="a6ac8-122">Přejděte do adresáře DurableDelay\CS.</span><span class="sxs-lookup"><span data-stu-id="a6ac8-122">Navigate to the DurableDelay\CS directory.</span></span>  
  
    5.  <span data-ttu-id="a6ac8-123">Spusťte Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="a6ac8-123">Run Setup.cmd.</span></span>  
  
2.  <span data-ttu-id="a6ac8-124">Spustit [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] pomocí zvýšenými oprávněními kliknutím pravým tlačítkem myši [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikonu a vyberte **spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="a6ac8-124">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] using elevated permissions by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
3.  <span data-ttu-id="a6ac8-125">Otevřete soubor řešení Delay.sln.</span><span class="sxs-lookup"><span data-stu-id="a6ac8-125">Open the Delay.sln solution file.</span></span>  
  
4.  <span data-ttu-id="a6ac8-126">Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.</span><span class="sxs-lookup"><span data-stu-id="a6ac8-126">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
5.  <span data-ttu-id="a6ac8-127">Stisknutím kombinace kláves CTRL + F5 a spusťte řešení.</span><span class="sxs-lookup"><span data-stu-id="a6ac8-127">Press CTRL+F5 to run the solution.</span></span>  
  
#### <a name="to-uninstall-this-sample"></a><span data-ttu-id="a6ac8-128">Chcete-li odinstalovat tuto ukázku</span><span class="sxs-lookup"><span data-stu-id="a6ac8-128">To uninstall this sample</span></span>  
  
1.  <span data-ttu-id="a6ac8-129">Otevřete [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a6ac8-129">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
2.  <span data-ttu-id="a6ac8-130">Přejděte do adresáře DurableDelay\CS.</span><span class="sxs-lookup"><span data-stu-id="a6ac8-130">Navigate to the DurableDelay\CS directory.</span></span>  
  
3.  <span data-ttu-id="a6ac8-131">Spusťte Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="a6ac8-131">Run Cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a6ac8-132">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="a6ac8-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a6ac8-133">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="a6ac8-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a6ac8-134">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="a6ac8-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a6ac8-135">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="a6ac8-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelay`