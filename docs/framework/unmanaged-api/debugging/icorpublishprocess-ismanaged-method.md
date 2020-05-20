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
ms.openlocfilehash: 3eec84624866b2be7068d7875cd650828c283fd2
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421095"
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="8409b-102">ICorPublishProcess::IsManaged – metoda</span><span class="sxs-lookup"><span data-stu-id="8409b-102">ICorPublishProcess::IsManaged Method</span></span>
<span data-ttu-id="8409b-103">Získá hodnotu, která označuje, zda se má proces, na který odkazuje tento [ICorPublishProcess](icorpublishprocess-interface.md) , známo, že má spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="8409b-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8409b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8409b-104">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8409b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8409b-105">Parameters</span></span>  
 `pbManaged`  
 <span data-ttu-id="8409b-106">mimo Ukazatel na logickou hodnotu, která určuje, zda má proces spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="8409b-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="8409b-107">Hodnota je v `true` případě, že proces má spravovaný kód. v opačném případě `false` .</span><span class="sxs-lookup"><span data-stu-id="8409b-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8409b-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8409b-108">Remarks</span></span>  
 <span data-ttu-id="8409b-109">Vzhledem k tomu, že aktuální verze nástroje `ICorPublishProcess` umožňuje přístup pouze k procesům, které mají spravovaný kód, `IsManaged` vždy vrátí `true` .</span><span class="sxs-lookup"><span data-stu-id="8409b-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8409b-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8409b-110">Requirements</span></span>  
 <span data-ttu-id="8409b-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8409b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8409b-112">**Hlavička:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="8409b-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="8409b-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8409b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8409b-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8409b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8409b-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="8409b-115">See also</span></span>

- [<span data-ttu-id="8409b-116">ICorPublishProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8409b-116">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
