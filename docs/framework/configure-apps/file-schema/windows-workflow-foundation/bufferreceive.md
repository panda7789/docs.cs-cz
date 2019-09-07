---
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: be5173ea43c6f7fca7180a311885a26c889b12db
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398838"
---
# <a name="bufferreceive"></a><span data-ttu-id="d3913-101">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="d3913-101">\<bufferReceive></span></span>
<span data-ttu-id="d3913-102">Zpracování, která umožňuje služba pracovního postupu ke zpracování zpráv mimo pořadí příjmu chování služby, který povoluje službu, chcete-li použít do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d3913-102">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="d3913-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d3913-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d3913-104">&nbsp;&nbsp;[ **\<souborů. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="d3913-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="d3913-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="d3913-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="d3913-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="d3913-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="d3913-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="d3913-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="d3913-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bufferReceive >**</span><span class="sxs-lookup"><span data-stu-id="d3913-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bufferReceive>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3913-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3913-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3913-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d3913-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d3913-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d3913-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3913-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="d3913-112">Attributes</span></span>  
  
|<span data-ttu-id="d3913-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="d3913-113">Attribute</span></span>|<span data-ttu-id="d3913-114">Popis</span><span class="sxs-lookup"><span data-stu-id="d3913-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d3913-115">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="d3913-115">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="d3913-116">Celé číslo, která určuje maximální počet čekajících na zpracování počet zpráv povolených pro každý kanál.</span><span class="sxs-lookup"><span data-stu-id="d3913-116">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="d3913-117">Výchozí hodnota je 512.</span><span class="sxs-lookup"><span data-stu-id="d3913-117">The default value is 512.</span></span> <span data-ttu-id="d3913-118">Tato vlastnost omezuje počet zpráv mimo pořadí, které lze přijímat pomocí služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="d3913-118">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d3913-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d3913-119">Child Elements</span></span>  
 <span data-ttu-id="d3913-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="d3913-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d3913-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d3913-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d3913-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="d3913-122">Element</span></span>|<span data-ttu-id="d3913-123">Popis</span><span class="sxs-lookup"><span data-stu-id="d3913-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3913-124">\<chování > \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="d3913-124">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="d3913-125">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="d3913-125">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3913-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d3913-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.BufferedReceiveServiceBehavior>
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
