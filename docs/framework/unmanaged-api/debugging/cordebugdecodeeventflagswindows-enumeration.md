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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207731"
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a><span data-ttu-id="ee2d4-102">Výčet CorDebugDecodeEventFlagsWindows</span><span class="sxs-lookup"><span data-stu-id="ee2d4-102">CorDebugDecodeEventFlagsWindows Enumeration</span></span>
<span data-ttu-id="ee2d4-103">Poskytuje další informace o ladění událostí na platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="ee2d4-103">Provides additional information about debug events on the Windows platform.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee2d4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee2d4-104">Syntax</span></span>  
  
```  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a><span data-ttu-id="ee2d4-105">Členové</span><span class="sxs-lookup"><span data-stu-id="ee2d4-105">Members</span></span>  
  
|<span data-ttu-id="ee2d4-106">Člen</span><span class="sxs-lookup"><span data-stu-id="ee2d4-106">Member</span></span>|<span data-ttu-id="ee2d4-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ee2d4-107">Description</span></span>|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|<span data-ttu-id="ee2d4-108">Označuje, že událost ladění je výjimka první příležitosti.</span><span class="sxs-lookup"><span data-stu-id="ee2d4-108">Indicates that the debug event is a first-chance exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee2d4-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ee2d4-109">Remarks</span></span>  
 <span data-ttu-id="ee2d4-110">[Icordebugprocess6::decodeevent –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) obsahuje metodu `dwFlags` parametr, který poskytuje další informace o ladění události, a jehož hodnota je závislá na Cílová architektura.</span><span class="sxs-lookup"><span data-stu-id="ee2d4-110">The [ICorDebugProcess6::DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method includes a `dwFlags` parameter that provides additional information about a debug event and whose value is dependent on the target architecture.</span></span> <span data-ttu-id="ee2d4-111">`CorDebugDecodeEventFlagsWindows` Výčtu lze použít s výjimky ladění na platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="ee2d4-111">The `CorDebugDecodeEventFlagsWindows` enumeration can be used with debug events on the Windows platform.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee2d4-112">Tento výčet je určena pro použití v .NET Native ladění pouze scénáře.</span><span class="sxs-lookup"><span data-stu-id="ee2d4-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee2d4-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ee2d4-113">Requirements</span></span>  
 <span data-ttu-id="ee2d4-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee2d4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee2d4-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ee2d4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee2d4-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee2d4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee2d4-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee2d4-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee2d4-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee2d4-118">See also</span></span>

- [<span data-ttu-id="ee2d4-119">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="ee2d4-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
