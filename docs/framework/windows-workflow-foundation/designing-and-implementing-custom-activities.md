---
title: Návrh a implementace vlastních aktivit
description: Tento článek poskytuje prostředky pro vytváření vlastních aktivit v nástroji Workflow Foundation vytvořením složených aktivit nebo vytvářením nových typů aktivit.
ms.date: 03/30/2017
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
ms.openlocfilehash: 9c184bff9518bb5581f3bf4cd408db224736192b
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419990"
---
# <a name="designing-and-implementing-custom-activities"></a><span data-ttu-id="36564-103">Návrh a implementace vlastních aktivit</span><span class="sxs-lookup"><span data-stu-id="36564-103">Designing and Implementing Custom Activities</span></span>
<span data-ttu-id="36564-104">Vlastní aktivity v [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] nástroji jsou vytvářeny buď prostřednictvím sestavování systémových aktivit, do složených aktivit, nebo vytvořením nových typů, které jsou odvozeny z <xref:System.Activities.CodeActivity> , <xref:System.Activities.AsyncCodeActivity> nebo <xref:System.Activities.NativeActivity> .</span><span class="sxs-lookup"><span data-stu-id="36564-104">Custom activities in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] are created by either assembling system-provided activities into composite activities or by creating new types that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, or <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="36564-105">Tato část popisuje, jak vytvořit vlastní aktivity pomocí obou metod.</span><span class="sxs-lookup"><span data-stu-id="36564-105">This section describes how to create custom activities with either method.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="36564-106">Vlastní aktivity ve výchozím nastavení se zobrazují v Návrháři pracovních postupů jako jednoduchý obdélník s názvem aktivity.</span><span class="sxs-lookup"><span data-stu-id="36564-106">Custom activities by default display within the workflow designer as a simple rectangle with the activity’s name.</span></span> <span data-ttu-id="36564-107">K poskytnutí vlastní vizuální reprezentace vaší aktivity v Návrháři pracovních postupů musíte také vytvořit vlastního návrháře.</span><span class="sxs-lookup"><span data-stu-id="36564-107">To provide a custom visual representation of your activity in the workflow designer you must also create a custom designer.</span></span> <span data-ttu-id="36564-108">Další informace najdete v tématu [použití vlastních návrhářů aktivit a šablon](using-custom-activity-designers-and-templates.md).</span><span class="sxs-lookup"><span data-stu-id="36564-108">For more information, see [Using Custom Activity Designers and Templates](using-custom-activity-designers-and-templates.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="36564-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="36564-109">In This Section</span></span>  
 [<span data-ttu-id="36564-110">Možnosti při vytváření aktivit</span><span class="sxs-lookup"><span data-stu-id="36564-110">Activity Authoring Options</span></span>](activity-authoring-options-in-wf.md)  
 <span data-ttu-id="36564-111">Popisuje styly vytváření dostupné v nástroji [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="36564-111">Discusses the authoring styles available in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="36564-112">Použití vlastní aktivity</span><span class="sxs-lookup"><span data-stu-id="36564-112">Using a custom activity</span></span>](using-a-custom-activity.md)  
 <span data-ttu-id="36564-113">Popisuje, jak přidat vlastní aktivitu do projektu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="36564-113">Describes how to add a custom activity to a workflow project.</span></span>  
  
  [<span data-ttu-id="36564-114">Vytváření asynchronních aktivit</span><span class="sxs-lookup"><span data-stu-id="36564-114">Creating Asynchronous Activities</span></span>](creating-asynchronous-activities-in-wf.md)  
 <span data-ttu-id="36564-115">Popisuje, jak vytvořit asynchronní aktivity.</span><span class="sxs-lookup"><span data-stu-id="36564-115">Describes how to create asynchronous activities.</span></span>  
  
 [<span data-ttu-id="36564-116">Konfigurace ověřování aktivit</span><span class="sxs-lookup"><span data-stu-id="36564-116">Configuring Activity Validation</span></span>](configuring-activity-validation.md)  
 <span data-ttu-id="36564-117">Popisuje, jak lze pomocí ověření aktivity identifikovat a ohlásit chyby v konfiguraci aktivity před jejím spuštěním.</span><span class="sxs-lookup"><span data-stu-id="36564-117">Describes how activity validation can be used to identify and report errors in an activity’s configuration prior to its execution.</span></span>  
  
 [<span data-ttu-id="36564-118">Vytvoření aktivity za běhu</span><span class="sxs-lookup"><span data-stu-id="36564-118">Creating an Activity at Runtime</span></span>](creating-an-activity-at-runtime-with-dynamicactivity.md)  
 <span data-ttu-id="36564-119">Popisuje, jak vytvářet aktivity za běhu pomocí <xref:System.Activities.DynamicActivity> .</span><span class="sxs-lookup"><span data-stu-id="36564-119">Discusses how to create activities at runtime using <xref:System.Activities.DynamicActivity>.</span></span>  
  
 [<span data-ttu-id="36564-120">Vlastnosti spuštění pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="36564-120">Workflow Execution Properties</span></span>](workflow-execution-properties.md)  
 <span data-ttu-id="36564-121">Popisuje použití vlastností spuštění pracovního postupu k přidání specifických vlastností kontextu do prostředí aktivity.</span><span class="sxs-lookup"><span data-stu-id="36564-121">Describes how to use workflow execution properties to add context specific properties to an activity’s environment</span></span>  
  
 [<span data-ttu-id="36564-122">Používání delegátů aktivit</span><span class="sxs-lookup"><span data-stu-id="36564-122">Using Activity Delegates</span></span>](using-activity-delegates.md)  
 <span data-ttu-id="36564-123">Popisuje, jak vytvářet a používat aktivity, které obsahují delegáty aktivit.</span><span class="sxs-lookup"><span data-stu-id="36564-123">Discusses how to author and use activities that contain activity delegates.</span></span>
  
 [<span data-ttu-id="36564-124">Používání rozšíření aktivit</span><span class="sxs-lookup"><span data-stu-id="36564-124">Using Activity Extensions</span></span>](using-activity-extensions.md)  
 <span data-ttu-id="36564-125">Popisuje, jak vytvářet a používat rozšíření aktivit.</span><span class="sxs-lookup"><span data-stu-id="36564-125">Describes how to author and use activity extensions.</span></span>  
  
 [<span data-ttu-id="36564-126">Využití informačních kanálů OData z pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="36564-126">Consuming OData Feeds from a Workflow</span></span>](consuming-odata-feeds-from-a-workflow.md)  
 <span data-ttu-id="36564-127">Popisuje několik metod pro volání datové služby WCF z pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="36564-127">Describes several methods for calling a WCF Data Service from a workflow.</span></span>  
  
 [<span data-ttu-id="36564-128">Určení oboru a viditelnosti definice aktivity</span><span class="sxs-lookup"><span data-stu-id="36564-128">Activity Definition Scoping and Visibility</span></span>](activity-definition-scoping-and-visibility.md)  
 <span data-ttu-id="36564-129">Popisuje možnosti a pravidla pro definování oboru dat a viditelnosti členů pro aktivity.</span><span class="sxs-lookup"><span data-stu-id="36564-129">Describes the options and rules for defining data scoping and member visibility for activities.</span></span>
