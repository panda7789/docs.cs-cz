---
title: "Ukládání do mezipaměti s odesílání kanálu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e69a2502-25cb-43bf-b8d2-95fbdecb41cb
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7f8a11397fe161edad6f726c1d6df9ed09dad54a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="channel-caching-with-send"></a><span data-ttu-id="f8f80-102">Ukládání do mezipaměti s odesílání kanálu</span><span class="sxs-lookup"><span data-stu-id="f8f80-102">Channel Caching with Send</span></span>
<span data-ttu-id="f8f80-103"><xref:System.ServiceModel.Activities.SendMessageChannelCache> Umožňuje uživatelům mají různé úrovně kanál ukládání do mezipaměti s <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.SendParametersContent> aktivity.</span><span class="sxs-lookup"><span data-stu-id="f8f80-103">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> enables users to have different levels of channel caching with <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.SendParametersContent> activities.</span></span> <span data-ttu-id="f8f80-104">Ve výchozím nastavení je povoleno ukládání do mezipaměti úrovni instance a tento příklad znázorňuje následující funkce:</span><span class="sxs-lookup"><span data-stu-id="f8f80-104">Instance-level caching is enabled by default and this sample demonstrates the following features:</span></span>  
  
1.  <span data-ttu-id="f8f80-105">Sdílené složky <xref:System.ServiceModel.Activities.SendMessageChannelCache> napříč domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="f8f80-105">Share a <xref:System.ServiceModel.Activities.SendMessageChannelCache> across an application domain.</span></span>  
  
2.  <span data-ttu-id="f8f80-106">Zakažte kanál ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="f8f80-106">Disable channel caching.</span></span>  
  
3.  <span data-ttu-id="f8f80-107">Sdílené složky <xref:System.ServiceModel.Activities.SendMessageChannelCache> mezi instancí pracovních postupů v <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="f8f80-107">Share a <xref:System.ServiceModel.Activities.SendMessageChannelCache> among workflow instances in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="f8f80-108">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="f8f80-108">Demonstrates</span></span>  
 <span data-ttu-id="f8f80-109"><xref:System.ServiceModel.Activities.SendMessageChannelCache>rozšíření, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.ReceiveContent> a <xref:System.ServiceModel.Activities.SendReply> aktivity.</span><span class="sxs-lookup"><span data-stu-id="f8f80-109"><xref:System.ServiceModel.Activities.SendMessageChannelCache> extension, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.ReceiveContent> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f8f80-110">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="f8f80-110">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f8f80-111">Načtení projektu řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] a sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="f8f80-111">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="f8f80-112">Spusťte aplikaci EchoWorkflowService vygenerovaných \EchoWorkflowService\bin\debug.</span><span class="sxs-lookup"><span data-stu-id="f8f80-112">Run the EchoWorkflowService application generated in \EchoWorkflowService\bin\debug.</span></span>  
  
3.  <span data-ttu-id="f8f80-113">Spusťte aplikaci EchoWorkflowClient vygenerovaných .\EchoWorkflowClient\bin\debug.</span><span class="sxs-lookup"><span data-stu-id="f8f80-113">Run the EchoWorkflowClient application generated in .\EchoWorkflowClient\bin\debug.</span></span>  
  
4.  <span data-ttu-id="f8f80-114">Klient volá operaci odezvu na službu a zobrazí výsledky.</span><span class="sxs-lookup"><span data-stu-id="f8f80-114">The client calls the Echo operation on the service and prints the results.</span></span> <span data-ttu-id="f8f80-115">Vytištěné výsledky stisknutím klávesy ENTER ukončete klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="f8f80-115">When the results have been printed, press ENTER to exit the client and the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f8f80-116">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="f8f80-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f8f80-117">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="f8f80-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f8f80-118">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="f8f80-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f8f80-119">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f8f80-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ChannelCache`
