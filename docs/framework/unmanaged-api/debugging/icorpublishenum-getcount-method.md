---
title: ICorPublishEnum::GetCount – metoda
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::GetCount
helpviewer_keywords:
- GetCount method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::GetCount method [.NET Framework debugging]
ms.assetid: d228f684-2be3-4029-93ae-31fe02213c1f
topic_type:
- apiref
ms.openlocfilehash: 7ed4236187fab1c1e81be9ddcdff1f1852e38f70
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421186"
---
# <a name="icorpublishenumgetcount-method"></a><span data-ttu-id="a59de-102">ICorPublishEnum::GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="a59de-102">ICorPublishEnum::GetCount Method</span></span>
<span data-ttu-id="a59de-103">Získá počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="a59de-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a59de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a59de-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a59de-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a59de-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="a59de-106">mimo Ukazatel na počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="a59de-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a59de-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a59de-107">Requirements</span></span>  
 <span data-ttu-id="a59de-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a59de-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a59de-109">**Hlavička:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="a59de-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="a59de-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a59de-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a59de-111">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a59de-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a59de-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="a59de-112">See also</span></span>

- [<span data-ttu-id="a59de-113">ICorPublishEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a59de-113">ICorPublishEnum Interface</span></span>](icorpublishenum-interface.md)
