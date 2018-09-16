---
title: Použití AsyncOperationContext v ukázce aktivity
ms.date: 03/30/2017
ms.assetid: 0888a0bd-d227-4c00-ad6a-b654a01740e8
ms.openlocfilehash: 4358a364a3f7ec69b7c1c548fcf82fe494f37505
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45666548"
---
# <a name="using-asyncoperationcontext-in-an-activity-sample"></a><span data-ttu-id="50104-102">Použití AsyncOperationContext v ukázce aktivity</span><span class="sxs-lookup"><span data-stu-id="50104-102">Using AsyncOperationContext in an Activity Sample</span></span>
<span data-ttu-id="50104-103">Tato ukázka předvádí, jak vyvíjet vlastní <xref:System.Activities.CodeActivity> , která používá <xref:System.Activities.AsyncCodeActivityContext> a provádí práci asynchronně mimo pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="50104-103">This sample demonstrates how to develop a custom <xref:System.Activities.CodeActivity> that uses <xref:System.Activities.AsyncCodeActivityContext> to perform work asynchronously outside of the workflow.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="50104-104">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="50104-104">Sample Details</span></span>  
 <span data-ttu-id="50104-105">Vzorová aktivita používá <xref:System.IO.FileStream.BeginWrite%2A> a <xref:System.IO.FileStream.EndWrite%2A> metody <xref:System.IO.FileStream> třídy asynchronního zápisu dat do souboru.</span><span class="sxs-lookup"><span data-stu-id="50104-105">The sample activity uses the <xref:System.IO.FileStream.BeginWrite%2A> and <xref:System.IO.FileStream.EndWrite%2A> methods on the <xref:System.IO.FileStream> class to asynchronously write data to a file.</span></span> <span data-ttu-id="50104-106">Vzor zavedené zde lze upravit pomocí jiné asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="50104-106">The pattern introduced here can be adapted for use with other asynchronous methods.</span></span> <span data-ttu-id="50104-107">Při provádění asynchronní operace, můžete provést další aktivity v pracovním postupu, ale pracovní postup nelze nastavit jako trvalý.</span><span class="sxs-lookup"><span data-stu-id="50104-107">While the asynchronous operation is executing, other activities in the workflow can execute, but the workflow cannot be persisted.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="50104-108">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="50104-108">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="50104-109">Otevřete v ukázkovém řešení Async.sln [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="50104-109">Open the Async.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="50104-110">Sestavte a spusťte řešení.</span><span class="sxs-lookup"><span data-stu-id="50104-110">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="50104-111">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="50104-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="50104-112">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="50104-112">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="50104-113">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="50104-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="50104-114">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="50104-114">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\Async`