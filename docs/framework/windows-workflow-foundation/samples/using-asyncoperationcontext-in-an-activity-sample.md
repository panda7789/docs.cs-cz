---
title: Pomocí AsyncOperationContext v ukázce aktivity
ms.date: 03/30/2017
ms.assetid: 0888a0bd-d227-4c00-ad6a-b654a01740e8
ms.openlocfilehash: da7b62ef9e29621d1e6ee1046afb5455af1164bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515494"
---
# <a name="using-asyncoperationcontext-in-an-activity-sample"></a><span data-ttu-id="da410-102">Pomocí AsyncOperationContext v ukázce aktivity</span><span class="sxs-lookup"><span data-stu-id="da410-102">Using AsyncOperationContext in an Activity Sample</span></span>
<span data-ttu-id="da410-103">Tento příklad ukazuje, jak vyvíjet vlastní <xref:System.Activities.CodeActivity> používající <xref:System.Activities.AsyncCodeActivityContext> pro práci asynchronně mimo pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="da410-103">This sample demonstrates how to develop a custom <xref:System.Activities.CodeActivity> that uses <xref:System.Activities.AsyncCodeActivityContext> to perform work asynchronously outside of the workflow.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="da410-104">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="da410-104">Sample Details</span></span>  
 <span data-ttu-id="da410-105">Vzorová aktivita používá <xref:System.IO.FileStream.BeginWrite%2A> a <xref:System.IO.FileStream.EndWrite%2A> metody <xref:System.IO.FileStream> třída asynchronně zapsat data do souboru.</span><span class="sxs-lookup"><span data-stu-id="da410-105">The sample activity uses the <xref:System.IO.FileStream.BeginWrite%2A> and <xref:System.IO.FileStream.EndWrite%2A> methods on the <xref:System.IO.FileStream> class to asynchronously write data to a file.</span></span> <span data-ttu-id="da410-106">Vzor sem zavedl lze upravit pro použití s jinými metodami asynchronní.</span><span class="sxs-lookup"><span data-stu-id="da410-106">The pattern introduced here can be adapted for use with other asynchronous methods.</span></span> <span data-ttu-id="da410-107">Při spouštění asynchronní operaci lze provést další aktivity v pracovním postupu, ale pracovní postup nelze nastavit jako trvalý.</span><span class="sxs-lookup"><span data-stu-id="da410-107">While the asynchronous operation is executing, other activities in the workflow can execute, but the workflow cannot be persisted.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="da410-108">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="da410-108">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="da410-109">Otevřete Async.sln ukázkové řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="da410-109">Open the Async.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="da410-110">Sestavení a spuštění řešení.</span><span class="sxs-lookup"><span data-stu-id="da410-110">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="da410-111">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="da410-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="da410-112">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="da410-112">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="da410-113">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="da410-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="da410-114">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="da410-114">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\Async`