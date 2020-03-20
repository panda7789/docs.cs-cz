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
ms.openlocfilehash: 32e899622b9c649a08e3bca1b6645f70dcbcbb19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178535"
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="c6622-102">ICorDebugRegisterSet::GetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="c6622-102">ICorDebugRegisterSet::GetRegisters Method</span></span>
<span data-ttu-id="c6622-103">Získá hodnotu každého registru (v počítači, který je aktuálně spuštěn kód), který je určen bitovou maskou.</span><span class="sxs-lookup"><span data-stu-id="c6622-103">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6622-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6622-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6622-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c6622-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="c6622-106">[v] Bitová maska, která určuje, které hodnoty registru mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="c6622-106">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="c6622-107">Každý bit odpovídá registru.</span><span class="sxs-lookup"><span data-stu-id="c6622-107">Each bit corresponds to a register.</span></span> <span data-ttu-id="c6622-108">Pokud bit je nastavena na jeden, hodnota registru je načten; v opačném případě není načtena hodnota registru.</span><span class="sxs-lookup"><span data-stu-id="c6622-108">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="c6622-109">[v] Počet hodnot registru, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="c6622-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="c6622-110">[out] Pole `CORDB_REGISTER` objektů, z nichž každý obdrží hodnotu registru.</span><span class="sxs-lookup"><span data-stu-id="c6622-110">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6622-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6622-111">Remarks</span></span>  
 <span data-ttu-id="c6622-112">Velikost pole by měla být rovna počtu bitů nastavených na jeden v bitové masce.</span><span class="sxs-lookup"><span data-stu-id="c6622-112">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="c6622-113">Parametr `regCount` určuje počet prvků ve vyrovnávací paměti, které obdrží hodnoty registru.</span><span class="sxs-lookup"><span data-stu-id="c6622-113">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="c6622-114">Pokud `regCount` je hodnota příliš malá pro počet registrů označených maskou, vyšší číslované registry budou ze sady zkráceny.</span><span class="sxs-lookup"><span data-stu-id="c6622-114">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="c6622-115">Pokud `regCount` je hodnota příliš velká, `regBuffer` nepoužívané prvky budou nezměněny.</span><span class="sxs-lookup"><span data-stu-id="c6622-115">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="c6622-116">Pokud bitová maska určuje registr, `GetRegisters` který není k dispozici, vrátí pro tento registr neurčitou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c6622-116">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6622-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c6622-117">Requirements</span></span>  
 <span data-ttu-id="c6622-118">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6622-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6622-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6622-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6622-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6622-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6622-121">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6622-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6622-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6622-122">See also</span></span>

- [<span data-ttu-id="c6622-123">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c6622-123">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="c6622-124">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c6622-124">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
