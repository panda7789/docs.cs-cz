---
title: "Ověření externích aktivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49619f59-9819-484a-bcd8-5596308e8551
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6ebc79fa582a32ccc252e6c22b9b223870da7e44
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="external-activity-validation"></a><span data-ttu-id="89e63-102">Ověření externích aktivity</span><span class="sxs-lookup"><span data-stu-id="89e63-102">External Activity Validation</span></span>
<span data-ttu-id="89e63-103">Tento příklad ukazuje, jak přidat logiku ověření do předdefinovaných aktivity, která nejsou autora.</span><span class="sxs-lookup"><span data-stu-id="89e63-103">This sample shows how to add validation logic to a built-in activity that you are not the author of.</span></span> <span data-ttu-id="89e63-104">Logiku ověření se skládá z vynucení, který všechny <xref:System.Activities.Statements.If> aktivity k dispozici v pracovním postupu, musíte být jejich <xref:System.Activities.Statements.If.Then%2A> sada vlastností nebo jejich <xref:System.Activities.Statements.If.Else%2A> sadu vlastností.</span><span class="sxs-lookup"><span data-stu-id="89e63-104">The validation logic consists of enforcing that all <xref:System.Activities.Statements.If> activities present in the workflow either have their <xref:System.Activities.Statements.If.Then%2A> property set or their <xref:System.Activities.Statements.If.Else%2A> property set.</span></span> <span data-ttu-id="89e63-105">Navíc obsahuje logiku ověření kontrola, která všechny <xref:System.Activities.Statements.Pick> aktivity v pracovním postupu mají více než jeden větve, a pokud není tento případ, vygeneruje se upozornění.</span><span class="sxs-lookup"><span data-stu-id="89e63-105">Also, the validation logic includes checking that all <xref:System.Activities.Statements.Pick> activities present in the workflow have more than one branch, and if that is not the case, a warning is generated.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="89e63-106">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="89e63-106">Sample details</span></span>  
 <span data-ttu-id="89e63-107">Tato ukázka vytvoří pracovní postup s instancí každé aktivity ověřit: <xref:System.Activities.Statements.If> aktivity a <xref:System.Activities.Statements.Pick> aktivity.</span><span class="sxs-lookup"><span data-stu-id="89e63-107">This sample creates a workflow with an instance of each activity to validate: the <xref:System.Activities.Statements.If> activity and the <xref:System.Activities.Statements.Pick> activity.</span></span> <span data-ttu-id="89e63-108">A <xref:System.Activities.Validation.Constraint> se vytvoří pro každou chování při ověřování.</span><span class="sxs-lookup"><span data-stu-id="89e63-108">A <xref:System.Activities.Validation.Constraint> is created for each validation behavior.</span></span> <span data-ttu-id="89e63-109">Omezení vytvořené v této ukázce jsou `ConstraintError_IfShouldHaveThenOrElse` a `ConstraintWarning_PickHasOneBranch`.</span><span class="sxs-lookup"><span data-stu-id="89e63-109">The constraints created in this sample are `ConstraintError_IfShouldHaveThenOrElse` and `ConstraintWarning_PickHasOneBranch`.</span></span> <span data-ttu-id="89e63-110">V dalším kroku přidáte těchto omezení na `AdditionalConstraints` kolekce <xref:System.Activities.Validation.ValidationSettings> instance.</span><span class="sxs-lookup"><span data-stu-id="89e63-110">Next, these constraints are added to the `AdditionalConstraints` collection of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="89e63-111">Nakonec `static` <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> metodu <xref:System.Activities.Validation.ActivityValidationServices> je voláno k ověření aktivity v pracovním postupu a ověření výsledky budou vytištěny ke konzole.</span><span class="sxs-lookup"><span data-stu-id="89e63-111">Finally, the `static`<xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> method of <xref:System.Activities.Validation.ActivityValidationServices> is called to validate the activities in the workflow and the validation results are printed out to the console.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89e63-112">Omezení zásad můžete přidat do žádné aktivity.</span><span class="sxs-lookup"><span data-stu-id="89e63-112">You can add policy constraints to any activity.</span></span> <span data-ttu-id="89e63-113">Například můžete přidat zásady omezení <xref:System.Activities.Statements.Sequence> nebo <xref:System.Activities.Statements.Parallel> aktivity.</span><span class="sxs-lookup"><span data-stu-id="89e63-113">For example, you can add a policy constraint to a <xref:System.Activities.Statements.Sequence> or <xref:System.Activities.Statements.Parallel> activity.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="89e63-114">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="89e63-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="89e63-115">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor ExternalActivityValidation.sln.</span><span class="sxs-lookup"><span data-stu-id="89e63-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ExternalActivityValidation.sln file.</span></span>  
  
2.  <span data-ttu-id="89e63-116">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="89e63-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="89e63-117">Chcete-li spustit řešení, stiskněte Ctrl + F5.</span><span class="sxs-lookup"><span data-stu-id="89e63-117">To run the solution, press Ctrl+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="89e63-118">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="89e63-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="89e63-119">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="89e63-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="89e63-120">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="89e63-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="89e63-121">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="89e63-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ExternalActivityValidation`