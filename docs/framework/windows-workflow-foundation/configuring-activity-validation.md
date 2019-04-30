---
title: Konfigurace ověřování aktivit
ms.date: 03/30/2017
ms.assetid: 25a4eccb-b8fc-4857-a01d-2683b6341219
ms.openlocfilehash: 65928de1dc8b8d9914648463a136790c7978f53c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774171"
---
# <a name="configuring-activity-validation"></a><span data-ttu-id="91edb-102">Konfigurace ověřování aktivit</span><span class="sxs-lookup"><span data-stu-id="91edb-102">Configuring Activity Validation</span></span>
<span data-ttu-id="91edb-103">Aktivita ověření umožňuje uživatelům a autoři aktivity k identifikaci a hlášení chyb v konfiguraci aktivity před jeho provedením.</span><span class="sxs-lookup"><span data-stu-id="91edb-103">Activity validation enables activity authors and users to identify and report errors in an activity’s configuration prior to its execution.</span></span> <span data-ttu-id="91edb-104">Windows Workflow Foundation (WF) obsahuje následující tři typy ověřování aktivit:</span><span class="sxs-lookup"><span data-stu-id="91edb-104">Windows Workflow Foundation (WF) provides the following three types of activity validation:</span></span>  
  
- <span data-ttu-id="91edb-105">`RequiredArgument` a `OverloadGroup` atributy.</span><span class="sxs-lookup"><span data-stu-id="91edb-105">`RequiredArgument` and `OverloadGroup` attributes.</span></span>  
  
- <span data-ttu-id="91edb-106">Imperativní ověřování na základě kódu.</span><span class="sxs-lookup"><span data-stu-id="91edb-106">Imperative code-based validation.</span></span>  
  
- <span data-ttu-id="91edb-107">Deklarativní omezení.</span><span class="sxs-lookup"><span data-stu-id="91edb-107">Declarative constraints.</span></span>  
  
 <span data-ttu-id="91edb-108">`RequiredArgument` a `OverloadGroup` atributy označuje, že některé argumenty pro aktivitu je povinný.</span><span class="sxs-lookup"><span data-stu-id="91edb-108">`RequiredArgument` and `OverloadGroup` attributes indicate that certain arguments on an activity are required.</span></span> <span data-ttu-id="91edb-109">Imperativní ověřování na základě kódu poskytuje jednoduchý způsob pro aktivitu pro ověřování o sobě a deklarativní omezení povolit ověřování aktivity a je naznačen vztah se obsažený pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="91edb-109">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and declarative constraints enable validation about the activity and its relationship with the containing workflow.</span></span> <span data-ttu-id="91edb-110">Pokud aktivita není správně nakonfigurována podle požadavků na ověření, chyby a upozornění ověření jsou vráceny.</span><span class="sxs-lookup"><span data-stu-id="91edb-110">If an activity is not configured properly according to the validation requirements, validation errors and warnings are returned.</span></span> <span data-ttu-id="91edb-111">Pokud obsažený pracovní postup je vytvořen pomocí návrháře postupu provádění, žádné chyby ověření a upozornění se zobrazí v návrháři.</span><span class="sxs-lookup"><span data-stu-id="91edb-111">If the containing workflow is created using the workflow designer, any validation errors and warnings are displayed in the designer.</span></span> <span data-ttu-id="91edb-112">Pokud je pracovní postup vytvořený mimo návrháře postupu provádění všechny chyby ověření jsou vráceny při vyvolání pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="91edb-112">If the workflow is created outside of the workflow designer any validation errors are returned when the workflow is invoked.</span></span> <span data-ttu-id="91edb-113">Bez ohledu na to, jak sled prací byl vytvořen pracovní postup s chyby ověření nikdy povoleno provádět.</span><span class="sxs-lookup"><span data-stu-id="91edb-113">Regardless of how the workflow was created, a workflow with validation errors is never allowed to execute.</span></span> <span data-ttu-id="91edb-114">Tato část obsahuje přehled těchto typů ověřování aktivit a jak vyvolání ověřování aktivit.</span><span class="sxs-lookup"><span data-stu-id="91edb-114">This section provides an overview of these types of activity validation and how activity validation is invoked.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="91edb-115">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="91edb-115">In This Section</span></span>  
 [<span data-ttu-id="91edb-116">Povinné argumenty a skupiny přetížení</span><span class="sxs-lookup"><span data-stu-id="91edb-116">Required Arguments and Overload Groups</span></span>](required-arguments-and-overload-groups.md)  
 <span data-ttu-id="91edb-117">Popisuje způsob použití `RequiredArgument` a `OverloadGroup` atributy pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="91edb-117">Describes how to use the `RequiredArgument` and `OverloadGroup` attributes to provide validation.</span></span>  
  
 [<span data-ttu-id="91edb-118">Ověřování na základě imperativního kódu</span><span class="sxs-lookup"><span data-stu-id="91edb-118">Imperative Code-Based Validation</span></span>](imperative-code-based-validation.md)  
 <span data-ttu-id="91edb-119">Popisuje způsob použití ověřování na základě kódu pro <xref:System.Activities.CodeActivity> a <xref:System.Activities.NativeActivity> podle aktivity.</span><span class="sxs-lookup"><span data-stu-id="91edb-119">Describes how to use code-based validation for <xref:System.Activities.CodeActivity> and <xref:System.Activities.NativeActivity> based activities.</span></span>  
  
 [<span data-ttu-id="91edb-120">Deklarativní omezení</span><span class="sxs-lookup"><span data-stu-id="91edb-120">Declarative Constraints</span></span>](declarative-constraints.md)  
 <span data-ttu-id="91edb-121">Popisuje způsob použití deklarativní omezení pro ověřování komplexní aktivity.</span><span class="sxs-lookup"><span data-stu-id="91edb-121">Describes how to use declarative constraints to provide complex activity validation.</span></span>  
  
 [<span data-ttu-id="91edb-122">Vyvolání ověřování aktivit</span><span class="sxs-lookup"><span data-stu-id="91edb-122">Invoking Activity Validation</span></span>](invoking-activity-validation.md)  
 <span data-ttu-id="91edb-123">Tento článek popisuje při ověřování aktivit je vyvolán automaticky a jak explicitně volat ověření.</span><span class="sxs-lookup"><span data-stu-id="91edb-123">Discusses when activity validation is invoked automatically and how to explicitly invoke validation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="91edb-124">Odkaz</span><span class="sxs-lookup"><span data-stu-id="91edb-124">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="91edb-125">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="91edb-125">Related Sections</span></span>
