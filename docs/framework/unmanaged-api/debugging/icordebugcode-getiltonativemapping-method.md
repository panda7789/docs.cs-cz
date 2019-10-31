---
title: ICorDebugCode::GetILToNativeMapping – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetILToNativeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetILToNativeMapping method [.NET Framework debugging]
ms.assetid: a8ecd8c8-9627-4356-9c6f-bd05e24637c0
topic_type:
- apiref
ms.openlocfilehash: 011da6aacbf4c40420329952f47b1fabdfc2c1a3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125623"
---
# <a name="icordebugcodegetiltonativemapping-method"></a><span data-ttu-id="723ce-102">ICorDebugCode::GetILToNativeMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="723ce-102">ICorDebugCode::GetILToNativeMapping Method</span></span>
<span data-ttu-id="723ce-103">Získá pole instancí "COR_DEBUG_IL_TO_NATIVE_MAP", které reprezentují mapování z posunu jazyka MSIL (Microsoft Intermediate Language) na nativní posuny.</span><span class="sxs-lookup"><span data-stu-id="723ce-103">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from Microsoft intermediate language (MSIL) offsets to native offsets.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="723ce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="723ce-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="723ce-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="723ce-105">Parameters</span></span>  
 `cMap`  
 <span data-ttu-id="723ce-106">pro Velikost pole `map`.</span><span class="sxs-lookup"><span data-stu-id="723ce-106">[in] The size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="723ce-107">mimo Ukazatel na skutečný počet prvků vrácených v poli `map`.</span><span class="sxs-lookup"><span data-stu-id="723ce-107">[out] A pointer to the actual number of elements returned in the `map` array.</span></span>  
  
 `map`  
 <span data-ttu-id="723ce-108">mimo Pole struktur `COR_DEBUG_IL_TO_NATIVE_MAP`, z nichž každý představuje mapování z posunu MSIL na nativní posun.</span><span class="sxs-lookup"><span data-stu-id="723ce-108">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which represents a mapping from an MSIL offset to a native offset.</span></span>  
  
 <span data-ttu-id="723ce-109">Poli vrácených prvků není žádné řazení.</span><span class="sxs-lookup"><span data-stu-id="723ce-109">There is no ordering to the array of elements returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="723ce-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="723ce-110">Remarks</span></span>  
 <span data-ttu-id="723ce-111">Metoda `GetILToNativeMapping` vrací smysluplné výsledky pouze v případě, že tato instance "ICorDebugCode" představuje nativní kód, který byl za běhu zkompilován z kódu jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="723ce-111">The `GetILToNativeMapping` method returns meaningful results only if this "ICorDebugCode" instance represents native code that was just-in-time (JIT) compiled from MSIL code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="723ce-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="723ce-112">Requirements</span></span>  
 <span data-ttu-id="723ce-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="723ce-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="723ce-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="723ce-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="723ce-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="723ce-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="723ce-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="723ce-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="723ce-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="723ce-117">See also</span></span>

- [<span data-ttu-id="723ce-118">Rozhraní ICorDebugCode</span><span class="sxs-lookup"><span data-stu-id="723ce-118">ICorDebugCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)
