---
title: IMetaDataEmit2::SaveDelta – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDelta
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDelta
helpviewer_keywords:
- IMetaDataEmit2::SaveDelta method [.NET Framework metadata]
- SaveDelta method [.NET Framework metadata]
ms.assetid: b95739fe-d2fa-4776-ae0d-31d9707ef799
topic_type:
- apiref
ms.openlocfilehash: afb0c09c09236267be2a999ce5c130feebb52b6f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447906"
---
# <a name="imetadataemit2savedelta-method"></a><span data-ttu-id="64d66-102">IMetaDataEmit2::SaveDelta – metoda</span><span class="sxs-lookup"><span data-stu-id="64d66-102">IMetaDataEmit2::SaveDelta Method</span></span>
<span data-ttu-id="64d66-103">Saves changes from the current edit-and-continue session to the specified file.</span><span class="sxs-lookup"><span data-stu-id="64d66-103">Saves changes from the current edit-and-continue session to the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64d66-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64d66-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,   
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64d66-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="64d66-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="64d66-106">[in] The file name under which to save changes.</span><span class="sxs-lookup"><span data-stu-id="64d66-106">[in] The file name under which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="64d66-107">[in] Reserved.</span><span class="sxs-lookup"><span data-stu-id="64d66-107">[in] Reserved.</span></span> <span data-ttu-id="64d66-108">Must be zero.</span><span class="sxs-lookup"><span data-stu-id="64d66-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64d66-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="64d66-109">Requirements</span></span>  
 <span data-ttu-id="64d66-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64d66-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64d66-111">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="64d66-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="64d66-112">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="64d66-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="64d66-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64d66-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64d66-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="64d66-114">See also</span></span>

- [<span data-ttu-id="64d66-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="64d66-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="64d66-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="64d66-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
