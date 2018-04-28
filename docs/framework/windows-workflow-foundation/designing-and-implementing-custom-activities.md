---
title: Navrhování a implementace vlastních aktivit
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bafa54764ba8b02dd05cadd65c3f3cbc64c4b081
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="designing-and-implementing-custom-activities"></a><span data-ttu-id="6deb9-102">Navrhování a implementace vlastních aktivit</span><span class="sxs-lookup"><span data-stu-id="6deb9-102">Designing and Implementing Custom Activities</span></span>
<span data-ttu-id="6deb9-103">Vlastní aktivity v [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] vytvářejí buď odlišnými poskytované systémem aktivit do složených aktivity nebo vytvoření nových typů, které jsou odvozeny od <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, nebo <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="6deb9-103">Custom activities in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] are created by either assembling system-provided activities into composite activities or by creating new types that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, or <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="6deb9-104">Tato část popisuje, jak vytvořit vlastní aktivity pomocí některé z metod.</span><span class="sxs-lookup"><span data-stu-id="6deb9-104">This section describes how to create custom activities with either method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6deb9-105">Vlastní aktivity ve výchozím nastavení zobrazí jako jednoduchý obdélníku s názvem aktivity v Návrháři pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="6deb9-105">Custom activities by default display within the workflow designer as a simple rectangle with the activity’s name.</span></span> <span data-ttu-id="6deb9-106">Poskytnout vlastní vizuální reprezentace aktivity v pracovním postupu návrháře je nutné také vytvořit vlastní návrháře.</span><span class="sxs-lookup"><span data-stu-id="6deb9-106">To provide a custom visual representation of your activity in the workflow designer you must also create a custom designer.</span></span> <span data-ttu-id="6deb9-107">Další informace najdete v tématu [pomocí Návrháře vlastních aktivit a šablony](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md).</span><span class="sxs-lookup"><span data-stu-id="6deb9-107">For more information, see [Using Custom Activity Designers and Templates](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6deb9-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6deb9-108">In This Section</span></span>  
 [<span data-ttu-id="6deb9-109">Možnosti při vytváření aktivit</span><span class="sxs-lookup"><span data-stu-id="6deb9-109">Activity Authoring Options</span></span>](../../../docs/framework/windows-workflow-foundation/activity-authoring-options-in-wf.md)  
 <span data-ttu-id="6deb9-110">Popisuje vytváření stylů, které jsou k dispozici v [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6deb9-110">Discusses the authoring styles available in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="6deb9-111">Použití vlastní aktivity</span><span class="sxs-lookup"><span data-stu-id="6deb9-111">Using a custom activity</span></span>](../../../docs/framework/windows-workflow-foundation/using-a-custom-activity.md)  
 <span data-ttu-id="6deb9-112">Popisuje, jak přidat vlastní aktivity pracovního postupu projektu.</span><span class="sxs-lookup"><span data-stu-id="6deb9-112">Describes how to add a custom activity to a workflow project.</span></span>  
  
  [<span data-ttu-id="6deb9-113">Vytváření asynchronních aktivit</span><span class="sxs-lookup"><span data-stu-id="6deb9-113">Creating Asynchronous Activities</span></span>](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md)  
 <span data-ttu-id="6deb9-114">Popisuje, jak vytvořit asynchronní aktivity.</span><span class="sxs-lookup"><span data-stu-id="6deb9-114">Describes how to create asynchronous activities.</span></span>  
  
 [<span data-ttu-id="6deb9-115">Konfigurace ověřování aktivit</span><span class="sxs-lookup"><span data-stu-id="6deb9-115">Configuring Activity Validation</span></span>](../../../docs/framework/windows-workflow-foundation/configuring-activity-validation.md)  
 <span data-ttu-id="6deb9-116">Popisuje, jak aktivita ověřování lze použít k identifikaci a nahlášení chyb v konfiguraci aktivity před jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="6deb9-116">Describes how activity validation can be used to identify and report errors in an activity’s configuration prior to its execution.</span></span>  
  
 [<span data-ttu-id="6deb9-117">Vytvoření aktivity za běhu</span><span class="sxs-lookup"><span data-stu-id="6deb9-117">Creating an Activity at Runtime</span></span>](../../../docs/framework/windows-workflow-foundation/creating-an-activity-at-runtime-with-dynamicactivity.md)  
 <span data-ttu-id="6deb9-118">Popisuje, jak vytvořit aktivit v modulu runtime pomocí <xref:System.Activities.DynamicActivity>.</span><span class="sxs-lookup"><span data-stu-id="6deb9-118">Discusses how to create activities at runtime using <xref:System.Activities.DynamicActivity>.</span></span>  
  
 [<span data-ttu-id="6deb9-119">Vlastnosti spuštění pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6deb9-119">Workflow Execution Properties</span></span>](../../../docs/framework/windows-workflow-foundation/workflow-execution-properties.md)  
 <span data-ttu-id="6deb9-120">Popisuje, jak pomocí vlastnosti spuštění pracovního postupu můžete přidat do prostředí aktivity konkrétních vlastností kontextu</span><span class="sxs-lookup"><span data-stu-id="6deb9-120">Describes how to use workflow execution properties to add context specific properties to an activity’s environment</span></span>  
  
 [<span data-ttu-id="6deb9-121">Používání delegátů aktivit</span><span class="sxs-lookup"><span data-stu-id="6deb9-121">Using Activity Delegates</span></span>](../../../docs/framework/windows-workflow-foundation/using-activity-delegates.md)  
 <span data-ttu-id="6deb9-122">Popisuje postup vytváření a používání aktivit, které obsahují aktivitu delegáti.</span><span class="sxs-lookup"><span data-stu-id="6deb9-122">Discusses how to author and use activities that contain activity delegates.</span></span>  
  
 [<span data-ttu-id="6deb9-123">Lokalizace aktivity</span><span class="sxs-lookup"><span data-stu-id="6deb9-123">Activity Localization</span></span>](../../../docs/framework/windows-workflow-foundation/activity-localization.md)  
 <span data-ttu-id="6deb9-124">Popisuje způsob použití lokalizace řetězcové prostředky v aktivitách.</span><span class="sxs-lookup"><span data-stu-id="6deb9-124">Describes how to use localization of string resources in activities.</span></span>  
  
 [<span data-ttu-id="6deb9-125">Používání rozšíření aktivit</span><span class="sxs-lookup"><span data-stu-id="6deb9-125">Using Activity Extensions</span></span>](../../../docs/framework/windows-workflow-foundation/using-activity-extensions.md)  
 <span data-ttu-id="6deb9-126">Popisuje postup vytváření a používání rozšíření aktivity.</span><span class="sxs-lookup"><span data-stu-id="6deb9-126">Describes how to author and use activity extensions.</span></span>  
  
 [<span data-ttu-id="6deb9-127">Využití informačních kanálů OData z pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6deb9-127">Consuming OData Feeds from a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/consuming-odata-feeds-from-a-workflow.md)  
 <span data-ttu-id="6deb9-128">Popisuje několik metod pro volání služby WCF Data Service z pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6deb9-128">Describes several methods for calling a WCF Data Service from a workflow.</span></span>  
  
 [<span data-ttu-id="6deb9-129">Určení oboru a viditelnosti definice aktivity</span><span class="sxs-lookup"><span data-stu-id="6deb9-129">Activity Definition Scoping and Visibility</span></span>](../../../docs/framework/windows-workflow-foundation/activity-definition-scoping-and-visibility.md)  
 <span data-ttu-id="6deb9-130">Popisuje možnosti a pravidla pro definování dat rozsahu a člen viditelnost pro aktivity.</span><span class="sxs-lookup"><span data-stu-id="6deb9-130">Describes the options and rules for defining data scoping and member visibility for activities.</span></span>
