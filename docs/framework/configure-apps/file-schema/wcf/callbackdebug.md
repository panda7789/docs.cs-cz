---
title: <callbackDebug>
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: a1190eb1c015ba07488ff5a5952f2f5f1b10974c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704515"
---
# <a name="callbackdebug"></a><span data-ttu-id="d715d-101">\<callbackDebug ></span><span class="sxs-lookup"><span data-stu-id="d715d-101">\<callbackDebug></span></span>
<span data-ttu-id="d715d-102">Určuje ladění služby pro objekt zpětného volání Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d715d-102">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
 <span data-ttu-id="d715d-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d715d-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="d715d-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="d715d-104">\<behaviors></span></span>  
<span data-ttu-id="d715d-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="d715d-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="d715d-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="d715d-106">\<behavior></span></span>  
<span data-ttu-id="d715d-107">\<callbackDebug ></span><span class="sxs-lookup"><span data-stu-id="d715d-107">\<callbackDebug></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d715d-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d715d-108">Syntax</span></span>  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a><span data-ttu-id="d715d-109">Type</span><span class="sxs-lookup"><span data-stu-id="d715d-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d715d-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d715d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d715d-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d715d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d715d-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="d715d-112">Attributes</span></span>  
  
|<span data-ttu-id="d715d-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="d715d-113">Attribute</span></span>|<span data-ttu-id="d715d-114">Popis</span><span class="sxs-lookup"><span data-stu-id="d715d-114">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="d715d-115">Hodnota, která určuje, zda objekty zpětného volání klienta vrátí informace o spravované výjimce v chyb SOAP zpět do služby.</span><span class="sxs-lookup"><span data-stu-id="d715d-115">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="d715d-116">Pokud tento atribut nastavíte na `true` můžete prostřednictvím kódu programu, může být povolen tok informací o řízené výjimce do objektu zpětného volání klienta zpět do služby pro účely ladění.</span><span class="sxs-lookup"><span data-stu-id="d715d-116">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="d715d-117">**Upozornění:**  Vracející informace o spravované výjimce klientům může představovat bezpečnostní riziko.</span><span class="sxs-lookup"><span data-stu-id="d715d-117">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="d715d-118">Je to proto, že podrobnosti o výjimce zveřejnit informace o implementaci vnitřní chybě služby, které by mohly používat neoprávněným klientů.</span><span class="sxs-lookup"><span data-stu-id="d715d-118">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d715d-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d715d-119">Child Elements</span></span>  
 <span data-ttu-id="d715d-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="d715d-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d715d-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d715d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d715d-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="d715d-122">Element</span></span>|<span data-ttu-id="d715d-123">Popis</span><span class="sxs-lookup"><span data-stu-id="d715d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d715d-124">\<behavior></span><span class="sxs-lookup"><span data-stu-id="d715d-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="d715d-125">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="d715d-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d715d-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d715d-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
