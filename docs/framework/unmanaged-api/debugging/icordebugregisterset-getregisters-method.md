---
title: ICorDebugRegisterSet::GetRegisters – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4887d44f0ac5603280efa0abdbd7e65c71fc3ca
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485448"
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="4de8f-102">ICorDebugRegisterSet::GetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="4de8f-102">ICorDebugRegisterSet::GetRegisters Method</span></span>
<span data-ttu-id="4de8f-103">Získá hodnotu každý registr (na počítači, který aktuálně spouští kód), která je určená bitová maska.</span><span class="sxs-lookup"><span data-stu-id="4de8f-103">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4de8f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4de8f-104">Syntax</span></span>  
  
```  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4de8f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4de8f-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="4de8f-106">[in] Bitová maska, která určuje, které registru jsou hodnoty, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="4de8f-106">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="4de8f-107">Každý bit odpovídá registru.</span><span class="sxs-lookup"><span data-stu-id="4de8f-107">Each bit corresponds to a register.</span></span> <span data-ttu-id="4de8f-108">Pokud je o něco nastavená na jednu, načte do registru hodnota; v opačném případě se načíst hodnotu do registru.</span><span class="sxs-lookup"><span data-stu-id="4de8f-108">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="4de8f-109">[in] Počet hodnot registru, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="4de8f-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="4de8f-110">[out] Pole `CORDB_REGISTER` objektů, z nichž každý přijímá hodnotu z registru.</span><span class="sxs-lookup"><span data-stu-id="4de8f-110">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4de8f-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4de8f-111">Remarks</span></span>  
 <span data-ttu-id="4de8f-112">Velikost pole by měl být roven počtu bitů nastavena na jednu v bitové masce.</span><span class="sxs-lookup"><span data-stu-id="4de8f-112">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="4de8f-113">`regCount` Parametr určuje počet prvků ve vyrovnávací paměti, která bude dostávat hodnot registru.</span><span class="sxs-lookup"><span data-stu-id="4de8f-113">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="4de8f-114">Pokud `regCount` hodnota je příliš malý počet registrů indikován maska, vyšší číslované registrů se zkrátí ze sady.</span><span class="sxs-lookup"><span data-stu-id="4de8f-114">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="4de8f-115">Pokud `regCount` hodnota je příliš velká, nepoužívané `regBuffer` prvky bude bez úprav.</span><span class="sxs-lookup"><span data-stu-id="4de8f-115">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="4de8f-116">Pokud bit masky určuje registru, který je k dispozici, `GetRegisters` vrátí neurčitá hodnota pro tento registr.</span><span class="sxs-lookup"><span data-stu-id="4de8f-116">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4de8f-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4de8f-117">Requirements</span></span>  
 <span data-ttu-id="4de8f-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4de8f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4de8f-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4de8f-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4de8f-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4de8f-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4de8f-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4de8f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4de8f-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4de8f-122">See also</span></span>
- [<span data-ttu-id="4de8f-123">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4de8f-123">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="4de8f-124">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4de8f-124">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
