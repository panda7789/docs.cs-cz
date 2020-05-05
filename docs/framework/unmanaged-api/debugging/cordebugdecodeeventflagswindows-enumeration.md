---
title: Výčet CorDebugDecodeEventFlagsWindows
ms.date: 03/30/2017
api_name:
- CorDebugDecodeEventFlagsWindows
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aa6cf962-30ae-4cfd-8895-826deeb46a54
topic_type:
- apiref
ms.openlocfilehash: a90ddd27834e7614c1827d606a9955b4d6c53127
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795973"
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a><span data-ttu-id="60457-102">Výčet CorDebugDecodeEventFlagsWindows</span><span class="sxs-lookup"><span data-stu-id="60457-102">CorDebugDecodeEventFlagsWindows Enumeration</span></span>
<span data-ttu-id="60457-103">Poskytuje další informace o událostech ladění na platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="60457-103">Provides additional information about debug events on the Windows platform.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60457-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60457-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a><span data-ttu-id="60457-105">Členové</span><span class="sxs-lookup"><span data-stu-id="60457-105">Members</span></span>  
  
|<span data-ttu-id="60457-106">Člen</span><span class="sxs-lookup"><span data-stu-id="60457-106">Member</span></span>|<span data-ttu-id="60457-107">Popis</span><span class="sxs-lookup"><span data-stu-id="60457-107">Description</span></span>|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|<span data-ttu-id="60457-108">Označuje, že událost ladění je první pravděpodobnost – výjimka.</span><span class="sxs-lookup"><span data-stu-id="60457-108">Indicates that the debug event is a first-chance exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60457-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="60457-109">Remarks</span></span>  
 <span data-ttu-id="60457-110">Metoda [ICorDebugProcess6::D ecodeevent](icordebugprocess6-decodeevent-method.md) obsahuje `dwFlags` parametr, který poskytuje další informace o události ladění a jejíž hodnota je závislá na cílové architektuře.</span><span class="sxs-lookup"><span data-stu-id="60457-110">The [ICorDebugProcess6::DecodeEvent](icordebugprocess6-decodeevent-method.md) method includes a `dwFlags` parameter that provides additional information about a debug event and whose value is dependent on the target architecture.</span></span> <span data-ttu-id="60457-111">`CorDebugDecodeEventFlagsWindows` Výčet lze použít s událostmi ladění na platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="60457-111">The `CorDebugDecodeEventFlagsWindows` enumeration can be used with debug events on the Windows platform.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="60457-112">Tento výčet je určený pro použití pouze v .NET Nativech scénářích ladění.</span><span class="sxs-lookup"><span data-stu-id="60457-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60457-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="60457-113">Requirements</span></span>  
 <span data-ttu-id="60457-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60457-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60457-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="60457-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60457-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="60457-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60457-117">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60457-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60457-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="60457-118">See also</span></span>

- [<span data-ttu-id="60457-119">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="60457-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
