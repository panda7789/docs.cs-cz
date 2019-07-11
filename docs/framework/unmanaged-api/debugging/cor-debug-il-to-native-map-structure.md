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
ms.openlocfilehash: 238e59978bd084379fe6c0576107d674812bce8d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740781"
---
# <a name="cordebugiltonativemap-structure"></a><span data-ttu-id="73b16-102">COR_DEBUG_IL_TO_NATIVE_MAP – struktura</span><span class="sxs-lookup"><span data-stu-id="73b16-102">COR_DEBUG_IL_TO_NATIVE_MAP Structure</span></span>
<span data-ttu-id="73b16-103">Obsahuje posuny, které se používají k mapování kód Microsoft intermediate language (MSIL) do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="73b16-103">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73b16-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73b16-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="73b16-105">Členové</span><span class="sxs-lookup"><span data-stu-id="73b16-105">Members</span></span>  
  
|<span data-ttu-id="73b16-106">Člen</span><span class="sxs-lookup"><span data-stu-id="73b16-106">Member</span></span>|<span data-ttu-id="73b16-107">Popis</span><span class="sxs-lookup"><span data-stu-id="73b16-107">Description</span></span>|  
|------------|-----------------|  
|`ilOffset`|<span data-ttu-id="73b16-108">Posun kód jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="73b16-108">The offset of the MSIL code.</span></span>|  
|`nativeStartOffset`|<span data-ttu-id="73b16-109">Posun počáteční nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="73b16-109">The offset of the start of the native code.</span></span>|  
|`nativeEndOffset`|<span data-ttu-id="73b16-110">Posun konec nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="73b16-110">The offset of the end of the native code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="73b16-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="73b16-111">Requirements</span></span>  
 <span data-ttu-id="73b16-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73b16-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73b16-113">**Záhlaví:** CorProf.idl, CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="73b16-113">**Header:** CorProf.idl, CorDebug.idl</span></span>  
  
 <span data-ttu-id="73b16-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73b16-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73b16-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73b16-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73b16-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73b16-116">See also</span></span>

- [<span data-ttu-id="73b16-117">GetILToNativeMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="73b16-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="73b16-118">GetILToNativeMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="73b16-118">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="73b16-119">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="73b16-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="73b16-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="73b16-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
