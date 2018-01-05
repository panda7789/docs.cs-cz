---
title: "StackOverflowInfo – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StackOverflowInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: StackOverflowInfo
helpviewer_keywords: StackOverflowInfo structure [.NET Framework hosting]
ms.assetid: 519389f2-0217-436c-99d4-93a76ebce5b5
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12a880a7c30277d382bff2b46ebe10720880e907
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="stackoverflowinfo-structure"></a><span data-ttu-id="b2a36-102">StackOverflowInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="b2a36-102">StackOverflowInfo Structure</span></span>
<span data-ttu-id="b2a36-103">Uloží typ přetečení, k níž došlo a informace na výjimku, která byla vydána z důvodu přetečení.</span><span class="sxs-lookup"><span data-stu-id="b2a36-103">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2a36-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2a36-104">Syntax</span></span>  
  
```  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="b2a36-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b2a36-105">Members</span></span>  
  
|<span data-ttu-id="b2a36-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b2a36-106">Member</span></span>|<span data-ttu-id="b2a36-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b2a36-107">Description</span></span>|  
|------------|-----------------|  
|`soType`|<span data-ttu-id="b2a36-108">Hodnota [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) výčet, který určuje typ přetečení.</span><span class="sxs-lookup"><span data-stu-id="b2a36-108">A value of the [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) enumeration that specifies the type of overflow.</span></span>|  
|`pExceptionInfo`|<span data-ttu-id="b2a36-109">Ukazatel na Win32 `EXCEPTION_POINTERS` objekt, který obsahuje záznam výjimky s popisem nezávislé na počítač výjimky a kontextu záznam s závislé na počítač popis kontext procesoru v okamžiku výjimky.</span><span class="sxs-lookup"><span data-stu-id="b2a36-109">A pointer to a Win32 `EXCEPTION_POINTERS` object, which contains an exception record with a machine-independent description of an exception and a context record with a machine-dependent description of the processor context at the time of the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2a36-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b2a36-110">Remarks</span></span>  
 <span data-ttu-id="b2a36-111">A `StackOverflowInfo` je předán objekt [iactiononclrevent::ONEVENT –](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) metodu pro `Event_StackOverflow` události.</span><span class="sxs-lookup"><span data-stu-id="b2a36-111">A `StackOverflowInfo` object is passed to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method for `Event_StackOverflow` events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2a36-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b2a36-112">Requirements</span></span>  
 <span data-ttu-id="b2a36-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2a36-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2a36-114">**Záhlaví:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="b2a36-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="b2a36-115">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b2a36-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b2a36-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2a36-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2a36-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2a36-117">See Also</span></span>  
 [<span data-ttu-id="b2a36-118">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="b2a36-118">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
