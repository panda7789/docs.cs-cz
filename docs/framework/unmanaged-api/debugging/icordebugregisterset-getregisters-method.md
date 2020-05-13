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
ms.openlocfilehash: 40de06d47654337542d2c80dc325f8201335312a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379156"
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="5295e-102">ICorDebugRegisterSet::GetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="5295e-102">ICorDebugRegisterSet::GetRegisters Method</span></span>
<span data-ttu-id="5295e-103">Získá hodnotu každého registru (na počítači, který právě spouští kód), který je určen bitovou maskou.</span><span class="sxs-lookup"><span data-stu-id="5295e-103">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5295e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5295e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5295e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5295e-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="5295e-106">pro Bitová maska, která určuje, které hodnoty registru mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="5295e-106">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="5295e-107">Každý bit odpovídá registru.</span><span class="sxs-lookup"><span data-stu-id="5295e-107">Each bit corresponds to a register.</span></span> <span data-ttu-id="5295e-108">Pokud je bit nastavený na jeden, načte se hodnota registru. v opačném případě se hodnota registru nenačte.</span><span class="sxs-lookup"><span data-stu-id="5295e-108">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="5295e-109">pro Počet hodnot registru, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="5295e-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="5295e-110">mimo Pole `CORDB_REGISTER` objektů, z nichž každý přijímá hodnotu registru.</span><span class="sxs-lookup"><span data-stu-id="5295e-110">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5295e-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5295e-111">Remarks</span></span>  
 <span data-ttu-id="5295e-112">Velikost pole musí být rovna počtu bitů nastaveným na jednu v bitové masce.</span><span class="sxs-lookup"><span data-stu-id="5295e-112">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="5295e-113">`regCount`Parametr určuje počet prvků ve vyrovnávací paměti, které budou přijímat hodnoty registru.</span><span class="sxs-lookup"><span data-stu-id="5295e-113">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="5295e-114">Pokud `regCount` je hodnota příliš malá pro počet registrů, které jsou označeny maskou, budou z množiny zkráceny i tyto registry s vyšším číslem.</span><span class="sxs-lookup"><span data-stu-id="5295e-114">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="5295e-115">`regCount`Je-li hodnota příliš velká, nepoužívané `regBuffer` prvky nebudou změněny.</span><span class="sxs-lookup"><span data-stu-id="5295e-115">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="5295e-116">Pokud Bitová maska určuje registr, který není k dispozici, `GetRegisters` vrátí neurčitou hodnotu pro tento registr.</span><span class="sxs-lookup"><span data-stu-id="5295e-116">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5295e-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5295e-117">Requirements</span></span>  
 <span data-ttu-id="5295e-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5295e-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5295e-119">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5295e-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5295e-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5295e-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5295e-121">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5295e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5295e-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="5295e-122">See also</span></span>

- [<span data-ttu-id="5295e-123">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5295e-123">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="5295e-124">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5295e-124">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
