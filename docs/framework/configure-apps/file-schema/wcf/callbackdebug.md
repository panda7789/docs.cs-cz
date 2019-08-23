---
title: <callbackDebug>
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 91e7bd63bf496f2c38776d88173ed2ac12a3b888
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926306"
---
# <a name="callbackdebug"></a><span data-ttu-id="753cd-101">\<callbackDebug ></span><span class="sxs-lookup"><span data-stu-id="753cd-101">\<callbackDebug></span></span>
<span data-ttu-id="753cd-102">Určuje ladění služby pro objekt zpětného volání služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="753cd-102">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
 <span data-ttu-id="753cd-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="753cd-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="753cd-104">\<> chování</span><span class="sxs-lookup"><span data-stu-id="753cd-104">\<behaviors></span></span>  
<span data-ttu-id="753cd-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="753cd-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="753cd-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="753cd-106">\<behavior></span></span>  
<span data-ttu-id="753cd-107">\<callbackDebug ></span><span class="sxs-lookup"><span data-stu-id="753cd-107">\<callbackDebug></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="753cd-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="753cd-108">Syntax</span></span>  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a><span data-ttu-id="753cd-109">type</span><span class="sxs-lookup"><span data-stu-id="753cd-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="753cd-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="753cd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="753cd-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="753cd-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="753cd-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="753cd-112">Attributes</span></span>  
  
|<span data-ttu-id="753cd-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="753cd-113">Attribute</span></span>|<span data-ttu-id="753cd-114">Popis</span><span class="sxs-lookup"><span data-stu-id="753cd-114">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="753cd-115">Hodnota, která určuje, zda objekty zpětného volání klienta vracejí informace o spravované výjimce v chybách protokolu SOAP zpět do služby.</span><span class="sxs-lookup"><span data-stu-id="753cd-115">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="753cd-116">Pokud tento atribut nastavíte na `true` programové, můžete povolit tok informací o spravovaných výjimkách v objektu zpětného volání klienta zpátky do služby pro účely ladění.</span><span class="sxs-lookup"><span data-stu-id="753cd-116">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="753cd-117">**Upozornění**  Vrácení informací o spravované výjimce klientům může představovat bezpečnostní riziko.</span><span class="sxs-lookup"><span data-stu-id="753cd-117">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="753cd-118">Důvodem je skutečnost, že podrobnosti o výjimce zpřístupňují informace o implementaci interní služby, které by mohly být používány neautorizovanými klienty.</span><span class="sxs-lookup"><span data-stu-id="753cd-118">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="753cd-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="753cd-119">Child Elements</span></span>  
 <span data-ttu-id="753cd-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="753cd-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="753cd-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="753cd-121">Parent Elements</span></span>  
  
|<span data-ttu-id="753cd-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="753cd-122">Element</span></span>|<span data-ttu-id="753cd-123">Popis</span><span class="sxs-lookup"><span data-stu-id="753cd-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="753cd-124">\<> chování</span><span class="sxs-lookup"><span data-stu-id="753cd-124">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="753cd-125">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="753cd-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="753cd-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="753cd-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
