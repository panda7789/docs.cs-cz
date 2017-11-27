---
title: "Omezení typů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6b246e6-1130-4698-9625-c5c42abcbfed
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f78337ebc643b584b89f26ca39e400fb8e6e9c26
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="constraint-types"></a><span data-ttu-id="8261c-102">Omezení typů</span><span class="sxs-lookup"><span data-stu-id="8261c-102">Constraint Types</span></span>
<span data-ttu-id="8261c-103">Tento příklad ukazuje dva různé způsoby použití omezení do pracovního postupu, jedna je z uvnitř aktivity (sestavení) a jeden z mimo (zásady).</span><span class="sxs-lookup"><span data-stu-id="8261c-103">This sample shows two different ways to apply constraints to a workflow, one is from inside the activity (build) and one is from outside of it (policy).</span></span> <span data-ttu-id="8261c-104">V tomto scénáři chce autor aktivity (od výrobce 3rth softwarové společnosti) k ověření vztah mezi dva argumenty.</span><span class="sxs-lookup"><span data-stu-id="8261c-104">In this scenario, an activity author (from a 3rth-party software company) wants to validate the relationship between two arguments.</span></span> <span data-ttu-id="8261c-105">V takovém případě náklady na by měla být menší než nebo rovna hodnotě cenu.</span><span class="sxs-lookup"><span data-stu-id="8261c-105">In this case, the cost should be smaller than or equal to the price.</span></span> <span data-ttu-id="8261c-106">Toto je omezení obecné ověření sestavení.</span><span class="sxs-lookup"><span data-stu-id="8261c-106">This is a general validation build constraint.</span></span>  
  
 <span data-ttu-id="8261c-107">Potom obchod vlastníka chce přidat některé ověřování pro tuto aktivitu Obecné.</span><span class="sxs-lookup"><span data-stu-id="8261c-107">Then a shop owner wants to add some validation to this generic activity.</span></span> <span data-ttu-id="8261c-108">V případě jeho chce většinu produkty být $9.99 nebo méně.</span><span class="sxs-lookup"><span data-stu-id="8261c-108">In his case, he wants the majority of its products to be $9.99 or less.</span></span> <span data-ttu-id="8261c-109">Ano, pomocí zásad omezení, která je na `CreateProduct` aktivity.</span><span class="sxs-lookup"><span data-stu-id="8261c-109">So, he uses a policy constraint that is on top of the `CreateProduct` activity.</span></span>  
  
 <span data-ttu-id="8261c-110">V ukázce:</span><span class="sxs-lookup"><span data-stu-id="8261c-110">In the sample:</span></span>  
  
 <span data-ttu-id="8261c-111">Musí se vytvořit aktivity (sestavení):</span><span class="sxs-lookup"><span data-stu-id="8261c-111">The activity author (build) must:</span></span>  
  
-   <span data-ttu-id="8261c-112">Vytvořit omezení (`PriceGreaterThanCost`).</span><span class="sxs-lookup"><span data-stu-id="8261c-112">Create a constraint (`PriceGreaterThanCost`).</span></span> <span data-ttu-id="8261c-113">Toto je, kde se nachází všechny logiku ověření.</span><span class="sxs-lookup"><span data-stu-id="8261c-113">This is where all the validation logic resides.</span></span>  
  
-   <span data-ttu-id="8261c-114">Přepsání `System.Activities.CodeActivity.OnGetConstraints()` a přidat omezení (`PriceGreaterThanCost`) k omezení <xref:System.Collections.IList>.</span><span class="sxs-lookup"><span data-stu-id="8261c-114">Override `System.Activities.CodeActivity.OnGetConstraints()` and add the constraint (`PriceGreaterThanCost`) to the constraints <xref:System.Collections.IList>.</span></span>  
  
 <span data-ttu-id="8261c-115">Musí se vytvořit pracovní postup (zásady):</span><span class="sxs-lookup"><span data-stu-id="8261c-115">The workflow author (policy) must:</span></span>  
  
-   <span data-ttu-id="8261c-116">Vytvoření pracovního postupu s instancí aktivity k ověření (`CreateProduct`).</span><span class="sxs-lookup"><span data-stu-id="8261c-116">Create a workflow with an instance of the activity to validate (`CreateProduct`).</span></span>  
  
-   <span data-ttu-id="8261c-117">Vytvořit omezení (`MaxPrice`).</span><span class="sxs-lookup"><span data-stu-id="8261c-117">Create a constraint (`MaxPrice`).</span></span>  
  
-   <span data-ttu-id="8261c-118">Vytvoření <xref:System.Activities.Validation.ValidationSettings> instance (`validationSettings`) a přidejte omezení (`MaxPrice`) do kolekce `AdditionalConstraints`.</span><span class="sxs-lookup"><span data-stu-id="8261c-118">Create a <xref:System.Activities.Validation.ValidationSettings> instance (`validationSettings`) and add the constraint (`MaxPrice`) to the collection `AdditionalConstraints`.</span></span> <span data-ttu-id="8261c-119">Zde Autor pracovního postupu můžete přidat omezení zásad pro všechny aktivity, například pořadí nebo paralelní.</span><span class="sxs-lookup"><span data-stu-id="8261c-119">Here the workflow author can add policy constraints to any activity, such as a sequence or parallel.</span></span>  
  
-   <span data-ttu-id="8261c-120">Volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, která vrátí <xref:System.Activities.Validation.ValidationResults> kolekce <xref:System.Activities.Validation.ValidationError> objekty.</span><span class="sxs-lookup"><span data-stu-id="8261c-120">Call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
-   <span data-ttu-id="8261c-121">(Volitelné) Tisk <xref:System.Activities.Validation.ValidationError> objekty.</span><span class="sxs-lookup"><span data-stu-id="8261c-121">(Optional) Print the <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8261c-122">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="8261c-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="8261c-123">Otevřete ConstraintTypes.sln ukázkové řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8261c-123">Open the ConstraintTypes.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="8261c-124">Sestavení a spuštění řešení.</span><span class="sxs-lookup"><span data-stu-id="8261c-124">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8261c-125">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="8261c-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8261c-126">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="8261c-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8261c-127">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="8261c-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8261c-128">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="8261c-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Validation\ConstraintLibrary`  
  
## <a name="see-also"></a><span data-ttu-id="8261c-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="8261c-129">See Also</span></span>
