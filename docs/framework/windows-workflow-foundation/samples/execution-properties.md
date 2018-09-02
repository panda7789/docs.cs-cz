---
title: Vlastnosti spuštění
ms.date: 03/30/2017
ms.assetid: 31c009db-397c-4653-87e2-32dc77fa4b13
ms.openlocfilehash: 4906c2ad11c8b5822764435d2b39a5b51f2673ba
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43409086"
---
# <a name="execution-properties"></a><span data-ttu-id="6bf8f-102">Vlastnosti spuštění</span><span class="sxs-lookup"><span data-stu-id="6bf8f-102">Execution Properties</span></span>
<span data-ttu-id="6bf8f-103">Tato ukázka předvádí, jak definovat a používat vlastnost spuštění ve vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="6bf8f-103">This sample shows how to define and use an execution property in a custom activity.</span></span> <span data-ttu-id="6bf8f-104">V tomto příkladu provádění vlastnost určuje barvu popředí v konzole.</span><span class="sxs-lookup"><span data-stu-id="6bf8f-104">In this example, the execution property determines the console's foreground color.</span></span> <span data-ttu-id="6bf8f-105">Příklad pracovního postupu ukazuje, jak různé logické cesty spuštění (větve z <xref:System.Activities.Statements.Parallel> aktivity) můžete udržovat různé konzoly barvy bez ohledu na prokládaného spouštění funkcí s aktivit (mezi větvemi z <xref:System.Activities.Statements.Parallel> aktivit).</span><span class="sxs-lookup"><span data-stu-id="6bf8f-105">An example workflow shows how different logical paths of execution (branches of a <xref:System.Activities.Statements.Parallel> activity) can maintain different console colors despite interleaved execution of activities (across the branches of the <xref:System.Activities.Statements.Parallel> activity).</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6bf8f-106">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="6bf8f-106">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="6bf8f-107">Otevřete v ukázkovém řešení ExecutionProperties.sln [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6bf8f-107">Open the ExecutionProperties.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6bf8f-108">Zobrazení ThreeColors.xaml před sestavením řešení zobrazí chybu, protože používá vlastní aktivity musí být sestaveny ve stejnou dobu jako řešení.</span><span class="sxs-lookup"><span data-stu-id="6bf8f-108">Viewing ThreeColors.xaml before building the solution displays an error, because the custom activities used must be built at the same time as the solution.</span></span>  
  
2.  <span data-ttu-id="6bf8f-109">Sestavte a spusťte řešení.</span><span class="sxs-lookup"><span data-stu-id="6bf8f-109">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6bf8f-110">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="6bf8f-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6bf8f-111">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="6bf8f-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6bf8f-112">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="6bf8f-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6bf8f-113">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="6bf8f-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ExecutionProperties`