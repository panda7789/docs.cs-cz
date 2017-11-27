---
title: "Navrhování a implementace vlastních aktivit"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
caps.latest.revision: "22"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f9243761803bc8b68ce37b3d3ad310e8bb7f93d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="designing-and-implementing-custom-activities"></a><span data-ttu-id="26de1-102">Navrhování a implementace vlastních aktivit</span><span class="sxs-lookup"><span data-stu-id="26de1-102">Designing and Implementing Custom Activities</span></span>
<span data-ttu-id="26de1-103">Vlastní aktivity v [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] vytvářejí buď odlišnými poskytované systémem aktivit do složených aktivity nebo vytvoření nových typů, které jsou odvozeny od <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, nebo <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="26de1-103">Custom activities in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] are created by either assembling system-provided activities into composite activities or by creating new types that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, or <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="26de1-104">Tato část popisuje, jak vytvořit vlastní aktivity pomocí některé z metod.</span><span class="sxs-lookup"><span data-stu-id="26de1-104">This section describes how to create custom activities with either method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="26de1-105">Vlastní aktivity ve výchozím nastavení zobrazí jako jednoduchý obdélníku s názvem aktivity v Návrháři pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="26de1-105">Custom activities by default display within the workflow designer as a simple rectangle with the activity’s name.</span></span> <span data-ttu-id="26de1-106">Poskytnout vlastní vizuální reprezentace aktivity v pracovním postupu návrháře je nutné také vytvořit vlastní návrháře.</span><span class="sxs-lookup"><span data-stu-id="26de1-106">To provide a custom visual representation of your activity in the workflow designer you must also create a custom designer.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="26de1-107">[Pomocí Návrháře vlastních aktivit a šablony](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md).</span><span class="sxs-lookup"><span data-stu-id="26de1-107"> [Using Custom Activity Designers and Templates](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="26de1-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="26de1-108">In This Section</span></span>  
 [<span data-ttu-id="26de1-109">Možnosti pro tvorbu aktivity</span><span class="sxs-lookup"><span data-stu-id="26de1-109">Activity Authoring Options</span></span>](../../../docs/framework/windows-workflow-foundation/activity-authoring-options-in-wf.md)  
 <span data-ttu-id="26de1-110">Popisuje vytváření stylů, které jsou k dispozici v [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="26de1-110">Discusses the authoring styles available in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="26de1-111">Pomocí vlastních aktivit</span><span class="sxs-lookup"><span data-stu-id="26de1-111">Using a custom activity</span></span>](../../../docs/framework/windows-workflow-foundation/using-a-custom-activity.md)  
 <span data-ttu-id="26de1-112">Popisuje, jak přidat vlastní aktivity pracovního postupu projektu.</span><span class="sxs-lookup"><span data-stu-id="26de1-112">Describes how to add a custom activity to a workflow project.</span></span>  
  
  [<span data-ttu-id="26de1-113">Vytváření asynchronních aktivit</span><span class="sxs-lookup"><span data-stu-id="26de1-113">Creating Asynchronous Activities</span></span>](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md)  
 <span data-ttu-id="26de1-114">Popisuje, jak vytvořit asynchronní aktivity.</span><span class="sxs-lookup"><span data-stu-id="26de1-114">Describes how to create asynchronous activities.</span></span>  
  
 [<span data-ttu-id="26de1-115">Konfigurace ověření aktivity</span><span class="sxs-lookup"><span data-stu-id="26de1-115">Configuring Activity Validation</span></span>](../../../docs/framework/windows-workflow-foundation/configuring-activity-validation.md)  
 <span data-ttu-id="26de1-116">Popisuje, jak aktivita ověřování lze použít k identifikaci a nahlášení chyb v konfiguraci aktivity před jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="26de1-116">Describes how activity validation can be used to identify and report errors in an activity’s configuration prior to its execution.</span></span>  
  
 [<span data-ttu-id="26de1-117">Vytvoření aktivity za běhu</span><span class="sxs-lookup"><span data-stu-id="26de1-117">Creating an Activity at Runtime</span></span>](../../../docs/framework/windows-workflow-foundation/creating-an-activity-at-runtime-with-dynamicactivity.md)  
 <span data-ttu-id="26de1-118">Popisuje, jak vytvořit aktivit v modulu runtime pomocí <xref:System.Activities.DynamicActivity>.</span><span class="sxs-lookup"><span data-stu-id="26de1-118">Discusses how to create activities at runtime using <xref:System.Activities.DynamicActivity>.</span></span>  
  
 [<span data-ttu-id="26de1-119">Vlastnosti pracovního postupu provádění</span><span class="sxs-lookup"><span data-stu-id="26de1-119">Workflow Execution Properties</span></span>](../../../docs/framework/windows-workflow-foundation/workflow-execution-properties.md)  
 <span data-ttu-id="26de1-120">Popisuje, jak pomocí vlastnosti spuštění pracovního postupu můžete přidat do prostředí aktivity konkrétních vlastností kontextu</span><span class="sxs-lookup"><span data-stu-id="26de1-120">Describes how to use workflow execution properties to add context specific properties to an activity’s environment</span></span>  
  
 [<span data-ttu-id="26de1-121">Použití delegátů aktivity</span><span class="sxs-lookup"><span data-stu-id="26de1-121">Using Activity Delegates</span></span>](../../../docs/framework/windows-workflow-foundation/using-activity-delegates.md)  
 <span data-ttu-id="26de1-122">Popisuje postup vytváření a používání aktivit, které obsahují aktivitu delegáti.</span><span class="sxs-lookup"><span data-stu-id="26de1-122">Discusses how to author and use activities that contain activity delegates.</span></span>  
  
 [<span data-ttu-id="26de1-123">Lokalizace aktivity</span><span class="sxs-lookup"><span data-stu-id="26de1-123">Activity Localization</span></span>](../../../docs/framework/windows-workflow-foundation/activity-localization.md)  
 <span data-ttu-id="26de1-124">Popisuje způsob použití lokalizace řetězcové prostředky v aktivitách.</span><span class="sxs-lookup"><span data-stu-id="26de1-124">Describes how to use localization of string resources in activities.</span></span>  
  
 [<span data-ttu-id="26de1-125">Pomocí rozšíření aktivity</span><span class="sxs-lookup"><span data-stu-id="26de1-125">Using Activity Extensions</span></span>](../../../docs/framework/windows-workflow-foundation/using-activity-extensions.md)  
 <span data-ttu-id="26de1-126">Popisuje postup vytváření a používání rozšíření aktivity.</span><span class="sxs-lookup"><span data-stu-id="26de1-126">Describes how to author and use activity extensions.</span></span>  
  
 [<span data-ttu-id="26de1-127">Využívání OData informační kanály z pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="26de1-127">Consuming OData Feeds from a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/consuming-odata-feeds-from-a-workflow.md)  
 <span data-ttu-id="26de1-128">Popisuje několik metod pro volání služby WCF Data Service z pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="26de1-128">Describes several methods for calling a WCF Data Service from a workflow.</span></span>  
  
 [<span data-ttu-id="26de1-129">Nastavení oboru definici aktivity a viditelnost</span><span class="sxs-lookup"><span data-stu-id="26de1-129">Activity Definition Scoping and Visibility</span></span>](../../../docs/framework/windows-workflow-foundation/activity-definition-scoping-and-visibility.md)  
 <span data-ttu-id="26de1-130">Popisuje možnosti a pravidla pro definování dat rozsahu a člen viditelnost pro aktivity.</span><span class="sxs-lookup"><span data-stu-id="26de1-130">Describes the options and rules for defining data scoping and member visibility for activities.</span></span>
