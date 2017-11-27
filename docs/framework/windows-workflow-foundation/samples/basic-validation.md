---
title: "Základní ověřování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba1343cc-aaab-4ade-b0c0-1dd5063bf4ad
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d388b3d6acad28e4ff952f72aa64a607d745f307
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="basic-validation"></a><span data-ttu-id="d3895-102">Základní ověřování</span><span class="sxs-lookup"><span data-stu-id="d3895-102">Basic Validation</span></span>
<span data-ttu-id="d3895-103">Tato ukázka se skládá z aktivity, `CreateProduct`, který ověří, jestli jeho `Cost` argument je menší než nebo rovno jeho `Price` argument.</span><span class="sxs-lookup"><span data-stu-id="d3895-103">This sample consists of an activity, `CreateProduct`, which validates that its `Cost` argument is smaller than or equal to its `Price` argument.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="d3895-104">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="d3895-104">Sample Details</span></span>  
 <span data-ttu-id="d3895-105">Existují dva autoři, které používají ověřování, Autor aktivity (vytvoří logiku ověření pro aktivitu) a Autor pracovního postupu, který volá služby ověřování v určitém pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="d3895-105">There are two authors that use validation, the activity author (creates the validation logic for the activity) and the workflow author that calls validation services on a specific workflow.</span></span> <span data-ttu-id="d3895-106">V tomto scénáři chce autor aktivity vynutit, že každá instance svou činnost musí mít menší nebo rovna nákladech, než který ceny.</span><span class="sxs-lookup"><span data-stu-id="d3895-106">In this scenario, the activity author wants to enforce that every instance of his activity must have a smaller or equal cost than that of the price.</span></span>  
  
 <span data-ttu-id="d3895-107">Musíte vytvořit aktivity (uvnitř aktivita):</span><span class="sxs-lookup"><span data-stu-id="d3895-107">The activity author (inside the activity) must:</span></span>  
  
-   <span data-ttu-id="d3895-108">Vytvořit omezení (`PriceGreaterThanCost`).</span><span class="sxs-lookup"><span data-stu-id="d3895-108">Create a constraint (`PriceGreaterThanCost`).</span></span> <span data-ttu-id="d3895-109">Toto je, kde se nachází všechny logiku ověření.</span><span class="sxs-lookup"><span data-stu-id="d3895-109">This is where all the validation logic resides.</span></span>  
  
-   <span data-ttu-id="d3895-110">Přepsání `System.Activities.CodeActivity.OnGetConstraints()` a přidat omezení (`PriceGreaterThanCost`) k omezení <xref:System.Collections.IList>.</span><span class="sxs-lookup"><span data-stu-id="d3895-110">Override `System.Activities.CodeActivity.OnGetConstraints()` and add the constraint (`PriceGreaterThanCost`) to the constraints <xref:System.Collections.IList>.</span></span>  
  
 <span data-ttu-id="d3895-111">Autor pracovního postupu (hlavní aplikace) musí:</span><span class="sxs-lookup"><span data-stu-id="d3895-111">The workflow author (main program) must:</span></span>  
  
-   <span data-ttu-id="d3895-112">Vytvoření pracovního postupu s instancí aktivity k ověření (`CreateProduct`).</span><span class="sxs-lookup"><span data-stu-id="d3895-112">Create a workflow with an instance of the activity to validate (`CreateProduct`).</span></span>  
  
-   <span data-ttu-id="d3895-113">Volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, která vrátí <xref:System.Activities.Validation.ValidationResults> kolekce <xref:System.Activities.Validation.ValidationError>.</span><span class="sxs-lookup"><span data-stu-id="d3895-113">Call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.ValidationError>.</span></span>  
  
-   <span data-ttu-id="d3895-114">(Volitelné) Tisk <xref:System.Activities.Validation.ValidationError> objekty.</span><span class="sxs-lookup"><span data-stu-id="d3895-114">(Optional) Print the <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d3895-115">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="d3895-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d3895-116">Otevřete BasicValidation.sln ukázkové řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d3895-116">Open the BasicValidation.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="d3895-117">Sestavení a spuštění řešení.</span><span class="sxs-lookup"><span data-stu-id="d3895-117">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d3895-118">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="d3895-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d3895-119">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="d3895-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d3895-120">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="d3895-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d3895-121">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="d3895-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\BasicValidation`  
  
## <a name="see-also"></a><span data-ttu-id="d3895-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3895-122">See Also</span></span>
