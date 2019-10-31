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
ms.openlocfilehash: 861d5daa481132d3d6527e8d5fbccfab6436c5fe
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139119"
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="42f4b-102">VariableLocationType – výčet</span><span class="sxs-lookup"><span data-stu-id="42f4b-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="42f4b-103">Označuje typ nativního umístění proměnné.</span><span class="sxs-lookup"><span data-stu-id="42f4b-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42f4b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42f4b-104">Syntax</span></span>  
  
```cpp  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,               
    VLT_REGISTER_RELATIVE,      
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="42f4b-105">Členové</span><span class="sxs-lookup"><span data-stu-id="42f4b-105">Members</span></span>  
  
|<span data-ttu-id="42f4b-106">Člen</span><span class="sxs-lookup"><span data-stu-id="42f4b-106">Member</span></span>|<span data-ttu-id="42f4b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="42f4b-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="42f4b-108">Proměnná je v registru.</span><span class="sxs-lookup"><span data-stu-id="42f4b-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="42f4b-109">Proměnná je v umístění relativní paměti pro registraci.</span><span class="sxs-lookup"><span data-stu-id="42f4b-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="42f4b-110">Proměnná není uložena v registru nebo v umístění relativní paměti registru.</span><span class="sxs-lookup"><span data-stu-id="42f4b-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42f4b-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="42f4b-111">Remarks</span></span>  
 <span data-ttu-id="42f4b-112">Člen `VariableLocationType` výčtu je vrácen metodou [ICorDebugVariableHome:: GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="42f4b-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42f4b-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="42f4b-113">Requirements</span></span>  
 <span data-ttu-id="42f4b-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42f4b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42f4b-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="42f4b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42f4b-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="42f4b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42f4b-117">**Verze .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42f4b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42f4b-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="42f4b-118">See also</span></span>

- [<span data-ttu-id="42f4b-119">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="42f4b-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
