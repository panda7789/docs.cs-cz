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
ms.openlocfilehash: 8be8ce36b557831bc0997dd1c69abb924390d051
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795817"
---
# <a name="cordebugjitcompilerflags-enumeration"></a><span data-ttu-id="799e0-102">CorDebugJITCompilerFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="799e0-102">CorDebugJITCompilerFlags Enumeration</span></span>
<span data-ttu-id="799e0-103">Obsahuje hodnoty, které mají vliv na chování spravovaného kompilátoru JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="799e0-103">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="799e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="799e0-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="799e0-105">Členové</span><span class="sxs-lookup"><span data-stu-id="799e0-105">Members</span></span>  
  
|<span data-ttu-id="799e0-106">Člen</span><span class="sxs-lookup"><span data-stu-id="799e0-106">Member</span></span>|<span data-ttu-id="799e0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="799e0-107">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|<span data-ttu-id="799e0-108">Určuje, že má kompilátor sledovat data kompilace a umožňuje optimalizace.</span><span class="sxs-lookup"><span data-stu-id="799e0-108">Specifies that the compiler should track compilation data, and allows optimizations.</span></span>|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|<span data-ttu-id="799e0-109">Určuje, že má kompilátor sledovat data kompilace, ale zakáže optimalizace.</span><span class="sxs-lookup"><span data-stu-id="799e0-109">Specifies that the compiler should track compilation data, but disables optimizations.</span></span>|  
|`CORDEBUG_JIT_ENABLE_ENC`|<span data-ttu-id="799e0-110">Určuje, že má kompilátor sledovat data kompilace, zakázat optimalizace a povolit technologie pro úpravy a pokračování.</span><span class="sxs-lookup"><span data-stu-id="799e0-110">Specifies that the compiler should track compilation data, disables optimizations, and enables Edit and Continue technologies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="799e0-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="799e0-111">Requirements</span></span>  
 <span data-ttu-id="799e0-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="799e0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="799e0-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="799e0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="799e0-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="799e0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="799e0-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="799e0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="799e0-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="799e0-116">See also</span></span>

- [<span data-ttu-id="799e0-117">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="799e0-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
