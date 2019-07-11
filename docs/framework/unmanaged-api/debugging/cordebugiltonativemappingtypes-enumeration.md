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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7d9f5373f2b4ea216ca517813b1334b9f5c38a6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739967"
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="ac61b-102">CorDebugIlToNativeMappingTypes – výčet</span><span class="sxs-lookup"><span data-stu-id="ac61b-102">CorDebugIlToNativeMappingTypes Enumeration</span></span>
<span data-ttu-id="ac61b-103">Označuje, zda určitý rozsah nativní pokyny, reprezentovaný instancí cor_debug_il_to_native_map – struktura odpovídá do oblasti zvláštní kód.</span><span class="sxs-lookup"><span data-stu-id="ac61b-103">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac61b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac61b-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="ac61b-105">Členové</span><span class="sxs-lookup"><span data-stu-id="ac61b-105">Members</span></span>  
  
|<span data-ttu-id="ac61b-106">Člen</span><span class="sxs-lookup"><span data-stu-id="ac61b-106">Member</span></span>|<span data-ttu-id="ac61b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ac61b-107">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="ac61b-108">Rozsah nativní pokyny neodpovídá žádné speciální kód oblasti.</span><span class="sxs-lookup"><span data-stu-id="ac61b-108">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="ac61b-109">Rozsah nativní pokyny odpovídá prologu.</span><span class="sxs-lookup"><span data-stu-id="ac61b-109">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="ac61b-110">Rozsah nativní pokyny odpovídá epilogu.</span><span class="sxs-lookup"><span data-stu-id="ac61b-110">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ac61b-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ac61b-111">Requirements</span></span>  
 <span data-ttu-id="ac61b-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac61b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac61b-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ac61b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac61b-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac61b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac61b-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac61b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac61b-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ac61b-116">See also</span></span>

- [<span data-ttu-id="ac61b-117">GetILToNativeMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="ac61b-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="ac61b-118">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="ac61b-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
