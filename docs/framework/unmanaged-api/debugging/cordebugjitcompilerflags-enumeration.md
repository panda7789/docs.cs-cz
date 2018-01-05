---
title: "CorDebugJITCompilerFlags – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugJITCompilerFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugJITCompilerFlags
helpviewer_keywords: CorDebugJITCompilerFlags enumeration [.NET Framework debugging]
ms.assetid: c0774f70-5bed-45e8-9922-fdad778c4c33
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dfb78a160a7a6b9f50174fc8bb177cfd8d3f9383
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugjitcompilerflags-enumeration"></a><span data-ttu-id="78bdf-102">CorDebugJITCompilerFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="78bdf-102">CorDebugJITCompilerFlags Enumeration</span></span>
<span data-ttu-id="78bdf-103">Obsahuje hodnoty, které ovlivňují chování objektu spravovaného kompilátoru za běhu (JIT).</span><span class="sxs-lookup"><span data-stu-id="78bdf-103">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78bdf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78bdf-104">Syntax</span></span>  
  
```  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="78bdf-105">Členové</span><span class="sxs-lookup"><span data-stu-id="78bdf-105">Members</span></span>  
  
|<span data-ttu-id="78bdf-106">Člen</span><span class="sxs-lookup"><span data-stu-id="78bdf-106">Member</span></span>|<span data-ttu-id="78bdf-107">Popis</span><span class="sxs-lookup"><span data-stu-id="78bdf-107">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|<span data-ttu-id="78bdf-108">Určuje, že by měl sledovat data kompilace kompilátor a umožňuje optimalizace.</span><span class="sxs-lookup"><span data-stu-id="78bdf-108">Specifies that the compiler should track compilation data, and allows optimizations.</span></span>|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|<span data-ttu-id="78bdf-109">Určuje, že by měl kompilátor sledovat kompilace data, ale zakáže optimalizace.</span><span class="sxs-lookup"><span data-stu-id="78bdf-109">Specifies that the compiler should track compilation data, but disables optimizations.</span></span>|  
|`CORDEBUG_JIT_ENABLE_ENC`|<span data-ttu-id="78bdf-110">Určuje, že kompilátor by měl kompilace data, zakáže optimalizace, sledovat a umožňuje upravit a pokračovat technologie.</span><span class="sxs-lookup"><span data-stu-id="78bdf-110">Specifies that the compiler should track compilation data, disables optimizations, and enables Edit and Continue technologies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="78bdf-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="78bdf-111">Requirements</span></span>  
 <span data-ttu-id="78bdf-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78bdf-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78bdf-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="78bdf-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78bdf-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78bdf-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78bdf-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78bdf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78bdf-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="78bdf-116">See Also</span></span>  
 [<span data-ttu-id="78bdf-117">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="78bdf-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
