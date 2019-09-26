---
title: COR_DEBUG_IL_TO_NATIVE_MAP – struktura
ms.date: 03/30/2017
api_name:
- COR_DEBUG_IL_TO_NATIVE_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: 06f3b504-085f-4142-934a-25381fe23d4c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: babb1ace1385c241b782691f22bfb4fbb689e310
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274066"
---
# <a name="cor_debug_il_to_native_map-structure"></a><span data-ttu-id="86b34-102">COR_DEBUG_IL_TO_NATIVE_MAP – struktura</span><span class="sxs-lookup"><span data-stu-id="86b34-102">COR_DEBUG_IL_TO_NATIVE_MAP Structure</span></span>
<span data-ttu-id="86b34-103">Obsahuje posuny, které se používají k mapování kódu jazyka MSIL (Microsoft Intermediate Language) do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="86b34-103">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86b34-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86b34-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="86b34-105">Členové</span><span class="sxs-lookup"><span data-stu-id="86b34-105">Members</span></span>  
  
|<span data-ttu-id="86b34-106">Člen</span><span class="sxs-lookup"><span data-stu-id="86b34-106">Member</span></span>|<span data-ttu-id="86b34-107">Popis</span><span class="sxs-lookup"><span data-stu-id="86b34-107">Description</span></span>|  
|------------|-----------------|  
|`ilOffset`|<span data-ttu-id="86b34-108">Posun kódu jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="86b34-108">The offset of the MSIL code.</span></span>|  
|`nativeStartOffset`|<span data-ttu-id="86b34-109">Posun začátku nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="86b34-109">The offset of the start of the native code.</span></span>|  
|`nativeEndOffset`|<span data-ttu-id="86b34-110">Posun konce nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="86b34-110">The offset of the end of the native code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="86b34-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="86b34-111">Requirements</span></span>  
 <span data-ttu-id="86b34-112">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86b34-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86b34-113">**Hlaviček** CorProf. idl, CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="86b34-113">**Header:** CorProf.idl, CorDebug.idl</span></span>  
  
 <span data-ttu-id="86b34-114">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86b34-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86b34-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86b34-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86b34-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="86b34-116">See also</span></span>

- [<span data-ttu-id="86b34-117">GetILToNativeMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="86b34-117">GetILToNativeMapping Method</span></span>](../profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="86b34-118">GetILToNativeMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="86b34-118">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="86b34-119">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="86b34-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="86b34-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="86b34-120">Debugging</span></span>](index.md)
