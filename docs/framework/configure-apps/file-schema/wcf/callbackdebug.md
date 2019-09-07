---
title: <callbackDebug>
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 92a8fa83b5cf5f429278ac8edc8439b627839aad
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400560"
---
# <a name="callbackdebug"></a><span data-ttu-id="920f7-101">\<callbackDebug ></span><span class="sxs-lookup"><span data-stu-id="920f7-101">\<callbackDebug></span></span>
<span data-ttu-id="920f7-102">Určuje ladění služby pro objekt zpětného volání služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="920f7-102">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
<span data-ttu-id="920f7-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="920f7-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="920f7-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="920f7-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="920f7-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="920f7-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="920f7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="920f7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="920f7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="920f7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="920f7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<callbackDebug >**</span><span class="sxs-lookup"><span data-stu-id="920f7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackDebug>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="920f7-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="920f7-109">Syntax</span></span>  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a><span data-ttu-id="920f7-110">type</span><span class="sxs-lookup"><span data-stu-id="920f7-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="920f7-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="920f7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="920f7-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="920f7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="920f7-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="920f7-113">Attributes</span></span>  
  
|<span data-ttu-id="920f7-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="920f7-114">Attribute</span></span>|<span data-ttu-id="920f7-115">Popis</span><span class="sxs-lookup"><span data-stu-id="920f7-115">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="920f7-116">Hodnota, která určuje, zda objekty zpětného volání klienta vracejí informace o spravované výjimce v chybách protokolu SOAP zpět do služby.</span><span class="sxs-lookup"><span data-stu-id="920f7-116">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="920f7-117">Pokud tento atribut nastavíte na `true` programové, můžete povolit tok informací o spravovaných výjimkách v objektu zpětného volání klienta zpátky do služby pro účely ladění.</span><span class="sxs-lookup"><span data-stu-id="920f7-117">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="920f7-118">**Upozornění**  Vrácení informací o spravované výjimce klientům může představovat bezpečnostní riziko.</span><span class="sxs-lookup"><span data-stu-id="920f7-118">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="920f7-119">Důvodem je skutečnost, že podrobnosti o výjimce zpřístupňují informace o implementaci interní služby, které by mohly být používány neautorizovanými klienty.</span><span class="sxs-lookup"><span data-stu-id="920f7-119">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="920f7-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="920f7-120">Child Elements</span></span>  
 <span data-ttu-id="920f7-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="920f7-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="920f7-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="920f7-122">Parent Elements</span></span>  
  
|<span data-ttu-id="920f7-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="920f7-123">Element</span></span>|<span data-ttu-id="920f7-124">Popis</span><span class="sxs-lookup"><span data-stu-id="920f7-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="920f7-125">\<> chování</span><span class="sxs-lookup"><span data-stu-id="920f7-125">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="920f7-126">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="920f7-126">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="920f7-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="920f7-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
