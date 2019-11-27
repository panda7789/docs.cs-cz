---
title: IMetaDataEmit::DeleteToken – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteToken
helpviewer_keywords:
- DeleteToken method [.NET Framework metadata]
- IMetaDataEmit::DeleteToken method [.NET Framework metadata]
ms.assetid: a4926d0a-261b-46b1-9994-82633661a64b
topic_type:
- apiref
ms.openlocfilehash: e8c145632911817e8e19d587bb8afead0a6c33af
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434344"
---
# <a name="imetadataemitdeletetoken-method"></a><span data-ttu-id="92872-102">IMetaDataEmit::DeleteToken – metoda</span><span class="sxs-lookup"><span data-stu-id="92872-102">IMetaDataEmit::DeleteToken Method</span></span>
<span data-ttu-id="92872-103">Odstraní zadaný token z aktuálního oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="92872-103">Deletes the specified token from the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92872-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92872-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteToken (   
    [in]  mdToken     tkObj   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92872-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="92872-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="92872-106">pro Token, který má být odstraněn.</span><span class="sxs-lookup"><span data-stu-id="92872-106">[in] The token to be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92872-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="92872-107">Requirements</span></span>  
 <span data-ttu-id="92872-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92872-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92872-109">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="92872-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="92872-110">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="92872-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92872-111">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92872-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92872-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="92872-112">See also</span></span>

- [<span data-ttu-id="92872-113">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92872-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="92872-114">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92872-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
