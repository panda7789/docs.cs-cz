---
title: Trvalá prodleva v XAMLX
ms.date: 03/30/2017
ms.assetid: efc38df4-2d34-453c-8e59-2c21d1307354
ms.openlocfilehash: 1eef9211c67d190ecb5f329c481fa2e3d1763353
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43389254"
---
# <a name="durable-delay-in-xamlx"></a><span data-ttu-id="98340-102">Trvalá prodleva v XAMLX</span><span class="sxs-lookup"><span data-stu-id="98340-102">Durable Delay in XAMLX</span></span>
<span data-ttu-id="98340-103">Tato ukázka demonstruje použití trvalá prodleva, což je zpoždění, které se přenese pracovního postupu odolné zařízení během zpoždění.</span><span class="sxs-lookup"><span data-stu-id="98340-103">This sample demonstrates how to use a durable delay, which is a delay that persists the workflow to a durable device during the delay.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="98340-104">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="98340-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="98340-105">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="98340-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="98340-106">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="98340-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="98340-107">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="98340-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlx`  
  
## <a name="discussion"></a><span data-ttu-id="98340-108">Diskuse</span><span class="sxs-lookup"><span data-stu-id="98340-108">Discussion</span></span>  
 <span data-ttu-id="98340-109">Ukázkový pracovní postup obsahuje dvě zprávy do místního souboru, které jsou odděleny ke zpoždění.</span><span class="sxs-lookup"><span data-stu-id="98340-109">The sample workflow contains two messages to a local file that are separated by a delay.</span></span> <span data-ttu-id="98340-110">Když se aktivuje zpoždění, pracovní postup bude uvolněna a čeká 5 sekund do úložiště instancí pracovních postupů, než se znovu načten v paměti.</span><span class="sxs-lookup"><span data-stu-id="98340-110">When the delay is triggered, the workflow is unloaded and waits 5 seconds in the workflow instance store before being reloaded in memory.</span></span>  
  
 <span data-ttu-id="98340-111">Soubor .xamlx je služby pracovního postupu, který je hostován v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="98340-111">The .xamlx file is a workflow service that is hosted in Visual Studio.</span></span> <span data-ttu-id="98340-112">Visual Studio používá Cassini, který používá hostiteli služby pracovního procesu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="98340-112">Visual Studio uses Cassini that uses a workflow service host to host the workflow.</span></span>  
  
 <span data-ttu-id="98340-113">Kromě hostování pracovního postupu, spravuje hostitele služby pracovního postupu instancí pracovních postupů pomocí načítání a uvolňování je.</span><span class="sxs-lookup"><span data-stu-id="98340-113">In addition to hosting the workflow, the workflow service host manages the workflow instances by loading and unloading them.</span></span> <span data-ttu-id="98340-114">Spustit instanci Windows Workflow Foundation (WF) definice (na hostiteli služby pracovního postupu), nastavení klienta, která odesílá zprávy <xref:System.ServiceModel.Activities.Receive> aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="98340-114">To start an instance of the Windows Workflow Foundation (WF) definition (on the workflow service host), set a client that sends a message to the <xref:System.ServiceModel.Activities.Receive> activity in the workflow.</span></span> <span data-ttu-id="98340-115">To <xref:System.ServiceModel.Activities.Receive> má jeho <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> nastavenou na `true`, bude moct vytvořit novou instanci pracovního postupu, jakmile obdrží zprávu.</span><span class="sxs-lookup"><span data-stu-id="98340-115">This <xref:System.ServiceModel.Activities.Receive> has its <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> property set to `true`, enabling it to create a new instance of the workflow once it receives a message.</span></span>  
  
 <span data-ttu-id="98340-116">Během inicializace uvolnění instance chování přidáno do konfiguračního souboru, který určuje k hostiteli služby pracovního postupu, pod kterým ji by měl uvolnit instance do trvalého úložiště (databáze).</span><span class="sxs-lookup"><span data-stu-id="98340-116">During initialization, an unload instance behavior is added to the configuration file that specifies to the workflow service host under which it should unload an instance to the persistence store (database).</span></span> <span data-ttu-id="98340-117">V tomto příkladu je uvolněn instance okamžitě po ukončení pracovního postupu nečinnosti (v případě, že se aktivuje zpoždění).</span><span class="sxs-lookup"><span data-stu-id="98340-117">For this sample, it unloads the instance immediately after the workflow goes idle (when the delay is triggered).</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="98340-118">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="98340-118">To use this sample</span></span>  
  
1.  <span data-ttu-id="98340-119">Otevřít [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="98340-119">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
2.  <span data-ttu-id="98340-120">Přejděte do složky DurableDelayXamlx\CS.</span><span class="sxs-lookup"><span data-stu-id="98340-120">Navigate to the DurableDelayXamlx\CS folder.</span></span>  
  
3.  <span data-ttu-id="98340-121">Spusťte Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="98340-121">Run Setup.cmd.</span></span>  
  
4.  <span data-ttu-id="98340-122">Spustit [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] jako správce.</span><span class="sxs-lookup"><span data-stu-id="98340-122">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] as an administrator.</span></span>  
  
5.  <span data-ttu-id="98340-123">Otevřete soubor řešení DurableDelayXamlx.sln.</span><span class="sxs-lookup"><span data-stu-id="98340-123">Open the DurableDelayXamlx.sln solution file.</span></span>  
  
6.  <span data-ttu-id="98340-124">V **Průzkumníka řešení**, klikněte pravým tlačítkem na řešení a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="98340-124">In **Solution Explorer**, right-click the solution and select **Properties**.</span></span>  
  
7.  <span data-ttu-id="98340-125">Vyberte **více projektů po spuštění** a nastavte oba projekty **Start**.</span><span class="sxs-lookup"><span data-stu-id="98340-125">Select **Multiple startup projects** and set both projects to **Start**.</span></span>  
  
8.  <span data-ttu-id="98340-126">Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="98340-126">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
9. <span data-ttu-id="98340-127">Abyste mohli spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="98340-127">To run the solution, press CTRL+F5.</span></span>  
  
#### <a name="to-uninstall-this-sample"></a><span data-ttu-id="98340-128">Chcete-li odinstalovat tuto ukázku</span><span class="sxs-lookup"><span data-stu-id="98340-128">To uninstall this sample</span></span>  
  
1.  <span data-ttu-id="98340-129">Otevřít [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="98340-129">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
2.  <span data-ttu-id="98340-130">Přejděte do složky DurableDelayXamlx\CS.</span><span class="sxs-lookup"><span data-stu-id="98340-130">Navigate to the DurableDelayXamlx\CS folder.</span></span>  
  
3.  <span data-ttu-id="98340-131">Spusťte Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="98340-131">Run Cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="98340-132">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="98340-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="98340-133">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="98340-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="98340-134">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="98340-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="98340-135">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="98340-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlX`
