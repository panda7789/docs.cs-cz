---
title: "Omezenému paralelní ForEach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2855b5f-e9a7-433d-96a4-40fc31025215
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6c8336060be48f55b974960e67ca1ebc57e76c63
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="throttled-parallel-foreach"></a><span data-ttu-id="213e8-102">Omezenému paralelní ForEach</span><span class="sxs-lookup"><span data-stu-id="213e8-102">Throttled Parallel ForEach</span></span>
<span data-ttu-id="213e8-103">`ThrottleParallelForEach` Aktivity je podobná <!--zz <xref:System.Activities.Statements.ParallelForEach>--> `System.Activities.Statements.ParallelForEach` aktivity s jednou výjimkou to umožňuje nastavení souběžnosti Multi-Factor omezit počet souběžných větví provést.</span><span class="sxs-lookup"><span data-stu-id="213e8-103">The `ThrottleParallelForEach` activity is similar to the <!--zz <xref:System.Activities.Statements.ParallelForEach>--> `System.Activities.Statements.ParallelForEach` activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span> <span data-ttu-id="213e8-104">`ThrottleParallelForEach` Aktivity je odvozena z <xref:System.Activities.NativeActivity>, protože je nutné ho naplánovat další aktivity (podřízené aktivity) a používá se pouze přístupné prostřednictvím <xref:System.Activities.NativeActivityContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="213e8-104">The `ThrottleParallelForEach` activity derives from <xref:System.Activities.NativeActivity>, because it needs to schedule other activities (the child activities) and this is only accessible through the <xref:System.Activities.NativeActivityContext> class.</span></span>  
  
## <a name="projects"></a><span data-ttu-id="213e8-105">Projekty</span><span class="sxs-lookup"><span data-stu-id="213e8-105">Projects</span></span>  
  
|<span data-ttu-id="213e8-106">**Název projektu**</span><span class="sxs-lookup"><span data-stu-id="213e8-106">**ProjectName**</span></span>|<span data-ttu-id="213e8-107">**Popis**</span><span class="sxs-lookup"><span data-stu-id="213e8-107">**Description**</span></span>|<span data-ttu-id="213e8-108">**Hlavní soubory**</span><span class="sxs-lookup"><span data-stu-id="213e8-108">**Main Files**</span></span>|  
|-|-|-|  
|<span data-ttu-id="213e8-109">ThrottledParallelForEach</span><span class="sxs-lookup"><span data-stu-id="213e8-109">ThrottledParallelForEach</span></span>|<span data-ttu-id="213e8-110">Obsahuje `ThrottledParallelForEach` aktivita a její designer.</span><span class="sxs-lookup"><span data-stu-id="213e8-110">Contains `ThrottledParallelForEach` activity and its designer.</span></span>|<span data-ttu-id="213e8-111">ThrottledParallelForEach.cs</span><span class="sxs-lookup"><span data-stu-id="213e8-111">ThrottledParallelForEach.cs</span></span><br /><br /> <span data-ttu-id="213e8-112">`ThrottledParallelForEach` Definici aktivity.</span><span class="sxs-lookup"><span data-stu-id="213e8-112">The `ThrottledParallelForEach` activity definition.</span></span>|  
|<span data-ttu-id="213e8-113">CodeTestClient</span><span class="sxs-lookup"><span data-stu-id="213e8-113">CodeTestClient</span></span>|<span data-ttu-id="213e8-114">Ukázková aplikace klienta, která slouží ke konfiguraci a spuštění pracovního postupu s `ThrottledParallelForEach` pomocí imperativní kódu.</span><span class="sxs-lookup"><span data-stu-id="213e8-114">Sample client application that configures and runs a workflow with a `ThrottledParallelForEach` using imperative code.</span></span>|<span data-ttu-id="213e8-115">Program.cs</span><span class="sxs-lookup"><span data-stu-id="213e8-115">Program.cs</span></span><br /><br /> <span data-ttu-id="213e8-116">Definuje a spouští instanci ukázkový pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="213e8-116">Defines and runs an instance of the sample workflow.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="213e8-117">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="213e8-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="213e8-118">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor ThrottledParallelForEach.sln.</span><span class="sxs-lookup"><span data-stu-id="213e8-118">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ThrottledParallelForEach.sln file.</span></span>  
  
2.  <span data-ttu-id="213e8-119">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="213e8-119">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="213e8-120">Pokud chcete spustit řešení, stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="213e8-120">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="213e8-121">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="213e8-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="213e8-122">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="213e8-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="213e8-123">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="213e8-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="213e8-124">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="213e8-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\ThrottledParallelForEach`  
  
## <a name="see-also"></a><span data-ttu-id="213e8-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="213e8-125">See Also</span></span>
