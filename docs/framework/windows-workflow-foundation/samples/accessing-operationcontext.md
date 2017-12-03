---
title: "Přístup k informacím OperationContext"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3c0966299f27312deb188aec00abe9949dc27c2d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="accessing-operationcontext"></a><span data-ttu-id="15294-102">Přístup k informacím OperationContext</span><span class="sxs-lookup"><span data-stu-id="15294-102">Accessing OperationContext</span></span>
<span data-ttu-id="15294-103">Tento příklad ukazuje, jak aktivity zasílání zpráv (<xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.Send>) lze použít s aktivitou vlastní rozsah pro přístup k <xref:System.ServiceModel.OperationContext.Current%2A> a připojit nebo načíst záhlaví vlastní zprávy v rámci odchozí nebo příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="15294-103">This sample demonstrates how the messaging activities (<xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.Send>) can be used with a custom scope activity to access <xref:System.ServiceModel.OperationContext.Current%2A> and attach or retrieve a custom message header within an outgoing or incoming message.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="15294-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="15294-104">Demonstrates</span></span>  
 <span data-ttu-id="15294-105">Aktivity, zasílání zpráv <xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.</span><span class="sxs-lookup"><span data-stu-id="15294-105">Messaging Activities, <xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="15294-106">Diskusní</span><span class="sxs-lookup"><span data-stu-id="15294-106">Discussion</span></span>  
 <span data-ttu-id="15294-107">Tento příklad ukazuje způsob použití body rozšiřitelnosti (<xref:System.ServiceModel.Activities.ISendMessageCallback>) <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) v zasílání zpráv aktivity pro přístup k <xref:System.ServiceModel.OperationContext.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="15294-107">This sample shows how to use extensibility points (<xref:System.ServiceModel.Activities.ISendMessageCallback>) <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) in the messaging activities to access <xref:System.ServiceModel.OperationContext.Current%2A>.</span></span> <span data-ttu-id="15294-108">V modulu runtime pracovního postupu jako implementaci jsou zaregistrována zpětná volání <xref:System.Activities.IExecutionProperty> , je převzata aktivitami zasílání zpráv při spuštění.</span><span class="sxs-lookup"><span data-stu-id="15294-108">The callbacks are registered within the workflow runtime as an implementation of <xref:System.Activities.IExecutionProperty> that is picked up by the messaging activities upon execution.</span></span> <span data-ttu-id="15294-109">Všechny aktivity zasílání zpráv ve stejném oboru, který <xref:System.Activities.IExecutionProperty> implementace má vliv.</span><span class="sxs-lookup"><span data-stu-id="15294-109">Any messaging activity in the same scope as that <xref:System.Activities.IExecutionProperty> implementation is affected.</span></span> <span data-ttu-id="15294-110">Konkrétně Tato ukázka používá aktivitu vlastní rozsah vynutit chování zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="15294-110">In particular, this sample uses a custom scope activity to enforce the callback behavior.</span></span> <span data-ttu-id="15294-111"><xref:System.ServiceModel.Activities.ISendMessageCallback> Se používá v pracovním postupu klienta zahrnout pracovního postupu <xref:System.Activities.WorkflowApplication.Id%2A> jako odchozí <xref:System.ServiceModel.Channels.MessageHeader>.</span><span class="sxs-lookup"><span data-stu-id="15294-111">The <xref:System.ServiceModel.Activities.ISendMessageCallback> is used in the client workflow to include the workflow’s <xref:System.Activities.WorkflowApplication.Id%2A> as an outgoing <xref:System.ServiceModel.Channels.MessageHeader>.</span></span> <span data-ttu-id="15294-112">Tuto hlavičku je pak zachyceny v služby pomocí <xref:System.ServiceModel.Activities.IReceiveMessageCallback> a hodnota hlavičky se vytiskne ke konzole.</span><span class="sxs-lookup"><span data-stu-id="15294-112">This header is then picked up in the service using the <xref:System.ServiceModel.Activities.IReceiveMessageCallback> and the value of the header is printed out to the console.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="15294-113">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="15294-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="15294-114">Tato ukázka zpřístupní služby pracovního postupu pomocí koncových bodů protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="15294-114">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="15294-115">Použít tuto ukázku, správné seznamy ACL adresa URL musí být přidán (viz [konfigurace HTTP a HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) podrobnosti), spuštění sady Visual Studio jako správce, nebo spuštěním následujícího příkazu řádku se zvýšenými oprávněními přidejte příslušné seznamy ACL.</span><span class="sxs-lookup"><span data-stu-id="15294-115">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="15294-116">Zajistěte, aby uživatelské jméno a doména jsou nahrazována.</span><span class="sxs-lookup"><span data-stu-id="15294-116">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2.  <span data-ttu-id="15294-117">Jakmile se přidají adresy URL seznamy ACL, použijte následující postup.</span><span class="sxs-lookup"><span data-stu-id="15294-117">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1.  <span data-ttu-id="15294-118">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="15294-118">Build the solution.</span></span>  
  
    2.  <span data-ttu-id="15294-119">Pravým tlačítkem myši řešení a výběrem nastavit více projektů spuštění **nastavit projekty po spuštění**.</span><span class="sxs-lookup"><span data-stu-id="15294-119">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span>  
  
    3.  <span data-ttu-id="15294-120">Přidat **služby** a **klienta** (v tomto pořadí) jako více projektů spuštění.</span><span class="sxs-lookup"><span data-stu-id="15294-120">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    4.  <span data-ttu-id="15294-121">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="15294-121">Run the application.</span></span> <span data-ttu-id="15294-122">Konzole klienta ukazuje pracovní postup spuštěn dvakrát a zobrazí se okno Service ID instance pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="15294-122">The client console shows a workflow running twice and the Service window shows the instance ID of those workflows.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="15294-123">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="15294-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="15294-124">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="15294-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="15294-125">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="15294-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="15294-126">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="15294-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
