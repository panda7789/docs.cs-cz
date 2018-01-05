---
title: ServiceThrottlingBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ccf1c167c4d1a072737f725de2fa0c132ca686f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="13631-102">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="13631-102">ServiceThrottlingBehavior</span></span>
<span data-ttu-id="13631-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="13631-103">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13631-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13631-104">Syntax</span></span>  
  
```  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="13631-105">Metody</span><span class="sxs-lookup"><span data-stu-id="13631-105">Methods</span></span>  
 <span data-ttu-id="13631-106">Třída třídy ServiceThrottlingBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="13631-106">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="13631-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="13631-107">Properties</span></span>  
 <span data-ttu-id="13631-108">Třída třídy ServiceThrottlingBehavior má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="13631-108">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="13631-109">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="13631-109">MaxConcurrentCalls</span></span>  
 <span data-ttu-id="13631-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="13631-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="13631-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="13631-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="13631-112">Maximální počet zpráv ve všech objektech dispečera v ServiceHost aktivně zpracovávají.</span><span class="sxs-lookup"><span data-stu-id="13631-112">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="13631-113">maxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="13631-113">MaxConcurrentInstances</span></span>  
 <span data-ttu-id="13631-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="13631-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="13631-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="13631-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="13631-116">Maximální počet objekty služby, které mohou být prováděny současně.</span><span class="sxs-lookup"><span data-stu-id="13631-116">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="13631-117">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="13631-117">MaxConcurrentSessions</span></span>  
 <span data-ttu-id="13631-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="13631-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="13631-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="13631-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="13631-120">Maximální počet relací, které hostitele může přijmout najednou.</span><span class="sxs-lookup"><span data-stu-id="13631-120">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13631-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="13631-121">Requirements</span></span>  
  
|<span data-ttu-id="13631-122">MOF</span><span class="sxs-lookup"><span data-stu-id="13631-122">MOF</span></span>|<span data-ttu-id="13631-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="13631-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="13631-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="13631-124">Namespace</span></span>|<span data-ttu-id="13631-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="13631-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="13631-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="13631-126">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
