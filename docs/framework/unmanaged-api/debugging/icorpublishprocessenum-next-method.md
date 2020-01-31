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
ms.openlocfilehash: 084af87acd73ef65739ba69ef2bd66d10d7c27c2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790518"
---
# <a name="icorpublishprocessenumnext-method"></a><span data-ttu-id="563d5-102">ICorPublishProcessEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="563d5-102">ICorPublishProcessEnum::Next Method</span></span>
<span data-ttu-id="563d5-103">Získá zadaný počet procesů z kolekce počínaje aktuální pozicí kurzoru.</span><span class="sxs-lookup"><span data-stu-id="563d5-103">Gets the specified number of processes from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="563d5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="563d5-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorPublishProcess **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="563d5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="563d5-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="563d5-106">pro Počet procesů, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="563d5-106">[in] The number of processes to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="563d5-107">mimo Ukazatel na pole načtených objektů [ICorPublishProcess](icorpublishprocess-interface.md) , z nichž každý představuje proces.</span><span class="sxs-lookup"><span data-stu-id="563d5-107">[out] A pointer to the array of retrieved [ICorPublishProcess](icorpublishprocess-interface.md) objects, each of which represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="563d5-108">mimo Ukazatel na počet skutečně vrácených procesů.</span><span class="sxs-lookup"><span data-stu-id="563d5-108">[out] Pointer to the number of processes actually returned.</span></span> <span data-ttu-id="563d5-109">Tato hodnota může být null, pokud je `celt` jedna.</span><span class="sxs-lookup"><span data-stu-id="563d5-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="563d5-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="563d5-110">Requirements</span></span>  
 <span data-ttu-id="563d5-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="563d5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="563d5-112">**Hlavička:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="563d5-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="563d5-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="563d5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="563d5-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="563d5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="563d5-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="563d5-115">See also</span></span>

- [<span data-ttu-id="563d5-116">ICorPublishProcessEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="563d5-116">ICorPublishProcessEnum Interface</span></span>](icorpublishprocessenum-interface.md)
