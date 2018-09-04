---
title: Kanál do mezipaměti pomocí Send
ms.date: 03/30/2017
ms.assetid: e69a2502-25cb-43bf-b8d2-95fbdecb41cb
ms.openlocfilehash: 619088def1f5e443a31244516655d75d1e25c9cb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43503812"
---
# <a name="channel-caching-with-send"></a><span data-ttu-id="baf0d-102">Kanál do mezipaměti pomocí Send</span><span class="sxs-lookup"><span data-stu-id="baf0d-102">Channel Caching with Send</span></span>
<span data-ttu-id="baf0d-103"><xref:System.ServiceModel.Activities.SendMessageChannelCache> Umožňuje uživatelům mají různé úrovně kanál ukládání do mezipaměti s <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.SendParametersContent> aktivity.</span><span class="sxs-lookup"><span data-stu-id="baf0d-103">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> enables users to have different levels of channel caching with <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.SendParametersContent> activities.</span></span> <span data-ttu-id="baf0d-104">Ve výchozím nastavení je povoleno ukládání do mezipaměti na úrovni instance a tato ukázka demonstruje následující funkce:</span><span class="sxs-lookup"><span data-stu-id="baf0d-104">Instance-level caching is enabled by default and this sample demonstrates the following features:</span></span>  
  
1.  <span data-ttu-id="baf0d-105">Sdílené složky <xref:System.ServiceModel.Activities.SendMessageChannelCache> napříč doménou aplikace.</span><span class="sxs-lookup"><span data-stu-id="baf0d-105">Share a <xref:System.ServiceModel.Activities.SendMessageChannelCache> across an application domain.</span></span>  
  
2.  <span data-ttu-id="baf0d-106">Zakáže ukládání do mezipaměti kanálu.</span><span class="sxs-lookup"><span data-stu-id="baf0d-106">Disable channel caching.</span></span>  
  
3.  <span data-ttu-id="baf0d-107">Sdílené složky <xref:System.ServiceModel.Activities.SendMessageChannelCache> mezi instance pracovního postupu <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="baf0d-107">Share a <xref:System.ServiceModel.Activities.SendMessageChannelCache> among workflow instances in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="baf0d-108">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="baf0d-108">Demonstrates</span></span>  
 <span data-ttu-id="baf0d-109"><xref:System.ServiceModel.Activities.SendMessageChannelCache> rozšíření, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.ReceiveContent> a <xref:System.ServiceModel.Activities.SendReply> aktivity.</span><span class="sxs-lookup"><span data-stu-id="baf0d-109"><xref:System.ServiceModel.Activities.SendMessageChannelCache> extension, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.ReceiveContent> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="baf0d-110">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="baf0d-110">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="baf0d-111">Načítání řešení projektu v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] a sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="baf0d-111">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="baf0d-112">Spusťte aplikaci EchoWorkflowService vygenerované v \EchoWorkflowService\bin\debug.</span><span class="sxs-lookup"><span data-stu-id="baf0d-112">Run the EchoWorkflowService application generated in \EchoWorkflowService\bin\debug.</span></span>  
  
3.  <span data-ttu-id="baf0d-113">Spusťte aplikaci EchoWorkflowClient vygenerované v .\EchoWorkflowClient\bin\debug.</span><span class="sxs-lookup"><span data-stu-id="baf0d-113">Run the EchoWorkflowClient application generated in .\EchoWorkflowClient\bin\debug.</span></span>  
  
4.  <span data-ttu-id="baf0d-114">Klient volá operace odezvu na službu a vypíše výsledky.</span><span class="sxs-lookup"><span data-stu-id="baf0d-114">The client calls the Echo operation on the service and prints the results.</span></span> <span data-ttu-id="baf0d-115">Výsledky dokončení tisku, stisknutím klávesy ENTER ukončete klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="baf0d-115">When the results have been printed, press ENTER to exit the client and the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="baf0d-116">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="baf0d-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="baf0d-117">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="baf0d-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="baf0d-118">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="baf0d-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="baf0d-119">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="baf0d-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ChannelCache`
