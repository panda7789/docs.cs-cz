---
title: ICorPublishProcessEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum::Next
helpviewer_keywords:
- ICorPublishProcessEnum::Next method [.NET Framework debugging]
- Next method, ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: 6c399f37-1e38-4ca1-b70d-8ae41f7228b7
topic_type:
- apiref
ms.openlocfilehash: b3bb1857075f857f62ec92ac6a2876a49655c70e
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421056"
---
# <a name="icorpublishprocessenumnext-method"></a><span data-ttu-id="3695a-102">ICorPublishProcessEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="3695a-102">ICorPublishProcessEnum::Next Method</span></span>
<span data-ttu-id="3695a-103">Získá zadaný počet procesů z kolekce počínaje aktuální pozicí kurzoru.</span><span class="sxs-lookup"><span data-stu-id="3695a-103">Gets the specified number of processes from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3695a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3695a-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorPublishProcess **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3695a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3695a-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="3695a-106">pro Počet procesů, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="3695a-106">[in] The number of processes to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="3695a-107">mimo Ukazatel na pole načtených objektů [ICorPublishProcess](icorpublishprocess-interface.md) , z nichž každý představuje proces.</span><span class="sxs-lookup"><span data-stu-id="3695a-107">[out] A pointer to the array of retrieved [ICorPublishProcess](icorpublishprocess-interface.md) objects, each of which represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="3695a-108">mimo Ukazatel na počet skutečně vrácených procesů.</span><span class="sxs-lookup"><span data-stu-id="3695a-108">[out] Pointer to the number of processes actually returned.</span></span> <span data-ttu-id="3695a-109">Tato hodnota může být null `celt` , pokud je jedna.</span><span class="sxs-lookup"><span data-stu-id="3695a-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3695a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3695a-110">Requirements</span></span>  
 <span data-ttu-id="3695a-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3695a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3695a-112">**Hlavička:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="3695a-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="3695a-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3695a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3695a-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3695a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3695a-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="3695a-115">See also</span></span>

- [<span data-ttu-id="3695a-116">ICorPublishProcessEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3695a-116">ICorPublishProcessEnum Interface</span></span>](icorpublishprocessenum-interface.md)
