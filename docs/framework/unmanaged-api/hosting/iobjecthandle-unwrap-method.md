---
title: IObjectHandle::Unwrap – metoda
ms.date: 03/30/2017
api_name:
- IObjectHandle.Unwrap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Unwrap
helpviewer_keywords:
- Unwrap method [.NET Framework hosting]
- IObjectHandle::Unwrap method [.NET Framework hosting]
ms.assetid: 794c6f8e-ed58-416b-b756-e864f2c958f7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da25055917743481f5a8314023ed94d552fe49ce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54526415"
---
# <a name="iobjecthandleunwrap-method"></a><span data-ttu-id="eee69-102">IObjectHandle::Unwrap – metoda</span><span class="sxs-lookup"><span data-stu-id="eee69-102">IObjectHandle::Unwrap Method</span></span>
<span data-ttu-id="eee69-103">Rozbalí objekt zařazování podle hodnot z dereference.</span><span class="sxs-lookup"><span data-stu-id="eee69-103">Unwraps a marshal-by-value object from indirection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eee69-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eee69-104">Syntax</span></span>  
  
```  
HRESULT Unwrap (  
    [out, retval] VARIANT *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eee69-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eee69-105">Parameters</span></span>  
 `ppv`  
 <span data-ttu-id="eee69-106">[out] Ukazatel na objekt k rozbalení.</span><span class="sxs-lookup"><span data-stu-id="eee69-106">[out] A pointer to the object to be unwrapped.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eee69-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eee69-107">Requirements</span></span>  
 <span data-ttu-id="eee69-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eee69-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eee69-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="eee69-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eee69-110">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eee69-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eee69-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eee69-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eee69-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eee69-112">See also</span></span>

