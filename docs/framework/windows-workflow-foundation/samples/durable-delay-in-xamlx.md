---
title: Trvanlivý zpoždění při XAMLX
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efc38df4-2d34-453c-8e59-2c21d1307354
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8fa5a9e4287bcbcb490754b84a8b5060d321f779
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="durable-delay-in-xamlx"></a><span data-ttu-id="4fd1e-102">Trvanlivý zpoždění při XAMLX</span><span class="sxs-lookup"><span data-stu-id="4fd1e-102">Durable Delay in XAMLX</span></span>
<span data-ttu-id="4fd1e-103">Tento příklad znázorňuje způsob použití trvanlivý zpoždění, což je zpoždění, která je uchována pracovního postupu trvanlivý zařízení během zpoždění.</span><span class="sxs-lookup"><span data-stu-id="4fd1e-103">This sample demonstrates how to use a durable delay, which is a delay that persists the workflow to a durable device during the delay.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4fd1e-104">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="4fd1e-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4fd1e-105">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="4fd1e-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4fd1e-106">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="4fd1e-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4fd1e-107">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="4fd1e-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlx`  
  
## <a name="discussion"></a><span data-ttu-id="4fd1e-108">Diskusní</span><span class="sxs-lookup"><span data-stu-id="4fd1e-108">Discussion</span></span>  
 <span data-ttu-id="4fd1e-109">Ukázkový pracovní postup obsahuje dvě zprávy do místního souboru, které jsou odděleny zpoždění.</span><span class="sxs-lookup"><span data-stu-id="4fd1e-109">The sample workflow contains two messages to a local file that are separated by a delay.</span></span> <span data-ttu-id="4fd1e-110">Když se aktivuje zpoždění pracovní postup je odpojen a čeká 5 sekund v úložišti instance pracovního postupu, než se znovu načíst v paměti.</span><span class="sxs-lookup"><span data-stu-id="4fd1e-110">When the delay is triggered, the workflow is unloaded and waits 5 seconds in the workflow instance store before being reloaded in memory.</span></span>  
  
 <span data-ttu-id="4fd1e-111">Soubor .xamlx je služby pracovního postupu, který je hostován v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4fd1e-111">The .xamlx file is a workflow service that is hosted in Visual Studio.</span></span> <span data-ttu-id="4fd1e-112">Visual Studio použije Cassini, který používá hostiteli služby pracovního procesu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="4fd1e-112">Visual Studio uses Cassini that uses a workflow service host to host the workflow.</span></span>  
  
 <span data-ttu-id="4fd1e-113">Kromě hostování pracovního postupu, spravuje hostitele služby pracovního postupu instancí pracovních postupů tím, načítání a uvolňování je.</span><span class="sxs-lookup"><span data-stu-id="4fd1e-113">In addition to hosting the workflow, the workflow service host manages the workflow instances by loading and unloading them.</span></span> <span data-ttu-id="4fd1e-114">Pokud chcete spustit instanci definici Windows Workflow Foundation (WF) (na hostiteli služby pracovního postupu), nastavení klienta, který odešle zprávu, která <xref:System.ServiceModel.Activities.Receive> aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="4fd1e-114">To start an instance of the Windows Workflow Foundation (WF) definition (on the workflow service host), set a client that sends a message to the <xref:System.ServiceModel.Activities.Receive> activity in the workflow.</span></span> <span data-ttu-id="4fd1e-115">To <xref:System.ServiceModel.Activities.Receive> má jeho <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> vlastnost nastavena na hodnotu `true`, kterých je možné vytvořit novou instanci pracovního postupu, jakmile obdrží zprávu.</span><span class="sxs-lookup"><span data-stu-id="4fd1e-115">This <xref:System.ServiceModel.Activities.Receive> has its <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> property set to `true`, enabling it to create a new instance of the workflow once it receives a message.</span></span>  
  
 <span data-ttu-id="4fd1e-116">Během inicializace uvolnění instance chování je do konfiguračního souboru, který určuje, že hostitel služby pracovního postupu, pod kterým je by uvolnit instance do úložiště trvalosti (databáze).</span><span class="sxs-lookup"><span data-stu-id="4fd1e-116">During initialization, an unload instance behavior is added to the configuration file that specifies to the workflow service host under which it should unload an instance to the persistence store (database).</span></span> <span data-ttu-id="4fd1e-117">Tato ukázka se uvolní instanci, ihned po pracovní postup přejde nečinnosti (když se spustí zpoždění).</span><span class="sxs-lookup"><span data-stu-id="4fd1e-117">For this sample, it unloads the instance immediately after the workflow goes idle (when the delay is triggered).</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="4fd1e-118">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="4fd1e-118">To use this sample</span></span>  
  
1.  <span data-ttu-id="4fd1e-119">Otevřete [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="4fd1e-119">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
2.  <span data-ttu-id="4fd1e-120">Přejděte do složky DurableDelayXamlx\CS.</span><span class="sxs-lookup"><span data-stu-id="4fd1e-120">Navigate to the DurableDelayXamlx\CS folder.</span></span>  
  
3.  <span data-ttu-id="4fd1e-121">Spusťte Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="4fd1e-121">Run Setup.cmd.</span></span>  
  
4.  <span data-ttu-id="4fd1e-122">Spustit [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] jako správce.</span><span class="sxs-lookup"><span data-stu-id="4fd1e-122">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] as an administrator.</span></span>  
  
5.  <span data-ttu-id="4fd1e-123">Otevřete soubor řešení DurableDelayXamlx.sln.</span><span class="sxs-lookup"><span data-stu-id="4fd1e-123">Open the DurableDelayXamlx.sln solution file.</span></span>  
  
6.  <span data-ttu-id="4fd1e-124">V **Průzkumníku řešení**, klikněte pravým tlačítkem na řešení a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="4fd1e-124">In **Solution Explorer**, right-click the solution and select **Properties**.</span></span>  
  
7.  <span data-ttu-id="4fd1e-125">Vyberte **více projektů po spuštění** a nastavte oba projekty **spustit**.</span><span class="sxs-lookup"><span data-stu-id="4fd1e-125">Select **Multiple startup projects** and set both projects to **Start**.</span></span>  
  
8.  <span data-ttu-id="4fd1e-126">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="4fd1e-126">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
9. <span data-ttu-id="4fd1e-127">Chcete-li spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="4fd1e-127">To run the solution, press CTRL+F5.</span></span>  
  
#### <a name="to-uninstall-this-sample"></a><span data-ttu-id="4fd1e-128">Chcete-li odinstalovat tuto ukázku</span><span class="sxs-lookup"><span data-stu-id="4fd1e-128">To uninstall this sample</span></span>  
  
1.  <span data-ttu-id="4fd1e-129">Otevřete [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="4fd1e-129">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
2.  <span data-ttu-id="4fd1e-130">Přejděte do složky DurableDelayXamlx\CS.</span><span class="sxs-lookup"><span data-stu-id="4fd1e-130">Navigate to the DurableDelayXamlx\CS folder.</span></span>  
  
3.  <span data-ttu-id="4fd1e-131">Spusťte Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="4fd1e-131">Run Cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4fd1e-132">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="4fd1e-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4fd1e-133">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="4fd1e-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4fd1e-134">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="4fd1e-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4fd1e-135">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="4fd1e-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlX`
