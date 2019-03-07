---
title: ICorDebugRegisterSet2::GetRegisters – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06c74509a0435fe54f754c6e47603bd74b5b09fe
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493593"
---
# <a name="icordebugregisterset2getregisters-method"></a><span data-ttu-id="fb64c-102">ICorDebugRegisterSet2::GetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="fb64c-102">ICorDebugRegisterSet2::GetRegisters Method</span></span>
<span data-ttu-id="fb64c-103">Získá hodnotu každý registr (pro platformu, na kterém právě spouští kód), který je určen podle daného bitové masky.</span><span class="sxs-lookup"><span data-stu-id="fb64c-103">Gets the value of each register (for the platform on which code is currently executing) that is specified by the given bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb64c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb64c-104">Syntax</span></span>  
  
```  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb64c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb64c-105">Parameters</span></span>  
 `maskCount`  
 <span data-ttu-id="fb64c-106">[in] Velikost v bajtech, nástroje `mask` pole.</span><span class="sxs-lookup"><span data-stu-id="fb64c-106">[in] The size, in bytes, of the `mask` array.</span></span>  
  
 `mask`  
 <span data-ttu-id="fb64c-107">[in] Pole bajtů, každý bit odpovídá registru.</span><span class="sxs-lookup"><span data-stu-id="fb64c-107">[in] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="fb64c-108">Pokud bit na hodnotu 1, budou načteny hodnoty odpovídající registru.</span><span class="sxs-lookup"><span data-stu-id="fb64c-108">If the bit is 1, the corresponding register's value will be retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="fb64c-109">[in] Počet hodnot registru, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="fb64c-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="fb64c-110">[out] Pole `CORDB_REGISTER` objektů, z nichž každý přijímá hodnotu z registru.</span><span class="sxs-lookup"><span data-stu-id="fb64c-110">[out] An array of `CORDB_REGISTER` objects, each of which receives the value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb64c-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fb64c-111">Remarks</span></span>  
 <span data-ttu-id="fb64c-112">`GetRegisters` Metoda vrátí pole hodnot z registrů, která jsou určena pomocí masky.</span><span class="sxs-lookup"><span data-stu-id="fb64c-112">The `GetRegisters` method returns an array of values from the registers that are specified by the mask.</span></span> <span data-ttu-id="fb64c-113">Pole neobsahuje hodnoty registrů, jejichž bitová maska není nastavena.</span><span class="sxs-lookup"><span data-stu-id="fb64c-113">The array does not contain values of registers whose mask bit is not set.</span></span> <span data-ttu-id="fb64c-114">Díky tomu se velikost `regBuffer` pole musí být stejná jako číslo od 1 masce.</span><span class="sxs-lookup"><span data-stu-id="fb64c-114">Thus, the size of the `regBuffer` array must be equal to the number of 1's in the mask.</span></span> <span data-ttu-id="fb64c-115">Pokud hodnota `regCount` je příliš malá pro počet registrů indikován maska hodnoty vyšší číslované registrů se zkrátí ze sady.</span><span class="sxs-lookup"><span data-stu-id="fb64c-115">If the value of `regCount` is too small for the number of registers indicated by the mask, the values of the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="fb64c-116">Pokud `regCount` je příliš velká, nepoužívané `regBuffer` prvky bude bez úprav.</span><span class="sxs-lookup"><span data-stu-id="fb64c-116">If `regCount` is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="fb64c-117">Pokud není k dispozici registr je indikován maska, vrátí se neurčitá hodnota pro tento registr.</span><span class="sxs-lookup"><span data-stu-id="fb64c-117">If an unavailable register is indicated by the mask, an indeterminate value will be returned for that register.</span></span>  
  
 <span data-ttu-id="fb64c-118">`ICorDebugRegisterSet2::GetRegisters` Metoda je nezbytná pro platformy, které mají více než 64 registrů.</span><span class="sxs-lookup"><span data-stu-id="fb64c-118">The `ICorDebugRegisterSet2::GetRegisters` method is necessary for platforms which have more than 64 registers.</span></span> <span data-ttu-id="fb64c-119">IA64 má například 128 registrů pro obecné účely a zaregistruje se 128 s plovoucí desetinnou čárkou, tak budete potřebovat víc než 64 bitů v bitové masce.</span><span class="sxs-lookup"><span data-stu-id="fb64c-119">For example, IA64 has 128 general purpose registers and 128 floating-point registers, so you need more than 64-bits in the bit mask.</span></span>  
  
 <span data-ttu-id="fb64c-120">Pokud nemáte více než 64 registrů, stejně jako v případě na platformách, například x86, `GetRegisters` metoda ve skutečnosti právě přeloží bajtů v `mask` do bajtového pole `ULONG64` a pak zavolá [icordebugregisterset –:: Getregisters –](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) metoda, která přijímá `ULONG64` masky.</span><span class="sxs-lookup"><span data-stu-id="fb64c-120">If you do not have more than 64 registers, as is the case on platforms such as x86, the `GetRegisters` method actually just translates the bytes in the `mask` byte array into a `ULONG64` and then calls the [ICorDebugRegisterSet::GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) method, which takes the `ULONG64` mask.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb64c-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fb64c-121">Requirements</span></span>  
 <span data-ttu-id="fb64c-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb64c-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb64c-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fb64c-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb64c-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb64c-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb64c-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb64c-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb64c-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fb64c-126">See also</span></span>
- [<span data-ttu-id="fb64c-127">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb64c-127">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [<span data-ttu-id="fb64c-128">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb64c-128">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
