---
title: IMetaDataImport::GetFieldProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldProps
helpviewer_keywords:
- IMetaDataImport::GetFieldProps method [.NET Framework metadata]
- GetFieldProps method [.NET Framework metadata]
ms.assetid: 7b0e9b10-8cef-4ba6-8432-40bf63e65ab1
topic_type:
- apiref
ms.openlocfilehash: 462512fd2c2b33905b45bb67599b23b301fc71f7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437991"
---
# <a name="imetadataimportgetfieldprops-method"></a><span data-ttu-id="2f5de-102">IMetaDataImport::GetFieldProps – metoda</span><span class="sxs-lookup"><span data-stu-id="2f5de-102">IMetaDataImport::GetFieldProps Method</span></span>
<span data-ttu-id="2f5de-103">Gets metadata associated with the field referenced by the specified FieldDef token.</span><span class="sxs-lookup"><span data-stu-id="2f5de-103">Gets metadata associated with the field referenced by the specified FieldDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f5de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f5de-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldProps (  
   [in]  mdFieldDef        mb,   
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szField,  
   [in]  ULONG             cchField,   
   [out] ULONG             *pchField,  
   [out] DWORD             *pdwAttr,  
   [in]  PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pcbSigBlob,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f5de-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2f5de-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="2f5de-106">[in] A FieldDef token that represents the field to get associated metadata for.</span><span class="sxs-lookup"><span data-stu-id="2f5de-106">[in] A FieldDef token that represents the field to get associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="2f5de-107">[out] A pointer to a TypeDef token that represents the type of the class that the field belongs to.</span><span class="sxs-lookup"><span data-stu-id="2f5de-107">[out] A pointer to a TypeDef token that represents the type of the class that the field belongs to.</span></span>  
  
 `szField`  
 <span data-ttu-id="2f5de-108">[out] The name of the field.</span><span class="sxs-lookup"><span data-stu-id="2f5de-108">[out] The name of the field.</span></span>  
  
 `cchField`  
 <span data-ttu-id="2f5de-109">[in] The size in wide characters of the buffer for *szField*.</span><span class="sxs-lookup"><span data-stu-id="2f5de-109">[in] The size in wide characters of the buffer for *szField*.</span></span>  
  
 `pchField`  
 <span data-ttu-id="2f5de-110">[out] The actual size of the returned buffer.</span><span class="sxs-lookup"><span data-stu-id="2f5de-110">[out] The actual size of the returned buffer.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="2f5de-111">[out] Flags associated with the field's metadata.</span><span class="sxs-lookup"><span data-stu-id="2f5de-111">[out] Flags associated with the field's metadata.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="2f5de-112">[in] A pointer to the binary metadata value that describes the field.</span><span class="sxs-lookup"><span data-stu-id="2f5de-112">[in] A pointer to the binary metadata value that describes the field.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="2f5de-113">[out] The size in bytes of `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="2f5de-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="2f5de-114">[out] A flag that specifies the value type of the field.</span><span class="sxs-lookup"><span data-stu-id="2f5de-114">[out] A flag that specifies the value type of the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="2f5de-115">[out] A constant value for the field.</span><span class="sxs-lookup"><span data-stu-id="2f5de-115">[out] A constant value for the field.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="2f5de-116">[out] The size in chars of `ppValue`, or zero if no string exists.</span><span class="sxs-lookup"><span data-stu-id="2f5de-116">[out] The size in chars of `ppValue`, or zero if no string exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f5de-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2f5de-117">Requirements</span></span>  
 <span data-ttu-id="2f5de-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f5de-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f5de-119">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2f5de-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2f5de-120">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2f5de-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2f5de-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f5de-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f5de-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2f5de-122">See also</span></span>

- [<span data-ttu-id="2f5de-123">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f5de-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="2f5de-124">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f5de-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
