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
ms.openlocfilehash: c347346c9157fea843527c662e26ffcfba22ace4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790959"
---
# <a name="icordebugvariablehome-interface"></a><span data-ttu-id="86c76-102">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="86c76-102">ICorDebugVariableHome Interface</span></span>
<span data-ttu-id="86c76-103">Představuje místní proměnnou nebo argument funkce.</span><span class="sxs-lookup"><span data-stu-id="86c76-103">Represents a local variable or argument of a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="86c76-104">Metody</span><span class="sxs-lookup"><span data-stu-id="86c76-104">Methods</span></span>  
  
|<span data-ttu-id="86c76-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="86c76-105">Method</span></span>|<span data-ttu-id="86c76-106">Popis</span><span class="sxs-lookup"><span data-stu-id="86c76-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="86c76-107">GetArgumentIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="86c76-107">GetArgumentIndex Method</span></span>](icordebugvariablehome-getargumentindex-method.md)|<span data-ttu-id="86c76-108">Získá index argumentu funkce.</span><span class="sxs-lookup"><span data-stu-id="86c76-108">Gets the index of a function argument.</span></span>|  
|[<span data-ttu-id="86c76-109">GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="86c76-109">GetCode Method</span></span>](icordebugvariablehome-getcode-method.md)|<span data-ttu-id="86c76-110">Získá instanci "ICorDebugCode", která obsahuje tento objekt `ICorDebugVariableHome`.</span><span class="sxs-lookup"><span data-stu-id="86c76-110">Gets the "ICorDebugCode" instance that contains this `ICorDebugVariableHome` object.</span></span>|  
|[<span data-ttu-id="86c76-111">GetLiveRange – metoda</span><span class="sxs-lookup"><span data-stu-id="86c76-111">GetLiveRange Method</span></span>](icordebugvariablehome-getliverange-method.md)|<span data-ttu-id="86c76-112">Získá nativní rozsah, ve kterém je tato proměnná živá.</span><span class="sxs-lookup"><span data-stu-id="86c76-112">Gets the native range over which this variable is live.</span></span>|  
|[<span data-ttu-id="86c76-113">GetLocationType – metoda</span><span class="sxs-lookup"><span data-stu-id="86c76-113">GetLocationType Method</span></span>](icordebugvariablehome-getlocationtype-method.md)|<span data-ttu-id="86c76-114">Získá typ nativního umístění proměnné.</span><span class="sxs-lookup"><span data-stu-id="86c76-114">Gets the type of the variable's native location.</span></span>|  
|[<span data-ttu-id="86c76-115">GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="86c76-115">GetOffset Method</span></span>](icordebugvariablehome-getoffset-method.md)|<span data-ttu-id="86c76-116">Získá posun od základního registru pro proměnnou.</span><span class="sxs-lookup"><span data-stu-id="86c76-116">Gets the offset from the base register for a variable.</span></span>|  
|[<span data-ttu-id="86c76-117">GetRegister – metoda</span><span class="sxs-lookup"><span data-stu-id="86c76-117">GetRegister Method</span></span>](icordebugvariablehome-getregister-method.md)|<span data-ttu-id="86c76-118">Získá registr, který obsahuje proměnnou s typem umístění `VLT_REGISTER`a základní registr pro proměnnou s typem umístění `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="86c76-118">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>|  
|[<span data-ttu-id="86c76-119">GetSlotIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="86c76-119">GetSlotIndex Method</span></span>](icordebugvariablehome-getslotindex-method.md)|<span data-ttu-id="86c76-120">Získá spravovaný index slotu místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="86c76-120">Gets the managed slot-index of a local variable.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="86c76-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="86c76-121">Example</span></span>  
 <span data-ttu-id="86c76-122">Následující fragment kódu používá objekt [ICorDebugCode4](icordebugcode4-interface.md) s názvem `pCode4`.</span><span class="sxs-lookup"><span data-stu-id="86c76-122">The following code fragment uses the [ICorDebugCode4](icordebugcode4-interface.md) object named `pCode4`.</span></span>  
  
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
  
## <a name="requirements"></a><span data-ttu-id="86c76-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="86c76-123">Requirements</span></span>  
 <span data-ttu-id="86c76-124">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86c76-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86c76-125">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="86c76-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86c76-126">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="86c76-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86c76-127">**Verze .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86c76-127">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86c76-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="86c76-128">See also</span></span>

- [<span data-ttu-id="86c76-129">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="86c76-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="86c76-130">ICorDebugVariableHomeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="86c76-130">ICorDebugVariableHomeEnum Interface</span></span>](icordebugvariablehomeenum-interface.md)
