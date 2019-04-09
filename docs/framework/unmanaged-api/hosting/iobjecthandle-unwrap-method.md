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
ms.openlocfilehash: 4c18607d5373b415228846350a3dd0637ade1b45
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150797"
---
# <a name="iobjecthandleunwrap-method"></a><span data-ttu-id="1cf54-102">IObjectHandle::Unwrap – metoda</span><span class="sxs-lookup"><span data-stu-id="1cf54-102">IObjectHandle::Unwrap Method</span></span>
<span data-ttu-id="1cf54-103">Rozbalí objekt zařazování podle hodnot z dereference.</span><span class="sxs-lookup"><span data-stu-id="1cf54-103">Unwraps a marshal-by-value object from indirection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cf54-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1cf54-104">Syntax</span></span>  
  
```  
HRESULT Unwrap (  
    [out, retval] VARIANT *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1cf54-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1cf54-105">Parameters</span></span>  
 `ppv`  
 <span data-ttu-id="1cf54-106">[out] Ukazatel na objekt k rozbalení.</span><span class="sxs-lookup"><span data-stu-id="1cf54-106">[out] A pointer to the object to be unwrapped.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cf54-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1cf54-107">Requirements</span></span>  
 <span data-ttu-id="1cf54-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cf54-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cf54-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1cf54-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1cf54-110">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1cf54-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="1cf54-111">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="1cf54-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
