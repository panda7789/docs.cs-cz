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
ms.openlocfilehash: bab7da5855eaf562e55738b489ebf6f62dc45d04
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740227"
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a><span data-ttu-id="62ab9-102">Výčet CorDebugDecodeEventFlagsWindows</span><span class="sxs-lookup"><span data-stu-id="62ab9-102">CorDebugDecodeEventFlagsWindows Enumeration</span></span>
<span data-ttu-id="62ab9-103">Poskytuje další informace o ladění událostí na platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="62ab9-103">Provides additional information about debug events on the Windows platform.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62ab9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62ab9-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a><span data-ttu-id="62ab9-105">Členové</span><span class="sxs-lookup"><span data-stu-id="62ab9-105">Members</span></span>  
  
|<span data-ttu-id="62ab9-106">Člen</span><span class="sxs-lookup"><span data-stu-id="62ab9-106">Member</span></span>|<span data-ttu-id="62ab9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="62ab9-107">Description</span></span>|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|<span data-ttu-id="62ab9-108">Označuje, že událost ladění je výjimka první příležitosti.</span><span class="sxs-lookup"><span data-stu-id="62ab9-108">Indicates that the debug event is a first-chance exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62ab9-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="62ab9-109">Remarks</span></span>  
 <span data-ttu-id="62ab9-110">[Icordebugprocess6::decodeevent –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) obsahuje metodu `dwFlags` parametr, který poskytuje další informace o ladění události, a jehož hodnota je závislá na Cílová architektura.</span><span class="sxs-lookup"><span data-stu-id="62ab9-110">The [ICorDebugProcess6::DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method includes a `dwFlags` parameter that provides additional information about a debug event and whose value is dependent on the target architecture.</span></span> <span data-ttu-id="62ab9-111">`CorDebugDecodeEventFlagsWindows` Výčtu lze použít s výjimky ladění na platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="62ab9-111">The `CorDebugDecodeEventFlagsWindows` enumeration can be used with debug events on the Windows platform.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="62ab9-112">Tento výčet je určena pro použití v .NET Native ladění pouze scénáře.</span><span class="sxs-lookup"><span data-stu-id="62ab9-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62ab9-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="62ab9-113">Requirements</span></span>  
 <span data-ttu-id="62ab9-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62ab9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62ab9-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="62ab9-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62ab9-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62ab9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62ab9-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62ab9-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62ab9-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="62ab9-118">See also</span></span>

- [<span data-ttu-id="62ab9-119">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="62ab9-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
