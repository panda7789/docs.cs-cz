---
title: "Ověření vztahy aktivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f11a34e-ed67-4bce-88ce-7e96bbb4d052
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 03ac8e41f8126c6b05eac82d143291a0de491969
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="activity-relationships-validation"></a><span data-ttu-id="e6e0b-102">Ověření vztahy aktivity</span><span class="sxs-lookup"><span data-stu-id="e6e0b-102">Activity Relationships Validation</span></span>
<span data-ttu-id="e6e0b-103">Tato ukázka se skládá ze tří aktivity `CreateCity`, `CreateState`, a `CreateCountry`.</span><span class="sxs-lookup"><span data-stu-id="e6e0b-103">This sample consists of three activities, `CreateCity`, `CreateState`, and `CreateCountry`.</span></span> <span data-ttu-id="e6e0b-104">`CreateCity`musí být uvnitř `CreateState` aktivitu, a `CreateState` musí být uvnitř `CreateCountry` aktivity.</span><span class="sxs-lookup"><span data-stu-id="e6e0b-104">`CreateCity` must be inside a `CreateState` activity, and `CreateState` must be inside a `CreateCountry` activity.</span></span> <span data-ttu-id="e6e0b-105">V tomto příkladu je logiku ověření v kódu `CreateState` aktivitu a v jazyce XAML pro `CreateCity` aktivity.</span><span class="sxs-lookup"><span data-stu-id="e6e0b-105">For the purpose of this sample, the validation logic is in code for the `CreateState` activity, and in XAML for the `CreateCity` activity.</span></span> <span data-ttu-id="e6e0b-106">Obě omezení mít stejné chování.</span><span class="sxs-lookup"><span data-stu-id="e6e0b-106">Both constraints have the same behavior.</span></span>  
  
 <span data-ttu-id="e6e0b-107">[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Poskytuje následující tři aktivity pomocné rutiny, které umožňuje vývojářům ověření vztahy mezi aktivitami:</span><span class="sxs-lookup"><span data-stu-id="e6e0b-107">The [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] provides the following three helper activities that allow the developer to validate relationships between activities:</span></span>  
  
 <xref:System.Activities.Validation.GetParentChain>  
 <span data-ttu-id="e6e0b-108">Poskytuje kolekci všechny aktivity, které patří do nadřazené aktuálního uzlu</span><span class="sxs-lookup"><span data-stu-id="e6e0b-108">Provides the collection of all activities that belong to the parent of the current node</span></span>  
  
 <xref:System.Activities.Validation.GetChildSubtree>  
 <span data-ttu-id="e6e0b-109">Poskytuje kolekci všechny aktivity, které patří do stromu dílčí aktuální uzel, s výjimkou aktuálního uzlu</span><span class="sxs-lookup"><span data-stu-id="e6e0b-109">Provides the collection of all activities that belong to the sub-tree of the current node, excluding the current node</span></span>  
  
 <xref:System.Activities.Validation.GetWorkflowTree>  
 <span data-ttu-id="e6e0b-110">Poskytuje kolekci všechny aktivity ve stejném stromu pro jako aktuálního uzlu</span><span class="sxs-lookup"><span data-stu-id="e6e0b-110">Provides the collection of all activities in the same tree as the current node</span></span>  
  
 <span data-ttu-id="e6e0b-111">V ukázce <xref:System.Activities.Statements.ForEach%601> aktivita se používá k provede kolekce vrácené <xref:System.Activities.Validation.GetParentChain>.</span><span class="sxs-lookup"><span data-stu-id="e6e0b-111">In the sample, a <xref:System.Activities.Statements.ForEach%601> activity is used to walk through the collection returned by <xref:System.Activities.Validation.GetParentChain>.</span></span> <span data-ttu-id="e6e0b-112">Pro každý element v kolekci, je její typ porovnání s `CreateCountry` (nebo `CreateState` Pokud `CreateCity` je ověřován), a pokud je nalezena shoda příznak výsledek je nastaven na `true`.</span><span class="sxs-lookup"><span data-stu-id="e6e0b-112">For every element in the collection, its type is compared to `CreateCountry` (or `CreateState` if `CreateCity` is being validated), and when a match is found the result flag is set to `true`.</span></span> <span data-ttu-id="e6e0b-113">Nakonec <xref:System.Activities.Validation.AssertValidation> slouží ke generování chybu ověření, pokud je výsledek příznak nastaven na `false`.</span><span class="sxs-lookup"><span data-stu-id="e6e0b-113">Finally, an <xref:System.Activities.Validation.AssertValidation> is used to generate a validation error if the result flag is set to `false`.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="e6e0b-114">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="e6e0b-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="e6e0b-115">Otevřete ContainmentValidation.sln ukázkové řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e6e0b-115">Open the ContainmentValidation.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="e6e0b-116">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="e6e0b-116">Build the solution.</span></span>  
  
3.  <span data-ttu-id="e6e0b-117">Stisknutím kláves CTRL + F5 spusťte program.</span><span class="sxs-lookup"><span data-stu-id="e6e0b-117">Press CTRL + F5 to launch the program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e6e0b-118">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="e6e0b-118">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e6e0b-119">Před pokračováním zkontrolovat na následující adresář (výchozí):</span><span class="sxs-lookup"><span data-stu-id="e6e0b-119">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e6e0b-120">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="e6e0b-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e6e0b-121">Tato ukázka se nachází v následujícím adresáři:</span><span class="sxs-lookup"><span data-stu-id="e6e0b-121">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ActivityRelationships`  
  
## <a name="see-also"></a><span data-ttu-id="e6e0b-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6e0b-122">See Also</span></span>
