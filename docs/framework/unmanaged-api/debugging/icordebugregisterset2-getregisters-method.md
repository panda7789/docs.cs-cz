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
ms.openlocfilehash: b7a356d80d63fae65191bbf4fc0a23d7e02004c9
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378234"
---
# <a name="icordebugregisterset2getregisters-method"></a><span data-ttu-id="d4105-102">ICorDebugRegisterSet2::GetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="d4105-102">ICorDebugRegisterSet2::GetRegisters Method</span></span>
<span data-ttu-id="d4105-103">Získá hodnotu každého registru (pro platformu, na které je aktuálně spuštěn kód), který je určen pomocí dané bitové masky.</span><span class="sxs-lookup"><span data-stu-id="d4105-103">Gets the value of each register (for the platform on which code is currently executing) that is specified by the given bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4105-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4105-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4105-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4105-105">Parameters</span></span>  
 `maskCount`  
 <span data-ttu-id="d4105-106">pro Velikost pole v bajtech `mask` .</span><span class="sxs-lookup"><span data-stu-id="d4105-106">[in] The size, in bytes, of the `mask` array.</span></span>  
  
 `mask`  
 <span data-ttu-id="d4105-107">pro Pole bajtů, každý bit, který odpovídá registru.</span><span class="sxs-lookup"><span data-stu-id="d4105-107">[in] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="d4105-108">Pokud je bit 1, načte se odpovídající hodnota registru.</span><span class="sxs-lookup"><span data-stu-id="d4105-108">If the bit is 1, the corresponding register's value will be retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="d4105-109">pro Počet hodnot registru, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="d4105-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="d4105-110">mimo Pole `CORDB_REGISTER` objektů, z nichž každý přijímá hodnotu registru.</span><span class="sxs-lookup"><span data-stu-id="d4105-110">[out] An array of `CORDB_REGISTER` objects, each of which receives the value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4105-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d4105-111">Remarks</span></span>  
 <span data-ttu-id="d4105-112">`GetRegisters`Metoda vrací pole hodnot z registrů, které jsou určeny maskou.</span><span class="sxs-lookup"><span data-stu-id="d4105-112">The `GetRegisters` method returns an array of values from the registers that are specified by the mask.</span></span> <span data-ttu-id="d4105-113">Pole neobsahuje hodnoty pro registry, jejichž bit maskování není nastaven.</span><span class="sxs-lookup"><span data-stu-id="d4105-113">The array does not contain values of registers whose mask bit is not set.</span></span> <span data-ttu-id="d4105-114">Proto `regBuffer` musí být velikost pole rovna počtu 1 v masce.</span><span class="sxs-lookup"><span data-stu-id="d4105-114">Thus, the size of the `regBuffer` array must be equal to the number of 1's in the mask.</span></span> <span data-ttu-id="d4105-115">Pokud `regCount` je hodnota příliš malá pro počet registrů, které jsou označeny maskou, hodnoty z vyšších očíslovaných registrů se ze sady zkrátí.</span><span class="sxs-lookup"><span data-stu-id="d4105-115">If the value of `regCount` is too small for the number of registers indicated by the mask, the values of the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="d4105-116">Pokud `regCount` je příliš velké, nepoužívané `regBuffer` prvky nebudou změněny.</span><span class="sxs-lookup"><span data-stu-id="d4105-116">If `regCount` is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="d4105-117">Pokud je nedostupný registr označen maskou, bude pro tento registr vrácena neurčitá hodnota.</span><span class="sxs-lookup"><span data-stu-id="d4105-117">If an unavailable register is indicated by the mask, an indeterminate value will be returned for that register.</span></span>  
  
 <span data-ttu-id="d4105-118">Tato `ICorDebugRegisterSet2::GetRegisters` Metoda je nezbytná pro platformy, které mají více než 64 registrů.</span><span class="sxs-lookup"><span data-stu-id="d4105-118">The `ICorDebugRegisterSet2::GetRegisters` method is necessary for platforms which have more than 64 registers.</span></span> <span data-ttu-id="d4105-119">Například IA64 má 128 registrů pro obecné účely a 128 registrů s plovoucí desetinnou čárkou, takže potřebujete více než 64-bitů v bitové masce.</span><span class="sxs-lookup"><span data-stu-id="d4105-119">For example, IA64 has 128 general purpose registers and 128 floating-point registers, so you need more than 64-bits in the bit mask.</span></span>  
  
 <span data-ttu-id="d4105-120">Pokud nemáte více než 64 registrů, stejně jako v případě platforem, jako je například x86, `GetRegisters` metoda skutečně převede bajty v poli `mask` bajtů do `ULONG64` a a pak zavolá metodu [ICorDebugRegisterSet:: GetRegisters](icordebugregisterset-getregisters-method.md) , která přebírá `ULONG64` masku.</span><span class="sxs-lookup"><span data-stu-id="d4105-120">If you do not have more than 64 registers, as is the case on platforms such as x86, the `GetRegisters` method actually just translates the bytes in the `mask` byte array into a `ULONG64` and then calls the [ICorDebugRegisterSet::GetRegisters](icordebugregisterset-getregisters-method.md) method, which takes the `ULONG64` mask.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4105-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d4105-121">Requirements</span></span>  
 <span data-ttu-id="d4105-122">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4105-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4105-123">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d4105-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4105-124">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d4105-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4105-125">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4105-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4105-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="d4105-126">See also</span></span>

- [<span data-ttu-id="d4105-127">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d4105-127">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="d4105-128">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d4105-128">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
