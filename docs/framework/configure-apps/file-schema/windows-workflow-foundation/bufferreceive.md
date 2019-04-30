---
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: 360d26fda964fa33640e833ad22dab7e06e153f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790257"
---
# <a name="bufferreceive"></a><span data-ttu-id="e8fed-101">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="e8fed-101">\<bufferReceive></span></span>
<span data-ttu-id="e8fed-102">Zpracování, která umožňuje služba pracovního postupu ke zpracování zpráv mimo pořadí příjmu chování služby, který povoluje službu, chcete-li použít do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e8fed-102">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="e8fed-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e8fed-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="e8fed-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="e8fed-104">\<behaviors></span></span>  
<span data-ttu-id="e8fed-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="e8fed-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="e8fed-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="e8fed-106">\<behavior></span></span>  
<span data-ttu-id="e8fed-107">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="e8fed-107">\<bufferReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8fed-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8fed-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8fed-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e8fed-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e8fed-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e8fed-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8fed-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="e8fed-111">Attributes</span></span>  
  
|<span data-ttu-id="e8fed-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="e8fed-112">Attribute</span></span>|<span data-ttu-id="e8fed-113">Popis</span><span class="sxs-lookup"><span data-stu-id="e8fed-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e8fed-114">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="e8fed-114">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="e8fed-115">Celé číslo, která určuje maximální počet čekajících na zpracování počet zpráv povolených pro každý kanál.</span><span class="sxs-lookup"><span data-stu-id="e8fed-115">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="e8fed-116">Výchozí hodnota je 512.</span><span class="sxs-lookup"><span data-stu-id="e8fed-116">The default value is 512.</span></span> <span data-ttu-id="e8fed-117">Tato vlastnost omezuje počet zpráv mimo pořadí, které lze přijímat pomocí služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e8fed-117">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e8fed-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e8fed-118">Child Elements</span></span>  
 <span data-ttu-id="e8fed-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="e8fed-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e8fed-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e8fed-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e8fed-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="e8fed-121">Element</span></span>|<span data-ttu-id="e8fed-122">Popis</span><span class="sxs-lookup"><span data-stu-id="e8fed-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8fed-123">\<chování > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e8fed-123">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="e8fed-124">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="e8fed-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e8fed-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8fed-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.BufferedReceiveServiceBehavior>
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
