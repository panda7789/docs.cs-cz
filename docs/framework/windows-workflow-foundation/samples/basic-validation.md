---
title: Základní ověřování
ms.date: 03/30/2017
ms.assetid: ba1343cc-aaab-4ade-b0c0-1dd5063bf4ad
ms.openlocfilehash: 74d99e2d426e9ea5701fad80418fdf019112cc9e
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581282"
---
# <a name="basic-validation"></a><span data-ttu-id="152ce-102">Základní ověřování</span><span class="sxs-lookup"><span data-stu-id="152ce-102">Basic Validation</span></span>
<span data-ttu-id="152ce-103">Tento příklad se skládá z aktivit, `CreateProduct`, který ověří, jestli jeho `Cost` argumentu je menší než nebo roven jeho `Price` argument.</span><span class="sxs-lookup"><span data-stu-id="152ce-103">This sample consists of an activity, `CreateProduct`, which validates that its `Cost` argument is smaller than or equal to its `Price` argument.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="152ce-104">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="152ce-104">Sample Details</span></span>  
 <span data-ttu-id="152ce-105">Existují dva autorů, které používají ověřování, autorem aktivity (vytvoří logiku ověřování aktivity) a Autor pracovního postupu, který volá ověření služby na konkrétní pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="152ce-105">There are two authors that use validation, the activity author (creates the validation logic for the activity) and the workflow author that calls validation services on a specific workflow.</span></span> <span data-ttu-id="152ce-106">V tomto scénáři autorem aktivity chce zajistit, že každá instance jeho aktivity musí mít menší nebo rovna náklady než u cena.</span><span class="sxs-lookup"><span data-stu-id="152ce-106">In this scenario, the activity author wants to enforce that every instance of his activity must have a smaller or equal cost than that of the price.</span></span>  
  
 <span data-ttu-id="152ce-107">Musí být autorem aktivity (v aktivitě):</span><span class="sxs-lookup"><span data-stu-id="152ce-107">The activity author (inside the activity) must:</span></span>  
  
-   <span data-ttu-id="152ce-108">Vytvoření omezení (`PriceGreaterThanCost`).</span><span class="sxs-lookup"><span data-stu-id="152ce-108">Create a constraint (`PriceGreaterThanCost`).</span></span> <span data-ttu-id="152ce-109">To je, ve které se nachází všechny logiku ověřování.</span><span class="sxs-lookup"><span data-stu-id="152ce-109">This is where all the validation logic resides.</span></span>  
  
-   <span data-ttu-id="152ce-110">Přepsat `System.Activities.CodeActivity.OnGetConstraints()` a přidat omezení (`PriceGreaterThanCost`) k omezením <xref:System.Collections.IList>.</span><span class="sxs-lookup"><span data-stu-id="152ce-110">Override `System.Activities.CodeActivity.OnGetConstraints()` and add the constraint (`PriceGreaterThanCost`) to the constraints <xref:System.Collections.IList>.</span></span>  
  
 <span data-ttu-id="152ce-111">Autor pracovního postupu (hlavní aplikace) musí:</span><span class="sxs-lookup"><span data-stu-id="152ce-111">The workflow author (main program) must:</span></span>  
  
-   <span data-ttu-id="152ce-112">Vytvoření pracovního postupu pomocí instance aktivity ověřit (`CreateProduct`).</span><span class="sxs-lookup"><span data-stu-id="152ce-112">Create a workflow with an instance of the activity to validate (`CreateProduct`).</span></span>  
  
-   <span data-ttu-id="152ce-113">Volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, který vrátí hodnotu <xref:System.Activities.Validation.ValidationResults> kolekce <xref:System.Activities.Validation.ValidationError>.</span><span class="sxs-lookup"><span data-stu-id="152ce-113">Call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.ValidationError>.</span></span>  
  
-   <span data-ttu-id="152ce-114">(Volitelné) Tisk <xref:System.Activities.Validation.ValidationError> objekty.</span><span class="sxs-lookup"><span data-stu-id="152ce-114">(Optional) Print the <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="152ce-115">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="152ce-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="152ce-116">Otevřete v ukázkovém řešení BasicValidation.sln [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="152ce-116">Open the BasicValidation.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="152ce-117">Sestavte a spusťte řešení.</span><span class="sxs-lookup"><span data-stu-id="152ce-117">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="152ce-118">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="152ce-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="152ce-119">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="152ce-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="152ce-120">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="152ce-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="152ce-121">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="152ce-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\BasicValidation`