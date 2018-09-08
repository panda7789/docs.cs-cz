---
title: Ověřování relací mezi aktivitami
ms.date: 03/30/2017
ms.assetid: 6f11a34e-ed67-4bce-88ce-7e96bbb4d052
ms.openlocfilehash: 50f08118fb5ad4d9b8fe809e7ab3cc5d57f28149
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44193663"
---
# <a name="activity-relationships-validation"></a><span data-ttu-id="41d83-102">Ověřování relací mezi aktivitami</span><span class="sxs-lookup"><span data-stu-id="41d83-102">Activity Relationships Validation</span></span>
<span data-ttu-id="41d83-103">Tento příklad se skládá ze tří činností `CreateCity`, `CreateState`, a `CreateCountry`.</span><span class="sxs-lookup"><span data-stu-id="41d83-103">This sample consists of three activities, `CreateCity`, `CreateState`, and `CreateCountry`.</span></span> <span data-ttu-id="41d83-104">`CreateCity` musí být uvnitř `CreateState` aktivitu, a `CreateState` musí být uvnitř `CreateCountry` aktivity.</span><span class="sxs-lookup"><span data-stu-id="41d83-104">`CreateCity` must be inside a `CreateState` activity, and `CreateState` must be inside a `CreateCountry` activity.</span></span> <span data-ttu-id="41d83-105">Pro účely této ukázce logiku ověřování je v kódu `CreateState` aktivitu a v XAML pro `CreateCity` aktivity.</span><span class="sxs-lookup"><span data-stu-id="41d83-105">For the purpose of this sample, the validation logic is in code for the `CreateState` activity, and in XAML for the `CreateCity` activity.</span></span> <span data-ttu-id="41d83-106">Obě omezení mají stejné chování.</span><span class="sxs-lookup"><span data-stu-id="41d83-106">Both constraints have the same behavior.</span></span>  
  
 <span data-ttu-id="41d83-107">[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Poskytuje následující tři aktivity pomocné rutiny, které umožňuje vývojářům ověřit relací mezi aktivitami:</span><span class="sxs-lookup"><span data-stu-id="41d83-107">The [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] provides the following three helper activities that allow the developer to validate relationships between activities:</span></span>  
  
 <xref:System.Activities.Validation.GetParentChain>  
 <span data-ttu-id="41d83-108">Obsahuje kolekci všech aktivit, které patří do nadřazeného aktuální uzel</span><span class="sxs-lookup"><span data-stu-id="41d83-108">Provides the collection of all activities that belong to the parent of the current node</span></span>  
  
 <xref:System.Activities.Validation.GetChildSubtree>  
 <span data-ttu-id="41d83-109">Obsahuje kolekci všech aktivit, které patří do dílčí stromu pro aktuální uzel, s výjimkou aktuální uzel</span><span class="sxs-lookup"><span data-stu-id="41d83-109">Provides the collection of all activities that belong to the sub-tree of the current node, excluding the current node</span></span>  
  
 <xref:System.Activities.Validation.GetWorkflowTree>  
 <span data-ttu-id="41d83-110">Obsahuje kolekci všech aktivit ve stejném stromu pro jako aktuální uzel</span><span class="sxs-lookup"><span data-stu-id="41d83-110">Provides the collection of all activities in the same tree as the current node</span></span>  
  
 <span data-ttu-id="41d83-111">V ukázce <xref:System.Activities.Statements.ForEach%601> aktivita se používá k provede kolekci vrácené poskytovatelem <xref:System.Activities.Validation.GetParentChain>.</span><span class="sxs-lookup"><span data-stu-id="41d83-111">In the sample, a <xref:System.Activities.Statements.ForEach%601> activity is used to walk through the collection returned by <xref:System.Activities.Validation.GetParentChain>.</span></span> <span data-ttu-id="41d83-112">Pro každý prvek v kolekci, jeho typ je ve srovnání s `CreateCountry` (nebo `CreateState` Pokud `CreateCity` ověřován), a když se najde shoda výsledek příznak je nastaven na `true`.</span><span class="sxs-lookup"><span data-stu-id="41d83-112">For every element in the collection, its type is compared to `CreateCountry` (or `CreateState` if `CreateCity` is being validated), and when a match is found the result flag is set to `true`.</span></span> <span data-ttu-id="41d83-113">A konečně <xref:System.Activities.Validation.AssertValidation> se používá k vygenerování chyby ověřování, pokud výsledek příznak je nastaven na `false`.</span><span class="sxs-lookup"><span data-stu-id="41d83-113">Finally, an <xref:System.Activities.Validation.AssertValidation> is used to generate a validation error if the result flag is set to `false`.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="41d83-114">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="41d83-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="41d83-115">Otevřete v ukázkovém řešení ContainmentValidation.sln [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="41d83-115">Open the ContainmentValidation.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="41d83-116">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="41d83-116">Build the solution.</span></span>  
  
3.  <span data-ttu-id="41d83-117">Stisknutím kláves CTRL + F5 spusťte program.</span><span class="sxs-lookup"><span data-stu-id="41d83-117">Press CTRL + F5 to launch the program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="41d83-118">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="41d83-118">The samples may already be installed on your computer.</span></span> <span data-ttu-id="41d83-119">Před pokračováním zkontrolujte následující adresář (výchozí):</span><span class="sxs-lookup"><span data-stu-id="41d83-119">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="41d83-120">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="41d83-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="41d83-121">Tato ukázka se nachází v následujícím adresáři:</span><span class="sxs-lookup"><span data-stu-id="41d83-121">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ActivityRelationships`
