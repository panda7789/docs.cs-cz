---
title: '&lt;bufferReceive&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e0fc3fb901e0f70b616f403b98abc7b9645b2b44
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltbufferreceivegt"></a><span data-ttu-id="c8146-102">&lt;bufferReceive&gt;</span><span class="sxs-lookup"><span data-stu-id="c8146-102">&lt;bufferReceive&gt;</span></span>
<span data-ttu-id="c8146-103">Zpracování, která umožňuje služba pracovního postupu ke zpracování zpráv mimo pořadí příjmu chování služby, který povoluje službu, chcete-li použít do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="c8146-103">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="c8146-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c8146-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c8146-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="c8146-105">\<behaviors></span></span>  
<span data-ttu-id="c8146-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="c8146-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="c8146-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="c8146-107">\<behavior></span></span>  
<span data-ttu-id="c8146-108">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="c8146-108">\<bufferReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8146-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8146-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c8146-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c8146-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c8146-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c8146-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c8146-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="c8146-112">Attributes</span></span>  
  
|<span data-ttu-id="c8146-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="c8146-113">Attribute</span></span>|<span data-ttu-id="c8146-114">Popis</span><span class="sxs-lookup"><span data-stu-id="c8146-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c8146-115">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="c8146-115">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="c8146-116">Celé číslo, která určuje maximální počet čekajících na zpracování počet zpráv povolených pro každý kanál.</span><span class="sxs-lookup"><span data-stu-id="c8146-116">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="c8146-117">Výchozí hodnota je 512.</span><span class="sxs-lookup"><span data-stu-id="c8146-117">The default value is 512.</span></span> <span data-ttu-id="c8146-118">Tato vlastnost omezuje počet zpráv mimo pořadí, které lze přijímat pomocí služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c8146-118">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c8146-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c8146-119">Child Elements</span></span>  
 <span data-ttu-id="c8146-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="c8146-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c8146-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c8146-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c8146-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="c8146-122">Element</span></span>|<span data-ttu-id="c8146-123">Popis</span><span class="sxs-lookup"><span data-stu-id="c8146-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c8146-124">\<chování > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="c8146-124">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="c8146-125">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="c8146-125">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c8146-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="c8146-126">See Also</span></span>  
<!-- <xref:System.ServiceModel.Activities.Description.BufferReceiveServiceBehavior>  -->
 <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
