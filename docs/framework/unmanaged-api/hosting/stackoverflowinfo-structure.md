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
ms.openlocfilehash: 941093b9a0856c2b716ba359c854473f3c9ea26a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006516"
---
# <a name="stackoverflowinfo-structure"></a><span data-ttu-id="89982-102">StackOverflowInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="89982-102">StackOverflowInfo Structure</span></span>
<span data-ttu-id="89982-103">Ukládá typ přetečení, ke kterému došlo, a informace o výjimce, která byla vyvolána z důvodu přetečení.</span><span class="sxs-lookup"><span data-stu-id="89982-103">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89982-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89982-104">Syntax</span></span>  
  
```cpp  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="89982-105">Členové</span><span class="sxs-lookup"><span data-stu-id="89982-105">Members</span></span>  
  
|<span data-ttu-id="89982-106">Člen</span><span class="sxs-lookup"><span data-stu-id="89982-106">Member</span></span>|<span data-ttu-id="89982-107">Description</span><span class="sxs-lookup"><span data-stu-id="89982-107">Description</span></span>|  
|------------|-----------------|  
|`soType`|<span data-ttu-id="89982-108">Hodnota výčtu [StackOverflowType –](stackoverflowtype-enumeration.md) , která určuje typ přetečení.</span><span class="sxs-lookup"><span data-stu-id="89982-108">A value of the [StackOverflowType](stackoverflowtype-enumeration.md) enumeration that specifies the type of overflow.</span></span>|  
|`pExceptionInfo`|<span data-ttu-id="89982-109">Ukazatel na `EXCEPTION_POINTERS` objekt Win32, který obsahuje záznam výjimky s popisem výjimky a záznamem kontextu s popisem procesoru závislého na počítači v době výjimky.</span><span class="sxs-lookup"><span data-stu-id="89982-109">A pointer to a Win32 `EXCEPTION_POINTERS` object, which contains an exception record with a machine-independent description of an exception and a context record with a machine-dependent description of the processor context at the time of the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89982-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="89982-110">Remarks</span></span>  
 <span data-ttu-id="89982-111">`StackOverflowInfo`Objekt je předán metodě [IActionOnCLREvent –::](iactiononclrevent-onevent-method.md) prohledatelné `Event_StackOverflow` události.</span><span class="sxs-lookup"><span data-stu-id="89982-111">A `StackOverflowInfo` object is passed to the [IActionOnCLREvent::OnEvent](iactiononclrevent-onevent-method.md) method for `Event_StackOverflow` events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89982-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="89982-112">Requirements</span></span>  
 <span data-ttu-id="89982-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89982-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89982-114">**Hlavička:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="89982-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="89982-115">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="89982-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="89982-116">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89982-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89982-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="89982-117">See also</span></span>

- [<span data-ttu-id="89982-118">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="89982-118">Hosting Structures</span></span>](hosting-structures.md)
