---
title: CorDebugJITCompilerFlagsDeprecated – výčet
ms.date: 03/30/2017
api_name:
- CorDebugJITCompilerFlagsDeprecated
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugJITCompilerFlagsDeprecated
helpviewer_keywords:
- CorDebugJITCompilerFlagsDeprecated enumeration [.NET Framework debugging]
ms.assetid: af15e2ca-6be1-472b-bd36-03644a1e3ddd
topic_type:
- apiref
ms.openlocfilehash: 7b8a726cffcc00d7371675192a209b2d8e9db94d
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795778"
---
# <a name="cordebugjitcompilerflagsdeprecated-enumeration"></a><span data-ttu-id="4bbf0-102">CorDebugJITCompilerFlagsDeprecated – výčet</span><span class="sxs-lookup"><span data-stu-id="4bbf0-102">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>
<span data-ttu-id="4bbf0-103">Tento výčet je zastaralý.</span><span class="sxs-lookup"><span data-stu-id="4bbf0-103">This enumeration is obsolete.</span></span> <span data-ttu-id="4bbf0-104">Místo toho `CORDEBUG_JIT_DEFAULT` použijte člen výčtu [CorDebugJITCompilerFlags –](cordebugjitcompilerflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="4bbf0-104">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bbf0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4bbf0-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugJITCompilerFlagsDeprecated {  
    CORDEBUG_JIT_TRACK_DEBUG_INFO  = 0x1  
} CorDebugJITCompilerFlagsDeprecated;  
```  
  
## <a name="members"></a><span data-ttu-id="4bbf0-106">Členové</span><span class="sxs-lookup"><span data-stu-id="4bbf0-106">Members</span></span>  
  
|<span data-ttu-id="4bbf0-107">Člen</span><span class="sxs-lookup"><span data-stu-id="4bbf0-107">Member</span></span>|<span data-ttu-id="4bbf0-108">Popis</span><span class="sxs-lookup"><span data-stu-id="4bbf0-108">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_TRACK_DEBUG_INFO`|<span data-ttu-id="4bbf0-109">Místo toho použijte `CORDEBUG_JIT_DEFAULT`.</span><span class="sxs-lookup"><span data-stu-id="4bbf0-109">Use `CORDEBUG_JIT_DEFAULT` instead.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4bbf0-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4bbf0-110">Requirements</span></span>  
 <span data-ttu-id="4bbf0-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bbf0-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bbf0-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4bbf0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4bbf0-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4bbf0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4bbf0-114">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="4bbf0-114">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bbf0-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="4bbf0-115">See also</span></span>

- [<span data-ttu-id="4bbf0-116">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="4bbf0-116">Debugging Enumerations</span></span>](debugging-enumerations.md)
