---
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: be5173ea43c6f7fca7180a311885a26c889b12db
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398838"
---
# \<bufferReceive>
<span data-ttu-id="8ae8d-101">Zpracování, která umožňuje služba pracovního postupu ke zpracování zpráv mimo pořadí příjmu chování služby, který povoluje službu, chcete-li použít do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="8ae8d-101">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bufferReceive>**  
  
## <a name="syntax"></a><span data-ttu-id="8ae8d-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ae8d-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ae8d-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8ae8d-103">Attributes and Elements</span></span>  
 <span data-ttu-id="8ae8d-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8ae8d-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ae8d-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="8ae8d-105">Attributes</span></span>  
  
|<span data-ttu-id="8ae8d-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="8ae8d-106">Attribute</span></span>|<span data-ttu-id="8ae8d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8ae8d-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8ae8d-108">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="8ae8d-108">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="8ae8d-109">Celé číslo, která určuje maximální počet čekajících na zpracování počet zpráv povolených pro každý kanál.</span><span class="sxs-lookup"><span data-stu-id="8ae8d-109">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="8ae8d-110">Výchozí hodnota je 512.</span><span class="sxs-lookup"><span data-stu-id="8ae8d-110">The default value is 512.</span></span> <span data-ttu-id="8ae8d-111">Tato vlastnost omezuje počet zpráv mimo pořadí, které lze přijímat pomocí služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8ae8d-111">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8ae8d-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8ae8d-112">Child Elements</span></span>  
 <span data-ttu-id="8ae8d-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="8ae8d-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8ae8d-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8ae8d-114">Parent Elements</span></span>  
  
|<span data-ttu-id="8ae8d-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="8ae8d-115">Element</span></span>|<span data-ttu-id="8ae8d-116">Description</span><span class="sxs-lookup"><span data-stu-id="8ae8d-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8ae8d-117">\<behavior>tohoto\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="8ae8d-117">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="8ae8d-118">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="8ae8d-118">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8ae8d-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ae8d-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.BufferedReceiveServiceBehavior>
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
