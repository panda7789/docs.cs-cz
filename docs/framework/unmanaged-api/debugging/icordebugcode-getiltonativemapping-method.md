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
ms.openlocfilehash: 3de85626be6ae8e4769ac261f4de1479461417ec
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893531"
---
# <a name="icordebugcodegetiltonativemapping-method"></a><span data-ttu-id="05539-102">ICorDebugCode::GetILToNativeMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="05539-102">ICorDebugCode::GetILToNativeMapping Method</span></span>
<span data-ttu-id="05539-103">Získá pole instancí "COR_DEBUG_IL_TO_NATIVE_MAP", které reprezentují mapování z posunu jazyka MSIL (Microsoft Intermediate Language) na nativní posuny.</span><span class="sxs-lookup"><span data-stu-id="05539-103">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from Microsoft intermediate language (MSIL) offsets to native offsets.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05539-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05539-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05539-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="05539-105">Parameters</span></span>  
 `cMap`  
 <span data-ttu-id="05539-106">pro Velikost `map` pole.</span><span class="sxs-lookup"><span data-stu-id="05539-106">[in] The size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="05539-107">mimo Ukazatel na skutečný počet prvků vrácených v `map` poli.</span><span class="sxs-lookup"><span data-stu-id="05539-107">[out] A pointer to the actual number of elements returned in the `map` array.</span></span>  
  
 `map`  
 <span data-ttu-id="05539-108">mimo Pole `COR_DEBUG_IL_TO_NATIVE_MAP` struktur, z nichž každý představuje mapování z posunu MSIL na nativní posun.</span><span class="sxs-lookup"><span data-stu-id="05539-108">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which represents a mapping from an MSIL offset to a native offset.</span></span>  
  
 <span data-ttu-id="05539-109">Poli vrácených prvků není žádné řazení.</span><span class="sxs-lookup"><span data-stu-id="05539-109">There is no ordering to the array of elements returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05539-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="05539-110">Remarks</span></span>  
 <span data-ttu-id="05539-111">`GetILToNativeMapping` Metoda vrátí smysluplné výsledky pouze v případě, že tato instance "ICorDebugCode" představuje nativní kód, který byl za běhu zkompilován z kódu jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="05539-111">The `GetILToNativeMapping` method returns meaningful results only if this "ICorDebugCode" instance represents native code that was just-in-time (JIT) compiled from MSIL code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05539-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="05539-112">Requirements</span></span>  
 <span data-ttu-id="05539-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05539-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05539-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="05539-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05539-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="05539-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05539-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05539-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05539-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="05539-117">See also</span></span>

- [<span data-ttu-id="05539-118">ICorDebugCode – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05539-118">ICorDebugCode Interface</span></span>](icordebugcode-interface1.md)
