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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1c734801fd5629d8ed6bf4bccd81cf6b6de246f4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777410"
---
# <a name="imetadataemitdeletetoken-method"></a><span data-ttu-id="cefb2-102">IMetaDataEmit::DeleteToken – metoda</span><span class="sxs-lookup"><span data-stu-id="cefb2-102">IMetaDataEmit::DeleteToken Method</span></span>
<span data-ttu-id="cefb2-103">Odstraní zadaný token z aktuálního rozsahu metadat.</span><span class="sxs-lookup"><span data-stu-id="cefb2-103">Deletes the specified token from the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cefb2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cefb2-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteToken (   
    [in]  mdToken     tkObj   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cefb2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cefb2-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="cefb2-106">[in] Token, který má být odstraněna.</span><span class="sxs-lookup"><span data-stu-id="cefb2-106">[in] The token to be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cefb2-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cefb2-107">Requirements</span></span>  
 <span data-ttu-id="cefb2-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cefb2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cefb2-109">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cefb2-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cefb2-110">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cefb2-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cefb2-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cefb2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cefb2-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cefb2-112">See also</span></span>

- [<span data-ttu-id="cefb2-113">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cefb2-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="cefb2-114">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cefb2-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
