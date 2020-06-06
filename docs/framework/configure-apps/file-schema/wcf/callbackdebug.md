---
title: <callbackDebug>
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 92a8fa83b5cf5f429278ac8edc8439b627839aad
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400560"
---
# \<callbackDebug>
<span data-ttu-id="db056-101">Určuje ladění služby pro objekt zpětného volání služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="db056-101">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackDebug>**  
  
## <a name="syntax"></a><span data-ttu-id="db056-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db056-102">Syntax</span></span>  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a><span data-ttu-id="db056-103">Typ</span><span class="sxs-lookup"><span data-stu-id="db056-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db056-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="db056-104">Attributes and Elements</span></span>  
 <span data-ttu-id="db056-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="db056-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db056-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="db056-106">Attributes</span></span>  
  
|<span data-ttu-id="db056-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="db056-107">Attribute</span></span>|<span data-ttu-id="db056-108">Popis</span><span class="sxs-lookup"><span data-stu-id="db056-108">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="db056-109">Hodnota, která určuje, zda objekty zpětného volání klienta vracejí informace o spravované výjimce v chybách protokolu SOAP zpět do služby.</span><span class="sxs-lookup"><span data-stu-id="db056-109">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="db056-110">Pokud tento atribut nastavíte na `true` programové, můžete povolit tok informací o spravovaných výjimkách v objektu zpětného volání klienta zpátky do služby pro účely ladění.</span><span class="sxs-lookup"><span data-stu-id="db056-110">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="db056-111">**Upozornění:**  Vrácení informací o spravované výjimce klientům může představovat bezpečnostní riziko.</span><span class="sxs-lookup"><span data-stu-id="db056-111">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="db056-112">Důvodem je skutečnost, že podrobnosti o výjimce zpřístupňují informace o implementaci interní služby, které by mohly být používány neautorizovanými klienty.</span><span class="sxs-lookup"><span data-stu-id="db056-112">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="db056-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="db056-113">Child Elements</span></span>  
 <span data-ttu-id="db056-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="db056-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="db056-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="db056-115">Parent Elements</span></span>  
  
|<span data-ttu-id="db056-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="db056-116">Element</span></span>|<span data-ttu-id="db056-117">Description</span><span class="sxs-lookup"><span data-stu-id="db056-117">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="db056-118">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="db056-118">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="db056-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="db056-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
