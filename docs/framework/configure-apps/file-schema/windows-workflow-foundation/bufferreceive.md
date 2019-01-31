---
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: 6ed37d73440dac22288ae1da526d81b2d0b990a1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55286621"
---
# <a name="bufferreceive"></a><span data-ttu-id="a5857-101">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="a5857-101">\<bufferReceive></span></span>
<span data-ttu-id="a5857-102">Zpracování, která umožňuje služba pracovního postupu ke zpracování zpráv mimo pořadí příjmu chování služby, který povoluje službu, chcete-li použít do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="a5857-102">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="a5857-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a5857-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="a5857-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="a5857-104">\<behaviors></span></span>  
<span data-ttu-id="a5857-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="a5857-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="a5857-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="a5857-106">\<behavior></span></span>  
<span data-ttu-id="a5857-107">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="a5857-107">\<bufferReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5857-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5857-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5857-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a5857-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a5857-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a5857-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5857-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="a5857-111">Attributes</span></span>  
  
|<span data-ttu-id="a5857-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="a5857-112">Attribute</span></span>|<span data-ttu-id="a5857-113">Popis</span><span class="sxs-lookup"><span data-stu-id="a5857-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a5857-114">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="a5857-114">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="a5857-115">Celé číslo, která určuje maximální počet čekajících na zpracování počet zpráv povolených pro každý kanál.</span><span class="sxs-lookup"><span data-stu-id="a5857-115">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="a5857-116">Výchozí hodnota je 512.</span><span class="sxs-lookup"><span data-stu-id="a5857-116">The default value is 512.</span></span> <span data-ttu-id="a5857-117">Tato vlastnost omezuje počet zpráv mimo pořadí, které lze přijímat pomocí služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a5857-117">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a5857-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a5857-118">Child Elements</span></span>  
 <span data-ttu-id="a5857-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="a5857-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a5857-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a5857-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a5857-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="a5857-121">Element</span></span>|<span data-ttu-id="a5857-122">Popis</span><span class="sxs-lookup"><span data-stu-id="a5857-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5857-123">\<chování > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="a5857-123">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="a5857-124">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="a5857-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a5857-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5857-125">See also</span></span>
<!-- <xref:System.ServiceModel.Activities.Description.BufferReceiveServiceBehavior>  -->
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
