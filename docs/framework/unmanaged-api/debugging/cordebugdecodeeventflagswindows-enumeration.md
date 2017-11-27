---
title: "Výčet CorDebugDecodeEventFlagsWindows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugDecodeEventFlagsWindows
api_location: mscordbi.dll
api_type: COM
ms.assetid: aa6cf962-30ae-4cfd-8895-826deeb46a54
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: facde76ec24d90795de7dfb70bfe5772a6f21531
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a><span data-ttu-id="6c2dd-102">Výčet CorDebugDecodeEventFlagsWindows</span><span class="sxs-lookup"><span data-stu-id="6c2dd-102">CorDebugDecodeEventFlagsWindows Enumeration</span></span>
<span data-ttu-id="6c2dd-103">Poskytuje další informace o ladění událostí na platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="6c2dd-103">Provides additional information about debug events on the Windows platform.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c2dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c2dd-104">Syntax</span></span>  
  
```  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a><span data-ttu-id="6c2dd-105">Členové</span><span class="sxs-lookup"><span data-stu-id="6c2dd-105">Members</span></span>  
  
|<span data-ttu-id="6c2dd-106">Člen</span><span class="sxs-lookup"><span data-stu-id="6c2dd-106">Member</span></span>|<span data-ttu-id="6c2dd-107">Popis</span><span class="sxs-lookup"><span data-stu-id="6c2dd-107">Description</span></span>|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|<span data-ttu-id="6c2dd-108">Označuje, že událost ladění je první odpovídající výjimce.</span><span class="sxs-lookup"><span data-stu-id="6c2dd-108">Indicates that the debug event is a first-chance exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c2dd-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6c2dd-109">Remarks</span></span>  
 <span data-ttu-id="6c2dd-110">[Icordebugprocess6::decodeevent –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) metoda zahrnuje `dwFlags` parametr, který obsahuje další informace o ladění událostí a jehož hodnota je závislá na cílové architektury.</span><span class="sxs-lookup"><span data-stu-id="6c2dd-110">The [ICorDebugProcess6::DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method includes a `dwFlags` parameter that provides additional information about a debug event and whose value is dependent on the target architecture.</span></span> <span data-ttu-id="6c2dd-111">`CorDebugDecodeEventFlagsWindows` Výčtu lze použít s událostmi ladění na platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="6c2dd-111">The `CorDebugDecodeEventFlagsWindows` enumeration can be used with debug events on the Windows platform.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c2dd-112">Tento výčet je určena pro použití v rozhraní .NET nativní ladění pouze scénáře.</span><span class="sxs-lookup"><span data-stu-id="6c2dd-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c2dd-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6c2dd-113">Requirements</span></span>  
 <span data-ttu-id="6c2dd-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c2dd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c2dd-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c2dd-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c2dd-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c2dd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c2dd-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c2dd-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c2dd-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c2dd-118">See Also</span></span>  
 [<span data-ttu-id="6c2dd-119">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="6c2dd-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
