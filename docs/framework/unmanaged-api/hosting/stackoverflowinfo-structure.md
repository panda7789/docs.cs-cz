---
title: StackOverflowInfo – struktura
ms.date: 03/30/2017
api_name:
- StackOverflowInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowInfo
helpviewer_keywords:
- StackOverflowInfo structure [.NET Framework hosting]
ms.assetid: 519389f2-0217-436c-99d4-93a76ebce5b5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac0f5d522a24394369583692f8c564254529bf13
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137343"
---
# <a name="stackoverflowinfo-structure"></a><span data-ttu-id="9792c-102">StackOverflowInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="9792c-102">StackOverflowInfo Structure</span></span>
<span data-ttu-id="9792c-103">Ukládá typu došlo k přetečení a informace o výjimce, která byla vyvolána z důvodu přetečení.</span><span class="sxs-lookup"><span data-stu-id="9792c-103">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9792c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9792c-104">Syntax</span></span>  
  
```  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="9792c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="9792c-105">Members</span></span>  
  
|<span data-ttu-id="9792c-106">Člen</span><span class="sxs-lookup"><span data-stu-id="9792c-106">Member</span></span>|<span data-ttu-id="9792c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9792c-107">Description</span></span>|  
|------------|-----------------|  
|`soType`|<span data-ttu-id="9792c-108">Hodnota [stackoverflowtype –](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) výčet, který určuje typ přetečení.</span><span class="sxs-lookup"><span data-stu-id="9792c-108">A value of the [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) enumeration that specifies the type of overflow.</span></span>|  
|`pExceptionInfo`|<span data-ttu-id="9792c-109">Ukazatel na Win32 `EXCEPTION_POINTERS` objektu, který obsahuje záznam o výjimce s popisem nezávislé na počítač výjimku a kontextového záznamu s popisem závislé na počítači kontext procesoru v okamžiku výjimky.</span><span class="sxs-lookup"><span data-stu-id="9792c-109">A pointer to a Win32 `EXCEPTION_POINTERS` object, which contains an exception record with a machine-independent description of an exception and a context record with a machine-dependent description of the processor context at the time of the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9792c-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9792c-110">Remarks</span></span>  
 <span data-ttu-id="9792c-111">A `StackOverflowInfo` objekt je předán [iactiononclrevent::ONEVENT –](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) metodu `Event_StackOverflow` události.</span><span class="sxs-lookup"><span data-stu-id="9792c-111">A `StackOverflowInfo` object is passed to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method for `Event_StackOverflow` events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9792c-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9792c-112">Requirements</span></span>  
 <span data-ttu-id="9792c-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9792c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9792c-114">**Záhlaví:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="9792c-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="9792c-115">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9792c-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="9792c-116">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9792c-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9792c-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9792c-117">See also</span></span>

- [<span data-ttu-id="9792c-118">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="9792c-118">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
