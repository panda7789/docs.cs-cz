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
ms.openlocfilehash: 29c5f96bab374d6e2d43424370bff2a4a2ab6df3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986572"
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="98aba-102">ICorPublishProcess::IsManaged – metoda</span><span class="sxs-lookup"><span data-stu-id="98aba-102">ICorPublishProcess::IsManaged Method</span></span>
<span data-ttu-id="98aba-103">Získá hodnotu určující, zda proces odkazuje toto [icorpublishprocess –](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) se ví, že máte spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="98aba-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98aba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98aba-104">Syntax</span></span>  
  
```  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98aba-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="98aba-105">Parameters</span></span>  
 `pbManaged`  
 <span data-ttu-id="98aba-106">[out] Ukazatel na logickou hodnotu, která určuje, zda má proces spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="98aba-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="98aba-107">Hodnota je `true` Pokud proces má spravovaného kódu; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="98aba-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98aba-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="98aba-108">Remarks</span></span>  
 <span data-ttu-id="98aba-109">Od aktuální verze `ICorPublishProcess` umožňuje přístup jenom k procesům, které mají spravovaného kódu, `IsManaged` vždy vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="98aba-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98aba-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="98aba-110">Requirements</span></span>  
 <span data-ttu-id="98aba-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98aba-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98aba-112">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="98aba-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="98aba-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98aba-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98aba-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98aba-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98aba-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="98aba-115">See also</span></span>

- [<span data-ttu-id="98aba-116">ICorPublishProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="98aba-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
