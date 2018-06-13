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
ms.openlocfilehash: 0d9a8f9aa910054a4541e4ff8c1f7cad63077ba8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439947"
---
# <a name="iobjecthandleunwrap-method"></a><span data-ttu-id="3eedb-102">IObjectHandle::Unwrap – metoda</span><span class="sxs-lookup"><span data-stu-id="3eedb-102">IObjectHandle::Unwrap Method</span></span>
<span data-ttu-id="3eedb-103">Rozbalí objekt zařazování hodnotu z indirection.</span><span class="sxs-lookup"><span data-stu-id="3eedb-103">Unwraps a marshal-by-value object from indirection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eedb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3eedb-104">Syntax</span></span>  
  
```  
HRESULT Unwrap (  
    [out, retval] VARIANT *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3eedb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3eedb-105">Parameters</span></span>  
 `ppv`  
 <span data-ttu-id="3eedb-106">[out] Ukazatel na objekt k rozbalení.</span><span class="sxs-lookup"><span data-stu-id="3eedb-106">[out] A pointer to the object to be unwrapped.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3eedb-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3eedb-107">Requirements</span></span>  
 <span data-ttu-id="3eedb-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3eedb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3eedb-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3eedb-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3eedb-110">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3eedb-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3eedb-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3eedb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eedb-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="3eedb-112">See Also</span></span>  
 
