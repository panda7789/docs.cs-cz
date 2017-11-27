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
ms.openlocfilehash: d7eb8421dcd68c67536e0de038f7038500556c47
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugjitcompilerflags-enumeration"></a><span data-ttu-id="bee3b-102">CorDebugJITCompilerFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="bee3b-102">CorDebugJITCompilerFlags Enumeration</span></span>
<span data-ttu-id="bee3b-103">Obsahuje hodnoty, které ovlivňují chování objektu spravovaného kompilátoru za běhu (JIT).</span><span class="sxs-lookup"><span data-stu-id="bee3b-103">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bee3b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bee3b-104">Syntax</span></span>  
  
```  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="bee3b-105">Členové</span><span class="sxs-lookup"><span data-stu-id="bee3b-105">Members</span></span>  
  
|<span data-ttu-id="bee3b-106">Člen</span><span class="sxs-lookup"><span data-stu-id="bee3b-106">Member</span></span>|<span data-ttu-id="bee3b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="bee3b-107">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|<span data-ttu-id="bee3b-108">Určuje, že by měl sledovat data kompilace kompilátor a umožňuje optimalizace.</span><span class="sxs-lookup"><span data-stu-id="bee3b-108">Specifies that the compiler should track compilation data, and allows optimizations.</span></span>|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|<span data-ttu-id="bee3b-109">Určuje, že by měl kompilátor sledovat kompilace data, ale zakáže optimalizace.</span><span class="sxs-lookup"><span data-stu-id="bee3b-109">Specifies that the compiler should track compilation data, but disables optimizations.</span></span>|  
|`CORDEBUG_JIT_ENABLE_ENC`|<span data-ttu-id="bee3b-110">Určuje, že kompilátor by měl kompilace data, zakáže optimalizace, sledovat a umožňuje upravit a pokračovat technologie.</span><span class="sxs-lookup"><span data-stu-id="bee3b-110">Specifies that the compiler should track compilation data, disables optimizations, and enables Edit and Continue technologies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bee3b-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bee3b-111">Requirements</span></span>  
 <span data-ttu-id="bee3b-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bee3b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bee3b-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bee3b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bee3b-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bee3b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bee3b-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bee3b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bee3b-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="bee3b-116">See Also</span></span>  
 [<span data-ttu-id="bee3b-117">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="bee3b-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
