---
title: ICorDebugVariableHome Interface
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugVariableHome
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome
helpviewer_keywords:
- ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 76f2bf3b-759f-4eed-bce7-119415b25915
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 78325236ab262c474e57b0d903033990b0e85f12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54721942"
---
# <a name="icordebugvariablehome-interface"></a><span data-ttu-id="6b59a-102">ICorDebugVariableHome Interface</span><span class="sxs-lookup"><span data-stu-id="6b59a-102">ICorDebugVariableHome Interface</span></span>
<span data-ttu-id="6b59a-103">Představuje místní proměnné nebo argumentu funkce.</span><span class="sxs-lookup"><span data-stu-id="6b59a-103">Represents a local variable or argument of a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6b59a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6b59a-104">Methods</span></span>  
  
|<span data-ttu-id="6b59a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6b59a-105">Method</span></span>|<span data-ttu-id="6b59a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="6b59a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6b59a-107">GetArgumentIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="6b59a-107">GetArgumentIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getargumentindex-method.md)|<span data-ttu-id="6b59a-108">Získá index argumentu funkce.</span><span class="sxs-lookup"><span data-stu-id="6b59a-108">Gets the index of a function argument.</span></span>|  
|[<span data-ttu-id="6b59a-109">GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="6b59a-109">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getcode-method.md)|<span data-ttu-id="6b59a-110">Získá instanci "ICorDebugCode", která obsahuje tato `ICorDebugVariableHome` objektu.</span><span class="sxs-lookup"><span data-stu-id="6b59a-110">Gets the "ICorDebugCode" instance that contains this `ICorDebugVariableHome` object.</span></span>|  
|[<span data-ttu-id="6b59a-111">GetLiveRange – metoda</span><span class="sxs-lookup"><span data-stu-id="6b59a-111">GetLiveRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getliverange-method.md)|<span data-ttu-id="6b59a-112">Získá nativní rozsah nad tím, které tato proměnná je v provozu.</span><span class="sxs-lookup"><span data-stu-id="6b59a-112">Gets the native range over which this variable is live.</span></span>|  
|[<span data-ttu-id="6b59a-113">GetLocationType – metoda</span><span class="sxs-lookup"><span data-stu-id="6b59a-113">GetLocationType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md)|<span data-ttu-id="6b59a-114">Získá typ proměnné nativní umístění.</span><span class="sxs-lookup"><span data-stu-id="6b59a-114">Gets the type of the variable's native location.</span></span>|  
|[<span data-ttu-id="6b59a-115">GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="6b59a-115">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getoffset-method.md)|<span data-ttu-id="6b59a-116">Získá posun od základní registrace pro proměnnou.</span><span class="sxs-lookup"><span data-stu-id="6b59a-116">Gets the offset from the base register for a variable.</span></span>|  
|[<span data-ttu-id="6b59a-117">GetRegister – metoda</span><span class="sxs-lookup"><span data-stu-id="6b59a-117">GetRegister Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getregister-method.md)|<span data-ttu-id="6b59a-118">Získá do registru, který obsahuje proměnnou s typem umístění `VLT_REGISTER`a základní registrace pro proměnnou s typem umístění `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="6b59a-118">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>|  
|[<span data-ttu-id="6b59a-119">GetSlotIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="6b59a-119">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getslotindex-method.md)|<span data-ttu-id="6b59a-120">Získá spravované slotu index lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="6b59a-120">Gets the managed slot-index of a local variable.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6b59a-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="6b59a-121">Example</span></span>  
 <span data-ttu-id="6b59a-122">Následující fragment kódu používá [icordebugcode4 –](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md) objekt s názvem `pCode4`.</span><span class="sxs-lookup"><span data-stu-id="6b59a-122">The following code fragment uses the [ICorDebugCode4](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md) object named `pCode4`.</span></span>  
  
```cpp  
ICorDebugCode4 *pCode4 = NULL;  
pCode->QueryInterface(IID_ICorDebugCode4, &pCode4);  
  
ICorDebugVariableEnum *pVarLocEnum = NULL;  
pCode4->EnumerateVariableHomes(&pVarLocEnum);  
  
// retrieve local variables and arguments  
ULONG celt = 0;  
pVarLocEnum->GetCount(&celt);  
ICorDebugVariableHome **homes = new ICorDebugVariableHome *[celt];  
ULONG celtFetched = 0;  
pVarLocEnum->Next(celt, homes, &celtFetched);  
  
for (int i = 0; i < celtFetched; i++)  
{  
    VariableLocationType locType = VLT_INVALID;  
    homes[i].GetLocationType(&locType);  
    switch (locType)  
    {  
    case VLT_REGISTER:  
        CorDebugRegister register = 0;  
        locals[i].GetRegister(&register);  
        // now we know which register it is in  
        break;  
    case VLT_REGISTER_RELATIVE:  
        CorDebugRegister baseRegister = 0;  
        LONG offset = 0;  
        locals[i].GetRegister(&register);  
        locals[i].GetOffset(&offset);  
        // now we know the register-relative offset  
        break;  
    case VLT_INVALID:  
        // handle case where we can't access the location  
        break;  
    }  
}  
```  
  
## <a name="requirements"></a><span data-ttu-id="6b59a-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6b59a-123">Requirements</span></span>  
 <span data-ttu-id="6b59a-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b59a-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b59a-125">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b59a-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b59a-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b59a-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b59a-127">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b59a-127">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b59a-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b59a-128">See also</span></span>
- [<span data-ttu-id="6b59a-129">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="6b59a-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="6b59a-130">ICorDebugVariableHomeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6b59a-130">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)
