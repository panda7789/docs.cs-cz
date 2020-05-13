---
title: ICorDebugObjectEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugObjectEnum interface [.NET Framework debugging]
- ICorDebugObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 10093e3d-26b6-4ad7-8ef3-bbf66243fc02
topic_type:
- apiref
ms.openlocfilehash: 70514464f27d6123a4de1d5800ed016a39541287
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207546"
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="bd07a-102">ICorDebugObjectEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="bd07a-102">ICorDebugObjectEnum::Next Method</span></span>
<span data-ttu-id="bd07a-103">Načte relativní virtuální adresy (RVA) zadaného počtu objektů z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="bd07a-103">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd07a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd07a-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd07a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bd07a-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="bd07a-106">pro Počet objektů, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="bd07a-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="bd07a-107">mimo Pole ukazatelů, z nichž každý odkazuje na objekt CORDB_ADDRESS.</span><span class="sxs-lookup"><span data-stu-id="bd07a-107">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="bd07a-108">mimo Ukazatel na počet skutečně vrácených objektů.</span><span class="sxs-lookup"><span data-stu-id="bd07a-108">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="bd07a-109">Tato hodnota může být null `celt` , pokud je jedna.</span><span class="sxs-lookup"><span data-stu-id="bd07a-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd07a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bd07a-110">Requirements</span></span>  
 <span data-ttu-id="bd07a-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd07a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd07a-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bd07a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd07a-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bd07a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd07a-114">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd07a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd07a-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="bd07a-115">See also</span></span>
