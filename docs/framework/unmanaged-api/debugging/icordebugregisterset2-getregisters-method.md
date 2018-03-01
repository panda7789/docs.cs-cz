---
title: "ICorDebugRegisterSet2::GetRegisters – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugRegisterSet2.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegisters method [.NET Framework debugging]
ms.assetid: dbc498a8-ba3f-42f2-bdd9-b623c77a1019
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 830fd9b4c04d536f64ca5b15e513c9f5f049f059
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugregisterset2getregisters-method"></a><span data-ttu-id="33c43-102">ICorDebugRegisterSet2::GetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="33c43-102">ICorDebugRegisterSet2::GetRegisters Method</span></span>
<span data-ttu-id="33c43-103">Získá hodnotu každý registrace (pro platformu, na kterém je aktuálně provádění kódu), který je určen podle dané bit masky.</span><span class="sxs-lookup"><span data-stu-id="33c43-103">Gets the value of each register (for the platform on which code is currently executing) that is specified by the given bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33c43-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33c43-104">Syntax</span></span>  
  
```  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="33c43-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33c43-105">Parameters</span></span>  
 `maskCount`  
 <span data-ttu-id="33c43-106">[v] Velikost v bajtech z `mask` pole.</span><span class="sxs-lookup"><span data-stu-id="33c43-106">[in] The size, in bytes, of the `mask` array.</span></span>  
  
 `mask`  
 <span data-ttu-id="33c43-107">[v] Pole bajtů, každý bit odpovídá registraci.</span><span class="sxs-lookup"><span data-stu-id="33c43-107">[in] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="33c43-108">Pokud je bit 1, budou načteny odpovídající registrace hodnotu.</span><span class="sxs-lookup"><span data-stu-id="33c43-108">If the bit is 1, the corresponding register's value will be retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="33c43-109">[v] Počet hodnot registru, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="33c43-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="33c43-110">[out] Pole `CORDB_REGISTER` objekty, z nichž každý obdrží hodnotu registru.</span><span class="sxs-lookup"><span data-stu-id="33c43-110">[out] An array of `CORDB_REGISTER` objects, each of which receives the value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33c43-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="33c43-111">Remarks</span></span>  
 <span data-ttu-id="33c43-112">`GetRegisters` Metoda vrátí pole hodnot z registrů, které jsou určené maska.</span><span class="sxs-lookup"><span data-stu-id="33c43-112">The `GetRegisters` method returns an array of values from the registers that are specified by the mask.</span></span> <span data-ttu-id="33c43-113">Pole neobsahuje hodnoty registrů, jejichž bit masky není nastavený.</span><span class="sxs-lookup"><span data-stu-id="33c43-113">The array does not contain values of registers whose mask bit is not set.</span></span> <span data-ttu-id="33c43-114">Proto velikost `regBuffer` pole musí být stejný jako počet na 1 v masce.</span><span class="sxs-lookup"><span data-stu-id="33c43-114">Thus, the size of the `regBuffer` array must be equal to the number of 1's in the mask.</span></span> <span data-ttu-id="33c43-115">Pokud hodnota `regCount` je příliš malá pro počet registry indikován maska hodnoty vyšší číslem registrů bude zkrácen ze sady.</span><span class="sxs-lookup"><span data-stu-id="33c43-115">If the value of `regCount` is too small for the number of registers indicated by the mask, the values of the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="33c43-116">Pokud `regCount` je příliš velký, nepoužívané `regBuffer` elementy bude beze změny.</span><span class="sxs-lookup"><span data-stu-id="33c43-116">If `regCount` is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="33c43-117">Pokud není k dispozici registrace je indikován maska, neurčitém hodnotu, bude vrácen pro této registrace.</span><span class="sxs-lookup"><span data-stu-id="33c43-117">If an unavailable register is indicated by the mask, an indeterminate value will be returned for that register.</span></span>  
  
 <span data-ttu-id="33c43-118">`ICorDebugRegisterSet2::GetRegisters` Metoda je nezbytné pro platformy, které mají víc než 64 Registry.</span><span class="sxs-lookup"><span data-stu-id="33c43-118">The `ICorDebugRegisterSet2::GetRegisters` method is necessary for platforms which have more than 64 registers.</span></span> <span data-ttu-id="33c43-119">IA64 má například 128 registry obecné účely a 128 zaregistruje se s plovoucí desetinnou čárkou, proto musíte víc než 64 bitů v bitová maska.</span><span class="sxs-lookup"><span data-stu-id="33c43-119">For example, IA64 has 128 general purpose registers and 128 floating-point registers, so you need more than 64-bits in the bit mask.</span></span>  
  
 <span data-ttu-id="33c43-120">Pokud nemáte víc než 64 registrů, stejně jako v případě na platformách, například x86, `GetRegisters` metoda ve skutečnosti jenom překládá bajtů v `mask` do bajtového pole `ULONG64` a potom zavolá [ICorDebugRegisterSet:: Getregisters –](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) metoda, která přebírá `ULONG64` masky.</span><span class="sxs-lookup"><span data-stu-id="33c43-120">If you do not have more than 64 registers, as is the case on platforms such as x86, the `GetRegisters` method actually just translates the bytes in the `mask` byte array into a `ULONG64` and then calls the [ICorDebugRegisterSet::GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) method, which takes the `ULONG64` mask.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33c43-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="33c43-121">Requirements</span></span>  
 <span data-ttu-id="33c43-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33c43-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33c43-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33c43-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33c43-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33c43-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33c43-125">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33c43-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33c43-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="33c43-126">See Also</span></span>  
 [<span data-ttu-id="33c43-127">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="33c43-127">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 [<span data-ttu-id="33c43-128">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="33c43-128">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
