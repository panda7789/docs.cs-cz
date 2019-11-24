---
title: IMetaDataImport::GetCustomAttributeProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeProps
helpviewer_keywords:
- GetCustomAttributeProps method [.NET Framework metadata]
- IMetaDataImport::GetCustomAttributeProps method [.NET Framework metadata]
ms.assetid: 6eefb243-a281-41c1-bcdc-7e17513bc446
topic_type:
- apiref
ms.openlocfilehash: 9a80336db4a5a8d7cfdebb7eb8d25bcb8f96e87c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437645"
---
# <a name="imetadataimportgetcustomattributeprops-method"></a><span data-ttu-id="15b19-102">IMetaDataImport::GetCustomAttributeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="15b19-102">IMetaDataImport::GetCustomAttributeProps Method</span></span>
<span data-ttu-id="15b19-103">Gets the value of the custom attribute, given its metadata token.</span><span class="sxs-lookup"><span data-stu-id="15b19-103">Gets the value of the custom attribute, given its metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15b19-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15b19-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15b19-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="15b19-105">Parameters</span></span>  
 `cv`  
 <span data-ttu-id="15b19-106">[in] A metadata token that represents the custom attribute to be retrieved.</span><span class="sxs-lookup"><span data-stu-id="15b19-106">[in] A metadata token that represents the custom attribute to be retrieved.</span></span>  
  
 `ptkObj`  
 <span data-ttu-id="15b19-107">[out, optional] A metadata token representing the object that the custom attribute modifies.</span><span class="sxs-lookup"><span data-stu-id="15b19-107">[out, optional] A metadata token representing the object that the custom attribute modifies.</span></span> <span data-ttu-id="15b19-108">This value can be any type of metadata token except `mdCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="15b19-108">This value can be any type of metadata token except `mdCustomAttribute`.</span></span>  
  
 `ptkType`  
 <span data-ttu-id="15b19-109">[out, optional] An `mdMethodDef` or `mdMemberRef` metadata token representing the <xref:System.Type> of the returned custom attribute.</span><span class="sxs-lookup"><span data-stu-id="15b19-109">[out, optional] An `mdMethodDef` or `mdMemberRef` metadata token representing the <xref:System.Type> of the returned custom attribute.</span></span>  
  
 `ppBlob`  
 <span data-ttu-id="15b19-110">[out, optional] A pointer to an array of data that is the value of the custom attribute.</span><span class="sxs-lookup"><span data-stu-id="15b19-110">[out, optional] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="15b19-111">[out, optional] The size in bytes of the data returned in \*`ppBlob`.</span><span class="sxs-lookup"><span data-stu-id="15b19-111">[out, optional] The size in bytes of the data returned in \*`ppBlob`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15b19-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="15b19-112">Remarks</span></span>  
 <span data-ttu-id="15b19-113">A custom attribute is stored as an array of data, the format which is understood by the metadata engine.</span><span class="sxs-lookup"><span data-stu-id="15b19-113">A custom attribute is stored as an array of data, the format which is understood by the metadata engine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15b19-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="15b19-114">Requirements</span></span>  
 <span data-ttu-id="15b19-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15b19-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15b19-116">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="15b19-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="15b19-117">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="15b19-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="15b19-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15b19-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15b19-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15b19-119">See also</span></span>

- [<span data-ttu-id="15b19-120">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="15b19-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="15b19-121">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="15b19-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
