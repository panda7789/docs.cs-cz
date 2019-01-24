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
ms.openlocfilehash: 56d4255b06f1317c87685737e4ee4021c37a77f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555008"
---
# <a name="cordebugiltonativemap-structure"></a><span data-ttu-id="b41cd-102">COR_DEBUG_IL_TO_NATIVE_MAP – struktura</span><span class="sxs-lookup"><span data-stu-id="b41cd-102">COR_DEBUG_IL_TO_NATIVE_MAP Structure</span></span>
<span data-ttu-id="b41cd-103">Obsahuje posuny, které se používají k mapování kód Microsoft intermediate language (MSIL) do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="b41cd-103">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b41cd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b41cd-104">Syntax</span></span>  
  
```  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="b41cd-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b41cd-105">Members</span></span>  
  
|<span data-ttu-id="b41cd-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b41cd-106">Member</span></span>|<span data-ttu-id="b41cd-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b41cd-107">Description</span></span>|  
|------------|-----------------|  
|`ilOffset`|<span data-ttu-id="b41cd-108">Posun kód jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="b41cd-108">The offset of the MSIL code.</span></span>|  
|`nativeStartOffset`|<span data-ttu-id="b41cd-109">Posun počáteční nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="b41cd-109">The offset of the start of the native code.</span></span>|  
|`nativeEndOffset`|<span data-ttu-id="b41cd-110">Posun konec nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="b41cd-110">The offset of the end of the native code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b41cd-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b41cd-111">Requirements</span></span>  
 <span data-ttu-id="b41cd-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b41cd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b41cd-113">**Záhlaví:** CorProf.idl, CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="b41cd-113">**Header:** CorProf.idl, CorDebug.idl</span></span>  
  
 <span data-ttu-id="b41cd-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b41cd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b41cd-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b41cd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b41cd-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b41cd-116">See also</span></span>
- [<span data-ttu-id="b41cd-117">GetILToNativeMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="b41cd-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="b41cd-118">GetILToNativeMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="b41cd-118">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="b41cd-119">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="b41cd-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="b41cd-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="b41cd-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
