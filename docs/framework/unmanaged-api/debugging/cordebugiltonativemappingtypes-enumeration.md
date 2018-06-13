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
ms.openlocfilehash: 9fec0f4f31f45847dc092808b2d47c662213e9d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402517"
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="55573-102">CorDebugIlToNativeMappingTypes – výčet</span><span class="sxs-lookup"><span data-stu-id="55573-102">CorDebugIlToNativeMappingTypes Enumeration</span></span>
<span data-ttu-id="55573-103">Určuje, jestli konkrétní rozsah nativní pokyny, reprezentována instanci cor_debug_il_to_native_map – struktura odpovídá speciální kód oblasti.</span><span class="sxs-lookup"><span data-stu-id="55573-103">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55573-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55573-104">Syntax</span></span>  
  
```  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="55573-105">Členové</span><span class="sxs-lookup"><span data-stu-id="55573-105">Members</span></span>  
  
|<span data-ttu-id="55573-106">Člen</span><span class="sxs-lookup"><span data-stu-id="55573-106">Member</span></span>|<span data-ttu-id="55573-107">Popis</span><span class="sxs-lookup"><span data-stu-id="55573-107">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="55573-108">Rozsah nativní pokyny neodpovídá žádné speciální kód oblasti.</span><span class="sxs-lookup"><span data-stu-id="55573-108">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="55573-109">Rozsah nativní pokyny odpovídá prologu.</span><span class="sxs-lookup"><span data-stu-id="55573-109">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="55573-110">Rozsah nativní pokyny odpovídá epilogu.</span><span class="sxs-lookup"><span data-stu-id="55573-110">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="55573-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="55573-111">Requirements</span></span>  
 <span data-ttu-id="55573-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55573-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55573-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="55573-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55573-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55573-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55573-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55573-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55573-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="55573-116">See Also</span></span>  
 [<span data-ttu-id="55573-117">GetILToNativeMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="55573-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)  
 [<span data-ttu-id="55573-118">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="55573-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
