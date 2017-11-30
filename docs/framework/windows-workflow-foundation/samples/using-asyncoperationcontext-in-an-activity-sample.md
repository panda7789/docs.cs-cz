---
title: "Pomocí AsyncOperationContext v ukázce aktivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0888a0bd-d227-4c00-ad6a-b654a01740e8
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ae62192517ee9117092ff11d2da5212d5a1c1fff
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2017
---
# <a name="using-asyncoperationcontext-in-an-activity-sample"></a><span data-ttu-id="c9cd8-102">Pomocí AsyncOperationContext v ukázce aktivity</span><span class="sxs-lookup"><span data-stu-id="c9cd8-102">Using AsyncOperationContext in an Activity Sample</span></span>
<span data-ttu-id="c9cd8-103">Tento příklad ukazuje, jak vyvíjet vlastní <xref:System.Activities.CodeActivity> používající <xref:System.Activities.AsyncCodeActivityContext> pro práci asynchronně mimo pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="c9cd8-103">This sample demonstrates how to develop a custom <xref:System.Activities.CodeActivity> that uses <xref:System.Activities.AsyncCodeActivityContext> to perform work asynchronously outside of the workflow.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="c9cd8-104">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="c9cd8-104">Sample Details</span></span>  
 <span data-ttu-id="c9cd8-105">Vzorová aktivita používá <xref:System.IO.FileStream.BeginWrite%2A> a <xref:System.IO.FileStream.EndWrite%2A> metody <xref:System.IO.FileStream> třída asynchronně zapsat data do souboru.</span><span class="sxs-lookup"><span data-stu-id="c9cd8-105">The sample activity uses the <xref:System.IO.FileStream.BeginWrite%2A> and <xref:System.IO.FileStream.EndWrite%2A> methods on the <xref:System.IO.FileStream> class to asynchronously write data to a file.</span></span> <span data-ttu-id="c9cd8-106">Vzor sem zavedl lze upravit pro použití s jinými metodami asynchronní.</span><span class="sxs-lookup"><span data-stu-id="c9cd8-106">The pattern introduced here can be adapted for use with other asynchronous methods.</span></span> <span data-ttu-id="c9cd8-107">Při spouštění asynchronní operaci lze provést další aktivity v pracovním postupu, ale pracovní postup nelze nastavit jako trvalý.</span><span class="sxs-lookup"><span data-stu-id="c9cd8-107">While the asynchronous operation is executing, other activities in the workflow can execute, but the workflow cannot be persisted.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c9cd8-108">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="c9cd8-108">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c9cd8-109">Otevřete Async.sln ukázkové řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c9cd8-109">Open the Async.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="c9cd8-110">Sestavení a spuštění řešení.</span><span class="sxs-lookup"><span data-stu-id="c9cd8-110">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c9cd8-111">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="c9cd8-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c9cd8-112">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="c9cd8-112">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c9cd8-113">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="c9cd8-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c9cd8-114">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="c9cd8-114">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\Async`