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
ms.openlocfilehash: e2fa5d5a998f51e0e90cfde22b40ec12f278307b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178365"
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="3f016-102">VariableLocationType – výčet</span><span class="sxs-lookup"><span data-stu-id="3f016-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="3f016-103">Označuje nativní typ umístění proměnné.</span><span class="sxs-lookup"><span data-stu-id="3f016-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f016-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f016-104">Syntax</span></span>  
  
```cpp  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,
    VLT_REGISTER_RELATIVE,
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="3f016-105">Členové</span><span class="sxs-lookup"><span data-stu-id="3f016-105">Members</span></span>  
  
|<span data-ttu-id="3f016-106">Člen</span><span class="sxs-lookup"><span data-stu-id="3f016-106">Member</span></span>|<span data-ttu-id="3f016-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3f016-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="3f016-108">Proměnná je v registru.</span><span class="sxs-lookup"><span data-stu-id="3f016-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="3f016-109">Proměnná je v umístění paměti relativní registru.</span><span class="sxs-lookup"><span data-stu-id="3f016-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="3f016-110">Proměnná není uložena v registru nebo umístění paměti relativní k registru.</span><span class="sxs-lookup"><span data-stu-id="3f016-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f016-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3f016-111">Remarks</span></span>  
 <span data-ttu-id="3f016-112">Člen výčtu `VariableLocationType` je vrácena [ICorDebugVariableHome::GetLocationType](icordebugvariablehome-getlocationtype-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="3f016-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f016-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3f016-113">Requirements</span></span>  
 <span data-ttu-id="3f016-114">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f016-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f016-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3f016-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f016-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f016-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f016-117">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f016-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f016-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f016-118">See also</span></span>

- [<span data-ttu-id="3f016-119">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="3f016-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
