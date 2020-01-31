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
ms.openlocfilehash: 737993ac80b26d490915af3e97fd6a9552246aee
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792109"
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="f7c85-102">ICorDebugRegisterSet::GetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="f7c85-102">ICorDebugRegisterSet::GetRegisters Method</span></span>
<span data-ttu-id="f7c85-103">Získá hodnotu každého registru (na počítači, který právě spouští kód), který je určen bitovou maskou.</span><span class="sxs-lookup"><span data-stu-id="f7c85-103">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7c85-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7c85-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7c85-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f7c85-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="f7c85-106">pro Bitová maska, která určuje, které hodnoty registru mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="f7c85-106">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="f7c85-107">Každý bit odpovídá registru.</span><span class="sxs-lookup"><span data-stu-id="f7c85-107">Each bit corresponds to a register.</span></span> <span data-ttu-id="f7c85-108">Pokud je bit nastavený na jeden, načte se hodnota registru. v opačném případě se hodnota registru nenačte.</span><span class="sxs-lookup"><span data-stu-id="f7c85-108">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="f7c85-109">pro Počet hodnot registru, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="f7c85-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="f7c85-110">mimo Pole objektů `CORDB_REGISTER`, z nichž každý přijímá hodnotu registru.</span><span class="sxs-lookup"><span data-stu-id="f7c85-110">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7c85-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f7c85-111">Remarks</span></span>  
 <span data-ttu-id="f7c85-112">Velikost pole musí být rovna počtu bitů nastaveným na jednu v bitové masce.</span><span class="sxs-lookup"><span data-stu-id="f7c85-112">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="f7c85-113">Parametr `regCount` určuje počet prvků ve vyrovnávací paměti, které budou přijímat hodnoty registru.</span><span class="sxs-lookup"><span data-stu-id="f7c85-113">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="f7c85-114">Pokud je hodnota `regCount` příliš malá pro počet registrů, které jsou označeny maskou, budou z množiny zkráceny i tyto registry s vyšším číslem.</span><span class="sxs-lookup"><span data-stu-id="f7c85-114">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="f7c85-115">Pokud je hodnota `regCount` příliš velká, nepoužívané prvky `regBuffer` nebudou změněny.</span><span class="sxs-lookup"><span data-stu-id="f7c85-115">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="f7c85-116">Pokud Bitová maska určuje registr, který není k dispozici, `GetRegisters` vrátí neurčitou hodnotu pro tento registr.</span><span class="sxs-lookup"><span data-stu-id="f7c85-116">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7c85-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f7c85-117">Requirements</span></span>  
 <span data-ttu-id="f7c85-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7c85-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7c85-119">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f7c85-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7c85-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f7c85-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7c85-121">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7c85-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7c85-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f7c85-122">See also</span></span>

- [<span data-ttu-id="f7c85-123">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f7c85-123">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="f7c85-124">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f7c85-124">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
