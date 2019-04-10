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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d4e006a03db5b16de93dfd07ec7b964db4bfc1d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207731"
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a><span data-ttu-id="97631-102">Výčet CorDebugDecodeEventFlagsWindows</span><span class="sxs-lookup"><span data-stu-id="97631-102">CorDebugDecodeEventFlagsWindows Enumeration</span></span>
<span data-ttu-id="97631-103">Poskytuje další informace o ladění událostí na platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="97631-103">Provides additional information about debug events on the Windows platform.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97631-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97631-104">Syntax</span></span>  
  
```  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a><span data-ttu-id="97631-105">Členové</span><span class="sxs-lookup"><span data-stu-id="97631-105">Members</span></span>  
  
|<span data-ttu-id="97631-106">Člen</span><span class="sxs-lookup"><span data-stu-id="97631-106">Member</span></span>|<span data-ttu-id="97631-107">Popis</span><span class="sxs-lookup"><span data-stu-id="97631-107">Description</span></span>|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|<span data-ttu-id="97631-108">Označuje, že událost ladění je výjimka první příležitosti.</span><span class="sxs-lookup"><span data-stu-id="97631-108">Indicates that the debug event is a first-chance exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97631-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="97631-109">Remarks</span></span>  
 <span data-ttu-id="97631-110">[Icordebugprocess6::decodeevent –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) obsahuje metodu `dwFlags` parametr, který poskytuje další informace o ladění události, a jehož hodnota je závislá na Cílová architektura.</span><span class="sxs-lookup"><span data-stu-id="97631-110">The [ICorDebugProcess6::DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method includes a `dwFlags` parameter that provides additional information about a debug event and whose value is dependent on the target architecture.</span></span> <span data-ttu-id="97631-111">`CorDebugDecodeEventFlagsWindows` Výčtu lze použít s výjimky ladění na platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="97631-111">The `CorDebugDecodeEventFlagsWindows` enumeration can be used with debug events on the Windows platform.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="97631-112">Tento výčet je určena pro použití v .NET Native ladění pouze scénáře.</span><span class="sxs-lookup"><span data-stu-id="97631-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97631-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="97631-113">Requirements</span></span>  
 <span data-ttu-id="97631-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97631-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97631-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="97631-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97631-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97631-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="97631-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="97631-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="97631-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="97631-118">See also</span></span>

- [<span data-ttu-id="97631-119">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="97631-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
