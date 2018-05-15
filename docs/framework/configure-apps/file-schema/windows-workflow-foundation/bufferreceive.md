---
title: '&lt;bufferReceive&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: 07d5b66b14d9495808f972734cdce4476efaefde
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltbufferreceivegt"></a><span data-ttu-id="7d41e-102">&lt;bufferReceive&gt;</span><span class="sxs-lookup"><span data-stu-id="7d41e-102">&lt;bufferReceive&gt;</span></span>
<span data-ttu-id="7d41e-103">Zpracování, která umožňuje služba pracovního postupu ke zpracování zpráv mimo pořadí příjmu chování služby, který povoluje službu, chcete-li použít do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7d41e-103">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="7d41e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7d41e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7d41e-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="7d41e-105">\<behaviors></span></span>  
<span data-ttu-id="7d41e-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7d41e-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="7d41e-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="7d41e-107">\<behavior></span></span>  
<span data-ttu-id="7d41e-108">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="7d41e-108">\<bufferReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d41e-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d41e-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d41e-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7d41e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7d41e-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7d41e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d41e-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="7d41e-112">Attributes</span></span>  
  
|<span data-ttu-id="7d41e-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="7d41e-113">Attribute</span></span>|<span data-ttu-id="7d41e-114">Popis</span><span class="sxs-lookup"><span data-stu-id="7d41e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7d41e-115">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="7d41e-115">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="7d41e-116">Celé číslo, která určuje maximální počet čekajících na zpracování počet zpráv povolených pro každý kanál.</span><span class="sxs-lookup"><span data-stu-id="7d41e-116">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="7d41e-117">Výchozí hodnota je 512.</span><span class="sxs-lookup"><span data-stu-id="7d41e-117">The default value is 512.</span></span> <span data-ttu-id="7d41e-118">Tato vlastnost omezuje počet zpráv mimo pořadí, které lze přijímat pomocí služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="7d41e-118">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d41e-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7d41e-119">Child Elements</span></span>  
 <span data-ttu-id="7d41e-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="7d41e-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7d41e-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7d41e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="7d41e-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="7d41e-122">Element</span></span>|<span data-ttu-id="7d41e-123">Popis</span><span class="sxs-lookup"><span data-stu-id="7d41e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d41e-124">\<chování > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7d41e-124">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="7d41e-125">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="7d41e-125">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7d41e-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d41e-126">See Also</span></span>  
<!-- <xref:System.ServiceModel.Activities.Description.BufferReceiveServiceBehavior>  -->
 <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
