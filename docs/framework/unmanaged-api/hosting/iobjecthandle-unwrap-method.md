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
ms.openlocfilehash: be488ebe663169cabc5b569335dfc784fdf30556
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102697"
---
# <a name="iobjecthandleunwrap-method"></a><span data-ttu-id="54923-102">IObjectHandle::Unwrap – metoda</span><span class="sxs-lookup"><span data-stu-id="54923-102">IObjectHandle::Unwrap Method</span></span>
<span data-ttu-id="54923-103">Rozbalí objekt zařazování podle hodnoty z indirekce.</span><span class="sxs-lookup"><span data-stu-id="54923-103">Unwraps a marshal-by-value object from indirection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54923-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54923-104">Syntax</span></span>  
  
```cpp  
HRESULT Unwrap (  
    [out, retval] VARIANT *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54923-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="54923-105">Parameters</span></span>  
 `ppv`  
 <span data-ttu-id="54923-106">mimo Ukazatel na objekt, který má být zabalen.</span><span class="sxs-lookup"><span data-stu-id="54923-106">[out] A pointer to the object to be unwrapped.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54923-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="54923-107">Requirements</span></span>  
 <span data-ttu-id="54923-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54923-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54923-109">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="54923-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="54923-110">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="54923-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54923-111">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54923-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
