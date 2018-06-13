---
title: Omezenému paralelní ForEach
ms.date: 03/30/2017
ms.assetid: f2855b5f-e9a7-433d-96a4-40fc31025215
ms.openlocfilehash: 195c627d62665f832384989d4ef03105c4af3757
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516259"
---
# <a name="throttled-parallel-foreach"></a><span data-ttu-id="8c5df-102">Omezenému paralelní ForEach</span><span class="sxs-lookup"><span data-stu-id="8c5df-102">Throttled Parallel ForEach</span></span>
<span data-ttu-id="8c5df-103">`ThrottleParallelForEach` Aktivity je podobná <!--zz <xref:System.Activities.Statements.ParallelForEach>--> `System.Activities.Statements.ParallelForEach` aktivity s jednou výjimkou to umožňuje nastavení souběžnosti Multi-Factor omezit počet souběžných větví provést.</span><span class="sxs-lookup"><span data-stu-id="8c5df-103">The `ThrottleParallelForEach` activity is similar to the <!--zz <xref:System.Activities.Statements.ParallelForEach>--> `System.Activities.Statements.ParallelForEach` activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span> <span data-ttu-id="8c5df-104">`ThrottleParallelForEach` Aktivity je odvozena z <xref:System.Activities.NativeActivity>, protože je nutné ho naplánovat další aktivity (podřízené aktivity) a používá se pouze přístupné prostřednictvím <xref:System.Activities.NativeActivityContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="8c5df-104">The `ThrottleParallelForEach` activity derives from <xref:System.Activities.NativeActivity>, because it needs to schedule other activities (the child activities) and this is only accessible through the <xref:System.Activities.NativeActivityContext> class.</span></span>  
  
## <a name="projects"></a><span data-ttu-id="8c5df-105">Projekty</span><span class="sxs-lookup"><span data-stu-id="8c5df-105">Projects</span></span>  
  
|<span data-ttu-id="8c5df-106">**ProjectName**</span><span class="sxs-lookup"><span data-stu-id="8c5df-106">**ProjectName**</span></span>|<span data-ttu-id="8c5df-107">**Popis**</span><span class="sxs-lookup"><span data-stu-id="8c5df-107">**Description**</span></span>|<span data-ttu-id="8c5df-108">**Hlavní soubory**</span><span class="sxs-lookup"><span data-stu-id="8c5df-108">**Main Files**</span></span>|  
|-|-|-|  
|<span data-ttu-id="8c5df-109">ThrottledParallelForEach</span><span class="sxs-lookup"><span data-stu-id="8c5df-109">ThrottledParallelForEach</span></span>|<span data-ttu-id="8c5df-110">Obsahuje `ThrottledParallelForEach` aktivita a její designer.</span><span class="sxs-lookup"><span data-stu-id="8c5df-110">Contains `ThrottledParallelForEach` activity and its designer.</span></span>|<span data-ttu-id="8c5df-111">ThrottledParallelForEach.cs</span><span class="sxs-lookup"><span data-stu-id="8c5df-111">ThrottledParallelForEach.cs</span></span><br /><br /> <span data-ttu-id="8c5df-112">`ThrottledParallelForEach` Definici aktivity.</span><span class="sxs-lookup"><span data-stu-id="8c5df-112">The `ThrottledParallelForEach` activity definition.</span></span>|  
|<span data-ttu-id="8c5df-113">CodeTestClient</span><span class="sxs-lookup"><span data-stu-id="8c5df-113">CodeTestClient</span></span>|<span data-ttu-id="8c5df-114">Ukázková aplikace klienta, která slouží ke konfiguraci a spuštění pracovního postupu s `ThrottledParallelForEach` pomocí imperativní kódu.</span><span class="sxs-lookup"><span data-stu-id="8c5df-114">Sample client application that configures and runs a workflow with a `ThrottledParallelForEach` using imperative code.</span></span>|<span data-ttu-id="8c5df-115">Program.cs</span><span class="sxs-lookup"><span data-stu-id="8c5df-115">Program.cs</span></span><br /><br /> <span data-ttu-id="8c5df-116">Definuje a spouští instanci ukázkový pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="8c5df-116">Defines and runs an instance of the sample workflow.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="8c5df-117">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="8c5df-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="8c5df-118">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor ThrottledParallelForEach.sln.</span><span class="sxs-lookup"><span data-stu-id="8c5df-118">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ThrottledParallelForEach.sln file.</span></span>  
  
2.  <span data-ttu-id="8c5df-119">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="8c5df-119">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="8c5df-120">Pokud chcete spustit řešení, stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="8c5df-120">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8c5df-121">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="8c5df-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8c5df-122">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="8c5df-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8c5df-123">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="8c5df-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8c5df-124">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="8c5df-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\ThrottledParallelForEach`