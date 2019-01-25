---
title: VariableLocationType Enumeration
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
ms.openlocfilehash: dd1a622faa095836a3d5c22c7a18084482074c2c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653213"
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="237b3-102">VariableLocationType Enumeration</span><span class="sxs-lookup"><span data-stu-id="237b3-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="237b3-103">Určuje umístění nativní typ proměnné.</span><span class="sxs-lookup"><span data-stu-id="237b3-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="237b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="237b3-104">Syntax</span></span>  
  
```  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,               
    VLT_REGISTER_RELATIVE,      
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="237b3-105">Členové</span><span class="sxs-lookup"><span data-stu-id="237b3-105">Members</span></span>  
  
|<span data-ttu-id="237b3-106">Člen</span><span class="sxs-lookup"><span data-stu-id="237b3-106">Member</span></span>|<span data-ttu-id="237b3-107">Popis</span><span class="sxs-lookup"><span data-stu-id="237b3-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="237b3-108">Proměnná je v registru.</span><span class="sxs-lookup"><span data-stu-id="237b3-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="237b3-109">Proměnná se nachází v umístění paměti register relativní.</span><span class="sxs-lookup"><span data-stu-id="237b3-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="237b3-110">Proměnná není uložen v registru nebo paměti register relativní umístění.</span><span class="sxs-lookup"><span data-stu-id="237b3-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="237b3-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="237b3-111">Remarks</span></span>  
 <span data-ttu-id="237b3-112">Člen `VariableLocationType` výčtu je vrácený [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="237b3-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="237b3-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="237b3-113">Requirements</span></span>  
 <span data-ttu-id="237b3-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="237b3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="237b3-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="237b3-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="237b3-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="237b3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="237b3-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="237b3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="237b3-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="237b3-118">See also</span></span>
- [<span data-ttu-id="237b3-119">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="237b3-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
