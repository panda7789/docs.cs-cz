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
ms.openlocfilehash: da3a100bd552eaa3233642b006e0265adbcac1ca
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132217"
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a><span data-ttu-id="5543f-102">Výčet CorDebugDecodeEventFlagsWindows</span><span class="sxs-lookup"><span data-stu-id="5543f-102">CorDebugDecodeEventFlagsWindows Enumeration</span></span>
<span data-ttu-id="5543f-103">Poskytuje další informace o událostech ladění na platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="5543f-103">Provides additional information about debug events on the Windows platform.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5543f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5543f-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a><span data-ttu-id="5543f-105">Členové</span><span class="sxs-lookup"><span data-stu-id="5543f-105">Members</span></span>  
  
|<span data-ttu-id="5543f-106">Člen</span><span class="sxs-lookup"><span data-stu-id="5543f-106">Member</span></span>|<span data-ttu-id="5543f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5543f-107">Description</span></span>|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|<span data-ttu-id="5543f-108">Označuje, že událost ladění je první pravděpodobnost – výjimka.</span><span class="sxs-lookup"><span data-stu-id="5543f-108">Indicates that the debug event is a first-chance exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5543f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5543f-109">Remarks</span></span>  
 <span data-ttu-id="5543f-110">Metoda [ICorDebugProcess6::D ecodeevent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) obsahuje parametr `dwFlags`, který poskytuje další informace o události ladění a jejíž hodnota je závislá na cílové architektuře.</span><span class="sxs-lookup"><span data-stu-id="5543f-110">The [ICorDebugProcess6::DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method includes a `dwFlags` parameter that provides additional information about a debug event and whose value is dependent on the target architecture.</span></span> <span data-ttu-id="5543f-111">Výčet `CorDebugDecodeEventFlagsWindows` lze použít s událostmi ladění na platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="5543f-111">The `CorDebugDecodeEventFlagsWindows` enumeration can be used with debug events on the Windows platform.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5543f-112">Tento výčet je určený pro použití pouze v .NET Nativech scénářích ladění.</span><span class="sxs-lookup"><span data-stu-id="5543f-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5543f-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5543f-113">Requirements</span></span>  
 <span data-ttu-id="5543f-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5543f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5543f-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5543f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5543f-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5543f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5543f-117">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5543f-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5543f-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5543f-118">See also</span></span>

- [<span data-ttu-id="5543f-119">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="5543f-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
