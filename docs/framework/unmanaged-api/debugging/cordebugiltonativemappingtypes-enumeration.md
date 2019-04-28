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
ms.openlocfilehash: 2f62707fb1e52a96cf3f131e9c11fee82ab03f4e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651763"
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="c4a06-102">CorDebugIlToNativeMappingTypes – výčet</span><span class="sxs-lookup"><span data-stu-id="c4a06-102">CorDebugIlToNativeMappingTypes Enumeration</span></span>
<span data-ttu-id="c4a06-103">Označuje, zda určitý rozsah nativní pokyny, reprezentovaný instancí cor_debug_il_to_native_map – struktura odpovídá do oblasti zvláštní kód.</span><span class="sxs-lookup"><span data-stu-id="c4a06-103">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4a06-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4a06-104">Syntax</span></span>  
  
```  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="c4a06-105">Členové</span><span class="sxs-lookup"><span data-stu-id="c4a06-105">Members</span></span>  
  
|<span data-ttu-id="c4a06-106">Člen</span><span class="sxs-lookup"><span data-stu-id="c4a06-106">Member</span></span>|<span data-ttu-id="c4a06-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c4a06-107">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="c4a06-108">Rozsah nativní pokyny neodpovídá žádné speciální kód oblasti.</span><span class="sxs-lookup"><span data-stu-id="c4a06-108">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="c4a06-109">Rozsah nativní pokyny odpovídá prologu.</span><span class="sxs-lookup"><span data-stu-id="c4a06-109">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="c4a06-110">Rozsah nativní pokyny odpovídá epilogu.</span><span class="sxs-lookup"><span data-stu-id="c4a06-110">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c4a06-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c4a06-111">Requirements</span></span>  
 <span data-ttu-id="c4a06-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4a06-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4a06-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4a06-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4a06-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4a06-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4a06-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4a06-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4a06-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4a06-116">See also</span></span>

- [<span data-ttu-id="c4a06-117">GetILToNativeMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="c4a06-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="c4a06-118">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="c4a06-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
