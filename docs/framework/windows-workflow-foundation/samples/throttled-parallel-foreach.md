---
title: Aktivita Throttledparallelforeach
ms.date: 03/30/2017
ms.assetid: f2855b5f-e9a7-433d-96a4-40fc31025215
ms.openlocfilehash: 7149e6db8992bff5b436ffae4a77d985ec255986
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43397910"
---
# <a name="throttled-parallel-foreach"></a><span data-ttu-id="bb326-102">Aktivita Throttledparallelforeach</span><span class="sxs-lookup"><span data-stu-id="bb326-102">Throttled Parallel ForEach</span></span>
<span data-ttu-id="bb326-103">`ThrottleParallelForEach` Aktivity se podobá <!--zz <xref:System.Activities.Statements.ParallelForEach>--> `System.Activities.Statements.ParallelForEach` činnost s jednou výjimkou, že umožňuje nastavení faktor souběžnost chcete omezit počet souběžných větve ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="bb326-103">The `ThrottleParallelForEach` activity is similar to the <!--zz <xref:System.Activities.Statements.ParallelForEach>--> `System.Activities.Statements.ParallelForEach` activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span> <span data-ttu-id="bb326-104">`ThrottleParallelForEach` Aktivity je odvozena z <xref:System.Activities.NativeActivity>, protože je potřeba naplánovat dalších aktivit (podřízené aktivity) a to je k dispozici pouze prostřednictvím <xref:System.Activities.NativeActivityContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="bb326-104">The `ThrottleParallelForEach` activity derives from <xref:System.Activities.NativeActivity>, because it needs to schedule other activities (the child activities) and this is only accessible through the <xref:System.Activities.NativeActivityContext> class.</span></span>  
  
## <a name="projects"></a><span data-ttu-id="bb326-105">Projekty</span><span class="sxs-lookup"><span data-stu-id="bb326-105">Projects</span></span>  
  
|<span data-ttu-id="bb326-106">**ProjectName**</span><span class="sxs-lookup"><span data-stu-id="bb326-106">**ProjectName**</span></span>|<span data-ttu-id="bb326-107">**Popis**</span><span class="sxs-lookup"><span data-stu-id="bb326-107">**Description**</span></span>|<span data-ttu-id="bb326-108">**Hlavní soubory**</span><span class="sxs-lookup"><span data-stu-id="bb326-108">**Main Files**</span></span>|  
|-|-|-|  
|<span data-ttu-id="bb326-109">ThrottledParallelForEach</span><span class="sxs-lookup"><span data-stu-id="bb326-109">ThrottledParallelForEach</span></span>|<span data-ttu-id="bb326-110">Obsahuje `ThrottledParallelForEach` aktivita a její návrháře.</span><span class="sxs-lookup"><span data-stu-id="bb326-110">Contains `ThrottledParallelForEach` activity and its designer.</span></span>|<span data-ttu-id="bb326-111">ThrottledParallelForEach.cs</span><span class="sxs-lookup"><span data-stu-id="bb326-111">ThrottledParallelForEach.cs</span></span><br /><br /> <span data-ttu-id="bb326-112">`ThrottledParallelForEach` Definici aktivity.</span><span class="sxs-lookup"><span data-stu-id="bb326-112">The `ThrottledParallelForEach` activity definition.</span></span>|  
|<span data-ttu-id="bb326-113">CodeTestClient</span><span class="sxs-lookup"><span data-stu-id="bb326-113">CodeTestClient</span></span>|<span data-ttu-id="bb326-114">Ukázková aplikace klienta, který konfiguruje a spustí pracovní postup s `ThrottledParallelForEach` pomocí imperativního kódu.</span><span class="sxs-lookup"><span data-stu-id="bb326-114">Sample client application that configures and runs a workflow with a `ThrottledParallelForEach` using imperative code.</span></span>|<span data-ttu-id="bb326-115">Program.cs</span><span class="sxs-lookup"><span data-stu-id="bb326-115">Program.cs</span></span><br /><br /> <span data-ttu-id="bb326-116">Definuje a spouští instanci ukázkového pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="bb326-116">Defines and runs an instance of the sample workflow.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="bb326-117">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="bb326-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="bb326-118">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor ThrottledParallelForEach.sln.</span><span class="sxs-lookup"><span data-stu-id="bb326-118">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ThrottledParallelForEach.sln file.</span></span>  
  
2.  <span data-ttu-id="bb326-119">Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="bb326-119">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="bb326-120">Abyste mohli spustit řešení, stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="bb326-120">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bb326-121">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="bb326-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bb326-122">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="bb326-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bb326-123">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="bb326-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bb326-124">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="bb326-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\ThrottledParallelForEach`