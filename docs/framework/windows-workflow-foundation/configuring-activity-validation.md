---
title: "Konfigurace ověření aktivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25a4eccb-b8fc-4857-a01d-2683b6341219
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d75f03a9af5caa5569cbfd4d1d09cda8936f6562
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-activity-validation"></a><span data-ttu-id="0995e-102">Konfigurace ověření aktivity</span><span class="sxs-lookup"><span data-stu-id="0995e-102">Configuring Activity Validation</span></span>
<span data-ttu-id="0995e-103">Aktivita ověření umožňuje autorům aktivity a uživatelé identifikovat a zprávy o chybách v konfiguraci aktivity před jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="0995e-103">Activity validation enables activity authors and users to identify and report errors in an activity’s configuration prior to its execution.</span></span> [!INCLUDE[wf](../../../includes/wf-md.md)]<span data-ttu-id="0995e-104">poskytuje následující tři typy ověření aktivity:</span><span class="sxs-lookup"><span data-stu-id="0995e-104"> provides the following three types of activity validation:</span></span>  
  
-   <span data-ttu-id="0995e-105">`RequiredArgument`a `OverloadGroup` atributy.</span><span class="sxs-lookup"><span data-stu-id="0995e-105">`RequiredArgument` and `OverloadGroup` attributes.</span></span>  
  
-   <span data-ttu-id="0995e-106">Imperativní ověření založené na kódu.</span><span class="sxs-lookup"><span data-stu-id="0995e-106">Imperative code-based validation.</span></span>  
  
-   <span data-ttu-id="0995e-107">Deklarativní omezení.</span><span class="sxs-lookup"><span data-stu-id="0995e-107">Declarative constraints.</span></span>  
  
 <span data-ttu-id="0995e-108">`RequiredArgument`a `OverloadGroup` atributy označuje, že některé argumenty u aktivit je požadovaná.</span><span class="sxs-lookup"><span data-stu-id="0995e-108">`RequiredArgument` and `OverloadGroup` attributes indicate that certain arguments on an activity are required.</span></span> <span data-ttu-id="0995e-109">Imperativní ověření založené na kódu poskytuje jednoduchý způsob, jak aktivity pro ověřování o samotné a deklarativní omezení povolit ověření o aktivity a jeho relace s obsažený pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="0995e-109">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and declarative constraints enable validation about the activity and its relationship with the containing workflow.</span></span> <span data-ttu-id="0995e-110">Pokud aktivita není správně nakonfigurována podle požadavků ověřování, vrátí se chyby ověření a upozornění.</span><span class="sxs-lookup"><span data-stu-id="0995e-110">If an activity is not configured properly according to the validation requirements, validation errors and warnings are returned.</span></span> <span data-ttu-id="0995e-111">Pokud obsažený pracovní postup je vytvořený pomocí návrháře pracovních postupů, všechny chyby ověření a upozornění se zobrazí v návrháři.</span><span class="sxs-lookup"><span data-stu-id="0995e-111">If the containing workflow is created using the workflow designer, any validation errors and warnings are displayed in the designer.</span></span> <span data-ttu-id="0995e-112">Pokud pracovní postup je vytvořen mimo návrháře pracovních postupů jsou vráceny všechny chyby ověření při vyvolání pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="0995e-112">If the workflow is created outside of the workflow designer any validation errors are returned when the workflow is invoked.</span></span> <span data-ttu-id="0995e-113">Bez ohledu na to, jak byl vytvořen pracovní postup nemá nikdy pracovního postupu se chyby ověření provést.</span><span class="sxs-lookup"><span data-stu-id="0995e-113">Regardless of how the workflow was created, a workflow with validation errors is never allowed to execute.</span></span> <span data-ttu-id="0995e-114">Tato část obsahuje přehled těchto typů ověřování aktivity a způsob volání ověření aktivity.</span><span class="sxs-lookup"><span data-stu-id="0995e-114">This section provides an overview of these types of activity validation and how activity validation is invoked.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0995e-115">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0995e-115">In This Section</span></span>  
 [<span data-ttu-id="0995e-116">Povinné argumenty a skupiny přetížení</span><span class="sxs-lookup"><span data-stu-id="0995e-116">Required Arguments and Overload Groups</span></span>](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md)  
 <span data-ttu-id="0995e-117">Popisuje postup použití `RequiredArgument` a `OverloadGroup` atributy pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="0995e-117">Describes how to use the `RequiredArgument` and `OverloadGroup` attributes to provide validation.</span></span>  
  
 [<span data-ttu-id="0995e-118">Ověřování na základě imperativního kódu</span><span class="sxs-lookup"><span data-stu-id="0995e-118">Imperative Code-Based Validation</span></span>](../../../docs/framework/windows-workflow-foundation/imperative-code-based-validation.md)  
 <span data-ttu-id="0995e-119">Popisuje, jak používat ověřování založené na kódu <xref:System.Activities.CodeActivity> a <xref:System.Activities.NativeActivity> na základě aktivity.</span><span class="sxs-lookup"><span data-stu-id="0995e-119">Describes how to use code-based validation for <xref:System.Activities.CodeActivity> and <xref:System.Activities.NativeActivity> based activities.</span></span>  
  
 [<span data-ttu-id="0995e-120">Deklarativní omezení</span><span class="sxs-lookup"><span data-stu-id="0995e-120">Declarative Constraints</span></span>](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md)  
 <span data-ttu-id="0995e-121">Popisuje, jak používat deklarativní omezení pro ověřování komplexní aktivity.</span><span class="sxs-lookup"><span data-stu-id="0995e-121">Describes how to use declarative constraints to provide complex activity validation.</span></span>  
  
 [<span data-ttu-id="0995e-122">Vyvolání ověřování aktivit</span><span class="sxs-lookup"><span data-stu-id="0995e-122">Invoking Activity Validation</span></span>](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md)  
 <span data-ttu-id="0995e-123">Popisuje při ověření aktivity se automaticky vyvolá a explicitně vyvolat ověřování.</span><span class="sxs-lookup"><span data-stu-id="0995e-123">Discusses when activity validation is invoked automatically and how to explicitly invoke validation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0995e-124">Odkaz</span><span class="sxs-lookup"><span data-stu-id="0995e-124">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0995e-125">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="0995e-125">Related Sections</span></span>
