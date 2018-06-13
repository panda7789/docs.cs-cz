---
title: ICorDebugVariableHome rozhraní
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
ms.openlocfilehash: ae11cdbbdb0fa63d1b903d18aff133344fd17f2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422530"
---
# <a name="icordebugvariablehome-interface"></a><span data-ttu-id="55525-102">ICorDebugVariableHome rozhraní</span><span class="sxs-lookup"><span data-stu-id="55525-102">ICorDebugVariableHome Interface</span></span>
<span data-ttu-id="55525-103">Představuje místní proměnné nebo argument funkce.</span><span class="sxs-lookup"><span data-stu-id="55525-103">Represents a local variable or argument of a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="55525-104">Metody</span><span class="sxs-lookup"><span data-stu-id="55525-104">Methods</span></span>  
  
|<span data-ttu-id="55525-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="55525-105">Method</span></span>|<span data-ttu-id="55525-106">Popis</span><span class="sxs-lookup"><span data-stu-id="55525-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="55525-107">GetArgumentIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="55525-107">GetArgumentIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getargumentindex-method.md)|<span data-ttu-id="55525-108">Získá index argument funkce.</span><span class="sxs-lookup"><span data-stu-id="55525-108">Gets the index of a function argument.</span></span>|  
|[<span data-ttu-id="55525-109">GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="55525-109">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getcode-method.md)|<span data-ttu-id="55525-110">Získá instanci "ICorDebugCode", která obsahuje toto `ICorDebugVariableHome` objektu.</span><span class="sxs-lookup"><span data-stu-id="55525-110">Gets the "ICorDebugCode" instance that contains this `ICorDebugVariableHome` object.</span></span>|  
|[<span data-ttu-id="55525-111">GetLiveRange – metoda</span><span class="sxs-lookup"><span data-stu-id="55525-111">GetLiveRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getliverange-method.md)|<span data-ttu-id="55525-112">Získá nativní rozsahu, za které je tato proměnná za provozu.</span><span class="sxs-lookup"><span data-stu-id="55525-112">Gets the native range over which this variable is live.</span></span>|  
|[<span data-ttu-id="55525-113">GetLocationType – metoda</span><span class="sxs-lookup"><span data-stu-id="55525-113">GetLocationType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md)|<span data-ttu-id="55525-114">Získá typ proměnné nativní umístění.</span><span class="sxs-lookup"><span data-stu-id="55525-114">Gets the type of the variable's native location.</span></span>|  
|[<span data-ttu-id="55525-115">GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="55525-115">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getoffset-method.md)|<span data-ttu-id="55525-116">Získá posun od základní registrace proměnné.</span><span class="sxs-lookup"><span data-stu-id="55525-116">Gets the offset from the base register for a variable.</span></span>|  
|[<span data-ttu-id="55525-117">GetRegister – metoda</span><span class="sxs-lookup"><span data-stu-id="55525-117">GetRegister Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getregister-method.md)|<span data-ttu-id="55525-118">Získá registrace, který obsahuje proměnnou s typem umístění `VLT_REGISTER`a základní registrace pro proměnné s typem umístění `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="55525-118">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>|  
|[<span data-ttu-id="55525-119">GetSlotIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="55525-119">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getslotindex-method.md)|<span data-ttu-id="55525-120">Získá spravovaného indexu slotu místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="55525-120">Gets the managed slot-index of a local variable.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="55525-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="55525-121">Example</span></span>  
 <span data-ttu-id="55525-122">Používá následující fragment kódu [ICorDebugCode4](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md) objekt s názvem `pCode4`.</span><span class="sxs-lookup"><span data-stu-id="55525-122">The following code fragment uses the [ICorDebugCode4](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md) object named `pCode4`.</span></span>  
  
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
  
## <a name="requirements"></a><span data-ttu-id="55525-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="55525-123">Requirements</span></span>  
 <span data-ttu-id="55525-124">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55525-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55525-125">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="55525-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55525-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55525-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55525-127">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55525-127">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55525-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="55525-128">See Also</span></span>  
 [<span data-ttu-id="55525-129">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="55525-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="55525-130">ICorDebugVariableHomeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="55525-130">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)
