---
title: IMetaDataImport::GetRVA – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
ms.openlocfilehash: a3a5cadc1b5a9df7967aae271ff10296843121dd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436953"
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="2b775-102">IMetaDataImport::GetRVA – metoda</span><span class="sxs-lookup"><span data-stu-id="2b775-102">IMetaDataImport::GetRVA Method</span></span>
<span data-ttu-id="2b775-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span><span class="sxs-lookup"><span data-stu-id="2b775-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b775-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b775-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,   
   [out] ULONG       *pulCodeRVA,   
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b775-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b775-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="2b775-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span><span class="sxs-lookup"><span data-stu-id="2b775-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="2b775-107">If the token is a FieldDef, the field must be a global variable.</span><span class="sxs-lookup"><span data-stu-id="2b775-107">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="2b775-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span><span class="sxs-lookup"><span data-stu-id="2b775-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="2b775-109">[out] A pointer to the implementation flags for the method.</span><span class="sxs-lookup"><span data-stu-id="2b775-109">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="2b775-110">This value is a bitmask from the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration.</span><span class="sxs-lookup"><span data-stu-id="2b775-110">This value is a bitmask from the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="2b775-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span><span class="sxs-lookup"><span data-stu-id="2b775-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b775-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2b775-112">Requirements</span></span>  
 <span data-ttu-id="2b775-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b775-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b775-114">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2b775-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2b775-115">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2b775-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2b775-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b775-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b775-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b775-117">See also</span></span>

- [<span data-ttu-id="2b775-118">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2b775-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="2b775-119">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2b775-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
