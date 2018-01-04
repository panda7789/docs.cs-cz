---
title: "ICorDebugRegisterSet::GetRegisters – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet.GetRegisters
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ddefb1ac5694bf1f213dd77e0ffc7f746b7e62cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="bf9e2-102">ICorDebugRegisterSet::GetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="bf9e2-102">ICorDebugRegisterSet::GetRegisters Method</span></span>
<span data-ttu-id="bf9e2-103">Získá hodnotu každý registrace (v počítači, který je aktuálně provádění kódu), který je určen podle bit masky.</span><span class="sxs-lookup"><span data-stu-id="bf9e2-103">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf9e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf9e2-104">Syntax</span></span>  
  
```  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bf9e2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf9e2-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="bf9e2-106">[v] Bitová maska, která určuje registrace, které se mají načíst hodnoty.</span><span class="sxs-lookup"><span data-stu-id="bf9e2-106">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="bf9e2-107">Každý bit odpovídá registraci.</span><span class="sxs-lookup"><span data-stu-id="bf9e2-107">Each bit corresponds to a register.</span></span> <span data-ttu-id="bf9e2-108">Pokud je trochu nastaven na jednu, je načíst hodnoty registru; jinak není načíst hodnoty registru.</span><span class="sxs-lookup"><span data-stu-id="bf9e2-108">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="bf9e2-109">[v] Počet hodnot registru, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="bf9e2-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="bf9e2-110">[out] Pole `CORDB_REGISTER` objekty, z nichž každý obdrží hodnotu registru.</span><span class="sxs-lookup"><span data-stu-id="bf9e2-110">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf9e2-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bf9e2-111">Remarks</span></span>  
 <span data-ttu-id="bf9e2-112">Velikost pole musí být roven počtu bitů, které jsou nastavené na jednu v bitová maska.</span><span class="sxs-lookup"><span data-stu-id="bf9e2-112">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="bf9e2-113">`regCount` Parametr určuje počet elementů ve vyrovnávací paměti, která bude přijímat hodnot registru.</span><span class="sxs-lookup"><span data-stu-id="bf9e2-113">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="bf9e2-114">Pokud `regCount` hodnota je příliš malý počet registry indikován maska, vyšší číslem registry bude zkrácen ze sady.</span><span class="sxs-lookup"><span data-stu-id="bf9e2-114">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="bf9e2-115">Pokud `regCount` hodnota je příliš velký, nepoužívané `regBuffer` elementy bude beze změny.</span><span class="sxs-lookup"><span data-stu-id="bf9e2-115">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="bf9e2-116">Pokud bitová maska určuje registrace, který je k dispozici, `GetRegisters` vrací neurčitém hodnotu pro tento registrace.</span><span class="sxs-lookup"><span data-stu-id="bf9e2-116">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf9e2-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bf9e2-117">Requirements</span></span>  
 <span data-ttu-id="bf9e2-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf9e2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf9e2-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf9e2-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf9e2-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf9e2-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf9e2-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf9e2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf9e2-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="bf9e2-122">See Also</span></span>  
 [<span data-ttu-id="bf9e2-123">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bf9e2-123">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [<span data-ttu-id="bf9e2-124">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bf9e2-124">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
