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
ms.openlocfilehash: 455fd06dbdbfd5d9753f3d7270647a742751d804
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420653"
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="b1ef6-102">VariableLocationType – výčet</span><span class="sxs-lookup"><span data-stu-id="b1ef6-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="b1ef6-103">Označuje typ nativního umístění proměnné.</span><span class="sxs-lookup"><span data-stu-id="b1ef6-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1ef6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1ef6-104">Syntax</span></span>  
  
```cpp  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,
    VLT_REGISTER_RELATIVE,
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="b1ef6-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b1ef6-105">Members</span></span>  
  
|<span data-ttu-id="b1ef6-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b1ef6-106">Member</span></span>|<span data-ttu-id="b1ef6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b1ef6-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="b1ef6-108">Proměnná je v registru.</span><span class="sxs-lookup"><span data-stu-id="b1ef6-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="b1ef6-109">Proměnná je v umístění relativní paměti pro registraci.</span><span class="sxs-lookup"><span data-stu-id="b1ef6-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="b1ef6-110">Proměnná není uložena v registru nebo v umístění relativní paměti registru.</span><span class="sxs-lookup"><span data-stu-id="b1ef6-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1ef6-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1ef6-111">Remarks</span></span>  
 <span data-ttu-id="b1ef6-112">Člen `VariableLocationType` výčtu je vrácen metodou [ICorDebugVariableHome:: GetLocationType](icordebugvariablehome-getlocationtype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b1ef6-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1ef6-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b1ef6-113">Requirements</span></span>  
 <span data-ttu-id="b1ef6-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1ef6-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1ef6-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b1ef6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1ef6-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b1ef6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1ef6-117">**Verze .NET Framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1ef6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1ef6-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1ef6-118">See also</span></span>

- [<span data-ttu-id="b1ef6-119">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="b1ef6-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
