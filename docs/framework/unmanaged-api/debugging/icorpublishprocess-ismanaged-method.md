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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b57a8bcc584ffd209def5a84a99b15daa7480ee6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534940"
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="69755-102">ICorPublishProcess::IsManaged – metoda</span><span class="sxs-lookup"><span data-stu-id="69755-102">ICorPublishProcess::IsManaged Method</span></span>
<span data-ttu-id="69755-103">Získá hodnotu určující, zda proces odkazuje toto [icorpublishprocess –](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) se ví, že máte spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="69755-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69755-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69755-104">Syntax</span></span>  
  
```  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="69755-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="69755-105">Parameters</span></span>  
 `pbManaged`  
 <span data-ttu-id="69755-106">[out] Ukazatel na logickou hodnotu, která určuje, zda má proces spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="69755-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="69755-107">Hodnota je `true` Pokud proces má spravovaného kódu; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="69755-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69755-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="69755-108">Remarks</span></span>  
 <span data-ttu-id="69755-109">Od aktuální verze `ICorPublishProcess` umožňuje přístup jenom k procesům, které mají spravovaného kódu, `IsManaged` vždy vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="69755-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69755-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="69755-110">Requirements</span></span>  
 <span data-ttu-id="69755-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69755-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69755-112">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="69755-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="69755-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69755-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69755-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69755-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69755-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69755-115">See also</span></span>
- [<span data-ttu-id="69755-116">ICorPublishProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="69755-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
