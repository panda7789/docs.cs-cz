---
title: Typy omezení
ms.date: 03/30/2017
ms.assetid: b6b246e6-1130-4698-9625-c5c42abcbfed
ms.openlocfilehash: 202a2c7b3a3fc400552e42c8606457964af66af2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401529"
---
# <a name="constraint-types"></a><span data-ttu-id="ba936-102">Typy omezení</span><span class="sxs-lookup"><span data-stu-id="ba936-102">Constraint Types</span></span>
<span data-ttu-id="ba936-103">Tento příklad ukazuje dva různé způsoby použití omezení do pracovního postupu, jeden je uvnitř aktivity (build) a jeden je z mimo něj (zásady).</span><span class="sxs-lookup"><span data-stu-id="ba936-103">This sample shows two different ways to apply constraints to a workflow, one is from inside the activity (build) and one is from outside of it (policy).</span></span> <span data-ttu-id="ba936-104">V tomto scénáři chce autor aktivity (ze strany 3rth softwarovou společnost) ověření vztahu mezi dvěma argumenty.</span><span class="sxs-lookup"><span data-stu-id="ba936-104">In this scenario, an activity author (from a 3rth-party software company) wants to validate the relationship between two arguments.</span></span> <span data-ttu-id="ba936-105">V tomto případě náklady na by měla být menší než nebo rovna hodnotě cena.</span><span class="sxs-lookup"><span data-stu-id="ba936-105">In this case, the cost should be smaller than or equal to the price.</span></span> <span data-ttu-id="ba936-106">Toto je omezení obecné ověření sestavení.</span><span class="sxs-lookup"><span data-stu-id="ba936-106">This is a general validation build constraint.</span></span>  
  
 <span data-ttu-id="ba936-107">Potom kupte vlastník chce přidat nějaké ověření této obecné aktivitě.</span><span class="sxs-lookup"><span data-stu-id="ba936-107">Then a shop owner wants to add some validation to this generic activity.</span></span> <span data-ttu-id="ba936-108">V případě jeho chce většinou produkty bude 9,99 USD nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="ba936-108">In his case, he wants the majority of its products to be $9.99 or less.</span></span> <span data-ttu-id="ba936-109">Ano, pomocí zásad omezení, které je nad `CreateProduct` aktivity.</span><span class="sxs-lookup"><span data-stu-id="ba936-109">So, he uses a policy constraint that is on top of the `CreateProduct` activity.</span></span>  
  
 <span data-ttu-id="ba936-110">V ukázce:</span><span class="sxs-lookup"><span data-stu-id="ba936-110">In the sample:</span></span>  
  
 <span data-ttu-id="ba936-111">Musí být autorem aktivity (build):</span><span class="sxs-lookup"><span data-stu-id="ba936-111">The activity author (build) must:</span></span>  
  
-   <span data-ttu-id="ba936-112">Vytvoření omezení (`PriceGreaterThanCost`).</span><span class="sxs-lookup"><span data-stu-id="ba936-112">Create a constraint (`PriceGreaterThanCost`).</span></span> <span data-ttu-id="ba936-113">To je, ve které se nachází všechny logiku ověřování.</span><span class="sxs-lookup"><span data-stu-id="ba936-113">This is where all the validation logic resides.</span></span>  
  
-   <span data-ttu-id="ba936-114">Přepsat `System.Activities.CodeActivity.OnGetConstraints()` a přidat omezení (`PriceGreaterThanCost`) k omezením <xref:System.Collections.IList>.</span><span class="sxs-lookup"><span data-stu-id="ba936-114">Override `System.Activities.CodeActivity.OnGetConstraints()` and add the constraint (`PriceGreaterThanCost`) to the constraints <xref:System.Collections.IList>.</span></span>  
  
 <span data-ttu-id="ba936-115">Musí se vytvořit pracovní postup (zásady):</span><span class="sxs-lookup"><span data-stu-id="ba936-115">The workflow author (policy) must:</span></span>  
  
-   <span data-ttu-id="ba936-116">Vytvoření pracovního postupu pomocí instance aktivity ověřit (`CreateProduct`).</span><span class="sxs-lookup"><span data-stu-id="ba936-116">Create a workflow with an instance of the activity to validate (`CreateProduct`).</span></span>  
  
-   <span data-ttu-id="ba936-117">Vytvoření omezení (`MaxPrice`).</span><span class="sxs-lookup"><span data-stu-id="ba936-117">Create a constraint (`MaxPrice`).</span></span>  
  
-   <span data-ttu-id="ba936-118">Vytvoření <xref:System.Activities.Validation.ValidationSettings> instance (`validationSettings`) a přidat omezení (`MaxPrice`) do kolekce `AdditionalConstraints`.</span><span class="sxs-lookup"><span data-stu-id="ba936-118">Create a <xref:System.Activities.Validation.ValidationSettings> instance (`validationSettings`) and add the constraint (`MaxPrice`) to the collection `AdditionalConstraints`.</span></span> <span data-ttu-id="ba936-119">Tady Autor pracovního postupu můžete přidat omezení zásad pro všechny aktivity, jako je například pořadí nebo paralelní.</span><span class="sxs-lookup"><span data-stu-id="ba936-119">Here the workflow author can add policy constraints to any activity, such as a sequence or parallel.</span></span>  
  
-   <span data-ttu-id="ba936-120">Volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, který vrátí hodnotu <xref:System.Activities.Validation.ValidationResults> kolekce <xref:System.Activities.Validation.ValidationError> objekty.</span><span class="sxs-lookup"><span data-stu-id="ba936-120">Call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
-   <span data-ttu-id="ba936-121">(Volitelné) Tisk <xref:System.Activities.Validation.ValidationError> objekty.</span><span class="sxs-lookup"><span data-stu-id="ba936-121">(Optional) Print the <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ba936-122">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="ba936-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ba936-123">Otevřete v ukázkovém řešení ConstraintTypes.sln [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ba936-123">Open the ConstraintTypes.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="ba936-124">Sestavte a spusťte řešení.</span><span class="sxs-lookup"><span data-stu-id="ba936-124">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ba936-125">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="ba936-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ba936-126">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ba936-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ba936-127">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="ba936-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ba936-128">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="ba936-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Validation\ConstraintLibrary`