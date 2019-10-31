---
title: ICorPublishProcess::IsManaged – metoda
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type:
- apiref
ms.openlocfilehash: ad3a357a98cb5ed28a34e4076b5e145903ceaf91
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103502"
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="32861-102">ICorPublishProcess::IsManaged – metoda</span><span class="sxs-lookup"><span data-stu-id="32861-102">ICorPublishProcess::IsManaged Method</span></span>
<span data-ttu-id="32861-103">Získá hodnotu, která označuje, zda se má proces, na který odkazuje tento [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) , známo, že má spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="32861-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32861-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32861-104">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32861-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="32861-105">Parameters</span></span>  
 `pbManaged`  
 <span data-ttu-id="32861-106">mimo Ukazatel na logickou hodnotu, která určuje, zda má proces spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="32861-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="32861-107">Hodnota je `true`, pokud má proces spravovaný kód. v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="32861-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32861-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="32861-108">Remarks</span></span>  
 <span data-ttu-id="32861-109">Vzhledem k tomu, že aktuální verze `ICorPublishProcess` umožňuje přístup pouze k procesům se spravovaným kódem, `IsManaged` vždy vrací `true`.</span><span class="sxs-lookup"><span data-stu-id="32861-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32861-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="32861-110">Requirements</span></span>  
 <span data-ttu-id="32861-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32861-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32861-112">**Hlavička:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="32861-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="32861-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="32861-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32861-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32861-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32861-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32861-115">See also</span></span>

- [<span data-ttu-id="32861-116">ICorPublishProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="32861-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
