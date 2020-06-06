---
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: 29b6d8982e712a0fa595b3103803f1795adea892
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398564"
---
# \<workflowUnhandledException>
<span data-ttu-id="646a6-101">Chování služby, který umožňuje určit akci, která má provést při dojde k neošetřené výjimce v rámci pracovního postupu služby.</span><span class="sxs-lookup"><span data-stu-id="646a6-101">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowUnhandledException>**  
  
## <a name="syntax"></a><span data-ttu-id="646a6-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="646a6-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="646a6-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="646a6-103">Attributes and Elements</span></span>  
 <span data-ttu-id="646a6-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="646a6-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="646a6-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="646a6-105">Attributes</span></span>  
  
|<span data-ttu-id="646a6-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="646a6-106">Attribute</span></span>|<span data-ttu-id="646a6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="646a6-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="646a6-108">action</span><span class="sxs-lookup"><span data-stu-id="646a6-108">action</span></span>|<span data-ttu-id="646a6-109">Řetězec, který určuje akci, která se má provést, když dojde k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="646a6-109">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="646a6-110">Tento atribut je typu<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span><span class="sxs-lookup"><span data-stu-id="646a6-110">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="646a6-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="646a6-111">Child Elements</span></span>  
 <span data-ttu-id="646a6-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="646a6-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="646a6-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="646a6-113">Parent Elements</span></span>  
  
|<span data-ttu-id="646a6-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="646a6-114">Element</span></span>|<span data-ttu-id="646a6-115">Description</span><span class="sxs-lookup"><span data-stu-id="646a6-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="646a6-116">\<behavior>tohoto\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="646a6-116">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="646a6-117">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="646a6-117">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="646a6-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="646a6-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
