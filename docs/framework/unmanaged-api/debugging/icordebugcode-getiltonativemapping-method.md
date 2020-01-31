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
ms.openlocfilehash: 98709c0ce7469db1d0365d71e10d2d021cd3b3f0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777892"
---
# <a name="icordebugcodegetiltonativemapping-method"></a><span data-ttu-id="4cda5-102">ICorDebugCode::GetILToNativeMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="4cda5-102">ICorDebugCode::GetILToNativeMapping Method</span></span>
<span data-ttu-id="4cda5-103">Získá pole instancí "COR_DEBUG_IL_TO_NATIVE_MAP", které reprezentují mapování z posunu jazyka MSIL (Microsoft Intermediate Language) na nativní posuny.</span><span class="sxs-lookup"><span data-stu-id="4cda5-103">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from Microsoft intermediate language (MSIL) offsets to native offsets.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cda5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4cda5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4cda5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4cda5-105">Parameters</span></span>  
 `cMap`  
 <span data-ttu-id="4cda5-106">pro Velikost pole `map`.</span><span class="sxs-lookup"><span data-stu-id="4cda5-106">[in] The size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="4cda5-107">mimo Ukazatel na skutečný počet prvků vrácených v poli `map`.</span><span class="sxs-lookup"><span data-stu-id="4cda5-107">[out] A pointer to the actual number of elements returned in the `map` array.</span></span>  
  
 `map`  
 <span data-ttu-id="4cda5-108">mimo Pole struktur `COR_DEBUG_IL_TO_NATIVE_MAP`, z nichž každý představuje mapování z posunu MSIL na nativní posun.</span><span class="sxs-lookup"><span data-stu-id="4cda5-108">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which represents a mapping from an MSIL offset to a native offset.</span></span>  
  
 <span data-ttu-id="4cda5-109">Poli vrácených prvků není žádné řazení.</span><span class="sxs-lookup"><span data-stu-id="4cda5-109">There is no ordering to the array of elements returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cda5-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4cda5-110">Remarks</span></span>  
 <span data-ttu-id="4cda5-111">Metoda `GetILToNativeMapping` vrací smysluplné výsledky pouze v případě, že tato instance "ICorDebugCode" představuje nativní kód, který byl za běhu zkompilován z kódu jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="4cda5-111">The `GetILToNativeMapping` method returns meaningful results only if this "ICorDebugCode" instance represents native code that was just-in-time (JIT) compiled from MSIL code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cda5-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4cda5-112">Requirements</span></span>  
 <span data-ttu-id="4cda5-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cda5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cda5-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4cda5-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4cda5-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4cda5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4cda5-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cda5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cda5-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4cda5-117">See also</span></span>

- [<span data-ttu-id="4cda5-118">Rozhraní ICorDebugCode</span><span class="sxs-lookup"><span data-stu-id="4cda5-118">ICorDebugCode Interface</span></span>](icordebugcode-interface1.md)
