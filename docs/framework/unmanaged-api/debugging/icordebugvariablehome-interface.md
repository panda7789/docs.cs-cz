---
title: ICorDebugVariableHome – rozhraní
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
ms.openlocfilehash: 339a0f502b7e47f7bee82a0da92185481d909e64
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768866"
---
# <a name="icordebugvariablehome-interface"></a><span data-ttu-id="7120d-102">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7120d-102">ICorDebugVariableHome Interface</span></span>
<span data-ttu-id="7120d-103">Představuje místní proměnné nebo argumentu funkce.</span><span class="sxs-lookup"><span data-stu-id="7120d-103">Represents a local variable or argument of a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7120d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7120d-104">Methods</span></span>  
  
|<span data-ttu-id="7120d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7120d-105">Method</span></span>|<span data-ttu-id="7120d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7120d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7120d-107">GetArgumentIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="7120d-107">GetArgumentIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getargumentindex-method.md)|<span data-ttu-id="7120d-108">Získá index argumentu funkce.</span><span class="sxs-lookup"><span data-stu-id="7120d-108">Gets the index of a function argument.</span></span>|  
|[<span data-ttu-id="7120d-109">GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="7120d-109">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getcode-method.md)|<span data-ttu-id="7120d-110">Získá instanci "ICorDebugCode", která obsahuje tato `ICorDebugVariableHome` objektu.</span><span class="sxs-lookup"><span data-stu-id="7120d-110">Gets the "ICorDebugCode" instance that contains this `ICorDebugVariableHome` object.</span></span>|  
|[<span data-ttu-id="7120d-111">GetLiveRange – metoda</span><span class="sxs-lookup"><span data-stu-id="7120d-111">GetLiveRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getliverange-method.md)|<span data-ttu-id="7120d-112">Získá nativní rozsah nad tím, které tato proměnná je v provozu.</span><span class="sxs-lookup"><span data-stu-id="7120d-112">Gets the native range over which this variable is live.</span></span>|  
|[<span data-ttu-id="7120d-113">GetLocationType – metoda</span><span class="sxs-lookup"><span data-stu-id="7120d-113">GetLocationType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md)|<span data-ttu-id="7120d-114">Získá typ proměnné nativní umístění.</span><span class="sxs-lookup"><span data-stu-id="7120d-114">Gets the type of the variable's native location.</span></span>|  
|[<span data-ttu-id="7120d-115">GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="7120d-115">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getoffset-method.md)|<span data-ttu-id="7120d-116">Získá posun od základní registrace pro proměnnou.</span><span class="sxs-lookup"><span data-stu-id="7120d-116">Gets the offset from the base register for a variable.</span></span>|  
|[<span data-ttu-id="7120d-117">GetRegister – metoda</span><span class="sxs-lookup"><span data-stu-id="7120d-117">GetRegister Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getregister-method.md)|<span data-ttu-id="7120d-118">Získá do registru, který obsahuje proměnnou s typem umístění `VLT_REGISTER`a základní registrace pro proměnnou s typem umístění `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="7120d-118">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>|  
|[<span data-ttu-id="7120d-119">GetSlotIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="7120d-119">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getslotindex-method.md)|<span data-ttu-id="7120d-120">Získá spravované slotu index lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="7120d-120">Gets the managed slot-index of a local variable.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7120d-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="7120d-121">Example</span></span>  
 <span data-ttu-id="7120d-122">Následující fragment kódu používá [icordebugcode4 –](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md) objekt s názvem `pCode4`.</span><span class="sxs-lookup"><span data-stu-id="7120d-122">The following code fragment uses the [ICorDebugCode4](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md) object named `pCode4`.</span></span>  
  
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
  
## <a name="requirements"></a><span data-ttu-id="7120d-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7120d-123">Requirements</span></span>  
 <span data-ttu-id="7120d-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7120d-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7120d-125">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7120d-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7120d-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7120d-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7120d-127">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7120d-127">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7120d-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7120d-128">See also</span></span>

- [<span data-ttu-id="7120d-129">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="7120d-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="7120d-130">ICorDebugVariableHomeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7120d-130">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)
