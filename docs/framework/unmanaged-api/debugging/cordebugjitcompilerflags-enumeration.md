---
title: CorDebugJITCompilerFlags – výčet
ms.date: 03/30/2017
api_name:
- CorDebugJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugJITCompilerFlags
helpviewer_keywords:
- CorDebugJITCompilerFlags enumeration [.NET Framework debugging]
ms.assetid: c0774f70-5bed-45e8-9922-fdad778c4c33
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 39bc1316bb7d8e2aba3390499437aadf263dac07
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739846"
---
# <a name="cordebugjitcompilerflags-enumeration"></a><span data-ttu-id="8fa15-102">CorDebugJITCompilerFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="8fa15-102">CorDebugJITCompilerFlags Enumeration</span></span>
<span data-ttu-id="8fa15-103">Obsahuje hodnoty, které ovlivňují chování spravované kompilátor just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="8fa15-103">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fa15-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8fa15-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="8fa15-105">Členové</span><span class="sxs-lookup"><span data-stu-id="8fa15-105">Members</span></span>  
  
|<span data-ttu-id="8fa15-106">Člen</span><span class="sxs-lookup"><span data-stu-id="8fa15-106">Member</span></span>|<span data-ttu-id="8fa15-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8fa15-107">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|<span data-ttu-id="8fa15-108">Určuje, že kompilátor by měl sledovat kompilace data a umožňuje optimalizace.</span><span class="sxs-lookup"><span data-stu-id="8fa15-108">Specifies that the compiler should track compilation data, and allows optimizations.</span></span>|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|<span data-ttu-id="8fa15-109">Určuje, že kompilátor by měl sledovat data kompilace, ale zakáže optimalizace.</span><span class="sxs-lookup"><span data-stu-id="8fa15-109">Specifies that the compiler should track compilation data, but disables optimizations.</span></span>|  
|`CORDEBUG_JIT_ENABLE_ENC`|<span data-ttu-id="8fa15-110">Určuje, že kompilátor by měl sledovat data kompilace, zakáže optimalizace, a umožňuje upravit a pokračovat technologie.</span><span class="sxs-lookup"><span data-stu-id="8fa15-110">Specifies that the compiler should track compilation data, disables optimizations, and enables Edit and Continue technologies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8fa15-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8fa15-111">Requirements</span></span>  
 <span data-ttu-id="8fa15-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fa15-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fa15-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8fa15-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8fa15-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8fa15-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8fa15-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fa15-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fa15-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8fa15-116">See also</span></span>

- [<span data-ttu-id="8fa15-117">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="8fa15-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
