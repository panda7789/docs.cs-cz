---
title: "VariableLocationType – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: VariableLocationType
api_location: mscordbi.dll
api_type: COM
f1_keywords: VariableLocationType
helpviewer_keywords: VariableLocationType enumeration [.NET Framework debugging]
ms.assetid: 8635ee3a-c84b-4626-876c-416bee54f787
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ea476ef32b807823108aa2836778da576618214
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="43dc6-102">VariableLocationType – výčet</span><span class="sxs-lookup"><span data-stu-id="43dc6-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="43dc6-103">Označuje typ nativní umístění proměnné.</span><span class="sxs-lookup"><span data-stu-id="43dc6-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43dc6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43dc6-104">Syntax</span></span>  
  
```  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,               
    VLT_REGISTER_RELATIVE,      
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="43dc6-105">Členové</span><span class="sxs-lookup"><span data-stu-id="43dc6-105">Members</span></span>  
  
|<span data-ttu-id="43dc6-106">Člen</span><span class="sxs-lookup"><span data-stu-id="43dc6-106">Member</span></span>|<span data-ttu-id="43dc6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="43dc6-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="43dc6-108">Proměnná je do registru.</span><span class="sxs-lookup"><span data-stu-id="43dc6-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="43dc6-109">Proměnná je v paměti register relativní umístění.</span><span class="sxs-lookup"><span data-stu-id="43dc6-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="43dc6-110">Proměnná nejsou uložené v registru nebo paměti register relativní umístění.</span><span class="sxs-lookup"><span data-stu-id="43dc6-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43dc6-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="43dc6-111">Remarks</span></span>  
 <span data-ttu-id="43dc6-112">Členem `VariableLocationType` výčtu je vrácený [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="43dc6-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43dc6-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="43dc6-113">Requirements</span></span>  
 <span data-ttu-id="43dc6-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43dc6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43dc6-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="43dc6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="43dc6-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43dc6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43dc6-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43dc6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43dc6-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="43dc6-118">See Also</span></span>  
 [<span data-ttu-id="43dc6-119">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="43dc6-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
