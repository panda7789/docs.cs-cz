---
title: "Ukázka koncový bod správy pracovního postupu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ac6e08f-c43d-4bb7-83c3-e3890a4dac03
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 193620902d5bcc2b71f91a26518ab4b6560e6753
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-management-endpoint-sample"></a><span data-ttu-id="1cfeb-102">Ukázka koncový bod správy pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1cfeb-102">Workflow Management Endpoint Sample</span></span>
<span data-ttu-id="1cfeb-103">Tento příklad ukazuje, jak koncový bod pracovního postupu ovládací prvek slouží k vytváření a spouštění pracovních postupů místně i vzdáleně.</span><span class="sxs-lookup"><span data-stu-id="1cfeb-103">This sample shows how a workflow control endpoint can be used to create and run workflows both locally and remotely.</span></span> <span data-ttu-id="1cfeb-104">Ukázka ukazuje, jak hostovat kontrolní koncový bod a zápis klientů volání kontrolní koncový bod vytvořit a spustit instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1cfeb-104">The sample demonstrates how to host a control endpoint and write clients that call the control endpoint to create and run the instance of a workflow.</span></span> <span data-ttu-id="1cfeb-105">Pracovní postup není služba.</span><span class="sxs-lookup"><span data-stu-id="1cfeb-105">The workflow is not a service.</span></span>  
  
 <span data-ttu-id="1cfeb-106">Na straně služby ukázku pracovního postupu je hostovaná s hostitele služby pracovního postupu a WorkflowControlEndpoint se přidá, aby klienti mohli provést operace ovládacího prvku (pozastavit, počáteční atd.).</span><span class="sxs-lookup"><span data-stu-id="1cfeb-106">On the service side of the sample a workflow is hosted with WorkflowServiceHost and a WorkflowControlEndpoint is added so that clients can perform control operations (Suspend, Start, etc).</span></span> <span data-ttu-id="1cfeb-107">Uživatelem definované CreationEndpoint je taky přidaný ke povolit pracovní postup, který se má vytvořit.</span><span class="sxs-lookup"><span data-stu-id="1cfeb-107">A user-defined CreationEndpoint is also added to allow the workflow to be created.</span></span> <span data-ttu-id="1cfeb-108">Služba pak použije tyto koncové body spustit pracovní postup v pozastaveném stavu a poté obnovit pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1cfeb-108">The service then uses these endpoints to start the workflow in a suspended state and then resume the workflow.</span></span> <span data-ttu-id="1cfeb-109">Klient provádí stejné operace, ale z kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="1cfeb-109">The client performs the same operations but from the client code.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="1cfeb-110">Tato rozhraní najdete [kontrolní koncový bod pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md) a [postupy: hostování bez služby pracovního postupu ve službě IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)</span><span class="sxs-lookup"><span data-stu-id="1cfeb-110"> these interfaces see, [Workflow Control Endpoint](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md) and [How to: Host a non-service workflow in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="1cfeb-111">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="1cfeb-111">To run the sample</span></span>  
  
1.  <span data-ttu-id="1cfeb-112">Spustit [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="1cfeb-112">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="1cfeb-113">Otevřete řešení ManagementEndpoint.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1cfeb-113">Open the ManagementEndpoint.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
3.  <span data-ttu-id="1cfeb-114">Sestavte řešení, stiskněte CTRL + SHIFT + B nebo vyberte **sestavit řešení** z **sestavení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="1cfeb-114">To build the solution, press CTRL+SHIFT+B or select **Build Solution** from the **Build** menu.</span></span>  
  
4.  <span data-ttu-id="1cfeb-115">Spusťte aplikaci ManagementEndpoint.exe.</span><span class="sxs-lookup"><span data-stu-id="1cfeb-115">Start the ManagementEndpoint.exe application.</span></span>  
  
5.  <span data-ttu-id="1cfeb-116">Spusťte aplikaci Client.exe.</span><span class="sxs-lookup"><span data-stu-id="1cfeb-116">Start the Client.exe application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1cfeb-117">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="1cfeb-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="1cfeb-118">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="1cfeb-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1cfeb-119">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="1cfeb-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1cfeb-120">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="1cfeb-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ManagementEndpoint`