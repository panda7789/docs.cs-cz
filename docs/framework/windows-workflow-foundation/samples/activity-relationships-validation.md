---
title: Ověření vztahy aktivity
ms.date: 03/30/2017
ms.assetid: 6f11a34e-ed67-4bce-88ce-7e96bbb4d052
ms.openlocfilehash: e6dd0e6a7b48444073ebae378e21c1b45977a1f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515105"
---
# <a name="activity-relationships-validation"></a><span data-ttu-id="ff8ac-102">Ověření vztahy aktivity</span><span class="sxs-lookup"><span data-stu-id="ff8ac-102">Activity Relationships Validation</span></span>
<span data-ttu-id="ff8ac-103">Tato ukázka se skládá ze tří aktivity `CreateCity`, `CreateState`, a `CreateCountry`.</span><span class="sxs-lookup"><span data-stu-id="ff8ac-103">This sample consists of three activities, `CreateCity`, `CreateState`, and `CreateCountry`.</span></span> <span data-ttu-id="ff8ac-104">`CreateCity` musí být uvnitř `CreateState` aktivitu, a `CreateState` musí být uvnitř `CreateCountry` aktivity.</span><span class="sxs-lookup"><span data-stu-id="ff8ac-104">`CreateCity` must be inside a `CreateState` activity, and `CreateState` must be inside a `CreateCountry` activity.</span></span> <span data-ttu-id="ff8ac-105">V tomto příkladu je logiku ověření v kódu `CreateState` aktivitu a v jazyce XAML pro `CreateCity` aktivity.</span><span class="sxs-lookup"><span data-stu-id="ff8ac-105">For the purpose of this sample, the validation logic is in code for the `CreateState` activity, and in XAML for the `CreateCity` activity.</span></span> <span data-ttu-id="ff8ac-106">Obě omezení mít stejné chování.</span><span class="sxs-lookup"><span data-stu-id="ff8ac-106">Both constraints have the same behavior.</span></span>  
  
 <span data-ttu-id="ff8ac-107">[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Poskytuje následující tři aktivity pomocné rutiny, které umožňuje vývojářům ověření vztahy mezi aktivitami:</span><span class="sxs-lookup"><span data-stu-id="ff8ac-107">The [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] provides the following three helper activities that allow the developer to validate relationships between activities:</span></span>  
  
 <xref:System.Activities.Validation.GetParentChain>  
 <span data-ttu-id="ff8ac-108">Poskytuje kolekci všechny aktivity, které patří do nadřazené aktuálního uzlu</span><span class="sxs-lookup"><span data-stu-id="ff8ac-108">Provides the collection of all activities that belong to the parent of the current node</span></span>  
  
 <xref:System.Activities.Validation.GetChildSubtree>  
 <span data-ttu-id="ff8ac-109">Poskytuje kolekci všechny aktivity, které patří do stromu dílčí aktuální uzel, s výjimkou aktuálního uzlu</span><span class="sxs-lookup"><span data-stu-id="ff8ac-109">Provides the collection of all activities that belong to the sub-tree of the current node, excluding the current node</span></span>  
  
 <xref:System.Activities.Validation.GetWorkflowTree>  
 <span data-ttu-id="ff8ac-110">Poskytuje kolekci všechny aktivity ve stejném stromu pro jako aktuálního uzlu</span><span class="sxs-lookup"><span data-stu-id="ff8ac-110">Provides the collection of all activities in the same tree as the current node</span></span>  
  
 <span data-ttu-id="ff8ac-111">V ukázce <xref:System.Activities.Statements.ForEach%601> aktivita se používá k provede kolekce vrácené <xref:System.Activities.Validation.GetParentChain>.</span><span class="sxs-lookup"><span data-stu-id="ff8ac-111">In the sample, a <xref:System.Activities.Statements.ForEach%601> activity is used to walk through the collection returned by <xref:System.Activities.Validation.GetParentChain>.</span></span> <span data-ttu-id="ff8ac-112">Pro každý element v kolekci, je její typ porovnání s `CreateCountry` (nebo `CreateState` Pokud `CreateCity` je ověřován), a pokud je nalezena shoda příznak výsledek je nastaven na `true`.</span><span class="sxs-lookup"><span data-stu-id="ff8ac-112">For every element in the collection, its type is compared to `CreateCountry` (or `CreateState` if `CreateCity` is being validated), and when a match is found the result flag is set to `true`.</span></span> <span data-ttu-id="ff8ac-113">Nakonec <xref:System.Activities.Validation.AssertValidation> slouží ke generování chybu ověření, pokud je výsledek příznak nastaven na `false`.</span><span class="sxs-lookup"><span data-stu-id="ff8ac-113">Finally, an <xref:System.Activities.Validation.AssertValidation> is used to generate a validation error if the result flag is set to `false`.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="ff8ac-114">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="ff8ac-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="ff8ac-115">Otevřete ContainmentValidation.sln ukázkové řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ff8ac-115">Open the ContainmentValidation.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="ff8ac-116">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="ff8ac-116">Build the solution.</span></span>  
  
3.  <span data-ttu-id="ff8ac-117">Stisknutím kláves CTRL + F5 spusťte program.</span><span class="sxs-lookup"><span data-stu-id="ff8ac-117">Press CTRL + F5 to launch the program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ff8ac-118">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="ff8ac-118">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ff8ac-119">Před pokračováním zkontrolovat na následující adresář (výchozí):</span><span class="sxs-lookup"><span data-stu-id="ff8ac-119">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ff8ac-120">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="ff8ac-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ff8ac-121">Tato ukázka se nachází v následujícím adresáři:</span><span class="sxs-lookup"><span data-stu-id="ff8ac-121">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ActivityRelationships`
