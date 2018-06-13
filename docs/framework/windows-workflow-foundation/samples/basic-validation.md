---
title: Základní ověřování
ms.date: 03/30/2017
ms.assetid: ba1343cc-aaab-4ade-b0c0-1dd5063bf4ad
ms.openlocfilehash: db7db339d0b7bfd756d8ba22fb8488b8f7ecfa3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514078"
---
# <a name="basic-validation"></a><span data-ttu-id="ac2fa-102">Základní ověřování</span><span class="sxs-lookup"><span data-stu-id="ac2fa-102">Basic Validation</span></span>
<span data-ttu-id="ac2fa-103">Tato ukázka se skládá z aktivity, `CreateProduct`, který ověří, jestli jeho `Cost` argument je menší než nebo rovno jeho `Price` argument.</span><span class="sxs-lookup"><span data-stu-id="ac2fa-103">This sample consists of an activity, `CreateProduct`, which validates that its `Cost` argument is smaller than or equal to its `Price` argument.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="ac2fa-104">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ac2fa-104">Sample Details</span></span>  
 <span data-ttu-id="ac2fa-105">Existují dva autoři, které používají ověřování, Autor aktivity (vytvoří logiku ověření pro aktivitu) a Autor pracovního postupu, který volá služby ověřování v určitém pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="ac2fa-105">There are two authors that use validation, the activity author (creates the validation logic for the activity) and the workflow author that calls validation services on a specific workflow.</span></span> <span data-ttu-id="ac2fa-106">V tomto scénáři chce autor aktivity vynutit, že každá instance svou činnost musí mít menší nebo rovna nákladech, než který ceny.</span><span class="sxs-lookup"><span data-stu-id="ac2fa-106">In this scenario, the activity author wants to enforce that every instance of his activity must have a smaller or equal cost than that of the price.</span></span>  
  
 <span data-ttu-id="ac2fa-107">Musíte vytvořit aktivity (uvnitř aktivita):</span><span class="sxs-lookup"><span data-stu-id="ac2fa-107">The activity author (inside the activity) must:</span></span>  
  
-   <span data-ttu-id="ac2fa-108">Vytvořit omezení (`PriceGreaterThanCost`).</span><span class="sxs-lookup"><span data-stu-id="ac2fa-108">Create a constraint (`PriceGreaterThanCost`).</span></span> <span data-ttu-id="ac2fa-109">Toto je, kde se nachází všechny logiku ověření.</span><span class="sxs-lookup"><span data-stu-id="ac2fa-109">This is where all the validation logic resides.</span></span>  
  
-   <span data-ttu-id="ac2fa-110">Přepsání `System.Activities.CodeActivity.OnGetConstraints()` a přidat omezení (`PriceGreaterThanCost`) k omezení <xref:System.Collections.IList>.</span><span class="sxs-lookup"><span data-stu-id="ac2fa-110">Override `System.Activities.CodeActivity.OnGetConstraints()` and add the constraint (`PriceGreaterThanCost`) to the constraints <xref:System.Collections.IList>.</span></span>  
  
 <span data-ttu-id="ac2fa-111">Autor pracovního postupu (hlavní aplikace) musí:</span><span class="sxs-lookup"><span data-stu-id="ac2fa-111">The workflow author (main program) must:</span></span>  
  
-   <span data-ttu-id="ac2fa-112">Vytvoření pracovního postupu s instancí aktivity k ověření (`CreateProduct`).</span><span class="sxs-lookup"><span data-stu-id="ac2fa-112">Create a workflow with an instance of the activity to validate (`CreateProduct`).</span></span>  
  
-   <span data-ttu-id="ac2fa-113">Volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, která vrátí <xref:System.Activities.Validation.ValidationResults> kolekce <xref:System.Activities.Validation.ValidationError>.</span><span class="sxs-lookup"><span data-stu-id="ac2fa-113">Call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.ValidationError>.</span></span>  
  
-   <span data-ttu-id="ac2fa-114">(Volitelné) Tisk <xref:System.Activities.Validation.ValidationError> objekty.</span><span class="sxs-lookup"><span data-stu-id="ac2fa-114">(Optional) Print the <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ac2fa-115">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="ac2fa-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ac2fa-116">Otevřete BasicValidation.sln ukázkové řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ac2fa-116">Open the BasicValidation.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="ac2fa-117">Sestavení a spuštění řešení.</span><span class="sxs-lookup"><span data-stu-id="ac2fa-117">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ac2fa-118">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="ac2fa-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ac2fa-119">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ac2fa-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ac2fa-120">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="ac2fa-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ac2fa-121">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="ac2fa-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\BasicValidation`