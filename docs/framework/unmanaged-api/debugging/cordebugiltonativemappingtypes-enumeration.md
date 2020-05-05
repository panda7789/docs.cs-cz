---
title: CorDebugIlToNativeMappingTypes – výčet
ms.date: 03/30/2017
api_name:
- CorDebugIlToNativeMappingTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIlToNativeMappingTypes
helpviewer_keywords:
- CorDebugIIToNativeMappingTypes enumeration [.NET Framework debugging]
ms.assetid: c35e2919-42c3-4ba0-ae28-443c35f66f93
topic_type:
- apiref
ms.openlocfilehash: 808fc70a308eff1b05aa49ea2bb89fe53377c973
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795843"
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="1fced-102">CorDebugIlToNativeMappingTypes – výčet</span><span class="sxs-lookup"><span data-stu-id="1fced-102">CorDebugIlToNativeMappingTypes Enumeration</span></span>
<span data-ttu-id="1fced-103">Označuje, zda určitý rozsah nativních instrukcí, reprezentovaných instancí COR_DEBUG_IL_TO_NATIVE_MAP struktury, odpovídá zvláštní oblasti kódu.</span><span class="sxs-lookup"><span data-stu-id="1fced-103">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fced-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1fced-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="1fced-105">Členové</span><span class="sxs-lookup"><span data-stu-id="1fced-105">Members</span></span>  
  
|<span data-ttu-id="1fced-106">Člen</span><span class="sxs-lookup"><span data-stu-id="1fced-106">Member</span></span>|<span data-ttu-id="1fced-107">Popis</span><span class="sxs-lookup"><span data-stu-id="1fced-107">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="1fced-108">Rozsah nativních instrukcí neodpovídá žádné zvláštní oblasti kódu.</span><span class="sxs-lookup"><span data-stu-id="1fced-108">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="1fced-109">Rozsah nativních instrukcí odpovídá prologu.</span><span class="sxs-lookup"><span data-stu-id="1fced-109">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="1fced-110">Rozsah nativních instrukcí odpovídá epilogu.</span><span class="sxs-lookup"><span data-stu-id="1fced-110">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1fced-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1fced-111">Requirements</span></span>  
 <span data-ttu-id="1fced-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fced-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fced-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1fced-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1fced-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1fced-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1fced-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fced-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fced-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="1fced-116">See also</span></span>

- [<span data-ttu-id="1fced-117">GetILToNativeMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="1fced-117">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="1fced-118">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="1fced-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
