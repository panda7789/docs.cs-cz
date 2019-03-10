---
title: Navrhování a implementace vlastních aktivit
ms.date: 03/30/2017
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
ms.openlocfilehash: 61a5de5a15835c728c18c0136952cf7ffdbaf000
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57706400"
---
# <a name="designing-and-implementing-custom-activities"></a><span data-ttu-id="d94f0-102">Navrhování a implementace vlastních aktivit</span><span class="sxs-lookup"><span data-stu-id="d94f0-102">Designing and Implementing Custom Activities</span></span>
<span data-ttu-id="d94f0-103">Vlastní aktivity v [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] se vytvoří buď kompletaci poskytované systémem aktivit do složených aktivit nebo vytvoření nových typů, které jsou odvozeny z <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, nebo <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="d94f0-103">Custom activities in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] are created by either assembling system-provided activities into composite activities or by creating new types that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, or <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="d94f0-104">Tato část popisuje, jak vytvořit vlastní aktivity pomocí některé z metod.</span><span class="sxs-lookup"><span data-stu-id="d94f0-104">This section describes how to create custom activities with either method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d94f0-105">Vlastní aktivity ve výchozím nastavení se zobrazí v Návrháři pracovních postupů jako jednoduchý obdélník s názvem aktivity.</span><span class="sxs-lookup"><span data-stu-id="d94f0-105">Custom activities by default display within the workflow designer as a simple rectangle with the activity’s name.</span></span> <span data-ttu-id="d94f0-106">Poskytnout vlastní vizuální znázornění vaše aktivity v pracovním postupu návrháře musíte také vytvořit vlastní návrháře.</span><span class="sxs-lookup"><span data-stu-id="d94f0-106">To provide a custom visual representation of your activity in the workflow designer you must also create a custom designer.</span></span> <span data-ttu-id="d94f0-107">Další informace najdete v tématu [použití vlastních návrhářů a šablon aktivity](using-custom-activity-designers-and-templates.md).</span><span class="sxs-lookup"><span data-stu-id="d94f0-107">For more information, see [Using Custom Activity Designers and Templates](using-custom-activity-designers-and-templates.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d94f0-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d94f0-108">In This Section</span></span>  
 [<span data-ttu-id="d94f0-109">Možnosti při vytváření aktivit</span><span class="sxs-lookup"><span data-stu-id="d94f0-109">Activity Authoring Options</span></span>](activity-authoring-options-in-wf.md)  
 <span data-ttu-id="d94f0-110">Tento článek popisuje vytváření styly k dispozici v [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d94f0-110">Discusses the authoring styles available in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="d94f0-111">Použití vlastní aktivity</span><span class="sxs-lookup"><span data-stu-id="d94f0-111">Using a custom activity</span></span>](using-a-custom-activity.md)  
 <span data-ttu-id="d94f0-112">Popisuje, jak přidat vlastní aktivity do projektu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="d94f0-112">Describes how to add a custom activity to a workflow project.</span></span>  
  
  [<span data-ttu-id="d94f0-113">Vytváření asynchronních aktivit</span><span class="sxs-lookup"><span data-stu-id="d94f0-113">Creating Asynchronous Activities</span></span>](creating-asynchronous-activities-in-wf.md)  
 <span data-ttu-id="d94f0-114">Popisuje, jak vytvořit asynchronní aktivity.</span><span class="sxs-lookup"><span data-stu-id="d94f0-114">Describes how to create asynchronous activities.</span></span>  
  
 [<span data-ttu-id="d94f0-115">Konfigurace ověřování aktivit</span><span class="sxs-lookup"><span data-stu-id="d94f0-115">Configuring Activity Validation</span></span>](configuring-activity-validation.md)  
 <span data-ttu-id="d94f0-116">Popisuje, jak ověřování aktivit slouží k identifikaci a oznamovat chyby v konfiguraci aktivity před jeho provedením.</span><span class="sxs-lookup"><span data-stu-id="d94f0-116">Describes how activity validation can be used to identify and report errors in an activity’s configuration prior to its execution.</span></span>  
  
 [<span data-ttu-id="d94f0-117">Vytvoření aktivity za běhu</span><span class="sxs-lookup"><span data-stu-id="d94f0-117">Creating an Activity at Runtime</span></span>](creating-an-activity-at-runtime-with-dynamicactivity.md)  
 <span data-ttu-id="d94f0-118">Popisuje způsob vytváření aktivit v modulu runtime pomocí <xref:System.Activities.DynamicActivity>.</span><span class="sxs-lookup"><span data-stu-id="d94f0-118">Discusses how to create activities at runtime using <xref:System.Activities.DynamicActivity>.</span></span>  
  
 [<span data-ttu-id="d94f0-119">Vlastnosti spuštění pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="d94f0-119">Workflow Execution Properties</span></span>](workflow-execution-properties.md)  
 <span data-ttu-id="d94f0-120">Popisuje, jak pomocí vlastnosti spuštění pracovního postupu můžete přidat do prostředí aktivity specifické vlastnosti kontextu</span><span class="sxs-lookup"><span data-stu-id="d94f0-120">Describes how to use workflow execution properties to add context specific properties to an activity’s environment</span></span>  
  
 [<span data-ttu-id="d94f0-121">Používání delegátů aktivit</span><span class="sxs-lookup"><span data-stu-id="d94f0-121">Using Activity Delegates</span></span>](using-activity-delegates.md)  
 <span data-ttu-id="d94f0-122">Popisuje, jak vytvářet a používat aktivity, které obsahují delegátů aktivit.</span><span class="sxs-lookup"><span data-stu-id="d94f0-122">Discusses how to author and use activities that contain activity delegates.</span></span>
  
 [<span data-ttu-id="d94f0-123">Používání rozšíření aktivit</span><span class="sxs-lookup"><span data-stu-id="d94f0-123">Using Activity Extensions</span></span>](using-activity-extensions.md)  
 <span data-ttu-id="d94f0-124">Popisuje způsob vytváření a používání rozšíření aktivit.</span><span class="sxs-lookup"><span data-stu-id="d94f0-124">Describes how to author and use activity extensions.</span></span>  
  
 [<span data-ttu-id="d94f0-125">Využití informačních kanálů OData z pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="d94f0-125">Consuming OData Feeds from a Workflow</span></span>](consuming-odata-feeds-from-a-workflow.md)  
 <span data-ttu-id="d94f0-126">Popisuje několik metod pro volání datové služby WCF z pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="d94f0-126">Describes several methods for calling a WCF Data Service from a workflow.</span></span>  
  
 [<span data-ttu-id="d94f0-127">Určení oboru a viditelnosti definice aktivity</span><span class="sxs-lookup"><span data-stu-id="d94f0-127">Activity Definition Scoping and Visibility</span></span>](activity-definition-scoping-and-visibility.md)  
 <span data-ttu-id="d94f0-128">Popisuje možnosti a pravidla pro definování dat určení oboru a člen viditelnost pro aktivity.</span><span class="sxs-lookup"><span data-stu-id="d94f0-128">Describes the options and rules for defining data scoping and member visibility for activities.</span></span>
