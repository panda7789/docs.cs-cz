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
ms.openlocfilehash: 1072026f92edbc646653c6dd74ec8e22d5b887e5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73105910"
---
# <a name="stackoverflowinfo-structure"></a><span data-ttu-id="302c9-102">StackOverflowInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="302c9-102">StackOverflowInfo Structure</span></span>
<span data-ttu-id="302c9-103">Ukládá typ přetečení, ke kterému došlo, a informace o výjimce, která byla vyvolána z důvodu přetečení.</span><span class="sxs-lookup"><span data-stu-id="302c9-103">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="302c9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="302c9-104">Syntax</span></span>  
  
```cpp  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="302c9-105">Členové</span><span class="sxs-lookup"><span data-stu-id="302c9-105">Members</span></span>  
  
|<span data-ttu-id="302c9-106">Člen</span><span class="sxs-lookup"><span data-stu-id="302c9-106">Member</span></span>|<span data-ttu-id="302c9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="302c9-107">Description</span></span>|  
|------------|-----------------|  
|`soType`|<span data-ttu-id="302c9-108">Hodnota výčtu [StackOverflowType –](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) , která určuje typ přetečení.</span><span class="sxs-lookup"><span data-stu-id="302c9-108">A value of the [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) enumeration that specifies the type of overflow.</span></span>|  
|`pExceptionInfo`|<span data-ttu-id="302c9-109">Ukazatel na objekt Win32 `EXCEPTION_POINTERS`, který obsahuje záznam výjimky s popisem výjimky a záznamem kontextu s popisem procesoru závislého na počítači v okamžiku výjimky.</span><span class="sxs-lookup"><span data-stu-id="302c9-109">A pointer to a Win32 `EXCEPTION_POINTERS` object, which contains an exception record with a machine-independent description of an exception and a context record with a machine-dependent description of the processor context at the time of the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="302c9-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="302c9-110">Remarks</span></span>  
 <span data-ttu-id="302c9-111">`StackOverflowInfo` objekt je předán metodě [IActionOnCLREvent –::](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) prohledatelné události `Event_StackOverflow`.</span><span class="sxs-lookup"><span data-stu-id="302c9-111">A `StackOverflowInfo` object is passed to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method for `Event_StackOverflow` events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="302c9-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="302c9-112">Requirements</span></span>  
 <span data-ttu-id="302c9-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="302c9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="302c9-114">**Hlavička:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="302c9-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="302c9-115">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="302c9-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="302c9-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="302c9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="302c9-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="302c9-117">See also</span></span>

- [<span data-ttu-id="302c9-118">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="302c9-118">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
