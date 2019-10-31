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
ms.openlocfilehash: 8e5583acfe338c185200c0b8e41b7d6e051fa146
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131354"
---
# <a name="icordebugregisterset2getregisters-method"></a><span data-ttu-id="3a478-102">ICorDebugRegisterSet2::GetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="3a478-102">ICorDebugRegisterSet2::GetRegisters Method</span></span>
<span data-ttu-id="3a478-103">Získá hodnotu každého registru (pro platformu, na které je aktuálně spuštěn kód), který je určen pomocí dané bitové masky.</span><span class="sxs-lookup"><span data-stu-id="3a478-103">Gets the value of each register (for the platform on which code is currently executing) that is specified by the given bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a478-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a478-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a478-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3a478-105">Parameters</span></span>  
 `maskCount`  
 <span data-ttu-id="3a478-106">pro Velikost pole `mask` v bajtech</span><span class="sxs-lookup"><span data-stu-id="3a478-106">[in] The size, in bytes, of the `mask` array.</span></span>  
  
 `mask`  
 <span data-ttu-id="3a478-107">pro Pole bajtů, každý bit, který odpovídá registru.</span><span class="sxs-lookup"><span data-stu-id="3a478-107">[in] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="3a478-108">Pokud je bit 1, načte se odpovídající hodnota registru.</span><span class="sxs-lookup"><span data-stu-id="3a478-108">If the bit is 1, the corresponding register's value will be retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="3a478-109">pro Počet hodnot registru, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="3a478-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="3a478-110">mimo Pole objektů `CORDB_REGISTER`, z nichž každý přijímá hodnotu registru.</span><span class="sxs-lookup"><span data-stu-id="3a478-110">[out] An array of `CORDB_REGISTER` objects, each of which receives the value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a478-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3a478-111">Remarks</span></span>  
 <span data-ttu-id="3a478-112">Metoda `GetRegisters` vrací pole hodnot z registrů, které jsou určeny maskou.</span><span class="sxs-lookup"><span data-stu-id="3a478-112">The `GetRegisters` method returns an array of values from the registers that are specified by the mask.</span></span> <span data-ttu-id="3a478-113">Pole neobsahuje hodnoty pro registry, jejichž bit maskování není nastaven.</span><span class="sxs-lookup"><span data-stu-id="3a478-113">The array does not contain values of registers whose mask bit is not set.</span></span> <span data-ttu-id="3a478-114">Proto musí být velikost pole `regBuffer` rovna počtu 1 v masce.</span><span class="sxs-lookup"><span data-stu-id="3a478-114">Thus, the size of the `regBuffer` array must be equal to the number of 1's in the mask.</span></span> <span data-ttu-id="3a478-115">Pokud je hodnota `regCount` příliš malá pro počet registrů, které jsou označeny maskou, hodnoty vyšších očíslovaných registrů se ze sady zkrátí.</span><span class="sxs-lookup"><span data-stu-id="3a478-115">If the value of `regCount` is too small for the number of registers indicated by the mask, the values of the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="3a478-116">Pokud je `regCount` příliš velká, nepoužívané prvky `regBuffer` nebudou změněny.</span><span class="sxs-lookup"><span data-stu-id="3a478-116">If `regCount` is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="3a478-117">Pokud je nedostupný registr označen maskou, bude pro tento registr vrácena neurčitá hodnota.</span><span class="sxs-lookup"><span data-stu-id="3a478-117">If an unavailable register is indicated by the mask, an indeterminate value will be returned for that register.</span></span>  
  
 <span data-ttu-id="3a478-118">Metoda `ICorDebugRegisterSet2::GetRegisters` je nezbytná pro platformy, které mají více než 64 registrů.</span><span class="sxs-lookup"><span data-stu-id="3a478-118">The `ICorDebugRegisterSet2::GetRegisters` method is necessary for platforms which have more than 64 registers.</span></span> <span data-ttu-id="3a478-119">Například IA64 má 128 registrů pro obecné účely a 128 registrů s plovoucí desetinnou čárkou, takže potřebujete více než 64-bitů v bitové masce.</span><span class="sxs-lookup"><span data-stu-id="3a478-119">For example, IA64 has 128 general purpose registers and 128 floating-point registers, so you need more than 64-bits in the bit mask.</span></span>  
  
 <span data-ttu-id="3a478-120">Pokud nemáte více než 64 registrů, stejně jako v případě platforem, jako je například x86, metoda `GetRegisters` ve skutečnosti pouze překládá bajty v poli `mask` bajtů do `ULONG64` a potom zavolá metodu [ICorDebugRegisterSet:: GetRegisters.](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) , který přebírá `ULONG64` masku.</span><span class="sxs-lookup"><span data-stu-id="3a478-120">If you do not have more than 64 registers, as is the case on platforms such as x86, the `GetRegisters` method actually just translates the bytes in the `mask` byte array into a `ULONG64` and then calls the [ICorDebugRegisterSet::GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) method, which takes the `ULONG64` mask.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a478-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3a478-121">Requirements</span></span>  
 <span data-ttu-id="3a478-122">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a478-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a478-123">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3a478-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a478-124">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3a478-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a478-125">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a478-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a478-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3a478-126">See also</span></span>

- [<span data-ttu-id="3a478-127">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3a478-127">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [<span data-ttu-id="3a478-128">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3a478-128">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
