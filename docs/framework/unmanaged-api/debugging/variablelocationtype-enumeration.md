---
title: VariableLocationType – výčet
ms.date: 03/30/2017
api_name:
- VariableLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- VariableLocationType
helpviewer_keywords:
- VariableLocationType enumeration [.NET Framework debugging]
ms.assetid: 8635ee3a-c84b-4626-876c-416bee54f787
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 392254efcd099aca60e58b3cc0bc61ca85aa2c66
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099947"
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="16664-102">VariableLocationType – výčet</span><span class="sxs-lookup"><span data-stu-id="16664-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="16664-103">Určuje umístění nativní typ proměnné.</span><span class="sxs-lookup"><span data-stu-id="16664-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16664-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16664-104">Syntax</span></span>  
  
```  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,               
    VLT_REGISTER_RELATIVE,      
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="16664-105">Členové</span><span class="sxs-lookup"><span data-stu-id="16664-105">Members</span></span>  
  
|<span data-ttu-id="16664-106">Člen</span><span class="sxs-lookup"><span data-stu-id="16664-106">Member</span></span>|<span data-ttu-id="16664-107">Popis</span><span class="sxs-lookup"><span data-stu-id="16664-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="16664-108">Proměnná je v registru.</span><span class="sxs-lookup"><span data-stu-id="16664-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="16664-109">Proměnná se nachází v umístění paměti register relativní.</span><span class="sxs-lookup"><span data-stu-id="16664-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="16664-110">Proměnná není uložen v registru nebo paměti register relativní umístění.</span><span class="sxs-lookup"><span data-stu-id="16664-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16664-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="16664-111">Remarks</span></span>  
 <span data-ttu-id="16664-112">Člen `VariableLocationType` výčtu je vrácený [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="16664-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16664-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="16664-113">Requirements</span></span>  
 <span data-ttu-id="16664-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16664-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16664-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="16664-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16664-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16664-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="16664-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="16664-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="16664-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="16664-118">See also</span></span>

- [<span data-ttu-id="16664-119">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="16664-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
