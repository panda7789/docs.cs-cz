---
title: IMetaDataImport::GetUserString – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetUserString
helpviewer_keywords:
- IMetaDataImport::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 0fd3bb47-58b5-4083-b241-b9719df7a285
topic_type:
- apiref
ms.openlocfilehash: 690abec6104f6eed1ad5a0eae9a6b6bb18d35b0d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436685"
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="4f33e-102">IMetaDataImport::GetUserString – metoda</span><span class="sxs-lookup"><span data-stu-id="4f33e-102">IMetaDataImport::GetUserString Method</span></span>
<span data-ttu-id="4f33e-103">Gets the literal string represented by the specified metadata token.</span><span class="sxs-lookup"><span data-stu-id="4f33e-103">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f33e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f33e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f33e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4f33e-105">Parameters</span></span>  
 `stk`  
 <span data-ttu-id="4f33e-106">[in] The String token to return the associated string for.</span><span class="sxs-lookup"><span data-stu-id="4f33e-106">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="4f33e-107">[out] A copy of the requested string.</span><span class="sxs-lookup"><span data-stu-id="4f33e-107">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="4f33e-108">[in] The maximum size in wide characters of the requested `szString`.</span><span class="sxs-lookup"><span data-stu-id="4f33e-108">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="4f33e-109">[out] The size in wide characters of the returned `szString`.</span><span class="sxs-lookup"><span data-stu-id="4f33e-109">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f33e-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4f33e-110">Requirements</span></span>  
 <span data-ttu-id="4f33e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f33e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f33e-112">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4f33e-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4f33e-113">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4f33e-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4f33e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f33e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f33e-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f33e-115">See also</span></span>

- [<span data-ttu-id="4f33e-116">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4f33e-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="4f33e-117">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4f33e-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
