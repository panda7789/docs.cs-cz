---
title: '&lt;callbackDebug&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0bb730a00358f771408ff0431ff2ab77623354a4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltcallbackdebuggt"></a><span data-ttu-id="313f7-102">&lt;callbackDebug&gt;</span><span class="sxs-lookup"><span data-stu-id="313f7-102">&lt;callbackDebug&gt;</span></span>
<span data-ttu-id="313f7-103">Určuje služby ladění pro [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] objekt zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="313f7-103">Specifies service debugging for a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] callback object.</span></span>  
  
 <span data-ttu-id="313f7-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="313f7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="313f7-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="313f7-105">\<behaviors></span></span>  
<span data-ttu-id="313f7-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="313f7-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="313f7-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="313f7-107">\<behavior></span></span>  
<span data-ttu-id="313f7-108">\<callbackDebug ></span><span class="sxs-lookup"><span data-stu-id="313f7-108">\<callbackDebug></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="313f7-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="313f7-109">Syntax</span></span>  
  
```xml  
<callbackDebug  includeExceptionDetailInFaults="Boolean" />  
```  
  
## <a name="type"></a><span data-ttu-id="313f7-110">Typ</span><span class="sxs-lookup"><span data-stu-id="313f7-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="313f7-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="313f7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="313f7-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="313f7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="313f7-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="313f7-113">Attributes</span></span>  
  
|<span data-ttu-id="313f7-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="313f7-114">Attribute</span></span>|<span data-ttu-id="313f7-115">Popis</span><span class="sxs-lookup"><span data-stu-id="313f7-115">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="313f7-116">Hodnota, která určuje, zda objekty zpětné volání klienta vrátit informace o spravovaných výjimce v chyb SOAP zpět ke službě.</span><span class="sxs-lookup"><span data-stu-id="313f7-116">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="313f7-117">Pokud tento atribut nastavíte na `true` prostřednictvím kódu programu, můžete povolit tok spravovaných výjimek informací v objektu zpětné volání klienta zpět na službu pro účely ladění.</span><span class="sxs-lookup"><span data-stu-id="313f7-117">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="313f7-118">**Upozornění:** vrácení informací o spravovaných výjimce klientům může být bezpečnostní riziko.</span><span class="sxs-lookup"><span data-stu-id="313f7-118">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="313f7-119">To je proto podrobnosti o výjimce zveřejnění informace o interní služby implementace, která může neoprávněným klienty.</span><span class="sxs-lookup"><span data-stu-id="313f7-119">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="313f7-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="313f7-120">Child Elements</span></span>  
 <span data-ttu-id="313f7-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="313f7-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="313f7-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="313f7-122">Parent Elements</span></span>  
  
|<span data-ttu-id="313f7-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="313f7-123">Element</span></span>|<span data-ttu-id="313f7-124">Popis</span><span class="sxs-lookup"><span data-stu-id="313f7-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="313f7-125">\<chování ></span><span class="sxs-lookup"><span data-stu-id="313f7-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="313f7-126">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="313f7-126">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="313f7-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="313f7-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CallbackDebugElement>  
 <xref:System.ServiceModel.Description.CallbackDebugBehavior>
